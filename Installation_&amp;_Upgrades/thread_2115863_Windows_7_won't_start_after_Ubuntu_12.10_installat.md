---
title: "Windows 7 won't start after Ubuntu 12.10 installation"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by VivaLaEvolucion on 2013-02-14
Hello,

as written in the title my Windows 7 installation won't boot. I had two partitions, one for the Windows 7 professional x64 system, allocation size about 50 GiB (drive C) , and one for the data, allocation size about 250 GiB (drive D).

To install Ubuntu 12.10 I reduced the data allocation partition to ~200GiB, and made one ~4GiB swap partition and one ~46GiB partition for Ubuntu.

When booting I arrive at the Grub boot manager and can boot Ubuntu. When I select the Windows installation, however, the screen turns black for a second and returns me to the boot manager.

I seem to have exactly the same symptoms as this guy:
[http://ubuntuforums.org/showthread.php?t=2113396](http://ubuntuforums.org/showthread.php?t=2113396)

I tried to fix the issue with a Win7 DVD, selecting auto-repair, but the program found no issues. I also reverted the installation to an older version, similarly with no effect.

I then made a Ubuntu boot repair disc, and ran boot repair. While this also didn't solve the issue it gave me this pastebin link:
[http://paste.ubuntu.com/1649291](http://paste.ubuntu.com/1649291)

Does this tell you anything about my problem and what I could do to fix it?

Thanks a lot.

---

### Post by kc1di on 2013-02-14
Hello VivaLaEvolucion and welcome to Ubuntu,

This is what I would try.

first repair the windows MBR see instructions on this [page]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

then reboot make sure windows will boot properly.
if it does the run boot-repair again and reinstall grub2 to the MBR

Now see if you can boot both windows and linux.
good luck

---

### Post by VivaLaEvolucion on 2013-02-14
Hi kc1di,

thanks for your friendly welcome and the suggestion. I followed the instructions you linked and received a prompt confirmation that it worked. I then rebooted, as expected Grub didn't start up. Instead I had a black screen with a flashing cursor in the top left. The system was non-responsive and after several keystrokes a speaker noise indicated the buffer was full.

After getting the same result upon a reboot I used the Ubuntu boot repair to restore Grub and again got the following pastebin link:
[http://paste.ubuntu.com/1650339](http://paste.ubuntu.com/1650339)

My situation is now almost the same as before. Only when I select Windows I get that black, unresponsive screen detailed above.

Any other ideas?

Thx in advance VLE

---

### Post by omid2s on 2013-02-14
Hello dear VivaLaEvolucion and welcome to [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")
 
maybe your media is bad
or your MD5 is bad
chek it on the ubuntu site
I hope solve it:lolflag:

---

### Post by oldfred on 2013-02-14
Your first pastebin showed grub installed to the Windows partition. You never install grub2's boot loader to the PBR of a NTFS partition. 
It looks like some of the repairs you ran did fix that. Testdisk will restore the backup and Windows fixBoot may also fix it.

I would try the full set of Windows repairs again including chkdsk until chkdsk shows no errors. Windows does not fix all errors on one pass.

Last pastebin makes Windows look normal, but it still can have internal errors. Grub2's os-prober finds the Windows entry so that says from Linux it can mount partition and see the boot files.

---

### Post by VivaLaEvolucion on 2013-02-14
Thank you oldfred,  that resolved the issue!

Firstly I installed and ran TestDisk as described on:
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

Then I booted with a Windows7 CD, opted to repair, *deselected* the identified Windows7 installation and ran the command prompt with:
bootrec.exe /fixboot
bootrec.exe /fixmbr

Here's the link to the description I used:
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

After restarting the computer, Windows 7 booted and ran chkdsk. I am writing this out of my Windows 7 environment.  Again, thanks a lot oldfred!

Edit: I had to run boot repair in order to restore the Grub boot manager.

---

