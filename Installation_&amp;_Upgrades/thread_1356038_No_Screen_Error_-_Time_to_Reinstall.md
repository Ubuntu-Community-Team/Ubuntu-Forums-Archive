---
title: "No Screen Error - Time to Reinstall?"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by AJH101 on 2009-12-15
I allowed a friend to install Karmic Koala because he said he knew what he was doing. Now I get a 'No Screen Error'. I do not know what other damage he may have done. How do I reinstall a fresh copy of Ubuntu. I am happy to wipe the drive if I need to.
 
Can anyone help me discover how wonderful Linux really can be?
 
Thanks!

---

### Post by darkod on 2009-12-15
Set your BIOS to boot from cd before the hdd. Put in the ubuntu cd and boot from it. You can first use the Try Ubuntu option to see how will it work. It is running from the cd in that mode. You can check if you can surf, audio, video, etc. All basic things, check if they are working fine. If something doesn't work, most probably it won't work right away after the install too. It doesn't mean it can't be "fixed", it just shows you what to expect.
If you're happy how it's running in Try Ubuntu, reboot again with the cd, select Install Ubuntu, and use the Use Whole Drive option if you want to overwrite your drive.
WARNING: That option will wipe your drive and all data will be lost!!! There are other options to use if that's not what you want. From your words it sounded like it is.

---

### Post by AJH101 on 2009-12-15
Thats great - a very speedy reply. Is it simple to reinstall default settings without losing data?
 
Thanks!

---

### Post by darkod on 2009-12-15
> **AJH101 said:**
> Thats great - a very speedy reply. Is it simple to reinstall default settings without losing data?
 
Thanks!

Not really. Depending what data are you referring to. But if you have anything on the computer that you want to copy, while using the Try Ubuntu option it will also allow you to copy data to external usb hdd for example. Even from windows ntfs partitions on your computer hdd.
But specifically the new ubuntu install will overwrite the old one, and it's better to do it that way if the old one is messed up.

---

### Post by AJH101 on 2009-12-16
OK fair enough. I will 'try' Ubuntu and copy the data I need then reinstall. I will let you know! Thank you :-)

---

### Post by AJH101 on 2009-12-17
Thanks for the advice but now I have a grub loading error (below) - even when booting from CD. Any ideas? Thanks!
 
Grub loading
error: unknown file system
grub rescue:

---

### Post by darkod on 2009-12-17
Sort of a dumb question: Are you sure you are booting from the cd? It might call broken grub from hdd and you thinking it's the cd.
I haven't seen this before, the cd giving such error.

---

### Post by AJH101 on 2009-12-17
I was retsarting after having installed from CD so yes, I am pretty sure it is booting from there - and yes - I had checked the CD for errors!

---

### Post by darkod on 2009-12-17
I'm puzzled. If the CD can't even boot you could probably try burning another CD or creating bootable USB stick.

---

### Post by AJH101 on 2009-12-17
Yes except that that option is not available in my BIOS - HDD CD or floppy! :-(

---

### Post by AJH101 on 2009-12-17
And the error appears before the installation CD starts to spin so I do not think that is the problem?!

---

### Post by darkod on 2009-12-17
Well the error does sound like hdd related, not cd. Also, the grub loading is probably coming from the hdd.
But you claim you are sure it is trying to boot the cd. Double check the setting in BIOS whether cd-rom is first choice and then hdd.
Otherwise it seems like a bad cd (even though you already used it) and try burning another cd with the ubuntu ISO, no faster than 4x burn speed.

---

### Post by AJH101 on 2009-12-18
I checked that I am booting from CD. I tried different disks with different OS and I get the same error. Any ideas?!

---

### Post by darkod on 2009-12-18
> **AJH101 said:**
> I checked that I am booting from CD. I tried different disks with different OS and I get the same error. Any ideas?!

If all other CDs are doing the same, it's not related only to the ubuntu CD. I don't know what to say, I have never seen error like that when trying to only boot a CD.

---

### Post by Grenage on 2009-12-18
It sounds like either the CDROM/DVDROM drive is on the way out (could explain why it all went wrong), or the BIOS is simply not booting from the driv at all.  Can you try another drive in the machine?

---

### Post by AJH101 on 2009-12-18
I am stuck on a 
 
Grub rescue
 
prompt. Nothing I enter (eg sudo) is recognised. Can you help me progress at all or do I have a dead computer?! Thanks

---

### Post by Grenage on 2009-12-18
See my previous post.

---

### Post by AJH101 on 2009-12-18
I will try another drive this evening. How do I reinstall the BIOS please? I am a bit of a Noob so I neeed to detailed walk through I am afraid. thanks!.

---

### Post by Grenage on 2009-12-18
You don't reinstall a BIOS, you can *flash*/replace the version it's running, but I would leave that unless you have to.

It's much more likely that you have a CD/DVD drive problem, so just let us know if the other drive doesn't work.

---

### Post by darkod on 2009-12-18
> **Grenage said:**
> You don't reinstall a BIOS, you can *flash*/replace the version it's running, but I would leave that unless you have to.

It's much more likely that you have a CD/DVD drive problem, so just let us know if the other drive doesn't work.

+1
Flashing the BIOS can leave your computer REALLY DEAD! Test with another cd drive and see how it goes.

---

### Post by AJH101 on 2009-12-18
Aha! New HDD was the answer! Thanks so much guys :-)

---

### Post by Grenage on 2009-12-18
Glad it's all sorted :)

---

### Post by VulcanTourist on 2010-01-07
NO, a new disk drive was NOT the answer!  The problem here is a LOGICAL one, not a physical one.  This entire thread should be stricken from the record, before it harms or misdirects someone else.

---

