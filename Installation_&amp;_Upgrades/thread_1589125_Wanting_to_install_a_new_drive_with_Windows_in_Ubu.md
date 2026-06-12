---
title: "Wanting to install a new drive with Windows in Ubuntu Desktop"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by TonyChaos on 2010-10-05
Hey all, 

I want to add another drive to my desktop machine so that I can use a Windows partition to do some gaming and use HTC Sync. What would be the best way to do this?

Thanks!

---

### Post by oldfred on 2010-10-05
Just install windows to the separate drive. It will put its boot loader into the MBR, but you can still boot your other drive and run sudo update-grub and it will find the windows install.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by TonyChaos on 2010-10-05
> **oldfred said:**
> Just install windows to the separate drive. It will put its boot loader into the MBR, but you can still boot your other drive and run sudo update-grub and it will find the windows install.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

So should I just plug the drive in and unplug the ubuntu drive, boot it up and install windows, then unplug that drive, plug back in the ubunu drive, boot it up, then plug in the windows drive and update the GRUB?

---

### Post by oldfred on 2010-10-06
Some recommend unplugging drives to be sure that an install does not put files on the 'wrong' drive.

Windows will want to be the first drive and if you unplug the Ubuntu drive windows will be first. When you plug it back in grub should add mapping to make it think it is first even if it is not. If you directly boot the windows drive from BIOS it should still be the  first drive as it boots.

---

### Post by TonyChaos on 2010-10-06
> **oldfred said:**
> Some recommend unplugging drives to be sure that an install does not put files on the 'wrong' drive.

Windows will want to be the first drive and if you unplug the Ubuntu drive windows will be first. When you plug it back in grub should add mapping to make it think it is first even if it is not. If you directly boot the windows drive from BIOS it should still be the  first drive as it boots.

So what I said to do would make everything work smoothly?

---

### Post by Mark Phelps on 2010-10-07
I'm one of those "some" that recommend unplugging extra drives when you do installs or version updates.  It's not entirely necessary, but it completely prevents the problem of GRUB being unintentionally installed to a drive already containing a different MBR.

It's really a simple matter later to reconnect the drives, boot from the Ubuntu drive, open a terminal, and enter "sudo update-grub".

That takes a LOT LESS time than it would to clean up MBR mistakes.

---

