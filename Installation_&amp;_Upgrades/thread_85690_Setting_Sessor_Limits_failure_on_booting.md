---
title: "Setting Sessor Limits failure on booting"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by impeteperry on 2005-11-03
I have just installed Ubuntu 5.10 on two computers. One old and one new.
Duriing boot up, I get a "failure" on the "Setting Sensor Limies" line. 
I did not have this with 5.04.
How do I fix this?

Thanks

---

### Post by teaker1s on 2005-11-03
[https://wiki.ubuntu.com/SensorInstallHowto?highlight=%28sensor%29](https://wiki.ubuntu.com/SensorInstallHowto?highlight=%28sensor%29)

---

### Post by impeteperry on 2005-11-03
Thanks for the prompt reply, I have saved and printed the "How-To"
I am a bit of a newbie so a couple of questions.
Does leaving it alone do any harm?
Will it be covered with an update in the future.?
Thanks

---

### Post by teaker1s on 2005-11-03
I'm new too the sensors protect against system failures-that said I've never bothered because i'm lazy, but it could save your computer if you suffered a fan failure for example

---

### Post by ThirdWorld on 2005-11-10
where is the mkdev.sh file? i cant find it, do you have to create the file with gedit? this is confussing...

---

### Post by ThirdWorld on 2005-11-11
ok i create the file using gedit. and i followed the instructions, kind of complicated but very usefull. everything works now. my question is... why i have to configure such things manually? i mean, its an Ubuntu bug? or you are always suppose to configure it yourself? will this be fixed with the upcoming dapper release? :confused:

---

### Post by teaker1s on 2005-11-11
maybe not the answer your expecting  but it will give you an idea-in the howto part of it will set sensor limits they will be general-for instance you may wish to change if you overclock cpu as fan failure and overclocking would result in massive heat increase almost instantly.
To avoid this stituation you would set the sensors at a lower value so the protection happened quicker
:KS :KS

---

