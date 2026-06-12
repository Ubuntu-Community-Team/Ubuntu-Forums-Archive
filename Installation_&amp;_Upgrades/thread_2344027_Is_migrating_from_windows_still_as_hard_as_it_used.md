---
title: "Is migrating from windows still as hard as it used to be?"
date: 2016-11-21
forum: Installation &amp; Upgrades
---

### Post by Ross_Munro on 2016-11-21
OK. A little click-baity. But I tried Ubuntu (from windows) about 7 years ago. I liked it. I wanted to stay with it, I really did. But damn. The problems with drivers and installing any. Little. Thing. All of my peripherals didn't work - printer, speakers, scanner, mic. To do anything seemed like a major learning curve and a day lost in tracking down drivers and installing and... and... And even then, after fixing this and tweaking that and doing this course of tutorials and watching all those youtube vids I still found myself logging out and then back into the windows drive for that one, small, essential program that I needed for which there was no linux alternative. I guess I'm asking for that reassuring pat on the back from those who have recently made the change. A quick there, there, it's much better now, I did it and it was painless - you can too.

---

### Post by cariboo on 2016-11-21
Changed title to remove implied profanity.

---

### Post by Ross_Munro on 2016-11-21
OK. So this isn't starting well. I downloaded the ISO and made a bootable USB and started to install alongside windows but the install couldn't detect any other operating system and wanted to wipe my drive. Any clues would be gratefully accepted.

---

### Post by QIII on 2016-11-21
Hello!

Did you first use the tools in Windows to shrink your Windows partition and create some empty space for your Linux partitions?

When attempting to install Ubuntu, did you choose "Do Something Else" for partitioning?

We'll be here to help, of course!  But it might be helpful to read [this wiki entry]("https://help.ubuntu.com/community/WindowsDualBoot") before you do anything further.  It will probably leave you with more questions than answers.  That's fine.  We'll help answer your questions!  After that, you might just find things go more smoothly.

Cheers!

---

### Post by Ross_Munro on 2016-11-21
I have 42gb available on my windows drive and 560gb available on my data drive. I figured that would be enough. I chose "do something else" from the same screen that was telling me that there is no windows on my computer in the vain hope that that would give me the option to install alongside windows. I set up my bootable USB exactly as described [here. ]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

---

### Post by C.S.Cameron on 2016-11-22
Right click on **Computer** in Start, left click on **Manage**, on the new screen left click **Disk Management**, you will see your hard disk.
If there is no free space, left click on the partition you want to install to and use **Shrink Volume** to provide enough space for your Ubuntu installation.

Now when you get to Something else you will see that free space.

Rufus is good for making the install disk you will use to install Ubuntu.

---

### Post by Ross_Munro on 2016-11-22
Thanks for that, but free space isn't the problem. The installation process tells me that there is no other operating system on my (windows 10) computer! The only option it then gives me is to completely wipe my hard drive and install Ubuntu instead. I don't want to do that, I want a dual install: Windows/Ubuntu so I can satisfy myself that everything I need is available and functioning. So, again, the problem is that the installation process doesn't recognise the windows system that is on my computer.

---

### Post by mastablasta on 2016-11-22
> **Ross_Munro said:**
> Thanks for that, but free space isn't the problem. The installation process tells me that there is no other operating system on my (windows 10) computer! The only option it then gives me is to completely wipe my hard drive and install Ubuntu instead. I don't want to do that, I want a dual install: Windows/Ubuntu so I can satisfy myself that everything I need is available and functioning. So, again, the problem is that the installation process doesn't recognise the windows system that is on my computer.


are you here searching for help or general comments? if general comments then ok. we can do that. : in general Ubuntu will "stick" to most things you throw it at. in other words it iwll work on majority of hardware. there is ubuntu certified website for certified hardware as well. ther eis harxdware that  comes Ubutnu preloaded (it works really well on those).

if you are asking for help then you should provide as much info as possible regarding your situation. see more here: [SIZE=2][https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)
[/SIZE]
when you started you didn't mention the operating system. having win 10 brings a few things with it. such as for example quick boot on windows 10, which if enabled actually suspends (hybernates?!) the computer while reserving the disk for itself. this will ofcourse result in no OS to be seen. you could just overwrite it... :twisted:

then you have't provided you partition setup. is it MBR? is it maybe MS proprietary dynamic partitioning?  we do not know if you use secure boot or not. we also do not know what are your system specs to be able to advise about drivers and such.

if you want to give it only a try you can use pesistency when creating LiveUSB. a 2 GB persistency should be enough to install all drivers into live USb session and see if it all works or not. 

