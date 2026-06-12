---
title: "Ubuntu 14.04 / Windows 10 / Acer E5-573 UEFI woes"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by jonhd2 on 2015-12-10
A typical recent attempt to use Boot Repair.... [http://paste.ubuntu.com/13913898](http://paste.ubuntu.com/13913898) (ignore the attempt to use 'default grub' - this is about 20th attempt to get it working).

Windows 10 PC. Added dual-boot Ubuntu 14.04. All of this with a UEFI BIOS enabled. Mostly with Secure Boot disabled. Original installation went fine. Loaded-up my data (inc. stuff like Thunderbird & Firefox profiles, from previous laptop). Everything good. Multiple reboots over a couple of days while I set it all up. Then, I needed (sorry!) to fire-up Windows, which I selected from the grub menu. All ok. On restart, no grub menu.
Tried a few things, eventually resorted to using a Boot Repair pendrive. This did the trick. Fine again, for a day, working in Ubuntu.
Next day, had to use Windows again (double sorry!). Same problem - no grub menu. Immediately tried the Boot Repair method, again. And have been doing so, for the past 5 days. Completely unable to get grub to reappear. Have tried stuff like:
- running the 'bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi' command from an admin cmd prompt - apparently does the business, but doesn't fix the problem.
- Messing-around with the boot device order in the BIOS (currently set at USB HDD / CD/DVD / HDD / Windows Boot Loader - have tried a variety of combinations)
- Have disabled anything to do with Hibernate mode, in Windows (Boot Repair reports referred to it as a problem).
- Enable / disable Secure Boot
- Revert to Legacy boot, and back again to UEFI.
Completely stuck, and desperate to get back to my Ubuntu OS!

Any suggestions (other than dispose of Windows)?

BR, Jon

---

### Post by oldfred on 2015-12-11
Do not use CSM/legacy/BIOS.
Windows only boots from gpt partitioned drives with UEFI.
Did you turn off fast start up or always on hibernation?
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Does Windows boot ok? It looks more like a BIOS install. Your partition layout is not the standard or recommended Windows layout.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

With UEFI you also should be able to boot both Ubuntu & Windows directly from UEFI boot menu or one time boot key.
Grub only boots working Windows. And currently grub will not boot Windows with secure boot on. If you really want secure boot you have to use one time boot key, often f10 or f12 to directly boot from UEFI. Ubuntu will work with Secure boot on.

You need to house clean the many duplicate UEFI entries for Unknown device which looks like it is using shim so an ubuntu entry that does not have correct description.
       
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD
[/URL]
    What brand/model computer or mother board? Some have known idiosyncrasies.

---

### Post by jonhd2 on 2015-12-11
Thanks for all of that. I'm going for a complete reinstall of Windows and Ubuntu, on the basis of what I've learned to date.
Fyi, I'm installing Win10 from the d/l ISO on to a machine - Acer E5-573 - that came with 8.1 preloaded, and which I authenticated.
I accepted Win10's 'default' install (partitioning) method, after first using the installer to delete ALL existing partitions & creating one partition for the entire disk - at which point the installer warned me that it might install additional partitions. What it actually produced was:
- 0:1 Recovery (450MB)
- 0:2 System (100MB)
- 0:3 MSR (16MB)
- 0:4 Primary (the remainder of the disk).
This was all done with the BIOS set to UEFI / Secure Boot disabled.
I'm currently installing Ubuntu 14.04.3 (again!), from a 'UEFI' usb pendrive (i.e. FAT32 formatted, with the contents of the Ubuntu ISO simply copied to the pendrive).

I shall probably return :-)

Jon

---

### Post by oldfred on 2015-12-11
Acer also in UEFI requires UEFI password and setting trust. 
Some of the very new ones require a down grade to UEFI.

These are all essentially the same, many link to each other. But some offer better explanation of details than others:
 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by jonhd2 on 2015-12-11
I was about to give-up! THIS is the one that fixed it for me - [http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
Very clear & concise - the step I had missed was having to return to the Boot Order menu, and move the shimx64.efi loader up (it was right at the bottom). No need to downgrade my BIOS, btw.

Thanks, Jon

---

### Post by oldfred on 2015-12-11
If solved you can change to [Solved] above first post.

---

