---
title: "[Solved] something changed with initramfs and cryptsetup?"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by piotr5 on 2015-03-31
after the upgrade to 14.4 I'm unable to create a working initramfs.
before I had a hook in /etc/initramfs-tools/hooks to copy a script for outputting the key to cryptsetup. now this script isn't getting executed.
I copied that script to /usr/share/initramfs-tools/hooks and there it works. however, I still cannot boot!
ubuntu didn't detect that rootfs is encrypted and just plainly refused to add cryptsetup to initramfs.
well, I added the actual executable "cryptsetup" from within my hook, but it still doesn't work.
when booting I get to the prompt and there manually starting cryptsetup results in errormessages.
seems I need initramfs-tools to become aware I have a crypt-root. how do I do that?
never had that problem before...

Edit: added the module-stuff from cryptroot hook to my hook, and it works now. in doing this I discovered, my hook in /etc is getting executed -- I forgot to copy it over to /usr/share. also it seems there are several bugs reported about initramfs-tools strangly having diverged from a general purpose mkinitramfs towards one where users are supposed to opt in and opt out of various building blocks. either this will be reverted, or some docs/gui will pop up advising how to configure that stuff. either way, I will have to make my hook more self-contained to cope with compatibility-breakage...

---

