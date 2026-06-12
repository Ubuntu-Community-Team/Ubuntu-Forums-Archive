---
title: "Live USB Problems"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by Dan Again on 2012-05-20
I am trying to install Ubuntu 12.04 on my new Asus Zenbook UX31E DH52. I downloaded the 64 bit desktop iso and created a Live USB using the built-in tool on another laptop I have that is already running Precise. I was able to boot into the USB and saw three options: Try without installing, Install, Check for Errors. For each one of these options, the computer just hangs with a black screen. The built-in light on the USB stick flashes slowly as if it is idling. I double checked the md5sum on the iso file and it seems to check out. Any ideas?

---

### Post by wilee-nilee on 2012-05-20
> **Dan Again said:**
> I am trying to install Ubuntu 12.04 on my new Asus Zenbook UX31E DH52. I downloaded the 64 bit desktop iso and created a Live USB using the built-in tool on another laptop I have that is already running Precise. I was able to boot into the USB and saw three options: Try without installing, Install, Check for Errors. For each one of these options, the computer just hangs with a black screen. The built-in light on the USB stick flashes slowly as if it is idling. I double checked the md5sum on the iso file and it seems to check out. Any ideas?

Check this link on using nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Dan Again on 2012-05-20
Thanks for your reply, but I'm not sure if that's what I need - when  boot into the USB I see the GRUB menu with the three options I list above. No matter which option I choose, the computer immediately hangs on a black screen. I do not ever see the Ubuntu splash screen with those options displayed. I tried altering the kernel boot options from GRUB as described in "How to temporarily set kernel boot options on an installed OS (not wubi)", but that did not seem to help.

---

### Post by wilee-nilee on 2012-05-20
> **Dan Again said:**
> Thanks for your reply, but I'm not sure if that's what I need - when  boot into the USB I see the GRUB menu with the three options I list above. No matter which option I choose, the computer immediately hangs on a black screen. I do not ever see the Ubuntu splash screen with those options displayed. I tried altering the kernel boot options from GRUB as described in "How to temporarily set kernel boot options on an installed OS (not wubi)", but that did not seem to help.

Read the link this is for black screens, just because it is a black screen does not mean it is hanging, but that there are no graphic drivers available at that point.

At the try ubuntu etc screen you hit f6 for the options.

---

### Post by Dan Again on 2012-05-20
I never get to an Ubuntu screen. When the Live USB boots it comes into a GRUB menu. I have the three options to select from at the GRUB menu. No matter which option I choose it appears to "hang" on a black screen.

---

### Post by wilee-nilee on 2012-05-20
> **Dan Again said:**
> I never get to an Ubuntu screen. When the Live USB boots it comes into a GRUB menu. I have the three options to select from at the GRUB menu. No matter which option I choose it appears to "hang" on a black screen.

The usb boot would not produce a grub menu unless grub was put there on a install in its mbr. Or you are seeing the installs grub just having the thumb plugged in.

So you tried at that grub menu to hit E for edit and used the arrow keys to navigate to the area where you see quiet splash and inserted nomodeset and booted from there and never get a command line which you would just type startx to get to the desktop.

It seems you have an actual install that use grub this has not been mentioned in the thread, or at least a attempt to install.

This is your first post.

> I am trying to install Ubuntu 12.04 on my new Asus Zenbook UX31E DH52. I  downloaded the 64 bit desktop iso and created a Live USB using the  built-in tool on another laptop I have that is already running Precise. I  was able to boot into the USB and saw three options: Try without  installing, Install, Check for Errors. For each one of these options,  the computer just hangs with a black screen. The built-in light on the  USB stick flashes slowly as if it is idling. I double checked the md5sum  on the iso file and it seems to check out. Any ideas?     This gives no indication of a install, has this thumb been used for other installs and has had grub dumped in its mbr.

The description is really broken I'm just trying to understand everything that has been done. :)

---

### Post by Dan Again on 2012-05-20
I really appreciate your help and I'm sorry my question is confusing. Here is what I did...
[LIST]
[*]downloaded iso
[*]made Live USB
[*]booted to USB on new computer with only Windows installed
[*]USB boots to GRUB (I realize this is atypical)
[*]Live USB "hangs" on black screen for all three GRUB options
[/LIST]
I do not know why my Live USB is booting into a GRUB. As I mentioned, I checked the md5sum and it was correct. I created two separate Live USB sticks, and both boot to a GRUB menu.

---

### Post by wilee-nilee on 2012-05-20
> **Dan Again said:**
> I really appreciate your help and I'm sorry my question is confusing. Here is what I did...
[LIST]
[*]downloaded iso
[*]made Live USB
[*]booted to USB on new computer with only Windows installed
[*]USB boots to GRUB (I realize this is atypical)
[*]Live USB "hangs" on black screen for all three GRUB options
[/LIST]
I do not know why my Live USB is booting into a GRUB. As I mentioned, I checked the md5sum and it was correct. I created two separate Live USB sticks, and both boot to a GRUB menu.

How are you loading the thumb, some usb loaders have similiar menus to grub and actually use grub like the multisystem bootloader. Unetbootin kind of looks like grub, but here is a actual grub screen shot that is grub2, is this what you are seeing.

This is grub 2 from debian lenny so blue not purple like ubuntu but says grub 2 at the top does yours look like and say this. 
[ATTACH]218357[/ATTACH]

I think we can probably figure out what is going on, if we could get into a live ubuntu desktop we could run a script that would tell us exactly where grub is and you would be able to install as well.

---

### Post by Dan Again on 2012-05-20
Okay - I've made headway! I read somewhere else that there were problems with UEFI boot loaders, so I followed some steps on another thread to boot properly into the USB with no GRUB menu. I am installing 12.04 now...huzzah! Thank you for your efforts, though, Wilee, I sincerely appreciate it!

---

### Post by wilee-nilee on 2012-05-20
> **Dan Again said:**
> Okay - I've made headway! I read somewhere else that there were problems with UEFI boot loaders, so I followed some steps on another thread to boot properly into the USB with no GRUB menu. I am installing 12.04 now...huzzah! Thank you for your efforts, though, Wilee, I sincerely appreciate it!

Cool I had not thought of UEFI, I have no clue there, good ground work on your own. :)

---

### Post by duph on 2013-03-12
> **Dan Again said:**
> Okay - I've made headway! I read somewhere else that there were problems with UEFI boot loaders, so I followed some steps on another thread to boot properly into the USB with no GRUB menu. I am installing 12.04 now...huzzah! Thank you for your efforts, though, Wilee, I sincerely appreciate it!

I have the same problem. In which thread did you find these steps?

---

