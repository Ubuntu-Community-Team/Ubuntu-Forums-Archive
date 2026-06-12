---
title: "ZFS encryption question"
date: 2022-04-08
forum: Installation &amp; Upgrades
---

### Post by david509 on 2022-04-08
In future, would it be possible to install Ubuntu with ZFS *native* encryption, for encrypting the **entire** Ubuntu OS (including swap space)?

A passphrase required on boot.

---

### Post by TheFu on 2022-04-08
Anything is possible - in the future, if we go far enough.

---

### Post by Impavidus on 2022-04-09
Except that the software used to decrypt the filesystem cannot be encrypted itself. That's why we use a /boot partition on encrypted systems.

---

### Post by tea for one on 2022-04-09
Some vendors have included UEFI options which can password-protect the drive.

One password to access the drive.
Second password to decrypt the filesystem.
Third password for user log-in.

I would bet that Yubikey users could add another level of protection.

Must go now, my car alarm is bleeping.........;)

---

### Post by david509 on 2022-04-09
Can anyone suggest this idea to the Ubuntu devs?
Native ZFS encryption is meant to be fastest, if it can encrypt the entire OS?

EDIT: obviously excluding the /boot, just encrypt the data and swap areas, so anything saved locally is fully encrypted.

---

### Post by TheFu on 2022-04-09
> **tea for one said:**
>  I would bet that Yubikey users could add another level of protection.

I use a few Yubikeys that are integrated with LUKS to do drive encryption.  They are challenge/response setups and work completely offline.  The way it works is grub asks for a passphrase and for the yubikey to be inserted. Then I enter it, it is read by the yubikey when I looooooong press the activation on the device, which reads the challenge and outputs a unique response based on the challenge passphrase that I've entered.  LUKS only knows that the response is or is not valid (within the 8 slots of acceptable passphrases) and either unlocks the LUKS container and boots, or it doesn't.

I have a few yubikeys setup for the challenge/response on my laptop. This is necessary since losing 1 yubikey would be really bad and leave me without any access, short of wipe and reinstall. The LUKS guys were smart by having 8 slots which can be used for decrypting the LUKS header which can then decrypt the full LUKS container. Sadly, I haven't come across a password manager with multiple crypto-key support.  KeePassXC supports OneKey and Yubikey, but only with 1 slot. They expect people to force multiple keys to output identical responses to the challenge.  That weakens the solution 50%. Now there are 2 devices in the world, not just 1, capable of unlocking the password manager.

LUKS is not native ZFS encryption.  But going back to at least 2013, people have been using ZFS inside LUKS encrypted containers successfully.  Any file system can go inside a LUKS container.  [https://help.ubuntu.com/community/encryptedZfs](https://help.ubuntu.com/community/encryptedZfs)  But this isn't the question asked by the OP.

---

### Post by david509 on 2022-04-09
If anyone is still wondering what exactly I mean...

The root / (absolutely everything) on an encrypted pool, swap space on the same/different pool, all using *native* ZFS encryption for faster performance over LUKS.

Password required at boot.

EDIT: the user selects the encryption option and passphrase in the Ubuntu installer.

---

### Post by TheFu on 2022-04-09
Do you happen to play BASS? ;)

LUKS en/decryption is pretty fast on systems with AES built into the hardware. Less than 3% overhead in my testing. Most CPUs have had AES-ni support for well over a decade.

Regardless, I can understand the desire for a single solution and think it will come .... in the future.

---

### Post by david509 on 2022-04-10
> **TheFu said:**
> Do you happen to play BASS? ;)

LUKS en/decryption is pretty fast on systems with AES built into the hardware. Less than 3% overhead in my testing. Most CPUs have had AES-ni support for well over a decade.

Regardless, I can understand the desire for a single solution and think it will come .... in the future.

If anyone knows how to get the wheels in motion. Make this happen for real in a future Ubuntu. :)

You never know, in Ubuntu 24.04 this could be a reality (native ZFS full encryption). I hope the devs are reading this. ;)

---

### Post by chpnp on 2022-04-15
I have not tried it, but if you have some time you can try this

[https://medium.com/@andaag/how-i-moved-a-ext4-ubuntu-install-to-encrypted-zfs-62af1170d46c](https://medium.com/@andaag/how-i-moved-a-ext4-ubuntu-install-to-encrypted-zfs-62af1170d46c)

---

