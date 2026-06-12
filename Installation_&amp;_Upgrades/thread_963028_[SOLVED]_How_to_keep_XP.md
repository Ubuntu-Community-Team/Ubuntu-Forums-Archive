---
title: "[SOLVED] How to keep XP"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by aculade on 2008-10-29
Hey everyone:

I started using Ubuntu a few months ago, learned a lot, loved it, installed it dual boot with XP, liked it so much I got a new hard drive, and installed it as the only OS. I haven't used XP since I can't remember when (until today at least) but now I'm noticing I would like to be able to dual boot into XP if I ever need to.

Hard drive 2 has the Ubuntu partition, swap, and about 50 GB free space. I also still have the old hard drive I had XP on (Hard drive 1).

My question is, since I'm unwilling to reinstall Ubuntu, I've got it (almost) just perfect now...is there any way I can just copy the 10 GB of files on HD 1 to the partition on HD 2 and set it up for dual boot manually?

I thought about just running XP off of the second hard drive in the external enclosure I got for the drive, but from what I've read, that's not gonna work. From what I understand this would have been easy as cake if I just copied the old hard drive to the new one, then installed Ubuntu from the CD to dual boot...but I didn't...what do I do now?

I'm on a laptop, so any two hard drive solutions requires one be USB and my BIOS doesn't look to boot from USB (and I haven't seen anywhere I can make it anything other than floppy, CD, hard drive, and one other thing not USB drive).

Any help is greatly appreciated! Thank you.

---

### Post by xen-uno on 2008-10-29
This is how I would to it ...

1st off, burn a SuperGrub disk ( see [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) )

Put in the new drive (take out the Ubuntu drive temporarily), enter your BIOS so it knows of the hardware changes and save, then install XP. Re-install the Ubuntu drive and enter BIOS again to update (Windows drive will be the primary boot drive but make sure HD boot order is correct). Login to Windows. You can have only 1 active partition so you need some software (I like Paragon Hard Disk Manager, or try this ... [http://partitionlogic.org.uk/download/index.html](http://partitionlogic.org.uk/download/index.html) ). You need to remove the Active designation of the Ubuntu partition. Gparted may also do this ... I don't know.

Now use the SuperGrub disk which will install the Grub bootloader onto the new boot partition and tie into your existing Ubuntu install. If SuperGrub correctly identified the partitions (hd[color=red]x[/color],[color=red]x[/color]), you should be able to dual boot.

Grub: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This may be of use too ...

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

You don't need to mess with partitioning as your dedicating a hard drive to XP which is the best way.

---

### Post by caljohnsmith on 2008-10-30
So the Ubuntu HDD is not currently in a USB enclosure, is that true? How are you currently booting Ubuntu, i.e. is your BIOS set to boot the Ubuntu drive? As far as moving XP to your Ubuntu drive, you might be able to use something like "clonezilla" to copy the partition over. One thing you will need to consider is what partition Windows gets on your Ubuntu drive; if Windows was on the first partition of HDD1 and you move it to any partition other than the first partition on HDD2, you will need to modify the Windows boot.ini file (not a big deal though). 

Another option would be to create an NTFS partition on HDD2 for Windows, use linux to copy all the Windows files over, install the Windows boot sector to the Windows partition, modify boot.ini if necessary, and that just might work (haven't had the opportunity to test it myself though). 

Just to clarify your setup, please post:
```
sudo fdisk -l

```
Let me know what you decide to do or if you would like further help. :)

---

### Post by aculade on 2008-10-30
Thanks so much for your help Xen-uno. I went a slightly different route though.

Ohp...I was just about to post what I did and saw your post Caljohnsmith. It does work, wish I had met you last night. haha. Thank you though.

I figured out a way to do it, not sure if it's the best, but it's the only way I could come up with--and it works EXACTLY like I was hoping! Ubuntu is the best!!

Disclaimer: I've only been working with Linux desktop environments for a few months now...use at your own risk.



--- When to use this tutorial ---
You have two separate hard drives, one with Windows and another with a Linux OS, and you want to make them dual boot (or triple, quadruple...whatever your OS-loving heart desires) from the same hard drive because you have a laptop or don't want to mess with setting up two hard drives or can't have two hard drives. You have a hard drive with Ubuntu just the way you like it and you don't have a Windows install CD. This allows you to just copy all of your Windows stuff and put it on the same hard drive as your Ubuntu stuff. Then, when you turn on your computer, you can choose whether you're in an Ubuntu mood or in a Windows mood. Then this is what you do!

--- When NOT to use this tutorial ---
If you haven't installed Ubuntu yet and only have Windows, while in Windows save the Ubuntu download from [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download"), burn it to a CD, put the CD in your CD tray, don't run the CD, shut down your computer with the CD still in the CD drive, turn back on your computer, and install Ubuntu as a dual booting OS. This way Ubuntu does all the work for you. It's incredibly easy. This is just for if you already have Ubuntu installed and have done a lot of tweaking and don't feel like losing everything and reinstalling Ubuntu and also don't want to reinstall Windows and have to reinstall all of your programs and save all of your files back into Windows.

If you have a desktop and can just install both hard drives. This will still work, but you'd probably be better off just leaving them on separate hard drives and in the part where we mess with GRUB and the boot.ini file, assigning them too look on different HDs. Just have to make sure that Windows is on your master drive and Ubuntu on the slave since Windows hates not being top dog. There is a way around it in GRUB by mapping the drives to each other, but I don't understand it and it wouldn't have helped my situation. You're better off to do a search for that instead.



Time to complete:
Without researching and everything like I tried to, probably only about 1 hour (But it could take all day; it totally depends on how big your Windows HD is as transferring the data takes most of the time. The smaller the better...the faster!!!). When I did it, it transferred about 10 GB by USB (a firewire external HD would be quicker) and resized the partitions in about 2 hours. So budget about 2 hours per 10 GBs if using USB, less for firewire. But whatever happens, you have to wait. You CAN NOT abort transferring the drives or resizing...you would likely lose everything. Just wait...even if it takes 2 days.

Things you need:
- Most everything is done using graphical interfaces, but you will have to do just a little from the command line. But when I say type "blah blah" you just type (or copy and paste) blah blah in the terminal and everything will be just fine. So it helps if you're not afraid of the command line, but certainly don't need to know anything about it really
- Your original Windows HD
- A second hard drive with a Linux OS already installed on it (Note: This hard drive must be big enough that you can fit both OSes...mine is 100GB and was plenty.)
- An external 2.5 inch (for laptop hard drives) hard drive enclosure, I got the NexStarSX IDE to USB 2.0 enclosure for about $15. Works like a charm. It does require two USB ports at a time though...just a warning. If you have a SATA laptop hard drive you will need a SATA to USB enclosure. If you have a firewire port, get an enclosure for firewire instead of USB
- The small screw driver that comes with the external HD enclosure for switching the drives. You may need to look up your computer's manual online to see how to remove your hard drive. For my older Toshiba Satellite it's just a single screw on the bottom of the right-hand side. Unscrew the screw, gently pry the cover off, and pull the piece of plastic connected to the hard drive until the drive slides out. Piece of cake, takes literally 30 seconds. Just make sure your not holding a static charge and don't touch anything but the plastic tab or the sides of the drive. Be gentle



**1.** With your Windows HD in your laptop, go through and get rid of any pictures, videos, music, and programs you don't want to keep. If you're like me, you already moved all of your important documents, pictures, and accounting program exports when you realized how much Windows used to abuse and take advantage of your good spirit and how powerful, customizable, and stable [insert any mainstream Linux OS here] is!

It's best you take your time and don't delete anything you could miss or don't know for certain what it is. If you're uncomfortable deleting stuff, don't worry about it, it'll just mean you have to wait a little longer on transferring everything and might mean you have to do a little resizing before and after transferring depending on how big your Windows installation is and how small your unallocated space on your Ubuntu hard drive is.

It also isn't a bad idea to Defragment the disk before trying to move it. You want to keep running the Windows Defragment utility until your data is towards the front of the graphic at the bottom. You can do a search for more info on defragmenting your Windows HD.

I got my Windows HD from over 30 GB down to under 11 GB on a 40 GB hard drive by getting rid of home movies (big space stealers...a couple GBs each), music (my music CD backups), and huge programs that I never used (like software for music editing, movie editing, games, etc.). Just burn these things to a CD or DVD, put them on a big flash drive, or put them on an external hard drive so you can still have them. Just be careful.

**2.** Reality check: essentially you will be transferring your entire Windows hard drive into the available space on your Ubuntu HD. So, needless to say, you have to have room to put it.

In my case, I have a 40 GB Windows HD and a 100 GB Ubuntu HD. When I installed Ubuntu, I set Ubuntu to run in a 48 GB partition with a 2 GB swap partition. That left about 50 GB of unassigned space on my hard drive. This made it incredibly easy to copy the entire Windows HD into a new partition on the Ubuntu HD without having to ever risk losing the Windows data by resizing the partition etc. on the Windows hard drive.

If you don't have enough free space, like when you installed Ubuntu you told it to take up the entire disk, you will need to do step 10 just with the Ubuntu partition. With the Ubuntu HD installed in your computer, start Ubuntu, open GParted, and make the Ubuntu partition small enough to fit the entire size of your other hard drive in the free space on the Ubuntu disk following step 10 below just with the Ubuntu ext3 partition. 

If your Windows hard drive is just too big to fit on the new drive, with the Windows HD installed in your computer, you will need to delete as much as you don't need from Windows, defrag the drive a couple of times, switch the HDs, put the Windows HD in the external HD enclosure, and from Ubuntu plug in the external HD, run GParted, and resize the Windows partition to just a little bigger than the minimum size just like in step 10, just it will be done on the Windows NTFS partition while it's still on "/dev/sdb" (the external HD). But then if something goes wrong you don't have any copies of the drive so you could lose data, although it is unlikely. Just please backup first if possible.

In short, your Ubuntu hard drive should have at least as much unallocated space as the size of your Windows HD. That minimizes a fair share of the risk of losing all your data and is by far the easiest way I could think of. If this isn't an option, you have to do one or both of the two paragraphs just above.

**3.** Turn off your computer, unplug the power, and install your Ubuntu hard drive into your laptop and put the Windows HD in an external 2.5" HD enclosure. Mine was USB because that's all I have. Make sure you don't static shock/drop anything--HDs can be delicate.

**4.** Boot up Ubuntu by turning on your computer with the Ubuntu drive installed.

**5.** You need to be able to work with the NTFS filesystem that Windows XP (and 98-ME) uses.

(If you're not on XP and not sure what filesystem your OS uses, with your Windows hard drive installed in your computer right-click the C:/ drive, click Properties, and make sure for the file system it says NTFS. If you have XP don't worry about it and leave your Ubuntu hard drive in.)

a) Open the Synaptic Package Manager
   Main Menu > System > Administration > Synaptic Package Manager
b) Type in your password
c) Click the Search button
d) Type in ntfsprogs
e) Find ntfsprogs in the list and right-click it
f) Select Mark for Installation
g) Let it install its dependencies as well
h) Then click Apply from the Synaptic Package Manager main window
   The NTFS programs will be installed

