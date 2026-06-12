---
title: "Can't get ubuntu 13.10 to boot from live cd"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by lewb60 on 2013-10-27
[B]Tried to install Ubuntu 13.10,won't boot up,BIOs is setup for boot from cdrom,message reads
failed and boots up with windows XP
[/B]

---

### Post by fantab on 2013-10-27
Can you "Try Ubuntu without Installing"? If NO, then it Sounds like either a bad .iso download or a bad BURN.

Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on your downloaded ubuntu.iso. If sums match you are good, if not, then re-download the .iso.
BURN the ubuntu.iso again to a DVD using [these methods]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows") or try [Unetbootin]("http://unetbootin.sourceforge.net/").

Also, have you created space for Ubuntu on the hard drive?

---

### Post by lewb60 on 2013-10-27
Thanks for your help. I purchased the Ubuntu 13.10 CD from OSDisc.com,I'm sure it's good. How do I create space for the install on my hard drive?

---

### Post by fantab on 2013-10-27
Can you post the spec details of your machine, like RAM, Graphics, Processor? Is it a 32bit machine or 64bit? If its a 32bit machine then you will need to install 32bit Ubuntu.
When you boot with Ubuntu DVD you should be able to "Try Ubuntu without Installing". If not then there is something not good with either the DVD or your machine.

You might find these tutorials useful:
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
[URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot
[/URL][URL="http://www.psychocats.net/ubuntu/installing"]http://www.psychocats.net/ubuntu/installing
[/URL]
Good Luck...

---

### Post by lewb60 on 2013-11-06
[B]
my computer is a rebuild I believe. It's a Verbatim.I got it for cheap money. it has 504mb of RAM
with an InTel celeron processor. i believe its a 32 bit machine. I have the BIOS set to boot with the CD ROM. I tried a live Cd for Ubuntu 11.04,it get's almost to a complete install,but it doesn'
finish,the ubuntu 13.10 CD doesn't boot up,it give a failure message and boots up with WindowsXP.
[/B]

---

### Post by fantab on 2013-11-06
If you machine has only 504mb of RAM then the Ubuntu-installer won't work well, if at all it works. It needs more ram. Also 'Unity' ubuntu's default desktop needs more than you have. Your best option will be **Lubuntu**, which uses LXDE or **Xubuntu** with XFCE.
If I were you I would go with [Lubuntu]("http://lubuntu.net/").

In case Lubuntu installer doesn't work, then try [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") this will install the bare minimum Ubuntu needed to install the main desktop will all applications. You will need a good network connection to download all the necessary packages.

Once the base system is ready, then 

```
sudo apt-get install lubuntu-desktop
```

Or

```
sudo apt-get install xubuntu-desktop
```

---

