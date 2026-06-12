---
title: "Installation fails &quot;after&quot; its completed"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by Greatnesss on 2012-02-29
Hi guys/girls.
Im completly new to linux and choose ubuntu since it feelt like a good beginers choice.
So I downloaded the 11.10 amd64 version.

First I tried to install it with wubi just to check it out.
But I got irritated by the fact that my /home/ folder was given limited space and the fact that it was installed in windows.

So I partitioned my system disc. 100gb was given for linux itself and 2gb for a swap area.

I used the "usb start up creator" tool that came along with the amd64.iso, I made an startup on a USB-stick and rebooted and launced from the USB

So far evertyhing was fine.

The installation went well, I punched in username, pw, location and so on.

Then I get to the point were a little box apparse that says "installation complete pls restart your system" so I hit the "restart" button and then a black screen with white text appares and a text in the middle of the screen that says "remove the boot media if any and press enter"
So I do this.

After this point, several lines of text appare.

Im clueless to what I should do. I have tried to google the problem, but I cant rly find any good answer.
Any help is greatly appriciated.

Im linking 2 pics of the events that happens "after" the installation is completed.

Here is the one from instantly after I press "restart" when the installation is complete
[http://imageshack.us/photo/my-images/694/20120229143544.jpg/](http://imageshack.us/photo/my-images/694/20120229143544.jpg/)

And this one is from when I have removed the USB and pressed enter
[http://imageshack.us/photo/my-images/440/20120229143621.jpg/](http://imageshack.us/photo/my-images/440/20120229143621.jpg/)


Regards
Greatness

---

### Post by miegiel on 2012-02-29
Personally I always restart before removing the media and turn the machine off as soon as it reboots (the BIOS). Only then I remove the CD, SD card or USB stick and power up again. (Just to avoid problems, I don't like to eject devices I booted of. Call me paranoid).

Just wondering: Didn't you try to force the reboot after it hangs? Worst case scenario: The installation fails and you'll need to try installing it again. ;)

BTW Welcome to ubuntu(forums)

---

### Post by Greatnesss on 2012-02-29
> **miegiel said:**
> Personally I always restart before removing the media and turn the machine off as soon as it reboots (the BIOS). Only then I remove the CD, SD card or USB stick and power up again. (Just to avoid problems, I don't like to eject devices I booted of. Call me paranoid).

Just wondering: Didn't you try to force the reboot after it hangs? Worst case scenario: The installation fails and you'll need to try installing it again. ;)

I could try that.

The thing is, if I remove and then hit enter and the text appare. I have to force reboot and then ubuntu dont show up as a bootable OS =/ Its not its not even installed

Thanks for you reply and your welcome =)

---

### Post by miegiel on 2012-02-29
> **Greatnesss said:**
> I could try that.

The thing is, if I remove and then hit enter and the text appare. I have to force reboot and then ubuntu dont show up as a bootable OS =/ Its not its not even installed

Thanks for you reply and your welcome =)

I guess something went wrong while installing [GRUB2]("http://en.wikipedia.org/wiki/GRUB") or updating the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record").

GRUB gives you the boot menu to choose which OS to boot. There are [faster ways]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2") to repair/reinstall GRUB, but in your case it's probably easier and safer to just try installing ubuntu again.

---

