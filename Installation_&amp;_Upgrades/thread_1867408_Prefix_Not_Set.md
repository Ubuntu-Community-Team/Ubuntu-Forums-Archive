---
title: "Prefix Not Set"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by mrgabe55 on 2011-10-22
Hi, I have just installed Ubuntu alongside xp using wubi but every time i try to boot into ubuntu it says error prefix not set and just goes into some thing that looks like command prompt

---

### Post by bcbc on 2011-10-22
"Prefix not set" is a benign message that happens on all wubi installs since 11.04 - and doesn't indicate the cause of booting problems.

If you're getting a grub prompt then likely there is another issue. More information will point us in the right direction.

Did you boot Ubuntu already or did this happen the very first time?
If the answer is this happened the first time, then where did you install Ubuntu? On an external drive?

---

### Post by mrgabe55 on 2011-10-23
I had just finished the wubi install on windows xp then i rebooted and choose ubuntu in the boot selection menu and it came up with error prefix not set and then the grub prompt came up and it has done that every time i have tryed since. I installed it on my laptops hardrive

---

### Post by bcbc on 2011-10-23
How old is the computer, and how big is the hard drive?

I'm not really sure what could be the problem...

Try this from the grub prompt:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root

```

And from windows, the output of (change C: if you installed on a different 'drive'):
```
dir C:\ubuntu\install
```

---

### Post by mrgabe55 on 2011-10-23
My Computer is a Toshiba M70 and the hard drive is 37gb i had 14gb free before the install. I just inputed search -s -f -n /ubuntu/disks/root.disk echo $root and then pressed enter and it did nothing and on this is what happened when i did the second thing: C:\Documents and Settings\Greg>dir C:\ubuntu\install
 Volume in drive C is XXXXXXXXXX( im not sure if it is safe to put this )
 Volume Serial Number is XXXXXXXXX ( im not sure if it is safe to put this )

 Directory of C:\ubuntu\install

24/10/2011  01:54 a.m.    <DIR>          .
24/10/2011  01:54 a.m.    <DIR>          ..
24/10/2011  01:54 a.m.    <DIR>          boot
24/10/2011  01:54 a.m.               446 preseed.cfg
24/10/2011  01:54 a.m.               302 wubildr-disk.cfg
               2 File(s)            748 bytes
               3 Dir(s)  14,301,958,144 bytes free

Thankyou for helping me!

---

### Post by bcbc on 2011-10-23
Okay, from the grub prompt enter:
```
configfile /ubuntu/install/wubildr-disk.cfg
```

Note the command is case-sensitive.

PS the previous commands I gave from the grub prompt should have been two separate commands. You can try them again after you note any errors from the above command.

---

### Post by mrgabe55 on 2011-10-23
They both came up with nothing.

---

### Post by mrgabe55 on 2011-10-23
Do you think installing ubuntu with a bootable usb stick would work?

---

### Post by bcbc on 2011-10-23
Hard to say whether installing direct will make a difference. I'm not sure what the problem is. If you decide to do this, just have a windows dvd handy so you can replace the bootloader if it fails. 

If you do have an Ubuntu USB, first boot it in live mode - select "Try it" without installing - so you're sure it runs okay on your hardware before installing it.

---

### Post by mrgabe55 on 2011-10-23
Yeah I think i will do that 


Thanks for your help bcbc

---

