---
title: "Installing on Dell C400"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by DenzilS on 2008-01-19
Relative newcomer to Linux - currently running another distro on a desktop PC, but would like to try Ubuntu 7.10 on my Dell C400 laptop.

Specs
1.2GHz P3-M
256Mb RAM
30Gb HD (blank unformatted)

So I download the install CD, boot up, and after seeing the list of services starting up I get a pale brown blank screen with a cursor in the middle. Nothing else.

So I try downloading the alternate install CD (I did tick the box) and left it to find it had downloaded apparently the same Live CD ISO as before (no text install option). I tried this one, with the same result, blank brown screen.

I have tried the safe graphics mode and OEM install options, same result. Any ideas?

Denzil

---

### Post by confused57 on 2008-01-19
> **DenzilS said:**
> Relative newcomer to Linux - currently running another distro on a desktop PC, but would like to try Ubuntu 7.10 on my Dell C400 laptop.

Specs
1.2GHz P3-M
256Mb RAM
30Gb HD (blank unformatted)

So I download the install CD, boot up, and after seeing the list of services starting up I get a pale brown blank screen with a cursor in the middle. Nothing else.

So I try downloading the alternate install CD (I did tick the box) and left it to find it had downloaded apparently the same Live CD ISO as before (no text install option). I tried this one, with the same result, blank brown screen.

I have tried the safe graphics mode and OEM install options, same result. Any ideas?

Denzil
The alternate cd will  install the same desktop programs as the live cd...have you tried pressing "Esc" when prompted by grub at boot of your pc?  This should open your grub boot menu, where you can select Recovery mode...if you're able to boot into Recovery mode, enter this after the root prompt(#):
```
dpkg-reconfigure xserver-xorg
```
select "No" at the first screen to autodetect, then you can probably go with the default selections for everything else, except select vesa as your video driver.  When you're finished reconfiguring xorg, enter reboot or reboot your computer by pressing reset button.

---

### Post by DenzilS on 2008-01-19
I guessed maybe there was some graphics driver issue, so wanted to try a text install. The issue there was that ticking the "alternate CD" box on the download page gave me exactly the same Live CD ISO. I couldn't do anything in GRUB because it wasn't installed. As I said, this was a completely blank HD.

As it happens, I just went shopping and found a magazine with a 7.10 DVD. That seems to have every installation option anybody could want. I tried the text based install and (so far) it is all working beautifully.

Denzil

---

### Post by immerohnegott on 2008-02-19
I've got the same laptop (writing this post on it, actually). Just download the alternate CD - for real, this time. It should install fine. I had a hell of a time getting installing from the live disc, but the alternate worked pretty nicely. I do, however, recommend using Xubuntu instead since XFCE is a bit lighter on the resources than Gnome or KDE (although I've been running KDE4 on here for a few weeks, and it's a lot quicker than I expected).

---

