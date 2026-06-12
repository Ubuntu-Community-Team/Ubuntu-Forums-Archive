---
title: "Cannot boot into Xubuntu 20.04 after upgrade from Lubuntu 16.04"
date: 2021-02-21
forum: Installation &amp; Upgrades
---

### Post by jbrid2 on 2021-02-21
Hi all,
I had Win10 and 16.04 installed on a partitioned SSD in UEFI mode. This was working for many years. I upgraded to 20.04 by re-formatting that Ubuntu partition and doing a fresh install onto that partition (/dev/sdc5). I booted the USB install media in UEFI mode. I verified that Secure Boot and Fast Boot are disabled in my BIOS settings.

Now, when I boot, I get the Grub menu, but 20.04 fails to boot. I get this:
```
Kernel panic : Unable to mount root fs or unknown
```

I am able to boot into 20.04 successfully by doing the following:
```
[COLOR=#000000][FONT=Courier New]grub> set root=(hd3,gpt5)[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]grub> linux /boot/vmlinuz-5.8.0-43-generic root=/dev/sdc5[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]grub> initrd /boot/initrd.img-5.8.0-43-generic[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]grub> boot[/FONT][/COLOR]


```

After booting this way, I tried:
```

update-grub
grub-install /dev/sdc

```

That did not help.

I then tried boot-repair. [Here is a link to the BootInfo summary.]("https://paste.ubuntu.com/p/wXqtFgNpT4/") 

That also did not help.

I can see that the Grub entry is referencing the wrong disk. It has root='**hd2,gpt5**'. I tried editing that through grub-customizer and that also did not work.

I appreciate anyone who reads this, and thank you for any assistance. The only option I have left at this point is to re-install 20.04, but I am not sure what I would even do differently. It seems like this may be an issue of a lingering Grub install from a previous version or something with UEFI. I am not sure. FWIW, I can succesfully boot into Win10.

Thanks!

Edit: Adding a link to the [BootInfo Summary prior to using boot-repair]("https://paste.ubuntu.com/p/Stwtp2GtFc/").

---

### Post by yancek on 2021-02-21
> I can see that the Grub entry is referencing the wrong disk. It has root='**hd2,gpt5**' 

If your root filesystem is on sdc5 then that is the correct entry.  Grub2 counts hard drives from zero so sdc would be hd2 and partitions are counted from 1.

Your boot repair is minimal and is missing most information usually included in the output.  You show 2 ubuntu efi entries (line 50, 51) in the first efi output but only one in the second output (line 74)
Next time you boot and see the Grub menu, hit the c key on the keyboard to get a grub prompt (grub>) and type in:  ls    then post that output here.

---

### Post by jbrid2 on 2021-02-21
Thank you for the response and clarification. Please see the 2nd boot repair that I linked to at the bottom of my original post for full info.

Please see the attachment for the ls commands from the grub prompt.

---

### Post by yancek on 2021-02-22
The ls info from Grub does show the Ubuntu drive as (hd3,gpt5) so use the method you describe in your initial post to boot Ubuntu.  Remove any flash drives and run sudo update-grub.  The output you posted does show the correct UUID.

---

### Post by jbrid2 on 2021-02-22
Thanks again.
I actually resolved this by re-creating the install media using Rufus and doing a re-install. Working now. I assume it was bad install media or just a bad install.

---

