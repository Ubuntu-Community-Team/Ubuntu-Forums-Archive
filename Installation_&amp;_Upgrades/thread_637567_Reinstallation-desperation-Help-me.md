---
title: "Reinstallation-desperation-Help-me"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2007-12-11
I want reinstall ubuntu, After I have chown my File System and home folders to chown -R devTest:devTest /devTest I can no use sudo command.
I want to boot with the cd I have used to install it, but each times I never get access to the cd, I only get access the the installed Kernel
How do i boot from the cd ?
for reinstallation purpose.


Thanks

---

### Post by PmDematagoda on 2007-12-11
Enter the BIOS and go to the Boot section, once there change the priority of the boot devices and ensure that the CD-ROM is at the top thus allowing you to boot the CD.

---

### Post by hoboy on 2007-12-11
> **PmDematagoda said:**
> Enter the BIOS and go to the Boot section, once there change the priority of the boot devices and ensure that the CD-ROM is at the top thus allowing you to boot the CD.

when I go to the boot they are 3 sections to choose

Ubuntu 7.10 , kernel  2.6.22 -14 generic

Ubuntu 7.10 , kernel 2.6.22 generic (recovery mode)

Ubuntu 7.10 , mentest86

witch one is the dc ?
Thanks

---

### Post by viking777 on 2007-12-11
This is difficult to diagnose, but what you are seeing does not appear to be the cd boot menu but the grub menu. My guess is that the chown command on your /dev/ folder has crippled your cd drive since that is where it resides (in /dev) so now you can no longer boot from it. You might want to try booting into recovery mode from the grub menu (the second choice on your list) and you should get to a point where it asks you for a password for maintenance. Enter your password and you will get to a command prompt then try to change your /dev/ folder back to root ownership with:

```
chown -R root: /dev
```

I must stress here though that without seeing your system it is very difficult to know if my theory is correct, I can't imagine that you will make things worse by doing what I have suggested, but I can't take responsibility if it does!

---

### Post by hoboy on 2007-12-11
> **viking777 said:**
> This is difficult to diagnose, but what you are seeing does not appear to be the cd boot menu but the grub menu. My guess is that the chown command on your /dev/ folder has crippled your cd drive since that is where it resides (in /dev) so now you can no longer boot from it. You might want to try booting into recovery mode from the grub menu (the second choice on your list) and you should get to a point where it asks you for a password for maintenance. Enter your password and you will get to a command prompt then try to change your /dev/ folder back to root ownership with:

```
chown -R root: /dev
```

I must stress here though that without seeing your system it is very difficult to know if my theory is correct, I can't imagine that you will make things worse by doing what I have suggested, but I can't take responsibility if it does!

When I launch boot on recovery mode I read a a point 
root@Tester-laptop, where tester is the user.
then i am not sured what to wirte there

---

### Post by Partyboi2 on 2007-12-11
viking777 suggested typing this command in
```
chown -R root: /dev
```You can always give that ago

---

### Post by PmDematagoda on 2007-12-11
> **hoboy said:**
> when I go to the boot they are 3 sections to choose

Ubuntu 7.10 , kernel  2.6.22 -14 generic

Ubuntu 7.10 , kernel 2.6.22 generic (recovery mode)

Ubuntu 7.10 , mentest86

witch one is the dc ?
Thanks

hoboy, I was actually talking about the start-up of the PC **before** the GRUB menu comes up. Press either Del or F2 to bring up the BIOS.

---

