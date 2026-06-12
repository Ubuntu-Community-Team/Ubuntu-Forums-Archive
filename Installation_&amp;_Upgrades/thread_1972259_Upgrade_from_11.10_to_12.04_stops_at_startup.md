---
title: "Upgrade from 11.10 to 12.04 stops at startup"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by kabeza on 2012-05-03
Hi
I've got an alternate x64 Ubuntu 12.04 cdrom
I inserted into my 11.10 clean install and started the upgrade process.

1) All went fine until it seemed it would restart and then I got the wallpaper and mouse cursor only for long time without cdrom reading nor disk led blinking so I suspected no activity and resetted PC

2) When restarted, it boots, shows Ubuntu splash and then gets hang at some startup command: "starting cups/printing spooler server [OK]" and then nothing happens.

Will "repair system" option from CD (at cdrom booting) delete any of my files or /home folder?

Any other suggestion?

PS: the upgrade indeed was done because /etc/lsb-release shows 12.04

PS: I can login into commandline (alt-F2) and can also see my files in /home/xxx

Thanks

---

### Post by oldfred on 2012-05-03
If you can login to command line, then it sounds like a video issue. What video card do you have.

You also should be able to boot into recovery mode and update system from that.

Often nomodeset on grub works. Sometimes it is other boot option settings.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu if nVidia is your video card.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by kabeza on 2012-05-03
My video is an on-board Intel, worked perfect on 11.10. I removed the NVidia card and never put it back since I did the clean 11.10 installation.

When I press shift before boot, I get a message

"boot:" and as I've read, I should write "rescue" and press enter?

**EDIT: SOLVED WITH. **
1) Shift at boot, selected the Ubuntu 12.04...."repair mode"
2) Run the repair damaged packages
3) Run the "repair damaged system" option from bootCD, reinstalled grub, 
4) reboot
5) working

---

