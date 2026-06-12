---
title: "Reinstalling UbuntuLTS 16.04"
date: 2016-10-26
forum: Installation &amp; Upgrades
---

### Post by apol1 on 2016-10-26
Hello, I need to reinstall my UbuntuLTS 16.04, Ive never done anything  like this but my info is backed up safely and Im ready to go

Heres my hardware information on the machine itself. I am not doing any partitions just yet, just Ubuntu for now. However the reason I am doing this is my OS has completely lost its ability to install any new software, please keep that in mind.

[FONT=Verdana]Video Card: 4GB EVGA NVIDIA GeForce GTX970 GDDR5 video card
Ram: [/FONT]
**[FONT=Verdana]DDR4 Memory[/FONT]**
   [FONT=Verdana]32GB Crucial Ballistix DDR4-2400MHz (4 x 8GB), CAS 16 latency, low voltage

[/FONT]**[FONT=Verdana]Motherboard[/FONT]**

   [FONT=Verdana]Asus X99-A/USB 3.1 Intel X99 based chipset, ATX Motherboard

I also welcome any feedback you have for me :)
[/FONT]

---

### Post by porkchop_001 on 2016-10-26
Hi there. The first thing you need to do is create some form of installation media with the Ubuntu .iso you would have downloaded. I recommend using UNetbootin ([https://unetbootin.github.io/](https://unetbootin.github.io/)) - which is a handy tool that let's you create a bootable USB drive with your .iso on it.

Once that's done, restart your computer and change the BIOS settings to boot into your USB. Once this is done restart your machine again, and you'll notice that your USB will be access fifrst - which, theoretically, should force the Ubuntu installation process to start! :)

The install process is pretty straight forward. If you're dual booting Windows or something then make sure you select that option, the specify how much storage you want each partition (Windows and Ubuntu) to use.

Once the installation process has completed, and you restart your machine again, you'll see a GRUB Boot screen. If you've installed Ubuntu alongside Windows, this is the screen where you'll specify which operating system you wish to use. Otherwise you just pick Ubuntu every time and you'll be throw into the OS instance.

Hope that helps!

---

### Post by apol1 on 2016-10-26
Great! I'll have to borrow another computer unfortunately, what would be your input on using a formatting disk to delete my hardrive and start over? I have an install disk but I get an error when i put it in. I also forgot to mention this machine is not partitioned at all, its only had Ubuntu on it from the start

---

### Post by bearlake on 2016-10-26
If you have a bootable USB/DVD with Ubuntu on it that you want to install, you should be good to go.

You can use the bootable media to partition your HDD to your preference.

---

### Post by paulvha on 2016-10-26
I had similar issue with update from 14.04. I downloaded the ISO file, branded a new DVD, Started the system from DVD and did a complete install. In my case it first tried to update 14.04, and thus not replacing all the files, but as that did not worked stable I choose a complete install in the installation menu.

---

### Post by ajgreeny on 2016-10-26
It might be more useful to you to try and figure out why your OS has completely lost its ability to install any new software.

What output do you get from the command ```
sudo apt-get update
``` and following that ```
sudo apt-get upgrade
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by yancek on 2016-10-26
You are getting advice on the information you have posted.  So as far as we know, you have one hard drive with a broken Ubuntu system on it (you might try getting that fixed as suggested above) and you have no other system on it and you have backed up all your data.  If that is actually the case, boot your install media and select Erase disk and install Ubuntu.  If that is not your situation, you will need to post more information.

You can select to format and partition the disk during the install.  If you already have or had Ubuntu on the drive, it was formatted but format again during the install. You forgot to post the error you get when start the install disk??

---

### Post by apol1 on 2016-10-27
Thx for the help :D I happened to have a CD install disk handy and it worked like a charm

---

### Post by apol1 on 2016-10-27
Thanks for wanting to fix my OS, Ive been trying for months but its a real stumper even for the gurus. I decided to go for the reinstall so i can learn more about the system before tackling a broken OS of that caliber. Thats why I did'nt post any errors, But I love your fix it attitude :)  

Anyway I got my system reinstalled flawlessly thanks to everyones wonderful input. Now I just gotta figure out how to close/delete old threads

---

### Post by apol1 on 2016-10-27
Thanks for jumping in to help me repair my system, but Im afraid Ive taken this road many times in the last few months. Even the experts were left scratching their heads. I got my OS reinstalled no problem though, hopefully I'll have learned more about my OS next time around.

However if you could show me how to delete this solved thread that would be great :)

---

### Post by bearlake on 2016-10-27
> **apol1 said:**
> Thanks for jumping in to help me repair my system, but Im afraid Ive taken this road many times in the last few months. Even the experts were left scratching their heads. I got my OS reinstalled no problem though, hopefully I'll have learned more about my OS next time around.

However if you could show me how to delete this solved thread that would be great :)

You can't delete a thread because it's solved.

Just above your 1st post in this thread, look for "Thread Tools" and select solved.

Glad your problem is solved. :D

---

### Post by QIII on 2016-10-27
Hello!

You can't delete a thread at all.  Only the Staff may remove threads from public view.

We won't do that with a solved thread:  These forums are not only for getting individual problems solved.  They are for enlightening the entire community.  If someone got an answer and solved their problem, but we removed it from public view, the community would be robbed of a bit of information that could help someone else later.

The UF is not an individual effort.  It is a community.

Cheers!

---

