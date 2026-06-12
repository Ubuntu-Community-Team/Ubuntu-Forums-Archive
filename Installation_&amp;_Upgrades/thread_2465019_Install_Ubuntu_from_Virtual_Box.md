---
title: "Install Ubuntu from Virtual Box?"
date: 2021-07-19
forum: Installation &amp; Upgrades
---

### Post by yaminb on 2021-07-19
HI all,

I have 2 drives and I install Ubuntu on both of them. I normally keep different versions, just for some redundancy.
Normally, if I need to install Ubuntu on one of the partitions, I put the installer on the USB and boot from that USB.

Is it possible to mount the installer in virtual box then use it 'install' Ubuntu on the unused  partition? Would this create any complications in my install?

Example:
1. Boot into my regular Ubuntu 20.04 (LTS) (/dev/sda1)
2. Download say Ubuntu 21.04 install ISO
3. Mount that Ubuntu 21.04 ISO in virtual box
4. in the VM, choose to install Ubuntu to /dev/sdc1)

Anyone see any issues? Maybe because it's a VM some settings in the install are incorrect as there would be less memory/CPU allocated to it? Maybe some drives won't be properly detected so the boot menu/grub on the new install won't be correct?
Or would everything work peachy clean?

Thanks,

---

### Post by sudodus on 2021-07-19
I have never done that. Normally the virtual machine can see virtual disks 'inside VirtualBox'.

If you can make the virtual machine see the real disk it should work. This is a bit tricky but possible with USB drives, and it might be possible also with SATA drives (but I don't know how). Let us hope someone else can help you doing that.

It is easier to see USB drives (and probably also SATA drives) from a virtual machine created with KVM + VirtManager.

[hr][/hr]
But it is easy to clone from an Ubuntu iso file to a USB pendrive and pendrives are cheap, so this is the way I recommend in order to install Ubuntu. (You can also install from any other 'extra' drive connected via USB, SATA, eSATA, PCI (mmcblk for SD cards, nvme for SSDs)) and of course an old optical disk, DVD, if the computer can boot from it.

---

### Post by TheFu on 2021-07-19
I suppose having multiple installs on the same system is 1 way to accomplish a little redundancy.
The storage UUIDs would almost certainly be different.  The storage device names are definitely different.  vdX vs sdX. 

There are other differences - like the NIC will be a virtual NIC - use virtio drivers for low overhead, better performance. The real NIC in the hardware is probably some cheapo Realtek junk or worse, wifi.

Then there is the GPU drivers - virtual machines only see virtual GPUs, so the real GPU driver would conflict. That could be bad, if not inside the VM, the problem will be seen booting it outside the VM.

For "emergency needs", I just use a live-boot "Try Ubuntu" flash drive.  About a year ago, the boot/OS HDD on my plex server died. I had backups, but not a spare HDD.  While I waited for a replacement to be shipped, I booted Ubuntu-Mate into the "Try Mate" environment, setup a little DLNA server, hooked up the 32+TB of storage to that and kept the family mostly happy.  What they had already watched wasn't stored, but all the media was there. Wifey found an old TV show that she wanted to rewatch, so that was a bonus.  5 days later, I did a fresh install onto the new-to-me HDD (I buy used enterprise HDDs), and restored everything so we were back just like the day before the crash. It was just entertainment stuff, so I don't use RAID with it, but I do have backups for everything.

Most importantly, the Try Ubuntu on a flash drive worked find the entire time.  I always keep one of those handy, since we have multiple systems here and sometimes booting from alternate media is necessary.  Obviously, important systems have much greater care taken, but for a laptop used 4 times a week, not daily, meh ... backups are more than sufficient. If anything really bad happens and I've wasted more than 30 minutes trying to fix it, I know that a restore of the backups takes 30-45minutes to be back to what is was previously.

Or keep a raspberry Pi v4 around.  That can be used as a desktop in a pinch.  Want to completely change the OS, just use a different microSD card. I understand that Mate runs reasonably well on a r-piv4.

There are options.  Try a few. See what works best for you.

I stopped duel/dual booting around 2010 after using virtual machines for a few years before that.  For my needs, VMs solve 97% of what I need in a desktop.

---

