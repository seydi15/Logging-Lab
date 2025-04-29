# Logging-Lab
--1st observation
When I ran the first version of the code using only console.log, console.info, console.warn, and console.error, I saw all the messages printed directly in the terminal. 
It showed messages like “Processing order” and the details of the items in the order. For example, when processing Order 456, I saw a warning that said “Large quantity 
detected” because one item had a quantity of 15. I also saw an error that said “Invalid price found” for an item with a price of 0. After each order was processed, the total
cost was printed. Then, the program simulated a critical error, and it printed “An error occurred” along with the error message. Finally, there was a debug message that said
“This is a debug message for development.” However, all the messages looked very similar and were not separated by severity or timestamp, which made it harder to tell which 
ones were most important.

--2nd observation
When I ran the updated code using the winston logging library, I noticed that the logs were much more organized and detailed. Each message had a level (such as info, warn,
or error), a message that explained what was happening, and a timestamp showing the exact time of the event. This made it easier to understand the flow of the application. 
For example, when an item had a very high quantity, a warning was logged, and when an item had an invalid price, it was logged as an error. A simulated critical error also 
appeared as an error log and included a full stack trace, which is very useful for debugging. In addition to showing up in the terminal, Winston automatically created two 
new log files:error.log and combined.log. The error.log file only included the error messages, while the combined.log file included everything—info, warnings, and errors. 
These files help keep a permanent record of what happened during the program run, which is great for reviewing issues later. Overall, logging with Winston was much clearer 
and better organized compared to just using console, and it gave me more control over how logs are stored and used.


--Observation with other format of winston
When I changed the logging level in winston.createLogger from 'info' to 'debug', I noticed that the debug messages, which were previously hidden, started showing up in the 
terminal and in the combined.log file. This is because setting the level to 'debug' allows Winston to log everything, including lower-level messages like debug, in addition
to info, warn, and error.Next, I tried different winston.format options. Changing the format to winston.format.simple() made the log output much easier to read, as it removed
the JSON structure and printed plain text messages. When I used winston.format.cli(), the logs became more colorful and developer-friendly in the terminal, which made it easier
to quickly spot warnings or errors at a glance.
