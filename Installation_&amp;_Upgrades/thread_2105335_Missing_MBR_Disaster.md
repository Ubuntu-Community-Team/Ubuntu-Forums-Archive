---
title: "Missing MBR?? Disaster"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by holt8137 on 2013-01-15
Hello all. I've run into a big problem born from my own stupidity, and I haven't a clue how to rectify the issue since my experience with Linux is next to nill. I'll try to give as much pertinent information as possible in a clear way. 

Drive Setup: 3 SSDs, 2 HDDs, 1 DVDR

SSD1: Windows
SSD2: NTFS program storage
SSD3: Unbuntu (was)
HDD1: In RAID1 with HDD2 (NTFS)
HDD2: In RAID1 with HDD1 (NTFS

Started with Windows 7 on SSD1 and Mint on SSD3. Ended up with Windows 8 on SSD1 and Ubuntu on SSD3. Can't remember if I upgraded (downgraded?) to Win8 before or after I formatted SSD3 with Mint and installed Ubuntu. 

With the above setup, upon booting up the machine, I was presented with GRUB and a selection prompt where I could decide between booting Ubuntu or Win8.

Decided I had enough of Win8 and I'm going back to Win7. Since I never used Ubuntu for anything other than tinkering and to satisfy my curiosity, I decided that had to go too, and I would just use SSD3 for additional expanded Windows program storage.

So, from within Windows I formatted SSD3 for NTFS (ie no more Ubuntu), stuck my Win7 install disk in the DVDR and mashed the restart button to reboot from Win7 install disk and go about my merry way formatting SSD1 for use as a fresh install of Win7.

My merry way came to an abrupt halt. I can't boot with the Win7 dvd. I can't boot into Win8. I either get a single blinking cursor, "unrecognized device", or sometimes in the case of the Win7 DVD I get "no media". After one of these events I get the following prompt:

```
grub recovery>
```

I've created an Ubuntu USB install drive. Attempting to boot to it also results in one of the above outcomes. At the grub recovery> prompt I've tried the following:

```

set root=(hd1,msdos1)
ls (hd1,msdos1)/boot

```

I get "unrecognized file system".

Now I've disconnected all drives except SSD1 and the DVDR. More of the same above. All I want is to get a fresh install of Win7.
Oh, and I can't eject the Win7 install disk because I have a custom PC enclosure the integrates a slot-load drive. If there is an eject button... it's not accessible. 

Any ideas you guys have would be greatly appreciated.

---

### Post by darkod on 2013-01-15
First, messing up the bootloader should not affect booting from the dvd drive. They have no relation. If you try to boot the dvd first, IT HAS TO work, no matter what you have on the hdds. Imagine if this was a new build with a blank hdd.

Second, if you now have only the windows disk connected, you can try booting it from the rescue prompt. But you made few errors in your commands. The first disk is hd0, not hd1 (they start counting from 0). The /boot is noyl for linux OS, not for windows. You have to chainload from grub to windows boot. Try this:
```
insmod part_msdos
insmod ntfs
set root=(hd0,msdos1)
chainaloder +1
boot
```

See if that boots windows.

But I repeat, since you want to reinstall win7 anyway, booting with the dvd and installing HAS to work, regardless what you have on the hdds and its bootloaders.

---

### Post by holt8137 on 2013-01-15
Thanks for the reply. Above when I say hd1,that's referring to the Ubuntu installation USB, while hd0 is the SSD that is suspossed to contain Win7.

As for your command recommendation, the following is the output
```

insmod part_msdos
insmod ntfs
Error: unrecognized filesystem
set root=(hd0,msdos1)
chainaloder +1
Error: unknown command
boot
Error: unknown command

```

However, after trying the above, I attempted to once more boot from the Win7 install disk. Low and behold it worked. I have absolutely no explanation why it wouldnt work before. It would attempt it, and then hang with a single blinking cursor. 

But hey, it decided to work. Thanks for the reply and suggestion.

---

### Post by darkod on 2013-01-16
Well, you shouldn't need to boot the usb from the broken grub on the hdd. The usb should be bootable itself so you can simply boot from it.

I made a typo in that command, sorry. It was supposed to be chainloader +1. Anyway, you got it working now. :)

---

