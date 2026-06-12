---
title: "unable to run or install lubuntu"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by timcs on 2011-04-27
Hi

  I am trying to run either as a live CD or as the install option on a Toshiba L30 256mb ram laptop. 

  When the grub menu options appears - I do not get the choice of the languages to start with and on choosing the run livecd or to install, the Lubuntu logo appears and the dots simply cycle through . This logo images never changes to a more "sharper" state to indicate that the graphics card has been found either.

 I have run the iso from different media and different burn speeds. Furthermore I have used the pendrivelinux to create and usb boot drive but get the same results. Another usb creator I have used is unetbootin-win with the same results as above.
  
  To test the iso , I ran it via virtualbox setting the ram to 256 and it does boot up. 

Any ideas?

---

### Post by timcs on 2011-04-28
It appears that there is an error I am getting which I can see when pressing escape on the logo boot up screen, this error is 

> GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)


Looking around these forums and on google this can be caused by incompatible graphics card. As I am unable to know what the chipset is as I cannot boot into linux, I tried at the grub line :

xforcevesa and (a bit of a stab in the dark) i915.modeset=0 xforcevesa

Are there any other suggestions on what I can try?

---

### Post by mörgæs on 2011-04-28
It is all explained here:
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Post 176 tells you how to solve the problem.

---

### Post by timcs on 2011-04-28
> **mörgæs said:**
> It is all explained here:
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Post 176 tells you how to solve the problem.

Thanks for this and thanks for the post number as that is a very large thread!

---

### Post by timcs on 2011-04-28
Thanks that worked but sadly the lubuntu desktop lacked certain options for me. Apart from xubuntu are there any other desktops I can try on a 256mb machine?

---

### Post by mörgæs on 2011-04-28
That was a fast install...

[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by timcs on 2011-04-28
> **mörgæs said:**
> That was a fast install...

[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

Thanks again for your reply here. Sadly one of the distros listed that I would like to have got going is Linux Mint LXDE but this gave me the same error as I got with Lubuntu. Does Mint have a mini version? as I have googled for it but had no luck finding a download page.

Some of the others mentioned found to be too slow even though this laptop has 256mb werid. 

Some are too limited such as DSL tiny and puppy . I have tried slax as well but it would not allow a connection to my WPA wireless router.

---

### Post by dino99 on 2011-04-28
try tinycore or puppy

---

### Post by timcs on 2011-04-28
> **dino99 said:**
> try tinycore or puppy

Tried both, as mentioned above I found puppy too limited. Cheers for the suggestion though. I think I must have gone through nearly all GUI based distros.

This laptop did have an old version of PCLinux OS Gnome on it but the later versions do not run. sadly I do not have the old version to go back to anymore :(

---

