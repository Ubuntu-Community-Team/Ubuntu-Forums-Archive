---
title: "No PCI after Edgy installation"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by cougar6 on 2006-11-12
Forgive the noob but here goes:
I've been following the thread at [http://www.ubuntuforums.org/showthread.php?t=297855](http://www.ubuntuforums.org/showthread.php?t=297855) because I, too, do not have a working Ethernet connection after installing 6.10.  However, this is a clean installation on a dual PIII 733 / 768MB box (slot 1 processors).  I had Vector Linux 5.1 installed but was unable to get it to recognize my second processor and when I recompiled a 2.6.18 kernel, I lost my Ethernet cards.  So, I acquiesced to a friend and downloaded / installed Ubuntu 6.10 only to see the same behavior; that is, two processors but no Ethernet.  I've tried 3 different NICs; 2 Intel Pro/100 and a 3COM card but nothing works.  So, the box boots, cat /proc/cpuinfo identifies 2 processors but lspci provides absolutely nothing.  I tried -v, -vv, and -vvv (from man lspci) and nothing.  So, I'm beginning to wonder if the issue is PCI bus and not necessarily Ethernet.  When Vector Linux was running, lspci reported:
VIA VT82C693A/694x Host Bridge
VT82C598/694x PCI
VT82C596 ISA
VT82C586A/B/VT82C686/A/B/VT823x/A/C/VT8235 IDE
Intel 82557/8/9 Ether Pro 100 Rev 8 (Both eth0 and eth1).
However, now that Ubuntu is running, lspci does not report anything at all.  Any ideas?
Cougar

---

### Post by DaveBorealis on 2006-11-12
> **cougar6 said:**
> when I recompiled a 2.6.18 kernel, I lost my Ethernet cards.

Have you tried a Dapper (6.06.1) live CD.  It runs a 2.6.15 kernel.  The Edgy issue with certain ethernet cards (or PCI bus) might be that 2.6.18 kernel.

Dave

---

### Post by cougar6 on 2006-11-12
Dave,
Thanks.  I have not tried an earlier version of Ubuntu yet.  However, I think I might have been misleading in my first post.  Here is the sequence of events:
1.  Installed Core 5 but it didn't recognize the video (Rage 128 - I know it's old but it's what I have) or the Ethernet cards (Intel Pro/100).
2.  Installed Vector Linux 5.1 (2.6.12 kernel I think) and it recognized everything except the 2nd processor.  Found a How-To online and recompiled a 2.6.18 kernel and ensured I enabled SMP.  I tried several times, each time adding more to the kernel instead of as modules (Ethernet cards and stuff) but I could never get both processors and both NICs at the same time.
3.  A buddy of mine from work kept telling me to run Ubuntu so I downloaded/burned the Live CD and installed it (slick interface by the way).  However, I couldn't get the Ethernet cards so I changed out the two Intel for a 3COM and even switched PCI slots but to no avail.  I currently have whatever kernel comes with 6.10 and a default (clean) install.
I will try compiling another (older) kernel for Edgy and see what happens and if I can't get that to work, I'll try a complete earlier version of Ubuntu.  To be honest, I'm not sure how well the compiled kernel was because I still don't quite understand the kernel / initrd / modules / boot sequence enough to guarantee that everything was installed / configured correctly.  Thanks again and I'll post again once I get it working.
Richard

---

### Post by DaveBorealis on 2006-11-12
> **cougar6 said:**
> I currently have whatever kernel comes with 6.10 and a default (clean) install.
That's 2.6.18.
> I will try compiling another (older) kernel for Edgy

In case it's something more complex than simply the kernel, I'd try the live Dapper (6.06, 2.6.15 kernel) CD first and see what works.  Burning the CD shouldn't take longer than compiling and booting into a new kernel.  (But that's jsut me. ;) )

Dave

---

### Post by cougar6 on 2006-11-13
Dave,
Well, it didn't work.  Live CD of 6.06.1 resulted in only 1 CPU and no Ethernet.  I tried lspci and got nothing again.  So, I'm reinstalling Vector Linux and am going to recompile a 2.6.12 kernel with SMP and see what happens.  Thanks for the help.

Richard

---

### Post by cougar6 on 2006-11-13
Just so everyone knows, my re-installation of Vector Linux 5.1 and recompiling the 2.6.12.6 kernel resulted in use of both CPUs and network cards.  lspci does provide output now where before I got absolutely nothing.  So, I'll run Vector Linux until I can determine what went wrong and then (hopefully) I can get Edgy to work on this box.  Thanks, Dave, for the help.
Richard

---

