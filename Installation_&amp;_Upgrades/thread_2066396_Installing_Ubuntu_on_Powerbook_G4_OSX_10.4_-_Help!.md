---
title: "Installing Ubuntu on Powerbook G4 OSX 10.4 - Help!!"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by reubicon on 2012-10-04
Hi,

Best to start with the fact that I'm no expert so simple terms without acronyms work best for me :)

I have a Powerbook G4 17" running Tiger 10.4.11

I downloaded the Ubuntu 12.04.1 LTS 32bit and burned to disk. I also copied it to USB.

After reading instructions on how to install I loaded the disk and restarted, holding down 'C' to boot the disk. Just went straight to OSX. I then tried booting to firmware and typing 'boot cd' and got error 

'boot cd load-size=0 adler32=1 LOAD SIZE is too small'

I then tried booting to firmware and typed 'boot usb 0/disk@1:2, \\yaboot'

I tried this replacing 'usb 0' with 'usb 1' and 'usb 2'. I only have two ports so I guessed the one I was plugged into had to be named either 0, 1 or 2. Each time the screen flicked briefly to text appearing half way down the left side, but then flicking to a grey blank screen with a No Entry sign.

I read some information saying that a partition is required to install Ubuntu but when I tried this a message appears in disk utility saying I can't partition because the disk contains the start up volume.

Thinking about the error message booting with the disk 'LOAD-SIZE is too small' I wondered if maybe I'd burnt the wrong software. The disk space taken up for the download was under 700mb, is this right?

I looked on the Ubuntu website and discovered many different places to download from this page [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

At this point I realised that installing Ubuntu on an older Mac is by no means a simple task. 

Can someone please help me out here? It seems Ubuntu is the only way I'll be able to keep this fantastic piece of kit running safely.

Thanks in advance :)

---

### Post by egami on 2012-10-30
Hi,
I used to have Ubuntu 12.04 Installed on my PowerBook 12" G4
(Until I started messing around, but that's an other story..)

I had no problem to install Ubuntu 12.04 PPC

Make sure you have the PPC version of ubuntu (Mac (PowerPC) and IBM-PPC (POWER5) desktop CD)
=> [ubuntu-12.04-desktop-powerpc.iso]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso")

Burn it on a disk as described on the Ubuntu homepage, boot your Mac by holding the 'Alt' key and chose the CD to boot from, it may take a wile until the Mac recognize the disk, then you should be able to follow a nice graphical install guidance. If nothing happen, just wait my PowerBook took ages to boot, just be patient.
More infos for example about how to install WLAN you fin here: [PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

---

### Post by egami on 2012-10-31
Well, I solved the problem with my own PPC now.

If the 12.04; 12.10 or whatever Desktop-CD is not working. Try, download and burn a older Ubuntu ppc version (8.04 ppc) and try again, then as you finished to install it you can online upgrade to a never version. (Update manager)

---

