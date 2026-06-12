---
title: "Can't verify sha256 sum as command gives me no DSA key"
date: 2022-08-22
forum: Installation &amp; Upgrades
---

### Post by empleat on 2022-08-22
Hello,

I want to verify my download, but command: ```
gpg --keyid-format -long --verify sha256sum.gpg sha256
``` - note command is corrent I copy paste it and now just rewriting it from head. It gives me only RSA key and no DSA key, so I can't request public key from key server in the next command from guide: how to verify your download.

Thanks for help!

---

### Post by TheFu on 2022-08-22
Download of what?

ISO files typically have a separate text file in the same download location with sha256 signatures.  
Running 

```
$ sha256sum /path/to/Ubuntu-xxxxx-yyy-zzz.iso
```
Software packages provided by Debian packages, repos and PPAs are all cryptographically signed and those signatures are validated before install, just after download.
If using sha256, DSA isn't used.

Perhaps if you explained exactly the use-case and showed the exact command used?

---

### Post by empleat on 2022-08-23
Sorry. Of latest Ubuntu for desktop.
> [COLOR=#000000]Software packages provided by Debian packages, repos and PPAs are all cryptographically signed and those signatures are validated before install, just after download.[/COLOR]
No idea what this means.
> [COLOR=#000000]If using sha256, DSA isn't used.[/COLOR]
I Am just following this tutorial: [https://ubuntu.com/tutorials/how-to-verify-ubuntu#4-retrieve-the-correct-signature-key](https://ubuntu.com/tutorials/how-to-verify-ubuntu#4-retrieve-the-correct-signature-key) 
I need DSA key to request public key from Ubuntu keyserver to verify my gpg signature, to verify sha256sum.

The command: > [COLOR=inherit][FONT=&amp]gpg --keyid-format long --keyserver hkp://keyserver.ubuntu.com --recv-keys 0x46181433FBB75451 0xD94AA3F0EFE21092[/FONT][/COLOR]
requires also DSA key, which I don't get by running previous command, only RSA!

---

### Post by TheFu on 2022-08-23
[https://ubuntuforums.org/showthread.php?t=2477894&p=14107912#post14107912](https://ubuntuforums.org/showthread.php?t=2477894&p=14107912#post14107912) is how I validate Ubuntu ISO files.  The compression used can chance, but the steps are about the same besides that.  The SHA256SUM file (without the .gpg extension) contains all we need to check the validity of the ISO.


That tutorial has 2 commands. The output from the first is necessary for the 2nd, if you insist on using the GPG keys.  

There are 5-500 different ways to solve any issue on Linux.  Picking the easiest when we are new is recommended.

---

### Post by &amp;KyT$0P# on 2022-08-23
If you already have some version of Ubuntu installed, the GPG keys for verifying those sha256sums are already installed somewhere on your system.  Probably one of the keyrings in [FONT=Courier New]/etc/apt/trusted.gpg.d/[/FONT]

---

### Post by empleat on 2022-08-23
> [URL="https://ubuntuforums.org/showthread.php?t=2477894&p=14107912#post14107912"]
https://ubuntuforums.org/showthread....2#post14107912[/URL][COLOR=#000000] is how I validate Ubuntu ISO files. The compression used can chance, but the steps are about the same besides that. The SHA256SUM file (without the .gpg extension) contains all we need to check the validity of the ISO.[/COLOR]


[COLOR=#000000]That tutorial has 2 commands. The output from the first is necessary for the 2nd, if you insist on using the GPG keys.[/COLOR]

[COLOR=#000000]There are 5-500 different ways to solve any issue on Linux. Picking the easiest when we are new is recommended.
[/COLOR]
Could you instead tell me please how to obtain public keys to verify gpg signature? Thanks! It is not my fault that tutorial is wrong.

> **halogen2 said:**
> If you already have some version of Ubuntu installed, the GPG keys for verifying those sha256sums are already installed somewhere on your system.  Probably one of the keyrings in [FONT=Courier New]/etc/apt/trusted.gpg.d/[/FONT]
But you need to verify gpg signature first to verify sha256 sum!

---

### Post by &amp;KyT$0P# on 2022-08-23
> **empleat said:**
> But you need to verify gpg signature first 

That's the step I'm talking about.  On my Xubuntu 22.04 system, to verify the gpg signature of the sha256sums for Ubuntu 22.04.1 iso, I would just do
```
gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg --verify SHA256SUMS.gpg SHA256SUMS
```

No need to fetch anything from a keyserver.

---

### Post by empleat on 2022-08-31
> **halogen2 said:**
> That's the step I'm talking about.  On my Xubuntu 22.04 system, to verify the gpg signature of the sha256sums for Ubuntu 22.04.1 iso, I would just do
```
gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg --verify SHA256SUMS.gpg SHA256SUMS
```

No need to fetch anything from a keyserver.
I try only RSA key and I realized I forgot to put 0x before the command it worked and fetched public key. I will also will use method to import keys from local ubuntu keyring to be sure. 

Thanks for help :)

---

