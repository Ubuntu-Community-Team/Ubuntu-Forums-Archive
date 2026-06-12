---
title: "Serial ATA RAID Stripe Failed on install?"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by zakeen on 2010-04-13
I get this error when trying to install 10.04 :(

"The ext4 file system creation in partition #1 of Serial ATA RAID isw_dceecfcacg_Volume0 (stripe) failed".

I have a sony Vaio with 2x256gb SSD running RAID0.

What do you guys think it could be?

---

### Post by zakeen on 2010-04-15
rain drops keep falling on my head........ :) bump.

---

### Post by srs5694 on 2010-04-15
I probably won't be able to help, but you need to give more information than this. Try posting the exact command that produced the error. You may also need to post the commands that led up to it and provide a better description of your RAID array. In fact, I strongly urge you to read [this Web site](http://catb.org/~esr/faqs/smart-questions.html) for information on how to get answers when you post questions.

---

### Post by ubungus on 2010-04-30
Well I reckon I've found the "issue". When fdisk is used to make partitions, they are referred to as 1,2 and 3 (depending on what you have).

However, when you format them you must use whatever /dev/mapper/XXX is.

So in my system, 

/dev/mapper/isw_bhaigfbah_GTR is the Stripe array.

In fdisk I created partitions for / and swap as

/dev/mapper/isw_bhaigfbah_GTR1
/dev/mapper/isw_bhaigfbah_GTR5

However in /dev/mapper they show up as

/dev/mapper/isw_bhaigfbah_GTRp1
/dev/mapper/isw_bhaigfbah_GTRp5

So when the installer tries to mke2fs the partitions, it throws error in /var/log/messages "Not found"

So I ended up using the guide for FakeRAID installation which works fine if you take into account the ACTUAL mappings.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Perhaps, it could be accounted for using symbolic links in /dev to overcome this problem for now?

---

### Post by fuzzybannana on 2010-04-30
Seems he is correct and problem is when gparted creates partitions the device path is different then what gparted expects. (xxx_0p1 instead od xxx_01)

Using parted -mkpart to partition from terminal and then rebooting remapped my devices to correct path.
Then by setting partitioning to manual during installation it installed correctly.


Hope this help.

---

