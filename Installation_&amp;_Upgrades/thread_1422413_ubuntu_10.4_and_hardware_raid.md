---
title: "ubuntu 10.4 and hardware raid"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by webutr on 2010-03-05
I have an ECS c51gm-m motherboard with 2 sata 500 gb drives installed.
I want to use these as raid backup drives -- and the motherboard allows enabling sata raid.
 
will the new ubuntu 10.4 do a good hardware raid discovery -- will the drives show up ?
my experience with the 9.1 wasn't all that good.
 
what would be the best route to follow to doo what I wish to ?
 
I am waiting for the 64bit 10.4 to be released -- I wanted a fresh install of the LTS.
 
advice here would be appreciated ... thanks.

---

### Post by viper250 on 2010-03-05
go into bios and enable your raid setting then choose the type of raid you want 
default usually set up your sata raid as mega raid totalling the size and showing it as 1 drive. this gives you a faster data transfer rate.
refer to the documentation of your motherboard for the proper settings.
drive mirroring will not show total size but will dulicate the image on the other drive.(this allows for automatic error correction) (this is usually used in server installations)
your choice of raid setting will depend on the importance of the data you are backing up.
if your data is crucial I suggest using the drive mirroring option.
 
I dont see any problems with installation Im running a dell poweredge 2800 with 8 scsi hard drives raid 0 as mega raid and mega raid1 is mirrored to megaraid 0
running 9.10

---

### Post by webutr on 2010-03-09
> **viper250 said:**
> go into bios and enable your raid setting then choose the type of raid you want 
default usually set up your sata raid as mega raid totalling the size and showing it as 1 drive. this gives you a faster data transfer rate.
refer to the documentation of your motherboard for the proper settings.
drive mirroring will not show total size but will dulicate the image on the other drive.(this allows for automatic error correction) (this is usually used in server installations)
your choice of raid setting will depend on the importance of the data you are backing up.
if your data is crucial I suggest using the drive mirroring option.
 
I dont see any problems with installation Im running a dell poweredge 2800 with 8 scsi hard drives raid 0 as mega raid and mega raid1 is mirrored to megaraid 0
running 9.10
 
thanks for the quick response -- I'll play around with the 9.1 I have -- and will give the 10.4 a good workout. Thanks again !

---

### Post by kari0ca on 2010-03-11
> **viper250 said:**
> go into bios and enable your raid setting then choose the type of raid you want 
default usually set up your sata raid as mega raid totalling the size and showing it as 1 drive. this gives you a faster data transfer rate.
refer to the documentation of your motherboard for the proper settings.
drive mirroring will not show total size but will dulicate the image on the other drive.(this allows for automatic error correction) (this is usually used in server installations)
your choice of raid setting will depend on the importance of the data you are backing up.
if your data is crucial I suggest using the drive mirroring option.
 
I dont see any problems with installation Im running a dell poweredge 2800 with 8 scsi hard drives raid 0 as mega raid and mega raid1 is mirrored to megaraid 0
running 9.10
Hi Viper250, i have a computer like that, but i have created my raid as raid0, on the bios, so i tried to install kubuntu 9.10. it was installed with no error, but the grub was not installed, there's any trick to install it?

---

### Post by darkod on 2010-03-11
It wasn't mentioned here yet, but for RAID and/or LVM install you need to use the Alternate Install CD, not the standard Desktop image (live CD).
There are workarounds with the live cd too, but by default it can leave bits not installed, like grub, which might have been the issue you mention having with 9.10.

---

### Post by psusi on 2010-03-11
9.10 works fine for me with a fake raid 0 configuration.  If you are not planning on dual booting with windows though, you might want to disable the fake raid support and just use the Linux software raid which you will need to use the alternate installer to set up.

---

### Post by kari0ca on 2010-03-11
> **psusi said:**
> 9.10 works fine for me with a fake raid 0 configuration.  If you are not planning on dual booting with windows though, you might want to disable the fake raid support and just use the Linux software raid which you will need to use the alternate installer to set up.

