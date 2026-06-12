---
title: "Install crash of Ubuntu 11.04 from 2gb USB stick:"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by tomot on 2011-06-07
1. the install process fails 3/4 along the orange install barometer 
2. "Installer crashed" appears in the btm. task bar
3. the Ubuntu installer tells me: **/var/log/syslogand/var/log/partman** is the location for the text file containing information about the crash.

Having found the file and having put it on my Ubuntu desktop, I now want to forward it to the Ubuntu developers. Sounds like a very simple process, but it isn't!

I Google the phrase "crash report Ubuntu"  which brings me to:  [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

I'm sure the people at the Apport are well intentioned, but I'm NOT willing to spend hours trying to understand nor read about all the problems, and how to send a crash report.

What would really help for a non techie like myself is an small application called **UbuntuCrash** into which I can drag and drop the crash file, after which I click, Send.

---

### Post by mörgæs on 2011-06-07
It is good that you want to take part in making Ubuntu better. You can post a bug report here:

[www.launchpad.net/ubuntu](www.launchpad.net/ubuntu)

---

### Post by tomot on 2011-06-10
upon reading more at this forum I see I'm not the only one having problems installing via USB stick.

I have removable HDD trays which each contain one HDD, hence I can quickly disengage any or all HDD's from the front of my computer.
I can then install any New HDD into the tray, and install Ubuntu.
By hitting F8, during the boot process I can direct from where I want to boot. The boot loader recognizes the HDD I want to install Ubuntu onto, as well as the USB I want to do the Ubuntu install from. Below is what I have discovered so far:


Ubuntu 11.04 Install wont start does not recognize 8gb USB
--------------------
8gb USB <--- Install To    
2gb USB <--- Install From 


Ubuntu 11.04 Install wont start does not recognize 8gb USB
--------------------
8gb USB <--- Install To    
CD      <--- Install From 


Ubuntu 11.04 Install fails at 75%, CRASH report issued, but no quick method by with to send it. 
--------------------
HDD     <--- Install To    
2gb USB <--- Install From 


Ubuntu 11.04 Install Works! Installed all drivers for Flash, PDF, Bookmarks from Windows Firefox, Address Book from Thunderbird 
--------------------
HDD     <--- Install To    
CD      <--- Install From 


Ubuntu 10.04 Install works! can't get Nvidia driver to display more than 1024x768 running Ubuntu from USB stick is way too slow.
--------------------
8gb USB <--- Install To    
CD      <--- Install From

I'm going to test the same above to see how a Ubuntu 10.04 install fairs.

---

