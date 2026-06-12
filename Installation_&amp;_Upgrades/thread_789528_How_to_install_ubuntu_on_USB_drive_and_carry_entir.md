---
title: "How to install ubuntu on USB drive and carry entire computing system in pocket?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Redrazor39 on 2008-05-10
How do you make it so you can install ubuntu on a USB flash/jump/thumb drive and save all of your documents, settings, and applications to that thumb/flash/jump drive-- but access hardware (screen, keyboard, mouse, etc.) with any computer you plug it into (that it's compatible with)?

Step by step instructions would be greatly appreciated and if they are visually illustrated that would be even better.

Thank you.

---

### Post by esteckis on 2008-05-10
You can read this website. But be sure you have an excellent flash drive with very fast read/write speeds.

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

---

### Post by Herman on 2008-05-10
Just install Hardy Heron in your USB flash memory stick in the regular way the same as any other hard drive. 
Hardy Heron features the latest [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/"). Mine has been able to set itself up automatically for all the different computers and monitors around my house that I have been able to boot a USB with so far. This renders the 'Persistent' type liveCD USB installs obsolete. 

All we need to do now is just a regular installation, and select 'guided partitioning' and choose the USB as the disk to install in. 
Remember to install GRUB to MBR in the USB device rather than let it go to your first hard disk. 
In the 'Desktop' Live/Install CD you do that in step 7 of 7 by pressing the 'advanced' button and selecting which hard disk (MBR) for GRUB to be installed in, and select your USB's MBR. 
If you are using the 'Alternate CD' to install with, you click '[No]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location")' when it asks you if it can install GRUB to MBR in the first hard disk, and specify your USB's MBR.

Normally, you won't have a lot of room for files in a USB jump drive, but those are available in large enough sizes these days for at least a few files. You probably need at least a 4.0 GB memory stick, but bigger is better. I don't think 2.0 GB would be big enough really.

1st EDIT: This how-to might be helpful to try to keep the operating system's disk space usage down to a minimum and let you have the maximum space in your USB for files, [HOWTO: Cleaning up all those unnecessary junk files...]("http://ubuntuforums.org/showthread.php?&t=140920") - By WhackToMack, also see,[ [ubuntu] /boot partition is full]("http://ubuntuforums.org/showthread.php?t=1435818") .

2nd EDIT: I recommend using the Reiser File System for flash memory installations, for better disc write performance, for more details jump to post [#69]("http://ubuntuforums.org/showpost.php?p=5882924&postcount=69")

3rd EDIT: I like this:                          [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile")  - by iva2k

4th EDIT: Ubuntu Intrepid Ibex and later feature the uuid command in the latest GRUB.
With UUID booting, you can boot a USB no matter what number the BIOS wants to give the USB drive.
No matter how many other USB drives and other kinds of hard drive you might have plugged in to a computer at the same time, with GRUB's new uuid command, GRUB will always be able to find the right root and boot partition and boot your USB for you. 

5th EDIT: Ubuntu Jaunty Jackalope and Karmic Koala and later all feature the ext4 file system by default. 
I now think ext4 file system is the best file system to use in flash memory sticks and Solid State Drives.

6th EDIT: Karmic Koala and later versions of Ubuntu feature GRUB 1.97 as the default boot loader, most people call it 'GRUB2'.
This new version of GRUB has improved abilities for USB booting and we're now able to boot Ubuntu in a USB using computers that were impossible to boot a USB device from before. 

7th EDIT: With GRUB2 it's easy to use this kind of USB install to rescue an unbootable system in a computer's internal hard disk, just boot the USB Ubuntu and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' and it will (most times at least) detect the internal operating system(s) and add them to the USB's boot menu. Then you only need to reboot and select the internal operating system that has the boot loader problem and boot it. Magic!
The reverse is also true, with Ubuntu running as the main operating system in the computer, you can plug in the USB with your auxilliary Ubuntu in it and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg for a boot option in the computer for booting the memory stick. It's much more convenient than using the BIOS to boot every time.

8th EDIT: Now that Lucid Lynx is here, times have never been better for USB flash memory installations, we can now use Ubuntu One for extra file storage and syncing with our main computers when we're on the move. I am still learning about Ubuntu One, but so far I think it's great!

If you have Ubuntu in your home computer, you can set up [SSH Networking]("http://members.iinet.net.au/%7Eherman546/p11.html") with port forwarding and use that over the internet to access all the files in your home computer from anywhere in the world, so you can then actually do much more with Ubuntu in a flash memory stick that you can carry around in your pocket than most people can with a whole computer.

See my first sig link for illustrated examples of how to install Ubuntu.

Regards, Herman :)

---

### Post by Herman on 2008-05-10
If your Hardy Heron USB install boots to a tan screen with a mouse pointer in it and nothing else, that's because there is a bug in Hardy Heron that seems to affect Gnome especially in USB devices. 
Refer to these two links, [https://bugs.launchpad.net/ubuntu/+s...dm/+bug/221850]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850") and [https://bugs.launchpad.net/ubuntu/+s...ng/+bug/218434]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434")

 To summarize, it is necessary to use the 'ctrl'+'alt'+'del' keyboard combination and log into a virtual terminal and type 'sudo rm /tmp/X0-lock', and then 'startx', and you should then have your Gnome Desktop.
Then open 'System'-->'Administration'-->'login window', open the security tab, and enable automatic login for the administrative user (yourself).
NOTE: It takes ages for the login window to open, like about five or six minutes and it looks like nothing is happening. Just be patient.

 The first time you try to shut down you'll be back to the tan screen again, (for the last time). 
Press'ctrl'+'alt'+'del' keyboard combination and log into a virtual terminal and type 'sudo shutdown -h -t 0 now', to shut the computer down.
From then on you shouldn't have any more problems, your USB disk will start up and shut down as normal.

EDIT: Since the work-around just described above results in an operating system without any user login at boot time, it would probably be a good idea to set a GRUB [password]("http://members.iinet.net.au/%7Eherman546/p15.html#password") for at least some security against unauthorized use of the USB operating system. Link: [URL="http://members.iinet.net.au/%7Eherman546/p15.html#password"]GRUB password

[/URL]  EDIT 2 : The above advice applies only to Hardy Heron 8.04, and not to 8.04.1 or later, the bug has been fixed.
 
One more good thing about making a normal installation in a USB as opposed to a Persistent LiveCD installation is, a regular install auto- mounts other USB drives, so we can plug in another USB flash memory stick with room for more files in it and use that for extra disk space. I'm running one of my USB flash memory installations right now and I just finished watching a movie which is stored in another USB flash memory plugged in right under the operating system's memory stick.

---

### Post by Redrazor39 on 2008-05-10
wow, thanks for all the assistance, but what exactly qualifies as a high quality super fast flash drive?

And would 8GB be necessary or would 4GB be fine? I thought the reqs. for Ubuntu are 4GB minimum.

---

### Post by Redrazor39 on 2008-05-10
also, how do you boot from the flash drive? do you plug it in and start the computer with the USB drive in or can you start from Windows/Mac OS X?

---

### Post by Herman on 2008-05-10
> how do you boot from the flash drive? do you plug it in and start the computer with the USB drive in or can you start from Windows/Mac OS X?:) Yes, you must have your flash memory stick already plugged in before you start the computer up so it will be detected during P.O.S.T. and registered in the BIOS.

There are at least three different ways that I use, and probably others can tell you more ways to boot a USB disk.

**1. If you don't have GRUB installed to MBR** in your computer, another way  to boot your USB flash memory device is by pressing a key as your  computer boots to bring up a menu from your BIOS this way, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).

**2. If you still have Legacy GRUB** - You can use [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli")  to boot your flash memory stick manually.
 To make it more automatic you can add a new entry to the bottom of your internal drive's Ubuntu /boot/grub/menu.lst file which will chainload the MBR or the boot sector in the USB flash memory stick.
For example, 
```
title   Hardy Heron USB Stick MBR Boot
root   (hd2)
chainloader +1
``` 

**3. If you're using GRUB2** - Just boot into your regular Ubuntu installation inside your computer and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg', and it will automatically add an entry for the USB Ubuntu auxilliary operating system. Then boot your auxlilliary Ubuntu USB and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' for an emergency boot entry in your USB for your main (internal) Ubuntu installation.

---

### Post by Redrazor39 on 2008-05-10
I was hoping there was a way to carry your entire computing system in a small USB drive without making changes to any host computers.

Is there a way to do that?

I was thinking of booting school computers, office computers, other home computers, etc. into Ubuntu when I got bored or needed a different tool or file.

---

### Post by esteckis on 2008-05-10
Here are 2 questions I have about using Hardy Heron on a latop.

1) Will I get a longer battery life using the USB device instead of the hard drive?
2) Will Ubuntu automatically put the hard drive to sleep since in essence the flash drive will have the swap file?  Since most of my files are on-line for access and I listen to the streaming radio, I really do not need to use the hard drive.  I also have 3 flash drives 8 gig 4 gig 2 gig.

Thanks for you help :)

Ooops, I forgot

In future reference of buying a flash drive, if it can handle windows ready boost, does that mean it will have better random read and write speeds?

---

### Post by Redrazor39 on 2008-05-10
those are good questions. I want to know that too. Don't forget to answer my questions in the post above that though!

---

### Post by esteckis on 2008-05-10
I am not that experienced with flash drives, one site that gives a lot of buyer reviews is newegg.com.  If I am correct, MMC cards and Flash do a sequential read/write and as you fill up the card when you need to change a file, it takes longer.  I am not familiar with what brands are good and the manufacturers have so many different models now.  That's why I was wondering, if a flash drive is windows ready boost compatible, does it at least give an idea that it runs pretty fast.

---

### Post by Herman on 2008-05-10
> but what exactly qualifies as a high quality super fast flash drive?
 I don't know, but it does seem to me as if there does could be a difference in quality between flash memory sticks, but maybe it's only my imagination, I haven't done any controlled tests on that subject yet. Others seem to be of the same opinion though.

EDITED ON 6th Jan 2010: I have since been doing some testing and a lot of reading and some flash memory and Solid State Drive manufacturers spend a lot of money having scientists and engineers researching ways to make flash memory faster, longer lasting and more reliable as well as affordable to the consumer. Flash memory is not all created equal, and prices are no indication of quality either, you need to be prepared to do your own up to date research if you want to be a smart flash memory shopper.

> And would 8GB be necessary or would 4GB be fine? I thought the reqs. for Ubuntu are 4GB minimum. I always thought that Ubuntu takes up a minimum of about 1..8 GB of hard disk space, but we should allow an extra 25% on top of that for the file system to have a little 'breathing space'. Linux file systems never need defragmenting, but they do perform best with a little extra unused space in the partition.

Right now I have Hardy installed in a Toshiba flash memory stick and a Kingstom Data Traveller, both are 4.0 GB in size, 0r 3.84 GiB according to Gnome Partition Editor.
In both of mine I have an extra Desktop installed, I did that because I didn't know how to get Gnome working at the time I first installed these two sticks. One has the Ubuntu (Gnome) Desktop plus XFCE (Xubuntu), and the other one has Ubuntu (Gnome) Desktop plus IceWM.  I believe that adding an extra desktop takes up quite a bit of disk space.
I will need to uninstall the extra desktops or install again fresh to see how big Hardy Heron is as a default install, but I can tell you that at the moment both of my USB installs have about 2.38 GiB used and 1.24 GiB unused out of a 3.62 GiB / (root) partition. There's a swap area of 219.61 MiB after that.

I would recommend people use a 4.0 GB stick or larger if a larger one is available. In my town 4.0 GB is the largest they stock in the local electrical store, or I would have a bigger one too.

UPDATE: The bare-bones Ubuntu Hardy Heron install occupies 1.98 GiB of space in the flash memory stick. You will need more space for adding software and some files, depending on what you're planning on using the stick for.

---

### Post by Herman on 2008-05-10
> 1) Will I get a longer battery life using the USB device instead of the hard drive?I don't know but I would imagine there would be a power savings there. We could test how fast the battery loses power running the hard drive and then running from the flash memory and finally running from the flash memory with the hard drive removed.
I have a couple of laptop size hard drives in external USB enclosures and those drwa all their power through the USB connection. Some computers haven't got the power in the USB port to spin them up, but will boot a normal sized hard disk an an external USB enclosure that has it's own separate power supply. (Plugged inot a wall socket).
That suggests that it probably does take some power to spin up a hard disk drive, I imagine a flash memory device would be quite a lot more energy efficient. :)
Anyway, I don't think there's any danger of a linux file system filling up your disk sequentially.
> 2) Will Ubuntu automatically put the hard drive to sleep since in essence the flash drive will have the swap file? Since most of my files are on-line for access and I listen to the streaming radio, I really do not need to use the hard drive. I also have 3 flash drives 8 gig 4 gig 2 gig.I imagine they will just remain asleep unless they are required.
> In future reference of buying a flash drive, if it can handle windows ready boost, does that mean it will have better random read and write speeds?I don't know really, I don't know anything about 'Windows Ready Boost', more detailed information about that would be needed before I'd be able to make any guesses about that.
I do think that certain software companies only exist for the sole purpose of taking people's money away, and they will try to get people to believe a lot of crazy things of it means they can get more it it, (your money). With that in mind I'd be very skeptial about whether 'Windows Ready Boost' really means anything or not. It could even mean they're worse, so extra sales effort is needed to induce people to take them of the vendors hands. :lolflag:
Testing would be needed to find out for sure.
> If I am correct, MMC cards and Flash do a sequential read/write and as you fill up the card when you need to change a file, it takes longer. Linux file systems work in a completely different way. That's why Linux file systems never need defragmenting.
Check out these two links, 
[CENTER][OneAndOneIs2 - Why doesn't Linux need defragmenting?]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")
                        
                        [ITworld.com - Fragmentation and Unix file systems]("http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html")

[LEFT]My analogy for imagining what linux file systems are like is to imagine a grape vine.
The grape vine's stem is the first superblock and metadata blocks which direct the operating system to the inodes. The inodes are like forks in the grapevine. There are bunches of grapes hanging everywhere along the vine and some bunches have most of the grapes full, (like sectors containing data), and others have some dried up sacks that may fill out if the vine is watered more. Those are like the empty sectors.
I'm not sure if that;s a fair analogy for how an ext2 or ext3 file system works, that's just how I imagine it since I haven't been educated on it enough to know any better. :)
I think NTFS is an attempt by Windows to try to emulate a Linux file system though, that's why NTFS doesn't need defragging as often as FAT32 used to.
Most USB flash memories come with FAT16.
FAT16 and FAT32 file systems do work more or less by filling the disk up sequentially, I think.
[/LEFT]
 
[/CENTER]

---

### Post by esteckis on 2008-05-10
Wiki article [http://en.wikipedia.org/wiki/ReadyBoost](http://en.wikipedia.org/wiki/ReadyBoost) So there is a difference when looking for random speeds on Flash. Because if you are going to use your swap file  on a flash, you want good random access speeds. I remember MS touted the ready boost aspect, but no ones old flash drives would work with it.  That is why the manufacturers certify that it is ready boost capable.

And there is a great difference on speeds of flash drive. My 4 gig transcend flash can read/ at 20 mbs second. Now that is obsolete.

---

### Post by Herman on 2008-05-10
Thanks for that link, that's interesting. It looks to me as if Windows has come up with a scheme for using any free space on the user's USB flash memory stick for an extra page file, (what we call a swap area in Linux).
That looks like a good idea to me now that I have had a quick read of that, and it seems to make sense and might even be a good idea. :)

I think you're probably right, probably if a USB flash memory is 'windows ready boost' compatible, it would be an indication that it at least meets those performance standards.
Then on the other hand, you would need to read the fine print or google the brand and model of flash memory you're comparing it with in case the other brand is better but just hasn't heard of 'windows ready boost'.
Another thing to consider is whether or not a faster flash memory will have more life expectancy than normal or if it will 'wear out' quicker, (or whatever flash memory does).
Or will better quality mean speed and longevity goes hand in hand, maybe due to the use of more refined materials or a superior manufacturing process?

---

### Post by esteckis on 2008-05-11
The actual reason for the ready boost under windows is because (from what I hear) is that the loading time when first starting your computer was horrendous under the Vista. Now, having ready boost your read time on your flash is a lot quicker because you do not have to wait for your hard drive to start spinning up.

Just another note: on the Pedrive Linux link I listed above, they do state that your life span of the flash will be degraded from all the reading and writing going on.  On the Pedrive Linux site, they had under the  Gutsy on USB, how to have changes stored in Ram and then when you shut down, then it is saved to the flash which helps cut down on all the random reading and writing to the flash drive.  They have not posted a way to do it with Hardy Heron yet.

---

### Post by redblue123 on 2008-05-11
To actually installing Hardy to a USB using the normal install you would need at least a 2gb flash drive.

You can install Hardy in persistent mode on a 1gb drive using the methods shown on these pages:
[http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/)
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

I've been using the Hardy on a USB using Ryan's instructions for about 2 weeks now.

As esteckis says, persistent cuts down on the read/write of a regular install, so it may be better (in addition to saving space)
@esteckis: pendrivelinux posted their version a day or two ago.

---

### Post by HunterThomson on 2008-05-11
I love Ubuntu and all but 

download BackTrack3 for USB instead:guitar:

[http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)

---

### Post by SANDIZ on 2008-06-13
I'm not at my comupter right now but I'll try this when I get home. But how do I get a Terminal window. I remember doing a ctrl+alt+del last night and it doesn't seem to respond. I had to press the on/off button.

---

### Post by Herman on 2008-06-13
> But how do I get a Terminal window. I remember doing a ctrl+alt+del last night and it doesn't seem to respond. I had to press the on/off button.Under normal circumstances we just go 'Applications'-->'Accessories'-->'Terminal'.
Another way to get a command prompt is to press 'Ctrl'+Alt'+'F1' or any 'F' key between 1 and 6.

I was just about to tell you that ctrl+alt+del doesn't do anything in Linux, (it didn't the last time I checked), but tried it just now in Hardy Heron to make sure, and when I do it twice the shutdown/reboot screen appears. That must be another new feature. I suppose if the mouse is frozen, but the keyboard still works we can shut down or reboot that way now. :)

