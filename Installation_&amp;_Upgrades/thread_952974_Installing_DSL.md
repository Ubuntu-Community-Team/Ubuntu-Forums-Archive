---
title: "Installing DSL??????"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by kwboom on 2008-10-19
Hi there I just got a old laptop from my father in law.... (pentium mmx 233Mhz with 32 meg of ram and a whopping 3 gig HD) well I think I am going to use this to test Damn Small Linux cause the system specs are a bit too high to run Hardy or any of the other distros....:lolflag:


Well when I put in the disk it only runs as a live CD.  Is there a special way to install it???????

---

### Post by Shazaam on 2008-10-19
You may need to use a partitioner like the gparted livecd to pre-partition the hard drive. Otherwise, right-click the dsl livecd desktop and go to Apps>Tools>Install to hard drive. You will need to know the name of the partition (hda1, sda1, etc). If dsl isn't your cup of tea you might try PuppyLinux.

---

### Post by robert shearer on 2008-10-19
Yes, Puppy linux +1.

Here is the link.....
[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by kwboom on 2008-10-19
I tried burning 2 disks of puppy and both give me error 20 when it tries to load????   

could this be a bad download?????

---

### Post by kwboom on 2008-10-19
ok well I am trying to install DSL on the laptop and I get to the end of the install and when it tells me to eject the cd and reboot to finish I do that and after I reboot it still tells me that there is no operating system????????

---

### Post by robert shearer on 2008-10-19
> **kwboom said:**
> I tried burning 2 disks of puppy and both give me error 20 when it tries to load????   

could this be a bad download?????

Could be.
Here is how to check the download integrity before burning...
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also you should burn it slowly.  4x speed is plenty.

If you are using Ubuntu to burn the disc then Brasero offers to verify the disc against the downloaded iso so you can check each step of the process.

What o/s are you using to download and what app to burn??

---

### Post by kwboom on 2008-10-20
Well I am using Hardy to download and using the burning program installed with Hardy to burn it ..  I am burning at a slow speed..  and the live cd part works with DSL but not with puppy, I am downloading it from the Puppy Linux site (not the torrent) but I can't figure out how to do a MD5 check on it can someone help me out a bit plz......

---

### Post by robert shearer on 2008-10-20
> **kwboom said:**
> Well I am using Hardy to download and using the burning program installed with Hardy to burn it ..  I am burning at a slow speed..  and the live cd part works with DSL but not with puppy, I am downloading it from the Puppy Linux site (not the torrent) but I can't figure out how to do a MD5 check on it can someone help me out a bit plz......

Download the iso file from the puppy site to your desktop.
Then, in a terminal type..

```
cd Desktop
```

and then type...
```
md5sum "name of the iso file"
```

Without the quotes and where the name of the iso file is the name of the iso on your desktop, just as it is shown below it.

There will be a delay while the md5sum is calculated and then a lot of numbers and letters will be displayed.

Make a note or leave the terminal open and go back to the puppy site you got the download from and find the md5sum for it.
Compare their md5sum and the one you have in the terminal and if they match then the download is good.

---

### Post by kerry_s on 2008-10-20
> **kwboom said:**
> ok well I am trying to install DSL on the laptop and I get to the end of the install and when it tells me to eject the cd and reboot to finish I do that and after I reboot it still tells me that there is no operating system????????

create the partions first, then start the installer, and then put the hda#
make sure you make a swap 256mb should do.

command for terminal:
sudo fdisk

---

### Post by kerry_s on 2008-10-20
puppy's to heavy it'll never start.

---

