---
title: "Uncompression Error RAM OK"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by ~zoey~ on 2014-03-26
My husband's computer runs Windows XP and I want to switch him to linux.  I booted ubuntu, kbuntu and linux mint, all of which booted fine, but none of the live cd's could connect to the internet.  The ethernet card was not linux friendly, so I replaced it with a netgear pci ethernet card that is.  I also replaced a case fan, which shouldn't have changed anything.  When I got everything hooked up again, XP boots fine, but none of the linux cd's that booted before I opened the case will boot.  The message is "uncompression error system halted".  I googled for information and pretty much all of the answers are about bad RAM, but Windows shows the RAM as fine. His PC has an Intel DG33TL board, Intel Core Duo CPU and 2 Gb RAM.  I'm not very linux savy, although I have run it for a few years.  This is driving me nuts, because I don't understand why the live cd's all booted fine before the card change, but now they show the error.  I would appreciate any and all suggestions.
               Thank You

---

### Post by SuperFreak on 2014-03-26
Did you try this [http://www.cnet.com/how-to/test-your-ram-with-windows-memory-diagnostic-tool/]("http://www.cnet.com/how-to/test-your-ram-with-windows-memory-diagnostic-tool/")? or are you assuming RAM is OK because XP works?

This may be a more thorough test but needs to run for several hours[http://pcsupport.about.com/od/toolsofthetrade/gr/memtest86.htm]("http://pcsupport.about.com/od/toolsofthetrade/gr/memtest86.htm")

Running Boot Repair is option suggested for your problem [HERE]("http://askubuntu.com/questions/207548/in-trying-to-repair-grub-i-get-an-uncompression-error-system-halted-notice")

---

### Post by ~zoey~ on 2014-03-26
[QUOTE=SuperFreak;12969127]Did you try this [http://www.cnet.com/how-to/test-your-ram-with-windows-memory-diagnostic-tool/]("http://www.cnet.com/how-to/test-your-ram-with-windows-memory-diagnostic-tool/")? or are you assuming RAM is OK because XP works?

I thought that it was probably OK because XP boots OK.  I tried to follow the directions in the above link.  It says "open the start menu and type"  The only place to type in the start menu that I know about is run and when I tried that I got the message that Windows can't find mdsched.exe.  I appreciate your fast reply and I will try the other links.  Whoops, just checked out the memtest link.  I know how to burn an ISO, but the computer won't boot from one anymore.
                     Thank You

---

### Post by ubfan1 on 2014-03-27
You can try to create a usb live media instead of a CD, or try cleaning the CD drive.  Might just be really dirty, and moving the unit around shook things up.  Try to reseat the memory sticks, and make sure nothing is pressing against them (like a cable).

---

### Post by ~zoey~ on 2014-03-27
> **ubfan1 said:**
> You can try to create a usb live media instead of a CD, or try cleaning the CD drive.  Might just be really dirty, and moving the unit around shook things up.  Try to reseat the memory sticks, and make sure nothing is pressing against them (like a cable).

Thank you so much!  A cable was pushing on the RAM, and maybe that was it because XP is gone and linux is installed.  Now I have to figure out how to get his canon printer/copier to work.

---

