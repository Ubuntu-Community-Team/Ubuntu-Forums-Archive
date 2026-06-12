---
title: "How to get Seeborg working for ubuntu 9.10"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by infernowolf36 on 2009-11-20
I'm having troubles here. i got this irc bot here: [http://code.google.com/p/seeborg/downloads/list](http://code.google.com/p/seeborg/downloads/list)

got the source file, and used ark to extract it. at this point i have no idea what to do now. as far as i know, seeborg is an irc bot that takes information and "learns" from it. either way it's a bot. i'd like to know how to get it up and running. 

any ideas/help would be greatly appreciated.

---

### Post by JBAlaska on 2009-11-20
[quote="From the readme"]To compile, **read the Makefiles** and **make any changes required (you may probably want to change CFCPU to better value), then type `make' and fix the errors which will be displayed**, if any. SeeBorg is in development and probably won't work as you expect.

[B]After running "make", you'll end up with two executables - "seeborg-irc" and "seeborg-linein", these are IRC client or linein interactive mode respectively. The linein is useful for offline chat with the bot and to test the modifications done to the dictionary.
[/B]
Without any parameters, seeborg-irc reads configuration from "seeborg-irc.cfg" file located in current working directory. If it doesn't exist, it will create one and terminate, suggesting you to inspect the config file, that would be a good idea. [/quote]

So check out the makefiles for clues

---

### Post by infernowolf36 on 2009-11-20
the only problem with that is it made more than one of those files. one has a .h after it the other a .d and another .c and maybe some more.

---

### Post by infernowolf36 on 2009-11-20
also, upon running make, i get 

In file included from seeborg.cpp:4:
seeutil.h: In function ‘int randInt(int, int)’:
seeutil.h:11: error: ‘rand’ was not declared in this scope
seeutil.h:11: error: ‘RAND_MAX’ was not declared in this scope
seeutil.h: In function ‘float randFloat(float, float)’:
seeutil.h:21: error: ‘rand’ was not declared in this scope
seeutil.h:21: error: ‘RAND_MAX’ was not declared in this scope
seeborg.cpp: In member function ‘std::string SeeBorg::Reply(std::string)’:
seeborg.cpp:77: error: ‘rand’ was not declared in this scope
seeborg.cpp: In member function ‘std::string SeeBorg::ParseCommands(std::string)’:
seeborg.cpp:195: error: ‘strlen’ was not declared in this scope
seeborg.cpp:195: error: ‘strncmp’ was not declared in this scope
seeborg.cpp: In function ‘std::string CMD_Quit_f(SeeBorg*, std::string)’:
seeborg.cpp:287: error: ‘exit’ was not declared in this scope
make: *** [seeborg.o] Error 1

---

### Post by infernowolf36 on 2009-11-23
no ideas?

---

### Post by DonSlice on 2009-12-28
> **infernowolf36 said:**
> no ideas?

Sorry to bump...

You need to get the latest build from the SVN.

[http://code.google.com/p/seeborg/source/checkout](http://code.google.com/p/seeborg/source/checkout)

---

