---
title: "New instillation, Blank screen with cursor"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by GenghisJohn on 2012-10-16
Hello all!

I hope everyone is happy and healthy.  

I had wanted to make my introduction other than begging for help but sadly, it looks that is how it's going to go...

I recently installed Ubuntu 12.04 on my wife's Dell Inspiron 6900

After installing and setting up my network information, it asks for her to choose a name and password and computer name, which we filled out of course.

After everything had finished and we were at the log in screen, the username and password didn't work, we tried several variations in spelling and and caps.  I finally came to the forums and found out how to reset the password and one of the steps is to reboot.  

Once we rebooted, our Dell Splash screen still came up (strangely I assumed it would be an Ubuntu screen) and after that screen it goes directly to a black screen with only a flashing cursor.  

I've not been able to do anything at all, I've rebooted and held shift, attempting to restore but nothing.  

Any help would be greatly appreciated!

Thank you all in advanced.

John

---

### Post by bogan on 2012-10-16
Hi!, **GenghisJohn**,

The Dell splash screen is perfectly normal and is the Bios screen. After 10-40 secs it should go to a blank black screen and then to the Grub bootloader menu.

Will it boot correctly from a LiveCD/USB?

What video card does it have?

Chao!, **bogan**.

---

### Post by GenghisJohn on 2012-10-16
Hi Bogan!

Thank you for taking the time to reply!

I tried booting with the CD, it got a little further but ultimately went to a blank screen with the "loading" icon and has been stuck there for several hours.

Unfortunately, I am not entirely sure what video card it has.

I was originally waiting for the grub menu so I could use the restore option, but it never quite gets that far.

John

---

### Post by bogan on 2012-10-16
Hi!,** GenghisJohn**,

When booting from a LiveCD/USB you should get an aubergine screen with two small Icons at the bottom, one a keyboard and the other a 'man' figure: pressing 'Esc' whilst that shows should open a grub type menu with some additional options in a bottom toolbar; [ If you get a 'choose Language' screen, press 'Esc' again] one is to "Press F6 other options" and that will give you a drop-down menu & the choice of boot command options to try.

The one most likely to meet your difficulty is 'nomodeset'; select it and follow the screen prompts to: "Try without Installing": you can then try out 'System Settings>Additional Drivers' to install whatever driver is missing, and to run a Terminal to get the info requested in my previous Post.

If you need more info check out Post#3 of the Installation & Updates Forum Blank Screen sticky: [ It's a long time since I used this, & I am writing from memory; full instructions are in this link:]
[http://ubuntuforums.org/showthread.php?t=1743535&page=108](http://ubuntuforums.org/showthread.php?t=1743535&page=108)

Chao!,** bogan**.

---

### Post by GenghisJohn on 2012-10-16
Hi again Bogan!

Thank you again for taking the time to reply sir.

I DID get that screen after I booted with the CD!

I will try that later tonight, have some things going on now and I can't get to it, oh I do hope it works!

Thank you very much for your help!

John

---

