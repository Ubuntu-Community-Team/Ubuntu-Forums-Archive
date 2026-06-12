---
title: "How do I boot 8.10 Installation With Noapic"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by Final Version on 2010-01-04
I'm required to use this to use the live cd, and just to install it. But I can't find the option to use it when booting.

---

### Post by yogesh.girikumar on 2010-01-04
Hi Final Version,


   	Just press F6 when the Live CD options are displayed. Then use arrow keys to select "noapic"




[IMG]http://img704.imageshack.us/img704/8168/screenshotzg.png[/IMG]

   	



Yogesh.

---

### Post by Final Version on 2010-01-04
I mean after I've installed it and I'm to select which os I want from Grub.

---

### Post by yogesh.girikumar on 2010-01-04
Hi,
       Yes, it is possible to do that.

       1. When the system boots, press Esc key during the countdown (i.e. when it says grub is loading). 

2. Select the option that says Ubuntu x.xx kernel-x.x.xx-x-generic and press 'e' without quotes 

[IMG]http://img191.imageshack.us/img191/8148/screenshotcs.png[/IMG]


3. Use arrow keys to go down the list to the option that begins with 'kernel' ( the second ) and press 'e' again without quotes.


[IMG]http://img231.imageshack.us/img231/8027/screenshot1.png[/IMG]

4. at the end of the line just leave a blank space and type 'noapic' without quotes.

[IMG]http://img191.imageshack.us/img191/7329/screenshot2c.png[/IMG]


5. Hit esc key to go back to the options and press 'b' without quotes to boot.


You can check this by doing


```
dmesg | grep apic
```      and to check if boot params have been passed as required, do:


```
cat /proc/cmdline
```You can also refer to this link which you might find useful.
[URL="http://ubuntuforums.org/archive/index.php/t-148761.html"]
  http://ubuntuforums.org/archive/index.php/t-148761.html[/URL]

---

