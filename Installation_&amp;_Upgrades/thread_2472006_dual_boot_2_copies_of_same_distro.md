---
title: "dual boot 2 copies of same distro"
date: 2022-02-15
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2022-02-15
I am currently using lubuntu 20.04.3. I want to install a second lubuntu 20.04.3 on my system. The second install would be to experiment with things like different DE, config settings, etc, without concern for my primary install. If things go sideways, I can simply reinstall with no loss of data files. To keep the systems easy to identify, I would change name of second install to 'experimental' in the grub menu. Is this possible. I run lubuntu only, no other distro or windows currently install, and more space than I would need for this. I just want to be able to deep dive into things without the fear of borking my system. Thanks for the help, you guys are the best.

---

### Post by oldfred on 2022-02-15
Second install control will be grub in control. You can easily change it back, by booting into main working install and reinstalling grub.
Or if Ubuntu use ubiquity -b which does not install any grub boot loader and manually add your own boot stanza to current install's 40_custom.
You then can name it anything you want and make a boot stanza that is generic so if kernel updated, you do not have to edit boot stanza.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Posted several examples of configfile type entry, but that requires grub in other install as it loads grub menu from that install.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by coley9225 on 2022-02-15
oldfred, thanks for the response. I always have to install without grub, my computer will not allow the grub to install in a normal fashion. If I install a second disto, at the prompt to reboot, I boot into existing lubuntu and update grub, then I can reboot and use new install. As far as the renaming, I use grub customizer, and I find it to work well for my purposes. I just wanted to make sure there wouldn't be some sort of conflict, or 'confuse' my computer(after all it is just a box). The lubuntu installer uses calamares installer, but in thee app menu is an option to install file system. Just acknowledge the absents of the bootloader, and install will continue normally, like the ubiquity -b method.

---

### Post by SeijiSensei on 2022-02-15
An easier option might be to create a virtual machine with KVM and install the second copy there.  Then you can work on both at the same time rather than needing to reboot.

---

