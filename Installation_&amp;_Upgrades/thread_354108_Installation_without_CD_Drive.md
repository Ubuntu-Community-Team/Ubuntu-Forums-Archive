---
title: "Installation without CD Drive"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by seb706 on 2007-02-05
Hi,

Is there any way to perform a network (ftp) installation of Ubuntu 6.10 on my IBM T23 laptop without the use of any cds?

Thanks,

Seb

---

### Post by logos34 on 2007-02-05
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

---

### Post by seb706 on 2007-02-06
Thanks for the reply, but is their a slightly easier method geared towards novices?  E.g. is there a bootable diskette which lets you enter ftp details and then loads the installer automatically?

---

### Post by pyromidget on 2007-02-06
Do you have a windows installation already the laptop?

If so, you can use this:

[http://downloads.sourceforge.net/instlux/instluxNETUbuntu6_06english.exe?modtime=1150144115&big_mirror=0](http://downloads.sourceforge.net/instlux/instluxNETUbuntu6_06english.exe?modtime=1150144115&big_mirror=0)

run it within wndows, and it will add an ubuntu 6.06 installation option to the ntldr. once installed, just dist-upgrade to 6.10

Hope this helps.

---

### Post by seb706 on 2007-02-06
Unfortunately I dont have windows installed on the laptop (it came without an OS), so I was wondering if there is an equivalent to the suse 'mini.iso' which can be copied to a USB drive?

---

### Post by logos34 on 2007-02-06
Here are a couple more links that seem a bit more accessible:
[http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/)
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

Or if there is a windows pc on your lan, there's this method:
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

> so I was wondering if there is an equivalent to the suse 'mini.iso' which can be copied to a USB drive?

You could give this a shot:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by seb706 on 2007-02-07
Thanks for the help - problem solved!

---

