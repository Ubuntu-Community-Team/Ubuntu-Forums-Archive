---
title: "black screen while installing"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by jasonlfunk on 2011-09-15
Hello,

I am trying to install ubuntu natty onto a Zotac Zbox. I have made a Live USB stick and it boots from it. I get the menu to select my language and then choose "Install Ubuntu Server" then the screen turns black and doesn't change. I know that the USB image is good because I've used this same stick to install on a different system. 

I've tried both the Server version and the Alternate and both do the same thing.

Any ideas?

---

### Post by MAFoElffen on 2011-09-15
> **jasonlfunk said:**
> Hello,

I am trying to install ubuntu natty onto a Zotac Zbox. I have made a Live USB stick and it boots from it. I get the menu to select my language and then choose "Install Ubuntu Server" then the screen turns black and doesn't change. I know that the USB image is good because I've used this same stick to install on a different system. 

I've tried both the Server version and the Alternate and both do the same thing.

Any ideas?
Your box uses an NVidia Chipset... Boot the Server install CD and use a "nomodeset" kernel boot option (F6 at the the install main boot screen > arrow down to nomodeset > spacebar to select > <esc>>) before you select thei"Install" menu item.

Refer to post 3 of this sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

