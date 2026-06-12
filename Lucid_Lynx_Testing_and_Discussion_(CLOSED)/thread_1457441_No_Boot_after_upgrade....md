---
title: "No Boot after upgrade..."
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rednus on 2010-04-18
Hi All, I have update the system yesterday which installed 2.6.32-21 and loads of other updates.. and now the system doesnt boot.. not even to recovery console.. worst part.. not even to old kernels.. not sure what the problem is.. tried removing splash and quite and tried nomodeset nothing works.. it stops after displaying the lines below: 

> Begin: Running /scripts/init-botoom...
Done.
[1.932134] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address xx.xx.xx.xx
[1.932227] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
============some more eth 0 lines==========
[2.060050] usb 7-1: new full speed USB device using uhci_hcd and address 2
[2.241227] usb 7-1: configuration #1 choosen from 1 choice
===============some more usb lines========
that is it.. please help.. i am using dell xps 1330 with nvidia card..

---

### Post by forumache on 2010-04-19
Same here, on a HP mini 311 (Nvidia Ion, i.e. 9400m)
I installed from Beta 2 CD, everything fine.
After running update, no boot...

I got into grub, removed splash and quiet words and saw it hanging after eth0, bm-43, sometimes after usb

Cannot reboot with SysRq, Ctr-Alt-Del, etc, just by turning off the computer.

It is strange that I still can make it work, like 1 out of 7 boots if I keep pressing Esc, while the blinking cursor is there.

---

### Post by antiram on 2010-04-19
maybe the rootfs is not mounted? You could overtake the installation from a livecd with eg (sda5 is your /, sda1 is /boot):

sudo mount /dev/sda5 /mnt
sudo mount /dev/sda1 /mnt/boot
for fs in proc sys dev dev/pts; do sudo mount --bind /$fs /mnt/$fs; done

overtake with:
sudo chroot /mnt

and update the initrd (some or all) with
update-initramfs -u -k all
for all initrds or only latest with:
update-initramfs -u -k 2.6.32-21-generic

---

### Post by Riffer on 2010-04-19
I have the same problem, when boot gets past the initial Ubuntu splash it freezes.  I can boot with the "recovery" option in grub and use the failsafex option.  If I use low graphics mode I can get to my desktop, if I try any other option to try and fix it nothing happens.  So I tend to think its an xserver problem.

---

### Post by manoynmonic on 2010-04-19
same problem here, only recovery-mode and failsafe graphics dont help.  I can only get to my desktop by booting into the previous kernel 2.6.32-19 - 2.6.32-21 won't let x start, even in failsafe.

---

### Post by KegHead on 2010-04-19
Hi!

No problems here.

Dell mini 9 & self made atom 330 desktop.

KegHead

---

### Post by forumache on 2010-04-20
fixed by blacklisting b43, ssb and recreating the initramfs
using now broadcom STA drivers and no problems

---

### Post by manoynmonic on 2010-04-20
> **forumache said:**
> fixed by blacklisting b43, ssb and recreating the initramfs
using now broadcom STA drivers and no problems

That is the same wifi card I have - wonder if it was the problem here too.  I fixed it by booting into the old pre-update kernel, installing Kernelcheck, and building a new kernel.  The latest from kernel.org is a few clicks newer than the one that came out in the upgrade that messed up lucid for me.  Maybe that was overkill, but it did the job.

---

### Post by k3lt01 on 2010-04-20
> **Riffer said:**
> I have the same problem, when boot gets past the initial Ubuntu splash it freezes.  I can boot with the "recovery" option in grub and use the failsafex option.  If I use low graphics mode I can get to my desktop, if I try any other option to try and fix it nothing happens.  So I tend to think its an xserver problem.

Riffer, you should take a look at [this bug report]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379"). If you believe it is the same as your problem please subscribe and add any relevant information so the devs can fix it. There is a workaround available so please read the bug report and try it.

---

### Post by dino99 on 2010-04-20
and go to Planet and watch Joao Pinto post

---

