---
title: "Ubuntu installation not recognizing Windows 8 previous installation"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by pablobertran on 2014-08-07
Mates.
I recently bought a Gateway NE522 laptop.

It came with Windows 8. I decided to format it, install windows on a small partition and install ubuntu after that.
The thing is that when I run Ubuntu installation, it doesn't recognize my windows 8 installation.

I googled a bit, and found a few possible solutions, like running ubuntu installation with UEFI boot activated. And still the same (And now can't acces the bios config, by the way)
By now I'm formatting all and installing just ubuntu.

What I need to know is...
Either if is there a way to make ubuntu's installation "see" windows 8, or if there's a way to install windows after ubuntu and then configure it's boot from grub.

Hope someone can help me through this.
Thanks in advance!
Pablo

---

### Post by yancek on 2014-08-07
I don't use UEFI so have no specific advice.  There are quite a number of posts here at the forums on this specific issue.  You could try using the search function.  Apparently it is necessary to install both windows and Linux in uefi mode, OR both in mbr mode.  You should disable to FAstBoot function in the BIOS and might be better off disabling Secure boot although I don't believe that is necessary.  Best to give it some time as I'm sure someone more familiar will post.

---

### Post by oldfred on 2014-08-08
While better to have both in UEFI or both in UEFI, you can boot each install differently.
You just will not be able to use grub to choose but have to use one time boot key, or go into UEFI/BIOS and change boot mode.

This user was not able to get UEFI to work with the Gateway and just used BIOS.
[http://ubuntuforums.org/showthread.php?t=2236614&highlight=gateway](http://ubuntuforums.org/showthread.php?t=2236614&highlight=gateway)

---

