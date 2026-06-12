---
title: "Installation Error"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by scargi on 2016-10-20
Hi all,

I'm getting an error when trying to install the latest Ubuntu desktop onto my PC. I'm installing through DVD (custom burnt), I've tested the disk and it came back with no errors, I'm guessing I might need to configure my BIOS or something, this is the first time installing linux so not sure where to start.

Error pic and others: [http://m.imgur.com/a/dQwfz](http://m.imgur.com/a/dQwfz)

Machine specs:
Gigabyte Z170XP-SLI
Intel i5 6600
Nvidia GTX 960
16gb DDR4
SSD

My Solution:
I managed to get this working eventually, as Bashing-om mentions below, it's probably because I have a GTX 960 (modern GPU).
To get this working, i added nomodeset into the boot settings file, more specifically.
When i got the GNU boot menu, i arrowed down to Install Ubuntu, pressed e, and where it stated "quiet splash ---", I adjusted it to "quiet splash nomodeset ---". Then hit F10 to boot.
This has to be done every time you boot either to install or boot to use the OS until you install the correct gfx drivers (or so i believe, i will update once successful with that too.)

---

### Post by Bashing-om on 2016-10-20
scargi; Hello;

As you have a recent Nvidia graphic's card / 
> 
Nvidia GTX 960

it may be presumed that there is no driver available in the installer.
Try the "nomeset" boot parameter:
See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter.
Loading the fall back graphic's driver .. and once installed you can then install an appropriate driver .

[INDENT][INDENT]you can do this
[/INDENT][/INDENT]

---

### Post by scargi on 2016-10-27
Thanks for your response, Although the link itself didn't initially solve my issue it was sent down the correct path that ended up doing so.

I'll post my solution into my initial post in case anyone in the future comes across it...

---

### Post by Bucky Ball on 2016-10-27
The driver should be right there in Additional Drivers. Go there and install it. Make sure the Canonical Partners repo is enabled in Software and Updates first and update first.

That's it. You shouldn't need to be diddling about outside the repository and may be making this more difficult than it needs to be. I have the GTX 970 running perfectly with driver from Additional Drivers and that's newer.

Install the driver and you won't need nomodeset. If you do need that option, it doesn't need to be done everytime. You add it to the /etc/default/grub file, but ask here first before changing anything in there if you need to.

PS: Please don't do as you did and back-post to your first thread. Confusing and no-one knows where you're up to. Keep it logical and chronological thanks. New post, not adding to the old one. Won't do your chances of support any good doing it backwards. 

I suggest you post a post now stating exactly where you are up to after you have installed the driver in Additional Drivers as outlined and rebooted *without* nomodeset. :)

---

