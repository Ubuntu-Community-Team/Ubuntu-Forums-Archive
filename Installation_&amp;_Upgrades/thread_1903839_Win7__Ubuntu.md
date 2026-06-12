---
title: "Win7 / Ubuntu"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by Claryn on 2012-01-03
Hi.

I currently got 1 SSD and 2 HDD's.
SSD: 60GB. (7GB free) Contains Windows 7
HDD: 1TB (640GB free) Contains applications and software for Windows 8
HDD: 2TB (Empty)

I want to run Ubuntu with Windows (Wubi). Someone told me that if I don't install Ubuntu on the same drive as Windows, I have to enter BIOS to chose witch OS that should boot. 

I want Ubuntu on the 2TB HDD, and still be able to use the HDD for more Windows software and applications. If I install Ubuntu on the empty HDD, will I be able to chose what OS to boot, and still use it in Windows?


Another way would be to install Ubuntu on the SSD, that got 7GB free, but Ubuntu takes 6Gb, so it wouldnt be much space left for Ubuntu applications.


Any suggestions to what I should do?

---

### Post by darkod on 2012-01-03
If you plan for any long term use of Ubuntu, I would say forget about wubi. That is only a short term install, to play around. Often updates will break it.
Not to mention that you will not be running a proper dual boot so if windows breaks down, nothing boots.

Yes, you can use only small part of the 2TB disk for ubuntu, and the rest as NTFS partitions holding data accessible from both windows and ubuntu.

I recommend installing as proper dual boot, putting the grub2 bootloader on the same disk. In bios change the first HDD to boot from and you will be getting the grub2 boot menu offering all the OSs you have.

As for the space allocated for ubuntu, depends on how you plan to use it. The minimum to allocate would be 10-15GB for the / (root) partition, and 2GB for swap, or 1.5 x RAM size if you plan to hibernate.

If you keep Home inside /, and plan to store large files, adjust the / size appropriately. You can always keep any large data on NTFS partitions which can be read from windows and ubuntu, as said.

If you have more questions, just ask.

---

### Post by Mark Phelps on 2012-01-03
While you MIGHT be able to install Ubuntu into the 7GB of free space on the SSD, that will fill up your SSD -- making it unreliable, as I have seen recommendations of leaving 20% free space on SSDs.

You would do better installing Ubuntu onto one of the hard drives -- but you will then need to boot from THAT drive in order to NOT mess up the MBR and boot loader on the Win7 SSD.

---

### Post by Claryn on 2012-01-03
Okei, thats alot of information...

I might do what you said and get a dual-boot.
I have no idea how to do this, would be great if you could explain it step by step or help me via TeamViewer or something like that.

I even got an error when I tryed to install Wubi on the HDD.. Ill just uninstall it then. 

Doing this on a laptop that only got 1 HDD? Is it possible to use Dual-boot there?

---

### Post by Claryn on 2012-01-03
Bump. I need help to do this dual-boot with the grub.

---

### Post by darkod on 2012-01-03
Yes, you can dual boot with 1 HDD on laptop/desktop.

In my last post I focused on the 2TB disk because that was your question. You can even install it on the 1TB disk since you have loads of free space. You really have a lot of options.

If you want to dual boot on one disk, you need to first check the partitions structure, in windows disk management or Gparted in ubuntu live mode with the cd (Try Ubuntu).

If you have 4 primary partitions already, you can't create partitions for ubuntu. If you have only 3 or less, you can install ubuntu without any problems.

