---
title: "Live CD installer botched bootloader"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by tim93 on 2016-05-17
I have (had) Ubuntu 15.04 running on my XPS 13 9343. Since I had to create a 16.04 LTS live CD for another project, I thought I would also boot it on my XPS and see what my install options were as I am (was) planning to do an upgrade this weekend. I booted from the CD, went to the live desktop, and opened the Install Ubuntu program. I only went as far as the options list for how to install (where it lists items like upgrade Ubuntu, install alongside, or erase disk and install). I didn't click on any of these options and quit the installer. I shut down the PC, and when I went to start the computer from the SSD, I was informed that no bootable devices were found. I know the OS on the SSD was working properly because I was running it to create the live CD just before booting the live CD.

This post isn't really requesting help, just pointing out a potential bug with the installer. Simply running through the first couple of options before selecting anything that would impact the pre-installed OS messed up my bootloader. So, I've been running in the Live desktop and manually backing up my SSD before doing the install for 16.04. Luckily, all of my files are still there (most were backed up anyway, so the most valuable files were safe regardless).

Bottom line, don't click the installer on the live CD until your current files are properly backed up or you don't care if the disk is modified. Simply opening the installer may damage your bootloader.

---

### Post by oldfred on 2016-05-17
Are you sure you did not change from/to UEFI boot instead of BIOS boot in UEFI when selecting DVD to boot?
Or in UEFI when you exited, it said set to defaults and you let it do that? It may have turned Secure boot on, and your install is normal UEFI boot?

---

### Post by tim93 on 2016-05-17
My default settings are UEFI with secure boot. I can bypass that and boot from disc by pressing F12. I checked again and these settings were correct. I've also tried booting with UEFI and no safe boot as well as legacy boot options. No bootables found in all three scenarios.

---

### Post by oldfred on 2016-05-17
Best to see details, if you cannot boot then you have to boot DVD or flash drive.
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by tim93 on 2016-05-17
[http://paste2.org/VCCsyJD8](http://paste2.org/VCCsyJD8)

(Took forever for the usr folder to back up. I was waiting until that was done.)

***UPDATE***

Ran Boot-Repair and am now back in my 15.04 install. Thank you for pointing me to those utilities. Bonehead simple to use and effective. The log from the repair is linked below. [URL="http://paste2.org/wvAJKB51"]

[/URL][http://paste2.org/wvAJKB51](http://paste2.org/wvAJKB51)

Should the installer on the Live CD do this before selecting a disk layout option (messing up the bootloader)?[URL="http://paste2.org/wvAJKB51"]
[/URL]

---

### Post by oldfred on 2016-05-18
You have a lot of kernels, best to houseclean unless doing a new clean install that will in effect houseclean everything.
You just about cannot do much with 15.04 anymore as it is expired.

 Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by tim93 on 2016-05-18
Yeah. I'm not sure how my installation became so cluttered. It was a clean install when I got the computer last June (machine originally had 14.04, which I removed and did a clean install shortly after receiving the computer). 

Now that I got everything working again, I'm going to take a drive image of the SSD, do a clean install of 16.04, and manually migrate documents and settings over. I plan on 16.04 LTS being the last OS install for quite some time (should be under maintenance for 5 years, right?).

---

### Post by oldfred on 2016-05-18
I keep old install & have extra / (root) partitions for new installs. I end up with all the 6 month releases, some now obsolete, but then use newest LTS as main working install. 
I export list of installed apps and have all data in separate /mnt/data partition so I can use all data in every install. Also makes moving from 14.04 to 16.04 easier. Found a fair amount of apps not in 16.04 when adding list from 14.04. Most not one's I really used.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

