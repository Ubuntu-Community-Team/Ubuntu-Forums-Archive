---
title: "Update OpenOffice.org in kubuntu 9.10"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by efAston on 2010-02-20
Hi,

You may tell from my question that I haven't got much Linux experience, but I'm currently having a problem where OpenOffice.org won't save anything, and I'm trying to update it. I've downloaded the latest 64 bit debian installer, and when I unpack it, there's a shell script file called "update" which is set to executable. If I click on that file nothing happens (WINE seems to have associated itself with shell scripts, and nothing happens when I try and open them through Dolphin) and if I paste its name into the terminal it says 
dpkg: requested operation requires superuser privilege
If I type su and then type my password it says "su: Authentication failure". I only entered one password during the kubuntu installation process and that was the password for my user login, so that is the password I'm trying to use with su.

I think I'm missing a couple of things here, any hints?

Cheers!
Aston

---

### Post by mörgæs on 2010-02-21
What happens if you use sudo in stead of su? ```
sudo update
```

---

### Post by mörgæs on 2010-02-21
By the way, as a first attempt you could also just uninstall Open Office through Synaptic and then install it again.

---

### Post by efAston on 2010-02-22
aston@aston:~/OOO320_m12_native_packed-1_en-US.9483$ sudo update
[sudo] password for aston:
sudo: update: command not found

Re-installing using a package manager gets the menus looking a bit weird and fixes the problem where I can't save, but still won't get me to 3.2 (only 3.1).

---

### Post by mörgæs on 2010-02-22
This is expected. *buntu 9.10 includes Open Office 3.1 in the repository. 

If you want to go to 3.2 (is it really necessary?) then you have to install it by hand or try Ubuntu 10.04. It is in alpha, but pretty stable. 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I have not tried installing by hand, sorry.

---

### Post by Hagar Delest on 2010-02-22
Or try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by efAston on 2010-02-26
Well the reason I want to be able to install 3.2 is so I know how to run installation scripts, as it's not the only package that uses one. I'll try the instructions Hagar linked, thanks all.

---

### Post by jimmers on 2010-02-27
Hi efAston,
You don't state where you are situated, I am running OOo 3.2 in jaunty
Try one of these, I got them from Ubuntu-geek

  	 	 	 	 	 	  This tutorial will explain how to install latest version of openoffice in ubuntu
 You can check what is new in openoffice 3.2 from [here]("http://www.openoffice.org/dev_docs/features/3.2/")
  First go to the [OpenOffice website]("http://download.openoffice.org/other.html") and download the Linux .deb file (On your [[COLOR=#006400]_desktop_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#"))
 1 - Once you have done that, extract the .deb file,
 [INDENT]OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Run the following command from terminal or just right click select extract
 [INDENT]tar xzvf OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Then you’ll see a file called OOO320_m12_native_packed-1_en-GB.9483
 2 - You can remove the existing version of OpenOffice if you wish with this command:
 [INDENT]sudo apt-get remove openoffice*.*[/INDENT] 3 - Copy and paste OOO320_m12_native_packed-1_en-GB.9483 onto the desktop then open Terminal and paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb[/INDENT] 4 - Then paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb[/INDENT] Once you’ve done that you’ll find OpenOffice 3.2 in Office.
    	 	 	 	 	 	  This tutorial will explain how to install latest version of openoffice in ubuntu
 You can check what is new in openoffice 3.2 from [here]("http://www.openoffice.org/dev_docs/features/3.2/")
  First go to the [OpenOffice website]("http://download.openoffice.org/other.html") and download the Linux .deb file (On your [[COLOR=#006400]_desktop_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#"))
 1 - Once you have done that, extract the .deb file,
 [INDENT]OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz[/INDENT] Run the following command from terminal or just right click select extract
 [INDENT]tar xzvf OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz[/INDENT] Then you’ll see a file called OOO320_m12_native_packed-1_en-US.9483
 2 - You can remove the existing version of OpenOffice if you wish with this command:
 [INDENT]sudo apt-get remove openoffice*.*[/INDENT] 3 - Copy and paste OOO320_m12_native_packed-1_en-US.9483 onto the desktop then open Terminal and paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb[/INDENT] 4 - Then paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb[/INDENT] Once you’ve done that you’ll find OpenOffice 3.2 in Office.


Worth a try, good luck
Jimmers

---

