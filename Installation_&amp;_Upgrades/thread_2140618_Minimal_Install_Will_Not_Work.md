---
title: "Minimal Install Will Not Work"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by Crucias on 2013-04-30
Howdy,

I downloaded the minimal install ISO with the intention of command line installing Ubuntu onto my Asus eeePC that has 2GB of RAM and 4GB of SSD. I can use the iso fine and dandy on VirtualBox, but when I hit "Command-line install" on the eee it spins up the external disk drive and then just hangs. I see the menu displayed perfectly, with Command-line install highlighted. I also tried with liveCD, same result

Anyone got any suggestions?

---

### Post by fantab on 2013-04-30
Installing on 4Gb SSD is not a good idea. You will need more space eventually, even if you go with the minimal install. You can, but you will run out of space quickly when you start installing other software.

Boot into your BIOS and see if UEFI is enabled, then check to what mode is SATA set to: IDE, RAID or AHCI. Then report back. Also check if there is INTEL SRT enabled and report back.

---

### Post by dino99 on 2013-04-30
Choosing a hardware compatible  distro is important: [http://www.leeenux-linux.com/](http://www.leeenux-linux.com/)

---

### Post by Crucias on 2013-04-30
Thanks for swift reply,

This device is 5 years old and quite simple. I only want VLC, Chrome and OpenOffice on it anyway - it's to be a dire emergency PC. In BIOS it has very few options; on "Advanced" tab it has the following:
[LIST]
[*]IDE Configuration
[LIST]
[*]IDE Master = SSD
[*]IDE Slave = None
[/LIST]

[*]Onboard Devices Configuration
[LIST]
[*]All enabled
[/LIST]

[*]OS Installation
[LIST]
[*]Set to "Start"
[/LIST]
[/LIST]

The only other options refer to boot priority and time. I should note that LiveCDs work though they throw a fit about minimum disk space. Persistent mode functions well off liveUSB

PC Specs: [http://www.umpcportal.com/products/ASUS/eee%20pc%20701](http://www.umpcportal.com/products/ASUS/eee%20pc%20701)

------------------

@Dino 

They charge for that, being unemployed I am not keen on the idea. Also the LiveCDs work just fine, it's the install that seems to be buggered.

---

### Post by dino99 on 2013-04-30
also you can glance at easypeasy  [http://distrowatch.com/index.php?distribution=easypeasy&release=all&month=all&year=all](http://distrowatch.com/index.php?distribution=easypeasy&release=all&month=all&year=all)

and possibly: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Crucias on 2013-04-30
Apparently I can install Lubuntu in a similar manner as to how they did it in this thread ([http://ubuntuforums.org/showthread.php?t=1975462](http://ubuntuforums.org/showthread.php?t=1975462)) but I cannot find the file, anyone know where minimum size is specified for the installer?

@Dino - I checked out the distro and it's based on mint for my device, not Ubuntu. I am trying to find a solution which does not involve me straying off Ubuntu. However, thank you for your replies

---

### Post by dino99 on 2013-04-30
dont worry, mint is based on ubuntu too  :P  which itself is a debian flavor  :mad: and all this is opened source  :guitar:

---

### Post by Crucias on 2013-04-30
Still costs $10 to download sadly, still I appreciate the input

---

### Post by ajgreeny on 2013-04-30
There is no compulsion to make a payment to get the .iso files, it is just a suggestion.  Go to the link, bottom left and you can skip the payment.

---

### Post by Crucias on 2013-04-30
I cannot see any download links other than the Paypal "Buynow" button. Bottom left of the screen says "Terms of Service" then a lot of blank space (Chrome, Firefox and Internet Explorer - the latter two without addons etc). 

I figured out how to bypass the minimum hard drive requirement, so it's installing now - here's hoping!

---

### Post by ajgreeny on 2013-04-30
My apologies!  I thought you were speaking about the suggested payment for Ubuntu, not Leeenux.

Note to self; "I must read more carefully."

---

### Post by Crucias on 2013-04-30
Haha all good, thank you for your reply regardless.

Just to note, my workaround worked and I now have a full Lubuntu on this eeePC with 1.5 GB of space left.

---

