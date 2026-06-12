---
title: "Acer EUFI laptop win8 to ubuntu to win8 licensing problems"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by bradgillap on 2013-03-09
Hi, I work for a pc repair shop and a few months ago one of my colleagues installed ubuntu 12 for a gentlemen and we were happy to do the service. The other day the gentlemen ran into an issue where he needed windows so he brought it back in to have windows loaded again.

Typically we would install windows and use the key on the laptop. This laptop did not come with a key as the information is stored in the UEFI from what I understand for the licensing. So we installed windows 8 off the network server in the shop but there was no key or activation information entered automatically like we were hoping.

For now I have returned the laptop back to the customer with Ubuntu loaded on it again.  I found out that my colleague had completely obliterated all the original partitions on the laptop on his first go around so built in recovery is not an option.  I know for fact that the shop is going to run into a lot more of this and what I really need to know is WHAT version of windows will this secure boot integrated bios licensing work with and where can I buy a copy for the shop?

We rarely nuke recovery partitions, it was an oversight by my colleagues part. Maybe he hadn't had a coffee yet that day but I promised the customer that I would do some research and after many hours of googling I can't get a handle on what exactly will fix this issue. I know this is a windows licensing issue and not a ubuntu issue but I feel that I'm more likely to find an answer here than all the other microsoft forums Ive been searching due to user experience with newer eufi laptops.

---

### Post by oldfred on 2013-03-09
I do not know if a standard Windows 8 installer will work with secure boot that is currently only required with new computers from a Vendor. But I would think it should.

So not confuse the Windows license key with the secure boot key that is inside the UEFI. Is not Windows license key still on sticker on bottom of computer?

Ubuntu bought the UEFI key and has that with its version of grub2, so it should boot any install with secure boot enabled. But many systems have further modified UEFI to restrict booting to Windows only.

Some new UEFI systems may be bricked if booting Linux in UEFI mode. (further testing shows Windows will also brick those computers).
 Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
New Linux UEFI boot loader
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)
Matthew Garrett
[http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/](http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/)
James Bottomley's random Pages - Linux Foundation Secure Boot System Released
[http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/](http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/)


 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

If it is one of these there is no way to reinstall with secure boot.
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

---

### Post by bradgillap on 2013-03-09
I appreciate your reply but I am well versed on ubuntu UEFI from my research already. This does not answer my question of puting windows 8 onto a slic locked machine that did not come with a windows 8 key sticker on it as the key is built into the bios somehow. 

I need to know which version of windows 8 disc to buy so that this bios based licensing will kick in automatically when windows 8 is installed on the machine. Current a standard over the counter windows 8 disc does not seem to work. We are a shop so purchasing a recovery disc from every manufacturer for every model is not feasible. 

I came here because this started because we did a clean install of ubuntu on the machine wiping out the recovery partitions but I have read that for laptops without a license key sticker there is a version of windows 8 that can be installed that will grab the licensing from the special slic bios this acer has.  Let be clear. I have not received adequate response from Microsoft so I'm hoping someone has had a similar experience here.

---

### Post by oldfred on 2013-03-09
Windows forums may know more as we are Ubuntu and only other systems as dual booting.
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by bradgillap on 2013-03-09
Again Fred, if you would have bothered to read my post you would see that I acknowledge your thoughts on that matter.  Unless you have more constructive input I'm not really interested.

---

### Post by bra|10n on 2013-03-09
Does the following code run in a terminal display the key you claim is written into bios;

```
sudo dmidecode
```

---

### Post by Mark Phelps on 2013-03-10
> **bradgillap said:**
> Again Fred, if you would have bothered to read my post you would see that I acknowledge your thoughts on that matter.  Unless you have more constructive input I'm not really interested.

You need to quit being RUDE and go the the RIGHT forum to get your answers -- the Win8 forum that oldfred already told you about!

---

### Post by presence1960 on 2013-03-10
OEMs are no longer putting stickers with Product Keys  on UEFI Windows 8 machines. The Product Key is embedded in BIOS and when the install is made via UEFI mode it will retrieve the Product Key automatically. See [here]("http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/")

When windows is running best to use Belarc Advisor or similar software to get the product key and write it down just in case.

To use a new Windows 8 with a product key different than the one preinstalled on OEM see [here]("http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c") to avoid contacting OEM to have product key deleted from firmware

---

### Post by presence1960 on 2013-03-10
> **bra|10n said:**
> Does the following code run in a terminal display the key you claim is written into bios;

```
sudo dmidecode
```

The Op's "claim" is correct.

---

