---
title: "fix boot scren Plymouth script"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by d0rkye on 2010-07-20
I put together a script for easily fixing the boot screen resolution in lucid lynx. I post it her so maybe it will help someone.

```
#!/bin/bash
# ----------------------------------
# Author: D0rkye
# Homepage: http://d0rkye.zsenialis.com/
# ----------------------------------
sudo apt-get install v86d hwinfo -y
sudo hwinfo --framebuffer
echo "---------------------------------------------------------------"
echo "Please enter the best resolution from the list above"
echo "It usualy looks like this >>Mode 0x0323: 1024x768 (+4096), 24 bits<<"
echo "And you have to enter it like this >>1024x768-24<<"
echo "---------------------------------------------------------------"
read resolution
sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/grub > ./newgrub
sudo mv -f ./newgrub /etc/default/grub
sed 's/\#GRUB\_GFXMODE\=640x480/GRUB\_GFXMODE\='$resolution'/g' /etc/default/grub > ./temp
sudo mv -f ./newgrub /etc/default/grub
sudo echo "uvesafb mode_option=$resolution mtrr=3 scroll=ywrap" >> /etc/initramfs-tools/modules
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub2
sudo update-initramfs -u
echo "The resolution should be fixed afther a reboot"

```

---

### Post by K.Mandla on 2010-07-23
Moved to Installation and Upgrades.

---

