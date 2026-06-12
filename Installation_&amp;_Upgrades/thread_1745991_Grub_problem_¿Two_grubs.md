---
title: "Grub problem ¿Two grubs?"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Beto on 2011-05-01
Hi, my problems began as many have started in the last few days.

I tried Natty.

I had two hard disks. On the first hard disk (sda) I had Maverick with a separate boot and home partition along with a Windows 7 partition (just for playing a couple of games).

The second hard disk (sdb) had a lot of space so I made a partition to see if Natty was ready for my notebook which has some patches installed for stuff that doesn't work out of the box.

I made only one partition for Natty with the OS and home together and using the same boot and swap partitions on sda.

Natty installed fine, but I wasn't able to boot Maverick again, even though it was there in Grub. I solved it (don't ask me how, it's a two days of work story).

The problem that I have now is that somehow there are two grubs.

I think the Natty grub, which is on the boot partition is the one the computer runs on boot.
Somehow, when the Maverick grub needs to be updated (kernel update), it updates a different grub in a boot folder and not the grub on boot partition.

Any ideas in how to "connect" Maverick with the boot partition???

Thanks in advance.

---

### Post by ssican on 2011-05-01
Each installation can have only (1)one (Partition /Boot).

A (Partition /Boot) can not belong to two operating systems.

My suggestions:
1) Use the file Browser "NAUTILUS" and go to ( /Boot Partition) and see which are the KERNEL on (/ BOOT Partition) and compare with the kernel of Maverick and Natty. And thus decide whether or not you keep theses KERNELS.

2) Backup yours files on Maverick and Natty, and Reinstall either Maverick or Natty.

3) Optional: Install -STARTUP-MANAGER- of Ubuntu Software Center - on Maverick and Natty to control which operating system will be started.
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by Beto on 2011-05-02
Hi, thanks for your answer.

It's ok, I see it was my mistake to think that I could use the same Grub partition for Maverick and Natty.
I though that Grub worked looking for any installed operating systems (and different kernels) on the computer and then created a list to boot any one of them, being indifferent of which operating system updated the Grub list.

As you pointed out, it does not work as I thought.

Right now, Natty's grub governs my notebook so if I install a different kernel on Maverick it does not show up when booting.
I realized that if I run "sudo update-grub" on Natty after updating the Maverick kernel, the new updated kernel does show up when booting, so I think it might be a workaround to keep both operating systems up-to-date until the patches released by the community for my notebook are updated to work in Natty.

Do you think is a good idea or I might find future problems working like this?

Best regards,

---

### Post by oldfred on 2011-05-02
Your workaround will work.

Since you have two drives, you should install Natty's boot loader to sdb, and have Maverick's boot loader in sda. Then you could boot either via BIOS and each will discover and let you boot the other.

Unless you have an old system with the 137GB BIOS boot limit or a server (or sever like desktop) with RAID or LVM, I would not have a separate /boot partition.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

You can share swap if you do not hibernate, but should only share /home if upgrading and not really going back as newer setting in /home may conflict with older versions of software. Software is usually designed to allow upgrades but not necessarily down grades. If you want to share files, you can create additional data partition(s).

---

### Post by MAFoElffen on 2011-05-02
> **Beto said:**
> Hi, thanks for your answer.

It's ok, I see it was my mistake to think that I could use the same Grub partition for Maverick and Natty.
I though that Grub worked looking for any installed operating systems (and different kernels) on the computer and then created a list to boot any one of them, being indifferent of which operating system updated the Grub list.

As you pointed out, it does not work as I thought.

Right now, Natty's grub governs my notebook so if I install a different kernel on Maverick it does not show up when booting.
I realized that if I run "sudo update-grub" on Natty after updating the Maverick kernel, the new updated kernel does show up when booting, so I think it might be a workaround to keep both operating systems up-to-date until the patches released by the community for my notebook are updated to work in Natty.

Do you think is a good idea or I might find future problems working like this?

Best regards,
GNU Grub 1.99~rc1 shipped with Natty and has options that Natty needs and uses.  I have bug reports at LP on other upstream issues w/ this version (unrelated).  I expect that both Maverick and Natty will "meet" again with the same Grub version somewhere down the line, when 1.99 goes to full "release" status. (Hoping!)

