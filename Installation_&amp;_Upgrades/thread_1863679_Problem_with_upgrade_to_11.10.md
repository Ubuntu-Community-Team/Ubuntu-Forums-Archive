---
title: "Problem with upgrade to 11.10"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by interacter on 2011-10-18
OK so this is my fault totally...

Long/short - always had an isse where if I left 11.04 alone for a few hours, the WiFi would drop and not restart until the desktop rebooted.  Never knew if it was the box or the router, but not a huge issue as never really left box running.

So start upgrade last night from 11.04 - 11.10.

Have to reboot halfway through as the WiFi dropped.  All started again fine.

This morning, click the Replace Network Config dialogue - and of course the network has died because the box was on over night.  

So the dialogue box then shows an error on every process line.

Being used to Windows, I figure that getting the system to reboot would be a good idea.  The option even said Reboot and Complete.

However, now it won't even boot.  Just gets to a black screen after the initial purple splash, then nothing.  Left it all alone for half hour and still nothing.

So I know this is my fault.  However, if I download the Upgrade image to USB, can I boot and upgrade from that?  

Or will I have to download the 11.04 image, boot from USB, pull off my data (emails/few files), reinstall the whole thing fresh and then upgrade? And then put my files back?

Thanks, in advance, from a very red faced noob........

---

### Post by garvinrick4 on 2011-10-18
You got one of two choices:
You can use a live cd with internet working and get into chroot of your file system
with some commands and try to finish upgrade or you can just reinstall.
If you want to try to fix with a live cd and chroot command give me output of this:
```
sudo fdisk -l
``` (lower case L)
and I will give you some commands to copy and paste. 
Or you can just reinstall up to you.

---

### Post by interacter on 2011-10-18
> **garvinrick4 said:**
> You got one of two choices:
You can use a live cd with internet working and get into chroot of your file system
with some commands and try to finish upgrade or you can just reinstall.
If you want to try to fix with a live cd and chroot command give me output of this:
sudo fdisk -l (lower case L)
and I will give you some commands to copy and paste. 
Or you can just reinstall up to you.

So, in essence, get it booting from USB then into terminal and go from there?  Have I understood that right (see, told you I was a noob... Only been on Linux desktop for a month, tops!)?

Would rather try to get the upgrade finished if I can - pulling off email/files etc is something I tried to avoid where I can just because it's boring!

I'll have to get that output later from home.  Should I d/l 11.04 and make a USB image or the 11.10 upgrade image to get into the system and then into terminal?

---

### Post by garvinrick4 on 2011-10-18
If you have a 11.04 or 11.10 usb or cd we can do it from there. (install cd using Try Ubuntu) All you do is boot off of
open a terminal and run some commands with your internet connected in Live Usb or cd. (make sure firefox connects to internet)
I am using sda5 as your linux install, [COLOR=Red]you use your own[/COLOR] from.
```
sudo fdisk -l
```Ok use your own sda# and copy and paste the rest.
```
sudo mount /dev/[COLOR=Red]sda5[/COLOR] /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
dkpg --configure -a
``````
apt-get update; apt-get upgrade
```If you got errors running above the internet is not working in live cd or usb. 
```
dpkg --configure -a
``````
apt-get -f install
```Does it say no more to upgrade.
If you got this far then might be ok.
```
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot
```Now lets see what happens you either got a working system or you do not and have to
reinstall.
#We are Mounting your install and a few more directorys and then checking to see if anything downloaded needs to be installed and for broken packages updating and upgrading system and unmounting what we mounted and rebooting.

---

### Post by interacter on 2011-10-18
Awesome - thank you!

Just a final noob question... what's sda?

---

### Post by garvinrick4 on 2011-10-18
> Just a final noob question... what's sda?In Windows partitions are called letters like C: or D: or F: and so on.
In Linux partitions are read as sda1 or sda2 or sda3 and so on and on.
They mean same thing,
When you run 
sudo fdisk -l (lower case L)
Will give you your sda#'s and one will be your Linux install. Will say Linux next to it.
so if it is sda1 you just replace my sda5 with sda1. (if you need help just post the outcome,  me or someone can tell you which it is.)

