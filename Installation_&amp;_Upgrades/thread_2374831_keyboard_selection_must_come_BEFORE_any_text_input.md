---
title: "keyboard selection must come BEFORE any text input in the installer"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by jaarvidsen on 2017-10-19
ive just installed kubuntu 17.10 on my laptop and chose to encrypt the hdd. bad mistake as my keyboard is norwegian but the system assumes english. so basically im locked out. (i prefer to use english language for various reasons but my keyboard is norwegian)

in the installer, why isnt the keyboard selection before everything else? as it is now its after where you enter your password and encryption password and unless you accidently chose a password that is the same regardless of keyboard layout you end up with quite a puzzle figuring out how to decrypt the hdd. 

i even chose 'try kubuntu' first and made sure to change the keyboard layout in the live environment but to no avail

---

### Post by grahammechanical on 2017-10-19
Perhaps it is best in your case to install Ubuntu as Norwegian and then after installation install the English language keyboard and other parts of the English language pack. Then at the login screen change the keyboard layout to Norwegian.

Regards

---

### Post by jaarvidsen on 2017-10-19
what if i dont know what things are called in norwegian?

---

### Post by jaarvidsen on 2017-10-20
i tried your suggestion and isntalled in norwegian and changed language after login - not very satisfactory, things like the pictures, videos documents folders etc were all in norwegian. so i installed again in english and made sure to choose a password that would involve hitting the same keys in both .no and .en (which limited the number of available characters significantly) and that worked well. but surely a better solution would be to choose the keyboard layout earlier in the installation process?

---

### Post by Impavidus on 2017-10-21
That would be better indeed. It's not listed in the [Ubuntu 17.10 release notes]("https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes"), but the issue is mentioned in the [Xubuntu 17.10 release notes]("https://wiki.xubuntu.org/releases/17.10/release-notes"), which link to a [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047384") that has been around for quite a while.

---

### Post by jaarvidsen on 2017-10-21
thanks for that
so its only been around since 2012... that fills me with confidence it will be fixed asap

---

