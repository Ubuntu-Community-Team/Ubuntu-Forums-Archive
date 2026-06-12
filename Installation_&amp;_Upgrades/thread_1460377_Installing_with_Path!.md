---
title: "Installing with Path!"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by gagea on 2010-04-22
Hello,

I can not understand what does this statement says and how to do it. Can anybody tell me what to do please.

  	 	 	 	 	 	  [FONT=YVGJNK+CMR12][SIZE=3]For the operating system to be able to locate the program, this directory must be specified in the global variable [/SIZE][/FONT][FONT=LTSOJN+CMTT12][SIZE=3]PATH[/SIZE][/FONT][FONT=YVGJNK+CMR12][SIZE=3]. In order to achieve this, you will have to add [/SIZE][/FONT][FONT=LTSOJN+CMTT12][SIZE=3]export PATH="/your_path/:$PATH" [/SIZE][/FONT][FONT=YVGJNK+CMR12][SIZE=3]to the [/SIZE][/FONT][FONT=LTSOJN+CMTT12][SIZE=3].bashrc [/SIZE][/FONT][FONT=YVGJNK+CMR12][SIZE=3]or the [/SIZE][/FONT][FONT=LTSOJN+CMTT12][SIZE=3].bash profile [/SIZE][/FONT][FONT=YVGJNK+CMR12][SIZE=3]located in your home directory ([/SIZE][/FONT][FONT=LTSOJN+CMTT12][SIZE=3]your path [/SIZE][/FONT][FONT=YVGJNK+CMR12][SIZE=3]is the path to the directory that contains PhyML binary).[/SIZE][/FONT]


[FONT=YVGJNK+CMR12][SIZE=3]](*,)
[/SIZE][/FONT]

---

### Post by kbielefe on 2010-04-26
If you compiled from source, generally typing "sudo make install" will install it somewhere that is already in your path, so you don't have to mess around with your .bashrc.

---

