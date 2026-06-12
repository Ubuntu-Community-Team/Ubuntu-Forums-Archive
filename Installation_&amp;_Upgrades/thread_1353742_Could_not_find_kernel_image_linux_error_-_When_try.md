---
title: "Could not find kernel image: linux error - When trying with a Live USB drive"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by Subbu_09 on 2009-12-13
Hi All,
 
I am new to Linux and after few hiccups initially, was able to successfully boot Ubuntu 9.10 Karmic Koala with a working LIVE cd. Infact, I also received the LIVE cd from Ubuntu yesterday. Now, I run into a problem when I try to create a LIVE USB drive.
 
I tried with Unetbootin and the Program in Pendrivelinux in my Windows XP and also 
I tried the USB disk creator from the ADMINISTRATION link while running the Live CD.
I get the same following error, when I make my BIOS to boot from the USB.
 
The error (Could not find kernel image: linux error) it seems, is very notorious and common one - as there are a lot of entries available in the internet for different versions of Linux. So, it will not be a surprise for many. But, what is surprising for me is, I am yet to find a single, comprehensive fix that will solve this issue, if not for all who reported it, but at least, it could have been Linux version specific. But, to my surprise, I should say there is NONE as of today.
 
Though, there are some solutions suggested, including the one given in PendriveLinux
themselves, it is not very user friendly OR easy to understand for a Non-Linux users.
 
Can some one give a step-by-step guide or instruction set to resolve this issue?
That would be great.
 
FYI - I use a 4 GB USB drive - Transcend FlashJet drive - and formatted it in FAT32.
 
I also used the HP USB Disk format tool as suggested in some forums before starting
my installtion in all the above methods I have suggested. The only known method that
I am yet to try is using the PendriveLinux's application to run from Ubuntu. But, I am sure that will also fail. because, there are no issues in my system when I boot with the LIVE CD. The boot error comes only when I use the USB disk.
 
I have also seen suggestions like one should use only USB drives upto 2GB disk space
(why is it so and what is the need for such a restriction?) and use only FAT16 formatting (instead of FAT32). But, I have not seen one common solution - as this error seems to be common and basic problem across all linux distros - that every one
can follow, of course with few changes if there need to be some, based on the distros.
 
I am hoping this thread would give answers to me as well as many users who have
the same issue and have reported it at different forums, but yet to find a easy to follow step by step instruction set - especially for Non-Linux users........
 
Thanks to all those tech-savvy Linux (Ubuntu users) guys, who can jump onto this and provide a quick and lasting solution for mee.....
 
Thanks
Subbu.

---

### Post by phillw on 2009-12-13
> **Subbu_09 said:**
> Hi All,
 
I am new to Linux and after few hiccups initially, was able to successfully boot Ubuntu 9.10 Karmic Koala with a working LIVE cd. Infact, I also received the LIVE cd from Ubuntu yesterday. Now, I run into a problem when I try to create a LIVE USB drive.
 
I tried with Unetbootin and the Program in Pendrivelinux in my Windows XP and also 
I tried the USB disk creator from the ADMINISTRATION link while running the Live CD.
I get the same following error, when I make my BIOS to boot from the USB.
 
The error (Could not find kernel image: linux error) it seems, is very notorious and common one - as there are a lot of entries available in the internet for different versions of Linux. So, it will not be a surprise for many. But, what is surprising for me is, I am yet to find a single, comprehensive fix that will solve this issue, if not for all who reported it, but at least, it could have been Linux version specific. But, to my surprise, I should say there is NONE as of today.
 
Though, there are some solutions suggested, including the one given in PendriveLinux
themselves, it is not very user friendly OR easy to understand for a Non-Linux users.
 
Can some one give a step-by-step guide or instruction set to resolve this issue?
That would be great.
 
FYI - I use a 4 GB USB drive - Transcend FlashJet drive - and formatted it in FAT32.
 
I also used the HP USB Disk format tool as suggested in some forums before starting
my installtion in all the above methods I have suggested. The only known method that
I am yet to try is using the PendriveLinux's application to run from Ubuntu. But, I am sure that will also fail. because, there are no issues in my system when I boot with the LIVE CD. The boot error comes only when I use the USB disk.
 
I have also seen suggestions like one should use only USB drives upto 2GB disk space
(why is it so and what is the need for such a restriction?) and use only FAT16 formatting (instead of FAT32). But, I have not seen one common solution - as this error seems to be common and basic problem across all linux distros - that every one
can follow, of course with few changes if there need to be some, based on the distros.
 
I am hoping this thread would give answers to me as well as many users who have
the same issue and have reported it at different forums, but yet to find a easy to follow step by step instruction set - especially for Non-Linux users........
 
Thanks to all those tech-savvy Linux (Ubuntu users) guys, who can jump onto this and provide a quick and lasting solution for mee.....
 
Thanks
Subbu.

Hi,

Using the utility within the LiveCD to make a booting USB is easy & reliable.
Getting your Computer to accept the USB device, however, is slightly more complicated - some BIOS's *SAY* that they can boot from USB, but are telling fibs !!

