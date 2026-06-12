---
title: "Black screen while choosing an installation option"
date: 2016-12-18
forum: Installation &amp; Upgrades
---

### Post by poz-saw on 2016-12-18
Hi everybody, first, sorry for my english, I am not from an english speaking country .. :/

Well, I have a problem and I hope, you can help me
I have a new computer without OS and I want to put on it Ubuntu witch I put in a bootable USB 
i chose my computer to boot on the USB
and there I can choose : "try without installing...
                                    install
                                   OEM
                                   and something else"
but, whatever the option i choose, the screen become black and nothing happen. 

sorry for the english

---

### Post by lestatbzh on 2016-12-19
> **poz-saw said:**
> Hi everybody, first, sorry for my english, I am not from an english speaking country .. :/

Well, I have a problem and I hope, you can help me
I have a new computer without OS and I want to put on it Ubuntu witch I put in a bootable USB 
i chose my computer to boot on the USB
and there I can choose : "try without installing...
                                    install
                                   OEM
                                   and something else"
but, whatever the option i choose, the screen become black and nothing happen. 

sorry for the english

Hi there,
I have the exact same issue...
I'm trying to install LUbuntu 16.10 64bit on my ACER AspireOne 725 using a 4Gb USB drive. I prepared it with Universal-Usb-Installer.

I have this same black screen just after selecting "install" or "try without installing".
Thx for the help.




EDIT:
Ok, I found the issue.
I knew I had to disable "secured boot" in BIOS but it wasn't enough.
In the BOOT section, I also changed the boot mode from UEFI to "legacy"

And then, LUbuntu installation correctly started at the next boot :)

---

