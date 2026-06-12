---
title: "Rufus for ubuntu ?"
date: 2020-12-17
forum: Installation &amp; Upgrades
---

### Post by gardenair on 2020-12-17
hi, 
     In my windows laptop to burn any iso file, I use "Rufus " software. i.e [https://rufus.ie](https://rufus.ie)  . The software is very easy, solid and user-friendly. The thing I want to ask is in ubuntu/Xubuntu can I use Rufus or there is similar software that can do the same thing as Rufus do?

---

### Post by ActionParsnip on 2020-12-17
You don't burn to USB. You burn optical media like CDs and DVDs. It is called "burning" because the laser used to put the data on the disk is more intense than the laser to read it. USB storage is magnetic. There is no burning. Rufus simply extracts the data and puts it on the USB stick then makes it bootable and usable.

---

### Post by ActionParsnip on 2020-12-17
There are lots of applications to put an ISO onto a USB stick in Ubuntu from command line options like 'dd' to GUI applications like "Startup Disk Creator". You can even install unetbooting using the below 3 commands
```

sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get -y install unetbootin

```

---

### Post by sudodus on 2020-12-17
+1 for the Ubuntu Startup Disk Creator.

The following link and links from it describes several methods and tools for the same and similar purposes,

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gardenair on 2020-12-17
Thanks for the reply. Well if I talk about **dd **command is it a part of ubuntu command line or I have download the dd utility command? what will be the syntax of the command? Suppose I have downloaded Xubuntu iso file and now want to to make a bootable USB which have an 8 GB capacity.

Appreciate you.

---

### Post by CatKiller on 2020-12-17
Personally, I've found Etcher entirely painless to use.

---

### Post by sudodus on 2020-12-17
dd is a standard Linux command and is included in all Ubuntu flavours (e.g. Xubuntu).

But dd is risky because there is no final checkpoint. It will accept your command without any question, also when you tell it to wipe the family pictures or other valuable data. Many people have made mistakes and pointed to the wrong drive and for this reason dd has earned the nickname Data Destroyer.

Instead I suggest that you select a dedicated tool with a graphical user interface, that helps you identify and select the correct target device, usually a USB pendrive.

Edit:

The Ubuntu **Startup Disk Creator** is also included the Ubuntu flavours (e.g. Xubuntu). It is easy to use and has a final checkpoint. It will help you identify and select the correct target device. But [there are also other tools](https://help.ubuntu.com/community/Installation/FromUSBStick) with similar properties.

If you want something more advanced than a basic live-only drive, for example a persistent live drive, or make a non-Ubuntu live-only drive, I can recommend [mkusb](https://help.ubuntu.com/community/mkusb).

---

### Post by #&amp;thj^% on 2020-12-17
> **sudodus said:**
> dd is a standard Linux command and is included in all Ubuntu flavours (e.g. Xubuntu).

But dd is risky because there is no final checkpoint. It will accept your command without any question, also when you tell it to wipe the family pictures or other valuable data. Many people have made mistakes and pointed to the wrong drive and for this reason dd has earned the nickname Data Destroyer.

Instead I suggest that you select a dedicated tool with a graphical user interface, that helps you identify and select the correct target device, usually a USB pendrive.

I myself prefer and use "dd" NOTE: Please heed sudous advice dd is also affectionately know as Disk Destroyer.
Many Great tools for this with GUI's available. sudodus has one also mkusb found here: [https://help.ubuntu.com/community/mkusb/gui](https://help.ubuntu.com/community/mkusb/gui)

---

### Post by GhX6GZMB on 2020-12-17
Startup Disk Creator. It's already in the standard menu and just as easy to use as Rufus.

---

### Post by VMC on 2020-12-17
I only use [Ventoy]("https://www.ventoy.net/en/index.html") now. Tried all the others. Ventoy is just to easy and has never failed.

---

### Post by C.S.Cameron on 2020-12-17
I mainly use **mkusb** in Ubuntu because I like a **Persistence** partition and a dedicated **Data** partition and the program has other tools for playing with USB drives.

**Ventoy** is not bad, it also allows persistent partitions but Data has to share a partition with the OS ISO's.

If I just need a quick OS installer USB, I use **Gnome-Disk**s.

---

### Post by gardenair on 2020-12-18
Thanks all for your kind replies. As to a  Rufus user (under windows 10), I was assuming that it will be also available in Linux. Unetbootin is the alternate I think but I have not yet used it.mkuse also seems fine.
does both will work in xububtu as well?

---

### Post by sudodus on 2020-12-18
Yes. Install each of them from its PPA. Both have graphical user interfaces (GUI).

---

### Post by ajgreeny on 2020-12-18
Since mkusb became available I have used nothing else. In my opinion it is very simple to use and quicker than many other applications I used in the past.

It uses dd in the background but takes a lot of trouble to ensure that there is just about no chance of dd becoming the "disk destroyer" or more correctly "data destroyer" (the disk can be reused even if you overwrite all the data on it) that it can be if you inadvertently choose the wrong destination device, ie disk, in your command.

---

### Post by ActionParsnip on 2020-12-18
> **VMC said:**
> I only use [Ventoy]("https://www.ventoy.net/en/index.html") now. Tried all the others. Ventoy is just to easy and has never failed.

Looks nice. Would be nice with a GUI for the average Joe user

---

