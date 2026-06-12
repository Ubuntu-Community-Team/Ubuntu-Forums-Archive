---
title: "Grub menu gone after installing Ubuntu 20.04.5 LTS (Focal Fossa)"
date: 2023-03-18
forum: Installation &amp; Upgrades
---

### Post by chairworm on 2023-03-18
Everything was working fine. Had Ubuntu 22.04 before. I removed it today and installed 20.04 to use some old software.

Here is pastebin of boot-repair: (My main ssd is sdb, sda is hdd and is not used):

[https://paste.ubuntu.com/p/yw3H3qhR8Z/](https://paste.ubuntu.com/p/yw3H3qhR8Z/)

Any help would be appreciated!

---

### Post by chairworm on 2023-03-18
My EFI seems to be messed up it seems. 

I have fixed the initial problem so grub menu is now showing up on boot.

However, my EFI says low space (almost 0 bytes)

Anyone know how to fix this?

I see a hidden folder called .Trashes that is taking up a lot of space. Maybe I need to move it out of EFI?

EDIT: Not really sure what I did to fix my initial problem but it involves using boot-repair (default settings) and changing GRUB_TIMEOUT_STYLE=hidden to menu.

---

### Post by oldfred on 2023-03-18
Is this an Acer? That is typically the only system that shows "unknown device" as an UEFI entry. You have to turn UEFI Secure boot on and set "trust" on the unknown entry, most Acer models. 

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044) & 
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by tea for one on 2023-03-18
> **chairworm said:**
> However, my EFI says low space (almost 0 bytes)
[COLOR="#0000FF"]Line 243[/COLOR] - /dev/sdb2     935K  99% [COLOR="#0000FF"]full[/COLOR] - This is your EFI partition

The Windows installer creates a very small ESP of 100MB.
The cynic in me would suggest that sharing with other OS boot files was not a consideration. 
Certainly big enough for Windows files but, if you add extra OS boot files, the space soon fills up.

On the other hand, the Ubuntu installer creates a massive 512MB for the ESP.
A somewhat more friendly approach.

Anyway, back to your problem.
Have you considered reducing or moving the Windows partitions to allow you to increase the size of the ESP?

Don’t forget, use Windows disk management tools to manipulate Windows partitions.

---

### Post by oldfred on 2023-03-18
Standard installs do not have an issue sharing ESP.
My Ubuntu only ESP only uses 16MB:
[FONT=monospace][COLOR=#000000]nvme0n1p1 vfat     512M  16.2M

[/COLOR]What is taking so much room in your ESP?
[/FONT]

---

### Post by MAFoElffen on 2023-03-18
Do
```

sudo du -hsx /boot/efi/EFI/* | sort -rh | head -n 25
sudo du -hsx /boot/efi/EFI/.* | sort -rh | head -n 25

```
The OP posted in Post #2 that 
[quote=chairworm]
I see a hidden folder called .Trashes that is taking up a lot of space. Maybe I need to move it out of EFI?
[/quote]
I'm thinking that in the install, it deleted what was there, before installing new, so maybe there is a complete copy of the old there?

If so, then he should be able to remove the content of that directory and fee up space...

---

### Post by chairworm on 2023-03-18
> **oldfred said:**
> Standard installs do not have an issue sharing ESP.
My Ubuntu only ESP only uses 16MB:
[FONT=monospace][COLOR=#000000]nvme0n1p1 vfat     512M  16.2M

[/COLOR]What is taking so much room in your ESP?
[/FONT]

Got a .Trashes folder on my ESP that is taking up a lot of space. I believe its a backup folder made by Hackintosh installation (not really sure).  I havent touched this .Trashes folder in like a year so I think its safe to remove. 

Thanks for your help btw!

---

### Post by chairworm on 2023-03-18
> **MAFoElffen said:**
> Do
```

sudo du -hsx /boot/efi/EFI/* | sort -rh | head -n 25
sudo du -hsx /boot/efi/EFI/.* | sort -rh | head -n 25

```
The OP posted in Post #2 that 

I'm thinking that in the install, it deleted what was there, before  installing new, so maybe there is a complete copy of the old there?

If so, then he should be able to remove the content of that directory and fee up space...

That was exactly it! I deleted this .Trashes folder and my problem was solved! Thanks for your help anyway! [IMG]https://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG]

---

### Post by MAFoElffen on 2023-03-18
Glad I could help. Please use the Thread Tools link on the upper right of the first page of the thread to mark this as Solved.

---

