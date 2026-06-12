---
title: "[SOLVED] please im so close to getting it...HELP"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by comacozi on 2007-08-28
i just installed feisty fawn. i restarted the computer after installation, and it all seems normal until a screen pops up saying that x server cannot start. I have an ati mobility radeon x1400, im guessing its a problem with my video driver.   ive been reading forums all day and night, i only need one thing, how do i change the sources, becasue when i try to install the aglrx drivers, it looks in the cd drive. im so close, please help.

---

### Post by Pumalite on 2007-08-28
You need linux-restricted-modules-2.6.20.5-15.20
Go to System>Administration>Software Sources and uncheck the CD.

---

### Post by comacozi on 2007-08-28
and i get that how

---

### Post by Pumalite on 2007-08-28
Through Synaptic ( see my editing above)

---

### Post by comacozi on 2007-08-28
yes but remember, xserver wont start, so all i have is a command prompt

---

### Post by Pumalite on 2007-08-28
sudo apt-get install linux-restricted-modules

---

### Post by comacozi on 2007-08-28
and its gunna install them from the cd drive.....is that what its supposed to do?

---

### Post by Pumalite on 2007-08-28
If you don't have connection to Internet, then re-connect your CD and see if it's in there with sudo apt-get install linux-restricted-modules. I don't know if they come in the disk or not.

---

### Post by comacozi on 2007-08-28
they dont i just tried, i have internet, just it wont look on the internet for drivers, it looks in the cd drive.  all i need to know is how to change this in command prompt

---

### Post by Pumalite on 2007-08-28
My instructions on how to do that are in post #2

---

### Post by comacozi on 2007-08-28
but i cant do that, all i have is a command prompt

---

### Post by Pumalite on 2007-08-28
Somebody with better command of the CLI will have to chime in.

---

### Post by comacozi on 2007-08-28
yes but your the only one thats been helping me, thanks alot.  ill get it one of these days

---

### Post by Pumalite on 2007-08-28
You are welcome. If I find the answer; I'll get back to you. Good luck.

---

### Post by comacozi on 2007-08-28
thanks

---

### Post by dabl on 2007-08-28
Follow the first 3 steps of this little "how-to": [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

Then, when you have a GUI, you can go back and follow Pumalite's guidance on getting your restricted driver.  :)

---

### Post by charles woodward on 2007-08-28
You can also manually edit the file that contains the list of software sources - I think it is called

sources.list

If I'm right it can be found under /etc/apt

(or you can just edit /etc/apt/sources.list.

---

