---
title: "Stuck at load screen during Kubuntu install"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Xone on 2008-04-11
I seem to be getting a weird occurrence during my Kubuntu install on my new computer.  It starts installing and then gets stuck in a shell screen.  It writes ubuntu@ubuntu: on the screen and I can type in commands.  

It looks like time 2:05 of the following video:
[http://www.linux.com/var/uploads/Media/flash/117051-1.swf](http://www.linux.com/var/uploads/Media/flash/117051-1.swf)

I couldn't find a similar error elsewhere.  Other info:  I've tried to install Ubuntu 7.10 and 6.06 as well, but both hang.  I'm a complete newbie, so I don't have much experience with linux. 

One other issue is that I can't seem to use the arrow keys to make a choice at the screen where you choose:  Start or install Kubuntu, Start Kubuntu in Safe mode, etc etc

Thanks for any forthcoming help!

---

### Post by Partyboi2 on 2008-04-11
When you downloaded ubuntu did you check that the [md5sum ]("https://help.ubuntu.com/community/HowToMD5SUM")matched? Also best to burn cd at a low speed like x4 or less to prevent corruption if you have not already done so.

---

### Post by Xone on 2008-04-11
I did check that the md5sum of the iso matched the one provided at Ubuntu Hashes, but I am having trouble checking the md5sum of the cd I burned. (I'm on a mac, and I couldn't use the method for checking the md5sum for cd's provided on the link you gave).  

However, I burned the cd at the absolute lowest burn speed (1x).

---

### Post by Xone on 2008-04-11
Ok, so I managed to get past the initial load screen with the prompt using another version of Kubuntu (one which someone else successfully installed), but soon after that screen I get stuck with a flashing cursor and an otherwise black screen.

---

### Post by Partyboi2 on 2008-04-11
> **Xone said:**
> Ok, so I managed to get past the initial load screen with the prompt using another version of Kubuntu (one which someone else successfully installed), but soon after that screen I get stuck with a flashing cursor and an otherwise black screen.
When you are at the kubuntu main menu screen press F6 to change boot options. At the end of the kernel line you will see the word "splash" change "splash" to "nosplash" and then press enter. Hopefully this will allow you to see where it is hanging.
Another thing to try is to choose option 2 at the kubuntu main menu "Start Kubuntu in safe graphics mode".

---

