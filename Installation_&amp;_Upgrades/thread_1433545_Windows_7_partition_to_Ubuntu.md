---
title: "Windows 7 partition to Ubuntu"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by BalaViknesh on 2010-03-19
Hi,

am planning to buy a new Sony Vaio With the Below Config.. 

3GB DDR3, 320 GB HDD, i3-330M, Intel HM55, ATI Mobility Radeon&#8482; HD 5470 Graphics...

It comes with preloaded Windows 7. **[COLOR="Red"]Can I keep Windows 7 and Partition the space for Ubuntu Directly or Do I have to Wipe off my Windows 7 ???[/COLOR]**

I tried same config in Acer but read in another forum that Acer's are not doing good in Ubuntu.

---

### Post by noonenose on 2010-03-19
I am running vista with Ubuntu; I did a defrag Windows and then used Parted magic Cd to change partitions. I used the slider to decrease the size  of Windows to half the size of my drive. You could then select your swap partition and linux partion size.I use ext2 for my swap partition and ext3 for my linux partion. Most Ubuntu software has Parted magic as part of the operating system. It should step you through the proccess . I am still a newbie and learning; I hope I helped out a little bit.

---

### Post by coffeecat on 2010-03-19
> **BalaViknesh said:**
> Hi,

am planning to buy a new Sony Vaio With the Below Config.. 

3GB DDR3, 320 GB HDD, i3-330M, Intel HM55, ATI Mobility Radeon™ HD 5470 Graphics...

You might want to research that ATI graphics before committing yourself. ATI support is getting better, but patchy. My Sony Vaio has Intel graphics and everything works ootb in Ubuntu (Jaunty, Karmic and Lucid)

> **BalaViknesh said:**
>  It comes with preloaded Windows 7. [COLOR=Black]**Can I keep Windows 7 and Partition the space for Ubuntu Directly or Do I have to Wipe off my Windows 7 ???**[/COLOR]
It will probably come with three partitions: 1 = recovery partition, 2 = odd little 100mb boot partition that Windows 7 seems to like, 3 = W7 C: drive.

I would advise **not** using parted/Gparted/parted magic to resize the C: partition of either Vista or W7. The previous poster got away with it, I got away with it, but there are some who have made their Vista/W7 unbootable this way. It is repairable but best avoided. Windows 7 (and Vista) has a built-in partition resizer which is best used before you have installed anything. If you've used the C: partition much, you'll find the utility won't let you shrink it by much - even if you defragment.

This is what I suggest you do:

1 - Boot into Windows and run the Sony utility that creates restore DVDs (the system will probably prompt you anyway). A useful backup if the restore partition gets damaged. Now run the inbuilt utility to shrink your Windows 7 partition by as much as you want, leaving a load of unallocated space.

2 - Boot into a live Ubuntu CD (you don't need the Gparted live or parted magic CD - the Ubuntu live CD has everything you want). Go to System > Adminstration > Gparted and create an extended partition in the unallocated space left after you shrank the Windows partition. Create as many logical partitions as you want - Linux can boot from logical partitions. Don't forget to create a swap partition (= RAM is a good rule of thumb. It used to be x2 RAM in the days of RAM being measured in MB.). And think about creating a NTFS partition which can be used read-write from both Ubuntu and Windows. Useful for personal files.

> **BalaViknesh said:**
> I tried same config in Acer but read in another forum that Acer's are not doing good in Ubuntu.

I think it depends on the model. I've also got an Acer with Windows7, and it works well enough in Ubuntu. Touchpad is rubbish. ATI graphics were OK-ish in Karmic, but are looking good in Lucid. Everything else is OK. It's as usable in Ubuntu as in Windows 7, but the whole feel of the Acer is shabby compared with the Sony.

---

### Post by reiki on 2010-03-19
> **BalaViknesh said:**
> Hi,

am planning to buy a new Sony Vaio With the Below Config.. 

3GB DDR3, 320 GB HDD, i3-330M, Intel HM55, ATI Mobility Radeon™ HD 5470 Graphics...

It comes with preloaded Windows 7. **[COLOR="Red"]Can I keep Windows 7 and Partition the space for Ubuntu Directly or Do I have to Wipe off my Windows 7 ???[/COLOR]**


I recently got a new micro desktop machine with ATI graphics (HD4330 in an MXM slot... very laptop-like)and it had Windows 7 Home Premium on it as shipped. If you start the machine for the first time and let it finish the Win7 installation and get to a desktop, you can use the built-in disk tools in Windows 7 to shrink the partition that windows 7 is on. I was surprised to see that I could shrink the partition that the OS was running on. I have a 750GB drive. I shrunk the windows7 partition to 100GB and used the rest for ubuntu (leaving 100GB unallocated so I could test new versions).

It seems you must do the partition shrink as soon as you get to your fresh, new Windows 7 desktop as once you install additional software, it may write unmovable files to areas of the partition where it can not be shrunk as small as you want.

I left the restore partition and Windows7 on my machine because it makes it much easier to do things later, like BIOS updates from the manufacturer, etc. Also, if it shipped with Win7 and you ever need to call in to Tech Support.... if you tell them you're running Ubuntu on your system, the first thing they'll tell you is to restore it to factory, which means.... Windows 7.
I just saves some headaches later to leave the factory OS install on there. Think of it as a utility partition and boot to it once in a while and let it stay updated. I boot to my windows partition about once a month and walk away and let it update. 

Just relating my recent experience with a new machine. I've been using Ubuntu as my primary OS since August of 2005. And this is the first machine I've purchased (as opposed to building it myself) in probably 15 years.

---

### Post by jimeikner on 2010-03-19
Then there's always the [Wubi]("http://wubi-installer.org/") solution...

---

