---
title: "Dual Boot Suse 9.2 and Hoary 5.04 with Grub, patched Suse Kernel, Suse would not boot"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by yetanothersteve on 2005-06-12
I have the AMD64 version of Suse 9.2 installed on hda2 and 32 bit Ubuntu Hoary 5.04 on hdb2.
Suse installed first, Hoary second and I allowed Hoary's GRUB to take over after the installer successfully found the bootable Suse partition and offered to add Suse to the list of bootable partitions.

On 6/11/2005, I patched my Suse Kernel using YOU from 2.6.8-24.14-default to 2.6.8-24-16-default without realizing that the Hoary GRUB would not know anything about this change.

My next attempt to boot Suse 9.2 resulted in an "Error 15:", where the Suse boot image was not found.

Solution: I booted into Hoary and using the root terminal edited the file /boot/grub/menu.lst with the new patched kernel's information
All the way at the bottom of menu.lst are the Suse entries and I have copied the new entries here.

```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		SuSE Linux 9.2 (x86-64) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8-24.16-default root=/dev/hda2 
initrd		/boot/initrd-2.6.8-24.16-default
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		SuSE Linux 9.2 (x86-64) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinux-2.6.8-24.16-default.gz root=/dev/hda2 
savedefault
boot

``` 
Basically, I changed anything referring to the old kernel, 2.6.8-24.14, to the new kernel, 2.6.8-24.16.

If this seems too obvious or easy for a write up in these forums, I did not find any information like this in my searches. If there is an "automagic" way to update Hoary GRUB, please post it.


P.S. Confuse your MS and IBM centric co-workers by buying an Ubuntu golf shirt to wear to work. I did and it did lead to positive conversation.

---

### Post by Stilgar on 2005-06-12
Well the first section seems ok, but the second part seems to be pretty messed up. I'm not familiar with suse, so maybe its ok.
<p>
could you give an ls of the /boot/ directory on /dev/hda2 ? Seems like its just a filename that isn't right.

---

### Post by mingus on 2005-06-12
and of course you did do

#grub-install

after making the changes to menu.lst?

Amd Stilgar is right, the second SuSE entry will not work - it is missing the initrd line.

---

### Post by mingus on 2005-06-12
and if neither of the above fix the problem, you can try chain-loading to SuSE . . .

---

### Post by yetanothersteve on 2005-06-15
I should have mentioned in my post that my dual boot was working fine when I selected this entry that I created. Never had to run grub-install, this entry was simply present the next time I rebooted.

> # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		SuSE Linux 9.2 (x86-64) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8-24.16-default root=/dev/hda2 
initrd		/boot/initrd-2.6.8-24.16-default
savedefault
boot
I deleted the other entry without the initrd information, not sure why the debian installer even created it originally.

For the curious, my ls of hda2/boot results in:
> ls boot
backup_mbr                  message
boot                        symvers-2.6.8-24.16-x86_64-default.gz
config-2.6.8-24.16-default  System.map-2.6.8-24.16-default
grub                        vmlinux-2.6.8-24.16-default.gz
initrd                      vmlinuz
initrd-2.6.8-24.16-default  vmlinuz-2.6.8-24.16-default

I must admit that ever since I had OpenBSD installed on a partition on hda and allowed OpenBSD to write to the MBR, things have been quirky.

Thanks again,
Steve

---

### Post by mingus on 2005-06-17
Steve,

FWIW . . .

I've been having unexplainable results with grub and booting, which timing wise seems to coincide with the 2.6 kernel, but that may be blind coincidence.  For example, on one box I've got just SuSE and XP, and grub works fine from a floppy but installed to the MBR it cannot find Stage 2.  Other weirdness, too.

On another box I've got the same SuSE 9.2, Ubuntu, Kubuntu, Xandros, Yoper, and XP.  I've found that the distros use grub differently, and I suspect some have hacked grub.  Ubuntu uses the Debian script (update-grub) which I think is similar to Fedora's Anaconda in auto-generating menu.lst.  YaST creates the file too but it is interactive, modular, and you can see what it's doing first.  Another difference is that YaST will want to chain-load to other distros (requiring grub to be installed in their /boot partition) while Debian uses an explicit kernel call in the menu stanza.
One other major difference is that SuSE uses the /etc/grub.conf file to tell grub-install where to place the Stage 1 and Stage 2 files, whereas Debian does not - SuSE has the grub-install script but I don't think it uses it, instead exec's the install command with grub.conf as stdin.

Bottom line, I've had problems mixing distro boot loaders.  And IMHO SuSE's method (and of course, YaST, for which there is no equiv in Ubuntu) is more robust.  That's why I use SuSE's grub and chain-load the others.

Just my 2 cents.  When you figure out the problem, be a favor if you posted your solution.

Best -

---