a word of advice if you are using mostly windows programs, it is better to stay on windows. if you are using plenty or majority of opensoruce programs on windows, then transition should be easy sicne you will get most of thing you are already using and some good alternatives for the rest. if you play plenty of games it is better to stay on windows as well. the linux games library is growing quite fast, but for major titles windows is still a better choice.

---

### Post by C.S.Cameron on 2016-11-22
When you select "Something else" in "installation type" does it show both hard drives?

---

### Post by Ross_Munro on 2016-11-22
> ...if you are using plenty or majority of opensoruce programs on windows

Blender, Libre Office, Audacity, gimp, Inkscape, Python, docker, vlc ...  I'm reminded that Audacity doesn't come in a linux version, but I could live without it if there is a half decent open source alternative. And I take your (very slightly condescending) point. I'm aware this is the cafe. The question was, is it still difficult to install Ubuntu. I was hoping to luck upon a couple of recent converts who would say, "No, it's real easy and painless." So, no, I'm not here looking for help. This difficulty arose during the conversation so I'll be moving on now. If I choose to continue I'll do so elsewhere.

---

### Post by Ross_Munro on 2016-11-22
From memory, yes. But I've had enough of shaving the yak for now. If I want to continue I'll find the right forum. Thanks.

---

### Post by ajgreeny on 2016-11-22
> **Ross_Munro said:**
> Blender, Libre Office, Audacity, gimp, Inkscape, Python, docker, vlc ...  [COLOR="#FF0000"]I'm reminded that Audacity doesn't come in a linux version, but I could live without it if there is a half decent open source alternative.[/COLOR] And I take your (very slightly condescending) point. I'm aware this is the cafe. The question was, is it still difficult to install Ubuntu. I was hoping to luck upon a couple of recent converts who would say, "No, it's real easy and painless." So, no, I'm not here looking for help. This difficulty arose during the conversation so I'll be moving on now. If I choose to continue I'll do so elsewhere.
What makes you thing there is no Audacity for Linux?  I have been using it successfully for years on Ubuntu and all the other DE versions that I haver used over those years.

I also note that you have not yet mentioned which version of Windows you have, nor how recent your hardware is, but there is a very real chance if the computer is fairly recent that your hardware and Windows are both UEFI, not an insuperasble problem, but definitely something you, and we, need to know before telling you exactly what to do next.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by ajgreeny on 2016-11-22
*Thread moved to **Installation & Upgrades**.* which is more appropriate for this thread and the problem you have in installing so should be a better fit.

---

### Post by mastablasta on 2016-11-22
> **Ross_Munro said:**
> Blender, Libre Office, Audacity, gimp, Inkscape, Python, docker, vlc ...  I'm reminded that Audacity doesn't come in a linux version, but I could live without it if there is a half decent open source alternative. And I take your (very slightly condescending) point. I'm aware this is the cafe. The question was, is it still difficult to install Ubuntu. I was hoping to luck upon a couple of recent converts who would say, "No, it's real easy and painless." So, no, I'm not here looking for help. This difficulty arose during the conversation so I'll be moving on now. If I choose to continue I'll do so elsewhere.

oh i see. well, it is really easy and painless. :)

especially for single OS. dual boot (as mentioned above) presents a few obstacles when using UEFI and windows 10. it is still easy to follow documentation and deal with them.

win 7 and below using MBR is really, really easy and fast (the whole thing should be over in about 15, 20 mins).

---

### Post by C.S.Cameron on 2016-11-22
I think Audacity has always come with Ubuntu, I've had it for close to ten years.

---

### Post by qyot27 on 2016-11-22
> **mastablasta said:**
> oh i see. well, it is really easy and painless. :)

especially for single OS. dual boot (as mentioned above) presents a few obstacles when using UEFI and windows 10. it is still easy to follow documentation and deal with them.
Unless it happens to be using 32-bit UEFI with a 64-bit processor*: then things get hairy and complicated...fast.  Especially if you want to run a proper installation of 64-bit Ubuntu from an external hard drive or USB, rather than just always using the Live USB.

*like you see on mini-PCs such as the Quantum Byte.

It's not impossible, but it's not simple either.  Although once the worst of it is over, it's fairly easy to mitigate in the future if you have your partitions set up correctly (and you're comfortable using GRUB2 manually).

---

### Post by QIII on 2016-11-22
Since the user has decided to find the "right forum" and has had enough of shaving the yak (for those of you unfamiliar with the with the phrase, it refers to a seemingly useless activity that is sort of an unfortunate requirement to be taken care of before progress can be made on the actual project), I suggest we all go about our business and allow the OP to sharpen their shears.

As this was yak shaving and not an actual request for support and it has already been moved once, we'll just ask the OP to start a support thread when the yak is fully shaven.

Closed.

---

