---
title: "failed usb installation"
date: 2014-03-13
forum: Installation &amp; Upgrades
---

### Post by jim_smith2 on 2014-03-13
I have a system with a usb flash drive on which I attempted an install  of both Ubuntu 12.04.4 Server and then with a desktop install of Debian  7.4 64 bit.

the ubuntu install went fine until the second reboot  after installation.  I edited the /etc/network/interfaces file to put in  a static IP and rebooted.  As ubuntu does sometimes, it lost its mind  and did the "busybox" thing and said among other things, that it could  not find various lvms such as /boot, and others.

I then tried the  debian install and the same thing happened, except that debian just  failed to an (initramfs) prompt after first complaining about the same  problem, not being able to find /root, /boot, and other lvms.  Again,  this was the second reboot after the install.

On both installs,  after rebooting from the initial installation, using the keyboard on the  installation system, I did the usual update and upgrade processs just  to make sure everything was working and up-to-date.  Both systems did  this find, and then I rebooted.  Things again were fine, so I did a  remote login over ssh to the system and logged in just fine in both  cases.  Then I edited the /etc/network/interfaces config file on both  machines to use a static IP address.  Then I rebooted once more.   That  is when the trouble hit as described above.  

forgot to mention,  both installed had issues where they tried to put grub on the hda  instead of the sda (usb flash drive)  don't know it that is part of the  problem or not.  I'm about to pull the plug and reboot with just the USB  drive in the computer.  If that succeeds i'll edit.

Please give  me some pointers on what is wrong.  I am attempting to setup a media  server which boots from usb flash drive and has a raid 5 array of 3 2tb  drives giving me 4tb of useful storage with 2tb parity.  

help!

Best Regards,
Jim Smith
On the banks of the Suwannee River in White Springs, Florida, USA

---