This is one tutorial with screenshots I found fast:
[http://blog.sudobits.com/2011/09/11/how-to-install-ubuntu-11-10-from-usb-drive-or-cd/](http://blog.sudobits.com/2011/09/11/how-to-install-ubuntu-11-10-from-usb-drive-or-cd/)

Be careful only where it says "Now select the partition which says – ‘free space’ and click on ‘New Partition Table’." it means New Partition, not a partition table. Writing a new partition table will delete all your existing partitions.

In your case you would have to create the / partition (filesystem ext4), and swap.

Under the partitions list note the drop-down box to select where to install grub2. Make sure you select the same disk (it can work on other disks too, but that's beyond the point).

---

### Post by Claryn on 2012-01-03
Do I need a USB stick or a CD? That means I have to wait over 2 weeks, because there is no way I can buy an empty cd.. the stores are closed..
Can't I install it directly? Like with Daemon Tools?

EDIT: Found a usb stick.

If I install it at the 1TB, should I backup everything I got there, or is it no danger for it to be lost?

---

### Post by darkod on 2012-01-03
It's always better to have a backup, although I have never lost data that way.

---

### Post by Claryn on 2012-01-03
OKEI.

I try install it. I can allocate as much space I want on the 2TB harddisc, as that is the only thing I can do without having to either replace windows 7 or erase everything on my 1TB harddisc. When I press "Next" it just freezes, I can move the mouce but no buttons are working. This happened when I only did test it from the usb stick. It's very annoying, because I have rebootet 8 times now because it freezes! 

Please reply abit faster, its annoying having to wait 15-20 minutes between the answers, I know you might be trying the best you can, but this is very annoying.

EDIT: Omg, its 5th time it freezes when I press Forward after chosing hwere to install, it says I cannot undo the changes, and that it might take long time *hits continues a billion times". hits "Go back" a billion times. Nothing works -.-

---

### Post by darkod on 2012-01-03
Did you make unpartitioned space on the HDD?

You can only create the ubuntu partitions in unpartitioned space.

---

### Post by Claryn on 2012-01-03
> **darkod said:**
> Did you make unpartitioned space on the HDD?

You can only create the ubuntu partitions in unpartitioned space.

I guess. I just installed it at the HDD and gave it 600GB. When I rebooted, I could chose between Windows and Linux Ubuntu :D

---

### Post by Claryn on 2012-01-03
> **darkod said:**
> Did you make unpartitioned space on the HDD?

You can only create the ubuntu partitions in unpartitioned space.

I guess I did.
I'm back in Windows now, because when I removed the USB stick, I just got this error, that there was no such device...and something with grub.

When I go to computer, I can only use 1,3TB of the 2TB HDD, so the space is allocated to Ubuntu.. I'll try reboot again without the usb disc and see...

---

### Post by darkod on 2012-01-03
I guess you were resizing the ntfs partition on the 2TB disk and that's why it took so long. When the disk is empty it's much faster to delete the partition, create your ubuntu partitions and install, and then you can create as many ntfs partitions as you want in the remaining space.

But that doesn't matter now.

Can you boot grub2 without the usb stick? You will have to set in bios to boot from the 2TB disk.

---

### Post by Claryn on 2012-01-03
> **darkod said:**
> I guess you were resizing the ntfs partition on the 2TB disk and that's why it took so long. When the disk is empty it's much faster to delete the partition, create your ubuntu partitions and install, and then you can create as many ntfs partitions as you want in the remaining space.

But that doesn't matter now.

Can you boot grub2 without the usb stick? You will have to set in bios to boot from the 2TB disk.

Okei, its working now.. but..

I don't have internet connection, even though I am WIRED to the router. I tryed to follow this guide there on how to connect, where I had to type in the IP, my internal IP, the submask and the gateway to get connected..Well, I click anything with my mouse, I have to use my keyboard - tabbing around, so when I open a window I can't close it. 

Is there a way I can remove Ubuntu and get back the 600GB I allocated to Ubuntu?

---

### Post by darkod on 2012-01-03
Most wired connections work out of the box, depending on the network adapter. And if your router is set for DHCP you don't need to enter anything manually, just to make sure the cable you are using to connect is working fine.

Your mouse doesn't work? Wireless? What model?

---

### Post by Claryn on 2012-01-03
> **darkod said:**
> Most wired connections work out of the box, depending on the network adapter. And if your router is set for DHCP you don't need to enter anything manually, just to make sure the cable you are using to connect is working fine.

Your mouse doesn't work? Wireless? What model?

Its a Cyborg Rat 7. I can move it, and you can see that you select the button, but you can't click them, or scroll down any page..
EDIT: Which Linux OS should I boot? The Recovery mode?

---

### Post by darkod on 2012-01-03
No, the first one, that doesn't say recovery mode.

Recovery is used when the main can't boot.

---

### Post by Claryn on 2012-01-03
> **darkod said:**
> No, the first one, that doesn't say recovery mode.

Recovery is used when the main can't boot.

Just nevermind everything. How do I remove it and get my 600GB back?

---

### Post by darkod on 2012-01-03
Well, this was a waste of time....

Just go into bios and set to boot from your SSD. That will load win7 directly, since it can't see linux.

Then open Disk Management and delete the ubuntu partitions. Use that space for ntfs partition or what ever you want.

---

### Post by Claryn on 2012-01-03
> **darkod said:**
> Well, this was a waste of time....

Just go into bios and set to boot from your SSD. That will load win7 directly, since it can't see linux.

Then open Disk Management and delete the ubuntu partitions. Use that space for ntfs partition or what ever you want.

Sorry for wasting your time.
Ubuntu is soo not what people says it is.

---

