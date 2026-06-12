---
title: "My pc won't load even DOS now :("
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2016-04-27
I had just installed Ubuntu Studio (alongside Windows 10). Then after seeing it was booting directly into Windows, I rebooted with a USB key with Boot repair. After choosing the USB key to boot from, it proceeded to attempt that, but it never got passed a black screen. I waited like 10 minutes.
Then I forced it to shutdown, removed the USB key, and turned it on again. But is not doing anything, not even loading DOS. I never had a case this bad :(
What now?
Specs :
Acer Predator G3-710

Thanks in advance guys,

JDL

---

### Post by ubfan1 on 2016-04-27
Try the EFI boot menu, some function key at power-on to allow you to select boot device or OS.  It should have choices for ubuntu or Windows included.  The Windows selection bypasses grub, the ubuntu selection should boot grub, which should have a selection for booting Windows, which might need secure boot to be disabled in order to work.

---

### Post by oldfred on 2016-04-27
Ever Acer we have seen requires a UEFI supervisory password and setting "trust" on the grub/Ubuntu efi boot files. Also some older threads said downgrade UEFI, but newer threads say update to newest works. So check that you have newest UEFI from Acer.

Some have more details or slightly different explanations that may help.
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)

---

### Post by javierdl on 2016-04-27
I hear you both, and thanks a million for replying. But how can I do any of that if the screen is just black. There was no DOS reading/loading the usual stuff, like the drives, the ram, etc

---

### Post by oldfred on 2016-04-27
You need to get into UEFI/BIOS, often f2 as you boot.
And you may need to do a cold boot or total power off. If laptop you also remove battery. And hold power switch for 10 sec or so to remove any left over power.
Then cold boot and press f2 (or whatever key your system uses) to get into UEFI/BIOS.

---