Each computer is slightly different, but, if you have the BIOS options of 'Boot from USB' and 'Boot from USB Hard Drive' - try the latter one. It worked for me :-)  Have a look at what external devices it says you can boot from, and give them each a try.

Hope that gets you up & running.

/edit - PenDrive linux provide, along with some quite wacky things to do with a pen-drive, a test for computers to see if they are 'fibbing' and seting your BIOS, it's here --> [http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

Regards,

Phill.

---

### Post by Subbu_09 on 2009-12-13
> **phillw said:**
> Hi,
 
Using the utility within the LiveCD to make a booting USB is easy & reliable.
Getting your Computer to accept the USB device, however, is slightly more complicated - some BIOS's *SAY* that they can boot from USB, but are telling fibs !!
 
Each computer is slightly different, but, if you have the BIOS options of 'Boot from USB' and 'Boot from USB Hard Drive' - try the latter one. It worked for me :-) Have a look at what external devices it says you can boot from, and give them each a try.
 
Hope that gets you up & running.
 
/edit - PenDrive linux provide, along with some quite wacky things to do with a pen-drive, a test for computers to see if they are 'fibbing' and seting your BIOS, it's here --> [http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)
 
Regards,
 
Phill.
 
Thank you Phill for that update.
 
In fact, I did try ALL options available in my BIOS relative to USB - like USB HDD, USB FDD, USB RMD HDD, USB RMD FDD and even USB CDROM(!?) but to no avail. I also
tried the PenDrive Linux's program to test my BIOS to boot from my 4 GB USB drive.
It also failed to boot with the same error message. What does this mean? 
 
Like you said, my BIOS simply mimicks being able to boot from a USB device, but in reality unable to do so?. I have tried all options available in the inernet for creating a bootable USB disk with Ubuntu 9.10 - tried both from Windows XP and from my Ubuntu Live CD, but all of them failed with the boot error, some of them with the could not find the linux kernel image error message.
 
Is there any fix for this? Mine is an AMIBIOS from American Megatrends. I am desparately trying to fix this issue, but all my efforts ended in vain.
 
Please give any workarounds that may be available to make my BIOS boot from a USB, even though it does list all the USB devices like I mentioned above.
 
Thanks,
Subbu.

---

### Post by phillw on 2009-12-13
> **Subbu_09 said:**
> Thank you Phill for that update.
 
In fact, I did try ALL options available in my BIOS relative to USB - like USB HDD, USB FDD, USB RMD HDD, USB RMD FDD and even USB CDROM(!?) but to no avail. I also
tried the PenDrive Linux's program to test my BIOS to boot from my 4 GB USB drive.
It also failed to boot with the same error message. What does this mean? 
 
Like you said, my BIOS simply mimicks being able to boot from a USB device, but in reality unable to do so?. I have tried all options available in the inernet for creating a bootable USB disk with Ubuntu 9.10 - tried both from Windows XP and from my Ubuntu Live CD, but all of them failed with the boot error, some of them with the could not find the linux kernel image error message.
 
Is there any fix for this? Mine is an AMIBIOS from American Megatrends. I am desparately trying to fix this issue, but all my efforts ended in vain.
 
Please give any workarounds that may be available to make my BIOS boot from a USB, even though it does list all the USB devices like I mentioned above.
 
Thanks,
Subbu.

You'll have to go a googling with your bios type and release number - there may be an update for it. Be careful with flashing BIOS - If you mess it - you WILL kill your machine.
Fortunately, the more modern bios's have a manufacturers fail-safe method of doing a flash - I'd strongly recommend you follow it !!

/edit - there is a long and quite involved method, using syslinux, to get your computer to 1st boot off the hard-drive, then go to the usb device - It's messy and I've never tried it - but, it may be an option for you.

Regards,

Phill.

---

### Post by Subbu_09 on 2009-12-15
> **phillw said:**
> You'll have to go a googling with your bios type and release number - there may be an update for it. Be careful with flashing BIOS - If you mess it - you WILL kill your machine.
Fortunately, the more modern bios's have a manufacturers fail-safe method of doing a flash - I'd strongly recommend you follow it !!
 
/edit - there is a long and quite involved method, using syslinux, to get your computer to 1st boot off the hard-drive, then go to the usb device - It's messy and I've never tried it - but, it may be an option for you.
 
Regards,
 
Phill.
 
Thank you Phill and I will never ever try to mess with my BIOS for trying Ubuntu thru' the LIVE USB as it has a chance of rendering my machinge useless. However, I did read somewhere to fool the BIOS to boot from the USB, after making it look like a ZIP drive, which I guess my BIOS should recognize and boot witout any problems. 
 
However, I have to follow a little involved process to make my USB mimic like a ZIP drive and then boot Ubuntu from there. I guess, that is the only way for me now and 
I am not sure if the SYSLINUX method you have suggested here is the same or not.
 
I will try that when I have little time and post the results if it was successful.
 
Thanks,
Subbu.

---