---

### Post by interacter on 2011-10-18
Ahh that makes sense!

Just creating the 11.10 USB now via my Ubunutu netbook - will get onto this as soon as I get home and update later.  Thank you for all the help!
Neil

---

### Post by interacter on 2011-10-18
Hiya

Righty ho...

Back home, going through your instructions.

the fdisk command gives:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005acaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   154204159    77101056   83  Linux
/dev/sda2       154206206   156301311     1047553    5  Extended
/dev/sda5       154206208   156301311     1047552   82  Linux swap / Solaris

Disk /dev/sdb: 2013 MB, 2013265920 bytes
62 heads, 62 sectors/track, 1022 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000b5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3928567     1964253    c  W95 FAT32 (LBA)


So I'm going to mount sda1 as this is the one that says Linux.


When I get down to the first chroot command, the terminal line says root@ubuntu:/#
The next dpkg command gives 

```
No command 'dkpg' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dkpg: command not found

```

So I've tried it with what Ubuntu suggests and I get:

```
root@ubuntu:/# dpkg - -configure -a
dpkg: error: unknown option -o

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
root@ubuntu:/# 

```

Can you shed any light?

Thanks!

---

### Post by interacter on 2011-10-18
update - I tried the ```
apt-get update; apt-get upgrade
``` line and got a lot of text which eventually ended in
```

Get:35 http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en [3,901 B]
Fetched 127 kB in 5s (23.5 kB/s)                                       
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# 

```Don't know if that helps...


WAIT ON THE ABOVE.  Copy/pasted the last line of the Ubuntu script from terminal and something's happening.  Lots of something, in fact.
Few erros coming up - few things can't be loaded (look like languages) but it's churning on through...
Something's going for a serious install... Haven't even used the apt get install line yet...

---

### Post by garvinrick4 on 2011-10-18
> dpkg - -configure -aYou ran wrong copy and paste is easier.
```
dpkg --configure -a
```Notice the two -- you have a space between them in post 8.

Looks like you have a good chance of working notice it says dpkg was interupted, so they were through downloading, just might get that install back off the ground.

---

### Post by garvinrick4 on 2011-10-18
> WAIT ON THE ABOVE.  Copy/pasted the last line of the Ubuntu script from  terminal and something's happening.  Lots of something, in fact.
Few erros coming up - few things can't be loaded (look like languages) but it's churning on through...Must have run the dpkg --configure -a

When it is done run the
```
apt-get update; apt-get upgrade
```then
```
dpkg --configure -a
```again.
Give it one of these also:
```
grub-install /dev/sda
``` (just to make sure boot loader in right place)
before
exit

---

### Post by interacter on 2011-10-18
Most excellent - it's working!

However... I can't get online (still have a blacklist as per this thread - [http://ubuntuforums.org/showthread.php?t=1850745&page=2](http://ubuntuforums.org/showthread.php?t=1850745&page=2) ) and it doesn't like my 2 monitors.  It shows an image and I can mouse from one to the other, but it comes up with a message on boot about can't load monitor settings plus in the system -> displays option, it only shows 1 monitor.

The most pressing issue is not being able to get online.  Should I remove the blacklist entry that was placed there in the last thread?  Will that work?

Thank you for all of your help so far - once I had got the right piece of code it seems to have worked like a dream...

---

### Post by garvinrick4 on 2011-10-18
> Most excellent - it's working!
Alright that was a 50/50 that worked out. Enjoy your Ubuntu, seems from Thread you have a Ralink
card and driver, put that in your Thread Title and a networking user will pick it up and help you out now.

---

### Post by interacter on 2011-10-19
Will do - thanks so much for your help - can't tell you how much I appreciate it!

---

