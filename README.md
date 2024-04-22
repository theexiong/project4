# project4

<b>Studio Ghibli Neural Network Model</b>

For this project, we were tasked with creating a machine learning model to either predict or classify data. Using Studio Ghibli characters, I had originally wanted to create a model that would predict what species a character was depending on their characteristics.

<b>Gathering Data</b>

To gather data, I used the sources listed below, to create a csv file that comprised of each character's:
1. Name
2. Age 
3. Height(cm) 
4. Eye Color
5. Hair Color
6. Special Powers
7. Country / Place of Residence
8. Gender
9. Species
10. Movie Character is in
11. Movie Release Date

<b>Preprocessing</b>

Using sqlite, I queried all the different types of species and their counts. This showed that there was not enough other species types to go with my original plan. So, my backup plan was to predict if a character was Human or Non-Human depending on their characteristics. I also queried the amount of Male versus Female characters, characters that had the same eye and hair colors, and the number of characters in a movie.

I then dropped non-beneficial columns, such as character name, movie, release date, and country/place of residence. Since these characters are fictional, some age and heights are unknown/unspecified. To solve the NaN issue, I found the average age and height and replaced all of the NaN values, because I wanted to be able to keep the character. For the specialPowers column, I catergorized characters as 0 for no special powers and 1 for special powers. The original age and height(cm) columns were replaced with the new updated values and were then scaled using StandardScaler. I made a copy of the cleanedCharacters_df and dropped the age, species, and height(cm) columns. Then merged the copied dataframe with the dataframe that contained the scaled values of age and height(cm). Next, pd.get_dummies was used to convert categorical values to numerical values and the dataframe was displayed to show the new values for each columns. I then replaced each species values as: Human,0 and Other Species,1. 

The processed dataframe values were then split into training and testing datasets using the train_test_split function. 

<b>Compile, Train, and Evaluate the Model</b>

A Standard Scaler was created and fitted to the X_training and X_testing datasets, thus transforming them. A Sequential model was then defined along with it's hidden layers, activation types and output layer. I then compiled the model and trained it using the defined model. One hundred epochs were used in the model. The model results were an accuracy of 91.3%. This accuracy exceeds the target accuracy of 75%. Overall, this model is acceptable.

<b>Model 2</b>
I also created a second notebook using the same model on the dataset. But for the second model, I dropped all characters with any NaN values. This model's accuracy result was 78.2%. This also exceeds the target accuracy of 75%, therefore acknowledges that this model works and is acceptable.



sources:</br>
https://github.com/Laboratoria/CDMX011-data-lovers/blob/master/src/data/ghibli/ghibli.json</br>
https://disney.fandom.com/wiki/Category:Studio_Ghibli_films</br>
https://ghibli.fandom.com/wiki/Studio_Ghibli</br>
https://www.kaggle.com/datasets/marshuu/ghibli-characters</br>
