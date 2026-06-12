---
title: "install to root or no boot loader"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by PlatinumPlus on 2007-02-20
Is there an option of installing the boot loader to a root partition or not to install a boot loader at all? I need to install on an already created partition with another linux sitting on a different partition and I want the other linuxes grub to load my OSs.

---

### Post by orb9220 on 2007-02-20
I believe the alternate CD will give the option of not installing grub.

---

### Post by PlatinumPlus on 2007-02-20
I have a pack of Live Dapper CDs but no alternate install CD, is it possible to get just an install app I can use in the LiveCD to get that install option? Like Vector once had an app you could installpkg on the live CD then you could proceed to install Vector to HD.

---

### Post by confused57 on 2007-02-20
Even if your latest Linux install overwrites your mbr, you can restore whichever OS grub you want to your mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I installed Sabayon, which installed it's grub to the mbr & didn't include entries to boot my other OS...I used the live cd to reinstall my Dapper grub to the mbr & Sabayon's grub to it's root partition...then I added an entry to Dapper's grub to boot Sabayon:

for example, say Dapper is on (hd0,0) & I installed Sabayon to (hd1,5), fire up the live cd:

```
sudo grub
find /boot/grub/stage1
```
will return
```
root (hd0,0)
root (hd1,5)
```
I would type in:
```
root (hd0,0)
setup (hd0)
root (hd1,5)
setup (hd1,5)
quit
```

Now I would have restored Dapper's grub & installed Sabayon's grub to it's root partition...I just add an entry to Dapper's grub to boot Sabayon:

title     Sabayon
rootnoverify  (hd1,5)
chainloader +1

Some of the earlier Ubuntu Desktop live cds did not allow you to select where to install grub, the later ones do and have a drop down menu, which by default is (hd0)...but you can click the "arrow down" next to it & select where to install grub...or type in the location, such as (hd1,5) or /dev/hdb6(in my case it was sda6).

---

### Post by PlatinumPlus on 2007-02-20
The unfortunate part is that I have SafeBoot installed on my machine and it sits on the MBR. If I mess up my MBR(like I did once with Zenwalk ;) ) I cannot boot into WinXP since it is encrypted and I will have to reinstall the whole machine. I had already installed another distro prior to installing safeboot so I could add other distros but only those that allow me to install loader in root or not at all. Then I can always go to grub menu.lst and edit accordingly.

---

### Post by confused57 on 2007-02-20
> **PlatinumPlus said:**
> The unfortunate part is that I have SafeBoot installed on my machine and it sits on the MBR. If I mess up my MBR(like I did once with Zenwalk ;) ) I cannot boot into WinXP since it is encrypted and I will have to reinstall the whole machine. I had already installed another distro prior to installing safeboot so I could add other distros but only those that allow me to install loader in root or not at all. Then I can always go to grub menu.lst and edit accordingly.

In that case, to be on the safe side it would be best to follow orb9220's advice & use the alternate cd...at grub install, select "no" to install to mbr...then you'll get a screen where you want to install grub, e.g. floppy or root partition or not at all.

If you want to see some screenshots of the alternate install cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by thefirstbruce on 2007-02-20
I went through an install last night where I wanted to ensure the grub wasn't written to mbr. 
After downloading desktop iso and starting installation, I realized there was no option on where to put grub. After RTFMing, I realized I needed to download the alternate iso. 

Apparently if the normal iso version sees other boot partitions in the mbr it won't install there. However, like you, I didn't want to leave it to chance to see if the install process recognised my XPP parts.

When working with critical partitions as you are, then I recommend doing backup partition images before messing with possible mbr overwrites. Or the better thing to do is buy another hdd, copy your partitions to that, and experiment with that.

---

### Post by thefirstbruce on 2007-05-09
SO I thought I'd be brave and try feisty 704....

what do you know....without any documentation or warning, the alternate version doesn't give an option to install grub somewhere else apart from mbr. Instead, it just powers through and installs itself right over whatever was there. thanks a lot ubuntu. another undocumented change from edgey with serious repercussions. I lost a valuable partition. and the 4 hours it took me to then download the desktop version. 

but then I get the desktop version installed, and still the wireless protocol the whole world uses WPA, still has no set up option. Linux is still stuck on WEP. 

This time I am really butting out of Ubuntu and Linux. As a recent survey showed, it is a time wasters OS for 20 somethings still living at home with Mommy.

As for OpenOffice, might be fine for high school graphs. But try to do any serious financial modelling, and it falls over. And anyone who says it is compatible with excel files failed middle school.

I'll be back when Ubuntu can actually do something like print, connect to peripherals, form networks with the current year's technology, or burn dvd's, or view multimedia.....all without having to burn up 30 hours looking for drivers and documentation. 

Hopefully Dell will sort Ubuntu's sharp but useless rep out.........good luck Michael...you'll need it...

---

### Post by PlatinumPlus on 2007-05-09
I have successfully installed using the Alternate CD for Kubuntu Feisty :popcorn: 

I am currently updating my system and all is well. I did get an option to install grub, lilo or nothing at all. I was like thrown into the Grub option but I had the options to choose where to install to. I selected /dev/hda8 but got an error because I think it wanted me to put /dev/sda8 (saw a similar problem in Arch) but I manually updated my menu.lst and unfortunately there were no vmlinuz and initrd symlinks but I managed to boot and I am typing this reply from my fresh Kubuntu install :lolflag:

---

### Post by Chappy7777 on 2007-05-09
the1stbruce, just a note to say that I installed Ubuntu on an old P2-333 a few mos back and right from the get go everything went fine. Since then I upgraded my PC to an AMD Duron 1Gig with 1 Gig of DDR Ram. The difference is as good as I hoped it would be, and better yet, the install in this machine went great. No hassles. And guess what, I am haven't been in my 20's since Woodstock. For myself, the joy of Linux is the challenge of learning it. All the new ways of downloading and installing. Getting RealPlayer to work, etc. If spending hours on an OS is not for you, then you can always spend hours playing with Malware, and other nasties that attack "real?" OSs. Also, I find it hard to whine about an OS that was mailed to me for free. Free. Let me know when and where you get Vista or Mac OS10 for free. 

Not a 20 something, sigh, just a old kid having fun w/a cool OS. Your judgement of OpenOffice is silly,
Chappy

---

### Post by thefirstbruce on 2007-05-09
folks, I muffed around with modems in the 90s, and am through with messing with immature technology. By your second decade of messing with such stuff, you get over it. 

chappy, I have a 200 row excel data worksheet, the backend for three graphs. It took 2 years to develop. OpenOffice can't cope with it.

---

### Post by thefirstbruce on 2007-05-10
And furthermore, there is absolutely no excuse for Ubuntu to not be up to speed with wireless WPA. 
Absolutely no one with more than half a brain who uses a computer for productive purposes would dream of using anything less. 

So it seems Ubuntu is indeed an unemployed tinkerer's OS.

---

