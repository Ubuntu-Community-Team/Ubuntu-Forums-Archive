---
title: "dual boot install on HP laptop"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by mcsheffrey on 2018-11-06
I just finished installing ubunbtu 18.04 for a friend on an HP laptop that is running windows 10. I choose the dual boot and 100GB partions size. Everything seemed to go correctly, so when I  did the re-boot after the install, windows 10 came up without the grub menu asking to choose which one I wanted to use. Re-tried booting several times, same thing windows 10 comes up, like ubuntu was never installed. When I go into disk manager in windows it does show the partition where ubuntu is installed. Now I have done this many times on other laptopsand have never has a problem, but they all have been dell laptops.  Any ideas?  Roy

---

### Post by oldfred on 2018-11-06
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What model HP?
Did you also update UEFI?
HP's used to be really bad at allowing something other than Windows, they violated UEFI spec that says NOT to use Description as part of UEFI boot. And only valid description was "Windows Boot Manager". Many work arounds.
But new posts with newer UEFI seem to have fewer issues.

Some of work arounds in link in my signature if you want to read ahead.

---

### Post by mcsheffrey on 2018-11-06
Thanks for the info, I believe your correct, the bios has never been updated and the laptop is fairly old (probably more than 5 yrs). Did have some problems disabling uefi just so I could do a full backup (CLONEZILLA) . I guess my best choice at this point would be to restore everything from my clonezilla backup. He will have to give up windows, if he wants ubuntu.  Thanks Roy

---

### Post by r_widell on 2018-11-07
My Elitebook 8470P wants me to hit the escape key (quickly) to get to the UEFI firmware startup options. Then I can hit F9 to select boot options. Does his machine have anything like that?

If so, is "Boot from EFI file" one of the options?

If all of the above is true, use that option to get into EFI/ubuntu and select the appropriate .efi file--
shimx64.efi if secure boot is enabled, else grubx64.efi.

That should launch grub and get you to the menu (you may have to hit the escape key to see the menu) where you can boot into ubuntu.

Once up, see what you can learn with ```
$ sudo efibootmanager
```

Good luck,
ron

---

