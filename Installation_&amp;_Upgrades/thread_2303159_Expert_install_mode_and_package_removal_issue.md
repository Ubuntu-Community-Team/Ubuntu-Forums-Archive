---
title: "Expert install mode and package removal issue"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by VariantX on 2015-11-16
I am dual booting with windows 10. I am using secure boot and prefer to use Ubuntu mate. I am running into issues when trying to remove packages that I do not use. I notice for example certain packages I remove will instruct me that "ubuntu-base" or the likes need to be removed. I am an advanced linux user. I chose Ubuntu because of secureboot at the moment. I would like to know how to launch the "Expert Mode" install using the Ubuntu Mate cd. I tried adding priority=low before the "---" and after. I then tried the "debconf/low" option as well without results. It seems like the bootloader is not taking any custom options I add. F6 does nothing and I only have the option to "Try Ubuntu", "Install", and "Memtest". I have read about the mini ISO but from what I understand the mini iso does not work with secureboot "out of the box".  

To sum it up:
How do I boot into expert install mode using Ubuntu Mate?
Is it safe to remove packages such as CUPS, Bind, Openssh, and Avahi without causing problems with Ubuntu. I do not use a virtual environment and this setup will be used for development and testing. I would like to customize the distro to the best of my ability per security and performance reasons. I do intend to do a custom kernel compile. (I have done this many times in debian without issue).

Thanks for the help. :)

---

### Post by grahammechanical on 2015-11-16
I have installed all the official members of the Ubuntu family of Linux distributions including Ubuntu Mate and they all use the same installer (Ubiquity).

Edubuntu will let us choose between installing all the default educational software or selecting groups of applications based on 3 or 4 age ranges. Ubuntu Studio will also give us the option of installing all the default applications or only those applications belonging to our area of interest, Audio, Video, Photography. That sort of thing.

I have been browsing the Ubuntu Mate web site and I can see nothing to indicate that we get options to select different application packs or which individual applications out of all the default offering.

What you are thinking of would go against the Ubuntu philosophy of not forcing the user to make difficult choices during the installation process. There used to be an alternate ISO image for machines with a very, very limited amount of RAM that needed a text based installer instead of a Graphical User Interface installer. But as far as I know Lubuntu is the only family member has now has an alternate ISO image. And I do not think that the Lubuntu alternate installer offers application selection either. And it might not work with secure boot because the machines it is meant to be used with pre-date secure boot.

Regards.

EDIT: I have never done it myself, but have you tried the OEM install? It might get you what you want.

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