Anyway, here's a link about the more traditional ways to shut down Linux, **[Avoiding filesystem damage]("http://members.iinet.net.au/%7Eherman546/p10.html#Avoiding_filesystem_damage")      **(Proper Emergency Shutdown Procedures for Linux).

---

### Post by Pumalite on 2008-06-13
Hi Herman:
I was practicing with your instructions. They are great. Only thing is I think the command is 'sudo rm /etc/.X0-lock'(At least in my system)

---

### Post by Xyem on 2008-06-13
I have 8.04 installed onto my Kingston 1GB stick. No swap, just one big ext3 partition..

It's a minimal install with Matchbox for the window manager. It behaves quite well, even though the drive reads at 9mb/s!

Edit: I actually installed it through QEMU :)

---

### Post by Herman on 2008-06-13
:) Hi Puma,
> I was practicing with your instructions. They are great. Only thing is I think the command is 'sudo rm /etc/.X0-lock'(At least in my system)Thanks for your input, Pumalite, are you running Hardy Heron? 

In my system the only file named .X0-lock is definitely in the /tmp directory, that can be verified with the 'find' command: 
```
herman@amd64hh:~$ sudo find / -name .X0-lock
[sudo] password for herman: 
find: /home/herman/.gvfs: Permission denied
/tmp/.X0-lock
herman@amd64hh:~$ 

```There seems to be something different about your system.
If there's something different about yours then possibly there will be others that are different too, so your post might help someone. I wonder why your is different though?  :)

