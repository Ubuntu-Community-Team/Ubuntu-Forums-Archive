---
title: "installation problem"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by seif_tun on 2011-02-23
Hello,

I'm facing a problem when installaing ubuntu 10.10 (32bit).
Actually , I have windows vista installed and I want to install ubuntu on a new partition(I'm using a bootable usb key)

The problem message is : 

[<c010363e>] kernel thread helper +0x6/0x10

and it's blocked there ...

thank you for help:)

---

### Post by Rubi1200 on 2011-02-23
Hi and welcome to the forums :-)

Did you check the integrity of the downloaded iso?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Try UNetbootin (works great with USB sticks):
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

What are the specifications especially RAM and graphics card?

Thanks.

---

### Post by seif_tun on 2011-02-24
Hello,

Thanks for Reply 

Well I fixed the problem:) I chose F1 in ubuntu installation menu screen to enter help menu ,then F6 and typed 
"live-install acpi=off" and that worked fine!

But :( both usb keyboard and usb mouse are not working at all so I cannot connect to my session ..

Thank you for help:)

---

### Post by Rubi1200 on 2011-02-24
You can look in BIOS and see if there are settings related to the USB devices; you may have to play around a bit (but not too much).

Other than that, I am glad you were able to at least get Ubuntu started.

---

### Post by seif_tun on 2011-02-25
Well I already checked bios settings and usb parameters are ok.. Keyboard and mouse are working fine during installation ,in contrsat they don't once the system restarts for the first time do i can't login :(

I tried 10.04 and the same problem occurs(this time during installation)...I Installed the 9.04 and upgrated it to 9.10 and that works fine:)

Thank you for helping me

---

### Post by Rubi1200 on 2011-02-25
No problem about the help, you are more than welcome :-)

Seems like a compatibility issue with the mouse and keyboard.

Hope you find a solution soon.

---

