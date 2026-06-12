---
title: "cannot use the installer disks"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Carus on 2010-01-19
i downloaded ubuntu-9.10-desktop-i386.iso
burned it, and put it in the computer, but every time i try something it wont work
i select, try ubuntu without any changes to your computer
and it says
> mount: mounting /dev/sr0 on /cdrom failed: invalid argument
and then it says unable to find a medium containing a live file system

and it shows the same error when i hit, install ubuntu, and when i select check disc for errors

weird thing also, my friend downloaded the file too, about the same time

and he cant install it or use the disc he made either, hes running into his own set of errors, cant install or really use the cd in any way

we get to the first menu, do decide what to do, but every option fails

---

### Post by sliketymo on 2010-01-19
Are you sure you have your bio's set to boot the cd first ?

---

### Post by JodiSte on 2010-01-19
Make sure you actually copy it as an image to the cd and not just the files.

When you insert a new blank cd a message will pop up asking you if you want to burn something to that disc.
Close all of that, go to the iso file you downloaded, right-click and choose, write to disc. This will actually write the whole ISO as an image to the cd.

When this process is finished, you should be able to start your machine from CD and it should work.

Check the instructions on the Ubuntu download page.

Hope this helps.

---

### Post by keling on 2010-01-19
Where you want to install it, entire disk or in a secondary partition with an existing windows OS ?

Have you check that there are no errors in the hard drive?

I had same problem a few days ago, I had three partitions, 
partition 1 : Windows
partition 2 : Linux  ( with some experiments ) my aim it was to reinstall it, happened same to you
partition 3 : for Data

I solve it just preparing the partition in  which I wanted to install my ubuntu:
STEPS
install ubuntu   -> unable to find a medium containing a live file system
Partition Magic ->  delete partition 2, logical volum (it contained swap and / filesystem )
 install ubuntu and success

Hope that can help you

---

### Post by blackened on 2010-01-19
If you downloaded from the website, then you should run the file against the checksums provided to insure the integrity of the downloaded data. If the file is corrupt, then you must re-download it. I suggest using bittorrent to get the iso as it checks data integrity as it downloads.

As was already mentioned, make sure you're burning the cd image, not just a data cd.

Lastly, burn the disk at 1x or 2x speed to avoid problematic results.

---

### Post by tommcd on 2010-01-19
Along with what has already been said, when you successfully manage to boot the Ubuntu live CD and get to this screen:
[http://www.psychocats.net/ubuntu/images/installingkarmic02.png](http://www.psychocats.net/ubuntu/images/installingkarmic02.png)
You should first choose the option that says "check disc for defects". This will verify that all the data on the CD is good. If it passes the check you can then go ahead and install Ubuntu.
Be sure to burn the CD at the slowest possible speed.

---

### Post by Carus on 2010-01-19
Thanks, ill try downloading it on bit torrent, and burning it at a lowest speed possible

to address your concerns:
- the boot order is cd first then hd
- i just right clicked and hit burn disc image in windows 7
- theres just one partition on the target computer, and windows runs fine, i havent come across and hd errors
- couldnt find any checksums on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) but then again, im not sure i would know how to check that
- check disc for defects doesnt even work

ill just download it on bit torrent if it checks integrity automatically, and burn at a slow speed


Thanks everyone for your speedy replies, and a bunch of ideas, I really apreciate it

---

### Post by Xog on 2010-01-19
> **Carus said:**
> Thanks, ill try downloading it on bit torrent, and burning it at a lowest speed possible

to address your concerns:
- the boot order is cd first then hd
- i just right clicked and hit burn disc image in windows 7
- theres just one partition on the target computer, and windows runs fine, i havent come across and hd errors
- couldnt find any checksums on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) but then again, im not sure i would know how to check that
- check disc for defects doesnt even work

ill just download it on bit torrent if it checks integrity automatically, and burn at a slow speed


Thanks everyone for your speedy replies, and a bunch of ideas, I really apreciate it

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

To check the .iso integrity,
Download and install this: [http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

Install the MD5HASH checksum program.

Right-click the ISO file.

Click Send To, then winMD5Sum. (this may take a minute or two)

To compare MD5 hashes, look for the .iso file you downloaded and find its name on: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

it should be something like 8790491bfa9d00f283ed9dd2d77b3906 if you have the ubuntu-9.10-desktop-i386.iso

Once you've confirmed that they both match up, burn the ISO image using the program InfraRecorder ([http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/))
Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog pops up. 

Open Infra Recorder and click the 'Write Image' button in the main screen. 

You can now install ubuntu. If you encounter errors, it's possible your CD drive is messed up.

---

### Post by Carus on 2010-01-21
well, thanks guys for all your help

i downloaded it on bit torrent, verified after the burn,
and it still didnt work on this target dekstop
on a whim i tried it on my laptop, and it worked! great, wonderfull

thanks for your help, i geuss i have see whats up with that other computer...

---

### Post by tommcd on 2010-01-21
> **Carus said:**
> 
i downloaded it on bit torrent, verified after the burn,
and it still didnt work on this target dekstop ...

So what exactly happens when you boot from the CD on the desktop? Does the CD boot to Ubuntu at all? Do you still get the same error messages you reported in your first post? Or different?

---

### Post by Carus on 2010-01-21
ya i still get the same error messages, not even the check disc for errors works - on the desktop
on my laptop it works fine.

---

### Post by blackened on 2010-01-21
Best I can tell is that this is a bug and could be related to a specific piece of hardware (I've seen mention of harddrives, multiple optical drives, and video cards as the culprits). 

Personally, I would start by cycling through the usual suspects of boot options: noapic, nolapic, and acpi=off

Try to boot to the livecd using one of those as a boot parameter on each attempt by highlighting "Try Ubuntu without any change to your computer", then press F6 for a popup of those options. Select the appropriate one, then press enter to boot into a live session.

---

### Post by Carus on 2010-01-23
well i tried the options to no luck, i also removed the quiet splash options

it just keeps ending with this
> 
[     79.365393] ifofs_fill_super: root inode is not a directory. Corrupted media?
mount: mounting /dev/sr0 on /cdrom failed: invalid argument
mount: mounting /dev/sr0 on /cdrom failed: invalid argument

BusyBox v1.13.3 (Ubuntu 1:1.13.3-ubuntu7) built-in sell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system


the mounting failed thing goes on forever upwards

---

### Post by blackened on 2010-01-23
It must be a bug in the way that Ubuntu recognizes your hardware or a problem with the hardware itself. Have you tried using a different optical drive in that same machine?

---

### Post by Carus on 2010-01-23
> **blackened said:**
> It must be a bug in the way that Ubuntu recognizes your hardware or a problem with the hardware itself. Have you tried using a different optical drive in that same machine?

i think the drive is a little messed up, when i went to pull the cd out recently, it was not sitting nicely in the tray, but was kind of jammed in a bit.
unfortunately i don't have another drive yet to test it out.

Thank you for your help

i suppose i can try the usb way of installing

---

### Post by blackened on 2010-01-23
If you have ubuntu installed on your laptop, then you can easily make a bootable USB with the USB startup disk creator that comes with the default install. Just point the program to your iso and off you go.

---

