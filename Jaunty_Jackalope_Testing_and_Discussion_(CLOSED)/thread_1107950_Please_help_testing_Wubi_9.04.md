---
title: "Please help testing Wubi 9.04"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ago on 2009-03-27
Wubi 9.04 ([http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)) is a complete rewrite (in python) from previous code base, so heavy hammering would be very much appreciated. You can either run Wubi 9.04 from the latest beta/daily ISO or grab the latest standalone build here: 

[http://people.ubuntu.com/~evand/wubi/jaunty/](http://people.ubuntu.com/~evand/wubi/jaunty/)

Please report any (unknown) problem here: 

[http://bugs.launchpad.net/wubi](http://bugs.launchpad.net/wubi)

If you do not have a launchpad account you can also append your comments to this thread. 


NOTES:

In either case, please mention what version/release you are using. 

If you have troubles on the windows side, note that there is a log stored in your windows user temp directory (type %temp% in explorer), it generally helps if you attach that too.

If you have troubles at boot, try to press ESC after selecting "Ubuntu" and select one of the other boot options.

The standalone version comes with a built-in download manager (bt + http) that will grab an ISO for you if a CD or a valid local ISO is not found, so running that will activate a slightly different code path as opposed to running Wubi from CD.

[s]There are known issues with the uninstaller at the moment ([https://bugs.launchpad.net/wubi/+bug/341605](https://bugs.launchpad.net/wubi/+bug/341605)), as a workaround, copy c:\ubuntu\uninstall-wubi.exe to a different directory and run it from there.[/s]


Many thanks in advance,


Ago

---

### Post by tjeremiah on 2009-03-27
I have a question. I used Wubi to install 8.10. Can I also use this version to upgrade to wubi 9.04 while maintaining my files? But I already updated to 9.04 beta, would it make a difference?

---

### Post by ago on 2009-03-27
Once Ubuntu is installed with Wubi you can dist-upgrade it as usual from within Ubuntu. But if you run the wubi installer again from within windows you will have to remove the previous installation before proceeding with the newer one. It is very straightforward to do a back-up in windows: just do a copy of c:\ubuntu.

---

### Post by tjeremiah on 2009-03-27
Thanks!

---

### Post by jac1d on 2009-04-07
I appear to be in Wubi hell.

I tried to install 9.04 and the installer failued on an acer laptop.

I then uninstalled from the program manager but that failed with the bcdelete fail saying the boot loader entry wasn't there (which it was not).

Ever since I've been in a loop of I can't complete the wubi install (so I can go back to 8.10) because here is no bootloader entry to delete and it bombs out.  I've tried downloading different versions from the website above but it always seems to call the CD versions regardless of what I execute.  If I try removing the CD it fails completely to execute.

I tried moving the copy from the D:\unbuntu directory (the uninstaller as noted in one of the bug reports) but that failed as well.  I do have two partitions (C and D) on the laptop and was trying to install to D, which may not be supported?

Any assistance in completing the removal would be appreciated.  

-Jeff

---

### Post by ronacc on 2009-04-07
one problem with testing WUBI . It requires you to install windows first:(

---

### Post by ago on 2009-04-08
You should be able to delete c:\ubuntu and repeat.

There were issues with the uninstaller but should have been fixed now, please always try the latest version (r118 ) and remember to post the version you are playing and possibly attach the log.

---

### Post by mxboy15u on 2009-04-08
I had to delete Ubuntu off of my computer because of a bad Kernel, I will be re-installing with wubi118 and will report any problems.

---

### Post by nbnds on 2009-04-09
After download and reboot it failed to create Swap File. Aborting, brought me into the live mode. Vista 32, assigned 15GB to ubuntu of 17 available. the same problem was in r117

---

### Post by ago on 2009-04-09
For swap issues, see [https://answers.edge.launchpad.net/wubi/+question/65689](https://answers.edge.launchpad.net/wubi/+question/65689)

---

### Post by Stalker72 on 2009-04-14
When I try to uninstall Ubuntu (installed using Wubi), I get an error (see attached image).

Cheers,

Stalker72

---

### Post by PGHammer on 2009-04-14
I ran Wubi 9.04 from the latest ISO (Kubuntu 9.04 beta 64-bit downloaded earlier today) mounted via VirtualCloneDrive in Vista Ultimate 64-bit.  I'm typing from it now, and I'm getting ready to activate the FGLRX drivers (I have an HD3450 in PCIe; the combo of this card and my older 19" non-PnP CRT will only run at the preferred resolution using the FGLRX driver).

---

### Post by shuttleworthwannabe on 2009-04-15
> **ago said:**
> Wubi 9.04 ([http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)) is a complete rewrite (in python) from previous code base, so heavy hammering would be very much appreciated. You can either run Wubi 9.04 from the latest beta/daily ISO or grab the latest standalone build here: 

[http://people.ubuntu.com/~evand/wubi/jaunty/](http://people.ubuntu.com/~evand/wubi/jaunty/)

Please report any (unknown) problem here: 

[http://bugs.launchpad.net/wubi](http://bugs.launchpad.net/wubi)

If you do not have a launchpad account you can also append your comments to this thread. 


NOTES:

In either case, please mention what version/release you are using. 

If you have troubles on the windows side, note that there is a log stored in your windows user temp directory (type %temp% in explorer), it generally helps if you attach that too.

If you have troubles at boot, try to press ESC after selecting "Ubuntu" and select one of the other boot options.

The standalone version comes with a built-in download manager (bt + http) that will grab an ISO for you if a CD or a valid local ISO is not found, so running that will activate a slightly different code path as opposed to running Wubi from CD.

[s]There are known issues with the uninstaller at the moment ([https://bugs.launchpad.net/wubi/+bug/341605](https://bugs.launchpad.net/wubi/+bug/341605)), as a workaround, copy c:\ubuntu\uninstall-wubi.exe to a different directory and run it from there.[/s]


Many thanks in advance,


Ago

Thanks Ago for the development of the new Wubi. Some feedback:

I used the 9.04 desktop Live CD beta version to install Ubuntu using Wubi that  was on the disc. but kept getting error messages. I can now confirm that wubi_r122 (standalone version) works perfectly fine.

many thanks

---

### Post by bennachie on 2009-04-15
I had no problem using Wubi on the Live CD of Jaunty Beta to install the system on my laptop. When I tried to use r120 of the standalone version of Wubi to install Jaunty on a spare desktop, I found that Wubi ignored the ISO of the same Live CD, and insisted on downloading a fresh version.

This was probably no bad thing, and the resulting installation went very smoothly. However, it doesn't quite seem to line up with the statement by the original poster that:

*The standalone version comes with a built-in download manager that will grab an ISO for you if a CD or a valid local ISO is not found, so running that will activate a slightly different code path as opposed to running Wubi from CD.*

Does validity, in that context, require more of the ISO than that it would generate a Live CD that could have been used to install Ubuntu in the normal manner on the same machine? I initially wondered whether the issue might have related to a mismatch between 32-bit and 64-bit versions of Ubuntu and Windows, but the same behaviour occurred with either version of the ISO.

---

### Post by lisati on 2009-04-17
I tried Wubi via a Jaunty Release Candidate disk and XP provided an error message, with the window (small w) title saying something about "No disk",  (sorry, no screen shot......, please stand by while I try to reproduce it and get more details of the error message. XP is doing it's CHKDSK stuff)

EDIT: Error message (copied manually from screen) is 
> Exception: Processing Message c0000013 Paramaters 75b6bf7c 4 75b6bf7c 75b6bf7c
Dialog has the options Cancel, Try again, and Continue.

Computer is a Comaq SR1520AN desktop with AMD Sempron 3200+ (AMD64) single-core processor, RAM upgraded to 1Gb, default version of Python installed, all XP updates (including SP3 & the patch from HP to allow SP3 to work on this family of machines). Possibly irrelavent: PCI TV tuner & video capture card installed by myself.

Speculation: Different versions of Python?

EDIT 2: Wubi seems to work fine within the copy of Vista Home Premium on another machine, with the 64-bit version installed in another partition. Will update if there's a problem.

---

### Post by mxboy15u on 2009-04-17
I had the swap issue today as well with the lates wubi release. I have not had the opportunity to test the solution.

---

### Post by PGHammer on 2009-04-18
> **mxboy15u said:**
> I had the swap issue today as well with the lates wubi release. I have not had the opportunity to test the solution.

Blanked the HD and reinstalled first Vista Ultimate 64-bit, then (after installing Vista Catalyst 9.4 and Vista X-Fi drivers), installed VirtualCloneDrive, and mounted the 9.04 RC and ran Wubi from that.  Just as in the last pre-RC beta, it was *flawless*.  I blanked the HD due to boot-menu corruption.  It was a Vista problem; Kubuntu and Wubi worked fine.

I've since installed the pre-release Catalyst 9.4s and open-source X-Fi driver from Creative; they worked flawlessly yet again (except for refresh-rate issues; I still have only 60 Hz NI, not 75 Hz, which is my default in Vista).

---

### Post by ago on 2009-04-18
> **Stalker72 said:**
> When I try to uninstall Ubuntu (installed using Wubi), I get an error (see attached image).

Cheers,

Stalker72

This should work in more recent versions, remove the directory manually and try installing/uninstalling with wubi r122+

---

### Post by Gedemins on 2009-04-19
installed wubi from beta, loaded ubuntu. but instead of loading normally, it loaded live session, with an icon on a desktop for "installing on disk".
i thought i should reinstall and got an error (see pic) so had to delete ubuntu manually.
now i thought with release candidate would be a different story, but after required reboot there was no choice of OS'es in boot menu.

---

### Post by hyperdude111 on 2009-04-19
Il test wubi on win7 seeing as the last version did not work with 7.

---

