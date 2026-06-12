---
title: "Ubuntu getting I/O errors after resizing partition from max to somepart using livecd."
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by bhaskar5 on 2014-11-04
Hi,

I have Ubuntu now(from longtime) and tried to install Windows on it to decrease the effort of taking backup.  

So, I created livecd(pendrive) with Ubuntu and restarted ubuntu and using live ubuntu, I resized the partition with below steps:  

    boot to live cd(pendrive)
    open gparted  
    Right click currently fully occupied(I think /dev/sda1) having 500GB (380GB unused) and clicked resize and changed 480gb value to 380gb and submitted.   
    Thats it I didnt make any other changes.  

Before doing this, I used winusb to create bootable from windows and it worked(setup started successfully).  
But, after this, windows setup couldnt start with some errors status ending with  0001.  

Ok, if necessary we can leave windows installation but currently many things not working.  
I tried to open Skype and it says 'some i/o error when I tried to login'.  
I put pendrive and it says some error and the same pendrive working in another laptop. 

**UPDATE**:
After implementing below command
sudo fsck.ext4 -f /dev/sda1errors fixed. I was able to use well.  
But, still i was unable boot usb with windows setup. Also, i tried using virt-manager, it also says some grub errors.  How can I fix this grub issue ?

Please let me know how to fix this. If necessary, I am ready to take backup and install windows again but even pen drive not being detected to backup files.  
Please let me know for any questions.

---