**6.** You also need to be able to work with partitions. I used GParted...worked like a charm.

a) Still in the Synaptic Package Manager, Click the search button
b) Type in GParted
c) Right-click gparted, Mark for Installation, Install dependencies, Apply
d) You can close the Synaptic Package Manager

**7.** Make your Windows HD available from Ubuntu.

a) With the Windows HD properly installed in the external HD enclosure, plug the enclosure's cables into the USB ports (or firewire port) in your computer
b) Flip the on switch (if there is one) on the external HD to turn it on
c) Ubuntu should automatically detect the drive and mount it. You're good to go. If not, you'll have to find another tutorial on mounting drives from the command line.

**8.** Open Gparted
   Main Menu > System > Administration > Partition Editor

**9.** Copy the Windows partition from the Windows HD to the Ubuntu HD.

a) In GParted, click the drop down list at the top-right corner that says something like /dev/sda (93.16 GB) (this will be different for your HD but similar).
b) Select the other drive
c) Right-click the NTFS Windows partition from the list of partitions
d) Select Copy
e) From the drop down list at the top-right again, go back to the drive that has Ubuntu and your swap partitions on it
f) Right click below the list of your partitions, and select paste
g) It will now say at the bottom of the GParted Window something to the effect that a partition needs to be created/copied, I can't remember which
h) Click Apply at the top of the GParted window
i) Prepare to wait between 30 min to a couple hours. By USB, it took me about an hour to transfer my 40 GB Windows HD partition to the open space on the Ubuntu HD

