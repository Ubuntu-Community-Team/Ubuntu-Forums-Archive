---
title: "Decompilation and disassembly prohibited.."
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by Magnus¤4 on 2011-04-19
Hi!

I have bought a netbook (HP mini 210) and am keen on installing 11.04 on it. Right now its running win 7 and been spending some time to clear up all the junk from HP, including deleting the HP tools partition and Recovery partition, now I want to install ubuntu as dualboot with win. have done this before on my previous computer so I am a little bit familiar with the procedure. This time though, I cannot make my netbook accept the install-USB that I have created. i can choose to boot from the USB when I enter bios but then this message comes up: 

Intel(r)PineView PCI Accelerated SVGA BIOS
Build Number...
Decompilation or Disassembly Prohibited
Copyright...

which is pretty much the same problem as this guy had -

[http://ubuntuforums.org/showthread.php?t=1598031](http://ubuntuforums.org/showthread.php?t=1598031)

He got it sorted out by using Unetbootin, but this, unfortunately, didnt work for me. I have tried both Unetbootin and Universal USB installer but I get the same message all the time.. so I followed the Unetbootin instructions on how to do a "frugal" install, but Unetbootin wouldnt recognize my new partition.(?)

So, maybe this isnt really a ubuntu problem cause I cant even reach the point of starting the usb, but I dont now what to do, and would very much appreciate any help....

thanks!

---

### Post by Joe of loath on 2011-04-19
Looks like a BIOS problem, it seems to be freezing before booting the USB.

---

### Post by Magnus¤4 on 2011-04-20
Tried YUMI Multiboot USB creator and it worked this time :)

thanks anyway!

---

### Post by ExportedThought on 2012-07-27
Hey this may be a little late, but i have an Acer Aspire One 722 that had the same exact problem and I was able to solve it by using the usb creator used with Jolicloud and it worked.  I have been working under the assumption that its the new hybrid operating system disk images that caused the problem. Hope this helps someone out.

---

