---
title: "Install with Raid 0"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Kalifornia909 on 2007-04-19
I have an Asus A7N8X motherboard with Nvidia raid chip. With the release of fiesty, I was wondering if anyone could give me a hand installing to a raid array. Previous versions of ubuntu (Edgy and Dapper) were able to see the SATA hard drives by themselves, but how can I install to a raid array.

---

### Post by John Williams on 2007-04-19
I followed this to install RAID1 on feisty. Works well. You should be able to adapt it to raid0 easily.

[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

:guitar:

BTW, this is software raid, not fake-raid. Most of the comments during my investigation of raid on ubuntu said avoid fakeraid...

[http://www.smop.co.uk/blog/index.php/2007/04/01/fakeraid-avoid/](http://www.smop.co.uk/blog/index.php/2007/04/01/fakeraid-avoid/)

[https://answers.launchpad.net/ubuntu/+question/4738](https://answers.launchpad.net/ubuntu/+question/4738)

---

### Post by Kalifornia909 on 2007-04-20
My partitioner shows the 2 individual drives. there is no option to set up raid anywhere. im not sure what the problem is.

---

### Post by paulieman on 2007-04-20
I followed the guide above and it worked great!  Are you using the Alternate Install CD?  Not sure if the Alternate CD is required, but I did use it, per the instructions and everything worked well for my RAID-1 install.  A friend of mine did use that very same method for his RAID-0 setup.

---

### Post by Kalifornia909 on 2007-04-20
i got it to setup a software raid. now img getting an error message saying it cannot load the operating system

---

### Post by Kalifornia909 on 2007-04-21
i have run the installer all day. no matter what i do. grub will not install.

---

### Post by hawa on 2007-04-21
The HowTo is about installing a raid on a clean set of harddisk.

Any clue of how to do it with an existing raid 0 with 1 winxp ntfs part and 1 free part?

---

### Post by Kalifornia909 on 2007-04-21
i think all of the grub problems is that it is trying to install to hd0. i tried changing the traget to md0 but that doesnt work. any ideas.

---

### Post by panchopc on 2007-04-21
the same thing is happening to me kalifornia
and i see lots of posts about this
all i want is to install ubuntu i dont care if it has raid or not
but if i enter the raid utility and delete the virtual disks
i only see the phisical drives in ubuntu
but the bios does see any drive to boot

---

### Post by Kalifornia909 on 2007-04-21
i found that the reason grub wont install is because the raid devices (md0) does not have an active partition table. therefore it cannot write to it. where to go from here i have no idea.

---

### Post by rothgar on 2007-04-21
I too am trying to install to a existing raid 0.  I do not want to have to wipe my XP installation to install kubuntu.  I even left 80 gigs free on the raid (unpartitioned) to be able to do this but I have not been able too.  if anyone finds something please let us know.

---

### Post by NewbieNik on 2007-04-21
Not sure if this is going to help, but:-

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

Gives me the impression you could install to the spare RAID space. Whether GRUB will be able to undestand the array and boot both OS's from it is another matter.
I will keep looking and maybe testing.

Best of luck

---

### Post by zero-Q on 2007-04-21
I have a upgrade&raid problem with 7.04, I told at this post [Thread]("http://ubuntuforums.org/showthread.php?t=416621&highlight=fakeraid+ich8")
what should I do????

---

### Post by Abecedaria on 2007-04-21
Linux, or at least Ubuntu, CANNOT directly boot a software RAID 0. This is because you have to load the RAID driver (madam?) first to see the array. The work-around is to use a RAID 1 partition to /boot the system , then move to the RAID 0 for /. The idea is to create three RAID partitions on each disk and then configure the array as follows:  

1)  a small, 100MB, RAID 1 array for /boot; 
2) then your main RAID 0 partition for /; (size as desired)
3) and finally a RAID 0  for SWAP. (should be double the amount of physical RAM)

Why put the swap partition last? I've heard that there is a bug that prevents the system from booting if put it before /.

This whole operation is actually very easy, but can ONLY be done from the partitioner on the Alternate Install CD....at least with edgy. Oh, I wish Ubuntu would get their act together and provide real RAID support from the graphical installer instead of this kludge. 

By the way although the system installs this way for me, GRUB is not configured correctly and I have to manually type GRUB commands to boot the system. Fun, fun, fun....

abc

---

### Post by Kalifornia909 on 2007-04-22
in y our config which partition do you set bootable flag on. is the root partition still the only bootable flag when you set up the sofware raid

---

### Post by Kalifornia909 on 2007-04-22
anyone got any idea. please help the linux noob

---

### Post by rothgar on 2007-04-22
so you are saying that:
A: my windows partition is going to be hosed
and B: I have to install with the alternate cd?

What will be left out if I install with the alternate CD?  I think KDE was one of the things left out so would I just be able to apt-get kde?  I don't want to install with the alternate cd because I don't want to have to deal with all the other stuff that will be missing.  Is there no solution for this?

---

### Post by Abecedaria on 2007-04-23
> **Kalifornia909 said:**
> in y our config which partition do you set bootable flag on. is the root partition still the only bootable flag when you set up the sofware raid