Regards, Herman :)

---

### Post by Pumalite on 2008-06-13
Well; it's Hardy amd64 on a Core 2 Duo. Hope it helps.

---

### Post by vpadro on 2008-06-26
Maybe someone could answer this:

I wonder if I can use a 2gb pen drive to install ubuntu 8.04 server in order to use it as a local DNS for my test lab(serving about 11 servers based on Xen), the machine will use Intel D201GLY MoBo which it's mini-itx and a 1Gb DDR2 533Mhx Stick only, no need for graphics or even X.

Could it be possible?

---

### Post by dewbob on 2008-06-27
> **Herman said:**
> Just install Hardy Heron in your USB flash memory stick in the regular way the same as any other hard drive... 

All we need to do now is just a regular installation, and select 'guided partitioning' and choose the USB as the disk to install in.... 


Herman, 

Thanks for the info.  I have tried a few times to install Ubuntu on my 8GB flash drive in this fashion, but I can't get the install to finish.

I get through all the set-up screens, and click install.  Ubuntu gets to 'Partition Formatting' (about 5% in) and then stops.  I receive the following error:

[INDENT]The attempt to mount a file system with the sawp in SCSI3 (0,0,0), partition #5 (sdb) at none failed.

You may now resume from partitioning menu.[/INDENT]

I am then given the option to 'go back' or 'continue' both buttons return me to the partitioning menu.

Any suggestions on what to try to get around this? 
 
Thanks for the help.

DewBob

---

### Post by Herman on 2008-06-27
Maybe try running your Ubuntu Hardy Heron Desktop Live CD and partitioning your USB flash memory with Gnome Partition Editor beforehand yourself. 
Then boot the installer and just select the mount points for the file systems with the partitions already made.

---

### Post by esteckis on 2008-06-28
I just happen to be doing a search and came across this site. The program worked on my USB.  The only thing I am noticing that when you install to a USB using Pendrivelinux method or this guys program, you cannot update Ubuntu and settings are not persistent because it is logged in as a live session and there is no option to maintain persistence.

