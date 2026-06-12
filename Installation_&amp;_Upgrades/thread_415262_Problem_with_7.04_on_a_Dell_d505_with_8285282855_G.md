---
title: "Problem with 7.04 on a Dell d505 with 82852/82855 Graphics Controller"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by hoppelhas on 2007-04-20
Hi,
I have installed Ubuntu 7.04 on a Dell Latitude D505. My problem is that on top of my screen is an green area and the complete desktop is shifted down. The stripe is about 1" big.  On the bottom i'm missing this 1". Also i miss the arrow of my mouse, but the mouse still work, couse i can see the mouse over effects. The same Problems i had with 6.10, but 6.06 works fine. I've made a screenshot with my cellphone. I hope someone can help me with that problem. And sorry for my bad English ;-)

---

### Post by milanista on 2007-04-20
Yes this is a problem on Latitude D505 bios A11
I tried A09 and it seemed to work(some errors in loading tho).
Then I upgraded to A11 from A09 and these problems, corrupt screen at the top and no mouse icon, started showing.

---

### Post by niviq on 2007-04-29
I now got a hand on a Dell D505 and have exactly the same problem!
I tried with different distributions - both installed and livecd, and all gilded  the same result.:( 
On tty1 I get some unusual messages. Yet the don't seem too revelant; only that there are "some" problems with the graphics-controller:
```

usplash: Setting mode 1024x768 failed
usplash: Setting mode 800x600 failed
usplash: Setting mode 640x480 failed
usplash: No usable theme found for 640x480
screen init failed
kinit: name_to_dev_t(/dev/disk/by-uuid/\my disk uuid here\) = sda2(8,2)
kinit: trying to resume from /dev/disk/by-uuid/\my disk uuid here\
kinit: No resume image, doing normal boot...

```
This is the only text that show up between "Loading, please wait..." and "Ubuntu 7.04 \computer name\ tty1"
How do I fix it? I do have a Windows CD.

---

### Post by lybbe on 2007-04-30
Do as milanista suggests. Downgrade to Bios A09 and it will work. I have the same problem on my D505 and it worked for me.

---

### Post by stuzor on 2007-06-18
Is there any other way to resolve this problem? I am unable to make any changes to the internal hd or system. I am running Ubuntu off of an external usb drive.

---

### Post by Tethtibis on 2007-06-27
how do you downgrade the bios? the same way you upgrade it? it will just flash it in reverse?

---

### Post by dbmarquardt on 2007-07-02
I'm trying to downgrade my BIOS' version but I don't know how yet.
I just have Ubuntu installed and I can't run the EXE with the BIOS downloaded from Dell ftp site. I will try to create a winxp boot disk, boot with it and run the exe. Let's see what happens.

In the meanwhile I am clicking Function+F8 to switch to the second monitor and clicking it again to go back. It's restoring my screen. :p

---

### Post by dbmarquardt on 2007-07-02
It's done. I fixed it by downgrading the BIOS' version to A09.
You can download it from [http://ftp.us.dell.com/bios/D505_A09.EXE](http://ftp.us.dell.com/bios/D505_A09.EXE). :o

---

### Post by Tethtibis on 2007-07-02
just here to confirm, that yes, two d505's have now been fixed for 7.04 by downgrading the bios to a09. :O)

---

### Post by coopbs on 2007-09-09
Wow am I glad I came across this thread, especially after spending a day on this issue to no avail.  I had the same issue as the original poster, and had bios rev. A11.  I downloaded the A09.exe file from the Dell FTP site and installed it under XP (I happen to dual boot Ubuntu 7.04 and Windows XP).    This solved my problem (well, first I tried hitting FN+F8 a couple times as indicated, and that worked, except the cursor was fuzzy and distorted, but at least appeared). Now with A09, all is well.  I still need to figure out how to get 1400x1050 resolution instead of 1024x768, but at least now I have a full screen aligned properly and a visible mouse pointer!  Regards.

---

### Post by zippytex on 2007-10-25
> **stuzor said:**
> Is there any other way to resolve this problem? I am unable to make any changes to the internal hd or system. I am running Ubuntu off of an external usb drive.

I went to system, adminstration, screens and grapics and chose the driver for the Intel 85X and then followed screen directions and it works.  The driver they use for intel is some kind of experimental driver.  I have the Intel 82852/82855  GM/GME graphics controller on my laptop.  I hope this helps.

---

