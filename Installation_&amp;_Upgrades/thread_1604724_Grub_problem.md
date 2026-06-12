---
title: "Grub problem"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by chris0108 on 2010-10-24
Hi there, 
     Iv been using ubuntu on my laptop for just over a year now and thought it about time my desktop got the same. I cant get rid of the vista section of the disk because of things i have on there so a friend gave me a spare 80gb hard drive to have a play with it and go from there. So first of all installed unbuntu 10.10 on the hard drive alls fine i can boot into both vista and ubuntu, i then want to install backtrack 4, so i booted the backtrack disc and off we went, i split the 80gb hard drive in two and installed backtrack to one section, now i cant boot to anything other than backtrack. I got an option for ubuntu although this does look different now (showing up as 'ubuntu, with linux 2.6.35-22-generic-pae') when i go to this option i get the message "error 15:file not found"
I also have the option for other operating system, i get this message when i choose this option "error 11: Unrecognized device string"

I have googled this problem but the only solution i could find was booting with a live disc, open a terminal and type sudo grub, but this does nothing at all??

Can anyone help me please? 
Many thanks Chris

---

### Post by oldfred on 2010-10-24
You probalby need to reinstall Ubuntu's grub2 to the MBR. But to see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

