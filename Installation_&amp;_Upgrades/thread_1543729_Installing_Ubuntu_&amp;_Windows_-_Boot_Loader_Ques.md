---
title: "Installing Ubuntu &amp; Windows - Boot Loader Question"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by rwonder on 2010-08-01
Hello Everyone!
(keep in mind i'm a noob)
So i had installed Ubuntu on my last computer and the boot loader was changed to the linux one (i think it's called grub right?). Anyways, I couldn't get it to go back to windows, so i had to use my recovery discs to do so.  In the process of doing so one of my hard drives (was dedicated to linux and so it was formated to the linux format not sure what that is but anyways) now my pc can't detect it.  So that's one issue if someone can help guide me through how to turn it back into a ntfs or fat32 that would be great.  But my bigger concern is, alright so i'm formatting my computer and i want ubuntu and windows 7 to be able to boot but i do NOT want the grub! I want to have Windows as my boot loader.  How can I do this?  Is my only option to by a high capacity sd card and boot off their?


Thanks guys!

---

### Post by phillw on 2010-08-01
Hi,

quickly put, the windows boot loaded cannot 'see' linux (ubuntu) areas. The linux (ubuntu) boot loader (grub) can 'see' both ubuntu and Win areas.

You can use chain-loading or things like Easy BCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)), but for a plain dual boot using one hard drive grub is a less complicated method.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) has some further details and explanations on the where's and why for's.

Regards,

Phill.

---

### Post by mittwit on 2010-08-01
Why don't you want grub? It can be set up to boot Windows rather than Ubuntu by default if that is what you want.

---

### Post by rwonder on 2010-08-01
If is send my computer in for repair, my warranty requires it in the condition that it was shipped out with (i mean i can have files and programs on it obviously - just can't send it with grub loader).

So what you are saying is it is not possible, because the windows loader will not see ubuntu is that correct?

If that is correct, then i guess my only option is a high capacity sd card right - then i go into boot options and choose the sd card?

Also any suggestions for that hard drive i was talking about before?


Thanks a lot guys

---

