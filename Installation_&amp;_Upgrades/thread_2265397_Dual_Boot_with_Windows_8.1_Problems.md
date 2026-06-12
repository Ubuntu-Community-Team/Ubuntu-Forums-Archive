---
title: "Dual Boot with Windows 8.1 Problems"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by patrickbo on 2015-02-14
I Purchased a Dell laptop, with Windows 8.1 pre-installed.  Followed the instructions of [http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) to install dual boot.  

After the install, i wasn't given the option of which OS to choose from, it booted directly to windows so i followed their last instruction of 

```
bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
```

Now, it loads directly to Ubuntu, and i can no longer access Windows.  Any assistance would be GREATLY appreciated, i'm freaking out LOL

Thanks

---

### Post by oldfred on 2015-02-15
I cannot believe those instructions say backup is optional.

Best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

