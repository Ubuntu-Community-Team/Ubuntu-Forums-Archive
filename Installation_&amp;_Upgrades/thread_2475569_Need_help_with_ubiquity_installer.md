---
title: "Need help with ubiquity installer"
date: 2022-06-01
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2022-06-01
Hi

I can install Ubuntu 20.04.4 by preseed OEM installations, but every time the installations becomes OEM where the user needs to input their name, username, password and hostname. Isn't there a way to skip that part so all is entered in the preseed-file so computer is login-ready when installation is done?

Anyone know this way of installing?

---

### Post by TheFu on 2022-06-01
Canonical reworked their installers and removed the ways we accomplished that previously.  

Looked at their new solution, but since we aren't shipping HW to consumers, decided it was just easier to ship a normal setup with a phone number to be called by the person who received it. They'd have to connect it to our network, an admin would ssh into the system and change the default username to the user's official company username (we have standards for that), then we'd set a password that had to be changed immediately and they'd be on their own.  I did play with the autoinstaller a few years ago, but only in a virtual machine.  Decided is wasn't worth the effort for our needs. We don't deploy 10 identical systems here. Each is a bit of a snowflake, so even the storage layouts are different.

The other option was to use something like Cobbler to push the minimal install using a PXE boot, then setup the needed stuff using Ansible. Again, these are all network methods.

I think Canonical has a guide for 20.04 and later desktop auto-installs somewhere. Google found it easily when I looked a few years ago.  [https://ubuntu.com/server/docs/install/autoinstall-quickstart](https://ubuntu.com/server/docs/install/autoinstall-quickstart)  Lots of results for the search.  All seemed to be for Servers, not desktops.  Found a script to create a simple autoinstall ISO [https://github.com/covertsh/ubuntu-autoinstall-generator](https://github.com/covertsh/ubuntu-autoinstall-generator)

---

### Post by Jaxilian on 2022-06-03
found it:

changed to false on row where it says "d-i oem-config/enable boolean true"

Had to go back to 20.04 since ubiquity is still in 22.04 and it is broken.

---

