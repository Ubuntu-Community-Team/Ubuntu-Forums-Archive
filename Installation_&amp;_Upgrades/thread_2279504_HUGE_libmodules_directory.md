---
title: "HUGE /lib/modules directory"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2015-05-23
While trying to do other things, I just encountered this... not sure it's a problem, but wonder why all these files are here?

Running Xubuntu 12.04

Attempting to install/run MMA - Musical Midi Accompaniment and LinuxBand...  looking for the mma file that starts the program, so did a search for 'mma' in Krusader... 

It found over 300 hits...  all in /lib/modules.  That directory is 6.7 GiB, 47,227 directories, 245,237 files.  

1st Dir is '3.2.0-23generic', 4/23/12, and the last one is 3.2.0-83generic, 5/11/15.  This would appear to be every upgrade that has crossed my screen?

Are all these files needed?  If not, why are they kept?  If so, why does the OS allow such bloat?

Back to MMA problems!!  Thanks.  DK

---

### Post by ubfan1 on 2015-05-24
Yes, every kernel upgrade you have applied puts it modules into the directories in /lib/modules.  Take a look in /boot to see which kernels are present for booting.  I tend to remove old ones myself:
apt-cache pkgnames |fgrep 3.2.0-23
to list the packages for that kernel, then if I am satisifies that only kernel packages are listed by the somewhat chancy use of just the version number,
sudo apt-get purge `!!`
The actual package to be removed are listed, and confirmation asked.
The grub menu is rebuilt without the kernel.
Repeat as needed, I keep at least two kernels around.
There used to be a parameter in /etc/defaults/grub to control the number of kernels kept around, but that's been gone awhile.
There might be some benefit from the apt-get autoremove command, but I like to control things myself, so haven't tried that.

---

