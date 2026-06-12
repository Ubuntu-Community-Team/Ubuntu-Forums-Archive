---
title: "GRUB issues"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by Chubuntip on 2008-02-09
Hey, just getting my feet wet with Ubuntu.

I installed 7.10 text-based onto my external hdd (80g) (as sdb2) after many issues.
Now I go to load my computer, with the hdd attached and it loads up to the point of saying "GRUB" with the cursor flashing at me like a vindictive child.
I cannot type and rebooting only brings me back to the same screen.

Dear, dear Linux masters, lend me your wisdom.

---

### Post by logos34 on 2008-02-09
Are you booting from the internal or external drive?  If grub is on the mbr of your internal disk (the default install location), then the problem could be that your Bios does not support USB boot.

If so, then you could try [this workaround]("https://help.ubuntu.com/community/BootFromUSB").

---

### Post by InfoTech on 2008-02-09
What happens when external HDD is not connected? How does your BIOS recognise the external drive? Is that eSATA drive, or?

---

### Post by Chubuntip on 2008-02-11
according to my one-time boot menu, it recognizes the USB HDD and will allow me to boot from it.

I had originally used the text-based install and I went back and re-installed with the live CD and now the grub runs, but errors out between error 5 and error 17.

now it doesn't matter if the drive is connected or which option I select, I cannot get my windows to boot as I cannot get past the grub.

thanks for the replies.

---

### Post by Chubuntip on 2008-02-11
FYI, GRUB error 5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 

GRUB error 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

I found this info courtesy of Hermann @ [http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

---

### Post by Chubuntip on 2008-02-11
I tried to burn a super-grub image disk, but I'm not sure if this will help me.
It seems to my limited brain that I have a partition issue.

Should I go back to the live CD and try to fix any partition issues, and/or what issues am I looking for?

---

### Post by froy02 on 2008-02-11
My assumption is that you installed Ubuntu in the ext drive and you tried to boot by choosing boot from USB drive.
Grub was installed in the internal drive but the 'menu.lst' is installed on the ext drive. To verify that your Window$ is still intact type the following commands in the grub prompt followed by [enter]:

root (hd0,0)
makeactive
chainloader +1

If window$ boots up, you still have your win installation.
To get your ubuntu installation from grub, first find where it is:

code:find /boot/grub/stage1
This would would return something (hdx,x) where x's are numbers. It returns the location of your ubuntu installation. These numbers are the ones you're going to use on the next line.
code:
configfile (hdx,x)/boot/grub/menu.lst

The last command tells grub to run the configuration file in the (hdx,x) drive.

If these 2 test are okay install grub again by the following commands in the grub prompt
code:
find /boot/grub/menu.lst
This again would return (hdx,x) which is the drive and partition.

code:
root (hdx,x)
This where you want grub to run a menu.lst file

code:
setup (hd0)

This would install grub in the first hard drive's MBR and that should be it.

Now reboot.

---

### Post by Chubuntip on 2008-02-11
the stage1 finds fine at (hd0,1)
the menu.lst opens what appears to be a boot log...something like this:
+---------------------------------------------------------------------------+
| Ubuntu 7.10, kernel 2.6.22-14-generic                                       |
| Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)           |
| Ubuntu 7.10, memtest86+                                                          |
|Other operating systems:                                                             |
|Windows NT/2000/XP (loader)                                                      |
|                                                                                                      |
+---------------------------------------------------------------------------+

and when I select the Ubuntu options I get: "Error 21: Selected drive does not exist"
selecting the windows loader gives me: "Segmentation fault (core dumped) and it takes me back to a terminal command prompt.

But I persevere and try to install grub again. All goes well and I get the most excellent words "succeeded Done."

But at the reboot. Nothing has changed. Is this because of the faults with the menu.lst attempts?

Is it because the file is found on (hd0,1) and not (hd0,0)?

---

