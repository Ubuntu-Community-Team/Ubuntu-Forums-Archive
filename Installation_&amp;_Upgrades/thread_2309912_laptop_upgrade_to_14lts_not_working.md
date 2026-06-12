---
title: "laptop upgrade to 14lts not working"
date: 2016-01-14
forum: Installation &amp; Upgrades
---

### Post by cee2 on 2016-01-14
im currently running 12 lts on my toshiba laptop
ive forgotten the password and can only access guest  login
the cdrom is broken and cant remember if  i used the usb cdrom i bought to do the install or if i downloaded it.
anyways, i try to do the upgrade via online software update, it downloads 2 small packages and appears to start but then stops without any error  showing

and i cant get my laptop to boot from cdrom or usb , tried both options and my burned version of 14 lts doesnt start it just goes into grub

when i try to boot up the 14 lts disk while using the laptop in 12 lts it either asks for passwrod or doesnt work

im stumped
do i throw away this laptop or continue using  as guest, my only option right now

---

### Post by v3.xx on 2016-01-14
Hi cee2

You could just reset your password on your current 12.04 install.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by cee2 on 2016-01-14
maybe im wrong but that link seems to need the old password to reset the to a new one?

---

### Post by sandyd on 2016-01-14
Moved to Installation & Upgrades

---

### Post by cee2 on 2016-01-14
ok password reset,  it was purposely not showing the new inputted password
supposedly worked to reset the password.

now theres a new problem.
recently another old desktop 12.04 LTS quit logging in
it would seem to accept the password and went blankscreen momentarily then straight back to login without saying there was a password error
it just keeps doing that
i never did figure out that problem before just installed 14.04 LTS with a properly working cdrom and bios unlike this laptop bios that may not be seeing the boot cd in a usb cdrom

any ideas here?

i managed to do an update so i know password is good now but it still does same thing when i try to upgrade to 14 lts, downloads 2 packages a little gear [gksu] shows up in side panel for 5 secs then disaapears and nothing more happens

---

### Post by grahammechanical on 2016-01-14
I am confused. It seems to be that you are now talking about 2 machines and different problems. Please decide which machine and which problem you want assistance with.

Problem: A computer with 12.04 on and a desire to upgrade to 14.04.

First do a regular update. Before upgrading Ubuntu must be up to date. Second, go into system settings> software sources or software & updates and make sure the utility is set to notify you of the next Long Term Support release. In this case update manager should take care of upgrading to 14.04 with a simple click of a button.

What method are you using to start the upgrade process? Are you using the command line?

Regards.

---

### Post by cee2 on 2016-01-14
its still the same laptop only it now resembles another machine that also presented this new problem, it wont login even with a new password
it seems to accept the password and goes to a black transition screen mommentarily then straight back to login screen with no error in passwrod showing in red,  just blank password box

i changed the password sucessfully on this laptop
ive fully updated it
clicking on the start button and clicking software updater brings me to update box which confirms its fully updated
i click on 14 LTS  upgrade button, it quickly downloads 2 files, a little gear in side panel called gksu if you hover mouse over it appears momentarily then disappears and nothing upgrades or happens
no command line

does a wireless connection affect updates?

---

### Post by cee2 on 2016-01-15
how do i install from disk while still booted up if i cant make it start from bios?

---

### Post by sammiev on 2016-01-15
Hi,

All my Toshiba laptops can boot from USB by Pressing F12 at the bios screen on startup.

Burn the ISO you want to the USB and boot into a live session. You can install from there.

---

### Post by cee2 on 2016-01-18
ok this looks like my best option and am in the process of doing it now.
cross fingers
if it works , thanks guys
if not i will be back, lol

---

