---
title: "Vuze 4.2 on Ubuntu Desktop"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dasme on 2009-04-16
guys can any1 guide me how to install the latest version of Vuze 4.2 64bit which i have downloaded from official site,  on my ubuntu 9.04 64 bit

thx

---

### Post by kiridude on 2009-04-16
REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

To Run:
1. Extract the contents of .tar.bz2 file (right click > "extract here."
2. Start Azureus by runnng the script named 'azureus' (from the directory where you have extracted Vuze) type:

```
./azureus
```

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.

---

### Post by dasme on 2009-04-16
> **kiridude said:**
> REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

To Run:
1. Extract the contents of .tar.bz2 file (right click > "extract here."
2. Start Azureus by runnng the script named 'azureus' (from the directory where you have extracted Vuze) type:

```
./azureus
```

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.

i can start vuze, but how to add this program to application menu?

---

### Post by kiridude on 2009-04-17
To add vuze to your apps menu (on Intrepid - it should be similar if not the same in Jaunty):

system > preferences > main menu > highlight the menu you would like it to appear under > then click "new item" > add a name (any name - it doesn't matter) > click "browse" next to the "command" field > follow the path to put the "azureus" script you used to the run the program and double click it > ok, and you're done.

:D

---

### Post by dasme on 2009-04-17
> **kiridude said:**
> To add vuze to your apps menu (on Intrepid - it should be similar if not the same in Jaunty):

system > preferences > main menu > highlight the menu you would like it to appear under > then click "new item" > add a name (any name - it doesn't matter) > click "browse" next to the "command" field > follow the path to put the "azureus" script you used to the run the program and double click it > ok, and you're done.

:D

Thx for all the help buddy.

all done n running well :)

---

