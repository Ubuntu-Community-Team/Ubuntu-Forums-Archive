---
title: "Ubuntu after INstall how to start it ???"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by JOKe on 2005-07-07
i installed ubuntu and i say TO INSTALL GRUB TO MBR but there is no grub the fucking xp is booted on start up ... so .. ? how can i boot the ubuntu to make grub install ??

---

### Post by amohanty on 2005-07-07
1. Pop in your install cd.
2. reboot
3. Enter CMOS setup provide CDROM as first boot device
4. Once installers screen comes up, select recovery and drop into recovery terminal.
5. use root and password
6. cd /boot/grub/
7. vi menu.lst
  7.1 Make sure 'hiddenmenu' has a '#' infront of it (ie commented out)
                 in vi: - navigate to hidden...
                         - a
                         - #
                         -<ESC>
  7.2 Make sure there is a reasonable number after 'timeout'
  7.3 Make sure 'default' is set to the number (starting from 0) of the ubuntu boot image. If its the first one listed after the comment ## ## End Default Options ## then use 0 or the relevant index.
  7.4 In vi: <ESC>:wq

8. Eject cd.
9. at the prompt: shutdown -r now


And hopefully if nothing else is screwed up you will see the nice little grub screen.

---

### Post by mingus on 2005-07-07
Umm . . . to add a few tweaks to the instructions above:  If you are using the installation CD, the boot command is "rescue".  You will be asked what partition root (/) is mounted on.  Then you will be dropped into a shell as root.  Very important:  If you created a separate partition for /boot, you must mount it.  Then #cd /boot/grub. 

The editing above is in the event that the grub menu has been hidden, which is one possibility.  There are others.  You can regenerate menu.lst with the #update-grub command.  You can then install grub to the MBR with the #grub-install command (defaults to MBR).

If this doesn't work, you probably have something a bit unusual in your configuration.  You'll need to post back the output of #fidsk -l, and files menu.lst, /boot/grub/device.map, and /etc/fstab.

PS.  Suggest care with the language.  This forum has strict rules re profanity.

---

