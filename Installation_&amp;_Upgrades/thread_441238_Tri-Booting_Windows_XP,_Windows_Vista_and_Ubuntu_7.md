---
title: "Tri-Booting Windows XP, Windows Vista and Ubuntu 7.04 (Feisty Fawn)?"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by muffinhead on 2007-05-12
Right now I got Windows XP and Vista installed Via a Dual-Boot, and I want to install Ubuntu 7.04 to a third separate partition now without messing up my XP and Vista installs.

Windows XP was the first Operating system I installed, followed by Vista. Right now my PC is using the Vista bootloader to either boot into XP or Vista.

I wanted to get some feedback and help on this because I don't want to mess up either of my installs, and am unsure of how to install Ubuntu with the Grub bootloader without messing up my current boot configuration.

Can someone help me with this, I'd really appreciate some help on this issue/problem, so I don't bork my XP or Vista install.

Thank You:)

---

### Post by hessiess on 2007-05-12
why exactly do you need 3 os's? xp and vista are basicly the same, ubuntu is a hell of a lot faster than xp is.

the only reel difrance between xp and vista is microsoft added pointless eyecandy, there stuped digatal midia protection thingie, and make it use tuns of ram and hd space.

---

### Post by confused57 on 2007-05-12
> **muffinhead said:**
> Right now I got Windows XP and Vista installed Via a Dual-Boot, and I want to install Ubuntu 7.04 to a third separate partition now without messing up my XP and Vista installs.

Windows XP was the first Operating system I installed, followed by Vista. Right now my PC is using the Vista bootloader to either boot into XP or Vista.

I wanted to get some feedback and help on this because I don't want to mess up either of my installs, and am unsure of how to install Ubuntu with the Grub bootloader without messing up my current boot configuration.

Can someone help me with this, I'd really appreciate some help on this issue/problem, so I don't bork my XP or Vista install.

Thank You:)
You "might" be able to use the Vista bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by bulldog on 2007-05-12
> **hessiess said:**
> why exactly do you need 3 os's? xp and vista are basicly the same, ubuntu is a hell of a lot faster than xp is.

the only reel difrance between xp and vista is microsoft added pointless eyecandy, there stuped digatal midia protection thingie, and make it use tuns of ram and hd space.

That's not what TS asked.
Your opinion on Vista and windows in general is clear,but there are people who like them and want them to be installed on their computer.
And I think they have the right to do so :)

---

### Post by muffinhead on 2007-05-12
> **confused57 said:**
> You "might" be able to use the Vista bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Thanks that explains it, but one more small thing:

It says to install the Grub or Lilo Boot Loader to the Boot Sector of the Partition/Drive that Linux is being installed to, and not the MBR (Master Boot Record). 

Only problem is, when installing Ubuntu, It automatically installs Grub to the MBR. How do I prevent this and get grub to install to the Partition and Boot Sector I want it to?

---

### Post by singedwings on 2007-05-12
If you unplug all your hard drives except the one you want to install linux to then the mbr written will be on the linux drive.

Once done plug in the others and away you go. You may need to point your bios to the right drive to boot from.

---

### Post by muffinhead on 2007-05-12
> **singedwings said:**
> If you unplug all your hard drives except the one you want to install linux to then the mbr written will be on the linux drive.

Once done plug in the others and away you go. You may need to point your bios to the right drive to boot from.

Unfortunately that is a problem, as I only have one hard drive divided into partitions. I do have another hard drive in an external enclosure connected to my PC via USB. However that is used for backup of my programs and such;)

And I cannot fit another hard drive into my PC because it is an HP Slimline PC (Fairly Small) and there is no room in the case for any additional Hard drives.

---

### Post by confused57 on 2007-05-12
The alternate install cd definitely allows you to install to the root partition, and I believe the live cd does also...I don't use the live cd to install Ubuntu, but I think there is a box with (hd0) that specifies where grub will be installed by default, but I think there is an arrow with a drop-down menu that may allow you to select the root partition...or you may be able to type in your root partition, e.g. /dev/sda3 or (hd0,2), depending which is your root partition.  You may want to wait for someone that has experience installing with the live cd to confirm this.

---

### Post by muffinhead on 2007-05-12
Anyone else that can help or confirm what confused said?

I've already downloaded and burned the Live CD of Feisty Fawn, and I would hate to have to download and install the Alternate Install CD and waste another DVD+R .

Thanks if anyone else can help, I'd really appreciate it;)

---

### Post by bulldog on 2007-05-12
Well I didn't use the live cd either but from what I know,there was only the Dapper live cd where you couldn't change the location of GRUB.

As far as I know you can with Edgy and Feisty live cd's.

---

### Post by r0cks0ul on 2007-05-16
You may want to visit this site on how to triple boot :guitar: :lolflag: 

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

---

### Post by tj.c on 2007-05-16
...from my foggy memory....
I did a triple boot of Win98, Win2000 and Dapper. I installed Win98, then Win2000, then Dapper (all into seperate partitions) allowing Dapper to install grub. I then edited menu.lst (the grub menu file), under the Win2000 section I hide the Win98 partition because Win2000 would insist on making it drive C messing up Win2000. 
You should grub able to handle what you want. I used and a lot at [http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

