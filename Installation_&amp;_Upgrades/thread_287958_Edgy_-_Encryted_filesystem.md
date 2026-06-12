---
title: "Edgy - Encryted filesystem"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by RichJacot on 2006-10-29
Hello,  Has anyone gotten an encrypted filesystem (LUKS) working on Edgy?  Not just a directory, but everything but the /boot partition?  
I've followed this howto, [https://wiki.ubuntu.com/EncryptedFilesystemHowto4]("https://wiki.ubuntu.com/EncryptedFilesystemHowto4") but without success.  
All appears to go well but upon reboot I get, "/dev/mapp/cryptoroot does not exist. Dropping to a shell". 

Does anyone have any ideas or has anyone got it working with Edgy?  (I'm doing a fresh install of Edgy)

Thanks

---

### Post by bushwacker on 2006-10-30
I'm having this exact same problem after upgrading from Dapper via apt-get (That was a total pain in of itself!). since swap and /home are crypted for me, Edgy gets me to a recovery console, then I have to manually mount. Luckily all data is intact, but it used to run with no errors, asking me for my LUKS password on bootup. It was per the [https://help.ubuntu.com/community/EncryptedFilesystem3](https://help.ubuntu.com/community/EncryptedFilesystem3) instructions (DM-Crypt/LUKS instead of RSA (much safter- no keyfiles to loose!).

Setting up LUKS with Knoppix or the ubuntu livecd is easy, but I'm not sure how to restore the functionality.

---

