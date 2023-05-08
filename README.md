# Knowledge Base Bot

This example bot is an improved version of knowledgebasebot provided in examples ('https://github.com/RasaHQ/rasa/'). 

## What’s inside this example?

This example contains some training data and the main files needed to build an
assistant on your local machine. The `knowledgebasebot` consists of the following files:

- **data/nlu.yml** contains training examples for the NLU model
- **data/stories.yml** contains training stories for the Core model
- **actions/actions.py** contains the custom action for querying the knowledge base
- **config.yml** contains the model configuration
- **domain.yml** contains the domain of the assistant
- **endpoints.yml** contains the webhook configuration for the custom action
- **knowledge_base_data.json** contains the data for the knowledge base

## How to use this example?

To train your knowledge base bot, execute
```
rasa train
```
This will store a zipped model file in `models/`.

To pin a specific version of rasa_sdk, replace rasa_sdk folder with rasa_sdk in 'Lib/site-packages/rasa_sdk'


Start the action server by
```
rasa run actions
```

To chat with the bot on the command line, run
```
rasa shell
```

## Sample user requests and expected bot response

Here are few sample inputs and expected responses from the bot that works on this nlu data.

```
User:  what is the cuisine of Donath?
Bot: 'Donath' has the value 'Italian' for attribute 'cuisine'.
User:  what is the price range of B&B ?
Bot: 'B&B (Berlin)' has the value 'mid-range' for attribute 'price-range'.
User:  does it have a swimming pool?
Bot: Did not find a valid value for attribute 'swimming-pool' for object 'B&B (Berlin)'.
User:  list some Italian restaurants
Bot: Found the following objects of type 'restaurant': 1: Donath 2: I due forni
User:  does the second have outside seating?
Bot: 'I due forni' has the value 'True' for attribute 'outside-seating'.
User:  show me some hotels in Berlin
Bot: Found the following objects of type 'hotel': 1: B&B (Berlin) 2: Jugendherberge (Berlin) 3: Berlin Hotel (Berlin) 4: Berlin Wall Hostel (Berlin) 5: Hilton (Berlin)
User:  what is the price range of third?
Bot: 'Berlin Hotel (Berlin)' has the value 'mid-range' for attribute 'price-range'.
User:  does it offer breakfast?
Bot: 'Berlin Hotel (Berlin)' has the value 'True' for attribute 'breakfast-included'.
User:  does Berlin Wall Hostel offer breakfast?
Bot: Did not find a valid value for attribute 'breakfast-included' for object 'Berlin Wall Hostel (Berlin)'.
```
