---
title: "failed to boot after automatic upgrade, stuck in busybox v1.18.5 (initramfs) promt"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by L_Darmiento on 2013-12-14
second time i've had a problem now with upgrading this machine, but this time the failure to boot seems much more serious

everything i've read points to fixing the problem with ubuntu boot repair, which i read here:
[http://askubuntu.com/questions/159554/ubuntu-12-04-wont-load-hangs-at-busybox-v1-18-5-initramfs](http://askubuntu.com/questions/159554/ubuntu-12-04-wont-load-hangs-at-busybox-v1-18-5-initramfs)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)


so i created a disk, booted to it, did some reading about boot repair, but as i'm going through the process, it tells me to backup data before performing the boot fix, but i can't access the data and when i tried to access the hard disk i got an error. is there a chance this wont work and i lose the data on the hard disk? i wont go through with that until i know how to back it up first, or that it wont lose the data while attempting the fix.

i am thinking about just taking this to a computer repair service bc i need the files on this hard drive and havent backed up in some time. i'm a novice although i've been running ubuntu for years now and despite having wiggled my way out of a few problems, these last two have just been a huge disappointment to me. i am sure i had my settings such that i have to approve my updates, and once again it rammed one through without me giving the go ahead so when i powered off and back up again i ended up in this boot limbo. 

pls help, thanks

---

### Post by brian.joe.kelley on 2013-12-14
In any kind of unix and that includes all linux,  there is the concept of booting from another "rescue" drive (usb, cd, dvd, other hardrive, etc.) and mounting
your "sick" original,crucial drive, so that you may surgically repair it. 
So you boot up on rescue and then have a shell.
Then you create a directory and mount your original drive to it.
Before that, you can use parted to identify that you original drive is seen and what its device path is.
# parted
<inside parted> print devices
look for something like /dev/sdb

Now the 128K question,  what could possibly have been corrupted and how do I fix it?
Chances are it's in /etc with a file like fstab.   Maybe a UUID got screwed up in that file or some sort of boot option.
Maybe, if you're lucky, you have a backup copy of it taken before the upgrade.
I'm thinking Solaris here, but you could look at a file like /var/adm/messages (Solaris) and see what happened during bootup when it went to initramfs.
Now, bear in mind that you're changing to something like:
# cd /mnt/etc
# cat fstab
or
# cd /mnt/var/adm
# cat or vi messages

Hope that helps.  Be CAREFUL with fstab.  See if you have a backup of that.

---

### Post by L_Darmiento on 2013-12-19
thanks, but i dont want to mess around with any of that until i know what i'm doing, i'm using boot repair gui and would rather do that then play around with the terminal if at all possible. any other suggestions? i dont want to go ahead with w/e boot repair does bc its telling me to backup my data, which i dont know how to do. i cannot afford to lose some of the things on this drive, so please keep that in mind, any other ideas/additional explanations that might be helpful?

---

### Post by L_Darmiento on 2013-12-27
**&#8203;just looking for a little help please**

---

### Post by L_Darmiento on 2013-12-31
**little help please **:confused:

---

