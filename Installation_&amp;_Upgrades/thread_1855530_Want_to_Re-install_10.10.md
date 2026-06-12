---
title: "Want to Re-install 10.10"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Elaphae on 2011-10-06
I have messed up my installation and want to reinstall from my 10.10 CD. Dual boot system with Windows XP Turbo. One HDD.

How did I mess it up? See unresolved here if you want:
[http://ubuntuforums.org/showthread.php?p=10948200#post10948200](http://ubuntuforums.org/showthread.php?p=10948200#post10948200)

At this point I just want to start over. On the same partition, with Windows still working. (I've managed to get some of my files but have failed at all tries to get to those owned by root).

System information:
CPU: AMD Phenom 9600 Quad Core
Speed: 2.32 GHz
System Memory: 1.75 GB
Video Card Model: ATI Radeon HD 3300 Graphics

Everything with 10.10 worked fine EXCEPT the volume in my headphones - which I tried to fix - which I failed at - which led me here to re-install.

Other information:

I doubt I have more than 50 hours on Ubuntu, 6-10 of which were installing and tweaking, the rest using programs - I am a beginner. (But have used other OS, mostly Apple for 15 plus years). I know graphics, desktop publishing, writing, Internet - not programming.

I tried the WUBI and failed and then went with the CD - which is what I want to use now. (The WUBI left some residual files (I uninstalled it the wrong way - I can live with them)).

I will gladly supply any screen images or other information, I miss using Ubuntu. I need a walk through if it there is much at the command line and have access to the net through a second computer if necessary.

I want to do it right and CANNOT LOSE THE DATA ON THE EXISTING WINDOWS partition. God (and maybe my cat) only know where my Windows install disk went...

Please help

---

### Post by oldfred on 2011-10-06
There are no guarantees. You really need good backups as any system change or just a random hard drive failure will cause loss of data. You can run most XP fixes except chkdsk from Linux, but you have to have a Windows repairCD or XP install disk to run chkdsk if need be.

Did you manage to backup your data in /home including the hidden files & folders?

Have you tried chrooting into your install and repairing it.

To reinstall and use the same partitions you have to use manual install and choose the / (root) partition. It will auto find swap. If /home is separate you have to also tell it which partition it is and mount it but DO NOT format it.

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Elaphae on 2011-10-06
"Have you tried chrooting into your install and repairing it."

No, but I am willing to try if I have good directions. What else would you need to know? I can get to the log in but my PW fails (yes, it is the correct one). The CD opens up OK.

Thanks a lot for your answer.

---

### Post by oldfred on 2011-10-06
You need a liveCD and it should be the same version but does not have to be (I think). Anything with a # is a comment, no need to type or copy that part of a line. Best from liveCD to copy from here each line & run it, then incorrect spaces or typos are avoided.

kansasnoob chroot------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

ON the CD you do not use your passwork just press enter.

---

### Post by Elaphae on 2011-10-06
I start with the live CD (the one I have is the one I originally used to install Ubuntu)

Open terminal and:

I change the partition number (sda5) to the correct one and type in what is between the lines below? I understand that I do not need to type in lines that begin with #

- - - - - - - - - - - - -
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo mount  --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf && sudo chroot /mnt


apt-get autoclean
apt-get clean

apt-get update
apt-get upgrade

apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
- - - - - - - - - - - -
Is that correct?

---

### Post by oldfred on 2011-10-06
Yes those should be the commands. If you have a specific issue with something you may need to uninstall and reinstall or just reinstall. 

If chroot part has errors, stop and we can review. Each of the && is just to combine each command into one easy to copy & paste line.
If you get any error messages copy those back here.

---

### Post by Elaphae on 2011-10-10
I've about got my nerve up, want to read it a couple of more times. I want to get it right and have Ubuntu back...

---

