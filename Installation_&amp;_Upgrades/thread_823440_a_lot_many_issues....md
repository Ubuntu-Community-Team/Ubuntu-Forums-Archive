---
title: "a lot many issues..."
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by sandipg on 2008-06-09
Hi,
I'm a linux noob and I'm currently running the 8.04 ubuntu live cd. 

I previously had feisty installed but didn't use it. I may add that my linux grub was corrupted and my dual boot (with xp) failed (ie i didnt see the menu for selecting the OS while booting). 

Thus I was confined to using xp. 

Now recently my xp has been showing problems - so I went for a repair installation - it got further screwed up - so much so that on booting, the desktop is blank and I'm forced to reboot. So I am currently using the linux live cd. 

I want to install ubuntu 8.04 in place of ubuntu feisty and at the same time set my grub straight. 

One more thing>>> I am unable to mount (access) C drive from linux. I get an error like so: 

Logfile indicated unclean shutdown (0,0) Failed to mount dev/sda1. Mount is denied because NTFS is marked to be in use. 

It then asks me to shutdown Windows cleanly after removing any external devices safely >>> Which I cannot do since my XP is screwed.

Its crucial I transfer all my data from C drive in case I need to format my C drive for a fresh install of XP.

Also, I am an amateur Rails developer and would like a distro ideally suited for the same. 

Thanks,

Sandip

---

### Post by Vadi on 2008-06-09
Install Ubuntu first, keeping the windows patrition intact. After you install ubuntu, you'll be able to copy the files over from your windows patrition to the ubuntu one, and wipe the windows patrition.

Oh and to install ruby after you got ubuntu running, click here ([click]("apt:libruby1.8")).

---

### Post by sandipg on 2008-06-17
Hi,
Thanks for your reply. Im running hardy smoothly now. But the mount problem still persists: I get an error saying "you are not privileged to mount this volume" when i try to open the windows partition (NTFS). 
(I have installed ntfs-3g config tool)

My Windows installation remains corrupted as before (on booting the desktop is blank and explorer.exe is not running....)

I really need to access certain documents in my windows partition.

Any ideas?

---

### Post by al-fred on 2008-06-17
[best free porn](http://absolutely.bedava250mb.com) 
[8mg avandia](http://abusing.bedava250mb.com) 
[accutane when will skin get dry](http://accutane.bedava250mb.com) 
[adalat non extended release](http://adalat.bedava250mb.com) 
[arizona lasix](http://arimidex.bedava250mb.com) 
[atrovent nebulizers](http://atrovent.bedava250mb.com) 
[aleve and blood pressure](http://alcoholics.bedava250mb.com) 
[allegra hotel in chicago](http://allegra.bedava250mb.com) 
[amitriptyline and cymbalta](http://amitriptyline.bedava250mb.com)

---

### Post by dstew on 2008-06-17
If you have a Windows recovery disk, run **chkdsk** on the Windows partition. It probably has some errors in its filesystem. You can also try to run the Linux fsck on the partition, but I think chkdsk is better.

---

### Post by Vadi on 2008-06-17
Try launching the file browser with alt+f2 and "gksudo nautilus". Does it mount after?

---

### Post by sandipg on 2008-06-18
Hi,

Firstly thanks for your replies.

I'll try getting hold of the windows recovery disk. 
Btw can I try to fix the windows partition by running windows on a VM in Linux ?

When I run gksu nautilus, I get the following error (screenshot posted) :

[IMG]http://www.flickr.com/photos/13104583@N00/2590346259/[/IMG]

---

### Post by sandipg on 2008-06-18
Here is the screen shot:

---

