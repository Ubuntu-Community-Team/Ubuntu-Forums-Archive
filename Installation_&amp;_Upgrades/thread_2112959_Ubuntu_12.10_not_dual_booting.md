---
title: "Ubuntu 12.10 not dual booting"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by deadpool15 on 2013-02-06
1. I installed Ubuntu 12.10 with windows 7 already installed.
2. I installed Ubuntu with live USB.
3. After successful installation, I restart it, and it automatically boot to windows 7, there is no GRUB menu.
4. I use Boot Repair from Ubuntu Secure Remix, but still no GRUB menu, it just boot to Windows 7.
5. Here is the report page [http://paste.ubuntu.com/1615848/](http://paste.ubuntu.com/1615848/)

Note: Everytime I boot into Ubuntu Secure Remix by live-usb, I had to replace "Quiet Plash" with "nomodeset" in the entry, and then I was able to get into Ubuntu to perform Boot repair.

HELP!

---

### Post by dino99 on 2013-02-06
boot on the livecd, then open a terminal and run:

sudo grub-install /dev/sda
sudo update-grub

---

### Post by PowerBarry43 on 2013-02-06
Hi

For recovering from a livecd, booting and reinstalling grub isn't sufficient, you need to chroot into your actual ubuntu install.

from the livecd we run:

```
mkdir /mnt/root
sudo mount -t ext4 /dev/sda1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub-install /dev/sda
sudo update-grub
exit
sudo init 6

``` 

you may have to replace sda1 with the name of your / ubuntu partition, this will depend on what you set it as when you first installed.

Hope this helps!

Barry

---

### Post by oldfred on 2013-02-06
Boot-Repair says it installed grub to the MBR. Is it still booting Windows?

If you needed nomodeset to boot liveCD/DVD/Flash then you will need it on first boot with grub. 
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    
       On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

    
With 12.10 I had to install headers before installing nVidia proprietary drive to get it to install correctly.
       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    
       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by deadpool15 on 2013-02-06
> **oldfred said:**
> Boot-Repair says it installed grub to the MBR. Is it still booting Windows?

If you needed nomodeset to boot liveCD/DVD/Flash then you will need it on first boot with grub. 
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    
       On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

    
With 12.10 I had to install headers before installing nVidia proprietary drive to get it to install correctly.
       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    
       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

Yes it still boot to windows. I will try PowerBarry's suggestion, and I'll report back.

---

### Post by deadpool15 on 2013-02-06
> **PowerBarry43 said:**
> Hi

For recovering from a livecd, booting and reinstalling grub isn't sufficient, you need to chroot into your actual ubuntu install.

from the livecd we run:

```
mkdir /mnt/root
sudo mount -t ext4 /dev/sda1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub-install /dev/sda
sudo update-grub
exit
sudo init 6

``` 

you may have to replace sda1 with the name of your / ubuntu partition, this will depend on what you set it as when you first installed.

Hope this helps!

Barry

when I typed in "sudo grub-install /dev/sda" i get this.....

root@ubuntu:/# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
source_dir doesn't exist. Please specify --target or --directory

---

### Post by oldfred on 2013-02-06
They instructions are basically correct to chroot, but you must use the partition with your Ubuntu install or sda5, not sda1 as posted as an example.

So change this:
sudo mount -t ext4 /dev/sda1 /mnt/root
to this
sudo mount -t ext4 /dev/sda5 /mnt/root

---

### Post by deadpool15 on 2013-02-06
> **oldfred said:**
> They instructions are basically correct to chroot, but you must use the partition with your Ubuntu install or sda5, not sda1 as posted as an example.

So change this:
sudo mount -t ext4 /dev/sda1 /mnt/root
to this
sudo mount -t ext4 /dev/sda5 /mnt/root

That's what I did, and I continue on until I reach the install-grub code and it give me that error. Here's my partition table:

/dev/sda
   /dev/sda1 ntfs
   /dev/sda2 ntfs
   /dev/sda3 ntfs
   /dev/sda5 ext4
   /dev/sda6 swap

my ubuntu partition must be the sda5 ext4 right?

---

### Post by oldfred on 2013-02-06
Did you use sda5 as the mount point in the chroot list of commands?

But Boot-Repair said it worked. So you must have some issue?

Do you have a BIOS with a security setting or built in virus checker that prevents writing to MBR? A few systems have that.

       BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker

            Disable Quickboot in BIOS

---

### Post by deadpool15 on 2013-02-06
> **oldfred said:**
> Did you use sda5 as the mount point in the chroot list of commands?

What do you mean by this? I just follows Powerbarry suggestion:

mkdir /mnt/root
sudo mount -t ext4 /dev/sda5 /mnt/root ---- I replaced sda1 with sda5
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub-install /dev/sda
 ..... there's no error until I reached grub-install /dev/sda

I don't recall seeing any security setting in the bio but I will check again.

---

### Post by darkod on 2013-02-06
> **deadpool15 said:**
> What do you mean by this? I just follows Powerbarry suggestion:

mkdir /mnt/root
sudo mount -t ext4 /dev/sda5 /mnt/root ---- I replaced sda1 with sda5
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub-install /dev/sda
 ..... there's no error until I reached grub-install /dev/sda

I don't recall seeing any security setting in the bio but I will check again.

The instructions are slightly wrong. The last two lines before 'exit' don't need sudo in front. When you execute the sudo chroot ... you are already inside as root so you don't need sudo. The following two lines should be only:
```
grub-install /dev/sda
update-grub
```

---

### Post by deadpool15 on 2013-02-06
I check my bios setting but I don't see any secure boot option.
I have tried grub-install /dev/sda without the sudo but it's still getting the error: source_dir doesn't exist. Please specify --target or --directory.

---

### Post by deadpool15 on 2013-02-06
Ok, I finally got it solved! I googled and found this thread [http://ubuntuforums.org/showthread.php?t=2073613](http://ubuntuforums.org/showthread.php?t=2073613)

I used these code suggested from the thread:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

rebooted, grub menu show up but window is not listed in the grub menu. So booted up to ubuntu anyway and used : sudo update-grub and now after reboot windows shows up :). Now how do I make windows the default os to be selected....

Anyway I'll mark this thread as solved. Thanks for the help!

---

### Post by oldfred on 2013-02-07
Generally the short method you used does not work if Boot-Repair did not work. But glad you got it sorted out.

You can edit grub file with default to boot by copy & paste Windows entry into grub config file or use Grub Customizer.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

Edit - update if in sub-menu you also need >2 type entry so it knows it is in a sub menu.
[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)
    
       If grub 1.99 with submenus it is a bit different - drs305
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
# and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
#change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

