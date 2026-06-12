---
title: "Cannot install GRUB to /dev/sda"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by WildZontar on 2011-05-26
I've decided to do a dual-boot of Windows 7 and Ubuntu ever since a keylogger stole all my passwords. I shrunk my volume using Windows' tool to 500GB and left another 500GB to Ubuntu. The installation goes fine up until bootloader install. Ubuntu installation stops with a "fatal error" when trying to install GRUB to /dev/sda.

I'm using a 1TB RAID0 array in two 500GB disks, using whatever hardware controller is on the Asus P8P67 Pro. Does this have something to do with the RAID0? Is there something else I'm supposed to do? Running Ubuntu 11.04.

Additionally, this is amd64 ubuntu.

---

### Post by ILoveYorkies on 2011-05-26
[SIZE=3]Hi there,
I'm just a linux beginner myself so I don't know how much I can help but  more info would help even the linux experts such as what is your  processor, AMD x64 or Intel x64, Win Home, Pro or Ultimate? 

I'm sorry but I don't know anything about RAID0 so I can't answer if that maybe what the problem is.[/SIZE] [SIZE=3]

Biggest question is: what does disk utility or Gparted say that /dev/sda  is? What I mean is does it say it's Windows boot partition or recovery  partition, etc.? How many partitions do you have? Are there 4 active  partitions? If so that could be a problem. Do you have a usb thumbdrive?  If so you could plug it in before trying to install Natty, then try to  install it again with usb plugged in. It should see the usb thumbdrive  if so then choose that as the drive to install Grub bootloader to.  That's what I did when I installed Ubuntu 11.04 on my netbook. Of course  if you do that, every time you want to boot into Ubuntu you will need  to plug the thumbdrive in first. I don't mind that myself. It might at  least get Unbuntu installed and bootable for you. How much ram do you  have? Maybe you should make a linux swapfile partition? I've read one  should be twice what your ram is 1gb ram=2 gb swapfile, etc.[/SIZE] [SIZE=3]
Hope this helps.[/SIZE]

---

### Post by psusi on 2011-05-26
Open a terminal window and run:

```

sudo blkid
sudo grub-install /dev/sda

```

And post the results.

---

### Post by ronparent on 2011-05-26
Not intending to contradict psusi who is generally more knowledgeably, but, if the systems are installed on a raid0 then grub 2 should be installed to the Ubuntu raid0 partition and the bootloader installed to the symbolic link for the raid0. From a live cd terminal run **ls /dev/mapper/**. The first item listed after control is the link for the raid array (that is where the bootloader is installed). If you post the output of **ls /dev/mapper/** nd tell me which partition Ubuntu is installed on I can give you explicit instructions.

Incidently, since sda is part of the raid set a fatal error is indicated for 10.04 but can be fixed with a grub reinstall. 10.10 and 11.04 I believe will install correctly.

---

### Post by Pumalite on 2011-05-26
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by psusi on 2011-05-26
Ahh, of course; I must not have been paying attention.  Yes, it shouldn't be trying to install to sda in the first place.

---

### Post by WildZontar on 2011-05-28
I got it up and running fine. I misunderstood how Fake RAID works. You need to select the mapper instead of sda or sdb, which are the physical hard disks.

---

### Post by ronparent on 2011-05-28
Great! Have fun.

---