### Post by froy02 on 2008-02-11
After you made all the changes did you boot with the same configuration, without changing the boot order?  
If that did not succeed here's a website that's more comprehensive about grub.  I learned about grub mostly from this site:

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by froy02 on 2008-02-11
By the way, yes, the Linux partition is in (hd0,1) so if your menu.lst has the line 'root  (hd0,0) ' after the title line then change it to 'root    (hd0,1)' in your menu.lst.  That's what your search returned in grub according to your post.

---

### Post by Chubuntip on 2008-02-12
alright, after a little more education and a lot of reading, here's what I have. My internal HDD (hd0) is ntfs. 
My external can be whatever I want it to be since there is nothing of real value on it. Right now it is fat32 (minus the swap and root that I have installed)

When I look at my grub menu for Ubuntu 7.10, kernel 2.6.22-14-generic I get:
root (hd1,0)
kernel  /boot/...
initred  /boot/...

And I'm noticing that my grub> find /boot/grub/stage1 is reporting the grub location on (hd0,0). So, being as logical as I am, I try editing the grub menu from 'root (hd1,0)' to 'root (hd0,0)' which...as you linux masters can already guess...leaves my terminal yelling at me about unsupported formats.

(I want to thank you guys for sticking with me. It can be hard to tolerate the weak and inexperienced)

does this mean that I need to reformat my primary (hd0) HDD to fat32 or something grub can deal with? Or am I on the wrong track?  :confused::confused:

---

### Post by Chubuntip on 2008-02-12
And furthermore,
I have tried reinstalling (both 32bit and text-based) using all of my 80GB external (screw the data I had on it!) and rebooting. 

When I choose to boot from the internal: GRUB error 5.
When I choose to boot from the external: GRUB error 5.

The laptop I'm installing onto is the only one with the correct burner to make the super grub disk, so I'm wondering about bootable disks/usb drives and if anyone has any experience with those?

Seriously, I must be missing something so simple.

Be honest, would it be easier to go to a previous version? 6.10? 7.04? Level with me now...

---

### Post by Partyboi2 on 2008-02-12
Try this, and hope it helps
> Quoted from the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")5 : Partition table invalid or corruptThis error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.                                         Check the partition table by running fdisk as root ('sudo fdisk -lu) in Linux, or use your favorite partition editing software to make sure one of your partitions has been marked 'active'. If no partition is marked as active, you can use Super [COLOR=#000000]GRUB[/COLOR] Disk to do that for you.If more than one partition has already been marked as active, you need to remove the 'active' flag from one of them, as only one is supposed to be set as active at a time. Use your partitioning software of that.

---

### Post by Chubuntip on 2008-02-12
I finally managed to get the super Grub onto a flash disk.

This did allow me to boot my windows, but I cannot boot Ubuntu except from the live CD, which just doesn't feel like home.

I'm assuming that I am still having partition issues.

The future game plan is:
1. make a super grub disk
2. repartition my external HDD, leaving blank space for Ubuntu.
3. reinstall Ubuntu and pray to God that the super grub can find both OS's with no issues.

Any bets on whether this will work?
Anyone have a better idea for me?

---

### Post by froy02 on 2008-02-12
Here's the website where I got the info for bootable 1gb usb stick.  It works on my Toshiba laptop.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Back to your installation:
If you are installing ubuntu in an external hard drive make sure you use an alternate CD installation disk.  When you get to point partitioning write down the media where it would be installed.  Then when it gets to the part where it ask you where you want to install grub, choose the drive where it is installed rather than your internal hd.  That way grub does not touch your internal installation.  
The advantage is that you don't have to connect the external drive to boot your internal OS because the menu.lst is always in a Ubuntu (ext drive).  This is dual boot using the Bios.  The disadvantage is you have to choose which drive to use as boot usually by pressing F8.

The second option is dual boot using grub.  Grub is installed in the first hd and menu.lst in the external hd.  This needs the external hd hooked up to boot either OS'.  The disadvatage is that you can not boot either OS' if the external hd is not hooked up.

If you choose the first option you could always go back later and install grub in the internal hd and also if something does not install properly you will be dealing with only 1 installation problem.  
Hope this help you.

---

