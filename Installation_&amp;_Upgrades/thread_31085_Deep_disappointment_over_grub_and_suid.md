---
title: "Deep disappointment over grub and suid"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by Aiown on 2005-05-01
Hi all,

No offence, but do we see another predatory OS emerging? 

I have multiple systems on my SATA hard drive, and strangely whenever the MBR is overwritten the whole partition table info gets lost. I am using Symon ([http://symon.da.ru](http://symon.da.ru)) as boot and partition manager and all the partition info including the Symon code is stored on the first sector beside the MBR. On older machines if Windows overwrote the MBR I simply re-ran the Symon install and all the settings were intact, but not on this machine (Dell Dimension 8400). Whenever the MBR is overwritten everything gets lost. 

Luckily I have the settings printed on paper and I simple ented them again into Symon and everything is up and running, but it is a hassle and takes some time.

I appreciate the work and support that goes into Ubuntu Linux and I had great hopes that it would work on my system while so many other distros failed: 

*in Mandrake 10.1* I could only get a screen that flickered at 60Hz; 
in *Suse 9.2* I cound eject a CD but the system didn't unmount it first, so placing another CD on the tray resulted gibberish, and it didn't recognise the DVD burner; 
*Slackware* wouldn't install; 
*Vector Linux SOHO* couldn't install the boot loader on either the root partition or floppy
*SimplyMepis* couldn't handle the videocard, and without GUI I couldn't install it - you need to click on the install icon on the desktop;
*Yoper* installed LILO on the root partition, but when I rebooted it wasn't there,.... etc.

The only Linux system that works right now is **Frugalware** :-(

Now, of course, I tried Kubuntu as I hate Gnome - I would rather go without Linux than use Gnome.
But, I had a few major problems with it:
[B]
1. GRUB problem.[/B] The choice was not presented where the boot loader should be installed. I understand that most people don't have a clue what partitions are, but and advance install procedure would have been helpful for those who want more control.
Grub over-wrote the MBR without asking and I was left with a non-functional machine with all my other systems killed. At least a warning should have been displayed concerning the dangers, but nothing, GRUB was installed silently ***without my knowledge***. A clearly predatory approach following in the footsteps of Microsoft? It took me some time before I recovered my other partitions and was able to boot into WinXP where all my work was.

**2. The usage of SUID.** It appeared I needed a root account for certain operations, so I enabled it, but from then on I couldn't perform certain operations from KDE (like clicking on Administrator Mode in KControl and typing the password resulted in failure - I tried both my user and root passwords, none worked). 

This was the end of the story for Kubuntu on my machine, sadly, I wiped it out in great disappointment.

Suggestion: give those idiots who know a bit more about computers and Linux to use it the way they want. Certainly, there are other distros out there that may meet their needs better than Ubuntu, but at times those don't even install on new machines while Ubuntu *does* install (why the hell is that?). 

Most people I came across chose a simple password for their user accounts, and it is shared around within the family, so going the SUID way doesn't help much in the area of security. 

Please, don't misunderstand me, I am not trying to bash (K)Ubuntu (wish that distro well for the future), but these above things prevent me from using it.

---

### Post by dave9191 on 2005-05-01
My experience with (k)ubuntu is much different from yours. Ubuntu tries to make things as simple as possible for new users hence the lack of advance options. It didnt ask me if i wanted grub or where to put it, but it did detect windows and asked me if there were other OS that it needed to know about. When booting after install i had a choice of windows or ubuntu. If I was setting that up manually I would have done it just like ubuntu, so i cant complian. 

The ubunutu mind set is that having a root account is too much of a temptation for users to log in as admins and mess things around. And that using sudo is quick, convinient and simple. I always set a root password, but thats a prefrence I have.

As for the control center its an annoying bug that can be fixed by allowing root logins in the config files and clearing your kde cache. 

One of the problems with kubuntu is that they ripped out gnome and put kde in its place and as a result they missed a few settings. Its just teething problems and I can see this distro growing in popularity very fast. 

This is my distro of choice, closley followed by gentoo. But I dont have days of compiling time to spare to get that running :)

Dave

---

### Post by az on 2005-05-01
But doesn't the installer tell you that grub will overwite your MBR?  I am pretty sure that it is written at the top of your screen.  

As far as sudo and security, you should add another user, or some other users, who will not have sudo priviledges.  No, having only one user with sudo privilidges is not secure. 

You can easily add users in the system settings interface.

---

