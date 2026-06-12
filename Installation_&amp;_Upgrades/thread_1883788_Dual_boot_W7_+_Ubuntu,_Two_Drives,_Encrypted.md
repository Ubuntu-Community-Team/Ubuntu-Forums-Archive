---
title: "Dual boot W7 + Ubuntu, Two Drives, Encrypted"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by lysdexik on 2011-11-19
Hey guys, I am posting here after searching all over the internet and not finding an answer to my specific question.
 
So here's the deal:
 
I have a laptop with an SSD and a 500GB HD both installed. My goal is to have Windows 7 installed on the SSD as the only OS on that drive, and Ubuntu installed on the 500GB HD.
 
What I have tried: I followed the guide located at this link: [http://stonesifer.org/](http://stonesifer.org/)
 
The problem with this guide is that it is using one hard drive for both OS's, which would be fine, but my SSD isn't big enough to accomodate both OS's plus all the programs that I would install to both.
 
I followed this guide, hoping that I would be able to change the start-up drive to the 500GB after all of the configuration and that grub would boot up. When I changed the boot drive to the 500GB, all I get is a black screen, so basically the computer never posts. When I have the SSD set to boot, it takes me immediately to the truecrypt screen. At the end of the guide it has you change around the boot manager on the truecrypt screen, and when I tried that step I got an error saying that a boot partition could not be found, that must be because it doesn't know to look on the 500GB drive for that.
 
If there is anyone who has solved this problem, please let me know as I don't want to start setting up my OS's if I am going to end up doing a complete reinstall.
 
Thanks alot in advance,
 
lysdexik.

---

### Post by lysdexik on 2011-11-21
anyone?

---

### Post by fantab on 2011-11-22
> **lysdexik said:**
> I have a laptop with an SSD and a 500GB HD both installed. My goal is to have Windows 7 installed on the SSD as the only OS on that drive, and Ubuntu installed on the 500GB HD.

When Installing UBUNTU:

To allocate space choose **"Something else"** option to Manually Partition to install Ubuntu.

Then Select the Partition on 500GB HDD to Install Ubuntu.

Now when Installing GRUB you can either choose your SSD or 500gb HDD. 
Let me assume that your SSD is the first HDD or /dev/sda and 500gb HDD is /dev/sdb.

Since Windows is on assumed /dev/sda, windows MBR will be on this /dev/sda. **If you choose /dev/sda to install GRUB, then it will overwrite Windows MBR.**

On the other hand if you choose /dev/sdb then GRUB will be installed to 500gb HDD where you have Ubuntu installed.

The Choice is yours. 

However, if you choose to **install GRUB on /dev/sdb** then you will have to **change the Hard Disk Boot Order in the BIOS** to boot /dev/sdb first. If not the Bios will keep booting Windows.

For more [**Read Here**]("http://members.iinet.net.au/%7Eherman546/p24.html")

Hope this helps.

---

### Post by WasMeHere on 2011-11-22
Welcome to the Ubuntu Forums, dyslektic, oops, sorry ;-)

I think fantab's advice is good, but I want to add a comment about the file system on the hard drive: Install linux on a linux file system!

If you already know and have done it, just skip reading ... You should install Ubuntu (and any linux) to its own file system. I would suggest ext3 or ext4. So before you start the installation, start a live session and create the partitions you want on that drive, one partition for the file system /, one partition for swap, and maybe one partition for configuration and private file /home. Use gparted to make the partitions.

Have fun finding out about Ubuntu :-)
Olle

---

