---
title: "uEFI - auto boot?"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by treousa on 2011-05-26
Hello,

I've done a lot of research on this, and non of the things I've tried to far have worked, but I feel like this is a really simple problem, so hopefully someone can help me.

I have a new Samsung 9 series that I've installed kubuntu 11.04 on, I wiped the drive completely clean and let the installer partition everything. Installation went fine, rebooted and whenever it boots, it will sit at the EFI selector screen with "ubuntu" being the only option. How do I get this to boot into ubuntu automatically after  a few seconds? I don't want to have to hit enter essentially.

I tried playing with efibootmgr and the timeout option, but that has no effect.

Is is possible to do what I am asking?

Any help would be much appreciated.

Thanks,

treo

---

### Post by srs5694 on 2011-05-26
There may be an option in your EFI menu, but my experience with UEFI implementations is limited, and I have none with the Samsung Series 9, so I can't be more precise than that.

If that fails, you could try creating a file called startup.nsh on the EFI System Partition. This is a startup script file, and you'd use it to launch GRUB. It would look something like this:

```

fs0:\EFI\ubuntu\grubx64.efi

```

I'm not positive of that final filename (grubx64.efi), since I've reconfigured my Ubuntu installations to use different boot loaders, so I might not be remembering the filename correctly. Look for a filename ending in .efi in the EFI/ubuntu directory on the EFI System Partition.

Note that the EFI System Partition should be mounted at /boot/efi, so you can go there to edit it. Note also that EFI uses Microsoft-style backslashes, not Unix/Linux-style slashes, to separate directory components. You can find more information on EFI startup scripts [here;](http://software.intel.com/en-us/articles/efi-shells-and-scripting/) or do a Web search.

---

### Post by treousa on 2011-05-26
I tried that, no dice, it doesn't seem to even look at the startup file.

---

