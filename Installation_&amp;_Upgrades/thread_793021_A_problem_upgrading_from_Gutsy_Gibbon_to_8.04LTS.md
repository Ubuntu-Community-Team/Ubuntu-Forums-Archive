---
title: "A problem upgrading from Gutsy Gibbon to 8.04LTS"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Ian Drummond on 2008-05-13
I am totaly new to Linux in general and Ubuntu in particular but hugely impressed with this software so far! I have downloaded successfuly many updates with no problems but this:- my installation is "up to date" according to the INFO given but will not update to 8.04LTS. It says something about being unable to calculate the changes and advises me to upload to you some files regarding the failed upgrade. I presume I will have to uninstall some stuff in order to upgrade but I don't know what exactly. I would be most grateful for assistance!

Regards,

Ian

---

### Post by Dirren on 2008-05-13
Hi,
I have the same problem but going from 7.04 to 7.10. I'm trying to come all the way from Edgy Eft (6.10) to Hardy H.
Yesterday I went to 7.04, and I was thinking to take the next step today, but 
Upgrade Manager bails out with that same message and ask me to report a bug on the upgrade manager package. 
Reading the logs it seems I have a horseload of broken dependencies, and I figure that is what causes the upgrade to fail.
Any clues on how to proceed or correct the broken deps?
Thanks,
:-JonasF

---

### Post by dstew on 2008-05-13
I think the installer wants to remove the nvidia restricted driver package, but it is in use by the gnome display manager, so if it gets removed, the computer will no longer be able to run the desktop. Ubuntu will not install this package automatically, because of the license restrictions.

One way to try to get around this is to reconfigure your xserver to use a different display driver (temporarily -- you can install the restricted driver once you get the new system installed.) From the desktop, you can go into the 
System --> Administration --> Restricted Drivers Manager and disable the nvidia restricted driver. That might be enough. If not, then on the command line, enter```
sudo dpkg-reconfigure xserver-xorg
```When it gets to the part about the display, pick either the linux native **nv** driver, or the **vesa** driver. You will still get a useable display, but no 3D effects. See if this works. I recommended it to a forum poster before, but he never said whether it worked or not.

---

### Post by Dirren on 2008-05-13
I got a hint that the nfs-common package was "held back". Don't know why or how that was so, but I installed it, and now the upgrade has rolled by that nagging failure to "calculate the upgrade". 
Crossing my fingers it will come all the way through.

BTW the appropriate place to post the bug-report (and files in /var/log/dist-upgrade) is on [ubuntu launchpad.net]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=update-manager").

---

### Post by Ian Drummond on 2008-05-14
Thanks "Dstew" for your help thus far. I uninstalled the Nvidia driver as you suggested (thankfully the GUI came up OK) and I re-tried downloading the 8.04LTS upgrade. I got further with it than the last time. By this I mean that a new problem surfaced! I apparently do not have enough space for the upgrade. This cannot be true because there is plenty! I apparently need another 1073mb to upgrade. I read the help files and downloaded the Gnome partition editor which it suggested. This looks scarey! I am unsure where exactly on my hard drives the Ubuntu install is on my machine. How can I work this out? (In windows explorer I would find it easily) Then how exactly do I use the Gnome partition editor to give me more space? If I can ask another question, how do I re-mount an unmounted drive? In the Gnome app there is an unmount button but no mount button.

P.S. I did say I was new to Ubuntu and as you can see, I did not lie.

Regards and thanks in anticipation,
Ian

---

### Post by dstew on 2008-05-14
What do you see as your current disk usage? I think there is a graphical tool Disk Usage Analyzer in the System --> Administration menu. From the command line, to look at disk usage, use the **df** command.

---

### Post by Ian Drummond on 2008-05-14
Thanks for the swift reply! I have attached the INFO re disk usage as given by the Disk usage analyser. Being a music freak there are many large hard-drives on the system.

Regards,

Ian.

---

### Post by dstew on 2008-05-14
I think your root filesystem /dev/sda7 is too congested. You only have 1 Gb of free space, and you probably need more. You can try to expand the root partition at the expense of some of the other partitions on sda. I think GParted can do this for you. You can also try to free up space on /dev/sda7 by various methods. Here is a [great thread on freeing up space in Ubuntu]("http://ubuntuforums.org/showthread.php?t=140920").

---

### Post by Ian Drummond on 2008-05-14
When I try to "unmount" the /dev/sda 7 partition in order to re-size it I get the following message,

"The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually." 

I have no clue how to do this, any help would be appreciated greatly!

Thanks in anticipation,

Ian.

---

### Post by dstew on 2008-05-14
You cannot partition a mounted filesystem, and if it happens to be your root filesystem, you cannot unmount it!

The solution, of course, it to partition the filesystem using a Live CD system, either the Ubuntu Live CD, or a special purpose [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). You can also partition during installation. But, I like to partition before installation.

