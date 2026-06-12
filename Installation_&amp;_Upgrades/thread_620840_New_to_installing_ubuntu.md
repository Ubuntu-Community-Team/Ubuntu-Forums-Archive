---
title: "New to installing ubuntu"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by Tiamats_Chosen on 2007-11-23
i got a hold of and old computer and replaced the HD.   ihave an old ubuntu5.10 install/live cd set and when i installed on the fresh HD its does not want to access any of the components and i cant get online.  i downloaded the new 7.10 iso but the computer does not want to read the disc.  i did the Hash test and i adds up and the disc reads as a install on both of my current dual booting systems.  

the PC specs are
128 ram
pentium3
and a fresh 20gb  HD
(yea  its old but it was free)

if someone can link me the iso to download that work for a system like that i would appreciate it:confused:

all i want is a internet browser PC  i have a cable connection and netgear router

---

### Post by Craigus on 2007-11-23
May I suggest PCFluxboxOS ?

Tinyflux 1.0 will do everything you want, and it will be quite fast enough on that machine:

[http://pcfluxboxos.wikidot.com/]("http://pcfluxboxos.wikidot.com/")

---

### Post by Sef on 2007-11-23
Get [Xubuntu]("http://xubuntu.org").  It is made for system like yours.   With 128 mb ram, it will work really well.  Ubuntu and Kubuntu need 256 mb ram minimum.

---

### Post by Herman on 2007-11-23
Sef is right. I agree. :)

Also, if you have 128 mb of RAM or less, you need to use the 'Alternate CD' to install with too. See my signature link below this post for details.
The 'Desktop' Live/Install CD will not work very well with 128 mb of RAM and probably won't be able to perform an installation with less than 256 mb of RAM, (and even then you would need to make a swap area first with a [GParted -- LiveCD.]("http://gparted.sourceforge.net/")

128 mb is plenty of RAM for the 'Alternate' CD. 
The 'Alternate' CD can be used to install a minimal system in 'Low Memory Mode' for installing with in computers with as little as 32 mb of RAM. 

Look for the 'Alternate CD download somewhere near where you downloaded the 'Desktop' Live Ubuntu CD from, or here, **[Get [B]Xubuntu** | **Xubuntu**.org]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.xubuntu.org%2Fget&ei=opJGR9j3HpG4pgSimpCvCw&usg=AFQjCNFtyRWGwHw7pYe6KfxfScjLfBGV5g&sig2=vUyrqWjxEC7LzrhwK6iD8A")[/B]

As Craigus suggested, you may find that some other desktop will give you even better performance than Xubuntu.
Fortunately it is very easy to install several different desktops in any *buntu, and try them all out to see which one you like best, and which works best in your machine.
I have one computer with 128 mb of RAM and I have Gnome desktop (Ubuntu), XFCE desktop (Xubuntu), IceWM desktop, and Fluxbox desktop, (Fluxbuntu), all in the same operating system, and I can boot up and log into whichever desktop I want.
IceWM is currently my favourite, but it's hard to decide between that and Xubuntu.

I only had 64 mb of RAM in the machine when I performed the installation. Story here: [Windows98SE+Ubuntu Gutsy Gibbon]("http://users.bigpond.net.au/hermanzone/p2.htm"). That is an example of a minimal install though, that's 'overkill', you won't need to go to that extreme with 128 mb of RAM.

You can also get Fluxbuntu 'Alternate' CDs. [Fluxbuntu Home Page]("http://fluxbuntu.org/js.html")
I presume the 'Installer' CD would be the same things as an 'Alternate' CD, but I could be wrong as I haven't tested it myself.

For Icebuntu, you would just install some other *buntu, (such as Xubuntu), then install the IceMW desktop, then install the Icebuntu theme. [Icebuntu]("https://wiki.ubuntu.com/IceBuntu").

Regards, Herman :)

---

