---
title: "Boot loader broken. Error"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by Mycle on 2011-12-12
Hi,
On my notebook I've had a multi-boot setup accessible through a couple of boot menus at startup.
I've now installed Ubuntu 11.10 on an external USB hard drive. I used the notebook to do the installation.
During the installation process I ensured that the "device for boot loader installation:" was set to the external drive.

So, now I have the bootloader on the external drive but it's taken over the loading process for both itself and the multiple OSs on the notebook and has disabled the independent booting of the notebook.

I can't boot the notebook unless the external drive is attached. If it isn't I get:
"error: no such device:... grub rescue>"

Is there an easy way to fix this please?

---

### Post by darkod on 2011-12-12
It would be helpful if you list all the OSs on the internal and the external HDD.

It looks like you installed the bootloader to the internal HDD after all. And because the config files are on the ext HDD, it can't boot without it.

Boot your main ubuntu (if you have it) from the int HDD (having the ext hdd attached if needed) and just execute:
sudo grub-install /dev/sda

That will install the grub from the booted system onto the MBR of /dev/sda.

Unless you have a wubi install, because you say "could of menus on startup". Usually there is one bootloader, there is no couple of menus.

If you have some kind of "special" setup be careful before running any commands who don't take into account specific setups.

---

### Post by devansh.j2007 on 2011-12-12
is it that u want bootloader on your external hard drive and internal hard drive as well?
well i am not sure but see what happes if u remove the USB hard drive put an ubuntu live cd and run grub-install from it.... then again when u plug back the hard drive the bootloader of your hard drive should be first if it is first device in BIOS... this is what i think never tried...... for grub-install... this will be helpful
run as root
```
mount /dev/sdax /mnt
grub-install --root-directory=/mnt /dev/sda
```

hope this helps

---

### Post by Mycle on 2011-12-12
> **darkod said:**
> It would be helpful if you list all the OSs on the internal and the external HDD.

On the internal notebook drive I recently installed Ubuntu 10.04
onto a newly made partition. The notebook already has WinXP, which contains it's own Windows installed version of Ubuntu 9.0 within it.

The first (Windows)boot menu on the notebook had Windows XP, Windows Recovery Console and Ubuntu listed. 

If I chose Windows XP from the above, I then got another menu listing Windows XP, or Ubuntu (the one installed through Windows).
> 
It looks like you installed the bootloader to the internal HDD after all. And because the config files are on the ext HDD, it can't boot without it.


It may be so, though I chose to install it on the external drive from the only set of options I was offered by the Ubuntu install process.

> 
Boot your main ubuntu (if you have it) from the int HDD (having the ext hdd attached if needed) and just execute:
sudo grub-install /dev/sda. 

That will install the grub from the booted system onto the MBR of /dev/sda.

Thanks, I'll try that and report back on the effect.

> 
Unless you have a wubi install, because you say "could of menus on startup". Usually there is one bootloader, there is no couple of menus.


There is a wubi install, I apologize for not making that clear before.

> 
If you have some kind of "special" setup be careful before running any commands who don't take into account specific setups.

Other than the notebook internal HD including both a wubi and also a standard Ubuntu installation I'm not sure whether it's "special" or not in the context you describe.

---

### Post by Mycle on 2011-12-12
> **devansh.j2007 said:**
> is it that u want bootloader on your external hard drive and internal hard drive as well?

Yes, I want the notebook to work as before, giving the boot choices of the 1 Windows and 2 Ubuntu installations it contains.

I want the external USB hard drive containing a single new installation of Ubuntu to be bootable on any computer I take it to, including the notebook. I realize that you can't always get what you want. :-)

> 
well i am not sure but see what happes if u remove the USB hard drive put an ubuntu live cd and run grub-install from it.... then again when u plug back the hard drive the bootloader of your hard drive should be first if it is first device in BIOS... this is what i think never tried...... for grub-install... this will be helpful
run as root
```
mount /dev/sdax /mnt
grub-install --root-directory=/mnt /dev/sda
```

hope this helps

Thanks, much appreciated, I'll try this if implementing the previous suggestion from darkod leaves any loose ends.

---

### Post by darkod on 2011-12-12
> On the internal notebook drive I recently installed Ubuntu 10.04
onto a newly made partition. The notebook already has WinXP, which  contains it's own Windows installed version of Ubuntu 9.0 within it.

The first (Windows)boot menu on the notebook had Windows XP, Windows Recovery Console and Ubuntu listed. 

If I chose Windows XP from the above, I then got another menu listing Windows XP, or Ubuntu (the one installed through Windows).

So when you installed the 10.04 did you tell it to install grub onto the root partition and not the MBR? How did the XP bootloader remain on the MBR? And how is it booting the 10.04 since it can't see it by default, with chainloaing?

If you are sure you are using windows bootloader running the grub-install command will install grub2 onto your MBR. Depending if you want to do that or not.

---

### Post by Mycle on 2011-12-13
> **darkod said:**
> So when you installed the 10.04 did you tell it to install grub onto the root partition and not the MBR? 

No, I didn't see that option but you can be sure I'll look out for it in future.
> 
How did the XP bootloader remain on the MBR? And how is it booting the 10.04 since it can't see it by default, with chainloaing?


Not quite sure but when it is working, the Ubuntu option in the first menu opens Ubuntu 10.04
> 
If you are sure you are using windows bootloader running the grub-install command will install grub2 onto your MBR. Depending if you want to do that or not.

Done it and now it's all working fine again, thanks.

Only thing I need to do now is clear out the unwanted boot options relating to the notebook OSs from the Ubuntu 11.10 installation on the external drive's grub menu.

---

