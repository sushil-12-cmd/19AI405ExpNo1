Name: Sushil Shiva R
Register Number: 212224250017
AIM:

To find the PEAS description for the given AI problem and develop an AI agent.


Theory
Medicine prescribing agent:
Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.

PEAS DESCRIPTION:
Agent Type	Performance	Environment	Actuators	Sensors
Medicine prescribing agent	Treating unhealthy, agent movement	Rooms, Patient	Medicine, Treatment	Location, Temperature of patient
DESIGN STEPS
STEP 1:Identifying the input:
Temperature from patients, Location.

STEP 2:Identifying the output:
Prescribe medicine if the patient in a random has a fever.

STEP 3:Developing the PEAS description:
PEAS description is developed by the performance, environment, actuators, and sensors in an agent.

STEP 4:Implementing the AI agent:
Treat unhealthy patients in each room. And check for the unhealthy patients in random room

STEP 5:
Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented

import random
ROOMS = ["Room 1", "Room 2"]
FEVER_THRESHOLD = 98.5
environment = {
    "Room 1": round(random.uniform(97.0, 101.0), 1),
    "Room 2": round(random.uniform(97.0, 101.0), 1)
}
agent_location = "Room 1"
performance_score = 0

def check_temperature(room):
    temp = environment[room]
    print(f"Checking {room}... Patient temperature: {temp}°F")
    return temp

def treat_patient(room):
    global performance_score
    print(f"Treating patient in {room}... ")
    performance_score += 1 

def move_to(room):
    global agent_location, performance_score
    if agent_location != room:
        print(f"Moving from {agent_location} to {room}... ")
        agent_location = room
        performance_score -= 1  
print("Medicine Prescribing Agent Simulation Started \n")

for room in ROOMS:
    move_to(room)
    temp = check_temperature(room)
    if temp > FEVER_THRESHOLD:
        treat_patient(room)
    else:
        print(f"No treatment needed in {room}.\n")
print("\nSimulation Complete!")
print(f"Final Performance Score: {performance_score}")
print("Environment State:", environment)