### Post by Deihmos on 2010-05-04
> **zakeen said:**
> I get this error when trying to install 10.04 :(
 
"The ext4 file system creation in partition #1 of Serial ATA RAID isw_dceecfcacg_Volume0 (stripe) failed".
 
I have a sony Vaio with 2x256gb SSD running RAID0.
 
What do you guys think it could be?
 
Same exact problem. it worked fine in 9.10 but 10.04 killed it completely.

---

### Post by dserbia on 2010-05-06
**Exactly** the same. I'll try it and see if it helps.

---

### Post by andrewjs18 on 2010-05-08
I had this problem with 10.04 also except I was trying to install ubuntu on a raid 1 array, not a raid 0.  what I did was download ubuntu 9.10 and it worked flawlessly..didn't have any problems installing the os on raid 1 and didn't have to do any 'fake raid'.

---

### Post by useful1 on 2010-05-14
Has guys, is there a work around for this?
 
Im a ubuntu rookie/noob.  Pretty good with windows, havent used linux at all in a decade.
 
Anyways, I have a new computer running an Athlon X3 440 that i assembled with a Gigabyte MA78LM-S2H motherboard along with 2 hard drives configured for RAID 0, (two hard drives acting as one in noob talk).  
 
So in the mean time, I figured, I'd tried ubuntu 10.04, since its been a while Ive tried to install a linux machine.
 
I downloaded the 10.04 .iso, burned it onto a CD, and booted it in the CD-ROM drive so that it would install at boot.  I went through, the "Welcome" screen, the "Where are you?" screen, "Keyboard Layout" screen, then the "Prepare disk space"
screen.  
 
Now this area, I chose, "Erase and use the entire disk".
 
After this is the "Who are you?" screen, and I filled out the login name, password, name of computer, and picked Log In Automatically.  
 
Finally, I come to the "Ready to Install" screen, and I clicked Install.
----
After this, it starts to install with the loading bar slowing moving up, 
Then the error window pops up showing "Failed to create a file system"
 
The ext4 file system creation in partition #1 of Serial ATA RAID pdc_fhfebjal (stripe) failed.
---
 
And basically, I cant install ubuntu anymore because of this.  Is there a work around that a simple windows user like me can understand?  Bear in mind, Im a windows guy, so any linux lingo would probably go over my head.
 
Thanks guys,
 
- U

---

### Post by Deihmos on 2010-05-14
Raid is pretty much broken with 10.04/ You can install 9.10 to a raid drive then upgrade to 10.04. That's the easy way to get it on a raid drive or you can install 10.04 to a single drive that's not in raid.

---

### Post by psusi on 2010-05-14
The work around is to manually partition with gparted, then have the installer use the existing partitions.  I believe that you also need to partition but not format in gparted, then in a terminal run sudo dmraid -an and sudo dmraid -ay, then fire up the installer and have it install to the existing partitions.

---

### Post by Deihmos on 2010-05-14
> **psusi said:**
> The work around is to manually partition with gparted, then have the installer use the existing partitions. I believe that you also need to partition but not format in gparted, then in a terminal run sudo dmraid -an and sudo dmraid -ay, then fire up the installer and have it install to the existing partitions.
 
That does not work.

---

### Post by ronparent on 2010-05-15
I did install 10.04 to a raid 0 and it was a bit complicated but it works.

There were and still are complications, but I can and do run a dual boot with Win7. I had almost given up after trying the Alpha2 thru RC without a solution in sight. My main problem was mostly fixed with the update to the 2.6.32.21 kernal which allowed my signature machine to boot without the nodmraid parameter (I couldn't figger how to install to a fakeraid if I had to use that parameter to boot).

Now the cautions. If you need to create partitions that will result in more than four total primary partiotions on the raid0 drive you will get an error and the install will stop.. If you need to pre-partition, best use a prior version, maybe 9.04 or before, to create a partition to install to. Note that gparted in 10.04 doesn't see the raid even when /dev/mapper is populated. For some reason the partitioner run from ubiquity does see the raid drive so in my case the installer ran properly. Note: I formatted to ext3 because I ran into errors trying to use ext4.

Secondly, my grub install had a fatal failure because it was set for bootloader on the default raid drive. I was able to fix by using another grub2 on another install to boot the raid0 install and setup the grub to write a MBR on a non raid drive (which I set in bios as the boot drive).

There are a bunch of other factors which I am still trying to untangle enough to write a coherent bug report. Don't expect to be able to use gparted to do anything with the raid0 (or the new Disk Utilty for that matter)! In my situation neither saw the raid - only unallocated drives.

I guess the bottom line is that if you are lucky you can install and operate 10.04 in a raid system. There are still bugs, pitfalls and pratfalls involved however. I wouldn't suggest renaming the symbolic links found in /dev/mapper because that also seemed to present me with unwanted outcomes. Good luck.

---

### Post by craigels39 on 2010-05-20
I was able to work around this in 10.04 using the network/alternate installation.  I'm guessing you could use this on the desktop version by using an X terminal or 'CTRL+ALT+F2' to get to a CLI.


   -Setup your partitions normally, accept the config and let the partitioner fail the first time
   -Use 'ALT+F2' to grab a console
   -Navigate to '/dev/mapper', do a quick 'ls' and notice the partition numbers that it has created (ie: isw_XXX_XXXp#)
   -Create a symbolic link for each partition to the location the partitioner expects (ie: 'ln -s isw_XXX_XXXp# isw_XXX_XXX#') If you are using a desktop versions, you may need to sudo so that the links are created as root.
   -Use ALT+F1 (CTRL+ALT+F7 for desktop versions) to go back to the text (GUI) installer and have it retry to write the partitions
   -At this point, the partitions formatted properly for me and I was able to continue installation.

---

### Post by craigels39 on 2010-05-20
Scratch that, the links and mappings do not come up properly on the reboot.

---

### Post by veredox on 2010-05-24
> **Deihmos said:**
> That does not work.

I just had success by adding a manual format before the running of the installer.

So the process is:
1) sudo gparted [your device: /dev/mapper/xxd]
2) Get your partitions how you want them
3) sudo dmraid -an
4) sudo dmraid -ay
5) sudo mkfs -t ext4 [your disk: /dev/mapper/xxd1]
6) Run the installer.

Good luck.

---

