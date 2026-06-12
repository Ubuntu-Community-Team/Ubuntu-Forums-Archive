---
title: "Ubuntu-WUBI installation Problem"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Excellis on 2013-04-04
Hello all, 

This is my first thread on the forums and it's regarding my installation of Ubuntu through WUBI.

I recently installed Ubuntu 12.10 on my 64-bit Windows 7 Ultimate PC, using the Windows installer available on the Ubuntu website. I saved Ubuntu in my C drive and was told to select Ubuntu in the "black screen" boot up list, where I should now be able to choose between Windows 7 and Ubuntu.
I restarted my computer and selected 'Ubuntu' in the list, instead of opening, it directs me to a error screen, which reads:

(Start)                                                                 
                                                                Windows Boot Manager

Windows Failed to start.  A recent Hardware or Software change might be the cause.  To fix the problem:

1. Insert your windows installation disk and restart your computer.

2. Choose your language settings and then click next.

3. Click "Repair your computer".

If you do not have the disk, contact your system administrator or computer manufacturer for assistance.

File: \Ubuntu\winboot\wubildr.mbr 

Status: 0xc000000f :confused:

information: The selected entry could not be loaded because the application is missing or corrupt.

Enter= Continue

(Finish)

I am not sure if I installed the correct version (32-bit or 64-bit) but I don't believe it matters if you install a 32-bit on a 64-bit (open to correction, of course).

Thank you in advance for any future assistance in solving the problem.

Excellis.

---

### Post by bcbc on 2013-04-05
It sounds like you have a GPT disk (your computer boots with UEFI). Wubi won't work in this case.

---

