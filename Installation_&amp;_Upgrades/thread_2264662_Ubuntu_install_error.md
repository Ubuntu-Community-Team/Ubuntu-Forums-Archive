---
title: "Ubuntu install error"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by andrew197 on 2015-02-09
Hi there!

So i've searched the forums for an answer to my problem but i didn't found any... 

So here it goes... i've had a windows 8.1 before and i had an error with the os and it was really annoying and i decided to switch to Linux Ubuntu. I have to say that i am a BRAND NEW user to the linux world and i don't really have any idea what i'm doing. I made an Ubuntu LiveUSB and i've entered the live session and clicked on the install ubuntu app.
The instalation was a success and at the end it promted a message that asked me if i still wanted to try ubuntu or restart in order to complete the instalation, so i restarted my laptop and it didn't do nothing, it only showed me some options to select from and they were "Try Ubuntu" "Install Ubuntu" "OEM install for manufactures" and "Check disk for defects". This is my only laptop, i am currently posting this from the liveUSB so please help. 

This is an image of the screen after i restarted the laptop.
Ubuntu won't boot after install...

[ATTACH=CONFIG]259853[/ATTACH]

Regards, 
Andrew!

---

### Post by andrew197 on 2015-02-09
I am totally new to the Linux world and i can't really figure it out on my own, so please help!

After i install Ubuntu from the liveUSB my laptop won't boot from the hdd, even though the Ubuntu installer said it installed successfuly.
I have no idea what to do next... if i have the liveUSB still connected it will boot from it, when i manually select the hdd it just gives me this screen : 
[ATTACH=CONFIG]259859[/ATTACH]... and after a few seconds it will show me the boot devices :
 [ATTACH=CONFIG]259857[/ATTACH]

When i restart my laptop from the liveUSb and the usb still connected it shows me this screen : 
[ATTACH=CONFIG]259858[/ATTACH]


I don't know what to do, please help!

My laptop is Lenovo IdeaPad Z570 Intel i5, nvidia geforce 540M 4GB ram

Thanks in advance, 
Andrew!

---

### Post by Penguin360 on 2015-02-09
Just curious, before you restarted your computer, did you remove your USB drive?

---

### Post by andrew197 on 2015-02-09
i tried everything, removed the usb, i left it in...everything i could've done i did.

---

### Post by TheFu on 2015-02-09
Please boot of a liveCD/USB flash drive, install the **boot-repair** OR boot-info tools, and run them.
If boot repair doesn't work, then it will create a URL - please post that back here.

Basically, it gathers facts for review by the experts.

---

### Post by andrew197 on 2015-02-09
after i successfuly install ubuntu and restart it shows me this with the live usb in : 
[ATTACH=CONFIG]259861[/ATTACH]

if i remove the usb it shows me this : 
[ATTACH=CONFIG]259862[/ATTACH]

and after a few seconds it gets me to the boot device screen : 
[ATTACH=CONFIG]259860[/ATTACH] and if i select the hdd it shows me the second screen again.

---

### Post by Penguin360 on 2015-02-09
So what happened when you chose to boot from HDD in the boot menu?

---

### Post by andrew197 on 2015-02-09
I think this is it, i took it directly from the boot repair window after it finished but it said that boot repair was successful :

[http://paste.ubuntu.com/10143482/](http://paste.ubuntu.com/10143482/)

---

### Post by andrew197 on 2015-02-09
if i select the hdd it will show me again this screen : 
[ATTACH=CONFIG]259865[/ATTACH]

and after a few seconds it loops back to this screen : 
[ATTACH=CONFIG]259864[/ATTACH]

---

### Post by Penguin360 on 2015-02-09
Check if this helps:

[http://ubuntuforums.org/showthread.php?t=2234007&highlight=Intel+UNDI+PXE](http://ubuntuforums.org/showthread.php?t=2234007&highlight=Intel+UNDI+PXE)

---

### Post by TheFu on 2015-02-09
First things first - was boot-repair actually successful or not? Try it if you haven't.

---

### Post by andrew197 on 2015-02-09
the soulution that guy used needs a liveCD and i have a USB...and i tried entering the first command from the soultion and it says "you need to be rooted".

---

### Post by andrew197 on 2015-02-09
Screenshot after i ran boot repair : [ATTACH=CONFIG]259866[/ATTACH]

---

### Post by TheFu on 2015-02-09
I think you misunderstand.

Can you boot the system now without the flash drive?  Did boot-repair actually fix anything?

---

### Post by Penguin360 on 2015-02-09
Well, it beats me. Sorry. Maybe someone else here can give you more help. But you might want to post your laptop's specs so people can better help you.

---

### Post by andrew197 on 2015-02-09
no, it can't boot the system from the hdd.

---

### Post by andrew197 on 2015-02-09
Ok, my laptop is a Lenovo IdeaPad Z570 with Intel i5 4GB RAM Nvidia Geforce 540M

---

### Post by slickymaster on 2015-02-09
Threads merged.

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

### Post by andrew197 on 2015-02-09
anyone still has any ideas of what is going on?

---

### Post by andrew197 on 2015-02-09
I really need help, this is my only laptop and i don't have access to another one...this is urgent.

---