### Post by louieb on 2007-11-23
> **Craigus said:**
> May I suggest PCFluxboxOS ?...will do everything you want, and it will be quite fast enough on that machine:
[http://pcfluxboxos.wikidot.com/](http://pcfluxboxos.wikidot.com/)
[PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/") +1 My new favorite lightweight Linux. xUbuntu's good too.  Humm Ginger or MaryAnn?

---

### Post by Tiamats_Chosen on 2007-11-23
ok  i tried  both the Xubuntu alternate disc and tinyflux. 

with xubuntu i got "remove disc(s) from drive and press any key to reboot"

and wiht tinyflux i got "ISOLINUX 3.35 PCLinuxOS  Copyright (c) 1994-2007  H. Peter Anvin"
and then nothing happens

windows is not installed on this computer and i dont have any intention to install.   is there something i am doing wrong?:confused:](*,)


getting ready to try Fluxbuntu now

---

### Post by Herman on 2007-11-23
>  and a fresh 20gb  HD
(yea  its old but it was free)>  with xubuntu i got "remove disc(s) from drive and press any key to reboot"

and wiht tinyflux i got "ISOLINUX 3.35 PCLinuxOS  Copyright (c) 1994-2007  H. Peter Anvin"
and then nothing happens It sounds to me as if you are having some bootloader problems. 

I don't know very much about isolinux or syslinux yet, I just started learning those, but isolinux is a liveCD booter, and syslinus is the hard drive version of it, so it sounds like your computer is trying to boot the CD/DVD drive instead of the hard drive.
 
You should go into your CMOS, (BIOS setup), and check that the hard disk is set up and detected properly in your  BIOS. 
Just check your settings, also your boot sequence in your CMOS to make sure it includes your hard disk in the list of bootable devices. 
Also check to be sure there's no MBR 'write protect', or anitvirus running, as those prevent the bootloader from being installed to the hard disk. Not all BIOSes have those, so if you don't find one, just skip it.  Then when you think everything in CMOS is okay, reboot.

You can install an operating system, or just re-install the boot loader from the last operating system you installed and it should boot okay then. Or try booting with Super Grub Disk.

If you still have trouble you should also recheck your hard drive IDE ribbon cable and hard drive jumper settings.  (ie;  Master, Slave or  Cable Select).

If your IDE ribbon cable has three black plugs, the hard drive jumper should be set to 'Master', assuming it is your number 1 (or only) hard drive.  Any other drives on the same IDE cable , (your CD/DVD drive for example), should be set to 'Slave' using the jumper clip.

If your IDE ribbon cable has one blue end (which is for the motherboard connection), one grey end, (to slave drive), and one black end, (to Master drive), then you have a 'cable select' IDE cable and you can set the jumpers on both of your drives to 'cable select'. When you do that, the way you plug the cable in will determine which drive is Master and which will be Slave.

When you are sure you have your IDE hard drive and CD/DVD drive set up and plugged in correctly, then you can install an operating system, or just re-install the boot loader from the last operating system you installed and it should boot okay then.

Actually, I suspect the IDE drive jumper settings, or the way the ribbon cable is plugged in will turn out to be the culprit, but I'm just guessing.

Regards, Herman :)

---

### Post by Pumalite on 2007-11-23
I think, if the OP wants to use Xubuntu, better stick to Feisty Alternate Xubuntu:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Tiamats_Chosen on 2007-11-24
The internal physical components are all correct. the original system had  xp2000 and i reformated to use the 5.10 (see first posts)   i had another harddrive thats completely blank so i need to have the order as 

cd-rom,   a:\ , hard drive, then network boot

or i get the "remove disks and press any key to reboot."  im am downloading the 7.04 install and alternate discs now.    would it be easier to intall DOS as the basic OS and then linux or no different at all.

if its not already clear im trying to do an installation from boot

---

### Post by Pumalite on 2007-11-24
What is the problem you have with your installation at this point?

---

### Post by Tiamats_Chosen on 2007-11-24
after trying the 7.04 i tried the 5.10 again and it worked
i believe it was the fact that i didnt have the computer hooked up to my router on the first instalation is why it didnt want to connect to the internet originally. 

thanks for the help and look for some Breazy badger questions later on
(found original "oregon trail game" tips on intalling that will be appreciated)

---

### Post by Pumalite on 2007-11-24
Good for you!

---

