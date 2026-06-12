---
title: "Distorted screen using nomodeset on live usb with Intel HD 4000"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by Nuckinfuts on 2013-11-15
Trying to install Ubuntu 13.10 on a Lenovo Yoga 11S (NOTE: NOT Yoga 11)

I've formatted my USB stick with UEFI support with GPT
When launching the live session without nomodeset in the kernel parameters, it just flashed to a black screen.

With nomodeset I get the following screen issue, then a black screen on tty7 when i would expect X (Mir?) to take over. I can switch to tty1 at this point but it is distorted in the same way that plymouth is in the screenshot attached. Has anyone encountered this or have a workaround?

[ATTACH=CONFIG]247860[/ATTACH]

---

### Post by Nuckinfuts on 2013-11-16
More testing results:
I've gotten 13.04 to boot through the live option fine with nomodeset, full res and everything
14.04 daily is borked the same way 13.10 is (as expected since they don't diverge much yet)
Arch 2013.11.1 install media boots into a text environment fine with nomodeset

All testing images written by Rufus from Windows 8.1 with UEFI+GPT and all MD5 sums checked

---

### Post by oldfred on 2013-11-16
I have seen at least these 4 different boot parameters instead of nomodeset for Intel. Not sure which may work.

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

---

### Post by Nuckinfuts on 2013-11-16
> 
acpi_backlight=vendor


This did the trick for getting (X)Ubuntu and Fedora 19 booting properly with KMS on the Lenovo Yoga 11s (Intel i5/Intel HD 4000)

Hopefully I've used enough terms to make this easily searchable

---

### Post by oldfred on 2013-11-16
Glad you got it working. :)

And thanks for update on which setting worked for you.

---

### Post by Nuckinfuts on 2013-11-16
use the chroot/update-grub method described here: [http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows) to update grub's boot parameters to include "acpi_backlight=vendor"

---

### Post by akanksha.dlf on 2013-12-19
> **Nuckinfuts said:**
> This did the trick for getting (X)Ubuntu and Fedora 19 booting properly with KMS on the Lenovo Yoga 11s (Intel i5/Intel HD 4000)

Hopefully I've used enough terms to make this easily searchable
i an newbie to ubuntu installation. i m trying to install 13.10 on lenovo yoga 11s. on booting from usb i get to the grub2 screen with options try ubuntu and install ubuntu n qem installation etc...if any of the options i get a black screen and cannot do anything. i dont know exactly wheere to write the lines acpi=vendor. can you please elaborate?

---

### Post by Nuckinfuts on 2014-02-15
> **akanksha.dlf said:**
> i an newbie to ubuntu installation. i m trying to install 13.10 on lenovo yoga 11s. on booting from usb i get to the grub2 screen with options try ubuntu and install ubuntu n qem installation etc...if any of the options i get a black screen and cannot do anything. i dont know exactly wheere to write the lines acpi=vendor. can you please elaborate?

Sorry for the very late reply, see this link on askubuntu for details: [http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

instead of entering "foo=bar", you'll want to enter "acpi_backlight=vendor"

---