**10.** Still in GParted, once the Windows NTFS partition has been copied to the Ubuntu HD, resize the Windows partition.

a) Right-click the NTFS partition on the Ubuntu HD, and click Resize/Move
b) Look at the number towards the top where it says Minimum Size. This is the actual size of the data on your HD.
c) Take that number and add N*1024, where N is the number of GB of space you think you might still need Windows to be able to use.

Example:
Under Minimum Size mine said 10672 MiB. This means that on my old HD, all of my files took up about 10.4 GB. I decided I would never need more than 2 GB of extra space for Windows to be able to use, so I decided that the New Size should be 10672 + (2 x 1024) = 12720 MiB.

d) Type this size into the New Size MiB input field
e) Slide the rectangle either to the front or the back of the available space by clicking in the middle of the rectangle and dragging it. Free Space Preceding or Free Spacing Following should be 0.
f) Click Resize/Move
g) Now in the main GParted window click Apply
h) Now you will wait again while it resizes and shifts the partition. This will take quite a while also, go eat or something. Whatever you do you can NOT, I repeat DO NOT, abort! You must wait. It will take forever, it may look like nothing's happening, but if it takes two days, you have to let it take 2 days or you'll likely lose everything on that partition
i) Once it's done, you can close GParted

**11.** Mount the new Windows partition

