---
title: "black screen after reboot with new vmlinux in virtual box 4.2"
date: 2015-07-08
forum: Installation &amp; Upgrades
---

### Post by zerop2 on 2015-07-08
would like to try kgdb debugging

black screen after reboot with new vmlinux

and reset again , kernel panic, no working init found



virtual box 4.2
[https://github.com/regit/regit-config/blob/master/virtualbox/config-3.5-vbox](https://github.com/regit/regit-config/blob/master/virtualbox/config-3.5-vbox)


mkdir /home/hello/kernel
cd kernel
git clone [https://github.com/torvalds/linux.git](https://github.com/torvalds/linux.git)
cd linux
cp ~/config-3.5-vbox /home/hello/kernel/linux/.config
make mrproper
make O=/home/hello/kernel menuconfig
make O=/home/hello/kernel
cd ..
sudo make modules && sudo make modules_install
sudo make install

sudo cp /etc/default/grub /etc/default/grub.bak
sudo gedit /etc/default/grub


replace
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
with
GRUB_CMDLINE_LINUX_DEFAULT="kernel /vmlinux ro root=LABEL=/ rhgb quiet crashkernel=128M@16M kgdbwait kgdboc=ttyS0,115200"

and

sudo rm /vmlinuz
sudo rm /initrd.img
sudo ln -s /boot/vmlinux-4.2-rc+ /vmlinuz
sudo ln -s /boot/initrd-4.2-rc+.img /initrd.img

sudo shutdown -h now

---

