---
title: "Gutsy on older PC"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2007-11-21
I decide to give it a try and install Gutsy on a old PC of mine. It's 400 Mhz and should have enough space. I used to have Win 98 on it. I went ahead and formatted the drive, changed BIOS to start with CDROM but when I reboot and my PC attempts to load from CD I get an error saying: Invalid system disk. Please replace disc and try again.

Now sure what to now...

---

### Post by oneadvent on 2007-11-21
sure you burned the iso and not the data?

---

### Post by Pumalite on 2007-11-21
How much memory do you have?

---

### Post by dodgingspam on 2007-11-21
Cache memory 128 Mb. 

CD was shipped to me. It worked fine on my laptop.

---

### Post by oneadvent on 2007-11-21
> **dodgingspam said:**
> I decide to give it a try and install Gutsy on a old PC of mine. It's 400 Mhz and should have enough space. I used to have Win 98 on it. I went ahead and formatted the drive, changed BIOS to start with CDROM but when I reboot and my PC attempts to load from CD I get an error saying: Invalid system disk. Please replace disc and try again.

Now sure what to now...

I got it. You must not have saved your bios settings.

It is trying to use the empty hd.

---

### Post by Pumalite on 2007-11-21
256 MB of RAM or less> Feisty Xubuntu Alternate CD:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Unicycle on 2007-11-21
> **dodgingspam said:**
> I decide to give it a try and install Gutsy on a old PC of mine. It's 400 Mhz and should have enough space. I used to have Win 98 on it. I went ahead and formatted the drive, changed BIOS to start with CDROM but when I reboot and my PC attempts to load from CD I get an error saying: Invalid system disk. Please replace disc and try again.

Now sure what to now...

I have Xubuntu on a PC with similar specs to yours that's laying around my house.  It works wonderfully.  Slow, but usable.

---

### Post by dodgingspam on 2007-11-21
Perhaps I need to look into Xubuntu.

---

### Post by oneadvent on 2007-11-21
It shouldn't say bad disk though, it would just be too slow to start it. 

No its not reading from the CDRom somewhere.

---

### Post by dodgingspam on 2007-11-21
Well... I see the cdrom trying to kick in for a few times

---

### Post by oneadvent on 2007-11-21
It does that anyway.

Did you check the bios again? 

Have you ever been able to boot from a cd on that computer?

---

### Post by ugm6hr on 2007-11-22
> **dodgingspam said:**
> I decide to give it a try and install Gutsy on a old PC of mine. It's 400 Mhz and should have enough space. I used to have Win 98 on it. I went ahead and formatted the drive, changed BIOS to start with CDROM but when I reboot and my PC attempts to load from CD I get an error saying: Invalid system disk. Please replace disc and try again.

Now sure what to now...

You will not be able to do this.  The minimum requirement for Ubuntu7.10 is 256MB RAM.

As stated, Xubuntu **Alternate**CD should work.  None of the others (Ubuntu, Kubuntu, Xubuntu LiveCD) will work.

---

### Post by dodgingspam on 2007-11-22
OK, I burned a CD with Xubuntu last night, but it still does not work. Here's what happens. I changed BIOS settings to boot in the following order: CDROM, C, A...

When it starts booting it says something like: 
> Verifying DMI Pool Data .............
Invalid sustem disk
Replace the disk, and then press any key

So that's where I am at the moment...

---

### Post by ugm6hr on 2007-11-22
Invalid System DIsc?  Sounds like the disc is bad.

Have you checked md5sum? Have you tried the CD on a different computer?

---

### Post by Pumalite on 2007-11-22
Make sure you burn as an 'image not as 'data'.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by oneadvent on 2007-11-22
> **dodgingspam said:**
> Cache memory 128 Mb. 

CD was shipped to me. It worked fine on my laptop.

He got one shipped to him. He did not burn it.

---

### Post by Pumalite on 2007-11-22
Download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by ugm6hr on 2007-11-22
> **oneadvent said:**
> He got one shipped to him. He did not burn it.

True for the Ubuntu CD (that won't work).  Not true for the Xubuntu CD (no shipit available).

---

### Post by Pumalite on 2007-11-22
Sorry, here:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by dodgingspam on 2007-11-23
I've received by mail UBUNTU and burned my own XUBUNTU. Somehow I get the same message when I try either.

That old CD used to run on Win 98. Perhaps I can reinstall it again and then add Xubuntu? It appeas hat it just does not know what to do with CD? Perhaps I need to try to format again?

---

### Post by oneadvent on 2007-11-23
It does not know what to do with the CD. It is not reading from it because BIOS has not been configured to read from it.

Are you sure that it is being recognized by BIOS? 

And how did you reformat it to start with?

---

### Post by dodgingspam on 2007-11-24
I've used Win 98 startup floppy to load drivers then ran

FORMAT C: 

Is there another way I can try? That was the only way for me to get to run FORMAT on C:

---

### Post by oneadvent on 2007-11-24
no no....see you used a floppy to boot from.

You are missing it somewhere in your bios. You have to tell it to boot from the CD.

If you already made the change it should still be the first boot.

Then don't have it boot the hd at all and see what it says, or from the floppy for that matter.

Another words, take out every option except the CD. 

(You will need to fix it later, but that should get the CD going.)

And BTW: You know, not all types of BIOS will let you boot from the CD Rom, and I'm not sure how to get around it with Linux. I'm sure someone out there does.

---

### Post by oneadvent on 2007-11-24
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

here that should work if you cannot boot from cd.

Let me know where you stand.

---

