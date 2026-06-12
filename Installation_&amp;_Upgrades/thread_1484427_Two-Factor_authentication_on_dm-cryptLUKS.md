---
title: "Two-Factor authentication on dm-crypt/LUKS"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by KwukDuck on 2010-05-15
Hello,    

I'm fairly new to Ubuntu and i finally got my netbook installed with the alternate iso (v10.04) and guided partitioning with encryption. 

Since i'm on-the-road a lot encryption is crucial, with windows i've always used TrueCrypt and DiskCryptor, this is very easy to setup and allows me to create usb/cd devices that i can boot off and contain a keyfile, on boot it also requires a passphrase. 

Currently all i need to do is boot from harddisk and enter my passphrase.  I would like to be able to boot from external device (in this case USB) that contains the bootloader and an integrated keyfile, also it should requist the passphrase. 

I found a guide on how to achieve two-factor authentication with dm-crypt on feisty but it's quite an old guide and is realy realy complicated for a newbie.    

Is there a fairly simple way to set this up?    

Thanks for any help you guys may offer.    

KD

---

### Post by KwukDuck on 2010-05-17
I asked around on IRC too but all i got back was "use debian".  Also i was told to 'just install /boot on the removable device'. Wich does not give me what i want, it needs to have an authenticating part on it aswell, anyone can make a device with /boot to make it work.

---

