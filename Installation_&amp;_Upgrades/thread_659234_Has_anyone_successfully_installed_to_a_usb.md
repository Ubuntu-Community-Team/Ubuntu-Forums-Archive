---
title: "Has anyone successfully installed to a usb?"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by agim on 2008-01-05
I want to install xubuntu (due to size) on a 1GB usb. I know this is a little small, but a friend of mine would like to try it out, and I am a little hesitant to try to make a partition on his XP, I hear it is something of an adventure.

What I would like to know, is what size usb did you use, what steps/tutorials did you follow, and how much of a performance hit did you notice.
Oh yeah, and did you install grub to the usb. If you did, how did you do it?
Thanks

---

### Post by Pumalite on 2008-01-05
You can install Gutsy:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
Make sure you disconnect all internal drives.

[http://www.pendrivelinux.com/2007/09/27/making-ubuntu-710-casper-persistent/](http://www.pendrivelinux.com/2007/09/27/making-ubuntu-710-casper-persistent/)

---

### Post by agim on 2008-01-05
Great tutorials, I sincerely appreciate it. Of course, now I have another question.
Disconnect my internal drives? Is this safe? How do I do it?

---

### Post by Pumalite on 2008-01-05
I'm hoping you have a Desktop. This is ti avoid getting half installed in your sda and the other half in the Pendrive. All you have to do is disconnect the cables temporarily.

---

### Post by agim on 2008-01-05
ah, a desktop. No, unfortunately (in this case) I don't have one. I have a laptop.

---

### Post by Pumalite on 2008-01-05
Read the links carefully and be careful where you install Grub

---

### Post by stevenmitnick on 2008-01-06
I was successful yesterday. I installed Ubuntu 8.04 Alpha 2 onto a 4 gig USB key.

I first reformatted the USB key from the FAT 32 (factory settings) to NTFS. I used Vista to do this. I then burned a DVD using LiveCD Ubuntu and booted up the computer with it. I then hit the install button and told it to install into the USB key. The installation process took about 2 hours and it worked.

Other formats I tried failed. I decided to try NTFS format to let Ubuntu think it was working with a hard drive. Using the auto install and following the directions while using the NTFS was all I did.

---

### Post by agim on 2008-01-07
Okay, so the initial part of the install went fine. I installed to the usb, the install was just under halfway done then it just stopped.

I ran dmesg and it told me that bcmxx.fw failed to load, or something along those lines. I know I should have written the exact error message, but I know this is a common one.

I will keep searching the forums and the net, but if anybody has some pointers, again, they would be appreciated.

---

### Post by Tekno_Cowboy on 2008-01-07
There is a very useful topic on this here:

[HTML]http://ubuntuforums.org/showthread.php?t=575406&highlight=persistent+usb[/HTML]

I use this method regularly, and it seems to work great. (I prefer the first method)

---

### Post by Pumalite on 2008-01-07
It's good to install wired to the Internet. Sometimes the installer starts trying to load a driver for the wireless and it can't.

---

### Post by agim on 2008-01-07
If I am connected to the internet, that driver won't fail to load?

---

### Post by Bllasae on 2008-01-07
You don't need to make a partition on his XP. You just need to make one on the USB key drive. And yes, I think that it's possible.

---

