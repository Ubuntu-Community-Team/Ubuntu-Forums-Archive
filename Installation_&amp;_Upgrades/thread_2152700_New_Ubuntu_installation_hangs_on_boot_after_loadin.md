---
title: "New Ubuntu installation hangs on boot after loading USB drivers"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by gsfgf on 2013-06-08
[COLOR=#333333][FONT=UbuntuRegular]I just installed Unbunu 13.04 on my mac, and it hangs on boot. It shows the output from loading the usb drivers (and all my usb devices appear to be there) and then stops. Pressing keys on the keyboard produces no input.

Edit: Screenshot: [http://i.imgur.com/JKVTBRZ.jpg](http://i.imgur.com/JKVTBRZ.jpg)

Also, I booted from a livecd to look at logs.  faillog is empty.  dmesg and boot say nothing has been logged yet.  Any others I should look at?[/FONT][/COLOR]

---

### Post by benzarti on 2013-06-08
Try unplugging you usb devices and keeping only mouse and keyboard and then power on/reboot your computer. After the system has started you can plug other usb.

---

### Post by gsfgf on 2013-06-08
Same result.

---

### Post by benzarti on 2013-06-08
Enter the grub menu by pressing SHIFT many times at boot-time, and the press e, add nomodeset to quiet splash. If linux starts, then it must be graphical card problem.

---

### Post by gsfgf on 2013-06-08
I'm using rEFInd, not GRUB, so I opened the boot editor and changed where it says "initrd=boot\initrd.img-3.8.0-19-generic" to "nomodset initrd=boot\initrd.img-3.8.0-19-generic"  Was that right?  There was no quiet splash option listed.  

If I did it right, it didn't work because I have the same problem.

---

### Post by benzarti on 2013-06-08
nomodeset is kernel parameter, try adding nomodeset like that :
```

linux   /boot/vmlinuz-3.8.0-19-generic root=UUID=f8349c70-d649-4cb4-a1c3-3026f8854de5 ro   quiet splash nomodeset $vt_handoff

```

---

### Post by gsfgf on 2013-06-08
That behaved differently.  It showed the Ubuntu boot screen, then failed with error: /dev/disk/by-uuid/[COLOR=#000000][FONT=Ubuntu Mono]f8349c70-d649-4cb4-a1c3-3026f8854de5 does not exist.  Dropping to a shell.  

Makes me think that I need to be passing boot options through rEFInd.  I'm going to see what's in the grub.conf that the installer made and add those to a refind.conf and report back.  [/FONT][/COLOR]

---

### Post by benzarti on 2013-06-08
The uuid must be of your hdd. You ONLY have to add nomodeset to the desired location in the script. This was only as an example : 
```

 linux   /boot/vmlinuz-3.8.0-19-generic root=UUID=f8349c70-d649-4cb4-a1c3-3026f8854de5 ro   quiet splash nomodeset $vt_handoff
```

---

