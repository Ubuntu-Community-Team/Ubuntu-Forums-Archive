---
title: "Change to directory where Drives are Held"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by jobrimal on 2012-01-19
:confused:[FONT="Garamond"]*[SIZE="3"][/SIZE]*[/FONT]
**
     Help!! I have recently changed to Ubuntu 11.10 from 10.4No prob except
insalling my Brother DCP-110C Printer:(:( have downloaded the relavent
lpr and cupswrapper drivers),No Prob. However in the insall phase, Brothers
instruct to change to directory  where drivers were down loaded to.HERE
IS THE PROBLEM  In the terminal I enterd
                                        cd downloads
                                   ANS.no such file or Directory.!!!  As I can see the drivers  in the DOWNLOADS directory I am stumped!!!!??? In ubuntu 10.4 I had no prob Insalling my printer:(

---

### Post by WthIteh on 2012-01-19
Not sure that you are pasting exact commands or not.
However, file names in Linux are case-sensitive.
So```
cd Downloads
```is OK not```
cd downloads
```.

---

### Post by jobrimal on 2012-01-20
Thank you for your prompt reply to this oldie!!:)
 I enterd cd downloads 
 I then entered  sudo mkdir /var/spool/lpd
and rx(sudo)password for brian  
 I entered my password (the same one I have used in ubuntu for 5 years)
rx  answer Sorry try again.  I do this three times!
Then the stupid machine  "sudo 3 incorrect pasword attempts"

  So Wthiteh I am still stuck:(

---

### Post by lukeiamyourfather on 2012-01-20
> **jobrimal said:**
> Thank you for your prompt reply to this oldie!!:)
 I enterd cd downloads 
 I then entered  sudo mkdir /var/spool/lpd
and rx(sudo)password for brian  
 I entered my password (the same one I have used in ubuntu for 5 years)
rx  answer Sorry try again.  I do this three times!
Then the stupid machine  "sudo 3 incorrect pasword attempts"

  So Wthiteh I am still stuck:(

The 'sudo' password is the same as the password you use to login.

---

### Post by jobrimal on 2012-01-21
[FONT="Garamond"][SIZE="3"]**[/SIZE][/FONT]:D

Thank you lukeiamyourfather:o

 the password that I used,was the same as I use to log in with:(

---