You need to set the bootable flag on the /boot partition, and should NOT set it on the / (root), RAID 0 partition. Remember, you can't boot from RAID 0, you have to boot from a RAID 1, and this is where you need to set the bootable flag. 

abc

---

### Post by Abecedaria on 2007-04-23
> **rothgar said:**
> so you are saying that:
A: my windows partition is going to be hosed
and B: I have to install with the alternate cd?

What will be left out if I install with the alternate CD?  I think KDE was one of the things left out so would I just be able to apt-get kde?  I don't want to install with the alternate cd because I don't want to have to deal with all the other stuff that will be missing.  Is there no solution for this?

It sounds like your RAID array is already set up, is this correct? No matter what you do, you should back up your Windows install before you do anything else; a software RAID on Ubuntu is a crap shoot as far as I'm concerned and you could easily hose the Windows partition. 

That said, it sounds like you could set up the free space on your RAID array with the 3 partitions I mentioned earlier. When grub installs on the newly created RAID1, /boot partition, it SHOULD see your Windows partition and add an option to dual boot in your GRUB menu. 

As far as using the Alternate CD, sorry, but that's the only Ubuntu installer that can create RAID partitions AFAIK. (At least with Edgy) The good news is that the Alternate CD contains everything on the regular CD, it just has a different installer. The default X Server for Ubuntu is gnome. If you want to install the KDE desktop, you should be installing Kubuntu. The only difference is that Ubuntu uses Gnome and Kubuntu uses KDE, AFAIK. 

abc

---

### Post by rothgar on 2007-04-24
> **Abecedaria said:**
> It sounds like your RAID array is already set up, is this correct?

Yes my raid is already set up in Windows and has been for about 6 months

> **Abecedaria said:**
> 
As far as using the Alternate CD, sorry, but that's the only Ubuntu installer that can create RAID partitions AFAIK. (At least with Edgy) The good news is that the Alternate CD contains everything on the regular CD, it just has a different installer. The default X Server for Ubuntu is gnome. If you want to install the KDE desktop, you should be installing Kubuntu. The only difference is that Ubuntu uses Gnome and Kubuntu uses KDE, AFAIK. 

I was using a kubuntu cd.  so after installing with this cd will it automatically start KDE? the last install I did with a alternate disk did not start any X session.  Does the alternate CD install all of the utilities that the regular cd does by default or is there a flag I have to use at install?

I am going to have to read your RAID 1 set up again to make sure I understand what you mean.

---

### Post by Abecedaria on 2007-04-24
> **rothgar said:**
> Yes my raid is already set up in Windows and has been for about 6 months


I was using a kubuntu cd.  so after installing with this cd will it automatically start KDE? the last install I did with a alternate disk did not start any X session.  Does the alternate CD install all of the utilities that the regular cd does by default or is there a flag I have to use at install?

I am going to have to read your RAID 1 set up again to make sure I understand what you mean.

I've never installed Kubuntu, so I can't say for sure, but I know that the Ubuntu Alternate CD DOES create a system that boots into a GUI. I'm almost positive that Kubuntu does the same. Even if it doesn't I'm sure it would be easy to track own instructions for how to make this work. Again, as far a I know, the alternate CD installs all the same things that the regular CD does, it just does it without the fancy "Live CD" interface. 

abc

---

### Post by panchopc on 2007-04-25
this did it for me guys
[http://ubuntuforums.org/showpost.php?p=1575949&postcount=20](http://ubuntuforums.org/showpost.php?p=1575949&postcount=20)

im using a perc 5i on a power edge 1950

after i followed does steps
and installed grub on (hd0,0)

grub error 21 stopped showing

but i still couldnt boot
because i couldnt mount
i had root =/dev/sdc1 on my menu.lst

i had it that way because inside live cd
my devices apeared as follows
/dev/hda "virtual floppy"
/dev/sdb "phisical drive"
/dev/sdc  "virtual drive"

so i changed my root to root=/dev/sdb1
and it mounted :)
it had to be sdb1 because hda disapears in bios
and moves the other devices one step back

but then i had to put my other hard drive on
so my devices appearad as follows

/dev/hda "virtual floppy"
/dev/sdb "phisical drive"
/dev/sdc  "phisical drive2"
/dev/sdd "virtual drive"
/dev/sde "virtual drive2"

so i had to change root on my menu.lst again
and add those devices to device.map

so i changed root to 
root=/dev/sdc1
again because a disapears in bios

it worked again
but theeeeeeen i made some updates
and it updated the kernel from .26 to .28

and know 5 menu options apeared
2 with .28 2 with .26 and the memtest

none of the booted cause it changed my
menu list from (hd0,0) to (hd1,0)

so i changed that and .28 still wouldnt boot
so i went and saw what devices i had and
i noticed that the phisical drive and virtual drive had become one
so i had to change my root to 
root =/dev/sda1

it booted
and when i saw how my disks where inside of ubuntu
sda = first phisical and first virtual
sdb = second phisical and second virtual
sdc = virtual floppy

---

