---
title: "Install printer PIXMA MP150"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by invigo on 2006-08-25
Dear Ubuntu friends,

I have proudly switched to Ubuntu and DELETED the crapy Windows XP with its viruses, hehe.

I'm still new in this field, therefore i'm experiencing difficulties; but that's normal, since I'm learning a new iconic language.

I just purchased a new printer CANON PIXMA MP150, but I can't get it to work. I have found drivers on this web page: [http://www.turboprint.info/download2.html](http://www.turboprint.info/download2.html)
Unfortunatelly I don't know how to install them and consequently get my printer to work.

Please help!THX

Blash, Slovenia

---

### Post by John.Michael.Kane on 2006-08-25
Save the **turboprint-1.94-4.tgz** file to your desktop.

Click Applications on the top menu click Accessories Open the program named terminal

Step1
Type: 
```
sudo apt-get install libgtk1.2
```

Step2
Type:
```
cd Desktop 
```
Step3
Type:
```
tar -xzf turboprint-1.94-4.tgz 
```
Step4
Type:
```
cd turboprint-1.94-4
```
Step5
Type:
```
sudo ./setup
```

---

### Post by invigo on 2006-08-25
SD-Plissken.

Thank you for your help! I have followed the instructions and it went smoothly. Now I have two icons on my desktop, one is called Turboprint-Setup and the other is Turboprint-Config. When double clicking on the Turboprint-Setup icon, a window occurs stating: ERROR xtpsetup must be run in root mode

Any ideas??

---

### Post by John.Michael.Kane on 2006-08-25
From the terminal try typing

```
sudo turboprint-Setup
```

---

### Post by invigo on 2006-08-25
Unfortunatelly it doesn't work.

Command not found. hmm

---

### Post by John.Michael.Kane on 2006-08-25
Try 

```
sudo ./xtpsetup
```

---

### Post by invigo on 2006-08-25
nope.

I wrote:
1. cd Desktop
2. sudo ./xtpsetup

command not found

---

### Post by John.Michael.Kane on 2006-08-25
Don't do it from cd Desktop.

If your teminal is reading as desktop
Type:
```
cd
```

Now type:
```
sudo ./xtpsetup
```

---

### Post by invigo on 2006-08-25
I wrote cd, like you told me. I was not in desktop; to be sure I wrote pwd and it stated:
/home

then I wrote sudo ./xtpsetup.

But, again: 
sudo: .xtpsetup: command not found

---

### Post by John.Michael.Kane on 2006-08-25
Type:
```
locate xtpsetup
``` 

post back what this reports.

---

### Post by invigo on 2006-08-25
it doesn't report anything at all. Not even "command not found". As if nothing happened

---

### Post by invigo on 2006-08-25
Maybe it's time to give up:) Maybe I should uninstall everything iand try all over again..... What do you think??

---

### Post by John.Michael.Kane on 2006-08-25
invigo I really don't want you have to re-install.however if you think that is the best route for you to start from scratch then that is fine. 

I'm sorry i was not able to get this program to work for you.


Help will be here if you need it.

---

### Post by invigo on 2006-08-25
NO, no, you've been of great help!!! I thought I was too anoying with all my stupid questions and actions. If you think it's better for me not to reinstall, then i'll will not do that. I really don't know where it all went wrong, hehe

Again, thanks 4 all your help, adn if you're willing to proceed, so am I.

---

### Post by John.Michael.Kane on 2006-08-25
Try typing:
```
cd Desktop
```

Then type:
```
locate xtpsetup
```

If it finds the file post back.

---

### Post by invigo on 2006-08-25
Nope. It the same as before, as if nothing happened. Maybe I made a mistake, when i was installing drivers, iwas just clicking next and ok, and so forth. But I recall that there was a window stating that the drivers are installed.

My msn: blazhouse1hotmail.com

Via messenger this could go faster, if it's ok with you. Otherwise we can continue here.

---

### Post by invigo on 2006-08-25
[email]blazhouse1@hotmail.com[/email]

---

### Post by John.Michael.Kane on 2006-08-25
Click on System then Click on Administration then click on printers 

Now click new printer. you should be able to add your printer or see your printer model there.

If not then you may have to start from a clean install.

---

### Post by invigo on 2006-08-25
[ATTACH]14836[/ATTACH]

[ATTACH]14837[/ATTACH]

The printer is recognised, but the driver for PIXMA MP150 is not included in the list. I made screen shots, so you can see it.

---

### Post by invigo on 2006-08-25
I think I found the problem, which I could have noticed if I was more precise. Turbo print is not off charge and I'm supposed to buy a registration key.

[ATTACH]14840[/ATTACH]

[ATTACH]14841[/ATTACH]

---

### Post by John.Michael.Kane on 2006-08-25
It should atleast allow you to print a testpage

Click on System then Click on Administration then click on printers

Now click new printer

When you try adding the printer. look for Canon Turboprint drivers.

Try:
```
sudo updatedb
```

Then:
```
sudo xtpconfig
```

---

### Post by invigo on 2006-08-25
Finally some good news.

I have started from scratch again and at some point clicked add on one of the many windows that kept opening. Mp150 appeared and i double clicked it. I also wrote sudo updatedb and sudo xtpconfig in the terminal and the printer is working now.

However, TurboPrints logo appears on every page I print and bellow the logo they write: To print without this logo, please purchase a license key at [www.turboprint.de](www.turboprint.de)

I tried to scan this print with MP150 using XSane Image Scaner, but It didn't work...

---

### Post by John.Michael.Kane on 2006-08-25
invigo I'm glad your able to print. i'm not sure the scanner function is support yet.

---

### Post by giorgian on 2006-09-13
no! it works for me! i simply used xsane and i got the images...

could it be a matter of permissions?

---

