---
title: "Installing Ubuntu impossible for me..."
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by phasair on 2011-10-12
Hello people,

I tried installing ubuntu, and I will describe what happened.
I am basically installing ubuntu from a usb drive, and I am trying to dual boot along side windows. Everything goes fine, I've picked a username and all that, it installs the system, and then it asks me to reboot. I press okay, and it goes into this screen.
[http://i.imgur.com/AtLhB.jpg](http://i.imgur.com/AtLhB.jpg) (I also attached it to this post)
And it stays there.

Then, when I hard powered my computer off, it automatically boots into windows. When I go into a partition manager, I can see an ext4 partition that's ~3.7 GB, and a swap partition, so I can only assume the files were copied to my harddrive, but the installation didn't finish.

Anyone have any idea to fix this? When I google search for crashing on shutdown, I mostly get advice that involves the terminal, but unfortunately, I can't use the terminal, because it happens during the installation...

Also, if it helps, wubi works fine, I've actually used it for a couple of days. But I really want an actual dual boot.

Thanks in advance!:KS  

EDIT: I tried the livecd, and it boots up fine. Unfortunately, when I shut down from the live cd, the same thing happens (it hangs with a similar picture)

---

### Post by Sef on 2011-10-12
> Then, when I hard powered my computer off, it automatically boots into  windows. When I go into a partition manager, I can see an ext4 partition  that's ~3.7 GB, and a swap partition, so I can only assume the files  were copied to my harddrive, but the installation didn't finish.

How big is your root partition? For the Ubuntu Desktop Edition, [15 GB]("https://help.ubuntu.com/community/Installation/SystemRequirements") is the recommended root partition size.

---

### Post by phasair on 2011-10-12
> **Sef said:**
> How big is your root partition? For the Ubuntu Desktop Edition, [15 GB]("https://help.ubuntu.com/community/Installation/SystemRequirements") is the recommended root partition size.

 The partition I was using was ~25 GB, the 3.7 was only the used space. I read somewhere a clean install of ubuntu takes approx 3-4 GB, so that's why I assumed that was the data of a clean install. Too bad I can't access it, since I don't think the installation completed properly.

---

