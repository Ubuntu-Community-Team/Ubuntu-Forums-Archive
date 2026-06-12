---
title: "Hangs on Install"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by kmashlea on 2011-10-17
Just got new MSI GT683DXR laptop and tried to run 11:10 from disk. It stops when it gets to USBHID:.

I have tried the 32 and 64 bit versions both do same, all I can do is ctrl-alt-del.

I then tried 10.10 this get futher but shows error message too many connections?

It gets to the select full install or run from cd. I click on run from cd and it hangs.

I tried installing to windows, same again, grub is in place but does get past USBHID.

Laptop has USB 3.0 ports as well as USB 2.0. I7 2670QM processor 8gb ram, 1.5 tb raid 0 drives.

I have installed the 11.10 into virtualbox and that is ok.

Can anyone help, I don't know what else to try.

---

### Post by kmashlea on 2011-10-18
After searching through other posts, I tried adding nomodeset when booting from cd and that worked.

I am now tring to install it inside windows but I cannot see how I can add nomodeset.

I tried editing the grub.cfg and re-writing the iso but then I get invalid MD5 and the install fails.

Is there anyway to get this working?

Thanks

---

### Post by kmashlea on 2011-10-18
Got around that finally.

Managed to get nomodeset into grub.cfg.

It now gets futher but crashes with weird characters on screen and then BusyBox Mount denied because NTFS volume is already exclusively opened.
Can't mount /dev/dm-3 /tmp...........

I had just got used to using ubuntu on the old laptop BUT I think after 4 days trying to install it on my new laptop that I will go back to Windows.

It obviously doesn't like new equipment or Nvidia?

---

