---
title: "Blank Hard Drive Install"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by ReikiMan on 2006-06-29
HELP!! newbie here! Can I, and if YES, how do I, install ubuntu on a completley BLANK hard drive ie , no operating system atall? I have downloaded the ISO to my laptop; if I burn a cd, can I install it on a blank hard drive on another PC?

---

### Post by MJN on 2006-06-29
Sure - the installer will recognise the absence of any formatted partitions and build them accordingly. It'll provide you with the opportunity to change what it suggests however at this level you're best off going with what it says.
 
Of course, it also depends on what you mean by 'blank' - you say 'no operating system' but this could still mean there are formatted partitions on there (e.g. a Windows FAT32/BTFS or even another ext2/3 (etc) Linux partition). Or it could mean blank as in brand new out of the packaging. Either way it doesn't matter to the installer - if it finds partitions on there it'll ask you if you want to remove them or work around them (if possible).
 
Mathew

---

### Post by ReikiMan on 2006-06-29
Matthew, thanks! I do mean 'blank'....there is nothing on the drive, no partitions, nothing. Also, I have the ISO file ready to copy; can I do that with Windows MediaPlayer or will I have to use Roxio? When I have burned the disc, just stick it in the drive, and off we go? Would it be better to put W98 on, as a back-up? Thanks for your time.

---

### Post by MJN on 2006-06-29
Whilst I'm not familiary with Windows Media Player I'm sure it wouldn't work even if it can burn CDs (which I'm guessing it probably can). Use Roxio.

As for putting Windows 98, no, don't do it. Ever. Not even as a backup. ;)

Seriously, you don't need any sort of 'backup', and indeed if you do I wouldn't recommend Windows 98 as it certainly won't live happily with Ubuntu if you installed it afterwards.

To summarise, burn your ISO image (as that's what it is, so you should be looking for that sort of function in Roxio) and boot from the CD (that *may* require going into your BIOS to make the setting) and then let the installer guide you through. Accept all the defaults and follow the guidance and you'll be up-and-running in no time!

A word of 'warning'... some things you took for granted in the Windows world may actually be a real headache under Linux. Just be open-minded and patient and you won't look back - Enjoy!

Mathew

---

### Post by ReikiMan on 2006-06-30
[QUOTE=MJN]Whilst I'm not familiary with Windows Media Player I'm sure it wouldn't work even if it can burn CDs (which I'm guessing it probably can). Use Roxio.

As for putting Windows 98, no, don't do it. Ever. Not even as a backup. ;)

Seriously, you don't need any sort of 'backup', and indeed if you do I wouldn't recommend Windows 98 as it certainly won't live happily with Ubuntu if you installed it afterwards.

To summarise, burn your ISO image (as that's what it is, so you should be looking for that sort of function in Roxio) and boot from the CD (that *may* require going into your BIOS to make the setting) and then let the installer guide you through. Accept all the defaults and follow the guidance and you'll be up-and-running in no time!

A word of 'warning'... some things you took for granted in the Windows world may actually be a real headache under Linux. Just be open-minded and patient and you won't look back - Enjoy!

Mathew[/QUOTE]
Mathew! Good Morning wherever you are! Sorry to be a pain in the ***, but I think I might be a dive and don't understand....I copied the ISO file (i-386...is that the right one?) put iit in the drive, booted up and got "DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER" which I did several times. Nada. Idiot's question, I know, but was I supposed to DO anything with the ISO file....? Is it a kind of zip file which I was supposed to have unpicked somehow? I appreciate your help with this Mathew, please stick with me...you're the one who replied to my plea!!

---

### Post by MJN on 2006-06-30
Don't worry about asking the questions - that's what we're all here for and we've all been down the same path!
 
The ISO image is exactly that - a binary bit-for-bit copy of an entire CD wrapped up in a single file. Now, to burn that image back to a CD you can't just 'copy' the file onto the disc like you would for documents, photos etc. You need to get Roxio to actually burn the *image* from the ISO file onto the CD. I'm not familiar with Roxio - a quick Google search suggests it's one-and-the-same as Easy CD Creator? If so, it looks like you need to go to **File** > **Record CD from Image** and then select your ISO file... a couple of search results imply that it may be looking for a .cif file by default but you'll be fine giving it your .iso file (although it may require you to select All/*.* (or similar) on the *Files as Type* search bit...
 
Is that what you did? Or did you just burn the ISO file the same way as you do with 'normal' files?
 
Mathew

---

### Post by ReikiMan on 2006-06-30
DOH!I burned it the normal way!(Roxio IS the same as EasyCD - they make it.) I will try again, with your instructions and get back to you, with either good or bad news, and another cry for help!

---

