---
title: "GRUB menu items showing twice"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2013-01-19
I also have double listing of the same version showing on my Grub screen

Please see attached images.

I actually have a double Grub Customizer menu.   I would like to know how to get it back to just showing the newest OS and the other versions filed under the Previous Versions.

I did not see a fix on this thread.  Also I don't do many changes to the GC, I just to the automatic updates and this problem slipped in with one of those updates.

---

### Post by oldfred on 2013-01-19
Moved to a new thread. Old thread is almost 2 years old and grub has changed a lot.
For reference old thread:
[http://ubuntuforums.org/showthread.php?t=1767774](http://ubuntuforums.org/showthread.php?t=1767774)

Post BootInfo report so we can see details. It looks like os-prober is importing another set from somewhere. Did you copy 30_os-prober at any time? But, I do not know how new sub-menu now works.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by jlh68 on 2013-02-07
OK, I updated my netbook two days ago after a long time of not updating.  When I restarted I have the duplicate grub menu items.  This is the same situation I had with my laptop, which I posted to this thread earlier.  

This makes me believe that the **Grub Customizer application** introduces this problem.  The OS-prober is not doing this because it would not lhappen to two of my computers with in two months.

This may be an old problem but is is still NOT FIXED since I had it appear on 2013.02.05 and that is only two day ago.

So how about a fix instead of just pushing this problem around.

---

### Post by oldfred on 2013-02-07
Post this:
 cd /etc/grub.d
 ls -l

---

### Post by jlh68 on 2013-02-07
john@Nighthawk:~$ cd /etc/grub.d
john@Nighthawk:/etc/grub.d$ ls -l
total 68
-rwxr-xr-x 1 root root 6743 Sep 12 16:18 00_header
-rwxr-xr-x 1 root root 5522 Apr 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7780 Dec 10 07:20 10_linux
-rwxr-xr-x 1 root root  998 Feb  2 11:51 10_linux_proxy
-rwxr-xr-x 1 root root 6335 Apr 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root  278 Feb  2 11:51 30_os-prober_proxy
-rwxr-xr-x 1 root root 1388 Dec 10 07:20 30_uefi-firmware
-rw-r--r-- 1 root root  214 Apr 17  2012 40_custom
-rw-r--r-- 1 root root   95 Apr 17  2012 41_custom
drwxr-xr-x 2 root root 4096 May 30  2012 bin
drwxr-xr-x 2 root root 4096 Feb  2 11:51 proxifiedScripts
-rw-r--r-- 1 root root  483 Apr 17  2012 README
john@Nighthawk:/etc/grub.d$

---

### Post by jlh68 on 2013-02-07
from my netbook:

john@WiseOwl:~$ cd /etc/grub.d 
john@WiseOwl:/etc/grub.d$ ls -l 
total 64 
-rwxr-xr-x 1 root root 6743 Dec 10 07:16 00_header 
-rwxr-xr-x 1 root root 5522 Oct  1  2011 05_debian_theme 
-rwxr-xr-x 1 root root  786 Feb  4 18:56 10_linux_proxy 
-rwxr-xr-x 1 root root 6335 Apr 17  2012 20_linux_xen 
-rwxr-xr-x 1 root root 1588 May  2  2011 20_memtest86+ 
-rwxr-xr-x 1 root root 7603 Apr 17  2012 30_os-prober 
-rwxr-xr-x 1 root root 1388 Dec 10 07:16 30_uefi-firmware 
-rwxr-xr-x 1 root root  214 Oct  1  2011 40_custom 
-rwxr-xr-x 1 root root   95 Oct  1  2011 41_custom 
drwxr-xr-x 2 root root 4096 Dec 22  2011 bin 
drwxr-xr-x 2 root root 4096 Feb  4 18:56 proxifiedScripts 
-rw-r--r-- 1 root root  483 Oct  1  2011 README 
john@WiseOwl:/etc/grub.d$

---

### Post by oldfred on 2013-02-08
I do not use grub customizer. Are these folders from grub customizer and what is in them?

drwxr-xr-x 2 root root 4096 Dec 22  2011 bin 
drwxr-xr-x 2 root root 4096 Feb  4 18:56 proxifiedScripts 

And is then grub adding entries from those folders also? It may be an issue with grub customizer.

---

### Post by fantab on 2013-02-08
Yes this is an issue with Grub-Customizer... actually its got something to do with 'proxy' files in /etc/grub.d... I tried using GC in bro's machine but the grub got messed up... I was forced to uninstall GC and then grub and reinstall it.

Also I have seen this issue particularly if there is multiboot... and/or an another GRUB is present so GC, I guess reads all the OS prober files in the system and messes it up... I am not 100% sure but may indicate some pointers in resolving the issue...

More on [**grubcfg_proxy**]("https://answers.launchpad.net/grub-customizer/+faq/1355").

---

### Post by oldfred on 2013-02-08
For new users with basic systems grub customizer is a gui and seems to work.

I always do thing manually, but I started before there were the newer tools and had to learn.

If not afraid of editing a few grub files manually it is not all that difficult to maintain yourself. I turn off os_prober and add my own 40_custom. I learned a lot from many of the threads by drs305.  And I use Ranchhand's methods to simplify multiple boot as now documented by cavsfan.

       The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by fantab on 2013-02-08
Thanks oldfred... I will definitely want to learn to manually manage the Grub. I Multiboot Arch, Ubuntu LTS and Ubuntu Development Release... It will give me more control over my Grub and Grub menu in particular...

---

