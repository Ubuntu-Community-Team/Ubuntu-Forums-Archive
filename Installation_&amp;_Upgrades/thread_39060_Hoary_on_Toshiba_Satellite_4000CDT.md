---
title: "Hoary on Toshiba Satellite 4000CDT"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by enmity on 2005-06-03
I am extremely noobish at this linux business, and I thought installation on an old laptop of mine would be interesting (Toshiba Satellite 4000CDT).

Unfortunately I can't get very far through the installation process.

After hitting enter for default install I get up to:
Retrieving nic-extra-modules 2.6.10-5-386-id
then
Unpacking nic-extra..........(etc)

Then blank screen then goes back to retrieving nic-extra.......(etc)

Any tips??

---

### Post by BeeZ on 2005-06-03
buy a new one? :)


reboot and dont use default?

---

### Post by enmity on 2005-06-03
Uhm they're not the best tips.

What would you suggest other than default.
I tried expert but that didn't work either.

What else can I try?

---

### Post by DrMoxie on 2005-06-03
Hmm, does it just keep bouncing back like that?  I've installed Ubuntu on 5 Toshiba Laptops so far without any hitches (2 Satellite A15's, 2 Satellite Pro 4280-XDVD's, and 1 Satellite 2400-S251).  

Has the laptop had any problems with its hard drive or CD-ROM drive in the past?  Maybe you could try a Live CD and see how far you get.  Just a thought....  :???:

I'll dig around and see if I can find a 4000 CDT and try installing on it as a reference point.

---

### Post by az on 2005-06-03
You need more than 32 megs of ram to install.  How much ram does that machine have?

---

### Post by DrMoxie on 2005-06-03
[QUOTE=azz]You need more than 32 megs of ram to install.  How much ram does that machine have?[/QUOTE]

They come stock with 32MB but are expandable to 160MB so that *might* be part of the problem.

---

### Post by mingus on 2005-06-03
I agree with azz . . . if the RAM is that small . . . I have not tried this with Ubuntu specifically, but with other distros where I've installed on low RAM hardware, I've created the swap partition in advance.  The installer then detects this and uses that.  The other little gotcha sometimes is that the installer kernel may not get the right amount of RAM passed to it from the BIOS, there is a kernel argument (google kernel argument howto) that instructs the kernel what the correct RAM value is.

---

### Post by az on 2005-06-03
I got 64 megs of ram for my toshiba for something like 25 bucks.  If this is not an option, perhaps you can try installing Woody (debian) and dist-upgrading to Hoary?

Or just use Woody to create a swap partition as mentioned....


I

---

### Post by mingus on 2005-06-04
or use a live CD like Knoppix to create the swap . . .

---

