---
title: "Plymouth with nVidia UbuntuStudio 16.04"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2016-08-22
***********Please note that the version is 16.04 and NOT 16.10 as mentioned - Thanks howefield for the correction ****************


Hi, I recently upgraded my US 14.04 to US 16.04 (32 bit) and now I have Plymouth woes once again - Plymouth screen was working fine in 14.04.

Here are some background details;

[LIST]
[*]Currently Plymouth screen shows up with rotating Ubuntu Studio icon with the Ubuntu Studio logo text underneath. 
[*]After a few seconds the screen blacks out 
[*]Now only the spinning icon is visible and the Ubuntu Studio logo is no longer visible. 
[*]After a few more seconds system boots normally. 
[/LIST]

I have /etc/initramfs-tools/conf.d/splash file with FRAMEBUFFER set to 'y'. and have the following two included in my /etc/default/grub

GRUB_GFXMODE=1400x1050-16
GRUB_GFXPAYLOAD_LINUX=keep

Since it appears that the problem may be caused by incorrect hand off, I booted the system without the $vt_handoff command in grub by editing the grub entry at boot time. This throws up some uvesafb errors which flashes across the screen and difficult to write down.

I am running nVidia 304 driver.

I would appreciate if anyone has any suggestions on how to fix this problem.


EDIT: Yes, did try the fixplymouth script without success.

---

### Post by howefield on 2016-08-22
Just to double check, do you really mean 16.10, which is the development version ?

Edit : ok in that case, thread title amended to reflect 16.04.

---

### Post by gdesilva on 2016-08-22
Oops...it is 16.04 - my apologies...

---

### Post by gdesilva on 2016-08-23
After a lot of testing, I feel that this is an issue with the vt_handoff specially as initially I get the spinning US icon with the logo underneath and then after a screen flicker I only see the spinning icon and not the US logo underneath. I removed $vt_handoff from grub command and replaced it with vt.handoff=7 (which is the value of $vt_handoff is supposed to be) but nothing changes. If I remove FRAMEBUFFER=y from /etc/initramfs-tools/conf.d/splash file then I get a black screen for a long time, a flicker and then the spinning icon and US logo as it should be.

I am running out of options to try out....any suggestions will be appreciated. Thanks

---

### Post by gdesilva on 2016-08-25
OK, I managed to hack the plymouth script (/usr/share/plymouth/themes/ubuntustudio-logo/mdv.script) to refresh the background image within the function refresh_callback(). After doing this ran update-initramfs -u and the plymouth screen displays as it should now.

Probably not the most elegant way of solving this problem but, hey, it works:)

---

