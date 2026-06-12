---
title: "GParted-problems while installing Ubuntu 6.06 LTS to an existing Windows XP-machine"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by Arzin Tynon on 2006-07-13
I tried the Ubuntu 6.06 LTS (Dapper Drake) LiveCD for awhile and got interested. I planned to use a bit older machine (1,54GHz 512MB winXP Pro) at work for the purpose, since it's not been used so much after I got a laptop. I was planning to install Ubuntu+XP on the laptop also, after I'd gotten my hands a bit dirtier with the more expendable desktop PC.

I started by clicking the "install"-icon on the desktop while running from the LiveCD. To cut the long story short: everything went fine until it came time to adjust the partitioning. I chose to manually edit the partition table, after reading some guides:
- [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
- [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)
- [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

I have a 120GiB harddisk, which was completely partitioned as one NTFS-drive for the XP. I had cleared&copied all the important things (except 20-30 GiB of music files I couldn't find a suitable place for), and defragged to make it as small and consistent as possible. In the GParted, it looked like this:

- /dev/hda1 ntfs 114.48 GiB (44.15 GiB used, 70.33 GiB free) (boot)
- unreserved 7.48 MiB (seems like XP installation is a bit sloppy)

Alas, I didn't worry ahead enough, so I didn't take a screen-capture at this point. I planned to re-partition the disk to be like this:

- primary Windows XP (NTFS) 46080 MB (~1GiB over the minimum)
- primary / Ubuntu root (ext3) 10240MiB
- extended 60920 MiB (all the rest of the space)
+ - logical /home (ext3)  58.49 GiB 
+ - logical /swap 1024 MiB (2xRAM size)

I made the re-partition description without a hitch, which resulted in 5 operations to be done. I let 'er rip, and... lo and behold: an error message during the 2nd or 3rd operation. I didn't catch the full messages, since the windows became blank after shuffling them around, and they wouldn't repaint. I could only see the closing 'x' button in the upper right corner. All I could really do was to click that. I got back to the main GParted window after a while, which showed me something horrible:

/dev/hda1 unknown   114.48 GiB (boot)
/dev/hda2 unknown  7,84 MiB
/dev/hda3 extended 0.00 MiB
 - unreserved  unreserved  0.00 MiB

Attached is the same thing as a screencapture (which I managed to mail myself), sorry for the language (it's in finnish, but I guess the labels are placed as usual):

<perkele_1.png>

Anyways, does anybody have a clue about what went wrong?

Also, are there some methods I could try to restore the ntfs-partition? It's size didn't change (except the little unreserved 7.48MiB turned to unknown 7.84 MiB, which could be a typo), so maybe I only need to do something with the partition table or something?

Suggestions and further questions appreciated. (And remember, I'm a newbie, so please be precise & thorough.)

Thanks,

---

### Post by GarethMB on 2006-07-13
I had the exact same problem, and the only solution i found was to use the kubuntu 6.06 installer, because the live partitioner uses qtparted not gparted. Not really a solution in all honesty. So I have 5 recommendations for you:

-Install kubuntu. You might like it. You could then add the ubuntu-desktop package if you wanted a gnome based ubuntu. You could use a script to remove KDE after, there's a few kicking around, but in my opinion that's risky.

-Use the alternate text based installer. It's a 700 MB download though so again it might not be suitable.

-Forget about ubuntu. Try a different distro.

-Forget about windows. Go pure ubuntu.

-There's a live CD called gparted. You *might* be able to sort out your partitions with this, then just install with the live CD after. Alternatively you might be able to find a QT based distro with QTparted and implement this to fix your partition problem.

---

### Post by Arzin Tynon on 2006-07-13
Thanks for the tips!

I just want to clarify: So, you actually made yours work after a similar "unknown" filesystem reading all over the place? With QtParted?

I want to make those partitions work first, without installing _any_ system. I actually tried to use qtparted from the System Rescue CD ([http://www.sysresccd.org/](http://www.sysresccd.org/)), but I'm not so familiar with the tool to figure out what to do. I just didn't dare to try any of the menu commands without knowing what they would do exactly. (GParted seems a bit more self-explanatory, thanks to better UI-design.)

So, if you made yours work, what was the procedure in QtParted?

I guess I have to start reading the GNU Parted manuals ([http://www.gnu.org/software/parted/manual/html_node/index.html)](http://www.gnu.org/software/parted/manual/html_node/index.html)), since QtParted webpage doesn't seem to have much for a user guide. I'd rather not, since the command line is a bit far away from the qtparted interface.

If nothing else comes up, I guess the Ubuntu alternate install cd's text mode installer could be worth a shot. At least the walkthrough on ([http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)) is clear.

---

### Post by GarethMB on 2006-07-13
Yes. I believe my problem was the same as the one that you are experiencing. The QTparted live installer on the kubuntu CD just worked with my hardware. Its interface and operation is very similar to GParted. I only used its GUI included with kubuntu, no CLI neccessary.

My process to summarise:

Installed Win XP home.

Partioned HD using gParted, on ubuntu live CD to no avail. Unable to install. Changes involved loss of bootloader. No OS able to boot therefore.

Partioned HD using QTparted on kubuntu live CD, installed kubuntu after successful partinioning. 

Hope that helps.

---

### Post by Newton on 2006-07-20
I had the exact same problem as Arzin. The ~40GB hard drive on my old Dell Dimension 4300 was partitioned into two parts: a tiny FAT16 that wasn't visible from Windows (I assume it's for wiping the system) and an NTFS partition from which I boot Windows XP.

All those bright colors and slick interfaces from Ubuntu lulled me into a false sense of security, so I only made a very quick backup of important files and defragmented, and didn't research the Gparted thoroughly beforehand. Gparted made it look easy enough to repartition, so I trimmed off 2.5 GB from the end of my main partition, then created a .5GB swap partition and 2GB partition for the Linux root. This seemed to execute fine, but when I went back to check, the main partition as listed as ~37GB of "unknown" and there were two 0KB "unknowns" after it. (That useless little FAT16 partition is still there.)

Now Windows refuses to boot. I'll probably be trying GarethMB's suggestion of reinstalling Windows and then, when I feel like trying Linux again, repartitioning with the editor from Kubuntu. But if possible, I really would like to recover my NTFS now. Is it possible to restore that partition with its data intact?

---

### Post by GarethMB on 2006-07-20
You're better off making a separate thread for your question.

---

### Post by mod187 on 2006-07-20
Newton- you may be able to fix the master boot record on XP by booting the XP install cd. I had to do the same after a similar problem.

---

### Post by Arzin Tynon on 2006-07-20
A little update: I tried the Kubuntu installer's QtParted, and the alternate install-cd's text mode as well, without any luck. Windows install-cd didn't help me either. A trusted linux-savvy support person fiddled his fingers at the command-line fdisks and even took a look at the MBR data straight from the disk. It was messed up. The high-level folder tree nodes weren't there, so it would've taken commercial software and a lot of waiting to find, identify and recover any of the files.

So, Newton, as far as I understood from my friend's words, it's possible to recover files if they're really important, but I don't know of any free software. One application (R-Studio) he showed to me had a demo version, which doesn't recover files larger than 64KB. ([http://www.data-recovery-software.net/](http://www.data-recovery-software.net/))

Well, I only lost my music, so I just repartitioned the whole shebang, installed XP on a smaller partition and left lots of unpartitioned space for Ubuntu. Which I installed in the alternate cd's text mode. Things went well, I now have two fresh and new operating systems on my hard drive. Maybe I'll try the ntfs-resizing with my laptop later on, but not in the near few weeks.

I just wish I could've understood what went wrong. Guess I won't be trusting GParted with any difficult tasks. Still like the interface, though. ;)

---

