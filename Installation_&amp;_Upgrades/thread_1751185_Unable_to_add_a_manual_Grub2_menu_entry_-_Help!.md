---
title: "Unable to add a manual Grub2 menu entry - Help!"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by markofealing on 2011-05-06
Having just upgraded to Ubuntu 11.04 from 10.10 I noticed that my Grub menu had not upgraded. 

The upgrade was not as straight forward as it should have been as the PC hung at the end of the installation resulting in a reboot and running dpkg in safe mode to get it all back up and running.

To fix the incorrect grub menu.lst file which was not updating, I renamed the original file and then ran **sudo update-grub**. It generated a new and correct file.

However, my Windows partition was not listed as a Grub menu option.

Entering sudo os-prober reported back that one did exist:

*/dev/sda1:Microsoft Windows XP Professional:Windows:chain*

but following this with an **update-grub** command made no difference to the Grub menu.

I noticed that my /etc/default/grub file was missing so copied this over from another Ubuntu PC.

I then followed [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) on manually adding a Windows menu entry to Grub2.

I created a file called 11_windows, gave it  +x permissions and added the following lines

#!/bin/sh -e
echo "Some string"
cat << EOF
menuentry "Windows" {
set root=(hd0,1)
chainloader (hd0,1)+1 
}
EOF 

Then did a update-grub. No entry was added which suggests to me that something is fundamentally wrong with Grub2 on this computer.

Other than trashing the Ubuntu installation and starting afresh, I've now run out of ideas as to what is preventing me from manually adding an entry in Grub2.

Thanks

---

### Post by lechien73 on 2011-05-06
Hi,

Maybe you should run bootinfoscript ([http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)) and post the results here between [CODE] tags. Grub2 doesn't have a menu.lst file, so it may be that you have a mix between legacy grub and grub2.

---

### Post by markofealing on 2011-05-07
Thanks to the link for the script, will give it a try.

Grub2 does still use the menu.lst file which is stored in /boot/grub.

The difference is that you are no longer supposed to edit it as it gets created on the fly when you do a update-grub.

---

