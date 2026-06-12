---
title: "Installing/Repairing Ubuntu on GPT"
date: 2014-01-20
forum: Installation &amp; Upgrades
---

### Post by abhishek-papanna on 2014-01-20
Hello All,

Please help me. I had installed ubuntu on a 3TB drive by creating a GPT. Now I installed a new AMD graphics card and the driver installation messed up my system. Now while booting the system freezes after some time.

Usually in such cases I do a fresh install because it is much faster than trying to fix. When I am trying to install ubuntu, it is not showing any partitions on my hard disk. I opened gparted and it shows the disk is unallocated. So I open file manager and see that all the partitions are intact. Why is the installer or GParted not showing these partitions? How can I proceed with installation?

I cannot backup my current drive as it has more data than all my backup drives can hold. I want to install ubuntu on this disk. Can anyone please help me?

Thanks in advance

---

### Post by ajgreeny on 2014-01-20
What does the Ubuntu installer show if you choose "Something Else" from the disk preparation (formatting) stage?

That is probably the best way to deal with overwriting an existing installation in any case, so I would recommend using it whenever possible, as it allows you to see exactly what is happening to your disk and what partitions are being made.

---

### Post by Zhivargo on 2014-01-20
When does your system freeze?

If you are doing a fresh install, cant you remove all partitions and individually created the following: 

/boot   ext2 100mb
/         ext4 250gb
/home ext4 2TB

(something like that?)

---

### Post by oldfred on 2014-01-20
I have never heard of installing a video card corrupting a partitioning. 

What does this show? If you do not have gdisk install it first. Not in live installer of Ubuntu either.
sudo apt-get install gdisk
If not sda change to your drive.
 sudo gdisk -l /dev/sda


 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by abhishek-papanna on 2014-01-20
Thanks for your replies. I am not new to Ubuntu. It is my primary/only OS. Sorry for not mentioning that earlier.

Anyway I cut open my seagate usb backup drive and found a 1TB SATA disk and installed ubuntu on it.

> **oldfred said:**
> I have never heard of installing a video card corrupting a partitioning.
Partitions are fine. Its the ubuntu installation that got corrupted. Everything was working fine until I installed ATI drivers.

When I installed for the first time on the 3TB disk I setup the partitions manually, everything was planned so I didnt have to go back to partitioning again. I have seperate patitions for boot, root, var, home, 4 data partitions and also one small efi drive. The problem is I am not able to view this in the installer(Ofcourse I choose manual/something else) option. When I try GParted it says the disk is unallocated, however the file manages sees the partitions and I am able to mount them as well.

---

### Post by oldfred on 2014-01-20
Does any partition need fsck, any special formats other than ext4?
Any other special configuration that may confused gparted. 
RAID, LVM Windows dynamic and others can cause issues as gparted does not work with them.

Show gdisk output.

---

