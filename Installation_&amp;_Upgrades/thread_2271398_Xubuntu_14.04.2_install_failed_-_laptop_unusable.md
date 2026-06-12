---
title: "Xubuntu 14.04.2 install failed - laptop unusable"
date: 2015-03-29
forum: Installation &amp; Upgrades
---

### Post by peppercorn7 on 2015-03-29
Hi, 

I did a foolish thing. I tried to install Xubuntu 14.04.2 (minimal/alternate install) on a Sony Vaio PCG-FXA47 without really knowing what I was doing. The Wireless Network Adapter previously would not seem to work under the Windows XP I had factory reinstalled. So I tried the Xubuntu, hoping that version 14 would have drivers all included so that I could get internet on here to do basic browsing from coffeeshops. 

The install had problems with the DHCP autoconfiguration. I tried manual configuration through vaguely-educated guessing, and that didn't work. So then I got the mirror site problem, so then it couldn't apparently download files it wanted to continue installing. I aborted installation. I put my Windows System Recovery CD's in and got a sector and another error, and was unable to boot. I get the install screen back if I put the Xubuntu CD back in, but I can't do anything without an internet connection. 

I just want my Windows back until I can invest the time and energy into doing this properly. It's an extremely bad time, and I wasted all day trying to get the wireless card to work, and I need to give up until I can do it with help, or unless I can miraculously save the install. It will seem like a miracle if I can get my Windows install back. Either one will do! 

Thanks for any help anyone can give.

---

### Post by peppercorn7 on 2015-03-30
I'm a somewhat-new Ubuntu user. Should I have posted this in the New to  Ubuntu section? If so, could someone please move this for me?

---

### Post by Vladlenin5000 on 2015-03-30
Hello and welcome.

Yours boils down to a netwroking & wireless type of question/support request.
However, Ubuntu isn't magical and can't bring back to life faulty hardware as it seems to be the case: > The Wireless Network Adapter previously would not seem to work under the Windows XP I had factory reinstalled..

If you need help with the wireless - at all times keeping in mind the aforementioned scenario - then first please read this, follow the instructions and if not solved open a new thread in that section and post the results of the script, either by annexing the txt file or Go advanced, click # (code) and past all of its contents inside.

---

### Post by kurt18947 on 2015-03-30
Could you boot from the live Ubuntu disk or a live USB? Even if you have a sick hard drive, you should still be able to boot to a live session. If you have access to a wired ethernet connection you may be able to at least get online using the live session. No expert on this stuff but if it were me, I'd use Gparted and/or Disks to look at the hard disk if one or both were included in the live distro. I'm pretty sure Disks will display S.M.A.R.T. disk info. You could maybe use Gparted to delete and recreate NTFS and ext* partitions. Perhaps Gparted will  mark any bad sectors so the Windows installer will run? If you start with disk editors, any data on the disk is at grave risk.

---

### Post by peppercorn7 on 2015-03-31
> **Vladlenin5000 said:**
> 
However, Ubuntu isn't magical and can't bring back to life faulty hardware as it seems to be the case: .

If you need help with the wireless - at all times keeping in mind the aforementioned scenario - then first please read this

Hi, thanks. I wasn't sure the wireless problem was hardware. The green indicator lights turn on, and it's possible I didn't install the drivers or configure the card properly in XP. I thought a new version of Ubuntu may have streamlined these processes since 2002. In any case, you suggested I read something but I think you forgot to create a link when you wrote "read this". In any case, I'm considering buying a $5 one-month dialup connection so Xubuntu can download files for installation and temporarily avoid the wireless card issue. 


> **kurt18947 said:**
> Could you boot from the live Ubuntu disk or a  live USB? 

You could maybe use Gparted to delete and recreate NTFS and ext*  partitions. Perhaps Gparted will  mark any bad sectors so the Windows  installer will run? If you start with disk editors, any data on the disk  is at grave risk. 

I don't have a live USB or an available flash drive. The CD I used is minimal/alternate install; I saw no option to live boot. Before the install fail, I had booted with a Xubuntu 6.10-desktop CD. I certainly wasn't mindful about partitions and file formats before razing XP. There is no data on the machine, though; it's just a matter of me figuring out how to use the disk tools later. Thanks. 

I have other urgent things to take care of right now, but I will get back to this ASAP (possibly weekend or later).

---

