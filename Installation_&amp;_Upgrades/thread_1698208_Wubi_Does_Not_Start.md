---
title: "Wubi Does Not Start"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by vrenjith on 2011-03-01
I have the Ubuntu Netbook CD. I tried installing Ubuntu by launching Wubi.exe. But nothing seems to be happening. I opened task manager and checked whether the process wubi.exe is starting. It is indeed starting up, but goes off in a few seconds.
I downloaded the wubi.exe again and tried, but without any success.
Any clues?

---

### Post by bcbc on 2011-03-01
Check the %temp% directory and look for the wubi-xx.xx-revxxx.log file. If there's nothing there, clean up any py* files and py*.tmp directories. That's worked for some before.

---

### Post by sahilsameerac on 2011-03-01
why are logging into windows
change bios settings to first boot device as cd rom and try restarting

---

### Post by vrenjith on 2011-03-02
Sahil: I do not have administrative rights on my laptop (office) to change the boot order settings.

bcbc: Cleaning up of the temporary directory helped. Now it is starting. Trying installation now. 

Thank you guys!

---

### Post by bcbc on 2011-03-02
If you don't have administrative rights you won't be able to install. At least I'd be surprised if it worked.

---

### Post by cano14 on 2012-01-03
[SIZE=2]I had the same problem installing ubuntu 11.10 from wubi, and this is what I found.
The problem seems to be that when wubi checks to see if you already have the ubuntu iso image, if it finds any iso file it cancels the installation because the iso it finds does not have the installation files it is looking for. 
The solution is to move any iso files you have in the folder it is looking at, and run wubi again. 
To find out where it is looking at go to the temp folder (start->run->%temp%) and open the log file (in my case wubi-11.10-rev245.log) look at the end and you will see it specifies the iso file it was trying to use.
 I had a couple of iso files in the root of my D partition and I moved them to a new folder and that took care of the problem. The log file still shows that wubi looked at those iso images at their new location, but it recognized they were not what it needed and moved on to download the ubuntu image.
[/SIZE]

---

