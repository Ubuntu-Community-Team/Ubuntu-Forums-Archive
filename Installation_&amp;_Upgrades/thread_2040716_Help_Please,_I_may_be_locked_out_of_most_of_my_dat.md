---
title: "Help Please, I may be locked out of most of my data."
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by Bogmaster on 2012-08-11
Yes, I will admit that I should have made more regular backups.  I normally run Ubuntu off a USB hard drive so I can use skype, etc on my work laptop as I travel frequently.  I decided it was time to do a full backup since it had been a while so I got a new USB HDD for the task.  I was brushing up on DD and was burning the install image to a USB card to do a fresh install on the new drive after backing up my windows partition.  The USB startup disk utility properly identified the .iso image of the installer and the USB card on which I wanted to burn it.  It then requested the authentication to copy the loader.  Since it did not specify, I thought it meant to the USB card, but instead, it burnt the loader to my old and full USB HDD.  

I plan to back up my old linux partition on the drive which contains my home folder before going further.

I can see the partition that my home folder is on, but it is encrypted.  I may have the encryption key somewhere, but it is doubtful, and even when I had it, I was unable to access the data from another running system when I plugged in the USB drive.

Did the live install overwrite the bootloader/MBR?
If so, is it possible to retrieve the initial bootloader/MBR?

If I try to reinstall, will it recognize my existing home folder and allow access again with the initial root password?

Is all hope lost for my home folder and this should just be taken as a good lesson for the future?

Thank you for any responses.

---

### Post by darkod on 2012-08-11
If only the bootloader was overwritten, everything should work fine after you put it back. And that should be easy.

Do you have ubuntu cd or usb with the version you were running? If not, can you make one?

You will need to boot it into live mode (Try Ubuntu). Once you get there, open terminal and post the output of:
```
sudo fdisk -l
```

---

