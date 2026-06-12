---
title: "Where did my boot menu go? :("
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Sinopa on 2011-02-25
I just did a boo boo :(

I installed Windows XP on an empty partition (don't ask why I did such a stupid thing) and now I can't boot back into ubuntu. My Grub is all gone and I miss it.

How I can restore my grub? And how can I restore it and add Windows Xp to it? 

Please heeeeelp me.... Oh The Agony...

---

### Post by auroraa9420 on 2011-02-25
> **Sinopa said:**
> I just did a boo boo :(

I installed Windows XP on an empty partition (don't ask why I did such a stupid thing) and now I can't boot back into ubuntu. My Grub is all gone and I miss it.

How I can restore my grub? Please heeeeelp me.... Oh The Agony...

try runing a live CD and backuping the files from the ubuntu disk and then reinstaing on your partition and put the old files back :P

(when i say files i mean your /home folder, the rest can be restored :S)

---

### Post by oldfred on 2011-02-25
Any install of windows automatically updates the MBR with the windows boot loader. You just need to reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


If you need specific instruction, post back and we can give you them for your configuration with this info:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

