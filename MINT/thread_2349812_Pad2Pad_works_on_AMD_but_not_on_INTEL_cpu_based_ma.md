---
title: "Pad2Pad works on AMD but not on INTEL cpu based machines"
date: 2017-01-18
forum: MINT
---

### Post by roderman59 on 2017-01-18
Hello,
I have two computers,  Laptop with Intel CPU  and a Desktop with an AMD  CPU.  
BOTH computers have the exact same Os (Linux Mint 18.1) with all  the updates.
   I have an install script for installing wine (1.6.2) that  is used on both computers (dpkg).  So as far as differences go they are the  cpu, sound and video. 
  I also have the latest winetricks which  installed  dotnet40 and corefonts which is needed by pad2pad. 
The Desktop is able to run pad2pad.exe via wine without any special tweaking.  
Both are in a 32-bit Arch when running wine.
  No  errors occur during installation of pad2pad.  

(Terminal for trace)   wine pad2pad.exe

both computers output the same information until the laptop fails
The  main screen of pad2pad comes up nicely but when it goes to load the data  I am working on, it freezes.
I get the following error on my LapTop (Intel) motherboard.

[COLOR=#A52A2A][SIZE=3]err:seh:setup_exception record stack overflow ..[/SIZE][/COLOR]

Any advice or steps to resolve this would be appreciated - I like the services of pad2pad and would like to use it on my laptop.

Thank you in advance, George

---

### Post by howefield on 2017-01-18
Thread moved to the "*MINT*" forum.

---

