Animals Table:
animal_id
animal_name
age
weight
species_id*

Species Table:
species_id
species_name

User Table:
user_id
user_password
user_email
first_name
last_name

User-Species Table:
user-species_id
user_id*
species_id*

Suggestion Table:
suggestion_id
user_id*
animal_id*

CREATE TABLE species(
  species_id SERIAL PRIMARY KEY,
  species_name VARCHAR(50) NOT NULL
);

CREATE TABLE animals (
  animal_id SERIAL PRIMARY KEY,
  animal_name VARCHAR(50) NOT NULL,
  age INT,
  weight NUMERIC,
  species_id INT NOT NULL REFERENCES species(species_id)
);

CREATE TABLE users (
  user_id SERIAL PRIMARY KEY,
  user_email VARCHAR(50) NOT NULL,
  user_password VARCHAR(500) NOT NULL,
  first_name VARCHAR(50),
  last_name VARCHAR(50)
);

CREATE TABLE user_species (
  user_species_id SERIAL PRIMARY KEY,
  user_id INT NOT NULL REFERENCES users(user_id),
  species_id INT NOT NULL REFERENCES species(species_id)
);

CREATE TABLE suggestions (
  suggestion_id SERIAL PRIMARY KEY,
  user_id INT NOT NULL REFERENCES users(user_id),
  animal_id INT NOT NULL REFERENCES animals(animal_id)
);