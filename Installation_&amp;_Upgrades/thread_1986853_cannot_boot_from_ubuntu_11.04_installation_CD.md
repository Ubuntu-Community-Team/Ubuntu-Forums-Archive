---
title: "cannot boot from ubuntu 11.04 installation CD"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by onelightyear on 2012-05-25
Using a brand new Thinkpad Linovo w520. I want to completely wipe off win 7 from the machine and replace it with ubuntu. Downloaded iso installation file and created the installation CD from there. 

I run the CD from windows and clicked on "Demo and complete installation" option from the ubuntu menu window that popped up. The option was supposed to reboot form CD but it did not. It's always windows that shows up (yes checked Bios to ensure that boot order was set to start with CD drive). Any idea what's going on?:confused:

---

### Post by roelforg on 2012-05-25
Why 11.04 and not 11.10?
But it could be a bad burn, did you burn the image as an image or as a file?

---

### Post by wilee-nilee on 2012-05-25
> **onelightyear said:**
> Using a brand new Thinkpad Linovo w520. I want to completely wipe off win 7 from the machine and replace it with ubuntu. Downloaded iso installation file and created the installation CD from there. 

I run the CD from windows and clicked on "Demo and complete installation" option from the ubuntu menu window that popped up. The option was supposed to reboot form CD but it did not. It's always windows that shows up (yes checked Bios to ensure that boot order was set to start with CD drive). Any idea what's going on?:confused:

Try the out of the bios per-session boot menu sometimes a f12 key pressed right after powering on.

The bios splash should give you the bios key and this one as well, or keys.

---

### Post by onelightyear on 2012-05-25
I bured the image as an iso file (i.e, as an image, right?).

Burn was Ok I think (since the installation window poped up correctly...). Also, I'm doing the burn for the second time coz I thought it was a burn problem. Assuming that there is no other reason to this issue, how can I check to see if the CD burn was OK? 

Tried (again) F12 option. the boot menu shows "ATAPI CD0: Otiarc DVD RW AD-7740H" on the top of the list.

---

### Post by wilee-nilee on 2012-05-25
> **onelightyear said:**
> I bured the image as an iso file (i.e, as an image, right?).

Burn was Ok I think (since the installation window poped up correctly...). Also, I'm doing the burn for the second time coz I thought it was a burn problem. Assuming that there is no other reason to this issue, how can I check to see if the CD burn was OK? 

Tried (again) F12 option. the boot menu shows "ATAPI CD0: Otiarc DVD RW AD-7740H" on the top of the list.

Burn as an an image yeah. You can check the md5sum of the ISO and disc as well,

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you have a usb/flash I would try that as well, unetbootin can load it for yah.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I would keep an image/clone of the main windows install though, you never know when it may come in handy.

---

