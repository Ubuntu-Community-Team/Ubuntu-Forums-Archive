---
title: "Ubuntu 10.04 LTS stucked in 57%"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by nsamba on 2012-01-18
Hi. I tried to install Ubtuntu 10.04 LTS on my PC with the ISO I burned from ubuntu's webpage. Everything was fine, untill it got stucked at 57%, displaying the messages "Copying files" and "Installation is about to finish".
I went out for three hours, and when I came back, it was still stucked at 57%.
I tried to install it again, but the same thing happened. What can I do?

---

### Post by WasMeHere on 2012-01-18
Welcome to the Ubuntu Forums, nsamba,

If you give us more information about your PC, it will be easier to help.

For example: Do you keep another operating system? Could it be that your hard drive is full or almost full?

Can you run a live session from the CD? Test Ubuntu (instead of installing it directly?

Have fun finding out about Ubuntu :-)
Olle

---

### Post by nsamba on 2012-01-19
> **Olle Wiklund said:**
> Welcome to the Ubuntu Forums, nsamba,

If you give us more information about your PC, it will be easier to help.

For example: Do you keep another operating system? Could it be that your hard drive is full or almost full?

Can you run a live session from the CD? Test Ubuntu (instead of installing it directly?

Have fun finding out about Ubuntu :-)
Olle

Thanks Olle! Actually, I don't have any other OS on my PC. The hard drive is empty.

I wanted to try running Ubuntu from the live CD but I lost it, and a friend gave me his Ubuntu 11.10 CD, so I'll try with that one.

I'll tell you how everything worked out. Thanks again!

---

### Post by WasMeHere on 2012-01-19
Good luck running a live session with Ubuntu on your computer!

Please come back and give some more details about the computer:
- motherboard
- cpu
- ram
- graphics
- hard drive

Knowing these data makes it easier to suggest what version and flavour of Ubuntu to suggest.

If the live session works, please post the result of the following commands in a terminal window
```
sudo fdisk -lu
```
```
df
```
```
gksudo lshw | less
```

Maybe your friend (who gave you the Ubuntu CD) can help you, otherwise, feel free to ask small as well as big questions here!

---

### Post by nsamba on 2012-01-19
> **Olle Wiklund said:**
> Good luck running a live session with Ubuntu on your computer!

Please come back and give some more details about the computer:
- motherboard
- cpu
- ram
- graphics
- hard drive

Knowing these data makes it easier to suggest what version and flavour of Ubuntu to suggest.

If the live session works, please post the result of the following commands in a terminal window
```
sudo fdisk -lu
``````
df
``````
gksudo lshw | less
```Maybe your friend (who gave you the Ubuntu CD) can help you, otherwise, feel free to ask small as well as big questions here!

I tried the live CD, and everything went ok, and I could finally install Ubuntu 11.10 on my PC. Everything seems to work fine, but here you have my PC's details, if maybe you think another version would be more appropiate:

Motherboard: Gigabyte H55M-S2
CPU: Intel Core i5 (dual core, 2.7GHZ)
Ram: 4GB DDR3
Graphics: Intel Graphics HD (on-board)
Hard drive: Western Digital SATA3 500GB.

It's seems like, for some reason, I couldn't install 10.04 LTS, but I had no trouble with 11.10

---

### Post by WasMeHere on 2012-01-19
> **nsamba said:**
> I tried the live CD, and everything went ok, and I could finally install Ubuntu 11.10 on my PC. Everything seems to work fine, but here you have my PC's details, if maybe you think another version would be more appropiate:

Motherboard: Gigabyte H55M-S2
CPU: Intel Core i5 (dual core, 2.7GHZ)
Ram: 4GB DDR3
Graphics: Intel Graphics HD (on-board)
Hard drive: Western Digital SATA3 500GB.

It's seems like, for some reason, I couldn't install 10.04 LTS, but I had no trouble with 11.10

Well, your computer has power enough for 'vanilla' Ubuntu with Unity, so if you are happy with it, just continue. You may also try (from a live CD) Kubuntu (with KDE,another advanced desktop environment). I think you need not consider Xubuntu, Lubuntu or some older version, because those are for less powerful computers or older computers.
--
We need not find out why Ubuntu 10.04 LTS didn't work, maybe because it is too old to recognize some hardware in your computer. Its software is updated, yes, but the kernel is old (except for security updates).

So have fun finding out about your new Ubuntu operating system :-)
Olle

---

### Post by Quackers on 2012-01-19
Maybe the 10-04 disc was corrupt (or the downloaded iso file that was burned to it).

---

### Post by nsamba on 2012-01-19
> **Quackers said:**
> Maybe the 10-04 disc was corrupt (or the downloaded iso file that was burned to it).

That's exactly what i thought, but when that happens, Brasero displays a message saying that something went wrong (I had to burn the ISO twice because the first time, it said that it failed burning the ISO)

---

### Post by Quackers on 2012-01-19
If you still have the iso file that you downloaded it may be an idea to check the md5sum.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by nsamba on 2012-01-19
> **Quackers said:**
> If you still have the iso file that you downloaded it may be an idea to check the md5sum.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Good idea! I'm still a newbie at this :P

---

### Post by Elfy on 2012-01-19
IF the iso you downloaded was not right then brasero would not know ;)

slow piskie :D

Though if you used a torrent to get the iso it should be ok.

---

### Post by Quackers on 2012-01-19
> **nsamba said:**
> Good idea! I'm still a newbie at this :P

We all are :-)

---

