---
title: "Installing drivers, a pain."
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Hmmster on 2010-02-06
It would be good to start with reading [http://forums.wow-europe.com/thread.html?topicId=12424324064&postId=124231760951&sid=1#0](http://forums.wow-europe.com/thread.html?topicId=12424324064&postId=124231760951&sid=1#0) , since that explains my problems.

Getting the 190.53 drivers it awful, i need to close down X, how do i do that?
CTRL + ALT + backspace doesn't work. Neither does Ctrl + alt + f1.

But then i remember, in 9.04 i had nVidia's driver installer instead of ubuntu's on my computer. Can i get that again? That one probably had 190.53 on it.

---

### Post by darkod on 2010-02-06
Have you tried EnvyNG? I think you can find it in Software Centre. That helps download and handle ATI and Nvidia drivers.

---

### Post by Hmmster on 2010-02-06
Downloading it now.
Wait, how do i USE it?

---

### Post by darkod on 2010-02-06
I'm not exactly sure where does it appear in the menu. I think Applications-System Tools. Check there first. Or Applications-Graphics (very unlikely).

Start the program and it will show available drivers and they have tick boxes whether used or not. I guess you just tick the box you want.

I've only used it in text mode but it did the trick for my ATI HD3200. It runs in text mode in terminal with:
envyng -t

---

### Post by Hmmster on 2010-02-06
+-----------------------------------------------------------------------------+
 | Number | Candidate Version  | Installed Version  | Compatible | Recommended |
 |-----------------------------------------------------------------------------|
 | 0      | 185.18.36-0ubuntu9 | 185.18.36-0ubuntu9 | +          | +           |
 |-----------------------------------------------------------------------------|
 | 1      | 173.14.20-0ubuntu5 | -                  | +          | -           |
 |-----------------------------------------------------------------------------|
 | 2      | 96.43.13-0ubuntu6  | -                  | +          | -           |
 +-----------------------------------------------------------------------------+


Are all i can choose from, but i want 190.53. D:

---

### Post by darkod on 2010-02-06
Can this help:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Hmmster on 2010-02-06
Well, i can get it from there. But then i get problems with it saying i need to cllose down X.

---

### Post by darkod on 2010-02-06
Well, I have no idea about that. There are instructions to install in Additional Information, but I don't know more.
One option you could try, is download the driver you need (32bit or 64bit), place it in your home folder.
Then reboot and from the grub menu select the Recovery Mode entry. That doesn't start X as far as I know, you'll only get command prompt. Because you know the driver is in your home folder just run it with ./filename.run (I think the instructions say you run it like that).

No need to close X when it's not running at all. Hopefully it will work.

---

### Post by Hmmster on 2010-02-06
Grub menu? o_o

---

### Post by darkod on 2010-02-06
> **Hmmster said:**
> Grub menu? o_o

When you boot the computer doesn't it show the grub menu? If you have only ubuntu, it wouldn't. For 9.10 you need to hit Esc to get the menu but you have to be quick after the BIOS finishes and before it actually starts loading ubuntu. It will say like:
Ubuntu 2.6.31-14 (recovery mode)

PS. If Esc doesn't work try with Shift too. I'm mixing them up, one was for 9.04 the other for 9.10. :)

---

### Post by SnowRider on 2010-02-06
nvidia 190.53 or better yet nvidia 195.30 is available in synaptic.Make sure you have nvidia-190.53-kernel-source & nvidia-190.53-modaliases installed.

---

### Post by Hmmster on 2010-02-06
The higest i can find in Synaptic is 185. :/

---

### Post by SnowRider on 2010-02-06
I have nvidia PPA enabled from [launchpad.net/~nvidia-vdpau/+archive/ppa]("launchpad.net/~nvidia-vdpau/+archive/ppa")

---

### Post by Hmmster on 2010-02-06
I feel really stupid now, but how do i enable that? :/
I mean,           [B]ppa:nvidia-vdpau/ppa is too short to be added to software sources.
EDIT:
Oh, tere's a dropdown menu. :P No need to answer my previous question.
[/B]

---

### Post by SnowRider on 2010-02-06
Click on the link I posted...click Technical details about this PPA.A dropdown menu will guide you through. Don't forget to run ```
sudo apt-get update
``` after.

---

### Post by Hmmster on 2010-02-06
Did you read my edit? <.<
Well, i got the drivers. But it didn't help. Thanks anyway!

---

