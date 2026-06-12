---
title: "Upgrade gone wrong"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by Quib on 2010-06-06
Roughly one month ago I tried to use the upgrade feature to go from 9.10 to 10.04. Things went wrong, and I found some help here from Wilee-Nilee, who helped me restore my MBR so that I could use my Win7 partition to conclude some important work. I'm back now to see if anyone can help me get the dual-boot up and running again.

What I started with: Dual Boot Win 7 64 bit / Ubuntu 9.10 64 bit I followed a tutorial to get the whole thing set up in the first place, so my skill level is very low when it comes to Ubuntu. The initial set up was a nightmare, but once it was finally up and running everything worked as it should. 

What I tried to do: I used the update manager in 9.10 to attempt to update to 10.04. After 6 hours of downloading and installing it asked me some questions about grub or updating grub and where to install grub... I really don't know. I read the suggestions and chose the the partition that I believe had the boot flag. I'm now not so sure.

I suppose that the upgrade went alright with the exception of the GRUB part, because when I install an Ubuntu 10.04 live disc it recognizes that I have both Win 7 and 10.04 installed, so maybe repairing GRUB (without losing the ability to boot into Win7) is a way to approach this.
or,
Couldn't I simply format the partition that Ubuntu is currently on (I have no important data on that partition) and install the 32bit version from the live disc? I know enough to choose to ext4 and to format the partition, but when it asks about mount point I don't know what to choose. Boot seems the intuitive choice, but I really have no clue. 

Anyone care to help me through this? It seems like it should be an easy enough fix, but I've been wrong before.   

Thanks in advance.

---

### Post by wojox on 2010-06-06
See here [WindowsDualBootUbuntu 10.04 or 9.10 ]("https://help.ubuntu.com/community/WindowsDualBoot#Ubuntu%2010.04%20or%209.10")

---

### Post by ubername on 2010-06-06
It should be straightforward to get you up and running with dual boot. I'm not sure why you suggested the 32bit version from the live CD unless that is what you have to hand. 64 bit has worked fine for me for as long as I've used Ubuntu.

Simply run the live cd and follow the prompts as usual. When you get to the partitioning bit, select your existing Ubuntu partition , check the box to format it (to be on the safe side), use ext4 as the file-system and select '/' as the mount point. (Unless you want to have separate partitions for /home and others - but there is no need to do this and can be changed later).

Now, right at the end of the install process when it shows the summary of what is going to be installed, which partitions are going to be formatted etc, there is an 'advanced' button. Click on that and make sure that grub is going to be installed to the MBR of the DRIVE which the Ubuntu partition is on (not the partition itself). i.e. pick something like sda rather than sda1. If you only have one drive that should be simple, Even if you have more drives it should be straightforward to work out which drive to use.

Please note these instructions are for a basic quick set-up. I am aware there are lots of different alternatives, but sometimes presenting all the options makes things more confusing.

---

### Post by swudee on 2010-06-06
OK this is what I did to try to recover a broken Grub.

Boot from the live CD
Open a terminal and do the following commands to mount the partition

$ sudo su
# mkdir /mnt/tmp
# mount /dev/sda5 /mnt/tmp

Then reinstall Grub

sudo grub-install --root-directory=/mnt/ /dev/sda

Make sure the system is updated which should reduce the chances of it breaking again.

good luck

---

### Post by Quib on 2010-06-06
I decided to try Swudee's instructions first (to keep the 64-bit version and save time, assuming the existing install is good). I followed the instructions, (keep in mind it is my first time in the terminal) and nothing noticeable happened after typing the commands, so I assumed that everything went as planned and tried closing the terminal window. It says that a process is still running and that closing the window will kill it. It's been this way for over an hour. Is there some command I should type to finish Swudee's instructions, should I simply close the window and boot to see if GRUB is fixed, or should I keep waiting?

If this doesn't work, and doesn't break the MBR then I'll try Ubername's method.

---

### Post by swudee on 2010-06-06
Hi, this should only take a minute or so.

As for updating first I guess I should have included these instructions.

# chroot /mnt/tmp 

  to chown root the partition so you manage packages as root.
                     

# apt-get update   

  to update apt's the repository list

# apt-get upgrade   

  to install the updates.

I do find that the terminal says that the process is still running after it has closed, mainly when I do gksudo nautilus though.
So maybe try updating and reinstalling nautilus, although it may have reinstalled grub already.

---

### Post by Quib on 2010-06-08
Alright, after attempting many of the suggestions I eventually downloaded the Lucid 64bit iso and formatted and re-installed on my ext4 partition.

Both operating systems work like a charm. 

I would change this to solved, but I don't know how.

Thanks for the help guys.

---