a) Open up the Ubuntu File System utility
   Main Menu > Accessories > File Browser
b) You should see on the left somewhere under File System a mysterious "##.# GB Media"
c) Right-click and select Mount
d) Type in your account password if it asks

**12.** Let GRUB know you want it to give you the option to boot into Windows.

a) Open the terminal utility
   Main Menu > Accessories > Terminal
b) Type "cd /boot/grub", no quotes
c) Type "ls" to see a list of the files
d) Make a backup of the menu file before we mess with it
   Type "sudo cp menu.lst menu.lst.backup"
   Enter your password
e) Type "ls" again and make sure you see a file menu.lst.backup. If so, your good, let's continue.
f) Type "sudo gedit menu.lst", enter your password. If this doesn't work because you don't have gedit installed try "sudo pico menu.lst"
g) The file opens in a new window
h) Scroll down just a little in the file until you see the line "## timeout sec", below this on the first line that doesn't have a # sign change the number after "timeout" to something like 10 or 15. This is the number of seconds you have to choose what OS you want to boot.
i) Below the line that says "## hiddenmenu", change the line that doesn't start with a # sign and change "hiddenmenu" to "#hiddenmenu". It will now show you that you have a choice of OSes without you having to press the escape key as soon as you turn your computer on
h) Now scroll to the very bottom of the file. The VERY bottom! It does matter. Copy and paste the following, you can change the title if you're doing this for an OS other than XP Home, it's just so you know what you're picking:

## Manually added copied XP partition from old hard drive to be bootable
## from the same hard drive running my Ubuntu install
title        Microsoft Windows XP Home Edition
root        (hd0,2)
savedefault
makeactive
chainloader    +1

You may have to change the root line. Reopen GParted as before, give it your password, now look at where it has your NTFS partition. At the far left it says something like /dev/sda3. Make a note of the number at the end of /dev/sda3. For me it is 3. This means my root line should read "root (hd0,2)". This says look for the boot script on hard drive 1, partition 3. Remember, Linux counts 0, 1, 2, etc. So the second number for the root line should be 1 less than the number from GParted.

You can close GParted.

i) Bring back up the menu.lst file by clicking it in your taskbar/panel. Change the (hd0,2) to (hd0,#), where # is 1 less than the sda#
j) Click Save
k) Close the menu.lst file

**13.** Now we have to make Windows happy. Windows doesn't play nice with others...it's very jealous and it expects to be your one and only. But too bad, Windows isn't top dog anymore.

a) Open up the file system again
   Main Menu > Accessories > File Browser
b) Click the "##.# GB Media" that we mounted earlier from the left
c) Scroll down until you see the file "boot.ini", double-click it
d) Just click Display (if it asks)
e) Change the partition(#) in the two lines "multi(0)disk(0)rdisk(0)partition(2)\WINDOWS" to the same number you told GRUB to look in, 2 for me again.
f) It is possible that Windows and Ubuntu use different numbers for the partition. You'll know this if when you startup your computer, you select the Windows OS, and it says can't find "HAL.DLL". If that happens, just boot into Ubuntu and repeat this step 13, changing the number for the partition(#) part. Start at 0 and work your way back up until it boots Windows successfully.


**14.** Reboot in Windows

a) Save and close everything in Ubuntu before shutting down
b) Restart the computer
   Main Menu > Quit select Restart
c) When your computer restarts you will be greeted by a black screen with a list of a few different kernels and OSs. Choose the one with the title that you created in step 12. If you don't want to run Windows, you can choose one of the Ubuntu listings or if you don't touch anything when the screen comes up on startup, after some number of seconds it will automatically boot your Ubuntu installation.



Congratulations! I assume this would work for installing even more (non-Windows) OSes as I do know that if you install Windows from a CD it can just overwrite your boot instructions by using it's bootloader instead of GRUB. Hope it helps and saves you the 8 hours I spend on figuring it out.

---

