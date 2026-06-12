---
title: "Ubuntu crashing in Virtual PC and typing speed issues."
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by tomnd on 2007-04-10
hi there,
i am a linux noob and have two main problems that make it very difficult (if impossible) to do anything. 

I have Ubuntu 6.10 (updated to 6.11)  and i am running it from MS Virtual PC 2004 (the problem?)

1. Ubuntu crashes within 2 mins of booting up, no matter what program i am using. I have not installed anything extra from the normal install. 

2. Typing speeds up invariably. So i will be typing a password or a command and it will produce 6 s's or n's etc. This really makes it difficult to type the password in the terminal when it doesn't show the number of characters entered.

Anyone had these problems or know of a way to sort them out.

My computer is: AMDx2 
                     1gb ram (256mb in ubuntu)  
                     win xp.

---

### Post by justsee on 2007-04-11
EDIT: This is the link you want to read [http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

Hey you've got the same problem as me - double-clock speed problem in AMD 64 chips. I went through this long arduous process trying to get VMWARE to work correctly, set up the correct arguments for the kernel, and now the latest update has wiped those settings! :-(

Basically what you may need to do is press delete when your pc boots up, go in and disable the power management functions (ACPI stuff), and when you boot into ubuntu, you'll have to edit the config file for grub at /boot/grub/menu.lst. Each kernel option is listed there and you'll have to try out adding parameters like noapci pci=noapic noapcitimer  to the line starting with kernel (add it in amongst the other parameters like splash etc)

I started this discovery here [http://www.vmware.com/community/message.jspa?messageID=231968](http://www.vmware.com/community/message.jspa?messageID=231968) which lists links to bugs regarding AMD 64 support. I'm no guru, so you'll have to follow the threads you find via Google, but there's also a bunch of posts on the forums here regarding this issue, for instance
[http://ubuntuforums.org/showthread.php?t=75708](http://ubuntuforums.org/showthread.php?t=75708)

Hope this helps a little bit, you're not alone!:
[http://www.google.co.uk/search?q=amd+64+clock+speed+bug+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.uk/search?q=amd+64+clock+speed+bug+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

