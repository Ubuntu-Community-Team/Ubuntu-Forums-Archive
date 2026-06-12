---
title: "problem installing ubuntu (black screen)"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by freeddy85 on 2008-01-16
hi, im trying to install ubuntu amd64 on my p5w dh, e6600, 8800gts, 960bf

after the cd boots i push the install\start key and its loadng som linux stuff but after that i just got black screen.:lolflag:

---

### Post by loneshadowcccp on 2008-01-16
got the same problem any help plz?

---

### Post by Lu_Xun00 on 2008-01-16
Yes, I am also having the same issues.  I would like to install Ubuntu on my laptop, but my error coincides with the other one's up there.  Any help would be greatly appreciated.

---

### Post by Taters on 2008-01-16
Hah.... same error.

Does your screen turn off? Mine does....

(8800gt)

---

### Post by freeddy85 on 2008-01-16
> **Taters said:**
> Hah.... same error.

Does your screen turn off? Mine does....

(8800gt)

Nope its just black but doesnt shut down, strange that they cant come up with a decent solution ore maby a update on this.. because it seems to affect many people. and i realy want to try ubuntu:(

---

### Post by rappin05 on 2008-01-16
I had it that it turns off, then i took out my video card and used onboard, which solved the turn off problem but now it goes to the ubuntu loading screen then freezes at a black screen with a flashing cursor. 
Computer:
Intel Core 2 duo 6600 64 bit capable
evga e-geforce 8600 GT
2 gb memory 
basic intel motherboard
ubuntu version attempted: 7.10 64bit version

---

### Post by Tony4324 on 2008-01-17
Hi All,

This is my first help to contribute.

I am also new to Unbuntu, like only 2 days into it.

When I installed Unbuntu I also had the black screen, the screen having gone into "standby", yellow light flashing. The first few times I thought I had commenced the install incorrectly, so I recommenced the install. On install attempt number 5 or 6 I accidentally pressed the "Enter" and Ubuntu install kept on going to ultimately install. 

So as an idea just for the exercise at the point of the black screen press enter. Why, I can not answer but in my case it worked!

Tony.

---

### Post by Lu_Xun00 on 2008-01-17
In a desperate attempt to succeed at installation, I indeed attempted the method above, but to no avail.  Still got the black screen.  I've always had trouble with Linux operating systems, but I thought this one was going to be less of a headache......

---

### Post by Lu_Xun00 on 2008-01-17
Could we please get a response?  I would like to use Ubuntu (if possible) soon.

---

### Post by freeddy85 on 2008-01-18
Just forget buggy ubuntu and install mandriva ore opensuse.
[http://www.opensuse.org/](http://www.opensuse.org/)
[http://www.mandriva.com/](http://www.mandriva.com/)

---

### Post by Partyboi2 on 2008-01-18
Have any of you tried the alternate cd to see if that works?
[alternate cd]("http://releases.ubuntu.com/releases/7.10/")

---

### Post by lswest on 2008-01-18
have you tried starting the liveCD in safe graphics mode?
mine wouldnt boot either, til i used the safe graphics mode with my nvidia 7150m/630m chip.  The default nv drivers just don't seem to work with some of the newer cards.  However, vesa always works so you can always install the nvidia drivers then.

---

### Post by redcrayon on 2008-03-23
I Had this issue too,
amd64, 3200+, 8600gt, 2gb ram.

After choosing install from the boot menu, the screen would quickly flash a little text then turn off, i decided to leave it for a few minutes...   after about 2 mins of no activity the cd started spinning up and about 2 mins later it had booted to the desktop (live cd)

hope this helps someone....


peace.

---

### Post by IanW on 2008-03-23
This is a known problem with Nvidia cards.

You need to remove the words "quiet splash" from the boot line (f6 on live cd menu).
Once installed, you then need to remove the same words from GRUB by using
```
sudo gedit /boot/grub/menu.lst
```

---

