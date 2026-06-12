---
title: "Gutsy Gibbon Java issue"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by DGentry on 2008-01-27
I'm having a tough time getting Java to work on this machine.
I went to a website that said I needed java installed and it had like 4 selection boxes.

Instead of reading and really finding out what I needed I just selected a box and it installed.

I'd go back to the site and it would come saying I needed java installed and the same boxes would display.
I'd check the next one down and get the same thing as before.

I get this output when I run:
sudo update-alternatives --config java

administrator@ubuntulamp:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/bin/gij-4.2
*         2    /usr/bin/cacao

Press enter to keep the default[*], or type selection number: 
administrator@ubuntulamp:~$ 

Is there a way to just un-install all this and start over?

---

### Post by taurus on 2008-01-27
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```
Now, select the latest version, 1.6 (or 6), from the list.

---

