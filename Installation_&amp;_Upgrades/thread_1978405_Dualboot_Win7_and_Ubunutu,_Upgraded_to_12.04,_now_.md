---
title: "Dualboot Win7 and Ubunutu, Upgraded to 12.04, now Ubu won't start"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by PeteMichaud on 2012-05-11
I upgrades from 11.10 to 12.04 today and boy am I sorry 8( All my work stuff in on Ubuntu, so I'm really hoping it's not toast.

I have a 64bit, Intel machine that I dual boot with Windows 7 and Ubuntu. 

Today, I upgraded to 12.04, and when I restarted as part of that process, it stopped working.

What happens is that I see the BIOS screen, then the boot menu where I select Windows or Ubuntu. If I select Windows it's fine (I'm using that right now). If I select Ubuntu, to goes to the next screen and after a very brief pause it flashes a DOS-like message on the screen for maybe 1/10th of a second. After that it starts the boot process all over again, with the BIO screen, etc, eventually landing back at the boot menu where I can select my OS.

After doing this several times the best I can figure out what the flashed message says is something like:

Try ([something], [something]) No winbuilder (not sure?)
Try ([something], [something]) NTFS: [something flashes here after the other text, in white text instead of gray. It's a sentence (probably an error message), but it's way too fast to read anything.

I don't know what's wrong, and I don't know how to even boot into safe mode or anything. 

I read somewhere that it may be a graphics driver thing, so in case it's important, I have 2 ATI Radeon HD 5700 configured with Crossfire. 

Help!

---

### Post by darkod on 2012-05-11
winbuilder or wubildr?

Are you using wubi inside windows, not a proper dual boot of ubuntu on its own partition?

---

### Post by PeteMichaud on 2012-05-11
Good question! I actually don't know the answer exactly. When I first set it up, I used an installer that just did the magic for me, I ran it in windows, and it did everything to make my machine dual boot. So I suspect you may be right, that it's not a "proper dual boot"?

If it helps at all, I have a /host directory in my root that is my whole secondary windows drive (C:\ in Windows, D:\ is storage. /host contains all the contents of d:)

---

### Post by darkod on 2012-05-11
If you installed it from windows, it's wubi.

And you just saw why it's only for a quick try, never meant to be a long term install. You can expect it to break during upgrades, or updates, etc. Don't count on wubi for long term use. It's short try only.

I don't use it so I don't know too much about it. If you have some important data, it can be saved.

If there is nothing worth saving, just deinstall from windows like any other program, then install it again either as wubi or on its own partition. For the proper install on its own partition you will have to have unpartitioned space not belonging to any partition, to install onto it.

---

### Post by PeteMichaud on 2012-05-11
Well, I need this to work long term, so I ordered a new drive (that'll be the partition), and I'll install it tomorrow. But how do I recover the existing data? Is it accessible through the Windows file system?

---

### Post by darkod on 2012-05-11
You have something like this for example, but the tutorial is about running from live mode:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

You can google for more options, something like "accessing wubi files from windows" or "mounting wubi files from windows".

---

### Post by bcbc on 2012-05-11
Use the tool from here [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/) Point it at the \ubuntu\disks\root.disk  to access your data read-only or [mount it from a live CD]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F")

I don't think Wubi is susceptible to upgrade failures any more than a normal install. What makes it a problem is that Wubi installs tend to be smaller than normal installs, so [running out of space]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/986272") is probably a risk. Other than that the risks are the same as normal installs (and if you browse the forums it appears that there is some risk).

But I do think that a Wubi install should not be used the same as a production install - you need to take special efforts to backup data. Actually, that's important on any install.

Anyway... you should be able to get your data off and reinstall a normal dual boot.

---

### Post by PeteMichaud on 2012-05-12
Thanks for all your help so far! I was able to grab the files I needed from my wubi install. 

I also now have a new hard drive that I have no installed in my computer yet. Before I do that, I want to get a guide to installing Ubuntu on a new hard drive, while Windows is on the old one. Is there something like that out there, that includes how I might format my new drive and everything? I haven't found anything that's that specific. I want to make sure I do it right because I don't want to hit this sort of problem again.

---

### Post by darkod on 2012-05-12
Doing a quick google search I didn't manage to find a tutorial with screenshots of 12.04 (I guess it's too fresh).

The general is: I would recommend having separate /home partition because it allows for easier clean install later while keeping your data in /home. But for this you have to use the manual partitioning, the option Something Else in the installer.

That will list all disks and partitions in the computer.

The bottom line is we are talking about three partitions in total:
root, the system partition, make it ext4, size 20-25GB (depends if you are running any larger programs and have plenty of space on the new hdd, give it more), mount point /
swap partition, filesystem swap area, doesn't use mount point (it can be 2GB or 1.5 x RAM size if you plan to hibernate)
/home partition, ext4, mount point /home (the rest of the disk)

Below the list, there is a drop down menu for the bootloader. Select the same disk, if we are talking about /dev/sdb for example, set it to /dev/sdb (there should not be a number in it, it shouldn't be installed on a partition).

That's about it. Note to boot from /dev/sdb as first option in BIOS otherwise /dev/sda might have a broken bootloader on it.

---

### Post by oldfred on 2012-05-12
darko's instructions are good, you also do not have to full partition drive if not sure what you want and/or you may want a NTFS partition for shared data. Generally best not to write much if at all into your Windows install, ok to read, but better to have the shared NTFS for read/write.

I have a couple of links, but they are the older versions. The installer has not changed much if at all across all the versions. The "big" change was manual install was renamed "Something else". :)

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

