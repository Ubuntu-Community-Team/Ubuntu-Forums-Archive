---
title: "No boot after upgrade to 11.04"
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2012-04-11
I upgraded from 10.02 to 10.10 to 11.04. The first upgrade went fine. The upgrade from 10.10 to 11.04, left me unable to boot. I tried booting from from a 10.10 cd, and I tried booting from the f12 key and drop down selections. Nothing has worked. Suggestions anybody?

---

### Post by drs305 on 2012-04-11
We need a lot more information before we can give you specifics. 

If you are at a grub rescue prompt, try using Boot Repair to fix the boot files. The link is in my signature line.

Otherwise, please give us more information about what is happening. Multiple upgradges can be very difficult to troubleshoot (and fix). 

If Boot Repair doesn't fix things, it has the ability of running the boot info script, which can give us details about your system.

---

### Post by lakelovers on 2012-04-11
I get a bios prompt and the f12 prompt (both on the same screen), then a black screen. I can bring up the f12 options but have been unable to get any of them to work. I can get the bios screen to work but that doesn't get me anywhere. I have a 10.10 cd,which I have tried to boot from but I get a black screen with that also. Very frustrating. I've used Linux and Ubuntu for years. every upgrade has been problematic.

Edit: I can just barely seen the log-in screen which is black with a faint image of the log-in prompt.

---

### Post by drs305 on 2012-04-11
I'll throw a couple of things out. 

First, if you last installed 11.04 if possible it would be good to get a copy of the 11.04 LiveCD. If Grub 2 is the problem the version is different enough from previous versions that installing files from a previous CD may not work.

Second, when trying to boot from the LiveCD, you can try pressing F6 to display the booting options. F6 again will reveal some boot options which may help. I'd try 'nomodeset' first, since the black screen tends to suggest a video driver problem.

If you can get to the Grub menu (by holding down SHIFT if necessary), pressing 'e' to edit the menuentry and replacing "quiet splash vt.handoff=7" with "nomodeset" may allow booting so you can install a video driver. After using the cursor/DEL keys to make the change in the menuentry, press CTRL-x to boot.

---

### Post by lakelovers on 2012-04-12
I did a fresh install of 11.10, and it fails to boot. I guess I'll just have to throw the computer out and start new. I don't understand why I can install 10.10 and it works but if I try to move up I cannot get even a fresh install to work. I got to the screen where I refresh grub but that didn't fix it. I'm still looking for ideas.

---

### Post by darkod on 2012-04-12
It might be a video driver issue.

Check the sticky on the top of the threads, it has some suggestions to troubleshoot video issues.

Also, try googling for your video card and 11.04 and 11.10 for known issues.

---

### Post by lakelovers on 2012-04-14
Thank for suggestions. I'm still struggling. I got to the screens with different boot options but I don't know the terminology or how to make the right selection.

**New Info**
I back tracked to 10.10, which works fine, but I would still like to move up to 11.10, which doesn't work. I have an ACER
ASPIRE, with 15.6" HD LCD, and an Acer Nplifyt 802.11b/g/n/ wireless network connection. The problem remains that after installing 11.10, it that it will not boot, or it boots but there is no screen image. I am a long time user of Ubuntu but I am not computer intelligent so I don't know how to work my way through the terminology to make the correct selections advised on the recovery screen. Can anybody give me a 1-2-3 easy step to solving my 11.10 problem?

---

### Post by lakelovers on 2012-04-15
I read the sticky at the top of the thread. I'll print it off and see if I can weed my way through it. It looks like a massive challenge and I don't know if I'm smart enough. I don't understand how/why some Ubuntu versions install and upgrade easily other have traps like 11.10. Wish me luck.

---

### Post by lakelovers on 2012-04-19
Life is too short. I've perused the instructions in the "stickies", tried to follow them, to no avail. I have been happy with Ubuntu & Linux over the years but I have come to the end of my wits. When it gets so complicated that the an average guy can't get it to work then it's way too complicated. And I thought Ubuntu was moving toward an easier life. As I've said 10.10 works but it's out of date. Upgrades don't work on my computer, a one-year old Acer.

---

### Post by darkod on 2012-04-19
One thing you could do is install the 12.04 LTS when it comes out. Check if it works in live mode first.
Starting from now, LTS versions will have 5yrs support even for the desktop OS. If it works as you like it, you will have updates for 5yrs and don't have to change it unless you want to.
For long term it's best to stick with LTS releases anyway.

If you are in a real hurry, you can install the 12.04 Beta right now, but since it's still in development it might disappoint you if something doesn't work out of the box in the Beta.

Also, LTS releases usually have best compatibility.

---

### Post by lakelovers on 2012-04-20
Thanks. That's what'll do.

---

### Post by lakelovers on 2012-04-26
Here I go again.. .

12.04 was released today 4/26, so I downloaded it and burned a dvd,and I get this error message when I try to boot it: E sub- process gpgv returned an error code(22) W: signature verification failed for media/ubuntu 12.04 LTS i386/dist/precise/Release.gpg

What do I do?

---

### Post by lakelovers on 2012-04-30
Iam defeated. Nothing works. Now l can't
even get 10.04 back.

I'm getting a very dark screen on which I can just barely see menu prompts (user name etc.) I'm guessing that the problem I'm having is the video instructions. I've looked at the various solutions for that but I'm baffled. Can anybody give me a Dummy's Guide to fixing screen resolutions etc. This is what's wrong with Ubuntu and Linux. With of all the variants in hardware I guess it's nearly impossible to make a fit for everything. But I would think that a fresh install would/should work with every  system. I've been doing fresh installs and still can't make anything work. I'd almost give my right arm for fix. I have only Ubuntu on my computer . .  . that ought to be worth something.

---

