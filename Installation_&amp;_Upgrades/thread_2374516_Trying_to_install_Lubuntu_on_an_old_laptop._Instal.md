---
title: "Trying to install Lubuntu on an old laptop. Installation gets stuck on the &quot;Preparing"
date: 2017-10-16
forum: Installation &amp; Upgrades
---

### Post by mateoamero on 2017-10-16
Hello I acquired an old Toshiba-Satellite A-100 laptop with Windows XP on it, the computer is pretty much worthless with XP, but I wish to extend its life by removing windows entirely and starting over with Lubuntu. I used "Startup Disk Creator" on my other PC with Ubuntu Studio to create a USB installer.

I was able to boot Lubuntu from the USB stick and everything seems fine, but when I go to actually install it it just hangs on the "Preparing to install Lubuntu" screen. This is the screen where you choose whether or not to Download updates and Install third-party software. When I click continue it just loads and loads and loads to no avail. I haven't waited for more than 15 minutes before, but I don't think that it should take that long. I have also tried to uncheck the updates and software, and it does the same thing.

Have any of you had this problem before? I am admittedly a noob, so any advice would be appreciated.
 I should also add that I also checked the disc for defects and it said that there was none.

EDIT: I waited for 30 minutes and finally I was able to continue, but shortly after I clicked to erase the hard disk and install Lubuntu it told me that the installer encountered an error copying files to the hard disk:
[Errno 5] Input/output error.   So I almost made some progress, but have a NEW problem, surely I should be able to fix this one as well.

---

### Post by QIII on 2017-10-16
Hello!

Please use the default font and color unless you want to draw attention to a very specific part of your post.

Thanks!

---

### Post by sudodus on 2017-10-17
How much RAM is there? Maybe it is not enough for the installer to work.

If less than 1 GB RAM, it is better to use a **Lubuntu alternate iso file** instead of a Lubuntu desktop iso file.

[hr][/hr]
If less than 512 GB RAM, you may be able to install Lubuntu, but it will be difficult to use the computer for typical tasks like browsing the internet, because many modern web pages need a lot of RAM to work well.

An alterntive is to try to find [second hand] RAM memory sticks that match the computer and increase RAM to at least 1 GB.

You can try to use a linux distro with an ultra light foot-print, for example Puppy Linux or Tiny Core.

