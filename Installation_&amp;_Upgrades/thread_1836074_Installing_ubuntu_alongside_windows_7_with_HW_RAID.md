---
title: "Installing ubuntu alongside windows 7 with HW RAID"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by kevinvw on 2011-08-30
Hi all,
First, let me say that I have really tried to find this topic on the forums with no luck.. lots on SW raid, but not pertinent to my case apparently.
 
I have win 7 64 bit on a fairly new machine, 3 500GB disks in RAID 1 using onboard raid controller. there is a 100MB boot partion, and I resized partitions so I have ~900GB windows and 30GB left for linux.
 
So, I have ubuntu 11.04 distribution, booted from the DVD and selected install.
(some intervening mis-steps here... had to go back to windows and shrink my windows main volume, recover windows mbr, lots of panicing on my part.)
 
I selected install alongside windows.
 
most of the install seemed to go ok, the partitions on my raid were recognized, files were copied, time went by.. at the end though, the windows MBR was gone again and unbuntu would not boot.
 
Anybody have any ideas? seems to be a lot of talk about raid compatibility, but mine seems to be recognized. when I boot from the ubuntu dvd, i can mount and access my windows partitions just fine. it looks like a great OS and I would love to get it installed!
 
thanks for any help!

---

### Post by YesWeCan on 2011-08-30
Hi there. "RAID compatibility" to a degree. I've not tried installing to a Windows RAID array myself but I have read this Grub problem coming up a lot. The Ubuntu installer doesn't seem to support Windows RAID properly.

This might help: [http://www.techspot.com/vb/topic153346.html](http://www.techspot.com/vb/topic153346.html)

Maybe this too: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by kevinvw on 2011-08-30
thanks for the quick response Yes!
I am anxious to try the first link.. looks promising as I did get to a spot where I could have completed an install without grub.
 
I will let you know how this goes.
 
it was also interesting to read about fakeraid.  I always assumed i had realraid!  Sounds like I may be taking a performance hit without a true raid controller.
I will post my raid interface details when I get home.
 
thanks again!

---

### Post by YesWeCan on 2011-08-30
> **kevinvw said:**
> it was also interesting to read about fakeraid.  I always assumed i had realraid!  Sounds like I may be taking a performance hit without a true raid controller.
I will post my raid interface details when I get home.
 
thanks again!
Hey, I thought the same thing as you about mobo RAID before I joined this forum. I'm not sure where the pejorative name "Fake RAID" originates. I have heard it called "Host RAID" too. I suppose  it is "hardware assist for Windows software RAID". I wonder why the mobo makers don't make that clearer? ;) :P

---

### Post by Hakunka-Matata on 2011-08-30
Excerpt from 2nd paragraph in [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Under Linux, which has built-in softRAID functionality that pre-dates  these devices, the hardware is normally seen for what it is -- multiple  hard drives and a multi-channel IDE/SATA controller.  Hence, ***fakeRAID***.

---

### Post by kevinvw on 2011-08-30
OK, well I am feeling a bit smarter.  the steps shown in [http://www.techspot.com/vb/topic153346.html](http://www.techspot.com/vb/topic153346.html)
didnt exactly match up to my setup.  my disk utility screen showed /dev/dm-x style disk devices.  using the gparted tool I found the /mapper version of the linux partition.
but when I picked that destination to install into, it wouldnt do it.  to be clear, am i supposed to pick the linux partion formatted as ext4, or the partition with the windows mbr in it?

[]("http://www.techspot.com/vb/topic153346.html")I included a screenshot of gparted and the disk utility.. although after the failed install i see that my linux partitions dont show up in that tool.. they are there tho!

thanks again for helping.. I really want to get ubuntu working.. it looks like a very cool environment!

---

### Post by kevinvw on 2011-08-31
well, i rebooted from ubuntu install cd to see if i could try again.. now i get:
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed
when i do the dpkg-reconfigure.. assume i need to wipe my linux partitions and install.. again... unless you know a quick way to recover a good grub-pc.

also, got a  screenshot of disk utility doing a better job..

---

### Post by YesWeCan on 2011-08-31
> **kevinvw said:**
> OK, well I am feeling a bit smarter.  the steps shown in [http://www.techspot.com/vb/topic153346.html](http://www.techspot.com/vb/topic153346.html)
didnt exactly match up to my setup.  my disk utility screen showed /dev/dm-x style disk devices.  using the gparted tool I found the /mapper version of the linux partition.
but when I picked that destination to install into, it wouldnt do it.  to be clear, am i supposed to pick the linux partion formatted as ext4, or the partition with the windows mbr in it?

[]("http://www.techspot.com/vb/topic153346.html")I included a screenshot of gparted and the disk utility.. although after the failed install i see that my linux partitions dont show up in that tool.. they are there tho!

thanks again for helping.. I really want to get ubuntu working.. it looks like a very cool environment!

I only have a minute to respond right now. It may be you have to install the dmraid drivers when you boot the live CD. This may be why Disk Utility is not showing the RAID partitions:
sudo apt-get install dmraid
sudo dmraid -ay

---

### Post by YesWeCan on 2011-08-31
> **kevinvw said:**
> well, i rebooted from ubuntu install cd to see if i could try again.. now i get:
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed
when i do the dpkg-reconfigure.. assume i need to wipe my linux partitions and install.. again... unless you know a quick way to recover a good grub-pc.

also, got a  screenshot of disk utility doing a better job..
So I think that tutorial basically does a chroot into the dmraid Ubuntu root and then does a reinstall of Grub using dkpg-reconfigure.
Instead, you might want to follow the official chroot/purge/install method. After making sure dmraid is installed, follow this guide: [https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall](https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall)
You may or may not have anything to purge, but the install of grub-pc should help.
You need to select the dmraid device for Grub rather than any individual disk drive. It will be called /dev/mapper/blahsomething

---

### Post by kevinvw on 2011-08-31
OK, did the purge/reinstall... still failed on install. I think i may be picking the wrong partition to install grub to. see attachment for my disk utility screen...
I have been trying to install to /dev/dm-3... the ext4 linux partition. but I have a feeling I should be installing to the 1TB device at the top of the peripheral list.. the parent raid array. But that scares me until somebody here smarter than me (anybody really) tells me its OK!
 
thanks again for being patient!
 
A little more on how my disks are setup:
3 500GB disks in raid config netting ~970GB total volume
  1 100MB partition, apparently a rescue boot partition (? not sure)
  969GB partition for windows.
 
I shrunk the 969 GB windows volume to free up ~30G and used that space for linux.  after an install i had:
 
1TB parent hard drive containing:
100 MB partition
920GB partition for windows
25GB partition ext4 filesystem with linux install
~6GB swap partition.
 
so i guess I would like to know which of the above partition/devices I should let grub install to... is it the 1TB parent hard drive?

---

### Post by kevinvw on 2011-09-02
OK, new approach.. buying a 4th hd to install to.
if you cant beat em, run away like a little girl.
thanks for all the help... sure i'll be back with more questions!

---

