---
title: "iso to disk, in 16.04 lts"
date: 2018-07-04
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2018-07-04
i got iso. 18.04lts just cant seem to get it to disk. transmission worked somehow, but know i cant configure, start up disk creator? the iso is on the destop, plus still on transmission. its also in the home directory. my blank disk is dvd+r memorex. probably could find better recording disk. i dont think, this is the problem.:(

---

### Post by sudodus on 2018-07-04
The tool **k3b** works well for me to burn an iso file to a DVD disk. (Select the slowest possible burn speed.)

---

### Post by oneleded on 2018-07-05
when i fist tried it, i was using start up disk creator. this was from accessories. i had skipped right over sound and video. turns out, if you right click on the iso., mine was on the desktop, it gives you the option of Xfburn, it was easy after that. i tried to run it before i did the checksum. the screen loaded to where i could check, try lubuntu without installing it. it started loading, than nothing happened. after a few minutes or so, i turned the PC off, and got the disk out. i did select the slowest burn speed i could, still?:confused:

---

### Post by sudodus on 2018-07-05
Did you check that the downloaded iso file is good? You can use **md5sum** for that purpose.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Please tell us about your computer: Brand name and model

And about your graphics chip/card and wifi chip/card (also brand name and model)

It will help us help you.

---

### Post by oneleded on 2018-07-12
i have a dell PC, optiplex 270. 2Gb memory, can add 2GB more memory. pentium 4. i think the processor is 2995Ghz, but will have to get back to you on that. Lubuntu is on 2nd HD 250GB.
i dont have graphics card, or, wifi card.
i made some mistakes on setting up the 2HD, and see now, i have to change the drive set up. 
i havent figured out, out to capture that  part of the screen, and put in in my post yet. it works, but is not done right. I'll get back with that as well...

---

### Post by sudodus on 2018-07-12
I found the following via the internet:
> Dell OptiPlex GX270
Processor
Intel 865G chipset, Intel®  Pentium®  4 processor w
ith 800 MHz front side bus and Hyper-Threading
support or 533 MHz front side bus (depending on processor) and 512K L2 cache or Celeron®  processor
with 400 MHz front side bus and 128K L2 cache  
Operating Systems
Microsoft Windows® XP Professional, Microsoft Windows XP Home, Mi
crosoft Windows 2000
Professional
Dell recommends Microsoft® Windows® XP Professional 
Memory
4 DIMM slots (SF Chassis only has two); Non-ECC
 dual channel shared
2
DDR SDRAM system memory
(333Mhz or 400Mhz) up to 4GB on the SD and SMT chassis
Video Graphics Controller
Integrated Intel Extreme® Graphics 2 

This is an old computer with a CPU and the built-in graphics is not powerful enough to play well with standard Ubuntu. But the Ubuntu community flavour Lubuntu has a light desktop environment and works better with old hardware.

I have a computer with somewhat similar specs, a Dell Dimension 4600 from 2004. It runs reasonably well with Lubuntu 16.04.1 LTS which will stay with the Xenial kernel series (linux 4.4 series). You can find, download and check the iso file **lubuntu-16.04.1-desktop-i386.iso**, the 32-bit desktop version of the first point release, via the following link

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

---

### Post by oneleded on 2018-07-13
i upgraded to 400 Mhz, DDR SDRAM.. Processor, x86 Family 15 model 2stepping 9 GenuineIntel~ 2992 Mhz.. some of the other info i've seen somewhere, maybe in the bios. im running XP pro. on 1st HD..
2HD is Lubuntu 16.04.   i had problems, with iso., 16.04 download, it would not burn correct to disk..  iso.14.04, iso.17.04 downloaded well, when i put them on disks.
i upgraded 14.04 to 17.04 with the disk iso. then i updated 17.04 to latest LTS version, which was 16.04 LTS.. Somehow i got pieces of 14.04 and some 64bit file?,  injected into 16.04...
I want to install 18.04, with this system if possible.. i got to yet to use md5sum, with the 18.04lts iso.  i think i will try it in windows, just to see what happens. besides i have the md5sum program installed on windows. i will try to get back, to this thread asap with results, but will still check for updates to latest post.  //Ed

---

### Post by sudodus on 2018-07-13
My similar computer (Dell Dimension 4600) works with Lubuntu 18.04 LTS, so I think it should work for you too. Good luck :-)

Chances are much better with a fresh installation compared to upgrading from a previous version.

---

### Post by oneleded on 2018-07-14
just wanted to say thanks sudous. lubuntu 18.04 was downloaded from the Lubuntu.me site. it didnt pass the checksum.

---

### Post by sudodus on 2018-07-14
[lubuntu.me]() is the official site of the Lubuntu community (which is officially recognized by Ubuntu).