### Post by clyrrad on 2010-06-14
> **craigels39 said:**
> I was able to work around this in 10.04 using the network/alternate installation.  I'm guessing you could use this on the desktop version by using an X terminal or 'CTRL+ALT+F2' to get to a CLI.


   -Setup your partitions normally, accept the config and let the partitioner fail the first time
   -Use 'ALT+F2' to grab a console
   -Navigate to '/dev/mapper', do a quick 'ls' and notice the partition numbers that it has created (ie: isw_XXX_XXXp#)
   -Create a symbolic link for each partition to the location the partitioner expects (ie: 'ln -s isw_XXX_XXXp# isw_XXX_XXX#') If you are using a desktop versions, you may need to sudo so that the links are created as root.
   -Use ALT+F1 (CTRL+ALT+F7 for desktop versions) to go back to the text (GUI) installer and have it retry to write the partitions
   -At this point, the partitions formatted properly for me and I was able to continue installation.

This worked for me, I tried for almost 2 days to get 10.04 Lucid to install and I could not for the life of me get it working.  I had 2 RAID 1 arrays setup (Volume0 is Ubuntu) and (Volume1 is for Data) - so I had 2 different RAID 1 Arrays setup.  I also had to use the Alternate CD to get this working.

So in summary, I had to download the 64bit Alternate CD, then I needed to do the steps identified by craigels39 and finally I was able to get Lucid installed and working.

Thanks for the tips craigels39 - but really for a Stable release of Ubuntu there should not be problems like this with the installer..... just my two cents. ):P

---

### Post by jkeeton on 2010-06-20
I was able to get around this by getting to the same failure as the OP,  then hitting Alt-f2, and renaming the /dev/mapper/BLAH**p**x to  /dev/mapper/BLAHx, where x was multiple entries. I tried to link  them,(soft and hard, but it said I had no disks) then back to the  installer, hit continue, and select the format option again.. All was  good, the system came up afterwards, and dmraid said it was good to go. 

john

---

### Post by ultione on 2010-06-22
> **jkeeton said:**
> I was able to get around this by getting to the same failure as the OP,  then hitting Alt-f2, and renaming the /dev/mapper/BLAH**p**x to  /dev/mapper/BLAHx, where x was multiple entries. I tried to link  them,(soft and hard, but it said I had no disks) then back to the  installer, hit continue, and select the format option again.. All was  good, the system came up afterwards, and dmraid said it was good to go. 

john

For others installing Ubuntu Server 10.04 on a RAID 1 mirror setup, you may encounter that you cannot boot after rebooting.

Had been pulling a lot of hair out to get it to boot from the RAID setup.
What I did, was boot from the CD and go to rescue mode.

At the stage where it asks you where you want to run your "/" root from, select /dev/mapper/BLAH**x** where you install root to and you should have an option to reinstall GRUB loader.

Select that option and when prompted to put the boot location, type in your raid device location, that is /dev/mapper/BLAH (do not use /dev/mapper/BLAH**x**)

Hope this helps others that is not installing using the desktop version.

---

### Post by shigeo_savant on 2010-08-30
the following workaround has worked with me.

-) chose "try ubuntu" instead "install ubuntu". that way you can open a console next to the installer
-) open a console and become root (sudo bash)
-) start the installer, click throug it and watch it fail
-) in the console 'cd /dev/mapper', and then hard link the new devices after it failed. the link name should be the name of the expected devices in /dev/mapper.
soft links don't work!

(you may need to reinstall grub after that, i recommend the super grub cd).

there is a new release ubuntu 10.04.1 out. it looks like it's fixed there but haven't tried it yet.

good luck.

---

### Post by shigeo_savant on 2010-12-22
hi.
just wanted to share my experience with you, maybe it will become useful for someone.

-) ubuntu 10.04 changed the mapped name of my fakeRAID during install. the above mentioned trick with hard-linking the expected name worked for me once but i couldn't reproduce it on another machine.

-) it seems to be a bug (i think in the device mapper) which has been fixed in 10.04.1.

-) both 10.04 and 10.04.1 experienced boot problems, because the grub is not correctly installed. workaround: boot the system with the "super grub cd", then execute "grub-install /dev/mapper/mapped-raid".

i think the grub install issue is expected to be fixed in 10.04.2 (can't find the appropriate bug right now...)


hope this helps someone.

---

