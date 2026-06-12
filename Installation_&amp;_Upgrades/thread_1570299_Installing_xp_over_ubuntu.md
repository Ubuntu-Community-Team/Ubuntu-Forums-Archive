---
title: "Installing xp over ubuntu"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by scuttmuffin on 2010-09-08
I recently had to put a new hard drive in my laptop. I have an hp dv5-1000us. The hard drive i put in was a seagate 320gb sata hdd. At the time of installation I did not have a windows os disc so I just installed ubunut 10.04. I have an xp install disc. When I boot from the install disc it acts like its going to load then I get the bluescreen of death. I have done some reading on this and from what i can tell I need change my sata compatibility in my bios to ahci; but when I go into my bios to system configuration I have no option to change my drive compatibility. Can anybody help me? Where can I get the proper sata driver for my laptop?

---

### Post by dirghrabadia on 2010-09-08
Generally, XP is installed first, and then Ubuntu. 
This thread might help: [http://ubuntuforums.org/showthread.php?t=466365](http://ubuntuforums.org/showthread.php?t=466365)

---

### Post by scuttmuffin on 2010-09-08
Yea I know xp should be first...well I do now at least. If I boot the ubuntu install disk and delete my partions so all I have is free space would that let me install xp with out getting the blue screen of death? If so thats all I need to do...I jsut dont want to wipe my hdd for nothing. Thanks for the tip also...the thread did help a little.

---

### Post by dirghrabadia on 2010-09-08
I think your XP cd would allow you to wipe your entire hard drive, and do a fresh installation, without getting the blue screen of death. That would leave you with XP only.

---

### Post by scuttmuffin on 2010-09-08
Ya you would think...but thats the problem tho...it doesnt.

---

### Post by dirghrabadia on 2010-09-08
Create a Gparted Live CD/USB ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)). Boot the CD/USB by changing the boot preference (if needed), and format the hard drive with NTFS system for XP to be installed.

---

### Post by dirghrabadia on 2010-09-08
Btw, I hope you have backed up all the required data from Ubuntu.

---

