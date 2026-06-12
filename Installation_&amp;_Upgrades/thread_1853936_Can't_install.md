---
title: "Can't install"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by daliz84 on 2011-10-03
Sorry for the generic title but this is the truth!

Every 11.04 variant (Ubuntu, Xubuntu, Kubuntu, Mint) I tried doesn't boot on my new PC. The same USB dongle works on other computers.

What I get is different on each variant, but substantially my boot process lasts 10-15 seconds and the result is always the same: Black screen.

I think my NVidia GT-530 isn't supported at all. Anyway, here are my Xorg logs:

[http://dl.dropbox.com/u/6870753/Xorg.0.log](http://dl.dropbox.com/u/6870753/Xorg.0.log)
[http://dl.dropbox.com/u/6870753/Xorg.1.log](http://dl.dropbox.com/u/6870753/Xorg.1.log)

I really hope someone can help me. Thank you!

---

### Post by Quackers on 2011-10-03
Welcome to UF :-)
You may need to use the nomodeset boot option, due to your video card. Here's how

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by daliz84 on 2011-10-03
Thank you for your answer!

Unfortunately, none of the proposed solutions worked.

---

### Post by MAFoElffen on 2011-10-03
> **daliz84 said:**
> Thank you for your answer!

Unfortunately, none of the proposed solutions worked.
Your NVidia GT-530 is supported.

How did you try to use the nomodeset kernel boot option?  If you look at post 			#[**3**]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3") of my graphics sticky... A little more clear/detailed instructions...  With NVidia cards, that kernel boot option should work or "xforcevesa"  

How much memory doees your system have?

---

### Post by daliz84 on 2011-10-09
Hi MAFoElffen, thank you for your answer.

I have tried adding "nomodeset" to the GRUB command line. Adding also "rdblacklist=nouveau" I've managed to make other distros work.

On Ubuntu (11.04 and 11.10) it is useless. All I get is the black screen. My system has 4 GB (RAM) and 500 GB (HD).

Any help, please?!

---

### Post by MAFoElffen on 2011-10-09
> **daliz84 said:**
> Hi MAFoElffen, thank you for your answer.

I have tried adding "nomodeset" to the GRUB command line. Adding also "rdblacklist=nouveau" I've managed to make other distros work.

On Ubuntu (11.04 and 11.10) it is useless. All I get is the black screen. My system has 4 GB (RAM) and 500 GB (HD).

Any help, please?!
I just looked at your xorg logs and let me clarify something I said.

 - Your nvidia card is supported by the proprietary drivers.
  -- You do not have proprietary drivers installed.
Since you do not have proprietary drivers installed, it is trying to use the NOUVEAU driver for NVIDIA, which doesn't seem to support the model of your nVidia card.  Before that, It fails on loading the nvidia module (not found / not installed) so it falls back to the nouveau.  It since it is not supported by that driver, it temp could go to vesa to use vesa modes instead.

Besides "nomodeset" you could also use:
```

xforcevesa
nouveau.modeset=0

```to get it booted initially to be able to install your driver.

There are 2 other options frorm your grub menu-
- Boot into rescue mode from the Grub boot menu item > Use safemode / low graphics... go to System > Administration > additional driver > install nvidia-current.

OR
- Grub Boot menu > Press "e" to enter an edit mode > Replace "quiet splash" with --verbose test" on the line that starts with "linux" > press <cntrl><x> to boot into tty text console. These instructions are to install an nvidia driver on a fresh install...
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo apt-get install linux-headers-'uname -r' 
sudo apt-get install nvidia-current
sudo apt-get upgrade
sudo reboot

```

Or you could install the nvidia binaries (see post 			#[**280**]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280") <--Link)  nVidia driver 285.05 is latest and does support your card.

---

### Post by daliz84 on 2011-10-11
Thank you, sir. You are a real gentleman :)
I will try this tonight.

---

### Post by daliz84 on 2011-10-13
Ok. It's incredible but it doesn't work yet.

Tried with:

- nouveau.nomodeset => nothing
- nouveau.modeset=0 => nothing
- nouveau.nomodeset xforcevesa => nothing
- xforcevesa => nothing
- xforcevesa nouveau.nomodeset => nothing

Tried with 'quiet splash', with 'quiet', with 'splash' and nothing at all.

It simply doesn't work.

With xforcevesa, Xorg.0.log says something like "can't find default screen".
With one of the above combinations I get the graphical mouse pointer, but the screen stays black.

Am I the only one in the world?!

---

### Post by daliz84 on 2011-10-15
I can add a detail, but I don't know if this is important:

My computer is a HP Pavilion with two graphic cards: the bundled Intel HD 3000 (but this is disabled in the bios by default and the ports are physically sealed) and the NVidia GT-530.

Thanks :(

---

