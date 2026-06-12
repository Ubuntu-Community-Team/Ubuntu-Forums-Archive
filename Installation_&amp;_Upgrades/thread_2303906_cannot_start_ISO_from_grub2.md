---
title: "cannot start ISO from grub2"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by elibenyaacov on 2015-11-22
hi all,

I'm trying to make an entry in my grub.conf file for installing xubuntu. this is the entry I added to the /etc/grub.d/40_custom file:

```
menuentry "xubuntu 15.10 i386 (ISO)" {
    set isofile=”/iso/xubuntu-15.10-desktop-i386.iso”
    loopback loop (hd0,7)$isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile 
    initrd (loop)/casper/initrd.lz
}
```

the problem is that once choosing this entry the computer hangs for 1 minute and then reboots. no messages are displayed during the time.

the strange thing is that if I enter grub command-line and enter by hand all the above text exactly as it's written, it successfully boot the ISO file and I get the xubuntu live loading.

what is the problem here?

thanks, eli

---

### Post by oldfred on 2015-11-22
Is the " you are using correct?
set isofile=&#8221; &#8221;

It looks like you have different quote symbols in label and on set isofile, or are you changing font somehow?

---

### Post by egeezer on 2015-11-22
Did you leave the exec tail -n +3 $0 line in place?

---

### Post by elibenyaacov on 2015-11-22
> **oldfred said:**
> Is the " you are using correct?
set isofile=” ”

It looks like you have different quote symbols in label and on set isofile, or are you changing font somehow?

:grin: wow man, you have good eyes. it was exactly that. thanks.

---

### Post by oldfred on 2015-11-22
Definitely not good eyes here, but learned hard way to to check even punctuation.
Back when 9 pin dot matrix printers & green & black monitors, I could not tell a , from a . Took me weeks to find error. :)

Glad you resolved it.

---

