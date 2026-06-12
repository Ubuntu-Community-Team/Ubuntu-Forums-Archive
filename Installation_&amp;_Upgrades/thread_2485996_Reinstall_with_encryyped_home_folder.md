---
title: "Reinstall with encryyped home folder"
date: 2023-04-17
forum: Installation &amp; Upgrades
---

### Post by makitso on 2023-04-17
Ubuntu 22.04
I encrypted the home folder, that is on its own partition, using encryptfs.  Looks like I need to reinstall the os.  
Will the ubuntu installer figure this out or do i need to start over with a clean install of /home and restore its contents?
.

---

### Post by TheFu on 2023-04-17
encryptfs is deprecated.

---

### Post by makitso on 2023-04-17
> **TheFu said:**
> encryptfs is deprecated.

Yes, I know.  However, this laptop is a dual-boot system so I cant encrypt the drive.

---

### Post by makitso on 2023-04-17
> **TheFu said:**
> encryptfs is deprecated.

Yes, I know.  However, this laptop is a dual-boot system so I couldn't encrypt the whole drive.

---

### Post by TheFu on 2023-04-18
[https://techterms.com/definition/deprecated](https://techterms.com/definition/deprecated)
You shouldn't use it. It has been about 5 yrs since it was last supported. If it does work, it would be luck and with the many installer changes across Ubuntu flavors, it is unlikely that anyone tested it.

But you are free to try anything you like.  Please, please, please, make complete system backups, since it is likely to cause data loss.

The alternative to using dual-boot is to run one of the OSes inside a virtual machine.  I've been doing that since about 2008. VMs work great, even on mid-level systems. I've never understood why people would choose to dual boot when VMs are so very easy and have been since around 2005.

---

### Post by guiverc on 2023-04-18
A number of Ubuntu releases included an option to include an encrypted home partition by default. I believe (*from memory*) Ubuntu 17.10 was one release to do that.

That security option still exists in Ubuntu repositories, but its **not** included by default on newer ISOs, thus to use an encrypted home partition for a *non-destructive* re-install (*including newer release; ie. upgrade via re-install*) you need only 

- boot the *live* system you want to install
- connect internet
- `sudo apt update`
- install required *encryption package* your existing encryption partition requires
- ( *I forget if mounting is required; I don't believe it is - but this needs to be correct *)
- start installer

Whilst I have a text file that I tend to read before I start the process myself (*if I can find it!; otherwise I work out the required package & mount appropriately & determine if it'll work when I start the installer by what options it offers me! otherwise exit installer & correct, restart installer & check etc*) but I can't find it.  I believe the package is `ecryptfs-utils` but I could be wrong sorry (*I'm thinking of the default Ubuntu 17.10 or whatever releases used to offer encrypted home*).

I've used this a number of times (*on laptops I'll take with me*), alas not often enough to recall details accurately sorry.  I can't guarantee this; and can't say that I performed it with 22.04, but I can say it was used with 18.04 & 20.04 multiple times (*& almost certainly I used it with 22.04 with a Xubuntu ISO*).  Do note: most of my installs after 17.10 have with been with *flavor* ISOs but I believe it'd work with all Desktop ISOs.

You can re-install a later release without data loss.

( *I only have some older laptops that still use encrypted home.. most laptops  I use have full disk encryption* )

---

### Post by TheFu on 2023-04-18
On Mint 21.1 (ubuntu 22.04 based)

```
$ apt search ecryptfs-utils
i   ecryptfs-utils                           - ecryptfs cryptographic filesystem (utilities)
```

---

### Post by makitso on 2023-04-24
> **guiverc said:**
> 

- boot the *live* system you want to install
- connect internet
- `sudo apt update`
- install required *encryption package* your existing encryption partition requires
- ( *I forget if mounting is required; I don't believe it is - but this needs to be correct *)
- start installer



Boy, I have tried every thing under the sun but can't get past the login screen on a reinstall of the OS.  
I installed ecryptfs-utils and cryptsetup, I even tried modprobeing crypd, crypto_simd and dm_crypt to the kernel but no help.
There must be something in the / that I am missing.

---

### Post by TheFu on 2023-04-24
cryptsetup is for LUKS and whole drive encryption.

The easy solution for this is to run one of the OSes inside a VM under the other OS, then use the default encryption method from the OS directly installed on the hardware to protect the VM.  Since around 2008, virtual machines have been great for desktops, provided you aren't hoping to game inside the VM or do 4k video editing.

Not sure how much I'd trust MSFT's disk encryption. Don't they automatically upload the keys to MSFT servers?  
[https://thehackernews.com/2015/12/windows-encryption-key-backup.html](https://thehackernews.com/2015/12/windows-encryption-key-backup.html) shows they did in 2016, but I've avoided MSFT stuff since before then.

From 2023:
[https://learn.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10](https://learn.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10) says this:
> Unlike a standard BitLocker implementation, BitLocker Device Encryption is enabled automatically so that the device is always protected. The following list outlines how BitLocker Device Encryption is enabled automatically:

    When a clean installation of Windows 11 or Windows 10 is completed and the out-of-box experience is finished, the computer is prepared for first use. As part of this preparation, BitLocker Device Encryption is initialized on the operating system drive and fixed data drives on the computer with a clear key that is the equivalent of standard BitLocker suspended state. In this state, the drive is shown with a warning icon in Windows Explorer. The yellow warning icon is removed after the TPM protector is created and the recovery key is backed up, as explained in the following bullet points.

    If the device isn't domain joined, a Microsoft account that has been granted administrative privileges on the device is required. When the administrator uses a Microsoft account to sign in, the clear key is removed, a recovery key is uploaded to the online Microsoft account, and a TPM protector is created. Should a device require the recovery key, the user will be guided to use an alternate device and navigate to a recovery key access URL to retrieve the recovery key by using their Microsoft account credentials.


Whenever I've looked up how to manually add LUKs encryption at install time to any Linux, the manual steps were complex and many pages long.

I tried encryptfs before decided it didn't meet my needs because backups didn't work unless all user's were logged in with a GUI session. That's not possible on a multi-user system.  All the file-based encryption tools leak metadata about the files, which is one of the core values good encryption avoids.  

We all have different needs, of course.

---

### Post by makitso on 2023-04-25
Solved my problem.  Thanks to @guiverc hint I did the following:
Once the install is complete reboot.
At the login screen if try logging in it loops back to the login screen.
So, I did dropped into terminal mode at the login screen and did a:
sudo apt update
sudo apt install ecryptfs-utils cryptsetup
This rebuilt the kernel with encryption.  
Now, a reboot allows the login screen to work correctly and I am back on the air.

---

