---
title: "Invalid arch independent elf magic"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by HBurd on 2013-08-04
Hi,
I had Kubuntu 12.04 installed alongside Windows 7, and decided to replace Kubuntu with Xubuntu 13.04. In the installer I had to manually remove the Kubuntu partition and create a new one for Xubuntu. The installation finished without any errors.

Now when I try to boot, I get the message
```
error: unknown filesystem
grub rescue >
```

Following instructions from [http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue), I typed the following
```
grub rescue > set root=(hd0,msdos4)
grub rescue > set prefix=(hd0,msdos4)/boot/grub/x86_64-efi/
grub rescue > insmod normal

```

which gave me the error
```
error: invalid arch independent ELF magic
```

At this point I am pretty much lost. I tried [this]("http://ubuntuforums.org/showthread.php?t=1965810") but it didn't work. Any help would be greatly appreciated.

Thanks.

---

### Post by oldfred on 2013-08-04
Often a grub install version difference. Did Xubuntu install its grub correctly or are you really booting the old version and it is not working with the new?

Best to see details or this may reinstall grub correctly.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by hansdown on 2013-08-04
Hi HBurd.

Is this a virtual machine install?

---

### Post by HBurd on 2013-08-05
Thanks, I just ran boot repair and it's fixed now. 

Here's the boot-info anyway: [http://paste.ubuntu.com/5950123/](http://paste.ubuntu.com/5950123/)

---

