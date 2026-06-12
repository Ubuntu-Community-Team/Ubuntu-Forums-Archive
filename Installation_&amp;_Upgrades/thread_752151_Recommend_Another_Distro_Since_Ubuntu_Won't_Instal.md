---
title: "Recommend Another Distro Since Ubuntu Won't Install?"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by LaneLester on 2008-04-11
Yes, I know that's an inflammatory Subject, but my milder one didn't get me any replies, and I'm running out of time to do something. I can't install either Xubuntu Gutsy or Hardy.

I just bought my wife a new Dell laptop with a 1280x800 screen. I resized the 360 GB drive down to leave Vista only 30 GB, and created some other partitions, including a 16 GB for Xubuntu. She had been using Kubuntu Gutsy on her old machine, and I was hoping Xubuntu and the newer machine might make a good difference.

The install seemed to go OK, but then I got an error 17 from grub when i tried to start Ubuntu. I discovered that menu.lst had the first option set to (hd0,0) instead of (hd0,5) where I had put Ubuntu. I edited menu.lst and got Ubuntu to start... sort of.

Instead of the GUI screen, I got a BusyBox prompt, and I noticed that there was no boot, home, media, or mnt directories.

I saw some other threads that implied that the BusyBox thing means a video problem. But that doesn't explain the missing directories.

I tried the F4 Alternate safe video option, and even the live CD couldn't get a GUI.

She mostly uses Firefox and OpenOffice, so she could just use Vista (!), but I just started her on Gnucash. That means I need to find some Linux distro that will install on this machine.

Lane

---

### Post by Belak on 2008-04-11
Well, what what video card do you have?
Sometimes it just takes a little bit of time to get it working.

If you want to switch though, I'd try Mint...
OpenSUSE is also an option, but to my knowledge, Ubuntu has some of the best linux support for most hardare.

What's your exact reason for having a dual boot?
It might just be better to have Ubuntu running inside a virtual machine inside Linux

---

### Post by wieman01 on 2008-04-11
OpenSuse
Knoppix
Debian

---

### Post by LaneLester on 2008-04-11
> **Belak said:**
> Well, what what video card do you have?
Sometimes it just takes a little bit of time to get it working.

I don't mind spending some time, but I tried all the tricks I knew.

It's a laptop, and Vista says it's a Mobile Intel 965 Express Chipset Family.

> If you want to switch though, I'd try Mint...
OpenSUSE is also an option, but to my knowledge, Ubuntu has some of the best linux support for most hardare.

Is Mint a Debian distro?

I was really shocked to have this trouble, since I had no trouble installing (x)Ubuntu on my wife's old laptop, my main machine, and my old laptop.

> What's your exact reason for having a dual boot?
It might just be better to have Ubuntu running inside a virtual machine inside Linux

I want dual boot for her machine for the rare times she want to run Kyodai (Linux has nothing that comes even close). But I want the machine to come up by default in Linux.

Lane

---

### Post by warp99 on 2008-04-11
> **LaneLester said:**
> The install seemed to go OK, but then I got an error 17 from grub when i tried to start Ubuntu. I discovered that menu.lst had the first option set to (hd0,0) instead of (hd0,5) where I had put Ubuntu. I edited menu.lst and got Ubuntu to start... sort of.

I saw some other threads that implied that the BusyBox thing means a video problem. But that doesn't explain the missing directories.

Can you boot to the install disk and mount the partition manually? Are the files there? Also is the partition an extended partition or primary one? Run 'fdisk -l /dev/$name_of_device' and post the results here.

Edit:
Well if it's hd0,5 then it's extended. Didn't notice that.

---

### Post by Belak on 2008-04-11
When it boots from grub, can you hit c to run the grub shell.
Then run the following command:
geometry (hd0)

This should give you your partition layout. Just in case you're not booting from the right partition.

---

### Post by warp99 on 2008-04-11
You may have to rebuild the initrd.img for some reason since your dropping to a Busybox prompt. Here is a post over at the Kubuntu post on how to chroot into the partition using the install disc:

[http://kubuntuforums.net/forums/index.php?topic=3091954.msg119367#msg119367](http://kubuntuforums.net/forums/index.php?topic=3091954.msg119367#msg119367)

---

### Post by LaneLester on 2008-04-11
Guys, I really appreciate all the suggestions.

The problem is now fixed, and as is true so often with me and computers, I have no idea what fixed the situation!

The only significant change I made was to format the big fat32 partition I had created to serve as a locations for docs, pics, etc. The Ubuntu partitioner was not able to format it for some reason, so I used a Winapp to do it.

Then I decided to reinstall Xubuntu Hardy for the new suggestions you had made. I had most recently tried Gutsy, and I really didn't want to use that version.

Anyway, after the install, the reboot to Xubuntu worked flawlessly! I haven't a clue, but I'm delighted.

Now to try to get wireless working. [grin]

Later: Oh, crud. I let Synaptic update everything (300+ files), and now it won't boot. It gets stuck with about 1" of the progress bar showing. Since I just downloaded the .iso yesterday, I'm surprised that much stuff got updated.

Oh, wait! It just went to the terminal screen and says "Loading hardware drivers [fail]" among a number of OKs. So I tried rebooting with the second stanza (recovery). It went along until it hit "USB Video Class driver" and then hung. I'll come back later when I have more info.

Even later: It finally said "[OK", "Setting the system clock," Loading kernel modules," and "Loading manual drivers." And then it stopped again.

Lane

---

### Post by LaneLester on 2008-04-11
OK, I downloaded a fresh daily build of Xubuntu Hardy and installed it. Then I did an update, and everything is fine. Whew!

Thanks again for all the suggestions.

Lane

---

### Post by iansyngin on 2008-04-11
ah, thank god for that. aren't computers great

---

### Post by LaneLester on 2008-04-11
> **iansyngin said:**
> ah, thank god for that. aren't computers great

Yes, they are... when they work. :)

Now I've discovered that the built-in wireless isn't working, and i've created a new thread to whine about that.

Lane

---

