---
title: "ubuntu Grub did not appear after installing ubuntu over windows7 (for dual boot )"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by devesh2408 on 2011-03-08
i have made 4 partition in my system,
1 reserved for system 100 mb
2nd 60gb ext4 for ubuntu (mount point /)
3rd 4 gb as a swap
4th 240 gb for windows
first i have installed windows7.
then i was installing ubuntu 10.10 64 bit, i have given boot location to hd0,1, i.e in 60 gb space .
but after complete installation of ubuntu when my system got restarted it is showing only window7, no login screen is coming for grub menu.
can any help me in this regard that what went wrong during installation.

---

### Post by oldfred on 2011-03-08
hd0,1 in grub2 is sda1. In grub legacy it would have been sda2. If you create the NTFS partition in advance win7 does not have to have a 100MB boot partition. It normally has that so users can encrypt the main install.

Post this, so we can see what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

