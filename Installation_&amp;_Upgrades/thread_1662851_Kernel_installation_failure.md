---
title: "Kernel installation failure"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by Evandar on 2011-01-08
Hey all

I'm quite new to the whole using Ubuntu (and Linux in general) thing. I recently realised that I could use Linux to "revive" old machines, and have set it as my goal to actually get all old PCs in my house working again using different variants of Ubuntu, while learning how to use the OS in the process. And now I got stuck while installing the OS on an old Laptop. It's an HP Omnibook XE-3, with a Pentium III 1066 MHz cpu and, supposedly, 256 MB of RAM. However, for some reason the computer only reads 248 MB, so I've been forced to resort to an alternative disc installation. Since the old HP has a broken CD tray, I've been using an external hard drive to boot the image, created with Ubuntu's startup disk creator, instead of an actual CD rom (I doubt that makes a difference, but just in case) 

There are two main issues which have really left me with no obvious (for a newbie) alternatives. Firstly, when the text installation procedure reaches the "Installing base system" part, an error message appears saying that no kernel could be found on my Drive, so the installation fails. If I try to skip installing a kernel temporarily, it lags horribly and produces multiple errors, dying shortly after.  

The second problem is that I can't actually do a command line boot to try and manually figure out a way around this. Selecting the command line installation mode on the main installation menu changes nothing, and it's a normal text install which runs instead. Unable to access the command line, I find myself pretty helpless.

If someone can help me figure out why my kernel is apparently missing, I would be very thankful. Alternatively, if you can provide command line help (accessing and perhaps using it as well), I would very much appreciate quite specific instructions in using it, since, as I said, I'm a newbie.

Thanks in advance.

---

### Post by Joe of loath on 2011-01-08
Have you tried re-downloading the .iso and creating the install disk again? Sounds like a classic case of a corrupted image file.

Also, regular Ubuntu will be very slow on 256mb of RAM, almost unusable. I suggest using Lubuntu instead, it's much quicker.

---

### Post by Evandar on 2011-01-08
> **Joe of loath said:**
> Have you tried re-downloading the .iso and creating the install disk again? Sounds like a classic case of a corrupted image file.

Also, regular Ubuntu will be very slow on 256mb of RAM, almost unusable. I suggest using Lubuntu instead, it's much quicker.

I've tried using multiple different downloads of Ubuntu, xubuntu, lubuntu, and the ubuntu server version. I know standard Ubuntu can't run fast, as I read quite a bit of documentation before selecting an OS. All of them gave the kernel error. I seriously doubt all of them were corrupted... Perhaps I am creating the disc wrong?

Edit: this is actually probably what happened, as after re-formatting the drive and experimenting with the startup disc creator options I have gone further into the installation than ever before. I wonder why I never thought that my startup disk might not have installed properly before, and always blamed it on the isos. Let's see how this goes. (I wonder why I never come up with solutions BEFORE I post in help forums)

---

### Post by Joe of loath on 2011-01-09
From what I remember, the alternate install only works from CD/DVD. If you're still using that, you might have to use this: [http://wiki.debian.org/BootUsb](http://wiki.debian.org/BootUsb)

It's worked flawlessly for me on multiple occasions, although I've never tried it with ubuntu it should work fine.

---

### Post by Evandar on 2011-01-09
> **Joe of loath said:**
> From what I remember, the alternate install only works from CD/DVD. If you're still using that, you might have to use this: [http://wiki.debian.org/BootUsb](http://wiki.debian.org/BootUsb)

It's worked flawlessly for me on multiple occasions, although I've never tried it with ubuntu it should work fine.

Well I managed to do a command line install without errors, so it seems to be working with USB now (although it still thinks that it's reading a CD/DVD). 

Thanks for the support, dude.

---

### Post by Joe of loath on 2011-01-09
Oh, excellent! Maybe the ubuntu alternate disc supports USB now.

If you want a GUI that will work well on your machine, install lxde. Or, if you want Gnome, you can buy memory for the XE-3 cheap on ebay, I think it supports a maximum of either 512mb or 1gb.

(I'm also looking for an XE-3 to repair one I bought a while back. Know anywhere to get good ones cheap? :lol:)

---

### Post by Evandar on 2011-01-09
for some reason, lxde makes mine crash, so I'm not too sure what I'll do with it. I need to try and repair it.

---

