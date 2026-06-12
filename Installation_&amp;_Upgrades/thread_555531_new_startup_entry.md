---
title: "new startup entry"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by daved1 on 2007-09-20
Hi all
I am a newbie to all this real computing lark, so i decided to load alongside xp

After install I had about 4 options to choose from ubuntu and windows and a couple of others then I installed updates now I have a couple of extra entries to choose from.

Can someone please tell me why and how to remove them

Cheers Dave :guitar:

---

### Post by stalker145 on 2007-09-20
> **daved1 said:**
> Hi all
I am a newbie to all this real computing lark, so i decided to load alongside xp

After install I had about 4 options to choose from ubuntu and windows and a couple of others then I installed updates now I have a couple of extra entries to choose from.

Can someone please tell me why and how to remove them

Cheers Dave :guitar:

It sounds like you're talking about GRUB. 

Correct me if I'm wrong, but the entries are recovery modes for booting into Ubuntu. I would advise against removing any of your 'extra entries' at this time. Really, they're just for your protection (if a kernel upgrade goes badly or you bork your system) and it doesn't really take up *that* much room.

If you do insist on removing the entries, you can simply edit /boot/grub/menu.lst and remove the desired entries.

Example:
```
sudo nano /boot/grub/menu.lst
```
or
```
gksudo gedit /boot/grub/menu.lst
```

If you choose to change this file, please, *please*, **please** make sure to back it up prior to changing.

Check back if you have any other questions.

---

### Post by daved1 on 2007-09-20
it is grub and the extra entries that I want to remove are the ones added when it updated the system they just look like dupliates of the ubuntu startup options.

cheers thanks for the advice
Dave

---

