---
title: "Urgent help needed"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Janeleaper on 2008-07-18
I set up my Dell Inspiron loaded with Ubuntu 3 days ago and had no problems.  This morning I got a message to install Hardy Heron. I started the download and all seemed well.  Then the installation stalled saying 4 minutes to go. 

After about half an hour I tried to use pidgin to get some help on the IRC channel, but I've never used this before and could not get it working.  

I turned the computer off at the tower.  Turned it on again and I seem to have completely lost everything.  The log in came up o.k. but after that I just have a blank brown screen with a large black margin to the left hand side.

What do I do?  I have no technical know-how - so simple language please!

---

### Post by Pumalite on 2008-07-18
Do a clean install of Hardy Heron.

---

### Post by Janeleaper on 2008-07-18
Thank-you, but how do I do that?

---

### Post by Pumalite on 2008-07-18
Download the iso from here>
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Burn it to disk.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Install. Go Manual and use the old partitions. You can ignore /swap

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Janeleaper on 2008-07-18
I have a disc for Ubuntu version 7.10, which Dell supplied with the pc.  I've tried putting it in the disc drive but nothing happens.

---

### Post by Pumalite on 2008-07-18
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your hard drive. Format ext3.
Install Ubuntu.

---

### Post by mocoloco on 2008-07-18
> **Pumalite said:**
> Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your hard drive. Format ext3.
Install Ubuntu.

Why download and burn a separate iso when the Ubuntu 8.04 liveCD has gparted?  Is there anything better about the gparted live?
I would say just download and burn the 8.04 (Hardy) iso and use it's option to take over the entire hard drive.  If you just installed 3 days ago it sounds like you wouldn't have personal data to lose, right?

---

### Post by Pumalite on 2008-07-18
Gparted is a newer version, more flexible, more powerful AND it works with unmopunted partitions/drives. Besides, the OP couldn't boot his 7.10 disk.

---

### Post by Janeleaper on 2008-07-18
Thanks for all this information.  I had to go out for a while, but I'm back now.

Sorry, I realise this is going to sound really stupid, but my success rate for 'burning discs' on my XP computer is not good.

Could I download Hardy Heron onto a memory stick and install it from there?

What I've done is re-install version 7.10.  The only problem I had, was with the partitioning.  The first attempt failed, but the second was o.k.

Now I'm trying to download Hardy Heron again.  I thought it was worth one more try.

---

### Post by kspncr on 2008-07-18
If your re-install of 7.10 was successful, you shouldn't need to waste a CD on installing Hardy; you can upgrade from update manager.

---

### Post by Pumalite on 2008-07-18
> **Janeleaper said:**
> Thanks for all this information.  I had to go out for a while, but I'm back now.

Sorry, I realise this is going to sound really stupid, but my success rate for 'burning discs' on my XP computer is not good.

Could I download Hardy Heron onto a memory stick and install it from there?

What I've done is re-install version 7.10.  The only problem I had, was with the partitioning.  The first attempt failed, but the second was o.k.

Now I'm trying to download Hardy Heron again.  I thought it was worth one more try.

A clean install is always better. Download ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install. Go to Mode>ISO>Burn Select 1x for speed.

---

### Post by avtolle on 2008-07-18
Hopefully, you fully updated 7.10 before beginning the upgrade to 8.04....

---

### Post by Janeleaper on 2008-07-18
That is precisely what I have done.

And I still have problems.  This time the upgrade got as far as re-starting the computer.  The Dell screen comes up, then the Grub screen, then the Ubuntu screen.  Then it reverts to the Dell screen, the Grub Screen and the Ubuntu screen again and so on ad infinitum.  

So, I'm going to have to reinstall 7.10 again.  I guess this time I'll do without Hardy Heron.

Can you tell me how I should deal with partitioning? Last time I could not do it manually, and I tried to use the whole disc without success.  It gave me 50%.  How do I erase the disc?

---

### Post by Pumalite on 2008-07-18
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your drive and format ext3. Then install. Use Guided>Use the Entire Disk.

---

