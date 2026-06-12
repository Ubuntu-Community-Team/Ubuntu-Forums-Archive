---
title: "vga792 is deprecated"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2009-11-30
Since installing 9.10, when I boot up I the following message appears briefly just after I select Ubuntu from the boot menu:```
vga=792 is deprecated. Use set gfxpayload=1024x768x24,1024x768 before linux command instead. 
```Does anybody know what's going on here?  Everything seems to work fine, but I'd like to get rid of this message, so that if another error message appears someday, I notice it.

---

### Post by Mark Phelps on 2009-12-01
I'm surprised none of the GRUB2 "experts" have responded, and since I'm NOT one of those, I can't give you detailed instructions ... but the gist of this is that in your GRUB options, you are trying to set the resolution of 1024x768 using an old "vga=nnn" parm.

You can confirm this by looking at your grub.cfg file, reading the Ubuntu entries, and noticing the presence of "vga=nnn" parms.

Fixing this requires going to the default GRUB file (sorry, I don't have the name handy) and changing the default resolution there to 1024xsd768 and saving that file.  Then, run "update-grub" to regenerate the cfg file.  Open the cfg file and confirm that the "vga=nnn" parms are gone.

---

### Post by darkod on 2009-12-01
The file with grub defaults is /etc/default/grub I believe. You will need to open it with:
sudo gedit /etc/default/grub

---

### Post by Ubuntist on 2009-12-02
Thanks, dudes.  In /etc/default/grub I changed```
GRUB_CMDLINE_LINUX=" vga=792 splash"
```to```
GRUB_CMDLINE_LINUX="gfxpayload=1024x768x24,1024x768 splash"
```and now all is sweetness and light.

---

### Post by Ronalddig on 2011-07-30
I followed the same thing yet its not working . i get same msg on boot. any solutions?

---

### Post by hcs7dap on 2011-07-30
Am quite a noob... so am quite nervous about giving advice.

However, I thought that to edit grub you have to use gksu (ie root access) and then run update-grub for the changes to take effect.

I had an issue with VGA=789 (now solved)... [http://ubuntuforums.org/showthread.php?t=1582540](http://ubuntuforums.org/showthread.php?t=1582540)

---

### Post by Razlo on 2011-08-19
If it helps, I'll post my running valid configuration. Note that grub_cmdline_linux is commented.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX="1024x768x32"
GRUB_GFXPAYLOAD_LINUX=1024x768x32
GRUB_GFXMODE=1024x768x32
```

I guess it's almost the same, but if anybody needs to try alternatives, this one works. **gfxmode** only changes grub resolution, and **gfxpayload_linux** I guess that only changes system non-graphic resolution, that is tty, and booting and shutdown screens.

Cheers!

EDIT: And don't forget that the resolution you enter must be supported by your driver! You will know the avaiable ones with a grub command. To access grub console, reboot, go to the SO selection screen and press **c**. The command is **vbeinfo**. They'll be printed in the screen. To set vbe_mode to configuration 0x101: **set vbemode=0x101**. Anyway, I think that this variable is listened by anybody.

EDIT2: Finally, there is a graphical tool called **startupmanager**. Haven't tried it, but it seems to let us choose the resolution.

---

