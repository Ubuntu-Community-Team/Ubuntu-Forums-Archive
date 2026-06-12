---
title: "VirtualBox - CANT CONVERT .BIN TO .VDI"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by novus721 on 2007-10-28
I recently gave up on vmware since I am tired of dealing with the nonsense associated with it. I am *desperatly* trying to get VirtualBox up and running, mainly using this as my guide

[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool)

After converting my .vmdk to a .bin, I have to convert the .bin to a .vdi by invoking this command
> LD_LIBRARY_PATH=/opt/VirtualBox* ./vditool DD new-file.vdi old-file.bin


And whenever I try to do it myself, this is my result:
> jj@ubuntu-desk:~$ LD_LIBRARY_PATH=/opt/VirtualBox* ./vditool DD /media/disk/VirtualBox/WindowsXP.vdi /media/disk/VirtualBox/XPro.bin
./vditool: error while loading shared libraries: VBoxDD.so: cannot open shared object file: No such file or directory


I have tried making the file names agree, switched their positions (though I believe what I have is correct even though it seems counter-intuitive), done it from root etc etc with no end in sight. I would GREATLY appreciate any help, thank you all very much!

---

### Post by scrivener on 2007-10-29
I had the same problem.  According to the VirtualBox manual they incorporated this into the VBoxManage command line tool.  You can run VBoxManage from the command line without any arguments to get a list of functions.

If all you want to do is convert a BIN to a VDI, try this from the command line:

> vboxmanage convertdd rawfile.bin rawfile.vdi

Or in your case:

> vboxmanage convertdd /media/disk/VirtualBox/XPro.bin /media/disk/VirtualBox/WindowsXP.vdi

---

### Post by dvo on 2008-04-01
How to convert WinXP.vmdk to WinXP.dvi

The usual way via "qemu-img convert" did not work on my installation
(Ubuntu 7.10 Gutsy; qemu 0.9); it just produced a not bootable image.
I successfully used Partition Magic instead:

1. In the VirtualBox main window, choose File -> Virtual Disk Manager -> New
   to create a Dynamically expanding image (say, WinXP.vdi) that 
   is nominally at least as large as the disk you want to convert.

2. For a VBox virtual machine which has the old existing VMDK (WinXP.vmdk)
   as the boot hard disk, attach the new image (WinXP) as a slave hard disk.

3. Boot the system and use Partition Magic to copy the old disk to the new one
   (PM may complain that the new partition is not bootable - don't worry.)
   PM will require a reboot and may fail after copying - still the copy is fine.

4. Shut down the virtual machine, detach the WinXP.vmdk, 
   attach the WinXP.dvi as the new boot disk, then try booting the new image.

5. Optionally, to compact the new disk, follow the instructions 
   in [http://murga-linux.com/puppy/viewtopic.php?t=21797](http://murga-linux.com/puppy/viewtopic.php?t=21797) - in a nutshell:
   On the WinXP command prompt, execute "dirms c", then "sdelete -c c:"
   then shut down the virtual machine 
   and execute "VBoxManage modifydvi WinXP.vdi compact" on the host.

---

