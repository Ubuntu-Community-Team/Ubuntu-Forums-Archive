---
title: "Ubuntu 9.10 overwrites grub"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by cesy on 2009-12-12
I just installed a copy of Ubuntu 9.10 on a partition on my desktop. It didn't ask me anything about grub. When I restarted, I found it had replaced my normal grub (which I had carefully set up - I have several different systems on this computer) with Grub2, with no apparent way to get back.

Firstly, how can ubuntu justify overwriting something like this without even giving the user an option?

Secondly, how can I undo it?

---

### Post by darkod on 2009-12-12
The option is in Advanced options (the button) in the last screen, before clicking the Install button. You can disable installing bootloader there.
Depending which OSs you have, grub2 should pick them up. If you would like to go back to your old grub, I guess it would be easy to restore it and you still have your menu.lst and stage1 where ever they were.

---

### Post by cesy on 2009-12-12
I went through the advanced options when I was telling it which partition to install on, and I didn't see that option.

It is not easy to restore it, and it's not picking up the right options, because my grub is on a different drive to the rest of my system, I had it carefully set up to deal with the fact that my main hard drive isn't bootable with this motherboard, and there's another hard drive I swap in occasionally. Can you tell me how to set the boot settings to point back at my old grub? It's a long time since I set it up. I just want to revert the changes the Ubuntu made.

---

### Post by darkod on 2009-12-12
Hmmm... you're telling ubuntu where to install in step 4, and the advanced options about grub2 are available in step 7 so I'm confused a bit.
For steps how to restore grub1 look here (second option, for 9.04 or before, that was using grub1):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You could do it from 9.04 cd or earlier, but not with 9.10 cd (that has grub2 in it). Where did you get grub1 last time? You can probably use that to restore too.

---

### Post by presence1960 on 2009-12-12
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

