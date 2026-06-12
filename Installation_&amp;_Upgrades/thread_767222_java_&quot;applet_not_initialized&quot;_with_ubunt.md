---
title: "java &quot;applet not initialized&quot; with ubuntu 8.04 and firefox 3"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by kruschev on 2008-04-25
I just upgraded to ubuntu 8.04 with firefox 3.0b5, and while most java applets seem to work, when I try to load this one:

[http://www.chessgames.com/perl/chessgame?gid=1143795](http://www.chessgames.com/perl/chessgame?gid=1143795)

I am left with a grey box and the message "applet not initialized" in the bar at the bottom of firefox. With ubuntu 7.1 and firefox 2 there was never any problem.

---

### Post by clsrskv on 2008-05-01
Could someone capable of writing an instruction on how to replace open-java with sun-java and make Firefox use this version instead of just crashing when an applet is loaded?

Please?!

---

### Post by Mainlake on 2008-05-04
Fought this one long time, and I couldn't get the applets work. Weirdly enough I solved this problem, by uninstalling all icedtea java plugins, and then restarting Firefox and going to the page that was not working. And to my great suprise applet works.

---

### Post by alishad on 2008-05-14
Removing the icedtea worked for me too...thanks

---

### Post by noworry on 2008-06-03
Thanks a lot !!! this worked for me :)

---

### Post by me0262 on 2008-06-10
That worked on Firefox RC 2008060309! Thank you!

Going further, the applet I use doesn't have a verified signature (Gallery2 Upload Applet).
I'm wondering if icedtea isn't capable of running unverified signed code.
Can someone verify this? (It's quite late for me, so I don't have the time to check. I also have to get to uploading 1.7GB of pictures now. (They've accumulated from the past couple of weeks because I couldn't figure this out))

---

### Post by vinu76jsr on 2008-06-11
sudo update-alternatives --config java

and select jvm. this way its also easy to switch between jvm's if u have to.

also do

sudo update-alternatives --config javac

and maybe it documentation is available.

sudo update-alternatives --config javadoc

this will work if you have sun-java already installed 

in my case I installed  sun-java and everything worked fine but then when I installed netbeans suddenly Topcoder applet stopped working, I figured out that netbeans install openjdk as a dependency and sun web start stopped working, 
rest normally works and I already told the workaround

---

### Post by TimDuncan on 2008-06-29
removing iced tea worked for me too! Probably best to try that first, then try the other method next.

---

### Post by Duranxl on 2008-07-20
I can´t get it to work..
I uninstalled ICEDtea because i also had this problem..but now i get "install missing plugin"..but then it says "GJCwebplugin" is already installed..
I restarted firefox to no avail!
help:(

edit: i´m on 64bit so cant install java plugin!

---

### Post by Fatfool on 2008-07-20
> **Duranxl said:**
> I can´t get it to work..
I uninstalled ICEDtea because i also had this problem..but now i get "install missing plugin"..but then it says "GJCwebplugin" is already installed..
I restarted firefox to no avail!
help:(

edit: i´m on 64bit so cant install java plugin!
here you go:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by Duranxl on 2008-07-20
> **Fatfool said:**
> here you go:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

i don't wanna use 32bit!:O

---

### Post by Fatfool on 2008-07-20
> **Duranxl said:**
> i don't wanna use 32bit!:O
aww come on, you won't notice a thing if you have the 32 bit and 64 bit of the same version of Firefox.

other than that, you could go bang on sun's door for taking an immense amount of time to get a 64 bit java plugin. its like 5 years and counting now. it is supposed to appear next year in Java 7.

---

### Post by zakad on 2010-07-05
> **Mainlake said:**
> Fought this one long time, and I couldn't get the applets work. Weirdly enough I solved this problem, by uninstalling all icedtea java plugins, and then restarting Firefox and going to the page that was not working. And to my great suprise applet works.

I had the same problem with Ubuntu Lucid and Firefox 3.6.6.  Also, to my great surprise, removing icedtea worked for me too.  Many thanks!

---

### Post by dalmolin on 2010-10-08
Removing icdtea plugin in Lucid did the trick... plus installing the sunjava plugin... thank you!!!!

---

### Post by balaji31d on 2011-01-25
> **Mainlake said:**
> Fought this one long time, and I couldn't get the applets work. Weirdly enough I solved this problem, by uninstalling all icedtea java plugins, and then restarting Firefox and going to the page that was not working. And to my great suprise applet works.


Worked for me too.. Thanks

---

### Post by jalms on 2011-10-01
Simple as it gets: sun-java plugin installed and all icedtea items removed from Synaptics manager.
Natty Narwhal 64 bit and Firefox 7.

---

### Post by oldos2er on 2011-10-01
Closed, necromancy.

---

