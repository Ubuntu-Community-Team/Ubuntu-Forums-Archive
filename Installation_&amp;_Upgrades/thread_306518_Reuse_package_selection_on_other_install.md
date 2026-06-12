---
title: "Reuse package selection on other install?"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by lithium on 2006-11-25
Hi, I got a new hard drive and need to reinstall edgy on it. I have a nice installation on the old drive and I would like to install the exactly same packages on the new hdd.

Is there a way to do this?

There's some save packages list option in synaptic but that doesn't seem to work. It would be cool to just make a standart install using the cd installer, boot into the new system and give it a list of packages that I want, so it can install the ones needed (from the net) and remove the ones I don't need.

Is there a way to do this?

Thx!

---

### Post by Spano on 2006-11-25
dpkg --get-selections > some_file

in your new installation:

dpkg --set-selections < some_file
apt-get dselect-upgrade

this won't preserve settings though as those are scattered around /etc and /var/lib

and some discussion:
[http://www.ubuntuforums.org/showthread.php?t=184392&highlight=dpkg+-set-selections+%26lt%3B+some_file](http://www.ubuntuforums.org/showthread.php?t=184392&highlight=dpkg+-set-selections+%26lt%3B+some_file)
Works great.

---

### Post by dcstar on 2006-11-25
> **lithium said:**
> Hi, I got a new hard drive and need to reinstall edgy on it. I have a nice installation on the old drive and I would like to install the exactly same packages on the new hdd.

Is there a way to do this?

There's some save packages list option in synaptic but that doesn't seem to work. It would be cool to just make a standart install using the cd installer, boot into the new system and give it a list of packages that I want, so it can install the ones needed (from the net) and remove the ones I don't need.

Is there a way to do this?

Thx!

If you want to basically transfer the existing installation from one drive to the other, do a search on using **partimage**.

---