---

### Post by lavinog on 2008-05-14
dstew is right, but I would recommend that you run gparted and send a screenshot first so we can help you.
Many times expanding a partition will require shrinking or moving another...this can get messy and time consuming (expect it to take over an hour if you have to move a couple of partitions around)
also a mistake will destroy lots of data...fortunately gparted is user friendly.

also when you resize your root partition make sure you give about twice the extra space that the updater requested...I was told I needed 1600 megs and i gave it 2000 megs, then it said i still needed another 600 megs...go figure.

---

### Post by Ian Drummond on 2008-05-14
Well from what you have said it seem that the computer shop which did the install for me has not given the root partition enough "breathing space" during the install. I have the original Gutsy Gibbon disk, could you "talk me through" the process of doing what needs to be done? Thanks for your patience, I did not realise that the problem would be as complicated as it seems to have become. I do however think that it will be worth solving to make this great software work as well as possible.

Thankd!

Ian

---

### Post by Ian Drummond on 2008-05-14
Well it would seem that the computer shop who did the original install has not left enough "breathing space" on sda7. I have the origional Gutsy Gibbon 7.10 disk but the thought of getting in to partitions makes me somewhat fearful. Would it be more sensible to re-install, from scratch the whole thing? Or is moving partitions and re-sizing a realistic option. The present install works perfectly and downloads all the updates exept the 8.04LTS. Should I simply bite the bullet and accept the limitations of the small boot sector partition? What to do?

ian.

---

### Post by Ian Drummond on 2008-05-15
Hi Lavinog, thanks for your advise also,Dstew has been so very helpful also! I attach the screen-shot of the partition editor for your scrutiny and hopefully, advice

Thanks!

Ian

---

### Post by dstew on 2008-05-15
Here's what you need to do. First, select your /boot partition, /dev/sda6, and resize it. Shrink is to about 500 MB, leaving unallocated space after the partition (to its right on the grapical display).

Next, resize your root partition, /dev/sda7, to take up all the unallocated space that will be in front of it. After that, it should be about 10 Gb in size, and you will be able to upgrade.

---

### Post by Malac on 2008-05-15
You could just try editing your /etc/apt/sources.list and changing all the "gutsy" to "hardy" then sudo apt-get update or Synaptic hit Reload button and give it a go this is what I did and it worked fine.
 
However this is not one of the recommended methods and I don't know if there would be any "bad" side-effects.

---

### Post by Ian Drummond on 2008-05-15
Thanks Dstew for the info but how do I unmount the boot partition in order to shrink it? the Gparted partition editor wont allow me to because it is "in use" I anticipate that you will tell me to use the original Gutsy disk, if so, what exactly do I do?

Ian.

---

### Post by dstew on 2008-05-15
You need to boot the system using a Live CD of some type that has a partition editor program on it. You can boot the Gutsy Live CD, and use the Gnome Partition Editor, which I think is in the System --> Administration menu.

If for some reason the hard disk partitions get mounted onto the Live CD file system, the icons will usually appear on the desktop. You should be able to right-click and unmount them.

---

### Post by Ian Drummond on 2008-05-16
Guys, I really do appreciate your time and patience in dealing with the problem I am having! I have located Gparted on the original Ubuntu Gutsy Gibbon 7.10 disk. it is at - /media/cdrom0/pool/main/gparted . I suppose I can use this to resize the partitions?  The next question is how to get the 7.10 disk to start at boot up. It does not come up on it's own and the screen info only gives me 2 options F2 - steup or F12 boot from the network. What do I do? Once again, please forgive my ingorance and once again many thanks to you all for sharing your knowledge!

Ian

---

### Post by dstew on 2008-05-16
What I meant is *boot* the live CD, and then run the partition editor from the Live CD desktop.

Press F2 to get into your BIOS setup screen. Find the menu that is usually labeled Boot and change the boot order so that the CD-ROM drive comes before the hard drive. Note: You might need to change it back after you have installed to get the hard drive to boot again.

---

### Post by Ian Drummond on 2008-05-16
Success! at least as far as re-sizing the partitions is concerned. Thank you so very much for your help and advice. Although it said on-screen that F2 took me into setup it turned out to be F1 (It took some time to sus this out) eventually I managed to boot from the DVD drive and used Gparted to do the resizing. I must say it was a little scarey and not something I really wanted to get into but having done it once, I would not be reticent again. All that remains is to download the upgrade to Hardy Heron and the job will be complete. I will let you know how it goes. Thanks to all but especially Dstew for your knowledge and advice. It re-kindles my confidence in the generosity of human nature. Thank you so much!

Ian.

---

### Post by tagudat on 2008-12-22
Hi,

I recently joined the forum and am not a computer specialist.
Have the same problem updating from 7.10 to 8.04 even so my graphic card is disabled.
Are there other bugs / solutions to pass this 'calculating 'error?

Thomas

---

