# Movie Recommendation System

## Project Overview

This project implements a movie recommendation system, focusing on collaborative filtering and similarity-based recommendation techniques. The system is designed to suggest movies to users based on their preferences and the characteristics of movies they have previously enjoyed. 

## Objectives

- **Explore** different collaborative filtering techniques to improve recommendation accuracy.
- **Analyze** user-movie interaction data to understand and predict user preferences.
- **Develop** a scalable recommendation function that can efficiently handle new data inputs.

## Methodology
The project involves:
1. **Data Preprocessing**: Data cleaning and transformation to construct a user-item matrix, where each cell represents a user's rating for a movie. Movies with insufficient ratings or sparse user interactions are filtered out to enhance the robustness of similarity calculations.
2. **Cosine Similarity Matrix**: Calculation of cosine similarity between movies, based on user ratings. This matrix enables the identification of movies similar to each other, providing the foundation for similarity-based recommendations.
3. **Recommendation Algorithms**:
   - **get_similar_movies**: A function that identifies the top 10 movies most similar to a target movie.
   - **recommend_movies**: A function that recommends movies to a user by predicting ratings for unwatched movies, utilizing user preferences and similarities with previously watched movies.

## Key Functions
### 1. `get_similar_movies(movie_id: int) -> Union[pd.DataFrame, str]`
This function takes a movie ID and returns a DataFrame containing details of the 10 most similar movies based on cosine similarity. If the movie ID is not found, it returns an error message.

- **Parameters**: `movie_id` (int) - ID of the target movie.
- **Returns**: DataFrame with similar movies or an error message if the ID is invalid.
- **Implementation Details**:
  - Checks for movie ID validity.
  - Uses the similarity matrix to identify and rank the top 10 similar movies, excluding the movie itself.
  - Retrieves movie details for easier interpretation of results.

### 2. `recommend_movies(user_id: int) -> pd.DataFrame`
This function recommends three movies to a given user, selecting those with the highest estimated ratings based on the user’s history.

- **Parameters**: `user_id` (int) - ID of the target user.
- **Returns**: DataFrame with recommended movies.
- **Implementation Details**:
  - Validates user ID presence in the dataset.
  - Calculates ratings for unwatched movies by taking a weighted average of ratings for similar movies that the user has watched.
  - Ranks estimated ratings in descending order and selects the top three movies.

## Notes and Additional Insights
- **Genre Representation**: Balancing genres among recommendations to avoid bias towards popular movies, ensuring recommendations cover diverse categories.
- **Zero-Filled Ratings**: Non-watched movies are marked with zero ratings; however, this does not imply user dislike. SVD-based techniques could be employed to further refine user preference predictions.
- **Future Work**: Implementation of alternative methods such as matrix factorization (e.g., Funk SVD or SVD++) to capture latent patterns in user preferences and item attributes.

## Dependencies
- **Python 3.8+**
- **Pandas**
- **NumPy**

## Usage

To use the recommendation system, follow these steps:
1. Install the required dependencies.
2. Execute the `get_similar_movies(movie_id)` function to find movies similar to a target movie.
3. Execute the `recommend_movies(user_id)` function to obtain personalized recommendations for a user.

## Acknowledgements

This project was submitted as part of the **SBE3021 AI in Medical Fields course, Spring 2024** under the supervison of **[Dr. Inas Yassine](https://www.linkedin.com/in/inas-yassine-15ab4b4/?originalSubdomain=eg)** and **[ENG. Merna Bibars](https://merna-atef.github.io/)**.


