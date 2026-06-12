---
title: "Broken Packages after upgrade to Edgy from Dapper"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by keithk50 on 2007-04-21
Hi folks,   I could do with some help with this one.   Upgraded to Edgy from Dapper and after several hours of nervous tension ended up with an error message saying that my system may be unstable.
After restarting the system it turned out I had 12 broken packages.   Managed to fix 11 of them but Samba remains broken.   Using "sudo apt-get upgrade -f" I got the following output:

rmat/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
(Reading database ... 111780 files and directories currently installed.)
Preparing to replace tzdata 2007b-0ubuntu0.6.10 (using .../tzdata_2007e-0ubuntu0.6.10_all.deb) ...
Unpacking replacement tzdata ...
Preparing to replace samba 3.0.22-1ubuntu3.2 (using .../samba_3.0.22-1ubuntu4.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
keith@keith-laptop:~$ 

I have tried everything to fix this, even tried to remove Samba then re-install.   No joy. At present the Sotware Update Manager returns the following message:
"Software index is broken. It is impossible to install or remove any sofware.   Please use the PackageManager Synaptic or use sudo apt-get install -f in a terminal to fix this issue at first.

Can anyone help with this or does it mean a re-install?   As a new user it has took a lot of hours to get Dapper working just as I want it but if it means a clean install then thats life.   At present I am running Edgy but unable to get any updates or software via the Software update Manager.   Thanks for reading.

---

### Post by keithk50 on 2007-04-21
Anyone?

---

### Post by funkythumb on 2007-04-29
This is not a reply as much as it is an additional plea for help. I had the EXACT same thing happen to my laptop when doing the dist-upgrade from Dapper to Edgy. Have tried everything that I can, but to no avail.

Thinking about using the recommended CD Alt install method to upgrade from Edgy to Fiesty, hoping that the Software Index problem is corrected. The only reason I haven't wiped out the system with a fresh install is that this laptop runs a raid server with 4 - 80GB striped drives. I'm only a year or so into using Linux on the side, so I'm still a bit of a novice and fearful of losing the 300+ GB of data...

Can anyone offer any help to this problem?

---

### Post by webramp on 2007-05-29
I had a similar problem while upgrading and got the following message:
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6.2_i386.deb) ...
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package nessusclient
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb


To fix this i ran dpkg -r nessusclient 
After i did this the apt-get -f install worked.

---

### Post by keithk50 on 2007-06-04
Hi Webramp,   Thanks for your post.   I did a complete re-install in the end after many hours of fruitless repair work to get the system fixed.   I am glad to hear that you were able to get your system fixed.   Its all good fun in the end eh!!!   Thanks again.

---