That's the problem Psusi, i have windows 7 installed on my machine... 
there is some way to solve this? it was pretty simple to set-up the raid on motherboard and install win, but i dont know how (i didn't try) to set-up by software for windows...

---

### Post by psusi on 2010-03-11
If you are on the livecd run this in a terminal and post the output:

```

sudo dmraid -ayv

```

---

### Post by kari0ca on 2010-03-12
> **psusi said:**
> If you are on the livecd run this in a terminal and post the output:

```

sudo dmraid -ayv

```

I didn't had the opportunity to test the command, but i will try today.
I should say too that i'm kind a noob to install linux, i used knoppix twice (installed on my hard drive) but not with raid. my experience with linux/unix is more like an simple user that make some shell scripts and play a little with the linux...

---

### Post by kari0ca on 2010-03-12
Hi Psusi, i tried the command that you posted, but it didn't worked, i started the kubuntu cd...

The output was this:
> ubuntu@ubuntu:~$ sudo dmraid -ayv
ERROR: invalid option argument for -a
ubuntu@ubuntu:~$

> ubuntu@ubuntu:~$ sudo dmraid -a y
RAID set "pdc_biddhgdddc" already active
RAID set "pdc_biddhgdddc1" already active
RAID set "pdc_biddhgdddc2" already active
RAID set "pdc_biddhgdddc3" already active

> ubuntu@ubuntu:~$ sudo dmraid -a y v
ERROR: pdc: wrong # of devices in RAID set "pdc_biddhgdddc" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_biddhgdddc" [1/2] on /dev/sda
ERROR: either the required RAID set not found or more options required
no raid sets and with names: "v"

---

### Post by psusi on 2010-03-13
Looks like it's working.

---

### Post by kari0ca on 2010-03-13
> **psusi said:**
> Looks like it's working.

Well, then i should have missed something, because grub was not installed on the MBR...
There is some kind of trick to install or setup the grub on mbr?

---

### Post by psusi on 2010-03-15
So you installed from the livecd and it didn't install grub for you?  What is the exact symptom again?  What did you tell the installer to use for your root filesystem?  And which version of Ubuntu was this?  9.10 should do this fine.  Can you mount the hard drive from the livecd and see what appears to be the normal root filesystem with files in it?  If so and it's just grub that isn't set up right, you can instal it with sudo grub-install (hd0).

---

### Post by kari0ca on 2010-03-15
> **psusi said:**
> So you installed from the livecd and it didn't install grub for you?  What is the exact symptom again?  What did you tell the installer to use for your root filesystem?  And which version of Ubuntu was this?  9.10 should do this fine.  Can you mount the hard drive from the livecd and see what appears to be the normal root filesystem with files in it?  If so and it's just grub that isn't set up right, you can instal it with sudo grub-install (hd0).
Psusi, when i installed kubuntu, i choose to install grub on MBR and when i restarted, my system went to windows without a menu to choose the S.O. to start... the version of kubuntu is 9.10

Now when i-m trying to find my hard drive i feel completely stupid, i can see an SDA and SDB and a lot of loop0 to 7, but i think that this is each hard drive(SDA and SDB)... so i didn't mounted the hard drive and installed the grub, i will try tomorrow...
there is some way to do it on an application or something?

---

### Post by psusi on 2010-03-16
Click on the Places menu, or look in My Computer.

---

### Post by kari0ca on 2010-03-17
Hi again, well, when kubutu live cd starts it doesn't mount my hard drives.

the strange thing is the location for the partitions, they are located on /dev/mapper/ and they are: 
pdc_biddhgdddc1 for linux partition, 
pdc_biddhgdddc2 for windows partition 1 (where windows is installed)
pdc_biddhgdddc3 for the secundary windows partition.

I tried to install grub but it was unsucessfull :(

btw i'm using kubuntu 9.10

---

### Post by psusi on 2010-03-17
I don't know about kubuntu but in ubuntu the partitions should show up under the Places menu, or in My Computer and auto mount.

How did you try installing grub, and how did it fail?  You might want to try [http://ubuntuforums.org/showpost.php?p=8982005&postcount=5](http://ubuntuforums.org/showpost.php?p=8982005&postcount=5)

---

### Post by kari0ca on 2010-03-21
Thanks Psusi, i apreciate all your help, it helped a lot.
After mounting the partitions, i tried to install kubuntu again and it worked!

I'm still a kind a lost on kubuntu, i used to use knoppix with a lot of software installed, but now i will get it with kpackage, i just dont know were it goes :D i will look harder and use it. 
thanks for all your help

---

