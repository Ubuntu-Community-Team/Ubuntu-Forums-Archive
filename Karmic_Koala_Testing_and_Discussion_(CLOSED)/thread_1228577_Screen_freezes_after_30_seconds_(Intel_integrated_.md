---
title: "Screen freezes after 30 seconds (Intel integrated Chipset)- mouse ok"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-08-01
Using Alpha 3, after booting the livecd, the screen freezes after about 30 seconds. I have an integrated Intel chipset. 

I'm current running Jaunty using the Intel fix "[Reverting the Jaunty Xorg intel driver to 2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")". Which works perfect.

 I'm assuming my problems is Intel related, as most have been of late. I tried the "nomodeset" option and several others all to no avail. I thought of trying to install Koala but of course its graphic install and fails again after around 30 seconds.

The problem is theres no way to get at the Intel driver to do a revert or change any xorg config because it freezes. I can't read any log files for same reason.

---

### Post by psyke83 on 2009-08-01
It's probably compiz causing your system to freeze. Disable it as soon as you have control of the desktop.

---

### Post by VMC on 2009-08-01
> **psyke83 said:**
> It's probably compiz causing your system to freeze. Disable it as soon as you have control of the desktop.

That was the first thing I tried. It still froze even after disabling compiz. But thanks for your reply.

---

### Post by jerrylamos on 2009-08-01
Not sure which intel integrated chipset you're using.  Try
lspci | grep VGA

On intel i830 chipset I can't get it to boot period with karmic alpha3 intel driver 2.8.0.  See launchpad bug #403037.  Last karmic that runs is Alpha2.  See [http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2) for directions on how to download and burn a CD.

On intel i845 chipset, it will boot Alpha3 in recovery mode if on grub menu I do an e and add nomodeset to the linux line, then on recovery menu root prompt do 
nano /etc/X11/xorg.conf 
and below the Identifier line add
Driver "vesa"
See launchpad bug # 406460

If there isn't any /etc/X11/xorg.conf then do 
Xorg -configure
to create one?

If this works for you, then to boot in regular mode after having made the "vesa" change then do
sudo gedit /etc/default/grub
replace splash with nomodeset
save
sudo update-grub

Good luck.  Isn't this fun.  I gather from some comments the developers "upstream" of Ubuntu, i.e. Debian and Gnome, don't test on intel video graphics pc's, or at least on not very many of them.  Intel did us a real favor by changing the way the various chips work which makes it devilish to develop a driver set to handle them all.

Jerry

---

### Post by VMC on 2009-08-01
> **jerrylamos said:**
> Not sure which intel integrated chipset you're using.  Try
lspci | grep VGA

On intel i830 chipset I can't get it to boot period with karmic alpha3 intel driver 2.8.0.  See launchpad bug #403037.  Last karmic that runs is Alpha2.  See [http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2) for directions on how to download and burn a CD.

On intel i845 chipset, it will boot Alpha3 in recovery mode if on grub menu I do an e and add nomodeset to the linux line, then on recovery menu root prompt do 
nano /etc/X11/xorg.conf 
and below the Identifier line add
Driver "vesa"
See launchpad bug # 406460

If there isn't any /etc/X11/xorg.conf then do 
Xorg -configure
to create one?

If this works for you, then to boot in regular mode after having made the "vesa" change then do
sudo gedit /etc/default/grub
replace splash with nomodeset
save
sudo update-grub

Good luck.  Isn't this fun.  I gather from some comments the developers "upstream" of Ubuntu, i.e. Debian and Gnome, don't test on intel video graphics pc's, or at least on not very many of them.  Intel did us a real favor by changing the way the various chips work which makes it devilish to develop a driver set to handle them all.

Jerry

Thank you jerry for this info ! It's a great help. The problem is I can't stay booted long enough to change anything. I have 30 seconds to work magic. While booted, Ctrl+Alt+F2 brings up console, but requires login. Maybe I can try to somehow boot to a screen size that will work. One of the kernel options I suppose.

Another problem is I can't get Koala installed because the graphic installer uses the same xorg as the live cd does and it too freezes at around 30 seconds. If I could get it installed then boot up using Jaunty and change sorg config files. I wish they included a text based installer.

Thanks again, you've been a big help. Another point which I don't fully understand.  Many users are stating they use a virtual machine and report how wonderful Koala is!? If everyone used there own hardware machine then we could have more bugs to throw at them. Using a VM as a test machine is useless.

BTW I have a 865 Intel chip-set: 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by nystire on 2009-08-01
Try installing it using the alternate install CD for Alpha 3 from here [http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/) . That way you'll have the OS installed and can then start tweaking before loading XOrg.

---

### Post by psyke83 on 2009-08-02
> **VMC said:**
> Thank you jerry for this info ! It's a great help. The problem is I can't stay booted long enough to change anything. I have 30 seconds to work magic. While booted, Ctrl+Alt+F2 brings up console, but requires login. Maybe I can try to somehow boot to a screen size that will work. One of the kernel options I suppose.

Another problem is I can't get Koala installed because the graphic installer uses the same xorg as the live cd does and it too freezes at around 30 seconds. If I could get it installed then boot up using Jaunty and change sorg config files. I wish they included a text based installer.

Thanks again, you've been a big help. Another point which I don't fully understand.  Many users are stating they use a virtual machine and report how wonderful Koala is!? If everyone used there own hardware machine then we could have more bugs to throw at them. Using a VM as a test machine is useless.

BTW I have a 865 Intel chip-set: 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Either:

Add the "nomodeset" parameter to your GRUB boot line and boot normally:

[LIST]
[*]Highlight the default Karmic boot option, press "e", add "nomodeset" just after "quiet spash". Press Ctrl+X to boot.
[/LIST]

If your system no longer freezes, edit your /etc/default/grub.conf file and run "sudo update-grub" as mentioned by another poster. This will permanently disable KMS.

Or:

Add the "nomodeset" parameter to your GRUB recovery boot line, and edit your xorg.conf via terminal:

[LIST]
[*]Do the same procedure as above, only boot into the recovery menu, and choose a root terminal.
[/LIST]

---

### Post by VMC on 2009-08-02
I was finally able to boot Koala using the livecd without it freezing up. I had to use "nomodeset" and "vga=ask" then used the mode 7. Oddly it still uses 1024x768, but doesn't freeze up. Mode 7 is 640x480.

When trying to install on hd , I go the "ubiquity stopped unexpectedly" message. I wanted to install manually, so I made room with unallocated space but the install program won't use it - or can't. I will now format it to ext4 from another program and see if I can install Koala.

Another point, I searched for quite awhile for the command-line boot options, such as nomodeset and vga=. There's a lot of info out there but nothing specifically for nomodeset. I thought I remember seeing display=1024x768 of some such option, but couldn't find anything.

I've got to keep Koala install away from trying anything Intel, until I get it installed. Then maybe the revert to the old Intel xorg driver 2.4 will work. It's the only thing working for my Jaunty install.

---

### Post by jerrylamos on 2009-08-02
> **nystire said:**
> Try installing it using the alternate install CD for Alpha 3 from here [http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/) . That way you'll have the OS installed and can then start tweaking before loading XOrg.

On one of my intel video graphics pc's I was able to install using the install menu choice from the CD Live first menu panel.  The bare install doesn't use gnome gdm so it worked.  Of course the boot then fails pending some future update to the intel driver....I keep it updated by booting in recovery mode, then with root prompt doing:

dhclient
apt-get update
apt-get dist-upgrade
reboot

in hopes that some day a workable fix will show up.  
Meanwhile I dual boot to karmic Alpha 2 which works.

Jerry

---

### Post by VMC on 2009-08-02
> **psyke83 said:**
> Either:

Add the "nomodeset" parameter to your GRUB boot line and boot normally:

[LIST]
[*]Highlight the default Karmic boot option, press "e", add "nomodeset" just after "quiet spash". Press Ctrl+X to boot.
[/LIST]

If your system no longer freezes, edit your /etc/default/grub.conf file and run "sudo update-grub" as mentioned by another poster. This will permanently disable KMS.

Or:

Add the "nomodeset" parameter to your GRUB recovery boot line, and edit your xorg.conf via terminal:

[LIST]
[*]Do the same procedure as above, only boot into the recovery menu, and choose a root terminal.
[/LIST]

I don't know what KMS stands for.

I was able to successfully install Karmic. I changed menu.lst (I'm still running Jaunty. Used it's grub menu), and added "nomodeset". that fixed the "tearing" of the screen, but I still get freeze. I haven't changed xorg.conf yet. That may fix my deep freeze issue.

The weird thing is, whild using livecd and using nomodeset" and vga=ask, I had to do a "scan" for mode. Otherwise the system would freeze. I removed the quiet and splash options. If the screen was blank during boot I knew it would freeze, but after a few "scans" and selecting mode 8 then the boot text messages would appear and it wold work. I have no idea why I had to wait or any of that other nonsense I had to do was all about.

Hopefully, when I fix xorg.conf, the installed version will boot.
Thanks for your help.

---

### Post by VMC on 2009-08-03
> **jerrylamos said:**
> Not sure which intel integrated chipset you're using.  Try
lspci | grep VGA

On intel i830 chipset I can't get it to boot period with karmic alpha3 intel driver 2.8.0.  See launchpad bug #403037.  Last karmic that runs is Alpha2.  See [http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2) for directions on how to download and burn a CD.

On intel i845 chipset, it will boot Alpha3 in recovery mode if on grub menu I do an e and add nomodeset to the linux line, then on recovery menu root prompt do 
nano /etc/X11/xorg.conf 
and below the Identifier line add
Driver "vesa"
See launchpad bug # 406460

If there isn't any /etc/X11/xorg.conf then do 
Xorg -configure
to create one?

If this works for you, then to boot in regular mode after having made the "vesa" change then do
sudo gedit /etc/default/grub
replace splash with nomodeset
save
sudo update-grub

Jerry, I am able to boot using Alpha 3. I tried your suggestions. I didn't have a xorg.conf file so I created one and made the changes. Still freezes after 30 seconds. I'm out of options now. If I only knew what happens after 30 seconds, maybe then I would know what's happening. Apparently not all the processes are up until 30+ seconds.

---

### Post by VMC on 2009-08-03
It now works!

Thanks to all. Jerry thanks to you as was able to update my system under recovery mode. I never had to do that before. Here's what I had to do.

(1) dhclient

(apt-get dist-upgrade, is hugh 181mb. That's my next step)
Addad to sources.list:
deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79

(2) sudo apt-get install xserver-xorg-video-intel-2.4
(3) apt-get update

Unfortunately I had to revert back to intel2.4. This is a strange one. Under Jaunty I only needed this in order to use video features. Jaunty didn't freeze before reverting. Koala froze before reverting back.

I have an older Intel i865 chip-set. Not sure if it will ever work outside of 2.4. I tried all the instructions. The "alternate method and this one: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Nothing worked except reverting to 2.4

---

### Post by raffen on 2009-09-11
I recently installed karmic koala and had similar screen freeze problems on a Intel 82865G chipset. The issues seem to be resolved by reverting back to xserver-xorg-video-intel-2.4 as described in the link below.  

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

