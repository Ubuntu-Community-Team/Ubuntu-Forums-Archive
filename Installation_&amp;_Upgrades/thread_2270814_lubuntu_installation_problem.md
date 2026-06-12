---
title: "lubuntu installation problem"
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by soma094 on 2015-03-25
I have noticed an installation problem with Lubuntu 14.10 32 bit version.

I have downloaded it from the official website and it wont boot from the usb.

Anyone else noticed this problem? any ideas how to fix this issue? 

With the 64 bit version is everything okay though. :)

---

### Post by Rex Bouwense on 2015-03-25
Worked fine for me.  That is what I am using.  Did you check the md5sum of the download?  Did you burn the image at the slowest possible speed?

---

### Post by soma094 on 2015-03-25
Yes i checked the md5sum and its fine, i did it with UNetbootin is there an option for adjusting the burning speed?

---

### Post by yancek on 2015-03-25
Did you get any warning/error message from unetbootin while trying to create the bootable flash drive?
Can you test the flash drive on another computer to eliminate that as a problem?
And what happens when you try to boot from the flash drive?

---

### Post by soma094 on 2015-03-25
no i didnt get any warning/error messages from unetbootin.

what happens is that it boots up the system normally (im using ubuntu 14.04 LTS 32 bit)

it also doesnt work on another pc i tried out. that one runs win8.1 64bit

i did everything as it is mentioned in the tutorials and as i mentioned earlier it worked with the 64 bit versions. I also tested it with Lubuntu 14.04 LTS 32bit and it also did not work.

---

### Post by ajgreeny on 2015-03-25
It is often necessary to use a keypress in order to get a machine to boot to a USB irrespective of how the priority in the BIOS is set.  Try F8 or F11, which is what I have to use on two separate machines I work with.

---

### Post by soma094 on 2015-03-26
Well i tried that too with both the 14.04 LTS 32bit version and the 14.10 32 bit version but it still booted up the system instead.

Strangely the 64 bit versions for both work for me fine :)

---

### Post by ajgreeny on 2015-03-26
Is this by any chance a machine running with UEFI and GPT partitioning?

I think you need a 64 bit OS for that hardware which would explain your problem.

---

### Post by soma094 on 2015-03-27
yep its running with that :) so i suppose then i have the solution :)

Thanks for the help :)

---

