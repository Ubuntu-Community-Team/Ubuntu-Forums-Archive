---
title: "standalone usb sdd install &amp; grub and or kernel updates"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by mc4man on 2019-03-10
I have a need for a bit to have Ubuntu (18.04.x) installed to an external ssd using UEFI.
Having looked thru some threads on how to do so, seemed a bit complicated in the case where the internal drive on the creating machine cannot be disabled
(I've only 2 laptops, neither allows disabling internal drives...

So I took a more simplistic approach and now do have 18.04.2 installed to an external ssd that can boot independently without messing up the creating machine.
What does come to mind though is it would appear that I can't let this ssd's install update grub as I gather that would screw up the machine it was running on .
If anyone can confirm this it  would be appreciated.
(- I've a solution to that if true..

---

### Post by oldfred on 2019-03-10
Did you change the UUID in the mount of the ESP in fstab to the external drive's ESP?
I normally do that, and have not had issues with my flash drives and one external SSD, but not have done a lot of updates where a full grub update occurred. Standard updates do not do a full reinstall of grub, only a major grub update might.

Post this:
lsblk -f
cat /etc/fstab

But I also have multiple live installers of Ubuntu, most really just the ISO loopmounted from grub. And then other repair ISO also on same flash drive. And try to do good backups.
That way I can recovery from just about anything that may go awry.

---

### Post by mc4man on 2019-03-10
This was a test run on an ssd I had lying around. If it worked out ok I'd get a newer, higher performing one that uses usb-c

Anyway it seems fine, booting to it while connected to my main use laptop (not the one I created the install with.

```
$ lsblk -f
NAME   FSTYPE  LABEL UUID                                 MOUNTPOINT
loop0  squashf                                            /snap/gnome-logs/45
loop1  squashf                                            /snap/gnome-3-26-1604/
loop2  squashf                                            /snap/gnome-system-mon
loop3  squashf                                            /snap/gtk-common-theme
loop4  squashf                                            /snap/gnome-calculator
loop5  squashf                                            /snap/gnome-characters
loop6  squashf                                            /snap/core/6350
sda                                                       
sdb                                                       
&#9500;&#9472;sdb1 vfat          E0DA-0C61                            
&#9500;&#9472;sdb2 ext4          b5ef3f68-8479-4c90-8c07-7fc4c165c5e9 
&#9500;&#9472;sdb3 ext4          90369a73-6a5f-4bc6-ad9a-2bf4dff02ebb 
&#9500;&#9472;sdb4 ext4          03c4e329-2a5f-4c4a-9daf-14fac38f2114 
&#9500;&#9472;sdb5 ext4          d547d5c2-f909-4095-9337-e4ee6835bee9 
&#9492;&#9472;sdb6 ext4          d7e9e4cc-43d2-4540-b1a2-d25e24c739cb 
sdc                                                       
&#9500;&#9472;sdc1 vfat          B027-D589                            /boot/efi
&#9492;&#9472;sdc2 ext4          f5180b4f-29cd-484e-ab42-e84b34726628 /
sr0                                                       
doug@doug-Lenovo-IdeaPad-Y580:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd2 during installation
UUID=f5180b4f-29cd-484e-ab42-e84b34726628 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdd1 during installation
UUID=B027-D589  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

Basically what I did,
On my never much used laptop that has only 16.04 installed, note that this was another like above lenovo where sda is now  an unused internal ssd (orig. for Intel RST

Booted to live session of 18.04.2
Opened gparted
Removed the boot/esp flags on the laptop's vfat partition
Connected the usb ssd, set to gpt & created a small vfat partition, enabled boot/esp flags on it
Installed 18.04.2 to the ext. ssd, set bootloader to the ext. ssd device.

After install re-opened gparted & put the boot/esp flags back on the laptops vfat partition.
That laptop booted fine back into 16.04, the usb ssd boots fine on either of the 2 laptops I have from the boot selection menu.

What I did notice is grub on the ext. ssd  lists 16.04, not a real issue as I'd never choose it. 

So my only concern is there any way at this point that a grub or kernel update  on the ssd  could cause issue with the existing boot/UEFI files on the machine I have it connected to?

Edit:  the ultimate target is my new laptop which is a win 10 machine. I don't want to mess with it for at least 30 days (return period), and because I need windows for some things don't want to mess it up anyway..

---

### Post by C.S.Cameron on 2019-03-10
When I run update-grub while running Ubuntu from an external drive, it adds any other OS it sees, (ie internal drives), to the external drives grub menu. Never had it mess up the internal drive.

---

### Post by oldfred on 2019-03-10
On almost all my installs, I turn off os-prober.
I have multiple installs on sda & sdb, some obsolete. It takes os-prober a while to scan system. So I create a 40_custom for only the few other systems I may want to boot from an install. Then grub update runs a lot faster and I do not have lots of old entries in grub menu.

       Use labels:
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13783902#post13783902](https://ubuntuforums.org/showthread.php?t=2076205&p=13783902#post13783902)
Configfile
[https://ubuntuforums.org/showthread.php?t=2076205&p=13788092#post13788092](https://ubuntuforums.org/showthread.php?t=2076205&p=13788092#post13788092)

---

### Post by ubfan1 on 2019-03-11
Be aware of some of the problems running an SSD over USB, like the adapter having USB Attached  SCSI Protocol (UASP) and  handling TRIM, as mentioned in [http://salutepc.altervista.org/ssd-on-usb-3-0-3-1-with-trim-support-windows-linux.html](http://salutepc.altervista.org/ssd-on-usb-3-0-3-1-with-trim-support-windows-linux.html).  Consider using an esata connector/box for the SSD to avoid such problems .

---

### Post by mc4man on 2019-03-11
> **ubfan1 said:**
> Be aware of some of the problems running an SSD over USB, like the adapter having USB Attached  SCSI Protocol (UASP) and  handling TRIM, as mentioned in [http://salutepc.altervista.org/ssd-on-usb-3-0-3-1-with-trim-support-windows-linux.html](http://salutepc.altervista.org/ssd-on-usb-3-0-3-1-with-trim-support-windows-linux.html).  Consider using an esata connector/box for the SSD to avoid such problems .
These days esata on new laptops is rare, no problem though. Checked out a similar device as to one getting & it shows  Driver=uas
Plus decent ext. ssd's should have some internal  form of garbage collection & wear-leveling..

---

