---
title: "ubuntu upgrade 12.10 to 13.04 stuck at splash screen"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by hdavid7 on 2013-06-14
Hi, 

I upgraded from 12.10 last night 13.04 and the upgrade went fine until I did the reboot. Laptop now gets stuck at splash screen on boot. Just before it gets to the splash screen I get errors about CIFS mount failing, it then hangs. If I boot into recovery mode and attempt to use the options for repairing packages or fsck I get more mount all errors and the laptop hangs. Googling gives results for other versions of ubuntu stuck at splash screen but the fsck command fixed their options. Or their issue was on shutdown, not booting. I am able to boot into windows without any issue. Any suggestions would be greatly appreciated.

Laptop details:
Hp elitebook 8570w
Dual boot with windows 7

Using the recovery mode option, I entered into a root console and ran fsck -c -f /dev/sda6 manually. It took 30 minutes but did not find any problems. The other sda partitions didn't have errors either but exited.immediately as they we not all file-systems. Left image is just before splash screen, right is the error when I run any of the recovery mode options.
[ATTACH=CONFIG]243800[/ATTACH][ATTACH=CONFIG]243801[/ATTACH]

Kind Regards,

hdavid7

---

### Post by 2F4U on 2013-06-14
The second screenshot suggests that your home folder may be on a Samba share. Is that correct? If the share is not mounting, that may explain the boot problems. If your home folder is not on Samba, try to deactivate the Samba mount points and see if the machine boots.

---

### Post by hdavid7 on 2013-06-14
Hi 2F4U, 

Thanks for that, I edited /etc/fstab and commented out the smb mount. It was just a folder on my home network. I had to use [COLOR=#000000][FONT=Verdana]mount -o remount,rw / [/FONT][/COLOR]from [http://www.linuxquestions.org/questions/linux-general-1/cannot-edit-fstab-in-recovery-mode-filesystem-is-read-only-540195/](http://www.linuxquestions.org/questions/linux-general-1/cannot-edit-fstab-in-recovery-mode-filesystem-is-read-only-540195/) so I could edit fstab in recovery more. Now my laptop boots to the splash screen w/o the mount errors but still freezes. The "KVM disabled by bios" still comes up.

---

### Post by hdavid7 on 2013-06-15
I wasn't able to fix problem without doing a re-install of ubuntu 13. I actually had to do two re-installs as the first re-install froze on restoring packages. The laptop now works great and boots w/o any issues.

---

