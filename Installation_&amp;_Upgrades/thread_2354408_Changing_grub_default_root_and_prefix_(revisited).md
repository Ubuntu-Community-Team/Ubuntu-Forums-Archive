---
title: "Changing grub default root and prefix (revisited)"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by shoemakerlevy9 on 2017-03-02
Hi,

I am having the same issue as a previous post that was never answered, but I have a unique situation. I have Ubuntu 14.04 installed in legacy mode and Win10 installed as UEFI. 
I did it this way because I was struggling to get both installed as UEFI, then I ended up liking the setup case it boots straight into an OS. To change OS's I just change the BIOS mode :) I know you can do the same thing with grub but hey, it was pretty easy to do it this way.

Link to older post
[https://ubuntuforums.org/showthread.php?t=2164519](https://ubuntuforums.org/showthread.php?t=2164519)

Other Similar (but slightly different) Posts
[http://askubuntu.com/questions/119597/grub-rescue-error-unknown-filesystem](http://askubuntu.com/questions/119597/grub-rescue-error-unknown-filesystem)
[https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux)

In my case my Ubuntu partition was (hd0, gpt5) and now its (hd0,gpt7) so I have to type
    ```
set prefix=(hd0,gpt7)/boot/grub
set root=(hd0,gpt7)
insmod normal
normal
```

...everytime I boot



Here is what I have tried so far

**1) Update Grub**
```
$ update-grub
$ grub-install /dev/sda
```
...no effect

**2) Boot Repair**
Selecting [Recommended Repair] yields the following error:
> The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.
I have run Boot-info and attached the output

---

### Post by oldfred on 2017-03-02
You have the very new NVMe type drives.
I am sure a newer version of Ubuntu would be better as older version probably was before NVMe was supported or fully supported.
And you need to be sure to install in UEFI boot mode, not BIOS/CSM/Legacy boot mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570) 
    
You may also have to upgrade your UEFI/BIOS to newest available from your vendor.
What brand/model system?

       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570) 
   Asus NVMe issues - not solved UEFI/BIOS issue?
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
[http://ubuntuforums.org/showthread.php?t=2325056](http://ubuntuforums.org/showthread.php?t=2325056) 
            Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22)
[https://ubuntuforums.org/archive/index.php/t-2292993.html](https://ubuntuforums.org/archive/index.php/t-2292993.html)
> I finally got my 2 SM951's dual booting Win10 and Ubuntu 15.10....and what a pain it was. 



---

### Post by LostFarmer on 2017-03-02
> update-grub
grub-install /dev/sda You are useing sudo before each command ?  The 2nd command is wrong for your hdd. it should be 
```
sudo grub-install /dev/nvme0n1
``` .    I would change the install to EFI per oldfred's post but if it works in legacy mode boot mode then .

---

