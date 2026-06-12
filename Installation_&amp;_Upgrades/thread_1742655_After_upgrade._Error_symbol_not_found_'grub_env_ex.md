---
title: "After upgrade. Error: symbol not found: 'grub_env_export'"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by G1ZmO65 on 2011-04-29
After upgrading from 10.10 to 11.04 I have this error. 

```
error: symbol not found: 'grub_env_export'
grub rescue>
```

Can anyone tell me what this means or how to fix it please?

Thanks

---

### Post by dino99 on 2011-04-29
grub is not well configured, remove then reinstall it using chroot

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

---

### Post by linuxone on 2011-04-29
Hi,

> **G1ZmO65 said:**
> After upgrading from 10.10 to 11.04 I have this error. 

```
error: symbol not found: 'grub_env_export'
grub rescue>
```

unfortunately I had the same error message after upgrading and can't boot my 11.04 system anymore. 

If you don't use encryption (encrypted partition), you'd be able to fix this. There are different solutions how you can fix and reinstall the bootloader. Guess this Howto should help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I would try to use Supergrub. Try to boot your Ubuntu system using supergrub, then open a Terminal (Kubuntu: Konsole) and run the command: "sudo update-grub2".
If this won't help. try another solution from this Howto.

Thomas

---

### Post by G1ZmO65 on 2011-04-29
I'll try Dino99's suggestion now and if that fails it'll give me something to do after work while my other half is watching the royal wedding lol

....gah the live cd is taking an eternity to boot... I'll need to go to work and continue this later :(

---

### Post by Riot@ct on 2011-04-29
I have the same problem but I use a Linux-RAID-0 Software .
How I can fix it?

Thank you!

---

### Post by dino99 on 2011-04-29
> **Riot@ct said:**
> I have the same problem but I use a Linux-RAID-0 Software .
How I can fix it?

Thank you!

better to create your own thread, than spamming that one

sudo dmraid -rE

---

### Post by G1ZmO65 on 2011-04-29
For what it's worth I also am running RAID'ed drives but they are on a hardware RAID card in an HP XW8200 workstation.

I did have problems after the original install with the grub as it's a dual boot Ubuntu/XP system. The issue originally was that grub was telling the system to boot from the wrong partition.

Just hope this issue is as simple to fix when I get home later.

---

### Post by Riot@ct on 2011-04-29
OK, I solved following this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery) Using the Ubuntu Desktop/Live CD (RECOMMENDED)
I changed /dev/sda with /dev/md0 ...some warning but when I reboot it works fine.
Only a problem, Playmouth not works and I see only a black screen but the boot process works fine.

---

### Post by G1ZmO65 on 2011-04-29
I solved this using the suggestion above from Dino99 (thanks)

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

tbh I'm not keen on the desktop interface though, think I'll revert to the classic

---

### Post by Paul Davis on 2011-04-29
The problem from what I can tell is that grub2 was upgraded, however, during the install the grub image was installed to the wrong hard drive.  The old grub2 image can't load the new grub2 modules so it fails.  Luckily there is a really easy way to fix it, just boot from the hard drive that mistakenly had the new grub2 image installed on it.   You can either change the boot drive in the BIOS directly or most BIOS's have a boot menu that lets you decide which drive to boot from.  Once you get back into Ubuntu you can just do a sudo grub-install /dev/sdx where sdx is the drive that the the grub2 image should have been installed on to get everything fixed to the way it should have been.

---

### Post by Singcrazy51 on 2011-07-14
How do you uninstall it? all I get is the command screen with the error message, and it won't accept any commands-  not that I know that many!
 
> **dino99 said:**
> grub is not well configured, remove then reinstall it using chroot
 
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

---

### Post by Singcrazy51 on 2011-07-15
> **dino99 said:**
> grub is not well configured, remove then reinstall it using chroot
 
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT")
 
 
How do you REMOVE IT OR uninstall it??
no matter what I type it just says command unknown!

---

