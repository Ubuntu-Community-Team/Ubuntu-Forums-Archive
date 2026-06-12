---
title: "How to get my own compiled kernel signed to pass the check of secure boot?"
date: 2017-03-21
forum: Installation &amp; Upgrades
---

### Post by hellofromme on 2017-03-21
I'm compiling linux kernel 4.4.52 on ubuntu 16.04.2(4.4.0-67-generic), but it gets stuck at ```
"Loading initial ramdisk..."
```, **no matter for normal boot or upstart or even recovery mode. **I guess this might not be the problem of my configuration, but because of the existence of [B]secure boot.

[/B]Acutally, I find that every image I download with ```
apt dist-upgrade
``` will come together with a file called ```
vmlinuz-<version>.efi.signed
```, and it seems to have something to do with the Canonical's private key, which is also used to sign the version of GRUB according to [http://askubuntu.com/questions/254533/what-is-vmlinuz-efi-signed](http://askubuntu.com/questions/254533/what-is-vmlinuz-efi-signed).

So my question is that how to replace the ubuntu kernel with my own compiled kernel? Is there any method other than disable secure boot in BIOS and switch to non-UEFI way? Thanks.

---

### Post by mörgæs on 2017-03-22
> **hellofromme said:**
> I guess this might not be the problem of my configuration, but because of the existence of **secure boot.**

Yes, this is a good (or bad) example of what 'Secure' Boot is about. It will get increasingly difficult for users to modify a kernel.

'Secure' Boot should never have been a part of UEFI and I suggest that the proper solution is to switch it off.

---

### Post by jeff666 on 2017-03-23
legacy mode doesn't really mean you don't have a uefi, the eufi boot tasks are altered but uefi services still can run (with no secure boot). Any way when compiling your custom kernel did you use the Ubuntu .config file (just a guess but maybe it is just a variable and it will just automatically do it)?

check this out (please let me know if it works i won't mid also using secure boot keys;)
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

---

### Post by hellofromme on 2017-03-27
@[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") @[**[COLOR=#000000]jeff666[/COLOR]**]("https://ubuntuforums.org/member.php?u=2059374") Thanks to you both, and sorry for the delay. I didn't try using openssl to generate a key, but I did the following to make it boot.
1. goto UEFI util(my motherboard is ASUS, maybe this step is a little different in other motherboards), set the 'OS Type' option to 'Other OS'; then set 'Launch CSM' option to 'Enabled'(although that's its original value), according to [https://www.asus.com/support/faq/1004383](https://www.asus.com/support/faq/1004383)
2. use the 'mokutil' sofware to disable ubuntu validation, `sudo mokutil --disable-validation`;

Then after verify the password, I can boot in insecure mode. I'm not sure which step worked but the problem was solved. Another thing to notice is that I later tried to recompile a whole new 4.4.55 kernel with validation enabled(mokutil --enable-validation), and it could boot... So I guess there still might be somthing wrong with my configuration? But anyway, I can run my own kernel now with secure boot off.

---

