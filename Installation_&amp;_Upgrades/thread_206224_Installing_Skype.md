---
title: "Installing Skype ?"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by ThaDoctor99 on 2006-06-29
Hi, 
Just wandering if any of you have installed skype as i cant get it to work, would be neat if any of you could just add some code to simplify the process.


Greetings Tobias

---

### Post by CameronCalver on 2006-06-29
well add this to your /etc/apt/sources.list

## Skype
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) breezy-seveas extras
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

and then do 

```
sudo apt-get install skype
```


and tell me if it work ok 

Cameron

---

### Post by Chaoticwhizz on 2006-06-29
tried it. I got:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package skype

Do you have to restart or log out, then back in after editing the sources.list file? I am running the AMD64 version so that may be why. Maybe there isnt a 64bit linux version.

---

### Post by tenshi-no-shi on 2006-06-30
Yo have to do sudo apt-get update first, That refreshs your package lists.

---

### Post by ThaDoctor99 on 2006-07-01
Says mistake with me.
Is this really the most easy way to do it ?
Skype is a little irritating to install ? It could have been done a little bit more handy.
But anyway, what about download a package from the website compile it and install that ?
 

Greetings Tobias

---

### Post by user1397 on 2006-07-01
[quote=ThaDoctor99]Says mistake with me.
Is this really the most easy way to do it ?
Skype is a little irritating to install ? It could have been done a little bit more handy.
But anyway, what about download a package from the website compile it and install that ?
 

Greetings Tobias[/quote]its actually quite easy, if given easy instructions.
[FONT=Verdana]
open a terminal (applications > accessories > terminal), and copy/paste this into it: ```
gksudo gedit /etc/apt/sources.list
```in sources.list, go to the bottom, skip a line, and add:

deb [http://download]("http://download").**skype**.com/linux/repos/debian/ stable non-free

save the file, and close it.  now go back to the terminal, and copy/paste this: ```
sudo aptitude update && sudo aptitude install skype
```it should appear under applications > internet > skype

[/FONT][FONT=Verdana]NOTE: Doing it this way is not _the_ easiest way to install skype, because you could just go to the skype website, download the deb package, double-click on it, and install it.  However, doing it the way described above makes it so that you can use the terminal or synaptic to find and install the package, should you choose to install/uninstall it. [/FONT]

---

### Post by ThaDoctor99 on 2006-07-03
It really seems not to work... But is the deb package like exe ?

---

### Post by ThaDoctor99 on 2006-07-03
Anyway I have now got skype installed in the very most easy way, while doing that I felt a bit of a fool :-), bvut anyway I think this idea about a forum is very good and everybody seems very open to help others that have troubles they once also had (Or at least I think they must have had.)


Greetings Tobias

---

### Post by CameronCalver on 2006-07-17
i agree with you i have had problemsso i made a thread and now i can help people with the problem and people can read the thread that helped me and i think without this forums ubuntu would not have gotten this far

---

