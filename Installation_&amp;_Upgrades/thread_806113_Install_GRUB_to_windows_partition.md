---
title: "Install GRUB to windows partition"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Ash44455666 on 2008-05-24
I'm sorry, but is this at all possible?  Here's my reasons...

About a month ago or so, might have been less, but anyways I installed Ubuntu 8.04 on my mother's PC to dual boot with Windows XP Home edition.  Everything worked perfectly, even the wireless card and compiz-fusion worked without any problems at all.  The thing is, my mom found herself never actually using Ubuntu... just Windows XP, and after a while she just asked me to get rid of it :neutral:
So I first just popped in the Ubuntu 8.04 CD and deleted Ubuntu's partition, including the main and the swap partitions.  I resized the Windows partition to fit all the empty space in the HDD, and I restarted the computer.  Of course I hadn't thought of this, but since GRUB was now gone, there wasn't any way to boot up Windows...
Ooh I know, I'll just pop in the Windows XP CD, start the recovery console, and "fix" the MBR.  If only... after booting from the CD, I got to the blue screen with "Windows Setup" or whatever is said at the top, but nothing was happening; it just stood there, nothing to do, nothing to say.
I had CDs with BartPE and UBCD4WIN (ultimate boot CD for Windows), and I tried those out.  They wouldn't finish booting up.  On my laptop, I tried getting DOS on a CD that I could use that included some form of the FIXMBR function.  For whatever reason, no CD worked, and the one that did apparantly asked for a registration code once started -_- [could skip this process, but the 'trial' version of it didn't allow for any actual writing to the MBR, or otherwise].
I tried using different methods of installing GRUB to Windows, but it always said either that it couldn't mount the selected partition, or that the 'folder' (wherever it be) didn't exist.

Is there any solution to this?  I guess I could just make a veeery small partition and install Ubuntu to restore GRUB, but if at all possible I'd like to avoid this method (not because of Ubuntu itself, it's great :****p, but because of the unnecessary space it's taking).

---

### Post by Pumalite on 2008-05-24
Try Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Ash44455666 on 2008-05-24
Hmm, I tried Super GRUB.  Since I can't do it on this computer I had to copy it to my flash drive, bring it to my laptop, burn it to CD, bring it to the computer, restart booting the new CD it took a little extra time (because the LiveCD occupied the CD drive at the time, just in case you can't remember :)).  When I rebooted the machine, the CD didn't boot.. at all, not even a hint that it was bootable in the first place.  Did I do something wrong?  I downloaded the most recent version in .iso form, and did all the steps explained in the beginning of this paragraph.

Edit:  Just adding, but I burned it as the ISO using ISO Recorder (very reliable), and not by extracting and burning the files themselves.

---

### Post by Pumalite on 2008-05-24
It has to be burnt as 'image', not as 'data'. OTOH, with all those transfers it might have gotten corrupted.

---

### Post by Ash44455666 on 2008-05-24
> **Pumalite said:**
> It has to be burnt as 'image', not as 'data'. OTOH, with all those transfers it might have gotten corrupted.

Well I just edited my last reply to just say that I made sure to save as an image and not the files themselves, but you replied 2 minutes before I edited it anyways, lol.  I guess I could just try again, but I've used up 4-5 CDs so far that all are useless now because they were unbootable (this PC is killing me :neutral:)

Edit:  Although this time I would just download it to the laptop and not on the LiveCD, and save myself a couple steps.

---

### Post by Ash44455666 on 2008-05-24
Well it still didn't work.  I even tried it on my father's PC, and it still wouldn't boot (set it to boot from the CD, and it read it a little... and then just booted from the HDD).  Is there another possibility?

---

### Post by Pumalite on 2008-05-24
Super Grub was your best shot.

---

### Post by meierfra. on 2008-05-24
Are you able to boot from the Ubuntu LiveCD? If yes, you can try"ms-sys".

Download the debian package for ms-sys from  here:

[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")

(Pick the i386 version)

You should be able to install the package by double-clicking the icon (if not, right-click the  icon)


Once ms-sys is installed;


```
sudo ms-sys -m /dev/sda
```

(Here I'm assuming that your hard drive is /dev/sda, you can find out the correct name by looking at the output of "sudo fdisk -l")

Reboot and hope for the best.

---

### Post by Rallg on 2008-05-24
Pumalite and meierfra are more knowledgeable than I am, so try what they suggest first. If their advice doesn't work:

Can you boot to the Ubuntu live CD (or any Linux live CD)? If so, boot the live CD. What volumes does it detect? Launch GParted. What partitions does it see on your hard drive? Do any of them have the "boot" flag?

In terminal, try:

ls -l /dev/disk/by-uuid

Does it reveal what you expect to see on the hard drive?

From the live CD, can you see the Grub menu.lst on the hard drive? (NOT the Grub menu.lst of the live CD.) What does it say? How about /etc/fstab on the hard drive (not the live CD)?

If you see anything odd, post the info here.

I cannot think of any obvious reason why your repair CDs cannot be fully loaded and used. My previous computer had XP, and I successfully removed Grub and restored the MBR at one time.

In the future: XP (but not Vista) allows you to text-edit a file within Windows, which can then use Grub from the Windows partition (no change to MBR). Later, if you change your mind, all you need to do is manually restore the Windows file to its original text, no fancy CD required. The method is well-documented around the Internet.

---

### Post by ballerh3 on 2008-05-25
I know I had to use the fixboot and fixmbr command in the recovery console so I can boot back into Windows XP.

---

