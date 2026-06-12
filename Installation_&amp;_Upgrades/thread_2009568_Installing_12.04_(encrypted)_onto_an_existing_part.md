---
title: "Installing 12.04 (encrypted) onto an existing partition"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by MagicalDean on 2012-06-24
I'm trying to dual boot Windows 7 and Ubuntu 12.04, both from separate HDs. However, the drive I want to use for Ubuntu is already partly used for backups. I therefore have two separate partitions, one of which I want to install Ubuntu onto. I'm trying to find a guide to do this while also encrypting Ubuntu, but I've completely failed so far. Are there actually any available?

---

### Post by cyrus_the_virus on 2012-06-24
Hi,

Assuming that you only want to encrypt your home directory and swap partition, this should be pretty straight forward.

[LIST=1]
[*] Boot into the ubuntu livecd 
[*] Select install
[*] When the installer asks where to install Ubuntu, you should select the "Advanced"  or "choose yourself" option (not sure how it is called)
[*] Selector create the partition where you want to install it.
More specifically, make sure you have two partitions:
- One "Swap" partition. It is recommended that this partition is about the size of your systems amount of RAM. This is used as an extension of your systems RAM.
- One EXT4 partition with mount point '/' (no quotes). This is the main parition for Ubuntu.

[*] When the installer asks about your user name, you can select "Encrypt my home folder"

[/LIST]

Hope that helps

---

### Post by MagicalDean on 2012-06-25
I remember doing it ages ago, and I think there was a partition for /home instead of the "Encrypt my home folder" option. Is the end result the same?

---

### Post by cyrus_the_virus on 2012-06-25
> **MagicalDean said:**
> I remember doing it ages ago, and I think there was a partition for /home instead of the "Encrypt my home folder" option. Is the end result the same?

I do remember that option, but as far as I recall that had nothing to do with encryption.
The 'Encrypt my home folder' option will not create a separate partition; your files are stored on the main partition instead (/).

---

