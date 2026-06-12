---
title: "GRUB doesn't like extra IDE HD?"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by Starcraftmazter on 2007-09-27
Hey.

I have a new comp. It came with an 80gb sata2 HD, on which  I put windows on. Then I installed a 160GB sata2 HD and put feisty on it, and then upgraded to gutsy, since it supports my new gfx card and mobo.

Now, gutsy works very well, and so I want to hook up my old IDE HD (60gb) with feisty and copy all my files and settings and things of that nature.

The problem is, once I hook it up, I am unable to get into gutsy. Here is a list of the outcomes for the different boot orders I tried with my HDs:

--------------------------------------
1. 80gb Windows
2. 160gb Gutsy
Boots into gutsy grub
--------------------------------------
1. 160gb Gutsy
2. 80gb Windows
Doesn't boot (no errors, just nothing happens)
--------------------------------------
Putting the old drive in,
--------------------------------------
[COLOR="Red"]1. 80gb Windows
2. 160gb Gutsy
3. 60gb Feisty
Boots into feisty grub (old HD)[/COLOR]
--------------------------------------
[COLOR="Red"]1. 80gb Windows
3. 60gb Feisty
2. 160gb Gutsy
Boots into feisty grub (old HD)[/COLOR]
--------------------------------------
[COLOR="SeaGreen"]1. 160gb Gutsy
2. 80gb Windows
3. 60gb Feisty
Doesn't boot (no errors, just nothing happens)[/COLOR]
--------------------------------------
[COLOR="SeaGreen"]1. 160gb Gutsy
2. 60gb Feisty
3. 80gb Windows
Doesn't boot (no errors, just nothing happens)[/COLOR]
--------------------------------------
[COLOR="Blue"]1. 60gb Feisty
2. 80gb Windows
3. 160gb Gutsy
Comes up with 'GRUB' on the bottom (after bios hardware lists, etc), and stops there. Doesn't display version, the dots or the list - just hangs there.[/COLOR]
--------------------------------------
[COLOR="Blue"]1. 60gb Feisty
2. 160gb Gutsy
3. 80gb Windows
Comes up with 'GRUB' on the bottom (after bios hardware lists, etc), and stops there. Doesn't display version, the dots or the list - just hangs there.[/COLOR]
--------------------------------------


Can someone please solve this puzzle, or otherwise tell me what to do, in order to boot into Gutsy on the new comp, with the Feisty HD being plugged in, so that I can copy stuff from it?

Thanks!

---

### Post by confused57 on 2007-09-27
About the only thing I could suggest is to try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

SGD might be able to boot your Gutsy drive(with 3 drives connecte)...if so, you may be able to mount your Feisty  partition(s) to copy files.

---

