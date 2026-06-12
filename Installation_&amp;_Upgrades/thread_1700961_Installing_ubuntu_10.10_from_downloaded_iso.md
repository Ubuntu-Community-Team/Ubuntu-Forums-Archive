---
title: "Installing ubuntu 10.10 from downloaded iso"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by Terry Tao Ling on 2011-03-05
My HDD died recently. Having fixed that, the only install CD I had was ubuntu 5.10, I was hopeful that, once back in action, I could just update to the latest ubuntu online. Not so!

I downloaded "ubuntu-10.04.2-desktop-i386.iso" and burnt it to CD using my other (Windows) PC. The CD would not boot, neither on my Linux nor my WIN32 PC!
 
 I tried various things to make it bootable (using Isobuster, Imgburn and Nero) but  to no avail.
According to Isobuster, the CD has a boot image. 

Can anyone advise me? What should I do to install ubuntu 10.10 on a PC running ubuntu 5.10?
Why won't  "ubuntu-10.04.2-desktop-i386.iso" boot up when burnt to a CD?

---

### Post by hosinfefer on 2011-03-05
real stupid ? but are you sure your box is set to boot from CD? Also after you burn the image in M$ if you put it back in the drive does your windows machine see an .iso file on the cd? Just trying to figure out if your just burning a .iso file to disk or doing an actual .iso unpackage to cd.

---

### Post by Terry Tao Ling on 2011-03-05
hosinfefer, thanks for replying

Q "are you sure your box is set to boot from CD?"

Yes. The box boots OK from the ubuntu 5.10 install CD. In BIOS, the cdrom is set as the 1st boot option.

Q "after you burn the image in M$ if you put it back in the drive does your windows machine see an .iso file"

In Explore, it sees a bunch of folders and files

Q "trying to figure out if your just burning a .iso file to disk or doing an actual .iso unpackage to cd."

I tried many combinations, none of which worked: 
1/ Asked Nero to open the iso image, and then burn it as a bootable CD
2/ Asked Imgburn to do the same thing
3/ Extracted the iso contents to a folder on my HDD, then used Isobuster to find and extract the boot image, then asked Imgburn to build a bootable disk using the extracted iso contents, and nominating that image as the boot image.
4/ Used Isobuster to pull a boot image from an ubuntu install disk that did boot (the old 5.10 version), and repeat "3/" using that image instead.
5/ Directed harsh language at the PC.

Terry

---

### Post by hosinfefer on 2011-03-05
I have had this issue sometimes. Have you tried to load everything onto a thumbdrive and boot from the thumbdrive? (plus it loads much faster:)

---

### Post by yourwhiteshadow on 2011-03-05
it could very well be the media. as in, that brand of CD. try burning a CD or DVD at different speeds. that should do that trick.

---

### Post by jcolyn on 2011-03-05
Try burning another CD at the lowest burn speed.

ISO's don't always burn right at higher speeds..

---

