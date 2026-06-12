---
title: "How to fix broken packages"
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2015-05-11
Hello everyone, after doing a new install of Ubuntu I starting to install the programs I've always used including Google chrome. The problem I'm having is I can't not install Google chrome after a few attempts, It's telling me I have a broken package but I'm not sure how to fix this. Thanks so much for any help with this matter.

---

### Post by slickymaster on 2015-05-11
How are you trying to install it? Directly downloading the *.deb package from google chrome download page or installing it through the official Google Chrome PPA?

---

### Post by RobGoss on 2015-05-11
Hello and thank you. I've tried installing from my terminal and Ubuntu software center and directly from Google's website neither one worked. As for the PPA I don't believe I've ever used that 

Any help would be great

---

### Post by slickymaster on 2015-05-11
Can you please post back, here in the thread, the output you get when you tried to install it?

---

### Post by mc4man on 2015-05-11
If this is an absolutely new install then try simply updating sources before trying to install anything - 
sudo apt-get update

---

### Post by RobGoss on 2015-05-11
> **slickymaster said:**
> Can you please post back, here in the thread, the output you get when you tried to install it?

I'm at work right now it's kind of hard to do that but as soon as I'm able I will do so.

---

### Post by RobGoss on 2015-05-11
[COLOR=#000000][SIZE=3][FONT=Lucida Grande]It worked thanks so much guys I had to locate the broken package from Synaptic Package Manager and then choose the Fix broken package and it seems to be ok now.[/FONT][/SIZE][/COLOR]

---

### Post by walttheboss on 2015-05-11
Here are some notes from my own IT Notes reference. 

H) Repair broken packages
I) Check and Repair
a) sudo dpkg --configure -a
II) Looks for and install missing dependencies 
a) sudo apt-get -f install
III) Sometimes the headers/sources get messed up.  
a) sudo rm /var/lib/apt/lists/* -vf
b) sudo apt-get update

---

### Post by RobGoss on 2015-05-11
> **walttheboss said:**
> Here are some notes from my own IT Notes reference. 

H) Repair broken packages
I) Check and Repair
a) sudo dpkg --configure -a
II) Looks for and install missing dependencies 
a) sudo apt-get -f install
III) Sometimes the headers/sources get messed up.  
a) sudo rm /var/lib/apt/lists/* -vf
b) sudo apt-get update


Thanks so much for this list I'm sure it will come in handy.

---

### Post by DanielWEWO on 2015-05-11
> **walttheboss said:**
> Here are some notes from my own IT Notes reference. 

H) Repair broken packages
I) Check and Repair
a) sudo dpkg --configure -a
II) Looks for and install missing dependencies 
a) sudo apt-get -f install
III) Sometimes the headers/sources get messed up.  
a) sudo rm /var/lib/apt/lists/* -vf
b) sudo apt-get update


What does apt-get -f do, and what is the -vf option for rm? Just curious as to your methods.

---

### Post by v3.xx on 2015-05-11
> **DanielWEWO said:**
> What does apt-get -f do, and what is the -vf option for rm? Just curious as to your methods.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by walttheboss on 2015-05-11
> **DanielWEWO said:**
> What does apt-get -f do, and what is the -vf option for rm? Just curious as to your methods.

-v almost always means verbose in linux.  That will tell you more details about what the command is doing.
-f usually stands for force.  

If you want -f and -v you can combine them as -vf  or write them all out as --verbose and --force

Two minuese means don't look at indivual letters but the word.

--forceverbose will NOT work but -fv will

I am no expert.  Just a guy in a job where I have had to learn lots of this stuff.

---

### Post by DanielWEWO on 2015-05-11
so the -f in apt-get stands for "fix" broken packages :) Nice!

---

### Post by ian-weisser on 2015-05-12
> **walttheboss said:**
> Here are some notes from my own IT Notes reference. 

H) Repair broken packages
I) Check and Repair
a) sudo dpkg --configure -a
II) Looks for and install missing dependencies 
a) sudo apt-get -f install
III) Sometimes the headers/sources get messed up.  
a) sudo rm /var/lib/apt/lists/* -vf
b) sudo apt-get update

A more flexible method is to do an apt-get update/upgrade...and read the error message.
Apt tries very hard to explain exactly what the problem is. None of the problems are difficult to fix, once you know what the problem is.

---

