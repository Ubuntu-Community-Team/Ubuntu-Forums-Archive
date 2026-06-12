---
title: "update-grub2 does not update grub.cfg"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by zonemikel on 2010-04-07
neither update-grub or update-grub2 are updating my /boot/grub/grub.cfg ? I just did a 
sudo apt-get --purge remove grub2 then
sudo apt-get install grub2
then 
update-grub2

```

michael@UsbDrive:~$ sudo update-grub2
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-18-generic
Found initrd image: /boot/initrd.img-2.6.28-18-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda2
michael@UsbDrive:~$ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory
michael@UsbDrive:~$ 


```there is however a /boot/grub/grub.cfg.new file ... wth ?

---

### Post by drs305 on 2010-04-07
You can use "sudo update-grub" now for Grub2, which you said you also tried.

However, try the direct command instead of the "stub" of update-grub:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Does that update the file?

Have you checked the file permissions of /boot/grub/grub.cfg?

---

### Post by zonemikel on 2010-04-07
```
michael@UsbDrive:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
[sudo] password for michael: 
sudo: grub-mkconfig: command not found

```/boot/grub/grub.cfg does not exist ... i have a copy of it though

let me shed some more light. I'm using xubuntu 9.04 and i upgraded to grub2. It seemed to work for a while then i realized that when i edited the /etc/grub.d/40_custom and then did update-grub it would not update the /boot/grub/grub.cfg 

so i deleted the file /boot/grub/grub/.cfg just to see if maybe grub would make another ? but that didnt happen. I think it made a new grub.cfg.new idk who or why that is there ? 

if i type grub-install -v i still get v1.96 idk why ?


```
michael@UsbDrive:~$ sudo apt-get --purge remove grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  os-prober grub-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@UsbDrive:~$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-pc
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  grub-pc grub2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1332kB/1341kB of archives.
After this operation, 4006kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com jaunty/main grub-pc 1.96+20080724-12ubuntu2 [1332kB]
Fetched 1332kB in 22s (58.5kB/s)                                                            
Preconfiguring packages ...
Selecting previously deselected package grub-pc.
(Reading database ... 130860 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.96+20080724-12ubuntu2_i386.deb) ...
Selecting previously deselected package grub2.
Unpacking grub2 (from .../grub2_1.96+20080724-12ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up grub-pc (1.96+20080724-12ubuntu2) ...

Setting up grub2 (1.96+20080724-12ubuntu2) ...

michael@UsbDrive:~$ sudo cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory

```

---

### Post by oldfred on 2010-04-07
The package is not grub2 but grub-pc. But only if you need to totally reinstall. the sudo update-grub should update grub.cfg unless you have old grub still there and it gets confused on what to boot.

purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by zonemikel on 2010-04-07
> **oldfred said:**
> The package is not grub2 but grub-pc. But only if you need to totally reinstall. the sudo update-grub should update grub.cfg unless you have old grub still there and it gets confused on what to boot.

purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

Thanks ! that worked ... guess i should try "purge" and not "remove" I did all you said except i installed grub2 "sudo apt-get install grub2" ... idk what was installed but what was booting my system was grub2 (the menu is different i can tell)

thanks again

---

### Post by mrojas73 on 2010-07-31
> **drs305 said:**
> You can use "sudo update-grub" now for Grub2, which you said you also tried.

However, try the direct command instead of the "stub" of update-grub:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Does that update the file?

Have you checked the file permissions of /boot/grub/grub.cfg?

Thank you...I got a kernel update and it wouldn't show up int he grub.cfg.  This fixed it.

Thank you.

---

### Post by hovrashko on 2011-01-28
what can i do about:

> sudo: grub-install: command not found

???

---

### Post by gordintoronto on 2011-01-28
What did you actually type? You can copy/paste from Terminal into a message.

---

