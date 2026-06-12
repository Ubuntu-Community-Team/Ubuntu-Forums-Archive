---
title: "yubikey-luks with just 1fa"
date: 2023-10-16
forum: Installation &amp; Upgrades
---

### Post by kozimodo2 on 2023-10-16
I've finally decided to try to do full disk encryption using a Yubikey to simplify the boot process.  I'm hoping to be able to boot with just the Yubikey inserted and not have to type the challenge password.  I followed [https://www.endpointdev.com/blog/2022/03/disk-decryption-yubikey/](https://www.endpointdev.com/blog/2022/03/disk-decryption-yubikey/) but it is not working as expected and still asks me for the challenge password.

Has anyone set up Ubuntu successfully with 1fa and a Yubikey?  If so, what do I need to do differently?

---

### Post by TheFu on 2023-10-16
In general, not using the challenge/response method is a bad idea. You could use a USB flash drive with a key-file instead, because that would be better than using a yubikey with static output (which is the other option you have).  There are lots of guides for setting up LUKS to use a keyfile. I'm sure you can find them.  Just don't lose the keyfile or have only 1 file on the USB storage. Make it slightly challenging for the bad guys to gain access, please.

BTW, LUKS has 8 slots so you can add more methods to unlock the LUKS storage without removing the challenge/response method.

---

### Post by kozimodo2 on 2023-10-19
I understand that 1fa is less secure and I'm ok with that -- at least it's encrypted.  I just want to know if yubikey-luks supports 1fa or not.  Following the instructions in the linked page does not seem to work.  If anyone has successfully gotten it to work, I would love to see what your config file looks like.

---

### Post by TheFu on 2023-10-19
> **kozimodo2 said:**
> I understand that 1fa is less secure and I'm ok with that -- at least it's encrypted.  I just want to know if yubikey-luks supports 1fa or not.  Following the instructions in the linked page does not seem to work.  If anyone has successfully gotten it to work, I would love to see what your config file looks like.

There is no config file for having yubikey dump the static, random, characters.  The yubikey tools let you set it - or half of it (I don't recall).  My old had 50% what I knew and 50% what the Yubi output.  To LUKS, it is just a static passphrase like any other and never, ever, changes until you manually replace it with a new one.  You still need to long press the Yubikey for it to be entered through the HID playback.  That method was before I setup challenge-response once Linux finally made that easy.  It was on a laptop that I traveled with and needed the extra protections. Actually, I even booted from an external SDHC card to prevent the evil-maid attack when traveling.

Like I said, better to use a 4K keyfile on a flash stick if you want LUKS Open to happen nearly automatically.  This would be more secure than the Yubikey's limited static playback capability and do what you want cheaper.  OTOH, if you use the yubikey for OAuth and/or TOTP and/or FIDO reasons as well, having multiple methods for LUKS decryption is good.

[Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it) shows how to have a key file automatically used on 1 system. The demo is for an encrypted USB flash drive, but you'll figure it out.

This is a bad idea, not having the "something YOU know" part, but if the system is in a locked room that only you have access into and you trust that nobody else will break in, fine.  I suppose it is also a good way to protect data on a disk that might need to be returned for warranty replacement that you'd rather NOT have the drive vendor having access, but really don't have any other security concerns.

Google found this using a Yubikey to unlock LUKS [https://www.guyrutenberg.com/2022/02/17/unlock-luks-volume-with-a-yubikey/](https://www.guyrutenberg.com/2022/02/17/unlock-luks-volume-with-a-yubikey/)

Some people run their entire OS off USB3 SSDs and they only keep data on other storage.  One of the guys who does that is a former federal agent. His stance makes my paranoia look insignificant.  He's see some things.

---

### Post by kozimodo2 on 2023-10-21
It turns out that the reason 1fa was not working for me is because the `yubikey-luks` package in the Ubuntu repo is not up to date.  Cloning and compiling it myself works!

---

