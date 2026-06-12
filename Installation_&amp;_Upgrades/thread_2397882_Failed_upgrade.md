---
title: "Failed upgrade"
date: 2018-08-04
forum: Installation &amp; Upgrades
---

### Post by mwredt-0 on 2018-08-04
I have been running Ubuntu 16.04 on a Toshiba Laptop with 3GB system memory and a 150 GB hard drive.  I downloaded and ran the install for Ubuntu 18.04 but it will not boot into 18.04.  
First some text appears on the screen as follows:

Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu 18.04.1 LTS (18.04)
Advanced options for Ubuntu 18.04.1 LTS (18.04)

Then there are more lines of text, then the word Ubuntu with five white dots under it.  These dots turn red one by one, then start to turn red again but just stop and nothing happens, the mouse doesn't work and the keyboard will do nothing except allow a hard shut down, power off.

After I ran the install for Ubuntu 18.04 and it would do nothing, I no longer had Ubuntu 16.04 so I used an old setup disk I have with Ubuntu 12.10 and installed that so I could at least boot up.  So now I don't have 16.04 on my computer and though it appears that 18.04 is on the hard drive I cannot access it.
What do I do to fix this?

---

### Post by Bashing-om on 2018-08-04
mwredt-0; Hello -

Yukkie -

installing 12.10 is of limited value as it is End_Of_Life and has no software repository support.
Let's return to 18.04 and see what we can do.
Firstly is what results in booting the 18.04 installer in the "try ubuntu"  mode ?

If there are no issues in the "try" mode, then we prepare to install to the hard drive - again -.
verify the .iso:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
verify the copy:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
install 18.04.

If still issues we boot to terminal and see what the system has to say .

[INDENT][INDENT]where there is a will - there is a way
[/INDENT][/INDENT]

---

