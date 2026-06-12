---
title: "How can I triple boot XP,KDE and Gnome?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by red33m on 2010-02-06
Hello everyone,

I am probably gonna buy an iPhone 3gs so I am gonna need to run iTunes on Ubuntu.I have already tried that a couple of times using wine but it doesn't work for me.I am currently running Ubuntu and Ubuntu KDE on a dual boot but I'd like to install Windows XP too.I entirely deleted my hard drive a couple of weeks ago and I tried to boot from the Windows XP CD and so it did..well until a blue screen came up and said that I for safety reasons it won't open Windows and I need to erase the whole hard drive..but I did that already!

Is there any other way that I can delete the whole system and install XP and both Gnome and KDE at the same time.

I just want to run XP for the iTunes support that's all.I don't want to get rid of Ubuntu of course!

Thanks for reading and so you know my prefix is both Gnome and KDE,

all answers are welcome!

red33m

---

### Post by leandromartinez98 on 2010-02-06
I don't know how to help with the XP thing. Just wanted to mention that (maybe you already know), that you don't need to dual-bool Gnome and KDE. You can install both windows managers in the same installation and choose between them on login.

---

### Post by llawwehttam on 2010-02-06
If you really need to install windows you have to wipe the HDD then format as NTFS for the windows install disk to read it.

Some ubuntu programs can read iPhones/iPods though.

---

### Post by SuperSonic4 on 2010-02-06
[list=A]
[*]Back up any important data
[*]Wipe the hard drive clean, if possible using XP, failing that a live CD
[*]Install XP
[*]Install GNOME and KDE in any order you like
[/list]

That way will avoid tricky grub issues. I'm not sure if you know this already but your GNOME and KDE installs can share swap

---

### Post by ssulaco on 2010-02-06
> **red33m said:**
> I entirely deleted my hard drive a couple of weeks ago and I tried to boot from the Windows XP CD and so it did..well until a blue screen came up and said that I for safety reasons it won't open Windows and I need to erase the whole hard drive..but I did that already!

Boot your live CD,open gparted,if it is already partitioned,I believe you can select first partition and click partition and format it to NTFS.....then try installing XP

---

### Post by red33m on 2010-02-06
Yeah I already know I can do that..but because I need to share the laptop with my brother he wants me to install two individual OSs..

---

### Post by Solethara on 2010-02-06
Instead of installing WinXP, you can use a virtual machine since you will  use it just for iTunes.

---

### Post by SuperSonic4 on 2010-02-06
> **solethara said:**
> instead of installing winxp, you can use a virtual machine since you will  use it just for itunes.

+1.

As long as you don't overdo a VM is a good ida

---

### Post by red33m on 2010-02-06
well I just finished partitioning the HD...but it'b be good to know how to run XP virtually..!

sounds amazing!

---

### Post by underquark on 2010-02-06
> **red33m said:**
> well I just finished partitioning the HD...but it'b be good to know how to run XP virtually..!

sounds amazing!
Install VirtualBox and then install Windows as a virtual machine.  You do see a slight performance hit but I still find it works fast enough to run my video editing program, VideoReDo, without too much effort.  Really benefits from a lot of RAM and a multi-core CPU. Suggest you also create a shared directory outwith the virtual machine so that you can share files easily yet keep the VM down to a reasonable size.

I still boot into XP occasionally to run certain programs that access the DVD drive or USB a lot and to use my scanner (Umax Astra 4500).  Paradoxically, my "real" XP doesn't see my wireless LAN, though, without making it jump through hoops.

---

### Post by red33m on 2010-02-06
this was the one way solution...it is cooler than I expected!

---

