---
title: "GRUB issues in dual boot LUKS Encrypted Ubuntu + VeraCrypt Encrypted Windows 10"
date: 2018-08-22
forum: Installation &amp; Upgrades
---

### Post by computerplumber on 2018-08-22
I just tried out the newly posted manual full disk encryption instructions [here]("https://help.ubuntu.com/community/ManualFullSystemEncryption/") today and I have to say they work very well .  The only difference in my case was that I had to leave the installer "hanging" (running) after the second post-install error message: [IMG]https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu?action=AttachFile&do=get&target=installer-crashed.png[/IMG] 
popped up because the "close" button wouldn't actually close the message and the installer.  I just told the script to conitnue running, which it successfully did and completed.  In my case in particular I had some problems with Qt5 packages after installation in programs like keepassx (which I resolved by reinstalling all the relevant packages using synaptic).  

Both ubuntu and windows systems work.  I can get to the drive decryption password  screen for ubuntu through GRUB but now the GRUB entry for Windows 10  does not work anymore.  I have edited the grub.cfg entry for the Windows  entry through the grub-customizer tool (in ubuntu if it isn't already obvious)  to point at the EFI file for the veracrypt bootloader.  I confirmed  that the veracrypt EFI file exists.

[IMG]https://i.imgur.com/qG4okdv.png[/IMG]

However when I select the windows entry in grub I get to a blue Windows  "Recovery" screen. 

[IMG]https://i.imgur.com/gYMMMgQ.jpg[/IMG]

I can still boot into veracrypt through selecting the  vera crypt entry in the BIOS menu so I'm pretty sure this is a GRUB  problem.  

  How should I fix this?

---

### Post by oldfred on 2018-08-22
Grub only boots working Windows. 
Generally Windows cannot be hibernated, nor need chkdsk. Not sure then if Windows also is encrypted if you can boot it from grub.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by computerplumber on 2018-08-23
> **oldfred said:**
> Grub only boots working Windows. 
Generally Windows cannot be hibernated, nor need chkdsk. Not sure then if Windows also is encrypted if you can boot it from grub.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Interesting that you say this. I actually got the directions here to work on unencrypted ubuntu 18.04 + veracrypt windows 10 before I manually encrypted ubuntu.

[https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b](https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b)

---

### Post by oldfred on 2018-08-23
This is what I know as he confirms grub will not boot Windows that is encrypted, but he seems to have a work around.
Grub cannot see the encrypted loader.

> Once you have the menu, you will most likely be disappointed to find out  that the &#8220;Windows&#8221; entry tries to load Windows directly off the  encrypted partition, fails miserably, tries to repair it, and fails  miserably again.
This happens because the entry is pointing to the old Windows loader, bypassing the VeraCrypt loader completely.

---

