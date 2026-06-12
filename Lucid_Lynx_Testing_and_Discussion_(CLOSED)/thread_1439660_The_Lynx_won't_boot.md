---
title: "The Lynx won't boot"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uubnewb on 2010-03-26
Hi all,

I installed the Lucid Lynx earlier today first booting from a live USB drive.

When booting from the USB drive everything works fine and installing Lucid Lynx via the live session went well.  However, after the installation, when I wanted to boot from my hard drive, I got a message stating that the partition I'm trying to access does not exist.

I tried re-installing Lucid Lynx but got the same problem.

Does anyone know how to fix this?

PS:  I don't know if this makes any difference, but I'm using an older version of Grub since Grub2 gave me some problems with my duel-boot setup.

---

### Post by Dragon42 on 2010-03-26
Hi,  Dont mean to take over your question, but I am having similar issue.  I updated last night and now I get a blank screen when restart.  After GRUB it has some text and then blank.  No messages though.  Good luck and I will watch this thread

---

### Post by Uubnewb on 2010-03-26
Dragon42, the text you get after Grub, is it by any chance the same as this:
```
error: no such device: xxxxx.xxxxx.xxxxx.xxxx
```

If so, I might have found a solution.  After your message I thought the problem might be in Grub, rather than the operating system itself.  That reminded me of [this site]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") someone told me about when I ran into some trouble with Grub back when Ubuntu 9.10 came out.

I'm going to try ```
sudo update-grub2
```.  I'll let you know if that solved my problem.

---

### Post by Uubnewb on 2010-03-26
OK, my problem is solved.

Unfortunately I couldn't use ```
sudo update-grub2
``` while booting from a live disc, so I booted up in Ubuntu 9.10 (which is also on this pc) to run the command.  Now everything is working again :D .

---

### Post by Dragon42 on 2010-03-26
I will try it tonight if I have time.  I tried booting with "rescue" and same thing came up (nothing).  I will try to see if i can at least get a command line to do what you suggested.  I was thinking about using a live cd I have to recover from my eagerness to use the new beta lynx.  Glad to hear you are up and running.  I might just do a fresh install and chalk it up to lesson learned.  Maybe i will turn one of my old computers into a test unit for beta stuff and experiments. Oh, and I am not sure if that line of text came up.  I don't think it had error in the line.  Thanks

---

### Post by Dragon42 on 2010-03-27
Kinda fixed.  Still doesn't boot right, but I used an older kernel to boot after some issues.  I think something happened during the update.  Going to do a fresh install and wait for official release.  Not a big deal, I am used to doing fresh installs constantly with my old OS.  Thanks

---

