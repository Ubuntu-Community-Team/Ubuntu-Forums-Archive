---
title: "can't update/chance partitions"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by dominikkugelmann on 2014-05-31
Hey,
I just wanted to update my system but it says that the system hasn't enough space to update (see screenshot below). To solve the problem i wanted to change the partitions with Gparted. 
It booted just fine but I can't chance the sice of my main partition. 
Where is my fault or is there an other solution?

greets

---

### Post by LastDino on 2014-05-31
It's in language I don't know. Is it possible that you've a separate /Boot? If yes, there is chance that old kernels are still residing there and cleaning them would do the desired job just fine.

---

### Post by vkmaxx on 2014-05-31
Please post error in English.

---

### Post by coffeecat on 2014-05-31
@dominikkugelmann, so that English-speaking people can help you, I've scanned your image with tesseract to get an output text file in German, cleaned up the tesseract output as best I can with my rudimentary knowledge of German, and put it through Google Translate.  

German text:

> Software-Aktualisierungen

 Nicht genug freier Festplattenspeicher verfügbar

Die Systemaktualisierung benötigt 72,5 M an freiem
Speicherplatz auf der Festplatte "/boot". Bitte stellen sie
mindestens 23,9 M an zusätzlichem Speicherplatz auf der
Festplatte /boot zur Verfügung. Leeren Sie
beispielsweise den Müll und löschen Sie temporäre pakete
aus früheren Installationen mit dem Befehl "sudo apt-get
clean".

English translation:

> Software updates

Not enough free disk space available

The system update requires 72.5 M of free
Space on the disk "/ boot". Please make
at least 23.9 M of additional space on the
Hard disk / boot available. Empty
For example, the trash and delete temporary packages
from previous installation with the command "sudo apt-get
clean ".

Your /boot partition is too full. I agree with LastDino - you need to uninstall unused kernels. Do you need help with that?

---

### Post by dominikkugelmann on 2014-05-31
Oh thanks @[**[COLOR=#990303][B]coffeecat**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=129087") for the translation. I've forgotten that its a german error massage :) 





Okey
How do i uninstall unused kernels?

---

### Post by sammiev on 2014-05-31
Here is a few options.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by dominikkugelmann on 2014-05-31
thanks

---

