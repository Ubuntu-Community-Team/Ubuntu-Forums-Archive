---
title: "error:out of disk grub rescue"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by factorialpython on 2010-03-03
trying to install 9.10 on pc (p3 650 20gb) had win 2000 on for years, but now in france it has died get the error

verifying DMI pool date.....

grub loading error out of disk
grub rescue>

i can do nothing, have to use ubuntu via livecd as i am unable to acces the grub rescue (would not know what to do with it if i did get in)

---

### Post by dstew on 2010-03-03
Maybe you are out of disk space. From a Live CD boot you can tell how much space is left on the hard disk partition you are trying to access. You can right-click its icon in the Places menu, if it shows up there. Or, from a command line, use```
sudo df -h
```

---

### Post by factorialpython on 2010-03-03
> **dstew said:**
> Maybe you are out of disk space. From a Live CD boot you can tell how much space is left on the hard disk partition you are trying to access. You can right-click its icon in the Places menu, if it shows up there. Or, from a command line, use```
sudo df -h
```

20 gig hard drive so let ubuntu have the lot, works super well when on the live cd, have tried to reinstall it a few times now but still same error, does the "verifying DMI pool data.... then gives the grub error, added problem is this (if i can ubuntu working that is) it needs to be in french mon deux!

---

### Post by kansasnoob on 2010-03-03
Look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

Particularly at the **Temporary Solution**, if that gets you booted then continue to the **Solution**.

---

### Post by factorialpython on 2010-03-03
> **kansasnoob said:**
> look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=boot_problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=boot_problems:write)

particularly at the **temporary solution**, if that gets you booted then continue to the **solution**.

tried that link, could not get into anything iether "shift" or "e" if i do put in anything it just says "unknown command", thankyou for your help, any other ideas? The link suggest 10.04 has solved this problem should i go down that route?

---

### Post by kansasnoob on 2010-03-03
> **factorialpython said:**
> tried that link, could not get into anything iether "shift" or "e" if i do put in anything it just says "unknown command", thankyou for your help, any other ideas? The link suggest 10.04 has solved this problem should i go down that route?

You're trying that during the boot process, before the error occurs right? 

Usually with Karmic's grub2 if you hold down the Shift key following the system screen display (like mine says VIA PC1) then the boot menu will appear and you would then press "e" (lower case E) to edit the boot entry. Not after the error appears :)

Lucid is still in development so it kind of depends on you. Where it's still at Alpha 3 there are bound to be some issues. But I'm using it right now and it's fairly good, though based on previous experience with development releases there is almost bound to be some breakage at some point.

If you really want stable I'd suggest Hardy (8.04.4). It's still supported until April 2011.

---

### Post by factorialpython on 2010-03-03
> **kansasnoob said:**
> You're trying that during the boot process, before the error occurs right? 

Usually with Karmic's grub2 if you hold down the Shift key following the system screen display (like mine says VIA PC1) then the boot menu will appear and you would then press "e" (lower case E) to edit the boot entry. Not after the error appears :)

Lucid is still in development so it kind of depends on you. Where it's still at Alpha 3 there are bound to be some issues. But I'm using it right now and it's fairly good, though based on previous experience with development releases there is almost bound to be some breakage at some point.

If you really want stable I'd suggest Hardy (8.04.4). It's still supported until April 2011.

rebooted the damn thing so many times got sore finger tried all you have said, but my old girl is still not giving me love! will search for 8.04 and i will give that a bash, who knows dafter things have happend before, thanks tons for your help, if all else fails will look for the trusted "hammer"

---

### Post by kansasnoob on 2010-03-03
You can get 8.04.4 here:

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by soteria on 2010-03-31
Just want to say I experienced a similar problem - fresh install of 9.10 server (on a P3 566, 60gb hdd) and after reboot was presented with the same 'out of disk' message.

The problem I realised was caused by the bios not having the correct disk size!  Hopefully this helps someone...

---

### Post by bean123 on 2010-03-31
Try BURG. I have added a workaround for buggy BIOS which has similar "out of disk" problem.

---

