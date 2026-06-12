---
title: "Encrypted root file system can't boot"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2007-04-27
Hi All,

I have asked a similarly entitled question elsewhere however due to the fact I know have my answers to the initial questions I'm submitting a new thread.

I'm trying to create a LUKS-encrypted (aes256) root partition. Once this is successful, a home and swap will follow. Here is the linux part of my partitioning setup on which the install was done [Feisty LiveCD]
```
/dev/sda9 = linux-swap 1GB
/dev/sda10 = /boot , ext3, 500MB
/dev/sda11 = temporary / , xfs, 5GB
/dev/sda12 = root to be, xfs, 10GB
/dev/sda13 = /home, xfs, 10GB
```

I have now re-booted into the /dev/sda11 Ubuntu. First, I downloaded everything I thought I might need:
```
sudo apt-get install gcc build-essential kernel-package initramfs-tools cryptsetup
```

Then, I started the procedures necessary to create my encrypted root:
```
sudo modprobe aes_i586 sha256 dm_mod dm_crypt
cat /etc/modules gives: fuse lp sbp2 aes_i586 dm_mod dm_crypt sha256

```

Next, I created the encrypted partition and the filesystem on it:
```
sudo cryptsetup --verify-passphrase --verbose --hash=sha256 --cipher=aes-cbc-essiv:sha256 --key-size=256 luksFormat /dev/sda12
sudo cryptsetup luksOpen /dev/sda12 root
sudo mkfs -t xfs /dev/mapper/root
```

All of which ran successfully. I now have an encrypted root partition. Here I become somewhat lost. Firstly, I mounted and populated the encrypted root:
```
sudo mount /dev/mapper/root /mnt/root
sudo cp -avx / /mnt/root
```
Then I edited the fstab on the root to point "/" to /dev/mapper/root and likewise created a grub entry which passes root=/dev/mapper/root to the kernel. I reboot, try my setup and nothing. I'm dumped in (initramfs) - BusyBox.

[LIST]
[*]I know I have missed out crypttab on the encrypted partition. Whether or not it's there makes no odds, the partition is encrypted, so the kernel can't read it.
[*]I note that ```
cat /usr/share/initramfs-tools/scripts/local-top/cryptroot | grep cryptsource
``` returns the line cryptsource="". Changing this to cryptsource="/dev/sda12" rendered my system unbootable last time I tried it.
[*] I note that from initramfs I can run cryptsetup, mount my encrypted file system and read it.
[*] However, /dev/mapper/root doesn't show up initially. I created a script in /etc/initramfs-tools/scripts/local-top containing this:
```
#!/bin/sh
modprobe aes_i586 cbc dm_mod dm_crypt
cryptsetup luksOpen /dev/sda12 root
```
chmod +x of course. Re-updating initramfs made no difference.
[/LIST]

So, in brief, I've narrowed down the problem to the fact that /dev/mapper/root isn't created when the initramfs is loaded, and hence can't be the root file system. My question is therefore how do I get it mounted?

Thanks very much for all your help - I've used the ubuntu wiki and various tutorials, even a German one to get this far but I seem to be missing a crucial part...

Quark_77

---

### Post by quark_77 on 2007-04-27
I've booted from the encrypted partition, I used the following script:

Loaction: /etc/initramfs-tools/scripts/local-top:
```
#!/bin/sh 
# Load AES module...
modprobe aes_i586

# mount (or try to) the encrypted partition...

# now use the command...
cryptsetup luksOpen /dev/sda12 root
sleep 10
# AND WE ARE DONE

```

The sleep 10 seems to have done the trick... it gives us time to enter the password.

[COLOR="DarkOrange"]New question then: this doesn't seem to be the nicest way of doing things - How do I change this so that the boot process waits indefinitely for the LUKS password?[/COLOR]

---

