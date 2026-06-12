---
title: "unetbootin broken?  or five cd's just for os's???"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by adduds on 2011-03-29
I'm trying out some other distros i have fedora, openSUSE, natty (wanna check out gnome3), and debian

i tried to create a pen drive for all separate ones of the using unetbootin' and none worked except natty

i installed image writer which doesn't recognize any of my iso's when i browse my filesystem the folder they're in is just empty

i've tried the multicd.sh script to create a multiboot dvd so i don't have to create 5 different cds but when i execute it it just lists memtest where its supposed to list all the .iso's in the folder (yes i renamed them all simple as per instructions...

and then the multibootusb which only recognized openSUSE and when it was done i couldn't boot off it

my pendrive only works at booting for ubuntu?

do i have to write 5 cd's just to experiment

i also tried

dd if=suse.iso of=/dev/scd1 bs=4m

---

### Post by mikewhatever on 2011-03-29
While I think Unetbooting should work, you can also write the both Fedora and Suse isos out with dd.
```
sudo dd if=Fedora...iso of=/dev/sdX bs=4096
```

...doesn't work for Ubuntu.

---

### Post by idoitprone on 2011-03-29
[http://multicd.tuxfamily.org/#SupportedDistros](http://multicd.tuxfamily.org/#SupportedDistros)

---

### Post by adduds on 2011-03-29
> **idoitprone said:**
> [http://multicd.tuxfamily.org/#SupportedDistros](http://multicd.tuxfamily.org/#SupportedDistros)

yes all the distros i have are listed there :) thanks

also is there a way to burn multiple cd os images onto one dvd?

---

