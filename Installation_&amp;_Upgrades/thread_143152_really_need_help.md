---
title: "really need help"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by dsimpson on 2006-03-11
I have been trying to install my ubuntu cd again, and when it gets to the point where it is "installing the base system" I get an error and it will go no further. "Installing the kernel - retrieving and installing linux-386."

Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.
Check /target/var/log/bootstrap.log for the details.

I am really new at this and need help desperately. I had the system up and running but tried to reinstall over the files again and have run into a mess of problems.

---

### Post by kaptainlange on 2006-03-11
Hey there again.

I've been doing an extremely frustrating install of Ubuntu today as well.  I had the exact same error and I eventually tracked it down to a bad cd.  Hit Alt-F3 to check what error messages are being thrown up during the install.

---

### Post by dsimpson on 2006-03-11
Hi again, I get to a point where it says - "the bootstrap program exited with an error (return value 1), and can go no farther. It did load all the way to the main screen once but said there were missing files and I should reinstall.

After pressing Alt-F3, these are the error messages:

No matching phusical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
No volume groups found
reading all physical volumes, this may take awhile
selecting previously deselected package base-files
(reading database...0 files and directories currently installed)
unpacking base-files (from.../base-files_3.1.5ubuntu4_i386.deb)...
dpkg:base-passwd depends on libc6 (>=2.3.4-1); however
package libc6 is not installed.
setting base-passwd (3.5.10)...

dpkg:base files; dependency porblems, but configuring anyway as you request: 
base files depend on awk: however;
package awk is not installed.
setting up basefiles (3.1.5ubuntu4)...
/var/lib/dpke\g/info/base-files.postinst: line 18: 7869 segmentation fault
h mod $2.$1

Theres alot going on here that I don't have a clue about. I did switch cd's and am on the 3rd one now, so I doubt it is a dirty cd.
At one time I had the system installed and up and running for over a week, then the last time I tried to find help and the files were missing so I tried to reinstall and that is where my problems began.

---

### Post by dsimpson on 2006-03-12
I have tried several options, I tried to install as a server, nothing! it froze again. I did try the Livecd and it worked somewhat, although it didn't load all the files and I needed to keep pressing continue to get the gnome features active. I wasn't able to do any repairs or figure anything out from there, but at least it did eventually work. I am still unable to load the complete breezy cd and get it working, if ANYONE can please help with some suggestions, it would be greatly appreciated. I really like the OS and don't want to leave it now.

---

### Post by dsimpson on 2006-03-12
Is there anyway to reformat the hard drive so that I can work around my problem and reinstall ubuntu. I am unable to do anything and it appears there is no one out there  that has an answer for me either, so I want to wipe my HD clean and start over with a new install. Could someone help me please!!!
I am unable to load ubuntu so cannot reformat, and repartitioning hasn't done it either, and the install cd will not remove the old files and it keeps me from reinstalling ubuntu. :cry:

---

