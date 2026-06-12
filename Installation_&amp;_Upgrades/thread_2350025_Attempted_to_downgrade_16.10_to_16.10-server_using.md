---
title: "Attempted to downgrade 16.10 to 16.10-server using tasksel, and now I cannot boot"
date: 2017-01-20
forum: Installation &amp; Upgrades
---

### Post by johnjohnjohnjohn on 2017-01-20
Ok I messed up.  I should've started with "Server" but i didn't. 

I setup a Plex Media Server.  I have  2, 6TB drives.  One contains the OS, my transfer of my plex media server database and files from a Windows box, about 1TB of music and 500GB of pictures.  The 2nd drive is movies and whatnot.

I created /boot and / and swap upon install.  I allowed Ubuntu to partition it for me.  I did not do any manual partitioning.  

I ran into problems on this install, in getting it to boot.  They were solved in [this thread ]("https://ubuntuforums.org/showthread.php?t=2243715&page=2")

To save a click

> 
 mount /dev/sda1 /mnt
cd /mnt/EFI 

 mkdir -p Microsoft/Boot 

 cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi  

 sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi" 

 sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\Microsoft\Boot\bootmfgw.efi " 




and this fixed and I could boot.

Since then, I started ripping out lightdm, NetworkManager, and a number of services I just didn't need.   Then i remembered "tasksel".  And this is where I got in trouble.

I installed tasksel... I unselected the Ubuntu Desktop, selected the SSH Server and Samba Server (as i already had them installed)... and tasksel just went off uninstalling damned near everything.   It removed my ntfs drivers, it removed vim, I saw "grub" packages being removed.  I'm not really sure what's gone and what stayed.

But when I rebooted it obviously doesn't come up.

I get an error that states

vmlinux-4.8.0-32-generic.efi.signed not found


I'm comfortable booting off USB, mountaing and chrooting.  What do I need to do to get this backup and running?

I'd really prefer not to reinstall b/c i have a TON of infromation that lives outside of my home directory that I would have to backup (again..just ot make sure) and then restore.  And I'm really hoping to avoid that.  

Any help is greatly appreciated.

Thanks

---

### Post by oldfred on 2017-01-20
If it is not in /home, you can just reinstall. 
And there is a "dirty" install where you do not format / partition so everything that is not part of a new install is not overwritten. But configurations & entire system is updated.

The Desktop depends is just about the entire system. But I am a bit surprised it uninstalled grub.
If kernels & some of the system is there, you can use Boot-Repair to reinstall grub & newest kernel using Advanced mode.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I think Boot-Repair does a mini-chroot, and at that point you may be able to run some additional install commands.

If UEFI, you have to also mount the ESP, if /boot separate you have to mount it as well as / to do a chroot. Also some other system partitions are also required if in separte partitions.


 UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by johnjohnjohnjohn on 2017-01-23
Boot-repair bombed on me...but manually ran some installs and that fixed it.   Thanks a million.

---

