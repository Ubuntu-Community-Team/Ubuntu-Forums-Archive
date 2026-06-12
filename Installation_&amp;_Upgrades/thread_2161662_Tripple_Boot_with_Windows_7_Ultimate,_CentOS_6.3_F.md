---
title: "Tripple Boot with Windows 7 Ultimate, CentOS 6.3 Final and  Ubuntu 13.04"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2013-07-11
Hello All,

          May this be helpful to you all. I have on my system Windows 7 Ultimate Installed along with Ubuntu 13.04.And ubuntu 13.04 support Grub2. Now when i installed CentOS 6.3,the grub(Not Grub2 as compared to ubuntu  13.04) got installed as bootloader erasing ubuntu 13.04 grub2 boot loader.When i saw the boot screen,only CentOS and Windows 7 are Listed as it is obvious the Ubuntu 13.04 was left out in the entry,which made ubuntu unbootable.Since i don't have ubuntu rescue DVD.I modified the CentOS's Grub and added ubuntu entry to boot up already installed ubuntu.It did booted up to ubuntu, but the x windows was just flickering. I entered into the terminal Alt+Ctrl+F3 combination(GUI window  Flickering) and logged into ubuntu terminal as root and re-installed   grub like grub-install /dev/sda.So now ubuntu grub2 is installed and it did not picked up the Installed CentOS to display in the Ubuntu Grub2 Bootloader Menu.So i have to enter manually a CentOS Boot menu to the Grub2 of ubuntu 13.04.This is how i did it

```

NOTE string after '#' is comment only for your explanation,you can safely delete the string starts with hash '#'

menuentry "CentOS 6.3 Final 64 Bit" 
{
        # hd0 denotes first hard disk and  number '8' denotes the HD Partition where i have installed CentOS...This can be different for you...use fdisk to findout
        set root='(hd0,8)' 
        #The below lines AFTER 'linux' is copied from CentOS 6.3's Grub config file--->menu.1st
	linux /boot/vmlinuz-2.6.32-279.el6.x86_64 ro root=UUID=5192aa99-bafc-4df1-ab1f-e49249d45b5c rd_NO_LUKS rd_NO_LVM LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16  KEYBOARDTYPE=pc KEYTABLE=us rd_NO_DM rhgb quiet

        #The below lines AFTER 'initrd' is copied from CentOS 6.3's Grub config file--->menu.1st
       initrd /boot/initramfs-2.6.32-279.el6.x86_64.img       
}

```

Make a BACKUP copy of this menu configuration as when grub is updated via internet,we have to add this lines manually.

That's all !! This works perfect for me.

Comments,Corrections or Updates are welcome

---