[hr][/hr]
See this link for more tips: [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by inerstellar-cowboy on 2017-10-17
Hello there! I am a noob myself

Luckily I have experience reviving a laptop from 2004 with lubuntu.

It would be helpful as the person said above to know the specs of your machine

I have to say that my experience with lubuntu was mixed, but that was probably bc of the severe limitations of my HP Compaq nc 8230..
40Gb HDD
512mb ram
intel pentium m

---

### Post by mateoamero on 2017-10-20
I thought I fixed the problem when I got past the Preparing to Install page, but I have not been successful in getting past the Errno 5 during the actual installation. I have tried both Lubuntu and Linux mint, and had the same Errno 5 / installer crash. ... I have also tried the lubuntu alernate ISO and got a similar error during the installation.   So I am thinking that maybe the hard drive may acquired some damage over the years. What do you guys think?

Specs according to Toshiba website are:
CPU: 2.00 GHz
RAM: 1 GB DDR2 667
HDD: 120 GB 5400 RPM
Video: 256 MB GeForce Go 7600

---

### Post by sudodus on 2017-10-20
There *may* be problems with the nvidia geforce graphics card.

Please describe in detail how it fails and the full error output.

---

### Post by mateoamero on 2017-10-20
I just tried the alternate ISO one more, it failed during the install and told me to check /var/log/syslog so I did, and it says:

Sub-process /usr/vin/dpkg returned an error code (1)
error: exiting on error base-installer/kernel/failed-install
WARNING **: Configuring 'bootstrap-base' failed with error code 1
WARNING **: Menu item 'bootstrap-base' failed.
INFO: Modifying debconf priority liimit from 'high' to 'medium'
debconf: Setting debconf/priority to medium

---

### Post by sudodus on 2017-10-20
This seems to be an error that is beyond my experience.

I hope someone else will recognize it and help you.

---

### Post by mateoamero on 2017-10-20
Dang well thanks anyways! I will scour through google now.

---

### Post by mörgæs on 2017-10-20
> **mateoamero said:**
> 
[Errno 5] Input/output error. 

This means a hard disk error. I wouldn't store important data here but you might be able to install the operative system. 

I suggest that you do a live boot without installing. Here you partition your hard disk in a way that the first say 20 GB are unused. The partitions to which you install should begin after the 20 GB mark.

Are you able to install now?

---

### Post by mateoamero on 2017-10-20
Interesting, I tried that and now I get, "An attempt to configure apt to install additional packages from the CD failed"
It told me that the installation finished, I restarted, and it just boots to a black screen with a blinking underscore. Do I need to manually configure some sort of boot menu or something? or did the installation actually fail?

By the way for the first 20 gigs, by "unused" did you mean unallocated? because thats what I have it as right now right now.

EDIT: Tried again and now I get an [Errno 30] Read-only file system: '/target/boot/vmlinuz-4.10.0-19- generic'

So it appears that the hard disk is not in good shape. I wish there was some way to at least install the OS. I was never planning on putting important information on the laptop. It'd just be nice to have a functioning (free) laptop to be able to take places, rather than lug my desktop.

---

### Post by kurt18947 on 2017-10-20
I'm don't know if Lubuntu comes with gnome-disk (disks) app, it likely doesn't being a 'lightweight' O.S.. If there were a way to install and run 'disks' or an app with similar function, you could check the SMART status and see if there were disk errors. I'm not positive but I think Xubuntu includes the 'disks' app on the live image. On an older machine, it's well to check the condition of the RAM and hard drive. Hard drives don't live forever and a spinning hard drives in a portable machine that may be moved or bumped while reading/writing is at greater risk IMO.

I had a somewhat similar problem with an older machine born with Windows ME so vintage around year 2000. It simply would not install Lubuntu, Xubuntu or their variants. I think it was a video incompatibility but I was able to install MX15. I would think any machine that would run Windows XP should be able to install the lighter *buntus. SODIMMs are pretty cheap on Ebay if you want to upgrade this machine and if adding memory doesn't involve much disassembly.

---

### Post by sudodus on 2017-10-21
Lubuntu does come with Disks alias gnome-disks. And I think it is a good idea to use it to check the S.M.A.R.T. data of the disk. See this link,

[Answer at AskUbuntu - scroll to 'Maybe the disk hardware is damaged'](https://askubuntu.com/questions/948036/reformating-hard-drive-after-malware-damaged-boot-sector/948560#948560)

---

### Post by mateoamero on 2017-10-24
Sorry for the late reply, it is not often I have the time to mess with this old laptop. I have tried the Disks program, and initially it said "Disk is OK" but with a few thousand or so "Bad sectors".

I then tried doing a Self-test, and now it says SELF-TEST FAILED. I have tried the Short, Extended and Conveyance tests.  I am not knowledgeable at all of this type of stuff so I am not really sure what this means. Does it mean that this laptop is trash? If so it is no big deal to me. The laptop is definitely not worth trying to replace the hard drive in my opinion if that is the only option.    Could I try making the proposed linux partition even smaller and then installing?

---

### Post by sudodus on 2017-10-25
I'm afraid that the hard disk drive is bad. It might not be worthwhile to buy a new hard disk drive, but you might find a used one in another old computer.

---

### Post by mörgæs on 2017-10-25
> **mateoamero said:**
> 
By the way for the first 20 gigs, by "unused" did you mean unallocated? because thats what I have it as right now right now.



You could try to leave a big chunk (80 GB) unallocated and see if it works better using only the last 40.

Have you tried installing from the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD")?

---

