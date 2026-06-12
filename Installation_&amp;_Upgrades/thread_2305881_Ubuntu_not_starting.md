---
title: "Ubuntu not starting"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by johann7 on 2015-12-10
Good day once again.. I have a big problem I have a Acer laptop after installing ubuntu if doesn't seem to start up correctly. I have googled and googled and downloaded and with every solution comes a new error.
Finally I have this to show here is a past from ubuntu pastebin

[http://paste.ubuntu.com/13885932/](http://paste.ubuntu.com/13885932/)

please help as this is going to give me a heart attack I have 2 ubuntu PC that is running without any problems... but this one... 
Any help would be appreciated!

---

### Post by jones quest on 2015-12-10
Hi,

Does your laptop have another operating system installed on it (windows)? Or is there any important data stored on the hard drives? 

If the answer is NO to both questions, then I would do the following.
Boot into your BIOS and check if the computer is using UEFI. If it is, change that to legacy BIOS mode and disable secure boot and fast startup. These are not needed if Ubuntu is the only operating system on the computer and removing them will make the boot procedure much simpler. 
Wipe the hard drive (/dev/sda - 500 GiB), by booting the computer with the Ubuntu installation medium (DVD or USB stick), and using gparted. Delete all of the partions and replace the GPT partition table with the traditional msdos partition table. (You might need to install gparted if it is not included in the installation medium.) GPT is only needed for the UEFI setup.
Install Ubuntu onto the blank drive with default options. When using legacy boot mode in the BIOS the installation will not create such a complicated boot setup that you have right now. And things should just work.
Hope this helps.

For further information on UEFI check ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) and for gparted ([http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)).

---

### Post by Bucky Ball on 2015-12-10
*Thread moved to **Installation & Upgrades**.*

@jones quest: All the info you need is in the link provided by OP in first post. :)

Run Boot Repair again. Go to the Advanced tab (from memory) and it gives you the choice of where to install grub (the default 'recommened repair' puts it everywhere). Aim that at 'sda' and hit fire. Reboot when that's done and see if it works. If that fails, try again with the Recommended Repair button.

It may fix things up, but you have a couple of errors there which it might not (but you might get the machine booting regardless):
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Partition outside the disk detected.
```

These may need further investigation. If you have a look at the bottom of the output Boot Repair gives some suggestions.

---

### Post by johann7 on 2015-12-11
> **jones quest said:**
> Hi,

Does your laptop have another operating system installed on it (windows)? Or is there any important data stored on the hard drives? 

If the answer is NO to both questions, then I would do the following.
Boot into your BIOS and check if the computer is using UEFI. If it is, change that to legacy BIOS mode and disable secure boot and fast startup. These are not needed if Ubuntu is the only operating system on the computer and removing them will make the boot procedure much simpler. 
Wipe the hard drive (/dev/sda - 500 GiB), by booting the computer with the Ubuntu installation medium (DVD or USB stick), and using gparted. Delete all of the partions and replace the GPT partition table with the traditional msdos partition table. (You might need to install gparted if it is not included in the installation medium.) GPT is only needed for the UEFI setup.
Install Ubuntu onto the blank drive with default options. When using legacy boot mode in the BIOS the installation will not create such a complicated boot setup that you have right now. And things should just work.
Hope this helps.

For further information on UEFI check ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) and for gparted ([http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)).

I did as advised but with no luck. Changed BIOS to Legacy, I booted with live CD formatted HDD and reloaded Ubuntu with default settings. This worked better but now every time I shutdown and startup again it gives me a black screen. Then after 20min I force shutdown with power button. Then when I boot again it works. So every 2nd time it boots?
Yesterday before I formatted I edited the grub and added [COLOR=#111111][FONT=Consolas]acpi=off [/FONT][/COLOR] this worked to the point there I needed to shutdown... It froze and through errors. The fix for this is noapic=force. but this conflicted with the acpi so I am between a rock and a hard place right now! What is my next option?

---

### Post by sudodus on 2015-12-11
Maybe there are problems with the driver for your graphics. What chip/card is it?

Have you tried the boot option **nomodeset**?

-o-

After a failure the boot sequence is not exactly the same as after a successful boot. This may explain why it boots every 2nd time. You can also try with some tweaks in the grub configuration. See this link

[Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by jones quest on 2015-12-12
I agree with sododus. Typically the black screen issues is caused by the graphics not being set correctly by the kernel during boot. You can prevent this by adding the parameter "nomodeset" to grub options.

Modify setting in grub: 
sudo gedit /etc/default/grub

look for the line that says:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
and change it to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 

Then update grub to make the change take place:
sudo update-grub
and reboot 

If you think you also need noapic=force for some reason, you can add that parameter also to the same grub-file you edited before.
Chage the line below: 
GRUB_CMDLINE_LINUX=""
to
GRUB_CMDLINE_LINUX="noapic, nolapic"
update grub and reboot.

If one of the grub option you try makes the computer not boot, you can temporarily change the grub option during boot by holding "SHIFT" and then pressing "e" on the kernel you intend to boot into. Then edit the text out from the boot options.

---

