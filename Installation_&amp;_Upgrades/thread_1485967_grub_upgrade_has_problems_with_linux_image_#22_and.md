---
title: "grub upgrade has problems with linux image #22 and unable to boot windows"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by petaloid on 2010-05-17
I recently performed a reinstall of ubuntu after mucking up my partitions, and I am running it dual booted with windows 7.
I recently performed a grub-pc update, but I didn't know what it was asking me to do during the process itself of updating the process.

It asked me at one point where to install grub, and I selected all my partitions because it suggested that if I didn't know. I think that may have damaged my windows section, which was also selection.

I've attached the output for:

```
sudo fdisk -l
sudo apt-get upgrade
and for this: [Boot Info Script]("http://bootinfoscript.sourceforge.net/")
```

Problem symptoms:

1) Weird upgrade error in apt-get
2) Unable to boot windows 7
3) Unable to activate proprietary drivers
4) Perpetually being reminded to restart

I appreciate any help you can provide.

---

### Post by kansasnoob on 2010-05-17
We really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's very likely to be this issue:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But I prefer testing to guessing :)

---

### Post by petaloid on 2010-05-17
> **kansasnoob said:**
> We really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's very likely to be this issue:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But I prefer testing to guessing :)

Posted in the attachment for the thread header

---

### Post by kansasnoob on 2010-05-17
As expected:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  **[COLOR="Red"]Grub 2[/COLOR]**
    Boot sector info:  [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 566915096 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe


Cause and solution here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I have filed a bug report but can't get folks to comment and add that they're effected:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Lack of comments = it'll never get fixed :(

---

### Post by petaloid on 2010-05-17
You were right on the money. I fixed it and I'm back in windows. That's great!

Thanks a lot.

Also, I posted on your launchpad bug to help it up :)

---

### Post by kansasnoob on 2010-05-17
> **petaloid said:**
> You were right on the money. I fixed it and I'm back in windows. That's great!

Thanks a lot.

Also, I posted on your launchpad bug to help it up :)

Many thanks to you :)

---