Please try again, or try via [http://releases.ubuntu.com/](http://releases.ubuntu.com/), where you can also find **torrent files**. One advantage with the torrent method is that the checksum is part of the process, so you should get it right that way without having to try more than once.

---

### Post by oneleded on 2018-07-15
Ubuntu Community, its where i got me download from. when lubuntu came up, on the screen from the disk, i recorded, it wouldnt let try lubuntu without installing.. how ever it did let me check the disk.. it said i had 4 bad file's.. i was running the torrent from the lubuntu.me site.. i will try the other place you suggested next.

---

### Post by oneleded on 2018-07-15
> **sudodus said:**
> [lubuntu.me]("http://lubuntu.me") is the official site of the Lubuntu community (which is officially recognized by Ubuntu).

Please try again, or try via [http://releases.ubuntu.com/](http://releases.ubuntu.com/), where you can also find **torrent files**. One advantage with the torrent method is that the checksum is part of the process, so you should get it right that way without having to try more than once.
i tried the alternate site as you suggested.,, and it downloaded faster than the torrent site at lubuntu.me site.. whether or not this download works??, i have to get back to you on this one.. download was 715 Mbs. to much for for some of the disks i have. i still have the DVD+R disks. they run 4.7GB. probably should have got RW... ya know if i can add to the +R disk and keep on going.

---

### Post by sudodus on 2018-07-15
I think that the only option is 'write-once', when you burn an iso file to a DVD+R disk.

(I used k3b last week, but I am no expert, nowadays I seldom burn CD and DVD disks. Most of the time I use USB pendrives instead.)

---

### Post by oneleded on 2018-07-17
interesting to know, an appreciated. tried the alternate site, thought i had the 32bit download, now im not sure. i have to get back on that one. should be plenty of USB burner programs for ubuntu, or many other versions of linux, shouldnt there?  k3b an  on---------  perhaps i should use the DVD+R for recording camera shots. it would better suited for that.

---

### Post by sudodus on 2018-07-17
I use k3b in Lubuntu and Ubuntu 18.04 LTS. You can install it with

```

sudo apt update
sudo apt install k3b

```

---

### Post by oneleded on 2018-07-17
> **sudodus said:**
> I use k3b in Lubuntu and Ubuntu 18.04 LTS. You can install it with

```

sudo apt update
sudo apt install k3b

```
when i tried this, i was much surprised.. i used my password and the update started with 14.04 LTS, yet included xenial in some of the dialog.
i checked update from disk, just in case i wanted to try to,    but, i am on a separate hard drive.     i think i need to change my update settings. an UN-check this part.

"add to post" 14.04 disk update couldnt find CD, to update 16.04.. see down 2 posts below...

---

### Post by sudodus on 2018-07-17
Sorry, I used the new syntax. I think you should use the old syntax

```

sudo apt-get update
sudo apt-get install k3b

```

in 14.04 LTS. Please try that.

Otherwise I don't know why the dialogue included xenial. Or have *you* added some xenial repository?

---

### Post by oneleded on 2018-07-17
sudo apt upgrade took me to a place almost as good as getting windows on 1st hard drive, an lubuntu on the 2nd. when i un-checked update from disk, i when to the part where it says to add, it was suggested to go to, http ubuntu repository, so i copied that, an got 187 xenial updates, i think i also got sudo apt install k3b later. i may have to get back on that later. just amazing what the correct command can do.. course ya got to learn from your mistakes. i had early on checked download from 14.04 disk, when i unchecked it, plus clicked add repository, it got me to xenial repository, for 16.04lts, which is what i am using.  PS i havent tried the old syntax as yet..

This Is For The Forum
i must clarify this a bit so it may be understood. sudo apt upgrade worked better for me, than sudo apt-get upgrade, as the same for, sudo apt install k3b, instead of sudo apt-get install k3b.
the reference to windows on 1st drive and linux on 2nd, is a reference to the thread i accomplished this, with much help from this forum. it was away from the point to this thread.
when i went to 16.04LTS i check update from 14.04 lTS disk. i should have not done this. when i unchecked this, then 16.04LTS started working better with its update function.
it was without malice or disrespect, i write the way i think. its had for me, to be understood, and not confuse others. just a thing. ed

---

### Post by oneleded on 2018-07-17
is it OK to ask which pen drive is the best to burn too? i already know some up my selections with cd's, dvd's. an pen drives have not been the best.  and about media for download, i download to desktop, then burn. perhaps i should burn straight to media. i think it is done this way, though not by me..

---

### Post by sudodus on 2018-07-17
Most USB pendrives work with most USB systems (so in most computers). But there are exceptions, that are difficult to predict. Maybe the following link and links from it can help you.

[**help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites**](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

If you 'only' want to use the USB pendrive for installing (and maybe some testing and repair), you can usually get along well with a cheap USB 2 pendrive, for example a Sandisk Cruzer Blade 4GB (maybe bigger, if you can no longer buy that size). I bought 10 of them, and they are good booters.

[hr][/hr]
In that case you can use a cloning tool to transfer the content of the iso file to the pendrive. The cloning process is very reliable, and I recommend a tool with a final checkpoint, so that you can double-check that you will be writing to the correct device.

- In Ubuntu 16.04 LTS and newer versions: **Startup Disk Creator**

- In Ubuntu 14.04 LTS and newer versions: **Disks** alias gnome-disks

- In Ubuntu 12.04.5 LTS and newer versions and many other linux distros: [**mkusb**](https://help.ubuntu.com/community/mkusb)

- In Windows: [**Win32 Disk Imager**](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) or [**Rufus** in 'dd mode'](https://rufus.akeo.ie/)

Rufus works well as an extracting tool in the standard mode, if that is what you want.

---

### Post by oneleded on 2018-07-18
just so happens, i got 2 Sandisk Cruzer Blade 8GB, an 1 Sandisk Cruzer Blade 64GB. i have to set 1 up.. they are probably fat.  however my hard drive is ext4, and i can burn to that perhaps. of course it may be better to burn to thumbdrive first, then try 18.04 for a ride, [try without installing], before i install it.
i am also working with;  [https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites) as too learn more..

---

### Post by oneleded on 2018-07-18
i moved any file from 8GB Sandisk to 64GB Sandisk, except files older than 2016, which went to trash bin. now i am doing the slow rewrite with zeros, an converting to,, ext4, instead of fat. hopefully, im on the right path.

---

### Post by oneleded on 2018-07-20
from what ive found out on the internet the sandisk cruzer blade 8gb, thumb drive is only good for Fat32. so i reformatted from ext3 back to fat. i could not get UNetbootin, to find the iso.file on the desktop. my choices where computer, of file,. i couldn't work my way around this.   after much research on line, i went to Disk Creator, as suggested. duh.. i had downloaded from the alternate site, 787Mb, round about,  usually a GB download. i got it to the thumb drive, but when setting up i didnt have the option to test, before install. i got cold feet, even though i was sure this was only going to be with the thumb drive. when my confidence builds up, i will do this. hate to mess up the 1st or 2nd hard drive. when i selected install lubuntu, it was like reading old dos selections, as far as the screen went. simple screen, simple instructions. just, not able try lubuntu first, before install. in a day or so i will re-edit this if i can to make it clearer.

---

### Post by sudodus on 2018-07-20
You can create file systems ***independently*** of the brand name and size of the USB pendrive. For example, you can create a partition and in that partition an **ext4** or **NTFS** file system in you Sandisk Cruzer Blade 8 GB.

---

### Post by westie457 on 2018-07-20
> [COLOR=#000000]when i selected install lubuntu, it was like reading old dos selections, as far as the screen went[/COLOR]
That looks like you downloaded the 'alternate' iso which I believe is for a server installation.
The alternate iso does not have a try-mode or graphical interface.

---

### Post by oneleded on 2018-07-21
> **westie457 said:**
> That looks like you downloaded the 'alternate' iso which I believe is for a server installation.
The alternate iso does not have a try-mode or graphical interface.
good point; it seems i found this out. i was leery of continuing, with the 8GB sandisk when it wanted to install.. i wasnt sure where this was going, so i aborted. guess i got lucky, an have not messed up either hard drive.

---

### Post by oneleded on 2018-07-21
> **sudodus said:**
> You can create file systems ***independently*** of the brand name and size of the USB pendrive. For example, you can create a partition and in that partition an **ext4** or **NTFS** file system in you Sandisk Cruzer Blade 8 GB.
good to know... i used the wrong download, from the alternate site. "westie457" pointed this out. the download i did will not allow you to test out, before you install. no telling what would have happened, had i allowed it to continue. it was going to install somewhere.
my intention is to get a better download 1st, format the thumb-drive better, an then go from there.

---

### Post by oneleded on 2018-07-29
> **sudodus said:**
> You can create file systems ***independently*** of the brand name and size of the USB pendrive. For example, you can create a partition and in that partition an **ext4** or **NTFS** file system in you Sandisk Cruzer Blade 8 GB.
i can install on the 8GB sandisk, or even install on the 2nd 250GB, HD i got plenty of spaces there. the only thing on the 2nd HD is lubuntu 16.04

---

### Post by sudodus on 2018-07-30
> **oneleded said:**
> i can install on the 8GB sandisk, or even install on the 2nd 250GB, HD i got plenty of spaces there. the only thing on the 2nd HD is lubuntu 16.04

Is this a question / do you want some advice?

---

### Post by oneleded on 2018-07-31
> **oneleded said:**
>  should i install on the 8GB sandisk, or  install on the 2nd 250GB, HD i got plenty of space there. the only thing on the 2nd HD is lubuntu 16.04
i need an opinion, so this is a question, or 2 of sorts.   the 8GB sandisk can be overwritten x-amount of times. the partition, on the 2nd HD, it might not matter about overwriting as much. so i think a question i got is which one is best,  including cost, as far as overwrite.   now i remember the 2nd question, more of less, which drive can be over written the most.

---

### Post by sudodus on 2018-08-01
The memory hardware of a hard disk drive has a much longer expected life (number of write operations) before failure compared to the memory cells of a USB pendrive.

There are different ways to look at cost. Of course you should look at the total cost. But when you look at cost, you should not only look at the total cost for the device, but also at the cost per megabyte storage space. The total cost for a HDD with 320 GB should be divided by 320, and the total cost for a HDD with 1 TB should be divided by 1000. The total cost for an 8 GB pendrive should be divided by 8.

You can also consider performance. An 8 GB pendrive has probably rather slow memory cells. There are fast USB 3 pendrives, but the size of those pendrives is 16 GB or bigger. HDDs and SSDs have faster memory hardware, particularly for write operations that are typical for a running operating system.

You can also consider convenience. If you want a portable system, a USB pendrive is more convenient, but if you will use the system at home and/or in one single computer most of the time, an HDD or SSD (connected externally via USB or eSATA) will work well.

---

### Post by oneleded on 2018-08-03
i understand. that explains it in greater detail, plus, i had thought i can do this either way, but needed to double check that also.  thanks again..

---

### Post by oneleded on 2018-08-06
i cant remember how, exactly i formatter 2nd HDD. till i learn how to post a thumbnail, from a captured picture, i cant show you. that might take a bit.. so i decided to go with the 8GB thumb drive for now. do i need to partition it? been a year or so since i last done these things, an i cant remember..  Ed

---

### Post by sudodus on 2018-08-07
When booted from a live [USB] drive, gparted is already there.

When booted from an installed Ubuntu system, you must install gparted.

```

sudo apt install gparted

```

**gparted** has a graphical user interface and I think it is user friendly, easy to use, in order to create a partition table, partitions and file systems (in the partitions).

But ...

- If you want to create a persistent live system, mkusb can do it for you (so you need not use gparted).

- If you want to create an installed system (in the 2nd HDD or in the 8 GB thumb drive), the installer can do it for you. So if you want a basic partitioning, you need not use gparted, but if you want something more advanced, please use gparted, and after that (in the installer), select 'Something else' and select the parttions that you created for this purpose.

In this case, please notice that 8 GB is not really enough for an installed system with standard Ubuntu. Instead you should install Lubuntu or Xubuntu, which need less drive space.

---

### Post by oneleded on 2018-08-11
poorly written

---

### Post by oneleded on 2018-08-16
> **oneleded said:**
> poorly written
is there a rule of thumb, for installing 18.04lts, on 8gb thumb drive? no pun intended.

---

### Post by sudodus on 2018-08-17
I'm not sure what you want, but I suggest the following:

- **Create a live-only or persistent live system** in an 8gb thumb drive with a tool, for example [mkusb](https://help.ubuntu.com/community/mkusb).

This works well with standard Ubuntu and all Ubuntu community flavours (Kubuntu, Lubuntu, ... Xubuntu). The reason why it works well is that most files in a live and persistent live system are compressed (and will expand into RAM when used).

- **Create an installed system** (installed like into an internal drive) in an 8gb thumb drive according to the following link.

Please notice that the drive is small, I would say too small for standard Ubuntu and some of the Ubuntu community flavours. Lubuntu and Xubuntu are small enough to make it work, but also in these cases you have little free space to create own files (or install extra program packages).

I would recommend that you use a 16 GB USB 3 drive (or bigger) for an installed system.

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by oneleded on 2018-08-17
i couldnt understand why i need to partition 8gb thumb drive, or even how to do it correctly.  now i think i know. i can proceed.. i hope this clears up some of my questions. thanx again for the responce.. ed
PS i am re-reading "how to make USB boot drives"

---

### Post by oneleded on 2018-09-12
i did resolve this to my end means. i went back to the Lubuntu.me site, and downloaded lubuntu i8.04.1LTS. 1GB, an put it on my desktop. I already had Unetbooting-linux-661. i  opened [startup disk creator],system tools. put in 8gb, that was formatted to ext4. startup disk creator oped unetbootin. from there i just had to brows to my desktop, click on the distro, push enter. was the usb starts i can try it or install. i plan on installing it on the 2nd HD anyway, so this works for me. its not persistent, but i dont need it to be.
i plan on saving the firefox bookmarks i have now, and reformatting the 2nd HD. i couldnt have this without the help i received here. i changed my mind, as i learned. thanks.
 when i find the link, which explains this better, i'l post a link.

---

