---
title: "Problem installing a dualboot on encrypted drive"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by ashasmash on 2008-09-19
My first drive is encrypted using truecrypt's whole disk encryption, my second drive is not encrypted and was freshly formatted.

Okay, first I attempted to install Ubuntu inside XP using WUBI, when I started the system up, I got my truecrypt password screen, then was given a bootloader, XP worked fine, but Ubuntu dropped to a terminal and was unresponsive to bring up gnome or whatever.

So, then I attempted using the live CD to install Ubuntu on the 2nd drive.  When I restarted the computer it booted straight to ubuntu with no options to go anywhere else. 

I can boot off the Truecrypt rescue disc and it takes me straight into windows with no option for ubuntu.  

So I guess I'm stuck.  I'd really like to dual boot, but I need to keep my encryption, and keeping a ISO around to boot windows seems problematic.

Any ideas?

---

### Post by Herman on 2008-09-19
> So, then I attempted using the live CD to install Ubuntu on the 2nd drive. When I restarted the computer it booted straight to ubuntu with no options to go anywhere else.I installed Ubuntu in a second hard disk in a fully encrypted file system using the Ubuntu 'Alternate' installation CD.
[Encrypted Ubuntu 8.04 - Step-by-step installation tutorial with screenshots!]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml")
Mine listed Windows XP and two other Ubuntu installations in it's boot menu, but in my computer, the other installations aren't encrypted. 

It (GRUB) should be able to boot and encrypted operating system because you're only chainloading the boot sector. The boot sector wouldn't be encrypted, surely?
I don't know anything about truecrypt, so I'm not sure, but you should be able to easily add a boot stanza to chainload your Windows to the bottom of the /boot/grub/menu.lst file in Ubuntu manually if it doesn't appear automatically.
```
gksudo gedit /boot/grub/menu.lst
```Copy the boot stanza below and paste it into your menu.lst,```
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by ashasmash on 2008-09-20
> **Herman said:**
> I'm not sure, but you should be able to easily add a boot stanza to chainload your Windows to the bottom of the /boot/grub/menu.lst file in Ubuntu manually if it doesn't appear automatically.
```
gksudo gedit /boot/grub/menu.lst
```Copy the boot stanza below and paste it into your menu.lst,```
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```

Thanks for the response!  I tried this and I do get the option of Windows in Grub, but when I select it I get 
"Error 13: Invalid or unsupported executable format
Press any key to continue..."

Then it dumps me back to the grub menu.

---

### Post by ashasmash on 2008-09-20
I tried the advice in this thread

[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

And that didn't work either.

---

### Post by Herman on 2008-09-20
Maybe the boot sector is encrypted too then, I don;t know anything about 'Truecrypt'.

Hmmm, it looks like I'll have some reading to do before I'll be able to be much more help to you.

[U][*TrueCrypt* - Free Open-Source On-The-Fly Disk Encryption Software ...]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.truecrypt.org%2F&ei=8YPUSJyxHoKMsAOYmbTyDA&usg=AFQjCNH8UXHuTTPFsxxhk9LfQtfx7CG5Pg&sig2=iJu3drM26btyVUCSHUZz0w")

[*TrueCrypt* - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=2&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FTrueCrypt&ei=8YPUSJyxHoKMsAOYmbTyDA&usg=AFQjCNH7roajTf0U5J2LRiC47EfZC7jjSQ&sig2=iIi97yGMN3lSIKaL7s4_qA")

[/U]It may be some time before I can reply with any kind of sensible suggestions....

---

