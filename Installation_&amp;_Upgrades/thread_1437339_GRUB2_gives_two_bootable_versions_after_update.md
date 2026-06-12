---
title: "GRUB2 gives two bootable versions after update"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by colourfullegume on 2010-03-23
Today, I used the Update Manager to do my first post-installation update of Ubuntu 9.10.

I have a multi-boot setup (Ubuntu / WinXP), using GRUB2.  Before the update, I had 5 options:

[INDENT] Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Home Edition (on /dev/sda1)
[/INDENT] 
After the update, there are an additional two at the top of the list:

[INDENT] Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
 Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Home Edition (on /dev/sda1)
[/INDENT] 
Is it valid that the -14- has remained in the list?  Surely I can only boot -20- now?  How should I get rid of this version since it is added by update-grub because of the existence of this file: /boot/vmlinuz-2.6.31-14-generic

Should I delete the file or just rename it?  Or is there a better way?

---

### Post by oldfred on 2010-03-23
We recommend that you keep two versions of the kernel as sometimes the new one will not work correctly with your configuration. Having the older one lets you boot. They do not take a lot a space but when you get a lot you can go into synaptic and uninstall the older ones and run sudo update-grub to remove them from the menu. Just be sure not to delete the one you are using or when you reboot you will not be able to boot.

Go to Synaptic Package Manager or Adept and search for linux-image.

---

### Post by lindsay7 on 2010-03-23
Leave it alone. That is just how the updates work. It leaves the old kernel there in case you have trouble booting into the new one. It is generally a good idea to just leave well enough alone it does not take up a lot of space and it is a good fall back.  If you are not booting into the latest version or want to change it. Download startup manager and you can set up your default startup option.

---

### Post by colourfullegume on 2010-03-24
Thanks oldfred & lindsay7.  The only problem was that I wanted to default to boot with Windows (for now ...) so I would have to keep updating the GRUB_DEFAULT every time I update, but I can live with that.  At least I know now that it's normal behaviour - I thought it would be impossible to boot into the older kernel.

---

### Post by lindsay7 on 2010-03-24
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu.  You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

### Post by colourfullegume on 2010-03-28
Thanks, lindsay7

I knew how to make the changes by editing **/etc/default/grub** (e.g., sudo nano /etc/default/grub) and then running **sudo update-grub**, but a GUI interface may come in handy for others reading this thread.

---

