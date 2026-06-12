---
title: "Upgrading laptops - take along my current install ?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by jdavidw13 on 2009-12-04
I'm upgrading my laptop and I was wondering if there's a recommended way I can move my current setup to the new machine?  I'm hoping to easily transfer everything in my /home folder, installed software, software settings, desktop and system settings.  Also I have apache and mysql installed to run a personal mediawiki.

Please tell me there's an easy way to move this stuff over without needing to painstakingly reinstall and reconfigure everything on the new laptop.

---

### Post by phillw on 2009-12-04
> **jdavidw13 said:**
> I'm upgrading my laptop and I was wondering if there's a recommended way I can move my current setup to the new machine?  I'm hoping to easily transfer everything in my /home folder, installed software, software settings, desktop and system settings.  Also I have apache and mysql installed to run a personal mediawiki.

Please tell me there's an easy way to move this stuff over without needing to painstakingly reinstall and reconfigure everything on the new laptop.

Yep you can ... may take a couple of tweeks to settle down Grub2, but you can either use something like clonzilla etc. or a shell script to backup your current installation and pop it over a clean install on the new machine.
Personally, I'd dump the MqSQL dbases to /home and just take /home over, but you can certainly 'photo-copy' your installation and move it, lock, stock & smoking barrell accross to the new machine. But, for you, with your other settings - I guess a full system backup and restore is going to be best for you.

Phill.

---