### Post by sdowney717 on 2008-07-18
I wonder if it is a video issue.
The login screen is available, so I suppose you can get to a terminal
What is your video card?

Run Wubi Hardy on NTFS with windows or
setup 7.04 then virtualbox and then run hardy.

---

### Post by Janeleaper on 2008-07-18
Thank you everybody.

Sorry, but I could not even back up my digital photos on a disc successfully, so I'm not going to try to download an OS onto one. 

The first time I tried to install Hardy Heron I'd fully updated 7.10.  The second time, I did not install updates before downloading HH, so I've tried it both ways. I'm done with HH for the time being anyway.  

I'm trying to re-install 7.10 again. At the partitioning screen I get one option only which is :

/dev/sda3 ext.3 /media/sda3  4038 MB used - 3200 MB

When I select "forward" I get the message:

"You need to specify a partition for the root file system (mount point "/") with a minimum of 2 GB, and a swap partition of at least 256 MB.  You may also set up other partitions if you wish"

On selection Mount I get the following boxes:

New partition size in megabytes (current setting 4038 )
Use as  (current setting Ext 3)
Mount point /media/sda 3

What should I enter please?

---

### Post by Janeleaper on 2008-07-18
I should add that if I leave the settings as they are and try to go forward, I get the message

"No root file system is defined.  Please correct this from the partitioning menu."  I have no idea what this means.

---

### Post by falcon61102 on 2008-07-18
When you are selecting your partitions in the partition manager, there is an option to select the mount point.  Before you can proceed on with the installation, you need to select one of the partitions to have the mount point of "/" from the drop down list.  When you click on edit partition, you should see where it says mount point.  Another partition you need to have is the SWAP partition and this partition is normally double the size of your RAM.  

Many people also like to have their home partition seperate and you can do that by creating a third partition and selecting "/home" for the mount point.  When you finish you should have something like:
```

Partition   Mount Point   Size(example)
 /dev/sda1  /             4000 MB
 /dev/sda2  /home         10000 MB
 /dev/sda3  SWAP          784 MB

```

---

### Post by Janeleaper on 2008-07-18
Hi.  I've successfully re-installed 7.10.  I used the 'use whole disc' option on partitioning.  Thank-you to everyone for your advice.  I might have a go at making a disc of Hardy Heron sometime and try installing it again.

---

### Post by falcon61102 on 2008-07-18
As I believe it was pointed out previously, if you have 7.10 up and running, you should be able to update your system to Hardy without reinstalling.  You should be able to download the updates directly.

---

### Post by Janeleaper on 2008-07-18
I should be able to, but I can't.  I've just made a third attempt.  This time was like the first.

I'd successfully installed 7.10.  I'd updated 7.10 and restarted.  I then attempted to use update to install Hardy Heron. This time it got to 2 minutes to go on installation before stalling.  When it stalls it starts up terminal, for some reason. 

I am now reinstalling 7.10 for the third time today.

---

### Post by falcon61102 on 2008-07-18
Does it give you any type of error for the install?

---

### Post by Janeleaper on 2008-07-18
No, it just stalls. Period. First and third attempts - it was towards the end of installation.  Second attempt it appeared to install correctly and restarted but then went into a loop of Dell screen to Ubuntu screen and back again, that I described in my post above.

---

### Post by falcon61102 on 2008-07-18
Wow, that is really odd and I have no idea, sorry.

If you really are up to testing your patience, you could try downloading a Hardy Live Cd and installing from that, otherwise, I don't know.

---

### Post by Pumalite on 2008-07-18
Clean the lens in your burner. Check CD integrity before you install.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Janeleaper on 2008-07-18
Pumalite - just want to say that you have probably been right all along.  Your suggestion of the cd was what I should have done. I'll think about doing it in the future, but for now I think I'll stick with 7.10.

---

### Post by Pumalite on 2008-07-18
Good luck!

---

### Post by sdowney717 on 2008-07-18
get 7.10 working. 
Download the CD for Hardy
install virtualbox
With virtualbox you can install and run multiple different OS's at the same time. They run in a window, It is rather interesting.
You can then run virtualbox and create a virtual Hardy to see if it works!

---

