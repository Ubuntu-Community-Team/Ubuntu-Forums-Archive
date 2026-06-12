---
title: "Purple screen while installing"
date: 2013-09-30
forum: Installation &amp; Upgrades
---

### Post by mike115 on 2013-09-30
Hello everyone I apologize in advance if there is a post out there that solves my problem(s).  I have read a ton before posting but can't seem to figure out what I am doing wrong.  so here is my story 

PC info:
HP ACPI x64-based PC
AMD Radeon HD 6410D Graphics

So I have been trying to set up a dual boot system for Win 8 and Ubuntu.  I Have allocated space on my hard drive, downloaded ubuntu 13.04 (64 bit), mounted it to an 4g usb drive, and checked my download from the grub menu (said my files were good)... however every time I boot from my USB and select install ubuntu I get the ubuntu purple screen for about 7 minutes with periodic "no dvi signal" messages.  It flashes back and forth several times and one of two things happens

1.  no dvi signal stays on and I have to power off and boot back into windows 
2.  ubuntu screen comes back with some static at the top and never gets any further  

Please help... I would really like to get this working.  From everything I have seen ubuntu looks like a great system but I can't get it up and running. 

Any help would be greatly appreciated.  Thanks Mike in Owings Mills

---

### Post by su:bhatta on 2013-10-01
See if following the instructions on this page helps: 

[http://askubuntu.com/questions/16207.../162076#162076]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076")

Seems like 'nomodeset' option will do the trick for you.

Also, you 'may' have to install propriatory drivers once you have completed installtion to get the right screen resolution etc.

---

### Post by coldraven on 2013-10-01
I'm no expert with dual booting with Win8 but I have read on this forum many times about "nomodeset".
Here is a link that may help:
[http://askubuntu.com/questions/207175/what-does-nomodeset-do](http://askubuntu.com/questions/207175/what-does-nomodeset-do)

Also on the purple screen the little keyboard and man icon at the bottom is for manual configuration. Have you tried to click it?
Hope this helps, if not then someone more knowledgeable might turn up.

---

### Post by Bucky Ball on 2013-10-01
> **coldraven said:**
> 
Also on the purple screen the little keyboard and man icon at the bottom is for manual configuration. Have you tried to click it?
Hope this helps, if not then someone more knowledgeable might turn up.

Because if you click it you should get the options to 'Install' 'Try' (should look like the second screen in the link provided by bhattabhishek). Hit F6, choose 'nomodset', continue. Easiest way to do it.

---

### Post by mike115 on 2013-10-01
Even on the purple screen I don't get the keyboard and man.  I have seen it before but I don't see to get that far.  

Anyway I will definitely try the nomodset tonight and report back.  My machine is definitly doing the UEFI boot also so I am reading up on that now also.  

Thanks for the info everyone ... I will let you know what I find

---

### Post by mike115 on 2013-10-01
OK so I got the the nomodeset got me through the instail process.  However at the end when it asked to restart I did and it want strait into windows boot.  guess its time to start digging on that.  Thanks for you help everyone

Update for future readers:

to get nomodeset on I had to edit from my grub menu (black screen with try or instal ubunutu) if you select instal ubuntu and click 'e' you can edit the boot script.  where is says splash quite (or something like that) you replace it with nomodeset.  Here is the link to how I did it [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Hope this helps

---

### Post by Bucky Ball on 2013-10-02
All good. Try boot repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can also install grub to sda (if it's not already) and that should fix also.

Run boot-repair. If it doesn't work, run again and create a boot-info with a link to it here. Thanks.

---

### Post by mike115 on 2013-10-02
> **Bucky Ball said:**
> All good. Try boot repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can also install grub to sda (if it's not already) and that should fix also.

Run boot-repair. If it doesn't work, run again and create a boot-info with a link to it here. Thanks.

Thanks for the info Bucky... I will try this as soon as I can and provide an update.  I tell you having this forum is a life saver:P

---

### Post by Bucky Ball on 2013-10-02
> **mike115 said:**
>   I tell you having this forum is a life saver:P

... and so say all of us! (Well, the majority of us, anyway. ;))

---

### Post by mike115 on 2013-10-02
Great news reboot repair got me going can now dual boot ..... Thanks everyone now I just need to find some time to play

---

### Post by mörgæs on 2013-10-02
Good, please mark the thread 'solved' (as mentioned already in Bucky's signature).

---

### Post by mike115 on 2013-10-03
Well on my way now.  I have finally got my boot issues straitened out and have done all system updates as well as updated my grub to nomodeset permanently.  Still have a couple of questions though. 

1.  My screen seems to be stretch wide and the resolution seems a little off.  I have it set to the highest display settings so maybe this is just what ubuntu looks like on my machine....?

2.  the responsiveness of the commands and search seem to be a little sluggish compared to the you-tube vids I have seen.  I have turned off the amazon search feature, but not sure if there is anything else I should be doing.  I have read many threads at this point related to display and responsiveness but I am not making sense of it.  

Any hints tips or tricks to optimize me set up would be greatly appreciated.  

Thanks

---

### Post by Bucky Ball on 2013-10-04
You should post a new thread with exact details and a descriptive title about your new problem, but ... you have it set to highest display settings? Not sure what that means. Look in the manual for your monitor and set them to the monitor specs. That would be why your screen is stretched: wrong settings. 1366x786 screen then that is what you want, not 'the highest', whatever that is. ;)

But as I say, post a new thread (and a link here if you want) as this support request doesn't relate to your thread title or the rest of the thread. Thanks. ;)

---

### Post by mike115 on 2013-10-04
Thanks again .... I will open a new thread

---

