---
title: "Encrypt /home directory after installation of Ubuntu 18.04"
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by gobsjungalist on 2019-01-23
I recently reinstalled Ubuntu 18.04 with a new laptop which has a 1 TB HDD and 256 SSD. I followed [these instructions]("https://askubuntu.com/questions/194457/installing-ubuntu-os-on-ssd-and-install-home-on-other-hdd") more or less for the installation, however I would like to encrypt my home directory as well. Is there an easy (preferably GUI) way of doing that?

---

### Post by TheFu on 2019-01-23
Home directory encryption was removed from Ubuntu 18.04+ due to a number of reasons. Performance, maintennce and security failures.  This link explains a little more:
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840) is a bug about this feature missing.

You can encrypt subdirectories, but I'd be careful which I did. I would avoid encrypting ~/.config/, for example.

[https://help.ubuntu.com/lts/serverguide/ecryptfs.html.en](https://help.ubuntu.com/lts/serverguide/ecryptfs.html.en) might be helpful. It is for 18.04 server, so not a GUI for encrypting.

I don't know 18.04, but in 16.04 using the Mate file manager, caja, some encrypted storage is recognized and GUI prompts come up to provide decryption when accessed. I had an external dm-crypt USB drive and Caja prompted. I've not used any GUI to encrypt stuff, sorry.

---

### Post by Dennis N on 2019-01-23
You can encrypt a file or directory from the file manager using gnupg by right click on the file/folder and select 'encrypt' when you have **seahorse** and the **seahorse-nautilus** plugin installed. 

There are then two sets of options presented: 
Type of encryption: 
1) passphrase (symmetric) or 2) public-key (asymmetric) encryption
and
How it's done:
1) encrypt the files separately or 2) make an single archive of all files and then encrypt the archive.

---

### Post by gobsjungalist on 2019-01-24
Thank you for the replies, the seahorse plugin looks useful. However, I managed to find what I was looking for eventually:
[https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html](https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html)

---

### Post by TheFu on 2019-01-24
> **gobsjungalist said:**
> Thank you for the replies, the seahorse plugin looks useful. However, I managed to find what I was looking for eventually:
[https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html](https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html)

Please keep excellent backups. There will be a large risk at every OS migration for something bad to happen. Even weekly patching may cause issues with encrypted HOME access, so create a non-encrypted userid to be used as a backup way into the machine.

If you consider this thread solved, please use the "thread tools" button near the top to mark it that way. Doing so helps the wider community and is a huge time-saver for volunteers AND people seeking solutions.

---