[http://klik.atekon.de/liveusb/#issues]("http://klik.atekon.de/liveusb/#issues")

---

### Post by Dr.Ninethousand on 2008-06-29
in my opinion Wolvix is an excellent OS for pendrives..

---

### Post by Tyan on 2008-06-29
Is it possible to do this with a 8 or 16 Gig SD chip?  And can a SD chip even boot?

Cause that would be neat.

---

### Post by Dr.Ninethousand on 2008-06-29
as examples, I have Wolvix installed on a 4GB pendrive, with about 2GB left for /home


and I even have a special version of Puppy Linux called Mean Puppy installed on a 64MB pendrive..

so as far as size; yes it's quite possible..  although many older computers still in use today are not able to boot from USB devices, that problem is becoming more rare..  you may have to go into BIOS and tell it to boot from your device, though..

I'm not sure about an SD chip being bootable, but don't they make tiny SD-to-USB converters?.

---

### Post by Redrazor39 on 2008-07-01
> **esteckis said:**
> I just happen to be doing a search and came across this site. The program worked on my USB.  The only thing I am noticing that when you install to a USB using Pendrivelinux method or this guys program, you cannot update Ubuntu and settings are not persistent because it is logged in as a live session and there is no option to maintain persistence.

[http://klik.atekon.de/liveusb/#issues]("http://klik.atekon.de/liveusb/#issues")

So with this method can you create a user and save all your settings, downloads, etc. all to the USB stick?

---

### Post by starcannon on 2008-07-01
This package does it for you, and presumably will be includedin 8.10
Google netted a lot of results on how to make it persistent as well.
[http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)

I made one months ago just to see if I could, but what I'd really like is the ability to not have to burn cd's in order to make live usb's, I'd send a lot less CD's to the trash if I didn't have to burn images that are outdated every 12 months. I'm sure were not far away from that, or at least I hope were not.

---

### Post by Dr.Ninethousand on 2008-07-01
hmm, you could probably mount the .iso on a virtual machine and install that way I would guess, if you have a version of a virtual machine that supports USB..

---

### Post by esteckis on 2008-07-07
> **Redrazor39 said:**
> So with this method can you create a user and save all your settings, downloads, etc. all to the USB stick?

I tried the Pendrive linux site with Ubuntu and Xubuntu.  Being a Linux newbie, the site did not state that when you get to the boot screen to press F6 for persistence. It does save your info on the USB if you press F6. I am seeing though that you cannot update Ubuntu because if I use the update manger the USB becomes corrupted.  But I was able to download the proprietary Broadcom wireless driver (restricted driver) and maintain installation of the driver on the next boot.

I wanted to try Xubuntu (for the less processor and ram requirememnts) Xubuntu does boot on the flash, but I have no menu panels showing. I do not know how to fix that.

Also on both of the above, you do not have the option to use your propietary video drives.

I have also tried Puppy Linux and Damn Small Linux. With my laptop (DEll 6400), I need that restricted Broadcom driver (fwcutter) and cannot get it with those two distributions.  The Ndswrapper does not work for me at all.

---

### Post by nuddernuby on 2008-07-26
Herman,jou doring! 
I use a 8Gb flash drive that was used to run Mandriva perfectly before my attempt to load Ubuntu 8.04 alternative. 
I have the same problem as DewBob but only later on in the install process.  Did you solve yours, DewBob?
When the install process reaches the step called 
> Select and install software
- this is just before the step called
> Build LTSP chroot-
it bombs out at about 85% complete, with exactly the same message as described in DewBob's post above.
I've taken several repeated attempts at this, with the same results every time - it fails at this particular point after most of the software has been installed.
Would anybody have any advice, please?

---

### Post by Pumalite on 2008-07-26
Burn a new CD. Do md5sum on the iso, burn at 4x or less. Do not use CD-RW. I've installed Hardy and Intrepid Ivex Alpha3 to 8 GB stick following Herman's recipe.

---

### Post by Herman on 2008-07-26
:) Hello nuddernuby,
Welcome! 
I agree with Pumalite, when something like that has happened to me, it seems to have been caused by either a damaged, dirty or corrupted CD-ROM, or a dirty optical lense in the CD/DVD drive.
There may be other reasons for that kind of behaviour too, but those things have been the cause of that type of problem for me a few times.

Sometimes, just wiping the CD with a soft cloth ot a tissue tipped in metholated spirits (denatured alcohol), or cleaning the optical lense with a Qtip (cotton bud), might solve this problem. 
A few CD/DVD drives are easy to clean, the lens slides out when we open the CD drawer, but in most CD/DVD drives it's a lot of work to dismantle them for proper cleaning, but I think it's better to try than to just give up and buy a new CD/DVD drive.

I cannot promise this will work for everyone with a similar problem, there is no guarantee your problem is the same as mine was. Only people with mechanical skills and the right tools should attempt to take thier CD/DVD drives apart for cleaning.

Here is a link to one of my web pages where I have illustrated what happened to me once, [Hardy Heron Beta / Gutsy Gibbon Graphical Installation C]("http://www.herman.linuxmaniac.net/p22.html"). (Scroll down to about 25% from the bottom of the page and you'll see what I did. :)

I repeat once again thought, this problem could be cause by something else, so maybe I'm wrong. I only know that cleaning things has helped me to overcome this type of problem a few times when it happened to me.

Regards, Herman

---

### Post by Browser_ice on 2008-07-29
I am thinking about creating/using a persistant Ubuntu on a pendrive. I am wondering about one thing : when booting with an Ubuntu on a usb key, will the PC's own HD be accessible through it ?

At the office, there is this work PC where I often use some files with other users and those files are residing on that PC alone. They all use Win-XP. So by me using Ubuntu on a USB Key, I would want to be able to update those files without having to reboot into XP.

Can I access/update files on the PC HD through my USB key Ubuntu ?

---

### Post by unutbu on 2008-07-29
In general[1], yes, you can access/update files on the PC's HD when you boot Ubuntu from a USB key.

When you boot Ubuntu, the internal PC HD will be considered the second drive and will be given a device name like /dev/sdb. You can find out for sure what the name is by opening a terminal and typing
```

sudo fdisk -l
```

If you want to access the first partition on the PC HD (/dev/sdb1), you would then type
```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

If the Windows partition has an NTFS filesystem, then be sure to install the ntfs-config and ntfs-3g packages.

[1] I've read some reports of users having problems with certain make/models of hard drives, but the problem seems to be pretty rare.

---

### Post by nuddernuby on 2008-08-02
Thanks to Pumalite and Herman.
Interestingly, I eventually tried to do the installation from a live disc instead of the alternative. It went off without a hitch and is running perfectly. Don't know what the problem was with the alternative version.
I appreciate your input.
nn

---

### Post by bondo101 on 2008-08-04
Thankyou very precise info was using a 2 gig thumb drive almost worked but forgot ya need more room for ubuntu. gonna try again i never give up having more fun with linux and learning more and more. who says ya kan't teach an old dog new tricks,   bondo101

---

### Post by shrinathk87 on 2008-08-04
Hey everyone...just wanted to let u know something..i heard installing an OS on a pendrive decreses its lifetime..because, a normal pendrive has some one million write cycles...(not sure on the number) but it does have LIMITED write cycles..so if u install an OS, frequent read-writes (eg swap etc. ) occur and the lifetime decreases...

and with reference to some guy name redrazor23,in the starting of the post, he asked if it was possible to use the OS on the pen drive without affecting the computers it has been plugged into...
well YES..booting off a USB stick does not AUTOMATICALLY alter any information on the HDD..but i guess you can MANUALLY read/write data on the HDD..

Thnx..

---

### Post by Herman on 2008-08-04
:) Hello shrinathk87,
Thank you very much for your thoughtful warning.
I agree with you that for everyday use it's better to install Ubuntu in a hard disk drive inside a computer.

There are some special occasions though, such as when we need to go traveling and we want to travel without a lot of heavy baggage, when it is useful to be able to have an operating system in something like a flash memory stick which is small enough to carry in one's pocket.
Laptops can be easily stolen especially when people have to stop at places where they will be surrounded by strangers. In that case one would not care if the hard drive might last longer.

Laptops (or a USB external hard drive) can be accidentally dropped and broken, compared with a USB flash memory which can take quite a bit of physical punishment and remain unaffected. I have read that military equipment uses flash memory in preference to hard disk drives in many instances due to it's superior ability to withstand shocks. 

Also, when we need something we can install many programs in for helping freinds fix their computers, Ubuntu installed in a flash memory is much better than a LiveCD. We can install the programs we want in the USB flash stick and they will always be there ready to use again. When we use a LiveCD, we need to install some programs every time we boot the CD if the program is not already included in the CD.

Flash memory technology is advancing, and getting more reliable and at the same time, getting more affordable.
Good quality modern flash memory is quite a lot different now than the flash memory we used to buy just one or two years ago. If we bother to take the time to do a little reading and research before we spend our money on a new flash memory stick we can probably buy one which will last as long or longer than a hard disk drive, without spending very much more money.

There are new computers which use flash memory instead of a hard disk drive, 
**[ASUS | *Eee PC*]("http://eeepc.asus.com/")**


I have spent quite some time googling on this subject and I still can't find any convincing looking tests which indicate that flash memory is really that bad. I have found a test which seems to indicate it will probably last as long as a hard disk drive. I don't have the link for that right now but I will find it and add it to this post later.

EDIT: I think these were the links I was thinking of, [Squeak! - How Solid is Hard Disk's Future?]("http://www.storagesearch.com/hardwayaheadforhds.html"), and [SSD Myths and Legends - "write endurance"]("http://www.storagesearch.com/ssdmyths-endurance.html")

EDIT: And this one too, [B][War of the Disks: Hard Disk Drives vs. Flash Solid State Disks]("http://www.storagesearch.com/bitmicro-art3.html")

[/B]Quoted from the above link:> **Reliability**  

 In terms of reliability, conventional HDDs pale when compared to SSDs. The absence of mechanical arms and spinning platters is the reason behind its [reliability]("http://www.storagesearch.com/reliability.html"). In demanding environments, SSDs provide the type of ruggedness required for mobile applications. Unlike the HDD, SSD's can withstand extreme shock and vibration with data integrity and without any danger of data loss. This feature is very important in industrial applications where exposure to highly combustible materials and electromagnetic radiation are typical. Their ability to deliver unnerving performance in extreme conditions also makes SSD play a vital role in military operations, be it in defense, aerospace or aviation applications. Military applications require, in most cases, an operating temperature range of -60°C to +95°C. Shock, vibration, and temperature ratings of HDDs cannot comply with military standards, only SSDs can.   Regards, Herman :)

---

### Post by drfox on 2008-08-04
> **redblue123 said:**
> 

I've been using the Hardy on a USB using Ryan's instructions for about 2 weeks now.

I installed Hardy using Ryan's instructions and Ubuntu automatically logs in as "Live Session User." Is it possible to go directly to a log in screen with the security of a user and password?

Larry

---

### Post by webplus on 2008-08-06
A couple of USB flash memory drives I would recommend for full installations are the OCZ Rally 2 (they have a lifetime warranty and use dual channel memory so they are very fast) and the Corsair Flash Voyager comes with a 10 year warranty.

The normal write cycle with flash memory is around 100,000 writes, but the better quality memory uses advanced technology to prolong the life even further.  The Corsair website has some useful details about this for anyone interested (corsair.com).

---

### Post by esteckis on 2008-08-10
Yes it does decrease life cycle of the USB, but from what I understand on the pendrive linux site, installing it with the casper, decreases the read/write cycles by using the casper method. I believe it holds more things in memory and then writes a final update when you shut the system down.

---

### Post by zaarch on 2008-08-12
a little help..guys.i have installed hardy on a 2GB usb flash drive..
and its booting up as well..

my issue is..that it boots into a built in shell (ash)..i dont know how to proceed from..there

should the drive not boot into a GUI...??

i thought maybe i made a mistake in the making the bootable usb hardy drive..but i have repeated the procedure over 3 times...result always the same..

boots into ash ...and its has a basic of 20 commands...reboot..cd..grep...that sort of stuff not very useful if ur trying for a portable os...

---

### Post by Herman on 2008-08-12
At least one cause of that kind of behavior is booting a kernel but not finding the matching initrd.img. That could be from having the wrong hard disk or partition number for GRUB in your booting stanza in your /boot/grub/menu.lst file.

It might be a good idea to try using [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to boot up with and doing a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."). 

Or if you don't like the command line, try                                                booting with Super Grub Disk and use that for a direct kernel boot.

Take a look in this link and see if it's any help, [busybox or tty error]("http://users.bigpond.net.au/hermanzone/p15.htm#busybox").

Probably you should take a look in your /boot/grub/menu.lst file in the USB disk and edit it with the correct information.

Regards, Herman :)

---

### Post by moycano on 2008-08-23
Finally I found the topic that was looking for. Sorry to say, but the documentation and the Community Docs have the baddest finder ever!

My situation is as follow:
-Successfully installed Xubuntu Hardy Heron in a 2GB pendrive.
-The drive contains only one big ext3 partition / and the little extended /swap

But I want to remove the swap (in order to preserve the life cycle of the flashdrive) and place a FAT32 partition instead, that can be accessed from a Windows system to access some small files anywhere. So, ¿what steps do I need to follow?

My guess would be: 1) Swapoff from GParted and 2) format to FAT32 ...but since the setup is considerable slow, I would like to ask before try the second one.

*SALUDOS*/REGARDS!

---

### Post by Herman on 2008-08-23
You guessed right. 
Just boot your Ubuntu Live CD and open Gnome Partition Editor (GParted), or use a GParted Live CD and delete the swap area or reformat it to FAT32. It should only take a few minutes in a normal computer.

You will also maybe need to edit /etc/fstab in Ubuntu in the flash memory stick and comment out the line for the swap area. I'm not sure, but it might save you from getting some error messages.
If you have a computer with enough RAM you might not really need any swap area, but most of us still have at least a small swap area somewhere. If your computer is noticably slower after you delete the swap, maybe you can make the swap area at the end of your hard disk instead, and set that up in /etc/fstab.

---

### Post by moycano on 2008-08-23
Wow, that's speed!

I will try it right now and, by the way, what I want to say is the installation were slow not the repartition process. Sorry if I put it wrong ...writing English isn't my best.

---

### Post by Herman on 2008-08-23
I have one brand of USB flash memory stick that seems very slow to read and write to, I don't know why. Installing Ubuntu took an hour and a half instead of only thirty minutes or so. It's a good brand too.

---

### Post by moycano on 2008-08-26
Herman, you know if is possible to install via loupmounted filesystem (wubi/lubi) to preserve the FAT32 partition and allow almost any system to read the content? I think shouldn't be much problem but this may need additional steps -¿grub?- to made the flash drive booteable in others PCs.

I say it because Windows only can see one partition per external media and often try to reformat (for example, if you made a full install and put a FAT or NTFS partition in the free space).

And I know that there is the fs-driver or selfmade drivers workarounds that really work, but lets just say for now aren't an option to me (rules and restrictions over the PCs that I have access to).

SALUDOS/REGARDS :-k

---

### Post by Herman on 2008-08-27
I don't know but maybe if you try asking in the Wubi section of Ubuntu Web Forums someone there might know.

 Regards, Herman  :)

---

### Post by moycano on 2008-08-27
> **Herman said:**
> I don't know but maybe if you try asking in the Wubi section of Ubuntu Web Forums...Doh, #-o, my mistake... I'll go and ask there 8-[

---

### Post by sofamensch on 2008-08-29
Hurray. This Thread is perfect for my needs :-)

**My history** 
Ok i already messed around with some live installation on my 1gb usb stick, but today i came across an 4gb for 9euro... i thought thatsa a joke so i bought it. 
Some speed testing shows write: 12-14 Mbyte/s read 25-30Mbyte/s. Which is actually quite neat and can compare with an average hard drive!

I just installed it directly, automatic partitioning created a EXT3 and a Swap Space.

The first boot was a wakeup call.. everything was slow. Even scrolling a WebPage had some delay sometimes. For now, i blame EXT3 and suggest to use FAT, I will just try that.


Probably when using a Flash Disk it would make sense not to have a Swap Space on the disk. From my experience, my 2GB are really enough for the most uses. Can probably save you some write accesses and increase the lifetime.

**Pro / Cons of Persistent Mode**
The most manuals for an USB Live installation are based around this Live USB Stick with some persistent mode.
I know that the actual discussion is to install everything like on a normal hard disk.
BUT a persistent Image definetly causes less writing accesses to the flash disk, since it -only- reads when booting. This would increase the disk's lifetime. And should probably be faster when booting, since an image needs less space anyways?




> **Tyan said:**
> Is it possible to do this with a 8 or 16 Gig SD chip?  And can a SD chip even boot?

Cause that would be neat.


Actually i have seen some setups that make it possible. The usual way is some cheap adapter, that gives you an IDE connector.
This is the usual stuff if you have a SilentPC, since this SD Stuff is faaaaaaaast.
\\:D/

---

### Post by sofamensch on 2008-08-29
UPdate: Sad. It is not possible to use FAT16 or Fa32 for "/" root directory, since they are not supported.

Oh and i should probably add that i use Intrepid Alpha 4.. if u guys have no problem with EXT3 i should try another release.

---

### Post by moycano on 2008-08-31
Since I successfully install in a USB but isn't practical to carry two drives just to ensure I can use them also in Windows, I'm just thinking about a small card reader as those have many physical disks that doesn't request any format relationship (like one in ext3 and other in fat32).

There's any difference in the process if I install in, let's say, a MicroSD instead a FlashDrive?

SALUDOS/REGARDS.

---

### Post by sofamensch on 2008-09-01
Well, i said i have seen PC's mounting from SD card, but connected to the IDE channel inside the PC. Here it is:
[http://www.geeky-gadgets.com/?p=31]("http://www.geeky-gadgets.com/?p=31")

I never heard of booting from SD as a portable Solution.

When you have a free SD Card, just try if it works.

---

### Post by Herman on 2008-09-04
**Shopping for a USB Flash Memory Stick**
Before you go and buy a new USB flash memory stick, you should take the time to do a little research about what kinds of flash memory is available in your price range.  
Probably a good first step would be to go downtown and see what USB memory sticks are for sale in stores near you and make notes of what brands and models are available.
When you get home, look for the websites of USB flash memory manufacturers. 
Most flash memory stick makers have a range of memory sticks available for different kinds of users. 
Flash memory is not all the same, you can get flash memory with different read speeds,  write speeds, and life expectancies. 
Some flash memory sticks cost more because of the added software in them for use with other operating systems. Most Ubuntu user probably are not interested in paying more money for extra software in a USB stick, we already have the best software for free. We're only going to delete the junk commercial software anyway, so we don't want to waste our money on that.
What we should be looking for is a ***data sheet*** or ***technical notes*** to see what claims the manufacturer makes about that product. (I mean, the flash memory itself, like - the stuff it's made of.)
A good quality flash memory stick might not necessarily cost any more money than trash quality flash memory that features a lot of fancy software which is designed to attract kids and childish adults.
Of course, if you just go and buy the cheapest flash memory stick you can see just because it is cheap, you are likely to end up with a cheap memory stick. You probably got just what you paid for.
I would expect that nowdays, even the cheapest kinds of flash memory sticks would feature some kind of '[wear levelling]("http://en.wikipedia.org/wiki/Wear_leveling")', which means that most conventional file systems can be used as-is on them.
Look for flash memory with good read and write speeds and look for flash memory which supports over a million read and write cycles. Some flash memory supports tens of millions of read and write cycles and equals or surpasses the life expectancy for a hard disk. Some kinds of flash memory is guaranteed for five years, they don't mention anything about how you use it or what you install in it.
The newest innovations in flash memory are very exciting and read and write speeds are possible in flash memory which are way faster than will ever be possible in hard disks, [IBM Flash Memory Breaks 1 Million IOPS Barrier]("http://hardware.slashdot.org/article.pl?sid=08/08/29/1646251").

**Swap Area in a USB memory stick?**
Many people think that having a swap area in a USB memory stick might not be a wise idea. That might be true depending on what kind of flash memory you have, but did you know there are some flash memory sticks available today (and for about the same price as other comparable flash memory), which is *recommended* to be used as page file for a certain other operating system? (A 'page file' is essentially the same thing as a 'swap area'). 
[http://www.sandisk.com/Retail/Default.aspx?CatID=1472](http://www.sandisk.com/Retail/Default.aspx?CatID=1472)
So if a memory stick manufacturer recommends using flash memory as memory for some other operating system then it seems reasonable to me to assume that it should be safe for Linux to use the same kind of flash memory as swap area. This may not apply to all types of flash memory though.  USB drives advertised with 'ReadyBoost Compatibility' certainly should be okay. [ReadyBoost Compatibilty List]("http://www.grantgibson.co.uk/misc/readyboost/") - Grant Gibson

**Regular installation or Pendrive?**
If you are in doubt about what kind of memory stick you have and what it can do, by all means, make a persistent type of installation from [Pendrive Linux.com]("http://www.pendrivelinux.com/"), those come with a special initrd.img which minimizes writes to the flash memory and so are about the safest and should maximize the life expectancy for any kind of flash memory.
You can use that kind of installation is very good, and can also be used for installiing Ubuntu is a hard disk.

If you just want to try out Ubuntu in a USB stick for a while to see if you like it, it's a lot quicker and easier to just install the regular way as if your USB stick was another hard drive.
If you're going to use it for demonstration purposes or the occasional file rescue, then installing in a USB stick the regular way is the best, because you can plug other USB sticks in beside the one you have booted and you'll be able to mount them and use the extra storage, which you can't do with the other kind of installation. You can also get updates without 'borking' the installation.
For occasional use a regular type of install should be fine.

If you're planning on using Ubuntu for everyday computing, it is best to install Ubuntu in a hard disk inside your computer, that's what Ubuntu is mainly designed for.
If you need to use Ubuntu in a USB on a regular (daily basis) for some reason, then try to calculate how long it will probably take to exceed the expected number of writes the manufacturer claims your USB flash memory is good for and make up your own mind whether you're happy with the result. Here is the only link I have been able to find so far which gives a mathematically based estimate for how long flash memory might last, but it's for a 64GB drive with 2 million writes, [SSD Myths and Legends - "write endurance"]("http://www.storagesearch.com/ssdmyths-endurance.html"). - "51 years".  Maybe I'm over simplifying, but based on that roughly, an 8 GB flash memory with only 1 million writes might last 2 or 3 years, but I'm only guessing.  If someone with mathematical ability can help here, please do join in. 

To sum up, judging from the information available to me, it seems logical to conclude that it's okay to install Ubuntu in a good qualiity USB flash memory stick in the regular way, the same as we would install to a hard drive, and we should be able to expect good performance and reasonable life for the flash memory.

---

### Post by sofamensch on 2008-09-06
Have you tried Intrepid on USB yet (with ext3, normal install)? I ask because it felt so slow and took ages to install/update/stuff?

Nice post Herman!

---

### Post by Herman on 2008-09-06
> Nice post Herman!     :) Thanks.
> Have you tried Intrepid on USB yet (with ext3, normal install)? I ask because it felt so slow and took ages to install/update/stuff? I have Intrepid in my big amd64 computer, but no, I haven't tried installing it in a USB flash memory stick yet. 
I do realize that writing to some flash memory sticks can be very slow. I found that out when I installed Hardy Heron in one of my flash memory sticks and it took about two hours instead of the expected half an hour for the installation to complete. That's because of the kind of flash memory I have, nothing to do with the Ubuntu installer.
I can't find the data sheet for that particular model of flash memory stick I used, so I guess the manufacturer doesn't consider the speed of that particular model of flash memory stick to be one of it's best features. 
I won't bother to name the manufacturer here, but they are a well known brand and have a lot of other great products. It's my own fault for choosing the wrong memory stick for the job I want to use it for. I was just in a hurry at the time.
UPDATE: I finally found a review which says my memory stick had a read speed of 29 MB/S but a write speed of only 9.4 MB/s. (No wonder).

The best flash memory stick I can buy from a store near me is an Amicroe 16GB USB flash memory and that will cost me about $149.00.  According to [mrgadget, Australia]("http://www.mrgadget.com.au/catalog/amicroe-16gb-usb-flash-drive-p-5571.html"), those are fast, Read Speed 25 MB/Sec Write Speed 20 MB/Sec and quite good quality, they have a one year warranty. [Amicroe 16GB USB]("http://www.amicroe.com.au/products/usb-flashdrives.html").

Take a look at the three 'Fastest Flash Drives' in this link, [USB Flash Dives]("http://www.everythingusb.com/hardware/Storage/USB_Flash_Drives.htm") -Everything USB. Now we're talking in the range of  34 MB/s read and 28 MB/s write speeds, Ready Boost, and ten year wrranty or even lifetime warranty.
There are larger models in those brands than what's shown there, I could get myself a [OCZ ATV 32GB USB 2.0 Flash Drive]("http://www.mwave.com.au/newAU/mwaveAU/productdetail.asp?CartID=mAU@VCGL6FFQSUO6HCZNP3NQZXMUDDV2BT7S9M4MTP2Q6V3ZW5&sku=37100585") or a [Corsair Voyager 32GB Flash USB2.0 Drive]("http://www.mwave.com.au/newAU/mwaveAU/productdetail.asp?CartID=mAU@VCGL6FFQSUO6HCZNP3NQZXMUDDV2BT7S9M4MTP2Q6V3ZW5&sku=37100384") from the internet for $160.20 or $169.95, but I'd have to buy those over the internet.
  :)

---

### Post by unutbu on 2008-09-06
Oh! If we're talking about a flash drive with a max sustained write speed of 20MB/s, 16GB size and 1M writes

then using Zsolt Kerekes' ([http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)) calculation for lifetime under the worse-case scenario,
the Amicroe would last

1M * 16GB / (20MB/s) = 0.8 * 10**9 s ~ 25.3 yrs

(assuming the Amicro has a write endurance rating of 1M cycles.)

---

### Post by Herman on 2008-09-07
Here's a really nice website for reading good objective reviews on USB flash memory, [USB Tests Benchmarks Reviews and News]("http://usbtests.com/") - By Peter Pauly. 
Very professional, an excellent website. The author seems to be a fellow Ubuntu user too. :)
Besides the pleasure being able to do some very interesting reading, I learned a number of new (to me) ideas from that site, one of them is that we can use a program in Ubuntu called bonnie++ for benchmarking the performance of our own USB flash memory sticks, or any other kind of disk, including hard disks too.
It is taking me some time to work out how to use bonnie++, and I'm still only a beginner at it. Maybe it's a little premature of me to post a how-to on it so soon, but here's a headstart on how to use bonnie++ anyway, for those who may be interested.

It's easiest to begin with a USB disk or any disc with plenty of free space, as bonnie++ needs room to write some files. Unfortunatly I'm not sure exactly how much free space is needed yet, I'm working on that and I'll update this post when I find out. I think we need at least 2 GB, but I'm not really sure yet, otherwise we can use a -s option in the command to write less data to the disc, but we need to write at least double the size of our RAM at a time it seems.
Using a computer that doesn't have very much RAM seems to help.
Also, making a 'dd' copy of the entire USB and then deleting the contents of the USB might be good. Restore the USB's contents with the 'dd' command again after the testing is over.

**Benchmark testing with [Bonnie++]("http://www.coker.com.au/bonnie++/").**
```
sudo apt-get install bonnie++
```Plug in your USB flash memory stick.
Check what directory it's mounted in.
```
ls /media
```For this example, we'll pretend the mount point for our USB device is just called 'disk'.
Make a directory in /media/disk for bonnie++ to work in,
```
sudo mkdir /media/disk/benchtest
``````
sudo chown herman.herman /media/disk/benchtest; sudo chmod 777 /media/disk/benchtest
```Now, we run bonnie++ in that directory,```
bonnie++ -d /media/disk/benchtest -m BlackBox
```NOTE: the -m option is for inserting the name of your USB drive or whatever drive you are testing.

Then you need to wait for a considerable length of time, like between ten minutes and half an hour or maybe longer while bonnie++ writes some data to the disc and erases it again and whatever else it needs to do to measure the disc's performance.
You should get an output something like this, 
```
Writing with putc()...done
Writing intelligently...done
Rewriting...done
Reading with getc()...done
Reading intelligently...done
start 'em...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
 BlackBox          4G 24453  46 **24710**   9 11907   3 **24980**  40 28446   3 127.2   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 28157  62 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
BlackBox,4G,24453,46,24710,9,11907,3,24980,40,28446,3,127.2,0,16,28157,62,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++
```The number '24710' indicates a write speed of 24.710 MB/s
The number '28446' indicates a read speed of 28.446 MB/s
Another important number is the number of random seeks, 127.2 per second in this example.
That's for an external USB drive by the way, not a SSD (Solid State Disc).

Now, if we want to automatically create an .html page with that output on it, but looking much more neat and tidy, we can use a script called bon_csv2html.
The bon_csv2html comes included in the bonnie++ package, and to use it we will be copying the comma separated bottom line of the output from the bonnie++ command and using the echo command to feed that into a script called bon_csv2html, which should now be located in /usr/bin/
We can pipe the output from bonnie++ through this script if we type 'echo' on the command line, and paste the bottom line from the output from the bonnie++ command, (the line with the list of numbers separated by commas) after it. 
Then we append the name of our script (bon_csv2html), and an 'append' symbol, (>>),  followed by the name of the .html file we want to make or append to, (bontest.html).
```
echo BlackBox,4G,24453,46,24710,9,11907,3,24980,40,28446,3,127.2,0,16,28157,62,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++  | bon_csv2html >> bontest.html
```That gives me a nice neat .html file named 'bontest.html' containing the information neatly in a table. I can open that with firefox. It looks like the examples shown in this link, [Testing your disks for PostgreSQL]("http://www.westnet.com/%7Egsmith/content/postgresql/pg-disktesting.htm") - Gregory Smith.

I'm collecting a whole series of tests in the same 'bontest.html' file and I am also editing it in kompozer to make it look even more presentable and easier to read.

I'm still learning how to use bonnie++ myself, but I hope that's enough info to help someone else to get started having fun benchmarking their discs and file systems with bonnie++. :)

---

### Post by C.S.Cameron on 2008-09-30
Interesting thread.
This is everything I know about installing to flash:
[http://ubuntuforums.org/showthread.php?t=922782](http://ubuntuforums.org/showthread.php?t=922782)

---

### Post by sofamensch on 2008-09-30
I think i already posted this, but 25MB/s writing Speed is absolutely OK!
But it doesnt explain why Ubuntu is running so slow. I guess its the Kernel, that does not access the USB Stick in the way it uses a hard disk. I guess USB devices are handled differently, in some ways, probably some Write-Cache.

No reason why the Setup takes so long, during 1 hour you could copy 90GB to the stick..

Probably the Persistent Mode does not encounter this problem, since the System is read sequently. I will check that this Weekend.:guitar:

---

### Post by Herman on 2008-09-30
:D Hello C.S.Cameron
Cool thread! (yours is ), Thank you! (insert virtual applause).
> Interesting thread.
This is everything I know about installing to flash:
[http://ubuntuforums.org/showthread.php?t=922782](http://ubuntuforums.org/showthread.php?t=922782)

---

### Post by Herman on 2008-09-30
> I think i already posted this, but 25MB/s writing Speed is absolutely OK!
But it doesnt explain why Ubuntu is running so slow. I guess its the Kernel, that does not access the USB Stick in the way it uses a hard disk. I guess USB devices are handled differently, in some ways, probably some Write-Cache.:D Hello sofamensch,
Hey, have you tried installing Ubuntu in your USB flash memory using the **ReiserFS**?

After I tested various different USB flash memories I have here with bonnie++ to learn how much difference there is in performance between manufacturers, I decided to compare a number of file systems.
The reiserfs turned out to be much faster than any other file system in some USB flash memory devices, and in others in wasn't so much faster, but it was at least the same speed as ext2 or ext3 or a little bit faster.

Quoting from: [Advanced filesystem implementor's guide, Part 1]("http://www.ibm.com/developerworks/library/l-fs.html")
> ReiserFS is around *eight to fifteen times*   faster than ext2 when handling files smaller than one k in size! Even better, these   performance improvements don't come at the expense of performance for other file   types. In general, ReiserFS outperforms ext2 in nearly every area, but really   shines when it comes to handling small files. > ReiserFS is able to pack the tails together, saving a lot   of space. In fact, a ReiserFS filesystem with tail packing enabled (the default)   can store six percent more data than the equivalent ext2 filesystem, which is   amazing in itself.However, tail packing does cause a slight performance hit since it forces   ReiserFS to repack data as files are modified. For this reason, ReiserFS tail   packing can be turned off, allowing the administrator to choose between good   speed and space efficiency, or opt for even more speed at the cost of some   storage capacity.
SO, I reinstalled Ubuntu in one of my best USB flash memory sticks, (the one I was complaining about being slow earlier, but which boasts of 'ReadyBoost capability), and I was very pleased with the results. 
It feels pretty much the same speed as a normal hard disk install to me when writing, and the reading is as expected for flash, much faster. 
I wonder what the results would have been like if I had installed in a faster USB?
I expect a great deal of variation between makes and models of flash memory and flash memory controllers.
Try **ReiserFS** and see if you can feel the difference too. 

EDITED 01/01/2009:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=6178d387-9ab5-4f23-a56d-8e0cba0addc3 / reiserfs notail,**nolog**,relatime,errors=remount-ro 0       1

# /dev/sda6
UUID=c6d20ccc-de8e-42ea-b568-aaf0cd049166 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` To make ReiserFS even faster, you can turn off the journaling. Adding the option 'nolog' to your /etc/fstab file turns off journaling. 

Regards, Herman :D

---

### Post by C.S.Cameron on 2008-10-02
Just tried setting up a new Kingston 4G using Manual partitioning.
Left 500M fat 32 partition,
1G home partition formatted ReiserFS,
and the rest ReiserFS, expt for 300M swap.
Seemed to work good at first, windows saw the fat.
Rebooted back into the flash, did the updates and the disk would not boot, made it part way at first, after a couple of trys, got no operating system.
I could see the partitions ok form the Live CD but could mount them.
Now even the gparted live cd can't see it, woops now it does.
any ideas?

---

### Post by flyingsliverfin on 2008-10-02
I also wanted to do that ever since my brother did it. So is it also possible to put xubuntu on a 512 mb flash drive? and how big is xubuntu

---

### Post by snowpine on 2008-10-02
> **flyingsliverfin said:**
> I also wanted to do that ever since my brother did it. So is it also possible to put xubuntu on a 512 mb flash drive? and how big is xubuntu

512mb is a little too small for Xubuntu. I think 2gb would be ideal. You can install SliTaz Linux on a 512mb stick though. :)

---

### Post by Herman on 2008-10-02
:D C.S.Cameron
> Now even the gparted live cd can't see it, woops now it does.
any ideas? :-k Hmm, the only reason I can think of for that kind of behaviour right away is the possibilty that the root  / file system might be a little bit corrupted already somehow. 
You should try right-clicking it in GParted and click 'unmount', (if it's mounted), and then click 'check'.
Click the 'Apply' icon and the 'Apply' button and GParted should be able to tidy up your file system(s) for you.
Try that and see if it helps, it shouldn't hurt anyway.

:D flyingsliverfin
> I also wanted to do that ever since my brother did it. So is it also possible to put xubuntu on a 512 mb flash drive? and how big is xubuntu  I don't think so, you'll need at least a 2.0 GB disk to install Xubuntu or Ubuntu in.
I'm not exactly sure how much hard disk space Xubuntu would occupy compared to Ubuntu, but I wouldn't imagine it would be all that much less. A clean install of Ubuntu will fill 1.8 GB, or at least it did last time I checked. You'll probably want at least a small swap area as well.
Actually, I would not really recommend installing in any less than 4.0 GB really.

You can probably get away with less if you do a [PendriveLinux]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.pendrivelinux.com%2F&ei=i4zlSKr9KYHwsAOm77jIDw&usg=AFQjCNGKCuMIIrCykN_asVfzxEA5JYKnKg&sig2=Bm2wrXRHIVfYOBQ2BLl_ww") type of installation, but even then, I think 2.0 GB at least, would be required.

---

### Post by C.S.Cameron on 2008-10-03
No luck, check failed on the root partition.
I'll try another install using ReiserFS.

Second try using ReiserFS,
Worked after install,
installed the 2 blacklist updates, rebooted, worked ok.
installed the security updates,  rebooted, worked ok.
installed the recommended updates,  rebooted, got message, pendrive without operating system, remove pen drive then reboot, then it went to grub, then blinking curser.
The grub option memtest worked, the option to boot to windows worked.
Booting to windows without pen drive got grub error 21.
Had to find windows install disk and go to repair console to do a fixmbr.
(this happened yesterday also, but I thought it was from playing with intrepid or usb-creator)
I'll give ext3 a try now to make sure the same thing doesn't happen.

Update
Tried several more times.
Found that best solution for not harming the windows mbr is to disable the hard drives when manually partitioning.
Install of 8.04.1 still would not work with reiserfs after updating recommended packages, (I'm not blaming reiserfs).
Installs were taking too long using Live CD so made a Live USB using usb-creator (for 8.04).
Downloaded Xubuntu 8.10 Beta to desktop, ran usb-creator, installing from the iso to a 2G Kingston.
Unplugged primary drive, inserted target drive, and installed from the newly created persistent drive into the previously created reiserfs partitions.
Tried booting the new, full install, flash drive
Had to revise menu.lst a bit as install got confused about which pendrive was root.
Got intrepid booted ok, then installed all the distribution updates.
Every thing seems to be working great so far with reiserfs.
Seems a bit faster now, not shure if intrepid might be helping.

---

### Post by nosoupforyou on 2008-12-30
Thanks for all the useful posts!
My current setup is
First partition (sdb1, I believe) - 2600mb FAT 32, /windows, Primary
Second partition (sdb2) - 5124mb Reiser FS, /, Primary
Last Partition, Swap Space, ~450mb (can't remember exact amount or what the total available memory was after formatting)

I did it like this so I can still use the FAT32 partition in windows but I cannot access it while running ubuntu off of the usb stick. 

As for the read/write cycles, I'm still a little concerned about my assumptions. I have a sandisk cruzer contour with 25MB/s read and 18MB/s write and is "enhanced for windows ready boost" + lifetime warranty (I don't know how easy they make it to replace) for $40. Assuming I have 1,000,000 read/write cycles and 450mb of swap, 450*1,000,000/25MB/s = 18,000,000s or 5000hrs but that's assuming every byte is written to evenly, I think that is how windows ready boost works to improve USB life. 

I tried the live USB creator in ubuntu 8.10 and some some pros/cons I found were;
pros
-system seemed to be faster after boot (the PC I'm testing this on has 3GB ram so that may be why, the PCs I'll probably use this on won't have nearly as much)
-less read/write cycles?
-easier set up for new users who may accidentally install to their hard drive
cons
-slower boot up
-logged in as live user (at least changes are still persistent)

---

### Post by unutbu on 2008-12-30
Hi nosoupforyou, thanks for the interesting question. I don't know for sure if wear-leveling applies to the whole disk or if wear-leveling is done on each partition separately.
Let's assume you are correct -- that it applies to each partition separately.
In this case, perhaps you can avoid the problem by deleting the swap partition, adding the space to the sdb2 root partition, and then creating a swap file which would reside within the sdb2 partition:

```
sudo dd if=/dev/zero of=/swapfile bs=1024k count=450      # 450MiB swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

And you can setup linux to automatically use the swap file  by editing fstab:
```
/swapfile none swap sw 0 0
```

---

### Post by nosoupforyou on 2008-12-30
Hi ubuntu, thanks for your reply!
> **unutbu said:**
> I don't know for sure if wear-leveling applies to the whole disk or if wear-leveling is done on each partition separately.[/CODE]

Wear levelling applies to each byte individually, or at least that's what I can infer from this statement about flash file systems on wikipedia. "Flash memory devices tend to wear out when a single block is repeatedly overwritten; flash file systems are designed to spread out writes evenly." So when we format a flash drive with FAT32, ReiserFS or anything else, the blocks don't wear evenly since we are using disk file systems.
[http://en.wikipedia.org/wiki/File_system#Flash_file_systems](http://en.wikipedia.org/wiki/File_system#Flash_file_systems)

I haven't done any real testing on swap partition vs file yet since the PC I'm using now has 3GB of ram. I'll have to try my other PC later or one of my friends, having your entire OS on a USB is great!

Also has anyone tried installing ubuntu to usb using unetbootin? How does it compare to what we are doing now? 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I also found this USB boot CD meant for booting up the live USB install for older PCs that can't boot from usb. Would it still work for the kind of install we are using? [http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/)

---

### Post by nosoupforyou on 2008-12-30
I decided to try the live usb installer method again, I first had to remove grub from the usb since it wouldn't let me boot into the live usb, here's the code I used if anyone is interested, it was pretty hard to find;
dd if=/dev/zero of=/dev/sdb bs=446 count=1
from; [http://www.tuxation.com/mbr-tricks-with-linux.html](http://www.tuxation.com/mbr-tricks-with-linux.html)

I was also able to access the entire memory of the usb (what was reserved in the casper-rw and the rest of what was available in windows!) this was not possible before when U3 was still installed on my drive for some reason.

I have come to the conclusion that the live usb creator in intrepid ibex is superior to installing to the usb drive as if it were a hard drive install because;
-you can format the entire drive in FAT32 so your entire memory is also visible in windows excluding anything that is stored in the casper-rw file
edit: I can't get it to work like this again and am going to give my previous set-up another try
-appears to be much faster (may just be my PC but try it yourself)
-less read/write cycles are done to the usb, when I ran ubuntu off of a regular install to the usb drive, the light that indicates writing to the flash drive is always flashing even when the pc is idle, there appears to be much less writing to the usb stick off of a live usb install, this will increase the life of your usb drive (amount varies greatly) and increase performance based on your PC

-the only downside is that you have to go through the live usb boot screen every time you boot up and you are logged in as a live-cd user, I may submit this idea to brainstorm for a usb installer that uses the regular boot screen and as a regular user, I think this would be a great feature with many possibilities
edit: It would also be great if you could partition the usb so that one of the partitions is accessible via windows the usb ubuntu install for transfering over files.

I was also reading what unetbootin does and it appears to just install the distribution to your usb drive and then modify the MBR on your PC to but the iso from the usb "UNetbootin uses a Windows or Linux-based installer to install a small modification to the bootloader" [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

edit: I found an idea which I believe is what I wanted on brainstorm, this is probably the best way a usb installation could be done but you guys are all more experienced than me so tell me what you think.
[[IMG]http://brainstorm.ubuntu.com/idea/12558/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/12558/)

---

### Post by nosoupforyou on 2009-01-01
After doing a lot of testing I've finally found a configuration that consistently works and suits my needs by having a partition that is visible through both windows and the usb-installed ubuntu. I've got enough free space to comfortably install updates to ubuntu and run it at a pretty good speed. I don't know how long the usb flash drive will last but since the price of drives drops so fast, my 8GB sandisk cruzer contour will probably be worth $5 by the time it wears out.

I did a regular ubuntu installation to the usb drive with a 2GB FAT32 primary /windows partition (has to be first to be used in windows) and a 6.6GB ReiserFS (better than ext3, haven't tried ext4 yet) primary / partition. I did not use swap space since most computers should have enough ram to easily run ubuntu by now and using the same usb drive to both load ubuntu and use as swap isn't that fast and increases wear to the usb drive. For some reason I could not access the FAT32 partition in ubuntu and I have no idea if this is what fixed it but after I installed ubuntu, I reformatted the FAT32 partition with windows and it worked.

If the brainstorm for a real usb installer is implemented that will probably be the way to go but for now the above configuration seems to be the best for doing what I wanted.
Also remember to install grub to the first part of the USB drive (eg. not sdb1 or sdb2 but sdb)

Thanks everyone for all your help! Everything works great now so I won't be doing any more testing or configuration changes at least until the next major release!

---

### Post by moycano on 2009-01-04
In the past months I've successfully installed xUbuntu in a 2.0GB FlashDrive in the followings ways:

1. The console method proposed in pendrivelinux (liveusb, ~1GB)
2. A full installation via LiveCD (without any HD plugged, ~2GB).
3. By automated ISO extraction via UNetbootin (~1GB), and
4. Via the usb-creator since Intrepid Ibex (~1GB).

And maybe the latest is the most balanced solution overall (size/functionality/simplicity) but still doesn't provide the freedom witch **nosoupforyou** and myself are talking about: *loopmounted filesystem* would be great.

[[IMG]http://brainstorm.ubuntu.com/idea/12558/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/12558/)

---

### Post by herold on 2009-01-18
I installed Ubuntu 8.10 from a live CD as a "liveCD" on a 4 GB USB drive, and it seemed to run well.  Then it offered to do an update, and since it is on a USB drive rather than on a CD, I clicked on the update.  The update seemed to go well for a while, like it would on my hard drive, but then hung.  I tried rebooting, but Ubuntu hung after the first splash screen.  So I deleted all of the files and reinstalled Ubuntu 8.10 live from the live CD.  Again, Ubuntu live ran well from the USB drive until I tried to update.  Again, it  hung, and failed after the first Ubuntu splash screen.  I was under the impression that  I could update a live "CD" installation on a USB drive, but that does not seem to be the case.  Does anyone have any more information on this?

While the drive is a 4 GB drive, it came with some Windows software on it, and I left it, thinking it would not cause any problem.  So only 3.7 GB is left for Ubuntu.  The update evidently was a big one, as I recall it was going to install over 200 files.  Am I running out of space on the drive?

---

### Post by moycano on 2009-01-18
Herold,  how much space do you leave to "save configuration and files" when execute the live-usb assistant? Maybe you didn't have enough to successfully apply the update.

---

### Post by herold on 2009-01-19
> **moycano said:**
> Herold,  how much space do you leave to "save configuration and files" when execute the live-usb assistant? Maybe you didn't have enough to successfully apply the update.

When I click on Places, Computer, Disc, and right-click on Disc, it shows 4.0 GB media, 207 items totaling 829 MB, free space 2.9 GB, total capacity 3.7 GB, filesystem msdos.  The usb drive, a Cruzer micro 4 GB usb stick, was formatted as FAT32 when I received it, and I did not change that.  It looks to me like I have 2.9 GB left, so running out of memory on the USB stick should not be a problem.  The computer, a Dell Vostro 1500, has 4 GB of memory installed (it came with less, and I added more to make a total of 4 GB), so I am thinking that even if all of the updates are saved temporarily in RAM, there should still be enough memory.

---

### Post by gett on 2009-02-04
hi
I'm considering buyng 1 TB USB HD, which I want to use at home and at work. Did I have to install Ubuntu 8.10 for all comp's (home - notebook & Desktop PC; work Desktop PC) and their different hardware?

---

### Post by Herman on 2009-02-05
No, you shouldn't need a separate Ubuntu installation for each different type of hardware, one installation should work for all your computers. That has been my experience anyway. 

If you read the forums you may see here and there where there are still a few various brands and types of hardware that are difficult for one reason or another. 
For the most part though, Ubuntu supports an amazing variety of hardware and will set itself up on boot-up for all kinds of keyboards, mice, monitors and most video cards, ethernet cards and so on. Sometimes it seems to take longer to boot when it gets moved from one computer to another, but not too much longer. You can hot plug keyboards and mice. 
I have an EeePC and it has a great wireless networking card. Ubuntu can detect wireless networks with it and join the network if it's unencrypted or if it's encrypted and you know the password.
If you use 32 bit Ubuntu it will work in both 32 and 64 bit computers.

Be very, very careful with your external hard drive when you are carrying it around, remember if you trip or slip and fall and drop an external hard disc drive hard enough to physically damage it you might lose all your data if it's not well backed up. 
(That happened to my wife one day on her way home from the office, she tripped coming up the steps at home).
USB flash memory sticks are much more durable, but of course, the problem then is the size limit for the amount of data you can save. 
An SSD in an external hard drive caddy would be cool, but more expensive, but your data would be safer than in a mechanical hard disk drive. Just a thought.

Regards, Herman :)

---

### Post by gett on 2009-02-05
> **Herman said:**
> No, you shouldn't need a separate Ubuntu installation for each different type of hardware

Thank you Herman for response, and of course thank you for wonderful site =D> you maintain, I learn a lot from it

---

### Post by nosoupforyou on 2009-02-22
I recently found ubuntu net-book remix [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr) the key feature I noticed was under system requirements "Storage: 4 GB Flash disk (SSD) or hard disk" so does that mean it includes packages that better optimise the desktops performance for running off a usb drive? Either way, flash memory has come a long way, still amazed with the possible read/write speeds of SDXC cards, it shouldn't really matter what type of media you install ubuntu to, but it is still nice to see flash memory as a possible system requirement for ubuntu.

Also has anyone tried using ext4 to format their USB drive and how do you find it compares to ReiserFS which is currently the best for a USB drive. Once Jaunty Jackalope is released, I will probably format my drive and let you guys know if no one's tried it out yet.

---

### Post by Herman on 2009-02-22
@ gett, thank you very much for the compliment, I'm happy if you found it helpful or interesting :D

@ nosoupforyou, Look at what's coming: USB3,

[USB 3.0 in the flesh - Engadget]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=2&url=http%3A%2F%2Fwww.engadget.com%2F2008%2F01%2F10%2Fusb-3-0-in-the-flesh%2F&ei=7QyhSfH-M4GStQO8sLHNCQ&usg=AFQjCNGQhRohXCw8sBuARvCCPA16Gn_-PQ&sig2=1Sp79ZdgrWx7w5CHmu8aog")

[USB 3.0 brings optical connection in 2008 | News Blog - CNET News]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Fnews.cnet.com%2F8301-10784_3-9780794-7.html&ei=7QyhSfH-M4GStQO8sLHNCQ&usg=AFQjCNExL1L4Qq-jWKagFqVRHNSaK8OPHQ&sig2=wkNk9kb5pPluUYTgMqqrNw")

[Revealed: USB 3.0 jacks and sockets • Register Hardware]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fwww.reghardware.co.uk%2F2008%2F01%2F09%2Fces_usb_3_revealed%2F&ei=7QyhSfH-M4GStQO8sLHNCQ&usg=AFQjCNGjD2npF_UXTlVRP6PAq8I1CR_Ufw&sig2=M3CShfCeU9CMsJfOyzICNw")

I think flash memory use will increase in the future, (I'm only guessing though).

---

### Post by lastfrontier on 2009-03-05
what about backtrack will this work for all iso's???

---

### Post by Cabs21 on 2010-01-05
Def going to retry this.  Thought was not possible when I got memory full errors.  Now that I have some help I will def give it another go. THX

---

### Post by Herman on 2010-08-21
:D There seems to be a number of forum users asking questions about how to do this, so I guess they're not able to find this old thread.

Rather than repeating the whole thing all over again, 



                                                     < BUMP >

---

### Post by confused57 on 2010-08-21
> **Herman said:**
> :D There seems to be a number of forum users asking questions about how to do this, so I guess they're not able to find this old thread.

Rather than repeating the whole thing all over again, 



                                                     < BUMP >

Hi Herman,  good to see you around the forum, hope you're doing well.  My 16Gb Patriot Xporter XT with 10.04 installed really comes in handy(it's a pretty fast flash drive).

I thought I'd mention that all of the links in your first post point to your previous account with Bigpond, didn't know if you were aware of this or not.

Take care,  
Jim

---

### Post by Herman on 2010-08-21
:D Hello confused57, 
I think I have those links all fixed now, thanks for letting me know. 

My old ISP, Bigpond really made a lot of work for me when they suddenly decided to discontinue bundling their free websites with their ADSL accounts. I use to think they were great before that. 

I'm doing fine and thanks to computer skills I picked up from using Ubuntu and hanging around these forums I have had a promotion into a great new job. I'm doing GPS and GIS work now and I love it. I moved into my new office last week. 

Good to see you're still around too and I hope you're also doing well.

Regards, Herman :)

---

### Post by thornspear on 2010-10-04
I've recently installed ubuntu 10.04.1 Desktop on a 4GB flash drive.   I've noticed I cannot install any software (from Ubuntu Software Center)  or plug-ins like MPEG-1 so I can play mp3s.  

Can I not use the  USB disk as an actual HD?  Do I have to use something like Puppy Linux  to acheive this? Or have I missed something?

---

### Post by snowpine on 2010-10-04
> **thornspear said:**
> I've recently installed ubuntu 10.04.1 Desktop on a 4GB flash drive.   I've noticed I cannot install any software (from Ubuntu Software Center)  or plug-ins like MPEG-1 so I can play mp3s.  

Can I not use the  USB disk as an actual HD?  Do I have to use something like Puppy Linux  to acheive this? Or have I missed something?

What are the specific error messages please when you try to install software?

---

### Post by thornspear on 2010-10-04
Interesting.  I was able to install VLC media player.  Originally when I looked in the Ubuntu Software Center for it, it didn't show the "Install" button to the right.  I had to click on "more info" and then another button appeared in there like "use this source".  When I clicked on that button, it changed into "Install - Free".  

I tried to uninstall VLC media player to re-create the scenario, but now it looks like it should ie.   the "Install" button to the right, after I enter my search criteria and hit enter. 

The MP3 error I'm receiving, is when I double click on an MP3, Movie Player attempts to search for a suitable plug-in, and... lol

Very strange, this time it actually worked.  I wonder if installing VLC had anything to do with it?  

Thanks for your quick reply snowpine, looks like I'm good to go for now.

---

### Post by snowpine on 2010-10-04
> **thornspear said:**
> 
Very strange, this time it actually worked.  I wonder if installing VLC had anything to do with it?  

Thanks for your quick reply snowpine, looks like I'm good to go for now.

Yup, VLC includes a bunch of codecs (including mp3 support) as "dependencies." Good luck with it! :)

---

### Post by thornspear on 2010-10-05
How do I go about saving my sessions to USB?  So when I boot from the flash drive again, all my files and software and settings remain.

---

### Post by snowpine on 2010-10-05
> **thornspear said:**
> How do I go about saving my sessions to USB?  So when I boot from the flash drive again, all my files and software and settings remain.

Ubuntu's 'usb-creator' application gives you the option to create a "persistent" USB install that will save your settings and files.

---

### Post by thornspear on 2010-10-05
I used windows to create my USB stick. 

I used the how to from this site: 

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Which uses the Universal USB Installer from [www.pendrivelinux.com](www.pendrivelinux.com)

I'll try and use Ubuntu's USB creator tonight when I get home as I don't have Ubuntu running on my work computer. 

I've tried using Ubuntu's USB creator in the past, in an attempt to install puppy linux, but I haven't had any success with it.  The program would never let me select the .ISO file.

---

### Post by thornspear on 2010-10-05
my bad.  There is a persistence option using the universal installer.  I must not have changed the default.  

Thanks.

---

### Post by MBybee on 2011-07-07
As someone who does this (on an SD card, actually), I have to highly recommend it. 

Currently have several people in my department running this way - it's great for keeping good backups (just rsync) and for being able to easily swap out machines.

Not sure why such an old thread was resurrected though - aren't there quite a few sites dedicated to this?

---

### Post by Thirusan on 2012-09-01
Check out my video it's easy to understand and much better it helps you refer back to this site if you want for more help:

I made two different videos one is easy and can only be done on certain OS such as Ubuntu 
Linux mint and some other ones.

But the second video explains how to install any Linux operating system on a usb.

First video:
[http://www.youtube.com/watch?v=oOsC5_-ph_M&list=UUKPnZFyxZ0uKhaJ6774YjiA&index=2&feature=plcp](http://www.youtube.com/watch?v=oOsC5_-ph_M&list=UUKPnZFyxZ0uKhaJ6774YjiA&index=2&feature=plcp)

Second video:
[http://www.youtube.com/watch?v=dWrmi4c6lFU&feature=player_profilepage](http://www.youtube.com/watch?v=dWrmi4c6lFU&feature=player_profilepage)

---

