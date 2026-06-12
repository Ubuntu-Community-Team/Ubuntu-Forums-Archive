---
title: "Cant Install 7.1? Help Please"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by climburr on 2008-01-03
Alright, I partitioned my hard drive and made drive U:/ formatted ntfs. I go to boot from the ubuntu disc and it comes up with the screen that says run and install etc. When I hit enter to select the first option (install) it loads, but after waiting for all the loading and all, I just end up viewing the screen that says :
Starting deferred execution scheduler atd     [OK]
starting periodic command scheduler crond    [OK]
Checking battery state...                               [OK]
Running local boot scripts (/etc/rc.local)        [OK]
_

And then it goes no further no matter how long I wait. Can any one help me please? I really want to spread and use ubuntu!
Thanks!

---

### Post by jan quark on 2008-01-04
ubuntu uses the file format ext3

why did you formated your U drive ( suppose for Ubuntu) into ntfs?

try the alternate CD. it solves many problems which yo may encounter during the Live CD installation.

the alternate cd is a text only installation, but have no fear its simple and more stable than the Live cd

---

### Post by perixx on 2008-01-04
maybe look here, if this applies to your problem:
[http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time]("http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time")
I've also encountered an issue with the live-CD for some weird reason activating the ANALOG/2nd video out of my graphics card at boot-up, instead of the digital out - or the switching of connectors during operation while graphics the mode is changed. 

I also have this problem under XP when loggin in, so it's maybe related to ATI cards/drivers...

did you try to switch between virtual terminal and X-server with CTRL+ALT+F1, respectively +F7?
If you can't open the X-server (graphical login) automatically, I'd try to use the first combination, opening a virtual terminal
and using either one of those commands:
```
startx
sudo /etc/init.d/gdm restart
```

another possibility: in the file /boot/grub/menu.lst, the command
```
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/[partition] ro **[COLOR="Blue"]quiet splash[/COLOR]**
```
is missing the coloured options; you can alter this by going into the virtual terminal and do 
```
sudo nano /boot/grub/menu.lst
```
then alter the command as needed and save+quit with CTRL+X.

perixx

---

### Post by c0met on 2008-01-04
This below link also has some great information regarding installing Linux systems.

[INDENT][[COLOR="Navy"]**http://users.bigpond.net.au/hermanzone/**[/COLOR]]("http://users.bigpond.net.au/hermanzone/")[/INDENT]

---

### Post by climburr on 2008-01-04
I didnt know not to format ntfs, how can i change that? Anyway, I cant even get to the desktop. Maybe its a problem with the 8800gt video card? How do i use or where do i download the alternate cd? Also, when do i press the ctrl shift F1 or the combination to open up the terminal you mentioned. Thanks for the replies!

---

### Post by perixx on 2008-01-05
oh, sorry - I didn't get that you've formatted your UBUNTU-partition with NTFS... the former posters are right, that won't work!

Use a Linux-compliant filesystem for Ubuntu: ext2/3, reiserfs, jfs or the likes. I used ext3. 
Simply re-install your Ubuntu from the live-CD. If it doesn't work in the first place, re-partition your drive to your needs (but be careful not to delete and partition the wrong (internal) drives!!) with > Applications > System > 'Gparted'.

If you like to use the whole disk for Ubuntu, choose 'use all of disk' in the installation menu 
or use Gparted and delete all other partitions and create a primary (ext3) partition, using all of the space except 2 GB's, and a second partition (linux-swap) of that size. 
Apply. 
Set main partition active (rightclick > set boot flag).
Install manually > create mountpoint '/' (root) on the main partition and 'swap' in swap > install Grub to MBR (hd0) > go.

perixx

---

### Post by climburr on 2008-01-06
The whole problem is though that I can't get to the desktop, so i can't use gparted or anything.

---

### Post by climburr on 2008-01-06
Also, it is ntfs, i made a mistake.

---

### Post by perixx on 2008-01-07
Allright, 
you either may have a corrupt Image - and try to re-download and re-burn your CD, or maybe have to fiddle a bit with the boot-options; when the boot-menu of your live-CD shows up, you can select to add / remove options with which Ubuntu will boot up (some F-key, don't know which one atm.)...

You could try those:
acpi=off
acpi=force
vga=normal
or the 'vesa' option, if availible...

Maybe someone else has more ideas.

perixx

---

### Post by climburr on 2008-01-07
I know the ISO isnt corrupt because i've booted from the disc on different computers. So when I get to the first page where it gives me a list of options like start and instal, i should press the F-key associated with options, and type the commands you gave me and hopefully it'll get me to the desktop? 
I've heard there may be some compatiblility issues with 8800gt graphcis cards.
Do you recommend using the alternate cd installation?
Thanks a ton!

---

### Post by climburr on 2008-01-07
I also have a disc Ubuntu sent me, which I am using.

---

### Post by perixx on 2008-01-09
Hello climburr!

I cannot speak for the 8800GTS, I've got no experience with that card (lack the money =]). Anyway, regarding the first question, yes, generally you can use (I think it was F6 / other boot options) the boot feature to display a line which you can just navigate and edit with the cursor (leftmost edge). Perhaps you give it a try... Also, you might trying to switch off the 'ACPI' function in the BIOS, but I'd recommend using the boot options first. Btw., haven't used the 'alterndate install CD' yet, but heard of it being a good problem-solver.

perixx

---

