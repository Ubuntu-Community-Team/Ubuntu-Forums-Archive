---
title: "Can't boot Ubuntu 10.04 with legacy grub"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by crazy4nix on 2010-06-30
Hi. I've Win XP installed on sda1 initially.
Then I installed Centos on sdb (boot partition on sdb1 and root on sdb2). I chose to install grub to MBR of sda. The Centos installation automatically created an entry in the menu.lst file and I can successfully boot either into XP or Centos.

Now I went ahead and installed Ubuntu 10.04 to sdb4. Both Centos and Ubuntu are sharing the swap partition at sdb3. 
When I was installing Ubuntu, I chose not to install grub because I wanted the grub already installed to boot all three. 
After Ubuntu was installed, I logged into Centos and added the following entry in its menu.lst [so I modified (sdb1)/boot/grub/menu.lst ]

     Code:
     title Ubuntu 10.04
        root (hd1,3)
        kernel /boot/vmlinuz-2.6.32-21-generic ro root=/dev/sdb4 splash quiet
        initrd /boot/initrd.img-2.6.32-21-generic 
It is not booting. It gives me error 2. What is wrong here. I know Ubuntu 10.04 is suppose to use grub 2, but I didn't install grub there. Here is what's in /boot of my Ubuntu installation (sdb4/boot):

     Code:
     -rw-r--r-- 1 root root  640617 Apr 16 09:01 abi-2.6.32-21-generic
-rw-r--r-- 1 root root  115847 Apr 16 09:01 config-2.6.32-21-generic
drwxr-xr-x 2 root root    4096 Apr 29 08:27 grub
-rw-r--r-- 1 root root 7965368 Jun 30  2010 initrd.img-2.6.32-21-generic
-rw-r--r-- 1 root root  160280 Mar 23 05:37 memtest86+.bin
-rw-r--r-- 1 root root 1687378 Apr 16 09:01 System.map-2.6.32-21-generic
-rw-r--r-- 1 root root    1196 Apr 16 09:03 vmcoreinfo-2.6.32-21-generic
-rw-r--r-- 1 root root 4029792 Apr 16 09:01 vmlinuz-2.6.32-21-generic 
The grub dir above is empty. Nothing inside. 
Please guide me. I tried to look for a solution myself, but wasn't able to find one. Thanks in advance.

---

### Post by dino99 on 2010-06-30
lucid works with grub2 (grub-pc), you cant use grub (legacy, dont know about centos)

---

### Post by crazy4nix on 2010-06-30
Thanks for prompt reply. But I thought the OS and the boot loader are independant of each other. That's why we can use grub to boot virtually anything... windows and as such. I find it hard to believe that new ubuntu is tied to grub 2...

---

### Post by paulb42 on 2010-06-30
You're right, crazy4nix, Ubuntu 10.04 is not tied to Grub2, it just ships it as default.. 
I installed 10.04 and didn't write grub, I just added an entry to Ubuntu 8.04's legacy grub. Its quite happy booting lucid that way.
Unfortunately I can't help with your error 2 ... other than it seems to mean this :
2 : "Selected disk doesn't exist"

You might have to replace /dev/sdb4 with a UID for the partition but I'm getting a bit out of my depth here. OldFred or Darkod will no doubt be able to help with that

---

### Post by darkod on 2010-06-30
You should be able to boot with grub1 but there is one important moment. Not sure if that's the problem here though.

Ubuntu by default offers ext4 and earlier grub1 versions didn't have support for ext4. Maybe that's the problem? I know with ubuntu, only with the version 9.04 started shipping grub1 with support for ext4. Not sure about the CentOS grub1 version.

PS. Also double check if that disk is still sdb and hd1, if any of them changed it would look at the wrong place because in menu.lst you are using (hd1,3) and /dev/sdb4.

---

### Post by stlsaint on 2010-06-30
Along with the lines of Darkod of checking to make sure that your UUID's are liniing up with grub and fstab, you can also check your bios settings for your harddrive, make sure your bios is reading your drive correctly and also check the options you have for DMA.

---

### Post by crazy4nix on 2010-06-30
Thanks for your replies guys.

Darkod, I actually used EXT3 to install my Ubuntu. 
I know that the partition Ubuntu is on is (hd1,3) because from the grub prompt, when I did
geometry (hd0)
geometry (hd1)
I got the right output. 
How do I make sure that it's still sdb4? It should be sdb4 from whose perspective? Centos or Ubuntu. 

Might I add, that initially Centos was seeing my hard disks as hdx instead of sdx even though they are SATA disks.. So I fixed the problem using ide0=noprobe and ide1=noprobe as my kernel arguments for Centos booting. I don't know if this changes anything. 
Thanks again!

---

### Post by darkod on 2010-06-30
Well since you are using Centos grub1, I guess it should be /dev/sdb4 from Centos perspective. Since you are sure about (hd1,3) another quick way to test is in menu.lst for the ubuntu entry change /dev/sdb4 into /dev/sda4. If it boots like that, that disk is sda for Centos.

---

### Post by crazy4nix on 2010-06-30
Thanks for your reply... 
i am quite certain that it's sdb4 and not sda4. 
The sda disk at SATA Port 0 is the disk that has windows on it...
The sdb disk at SATA Port 1 is the disk that has Centos and Ubuntu on it...

Nonetheless, I will try changing as per your suggestion and see what happens... 
Thanks again!

---

