---
title: "Question before I upgrade (dual boot)"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by latenightrob on 2010-05-18
Hello and thanks in advance!

I currently am running 9.10 and win7 dual boot set up from scratch following this article from lifehaker.com [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I have read on this site many people having trouble with their respective grubs' after upgrade loosing their win7 os.  Question is how do you prevent this when upgrading?  Is there a certain pop-up during installation that has to be answered a certain way?  Reading the upgrade page/notes it just says to follow on screen instructions.  instead of upgrading would it be better to do a fresh install from the live cd?

thanks again

Rob

---

### Post by Paddy Landau on 2010-05-18
My friend upgraded from 9.10 to 10.04 without any problem whatsoever.

It seems quite random as to whether it has problems.

Make sure you do a backup first, obviously; make sure you have a working Live CD in case of problems; and find out how to restore grub in case it goes wrong.

---

### Post by darkod on 2010-05-18
If you don't have too much data and settings to put back, a clean install is always better than upgrade for any OS.

If you want to try an upgrade, the first thing would be to check if the cd works in live mode. It could show you potential problems with hardware.
The mentioned grub2 "problem" was mainly due to people being unaware what is a disk and what a partition, and basically how bootloaders work.
In the pop-up window to select where to install grub2 they selected ALL disks and ALL partitions. This is what makes windows unbootable. For example if you have only ubuntu, you will not be affected even if you do this "error".

You should tell grub2 to install on the disk you are booting from, like /dev/sda, /dev/sdb, etc. If in doubt, select all disks BUT ONLY disks, not partitions like /dev/sda5, /dev/sdb1, etc. THERE SHOULD BE NO NUMBER!!! The number specifies a partition on the disk.

---

### Post by cybrsaylr on 2010-05-18
I did a clean install on my laptop. It went smoothly with no problems at all. On the clean install I checked to save all my personal settings/files from 9.10 to 10.04 and was pleasantly surprised to see everything I wanted saved carried over to 10.04. 

Question? Is this still considered a true 'clean install'?

The only thing I had to do was tweak Flash to get it running and all was good with 10.04.

---

### Post by darkod on 2010-05-18
> **cybrsaylr said:**
> I did a clean install on my laptop. It went smoothly with no problems at all. On the clean install I checked to save all my personal settings/files from 9.10 to 10.04 and was pleasantly surprised to see everything I wanted saved carried over to 10.04. 

Question? Is this still considered a true 'clean install'?

The only thing I had to do was tweak Flash to get it running and all was good with 10.04.

I'm not some great ubuntu expert, but to be honest this is the first time I hear something like this.

Did you use Manual Partitioning method and selected to install over the same root partition but didn't tick the format box?

During clean install you would usually install over your old version, and I am usually selecting the partition to be formatted. In that case everything is gone (including future possible hiccups from the older files) but it also means there is no possibility to save the personal files too.

However, I have never tried what will happen if:

1. You do a clean install onto a new partition, not formatting the 9.10 partition. In that case it might get detected and saving of the files offered.
2. You install over the 9.10 partition but do not tick the format box. Again, this might mean the underlaying 9.10 install is detected and saving of files offered.

---

### Post by latenightrob on 2010-05-18
thanks for the info guys, going to boot from the live cd now and check it out!

---

### Post by latenightrob on 2010-05-18
well live CD didn't work, says that it didn't recognize my vid. card (nvidia geforce 9800 gtx+)  I find that weird since 9.10 had no problems?

---

### Post by darkod on 2010-05-18
I haven't tried this with the new 10.04 live cd, but while the first ubuntu splash image is shown, it seems you can hit Space to get a menu. In that menu you can then hit F6 for advanced options.

Select Safe Graphics and see how it goes. You might need to select Try Ubuntu after that, to tell it whether you want to try and install.

In case F6 just displays line of command, use the arrows keys and End to go to the end, and add nomodeset

If it boots like that into the live desktop, usually you can install but you have to do the same procedure on first boot, and once it's booted it will find available drivers on its own usually.

---

### Post by latenightrob on 2010-05-18
thanks for the reply, turns out I burned the early version (which I obviously never played with) of lucid and not the most current, burning that now and I will see where it goes, will know in a few minutes.

---

### Post by oldsoundguy on 2010-05-18
I normally do a clean install (saving the ~/home folder and all the files to a thumb drive and then bring them back to get my settings), but this time, I decided to do the on line upgrade on three computers.
Two were coming from 9.10 and one from 8.04.
The two on 9.10 went TOTALLY without an issue (other than a real upscrew with Skype that still has not been fixed)
The upgrade from LTS 8.04 to LTS 10.04 had (still has) the Skype issue .. but it also had display issues.  Turns out that the upgrade drags along the old xorg.conf file and ADDS to it .. made the file HUGE .. several pages long on a printout.  and I lost some of the optional functions on my display .. roataion using the default (editing did not fix it) and RESOLUTION SETTINGS AND ROTATION using the restricted drivers.
A member here suggested running sudo rm on the xorg file and rebooting.
Since I DID have my home folder saved .. figured out why not?
Did it an did NOT have to use the saved folder as Ubuntu "fixed itself".
BUT YMMV on using the on line upgrade .. lots DO have issues and it can be caused by things as simple as a mechanical problem in your computer to a hiccup on the web, to a problem with the mirror site.
Burn a copy from the torrents FIRST just in case you need to do that clean install and SAVE that home folder some where safe (even create a separate partition for it if need be).  This just in case you have to go to point A and start all over again.

10.04 will not disappoint once you get up and running.  It has to be the best thing yet for Ubuntu!

---

### Post by darkod on 2010-05-18
> **oldsoundguy said:**
> I normally do a clean install (saving the ~/home folder and all the files to a thumb drive and then bring them back to get my settings), but this time, I decided to do the on line upgrade on three computers.
Two were coming from 9.10 and one from 8.04.
The two on 9.10 went TOTALLY without an issue (other than a real upscrew with Skype that still has not been fixed)
The upgrade from LTS 8.04 to LTS 10.04 had (still has) the Skype issue .. but it also had display issues.  Turns out that the upgrade drags along the old xorg.conf file and ADDS to it .. made the file HUGE .. several pages long on a printout.  and I lost some of the optional functions on my display .. roataion using the default (editing did not fix it) and RESOLUTION SETTINGS AND ROTATION using the restricted drivers.
A member here suggested running sudo rm on the xorg file and rebooting.
Since I DID have my home folder saved .. figured out why not?
Did it an did NOT have to use the saved folder as Ubuntu "fixed itself".
BUT YMMV on using the on line upgrade .. lots DO have issues and it can be caused by things as simple as a mechanical problem in your computer to a hiccup on the web, to a problem with the mirror site.
Burn a copy from the torrents FIRST just in case you need to do that clean install and SAVE that home folder some where safe (even create a separate partition for it if need be).  This just in case you have to go to point A and start all over again.

10.04 will not disappoint once you get up and running.  It has to be the best thing yet for Ubuntu!

+1 Very nice said, all of it.

---

### Post by cybrsaylr on 2010-05-18
> **darkod said:**
> I'm not some great ubuntu expert, but to be honest this is the first time I hear something like this.

Did you use Manual Partitioning method and selected to install over the same root partition but didn't tick the format box?

During clean install you would usually install over your old version, and I am usually selecting the partition to be formatted. In that case everything is gone (including future possible hiccups from the older files) but it also means there is no possibility to save the personal files too.

However, I have never tried what will happen if:

1. You do a clean install onto a new partition, not formatting the 9.10 partition. In that case it might get detected and saving of the files offered.
2. You install over the 9.10 partition but do not tick the format box. Again, this might mean the underlaying 9.10 install is detected and saving of files offered.
This is the first time I tried an install this way.

I did a clean 10.04 install on the same partition 9.10 was on.
I didn't check the format box.
This is why I asked if it was a true 'clean install'?
GRUB still shows all the old kernels on startup from Linux 2.6.31-14 generic up to the latest Linux 2.6.32-22-generic.
There are 16 lines of them listed on GNU GRUB on boot-up.

When the 10.04 Live-CD asked if I wanted to save settings/files from Vista or Ubuntu 9.10, I checked the 9.10 box and during the install it looked like it was copying over 9.10 files to 10.04.

---

### Post by oldsoundguy on 2010-05-18
ASSUMPTION HERE, but seeing as you have the old kernels, it  may have gone as an update!  Did NOT know that was possible.
For grins, open up the editor sudo nano /etc/X11/xorg.conf and see just how big THAT file is.  The clean 10.04 will be blank. The upgrade will have entries, provided you have not REMOVED the file as I have done.

---

### Post by cybrsaylr on 2010-05-18
> **oldsoundguy said:**
> 
For grins, open up the editor sudo nano /etc/X11/xorg.conf and see just how big THAT file is.  The clean 10.04 will be blank. The upgrade will have entries, provided you have not REMOVED the file as I have done.

I never opened that up before.
How do you do it, so I can get a look?

---

### Post by oldsoundguy on 2010-05-18
> **cybrsaylr said:**
> I never opened that up before.
How do you do it, so I can get a look?

sorry .. forget to keep it simple some times. 

Open terminal under applications> accessories. 
Cut and paste this into there:

sudo nano /etc/X11/xorg.conf

enter your password hit enter

an EDITABLE screen will come up with the contents of the file if there is anything there.

DO NOT EDIT .. this is for someone that knows what they are doing and is willing to pay the consequences if they screw it up!

after you view the contents (using the arrow keys), hit ctrl>x to exit the editor.

Then type in exit at the prompt and hit enter.

---

### Post by Paddy Landau on 2010-05-18
> **oldsoundguy said:**
> ASSUMPTION HERE, but seeing as you have the old kernels, it  may have gone as an update!
He did a clean install over a partition that already had data.

Thus, after it was installed, his old /home directory was still there, as were the old kernels.

Presumably Grub picked up the old kernels as well the new.

From a practical point of view, it would be much the same as doing a fresh install on a formatted partition, then replacing the new /home with a backup of the old /home; that's why all the settings were retained.

But, quite possibly, Synaptic is blissfully unaware of the old kernels and any old programs that previously had been installed. If I'm right, they will remain on the disk until such a time as the disk is reformatted. It's not a problem, of course, unless you are tight on space.

---

### Post by cybrsaylr on 2010-05-18
> **oldsoundguy said:**
> 
For grins, open up the editor sudo nano /etc/X11/xorg.conf and see just how big THAT file is.  The clean 10.04 will be blank. The upgrade will have entries, provided you have not REMOVED the file as I have done.

OK.
Figured it out. Opened it up and it is blank!

---

### Post by cybrsaylr on 2010-05-18
> **Paddy Landau said:**
> He did a clean install over a partition that already had data.

Thus, after it was installed, his old /home directory was still there, as were the old kernels.


But, quite possibly, Synaptic is blissfully unaware of the old kernels and any old programs that previously had been installed. If I'm right, they will remain on the disk until such a time as the disk is reformatted. It's not a problem, of course, unless you are tight on space.

This is what happened.

All the old programs put in on 9.10 were retained and carried over to 10.04.
This pleased me the most since I had added programs and modified 9.10 several times and discovered I did not have to do it all over again as I had in the past when doing a clean install up to the next version.

PS: Correction on the above posting. 
Just rechecked my laptop and all the programs I had added to 9.10 did not carry over to 10.04. I will have to reinstall them over again.

---

