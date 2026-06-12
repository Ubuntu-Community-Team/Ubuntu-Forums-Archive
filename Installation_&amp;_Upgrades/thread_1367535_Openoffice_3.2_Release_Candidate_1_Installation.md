---
title: "Openoffice 3.2 Release Candidate 1 Installation"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by scouser73 on 2009-12-29
Firstly, go to the OpenOffice website: [http://download.openoffice.org/all_rc.html#untested-full](http://download.openoffice.org/all_rc.html#untested-full) and download the **Linux .deb** file.

**1** - Once you have done that, extract the .deb file, 

> **OOo_3.2_LinuxIntel_install_en-US_deb.tar.gz** 

Then you'll see a file called OOO320_m8_native_packed-1_en-US.9472

**2** - You can remove the existing version of OpenOffice if you wish with this command: 

> **sudo apt-get remove openoffice*.***

**3** - Copy and paste OOO320_m8_native_packed-1_en-US.9472 onto the desktop then open Terminal and paste this command: 

> **sudo dpkg -i ~/Desktop/OOO320_m8_native_packed-1_en-US.9472/DEBS/*.deb**

**4** - Then paste this command: 

> **sudo dpkg -i ~/Desktop/OOO320_m8_native_packed-1_en-US.9472/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb**

Once you've done that you'll find OpenOffice 3.2 in Office.

---

### Post by phillw on 2009-12-29
Hi,

Just be aware that there are a couple of outstanding bug-fixes for the RC & it may well be a that another RC appears.

[http://ubuntuforums.org/showthread.php?t=1366654](http://ubuntuforums.org/showthread.php?t=1366654)

Has a discussion on it.

Regards,

Phill.

---

### Post by scouser73 on 2009-12-29
Thanks Phill

---

### Post by anselm on 2009-12-29
Will this work on 8.04LTS??

---

### Post by scouser73 on 2009-12-29
Yes

---

### Post by mjmcomputer on 2010-04-02
I am trying to upgrade Openoffice  from 2.4 to 3.2 on Ubuntu 8.04 LTS. When I try the command: sudo dpkg -i~/Desktop/OOO320_m12_native_packed-l_en_US.9483/DEBS/*.deb dpkg returns "unknown option -~". The extracted folder is on my desktop. Any help is appreciated.

---

### Post by Slim Odds on 2010-04-02
> **mjmcomputer said:**
> I am trying to upgrade Openoffice  from 2.4 to 3.2 on Ubuntu 8.04 LTS. When I try the command: sudo dpkg -i~/Desktop/OOO320_m12_native_packed-l_en_US.9483/DEBS/*.deb dpkg returns "unknown option -~". The extracted folder is on my desktop. Any help is appreciated.

Put a space between the "-i" and the "~"

---

### Post by mjmcomputer on 2010-04-03
Thanks, but that didn't quite work either. Got this response "dpkg: error processing ~/Desktop/OOO320_m12_native_packed-l_en-US.9483/DEBS/*.deb (--install): cannot access archive: No such file or directory"
The directory does exist on my desktop with the DEBS subdirectory full of .deb files. I tried uninstalling the older version of Open Office and reentering the command but get the same result.
Any idea why it can't seem to find the files?

---

### Post by mjmcomputer on 2010-04-03
Ok I got it to find the directory, I had an l where a 1 should have been. Now I get a different error:
/home/mark/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-base_3.2.0-12_i386.deb: line 1: syntax error near unexpected token `newline'
/home/mark/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-base_3.2.0-12_i386.deb: line 1: `!<arch>'

I checked the md5sum of the archive I downloaded and it matches so it should be good.
Any suggestions?
TIA

---

### Post by mjmcomputer on 2010-04-03
Got it! Had to redo the uninstall. In my messing around I had installed some .debs with GDebi. After removing them it installed without issue.
):P

---

### Post by Jose Catre-Vandis on 2010-04-07
Worked nicely for me with a bit of editing for the version and locales (GB)

```
sudo dpkg -i ~/Downloads/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb
```
```
sudo dpkg -i ~/Downloads/OOO320_m12_native_packed-1_en-GB.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb
```

---

