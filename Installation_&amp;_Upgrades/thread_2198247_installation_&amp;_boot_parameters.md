---
title: "installation &amp; boot parameters"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by allen-biggins on 2014-01-07
I'm looking for a document that can explain what the installation and/or boot parameters are, what they do, which ones shouldn't be used and how does one check to see what parameters are in use.

Thanks

Allen

---

### Post by tfrue on 2014-01-07
You can read the man pages or look online for GRUB2. Also, you can check out how the MBR and GPT works with Linux and in general. But there is a bounty of information for all three so be ready to learn. Be sure that when you look up info for grub2, that you are looking at grub2 info, not the original grub, also know as legacy grub, because the way the grub2 works is different and mixing the two will be bad. Trust me, I did this lol.

---

### Post by oldfred on 2014-01-10
Some info:
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Your boot parameters would be in grub.
cat /etc/default/grub

use q to exit:
       
  info -f grub -n 'Simple configuration'

Usually added to this line:

 GRUB_CMD_LINUX_DEFAULT="quiet splash"
or this:
GRUB_CMDLINE_LINUX=""

---

### Post by grahammechanical on 2014-01-10
Here where you can download the Grub manual from

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Also, if you select a Grub boot option at the Grub menu and press E then you will put Grub into Edit mode and that will reveal the boot parameters. Press Esc to go back to the Grub menu.

Regards.

---