---

### Post by Beto on 2011-05-02
> **MAFoElffen said:**
> GNU Grub 1.99~rc1 shipped with Natty and has options that Natty needs and uses.  I have bug reports at LP on other upstream issues w/ this version (unrelated).  I expect that both Maverick and Natty will "meet" again with the same Grub version somewhere down the line, when 1.99 goes to full "release" status. (Hoping!)

Hi,
How can I relate your answer to my problem?
This means that I'll always have to run "sudo update-grub" from Natty, because from Maverick might break the system?

Regards,

---

### Post by Beto on 2011-05-02
> **oldfred said:**
> Your workaround will work.

Since you have two drives, you should install Natty's boot loader to sdb, and have Maverick's boot loader in sda. Then you could boot either via BIOS and each will discover and let you boot the other.

Unless you have an old system with the 137GB BIOS boot limit or a server (or sever like desktop) with RAID or LVM, I would not have a separate /boot partition.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

You can share swap if you do not hibernate, but should only share /home if upgrading and not really going back as newer setting in /home may conflict with older versions of software. Software is usually designed to allow upgrades but not necessarily down grades. If you want to share files, you can create additional data partition(s).

Thanks for the answer and the links provided. I'll check them at night when I get home.

Regards,

---

### Post by oldfred on 2011-05-02
Ubuntu always puts a link to the newest kernal in / (root). You can create a custom entry to use the link and that will always boot the newest kernel.

gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Change details to your drive & partition. Example is for sda13 or hd0,13.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on [COLOR=Red]sda13[/COLOR]" {
    set root=(hd[COLOR=Red]0[/COLOR],[COLOR=Red]13[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=Red]a13[/COLOR] ro quiet splash
        initrd /initrd.img
}

---

### Post by ssican on 2011-05-03
Beto, you have a NOTEBOOK and (2)two Hard-Disk-Drives, ok?
Is your second Hard-Disk-Drive an (External Hard-Disk-Drive),or an USB Pen Drive?

EDIT 1:
With (2)two hard-drives it is possible choose which hard drive will be started (which operating system will be started) accessing the BIOS.
The BIOS, also called SETUP, contains the OPTION to start/boot of the First Hard Disk (sda), or of the second Hard Disk (sdb),

On the BIOS, in (Advanced BIOS Features)>(Hard Disk Boot Priority) there is the Option "FIRST BOOT DEVICE". 
The First Boot Device may be 1-Hard-Drive one/Hard-Drive two 2-CD-ROM, 3-Other Device(external drive, USB Pen drive).

EDIT 2:
Information about BIOS:
1- BIOS PAGE
[http://members.iinet.net.au/~herman546/p1.html](http://members.iinet.net.au/~herman546/p1.html)

2- How to access your BIOS set up
[http://en.kioskea.net/faq/283-how-to-access-your-bios-set-up](http://en.kioskea.net/faq/283-how-to-access-your-bios-set-up)

---

### Post by Beto on 2011-05-03
> **ssican said:**
> Beto, you have a NOTEBOOK and (2)two Hard-Disk-Drives, ok?
Is your second Hard-Disk-Drive an (External Hard-Disk-Drive),or an USB Pen Drive?

Neither, both Hard Disks are internal. It is a Dell XPS 17.

Why?

---

### Post by ssican on 2011-05-03
Because you can directly access an operating system by changing the boot priority in BIOS.

---

### Post by oldfred on 2011-05-03
I have 3 drives with Ubuntu on 2 of them. But all three MBRs boot different versions of Ubuntu as default. I normally boot the drive with the MBR set for the version I use the most and can select the others from the grub menu. But I can also use f12 or BIOS to select the other installs.

You can boot into any version and install grub2's boot loader to any MBR from that install.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Beto on 2011-05-03
Wow, you guys have been very helpful.
You have taught me new things. I'll work on them on the weekend, but I'm pretty sure the problem will be solved, as it is not an Ubuntu problem, it is a user-knowledge problem.
I'll be marking this post as solved.

Thanks!!!

---

