---
title: "Rebooting back"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by Minti on 2007-04-08
I heard about Linux and wanted to try it out. Then I downloaded Ubuntu, burned it on a CD and began installing, but when it was on 72% it said there wasn't enough disc space left (and I gave it 35 GB), so I thought 'oh well' and tried rebooting, took the CD out and waited, but then it said I had to put a CD in to start-up. Currently I can't get on my Windows XP or my Linux and I can only use the CD for anything. I found a CD for Windows XP, but it says that's it's only for recovering, and when I put it in, it wants to install a lot of things. I've also tried to look in the BIOS in setup and even said it shouldn't check for CDs, but it still does.

Please, I need help quickly so I can use my computer again!

---

### Post by tgm4883 on 2007-04-08
Without helping you to try and fix the linux problem.

Did you leave your windows partition intact?  If so pop in your windows cd, boot to recovery mode and type in 

```
fixmbr
```

ps, not sure this will work with a restore cd.

---

### Post by Minti on 2007-04-08
First off, I only split the drive that actually was empty, so I have left it intact. And when I put the CD in it first reads some files, then gives me 3 options: Install Windows XP, Recover and Cancel.

When I press Recover, it first asks for which program (or something, can't quite remember) in C:\Windows it should use, and it wants a number between 0 and 9, so I just pressed 1, then it asks for the administrator password, and I tried mine, but it said it didn't work! (Now I'm not good with Windows, so I don't know what that password is, I just used that to the Administrator-user on the computer). I have no place to enter that code.

I hope I can fix this soon..

EDIT: I got it working, I just had to leave the password empty, and when I entered that code it said WARNING and Are you sure? I pressed Y and it was happy, but when I wrote exit to leave and restart, it came back, and said again that it needed a boot disc.

---

### Post by Minti on 2007-04-09
Just wanted to say that I fixed this.

I ran the install.exe on the Linux CD again and changed the files there, since the installer had changed stuff to make it fit Linux (It had made hda7, a etc32 (I THINK it was 32, don't blame anything on me!) drive boot, so I made hda1 boot instead and deleted the etc32 and the other file (to tired to remember names after 6 hours of work on it in the middle of the night)).

---

