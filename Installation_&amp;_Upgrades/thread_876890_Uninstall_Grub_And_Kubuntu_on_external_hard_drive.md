---
title: "Uninstall Grub? And Kubuntu on external hard drive?"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by blahbah7 on 2008-08-01
On my laptop I have a dual boot with Vista and Ubuntu.  I installed Kubuntu on my external hard drive and it looks like I installed it wrong.  I did the regular live cd installation when it looks like I should have done this: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Now I want to reformat the partition that I have Kubuntu on but I need to figure out how to switch grub back to the Ubuntu on my internal hard drive, how would I switch grub back to there?  At the moment I get error 21 whenever I don't have my external hard drive in and try to boot

---

### Post by Pumalite on 2008-08-01
First fix your Windows MBR with installation disk (Recovery>Fixmbr>Fixboot)
Or super grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Burn to disk and boot from it. Come back later for the rest.

---

### Post by blahbah7 on 2008-08-02
Ok I did that and it worked great, now how do I make it bootable?

---

