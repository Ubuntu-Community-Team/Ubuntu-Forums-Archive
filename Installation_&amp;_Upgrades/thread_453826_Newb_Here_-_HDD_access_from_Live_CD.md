---
title: "Newb Here - HDD access from Live CD"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by U_Bunt_Who? on 2007-05-24
Hello!

New to the linux world here, but intrigued.

I partitioned my HD from the live CD.  I included a 100gig partition to share between vista and the live CD along with a swap partition.  (the [<ext2fsd> utillity ]("http://ext2fsd.sourceforge.net/") that was recommended by LaughingLoki works with Vista - at least it seems to)   I also left a 9 gig partition for an Ubuntu install.  I couldn't figure out how to get it to dual boot with Vista.  Seems to be the norm unless you have multiple HD's.

I can't seem to figure out how to access that partition from the Live CD.  Also, how can I save my settings when shutting down the Live CD?  

And last of all.  Root - how do I login as root?  I can't seem to find that one anywhere...

Thanks all.

---

### Post by jerrylamos on 2007-05-24
Not quite sure about your setup - some general Ubuntu things:
Usually root is never used.  Preface commands with sudo (acronym for pseudo) like so:
Applications, Accessories, Terminal

sudo mkdir /media/C
it'll ask for your regular password

sudo mount /dev/hda1 /media/C

ls /media/C

Now hda1 may vary, like sda2, or whatever.  Usually do:

Applications, Accessories, Terminal

df -h

and try to figure out what /dev your partitions are.  On my system /dev/hda1 is Windoze.  The /dev name can vary depending on firewire, IDE, Sata, gosh knows what.

There's a way to do that with menus too, Places, Computer will usually display the partitions, and you can double click on what you think are the various partitions.  It will ask you your regular password.  I don't have CD Live up at the moment to check on the keystrokes.

For dual boot, install Microsoft in first partition on first hard drive.

Ubuntu needs another partition, file type ext3, and a swap, at least 512 MB, file type swap

When you do the install of Ubuntu it sets up the dual boot.

BTW, I like to set up my partitions with Gparted.  It's System, Administration, Gparted.  If its not there, then do Applications, Add/Remove, search on Gparted, select it, and Apply.
You start Gparted and with the arrows in the upper right corner select the partition you want to set up, create, whatever.  Note changing Microsofts partition will likely kill it.

With the partitions set up ahead of time, on install select "manual" to check that everything's O.K.

I recommend "The Official Ubuntu Book" at your bookseller or Amazon.

As far as saving settings on CD Live, there's "persistent" mode on Dapper 6.06 and Edgy 6.10.  It's busted on Feisty 7.04  (gnash teeth) maybe, just maybe they'll get it running for Gutsy 7.10 due in October.  2007 that is.

Cheers, Jerry

---

### Post by eapache on 2007-05-24
There isn't an option in the installer for dual-boot. It should do it automatically.

To access a partition from the livecd, go to Places > Computer, and then right-click on the partition and say Mount.

To save settings, you will need a thumb-drive (cd is read-only).

You really don't want to login directly as root, as it leaves the computer insecure. To run an individual command as root, put sudo in front of it in the cmd prompt.

---

### Post by U_Bunt_Who? on 2007-05-24
Thanks folks.  Much appreciated.

As for the dual boot.  When I installed vista after ubuntu (all partitioned accordingly) it killed the ub boot.  If I installed it after vista, it would kill the vista boot.  They didn't seem to want to work together.  Is there a way to set the grub boot menu to include vista?

---

### Post by U_Bunt_Who? on 2007-05-25
Alright - Tried all of the above.  Still no go.

From the "Computer" it says cannot mount /dev/sda4 because it is not removable.

From the cmd line it says that it's not valid.

Any other ideas?

Thanks again all.

---

### Post by Albinodrew on 2007-05-28
Hi U_Bunt_Who?, welcome to the community and nice wordplay for your name.

First I'd like to correct jerrylamos on the meaning of SUDO, it means "**S**uper**U**ser**DO**", it comes from the old UNIX system.

U_Bunt_Who? help us helping you by giving us more info about you installation, like in this case,

1 - What Ubuntu version is yours LiveCD
2 - what is your total drive size, 120G 160G?
3 - What File System is your 100g partition, NTFS, ext3fs, FAT32 etc. 

For now I will assume (and hope I will not make an *** out of myself;)) that you have the 7.04 LiveCD and want to access (READ from and WRITE to) an ext3fs partition and cannot boot from an already installed Ubuntu.

After booting from the LiveCD, go to System > User and Group
click on "add user"
enter the usrename you already have created for your Ubuntu system, your name, your password and click VALIDATE

Now goto System > Quit
choose CHANGE USERS

It will looks like shutting down, but **wait and don't panic**, a connection window will appears

Enter your USERNAME, then you PASSWORD

Now you should be in your gnome desktop and have access to your files.

Checking it, goto   Places > Computer

You should have all your partition, as Disk1, Disk2 etc. (or something like that) as drive icon, double click on any one, it should open and show its content. 

Hope I've been of help.


**P.S.:** I highly suggest printing a posting that help, thus creating your own little rescue/reference documentations, just in case.

---

