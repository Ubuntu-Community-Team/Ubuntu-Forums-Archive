---
title: "Upgrade 12.04 - weirdest situation"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by nimdil on 2012-05-06
Hello!

The situation is as follows. My fiance owns a HP laptop - around 4 years old. Recently she decided to click yes when it asked her to upgrade to version 12.04.
And she is currently 300+kms away.
The previous version was - I believe - 11.10.

So after the installation the laptop rebooted and nothing happened. Black screen etc.
She mentioned that in recovery mode the effect was pretty much the same, though this time there was some output before the black screen with nothing. The last information she spotted was apparently "failed to create pty" which is rather weird.

I called her, we navigated through GRUB and here is what I was able to remotely determine:

The
"initrd /boot/initrd.img-...-generic" line disappeared.

The 
"linux /boot/vmlinuz-..." line referred to a vmlinuz version without corresponding "initrd.img-..." file in the /boot folder. We tried following combinations:

linux /boot/vmlinuz-3.2.?-?-generic ... (I don't recall the specific version atm)
initrd /boot/initrd.img-3.0.0-17-generic (latest found in /boot folder)

linux /boot/vmlinuz-3.0.0-17-generic ...
initrd /boot/initrd.img-3.0.0-17-generic 

linux /boot/vmlinuz-2.6.38-11-generic ...
initrd /boot/initrd.img-2.6.38-11-generic 

in the place of ... there are all original parameters passed to a kernel.

No effect for each.

Any suggestions? Or should she just download the latest Ubuntu 12.04 ISO and reinstall (in theory the simplest/fastest combination as she also has a desktop for her disposal)?

Also - what possibly could be a reason for disappearance of "initrd ..." line? This is confirmed issue as she sent ma photo of a screen :) The line disappeared also from previous ubuntu versions option in GRUB.

The hardware should be able to handle Ubuntu 12.04 - it is Intel Core 2 Duo 2.0 GhZ, 3 GB memory. If for some reason GPU is relevant it is X3100 integrated.

---

### Post by darkod on 2012-05-06
Forget about the line missing right now, is the file in the /boot folder? Can she check?

What is the latest (with a highest number) combination of both vmlinuz and initrd.img present in /boot?

Sounds like something went wrong with the upgrade. It's only up to you if you think clean reinstall is best. Lets see few things, and if it doesn't work, she can reinstall without wasting too much time troubleshooting.

---

### Post by drs305 on 2012-05-06
Broken upgrades are often difficult to diagnose and it's usually faster to just reinstall. Of course it depends on the specific situation.

If it's just the kernel installation that went bad, one way to get it installed without going through an entire reinstallation would be to boot a LiveCD (of the new version), chroot into the new installation, and install/reinstall "linux-image". It should put the linux kernel in the correct place and regenerate an initrd image.

Chrooting isn't everyone's cup of tea, and it sometimes seems a bit overwhelming. But if it's something you want to try, the way to get into the chroot is detailed in the "Chroot" link in my signature line. You most likely wouldn't need to reinstall grub (the purpose of the guide) - just the kernel.

Again, we really don't know specifically what happened, and I reemphasize that this procedure is a probably a long shot.

---

### Post by nimdil on 2012-05-06
The files are there - we've taken the filenames by switching to GRUB shell mode (or however it is properly code) and listing folder content, than writing the exact same paths/filenames to the GRUB and firing the boot with f10. Also the system has tons of other versions. 

CHROOT is probably out of question atm as I won't have contact with laptop for at least two weeks and it is a bit too much to give instructions for such an operation via phone. If reinstalling from LiveCD will work that's OK by us. No data loss, easy to perform.

I just can't understand how she ended up with vmlinuz without corresponding initrd.img file. Anyway the latest are:

initrd.img-3.0.0-17-generic
vmlinuz-3.2.0-24-generic
though the vmlinuz-3.0.0-17-generic is present as well.

@drs305
are you suggesting that there is s.t. wrong with GRUB?

---

### Post by darkod on 2012-05-06
Well, what I meant was the latest version that has both files present. Obviously the initrd.img-3.2.0 is missing. So, the latest version with both vmlinuz and initrd.img present is 3.0.0 which is 11.10. Something went wrong during the upgrade.

Right now, and her being 300kms away, reinstall sounds best I would say.

drs is right, there is a possibility it's not only the initrd.img that is missing. You can't know at this moment if something else went wrong. By the time you catch every error, you already have a clean 12.04 LTS installed.

---

### Post by drs305 on 2012-05-06
> **nimdil said:**
> 
@drs305
are you suggesting that there is s.t. wrong with GRUB?

No. It appears you have verified that the 3.2... initrd file is truly missing and that it isn't just missing from the Grub menu.

I only mentioned reisntalling Grub since that is what the chroot instructions in the link were provided for. I wanted to stress the link told you how to chroot but that once 'chrooted' the rest of the instructions wouldn't be needed.

Since the kernel was installed for 12.04 I don't think you are going to have any success trying to get back into an earlier release.

---

### Post by nimdil on 2012-05-06
OK, Thanks for answers!

---

