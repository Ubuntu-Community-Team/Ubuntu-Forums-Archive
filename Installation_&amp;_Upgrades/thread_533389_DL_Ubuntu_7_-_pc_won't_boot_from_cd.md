---
title: "DL Ubuntu 7 - pc won't boot from cd"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by miershpedankl on 2007-08-23
I am new to Ubuntu, but not totally new to computers.  I have downloaded and burned the new 7.x version of Ubuntu and my laptop recognizes the cd.  I am trying to load it on my desktop, but it won't boot for some reason.  When I try to view the cd via windows it doesn't recognize the format. 

Second thing - I have Debian on one drive and WinXP on the other.  When I try to boot from the cd I get the normal "choose your operating system" screen.  

Any suggestions?  

Thanks,
miershpedankl

---

### Post by Pumalite on 2007-08-23
Try Alternate CD. Or, do md5sum on iso, burn at 4x, make sure you burn as 'Image', etc.

---

### Post by miershpedankl on 2007-08-23
I've tried another cd, even a later version of Ubuntu - same problem. 

I'll give the 4x method a try.  I sorta understand what md5sum is - checks to see if the hashes on the cd match the hashes on the downloaded file, right?  I don't even know what I just said, but I think that is right.  \

In the meantime it won't hurt to burn at a slower speed and then try from there, so that's what I'll do.

Thanks!

---

### Post by merlinus on 2007-08-23
If you cannot view the cd contents in windows, then your disk and/or cd drive has defects, or the download is corrupt.

As Pumalite said, do a checksum.  Info here:

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

-merlin

---

### Post by miershpedankl on 2007-08-23
Thanks for the site - I will look it up.  However, since I am typing - I am looking at the contents now via Debian.  Is there a way to install fro Debian?

---

### Post by Pumalite on 2007-08-23
Why would you want to do that?

---

### Post by miershpedankl on 2007-08-23
Well, I guess I was thinking that I could load it from Debian, but I guess that doesn't make any sense.  Ok, nevermind.  Gotta boot with it. :lolflag:

---

### Post by miershpedankl on 2007-08-23
But, if I can view it via Debian wouldn't that mean that the cd/files are not corrupt?

---

### Post by merlinus on 2007-08-23
Not necessarily.  Try booting from the cd on a different computer or cd drive.

Since your computer cannot boot from the cd, there are clearly problems.

You might check the BIOS boot settings to ensure that the cd is listed before your hdds.

-merlin

---

### Post by Pumalite on 2007-08-23
Also posting your specs would help us help you better. I still have the feeling, as I said earlier that you might need the Alternate CD, depending on your specs. What graphics?. How much memory do you have?.

---

### Post by miershpedankl on 2007-08-23
I had already set the BIOS settings.  On this desktop I only have 320MB RAM, but that's enough, right?  

Graphics - crap, where do I find the graphics info? (sorry, don't mean to waste your time) :(

Should I avoid using RW cd for this?

I didn't have WinMD5Sum so I m installing that and the recommended cd burner.

Oh well, it's late - thanks for your help, I'll pick this up again in a couple of days maybe.  Hoping to free myself of Windows once and for all!!

Thanks

---

### Post by miershpedankl on 2007-08-28
Re-burning the image at 4x fixed my issues. :)  Thanks for your help - miershpedankl

---

### Post by Pumalite on 2007-08-28
I hope you are using the Alternate CD iso. With your specs you might have trouble booting the Live CD.

---

### Post by miershpedankl on 2007-08-28
Already booted with the cd and installed OS with the standard iso download from the site.  

Cheers,
miershpedakl

---

