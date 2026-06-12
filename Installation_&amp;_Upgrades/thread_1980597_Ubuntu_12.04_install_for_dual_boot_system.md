---
title: "Ubuntu 12.04 install for dual boot system"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by hockey9876 on 2012-05-15
I'm looking to upgrade my desktop system to ubuntu 12.04.
The system has 2 hard drives, one with ubuntu 8.10 (hd0)and 
the other is windows vista (hd1).  Each drive is 500gb.

My concern is that I've seen a lot of literature where dual
booted systems do not work with 12.04.  My question is how can
I tell during the install process whether it recognizes the
other hard drive so that the windows drive is added as a menuitem
for display during the boot process?

Any insight would be greatly appreciated.  

John

---

### Post by jadtech on 2012-05-15
it does for sure work with dual boot systems  no matter if you have one drive with serveral partitions or  multiole hard drives :)

if you have  hard drive set raid then you need to get the alternate ISO to burn ...

you will know with out  a doubt if its seeing both drives and if you have any doubt before you install use gpated to make partitions  where you want them and you  direct the install to the / Root you made for the install

---

### Post by oldfred on 2012-05-15
I have not seen where 12.04 does not work for dual booting. Not to say there are not some issues which we seem to get a lot of here, since we are here to solve issues.

My system dual boots with 4 drives. XP is on sda. Many are booting multiple systems on multiple drives. Even XP and Windows 7 & Ubuntu or Windows 8, XP and Ubuntu.

With multiple drives it is best to understand partitioning and use manual install as that gives the option of where to install grub2's boot loader. All the auto install options normally install grub2's boot loader to sda. If your system lets you boot either drive, it is best to keep each system separte, some suggest disconnecting the Windows drive to avoid issues.

The desktop has changed a lot with Unity, but the install process is almost the same as it has been for ages. Minor differences, one being manual install is now Something Else.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by hockey9876 on 2012-05-17
Oldfred,

Your advice was spot on.  Worked like a charm.  The only thing I have left
is how do I increast the font size of the menu when the system boots
up.  The old black & white was decently sized.  This new one I need a 
stronger perscription to read it...

Thanks,

John

---

### Post by oldfred on 2012-05-17
Same here, I have not yet changed my display as I almost always just let it boot the first entry. I have other grubs in other drives and often use BIOS' one time key to choose another install.

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

Grub now seems to be able to find your video mode so it uses the new resolution, where the old was just a default of  GRUB_gfxmode=640x480.

Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768

or manually 
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub

---

### Post by grahammechanical on 2012-05-17
check out Grub Customizer

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I use it not only to increase the text size of the Grub menu but to put an image behind the Grub menu and also to hide those old kernel images that are left in the menu when there is a kernel update. Grub Customizer does not delete the images just hides them from the Grub menu.

Regards.

---

