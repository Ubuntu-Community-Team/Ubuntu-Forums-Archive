---
title: "Toshiba Satellite Laptop"
date: 2015-04-17
forum: Installation &amp; Upgrades
---

### Post by GNUway Tech on 2015-04-17
I recently bought a new Toshiba Satellite laptop, and tried to install Ubuntu 14.10 on it. For some reason, it will format and install, but it won't boot from the hard drive.:confused:

It ran Windows 8.1 when I took it out of the box. I changed the boot order to boot from the DVD drive, and booted a newly burnt Ubuntu 14.10 disk. The install process went smoothly, it updated as it installed, and kicked the disk back out when it was done. I rebooted, changed the boot order back to boot from the hard drive, but I couldn't get it to boot from the hard drive after that. It just gave me a message to change the boot order, or reinsert the boot media. I burned a new disk and reinstalled it again, and the same outcome.](*,)

I called Toshiba, and, of course, they said it was out of their support after I reformatted it. They recommended spending $40 on a new recovery media.:mad:

Anybody else had this problem before??? I've never had a problem installing and booting Ubuntu like this. It just doesn't seem to want to boot the newly installed OS.

---

### Post by kc1di on 2015-04-17
give boot-repair a try found[ here :]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by GNUway Tech on 2015-04-17
I'll give that a try, thanks!!!

---

### Post by kc1di on 2015-04-17
> **GNUway Tech said:**
> I'll give that a try, thanks!!!

make sure to copy down the file address it gives you after boot-repair runs in case it does not work post the address here.
it has a lot of information that can be helpful to getting you going.

---

### Post by GNUway Tech on 2015-04-17
Ok, it didn't work. The address was [http://paste.ubuntu.com/10842326/](http://paste.ubuntu.com/10842326/). What do I do now???

---

### Post by kc1di on 2015-04-18
Your system is set up to boot in UEFI mode - If Ubuntu is going to be the only OS on the system then you can turn that mode off on some machines and it should boot without needing to install in UEFI Mode.  Not all Vendors allow you to turn it off though.  That may be the case for the Toshiba.  in that case you'll need to follow the procedures on [this page ]("https://help.ubuntu.com/community/UEFI")to get it to boot properly.  You must use the 64 bit version of Ubuntu to boot in UEFI Mode. 

Good Luck

---

### Post by oldfred on 2015-04-18
Many with Toshiba's found that Toshiba modified UEFI to only boot a UEFI description that says Windows. That is not per UEFI specifications. Those dual booting were able to copy grub to /EFI/Boot folder and use a hard drive UEFI entry that would work.

Others only booting Ubuntu change the name in UEFI to read Windows but really boot grub or shim.
If your UEFI still has a Windows entry to Windows files that are not now in efi partition you should delete that also.

 If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

    
I think these are were dual boot so renamed bootx64.efi which you could do, but rename is probably better since only booting Ubuntu.
 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

---

### Post by mattharris4 on 2015-04-19
> **kc1di said:**
> Your system is set up to boot in UEFI mode - If Ubuntu is going to be the only OS on the system then you can turn that mode off on some machines and it should boot without needing to install in UEFI Mode.  Not all Vendors allow you to turn it off though.  That may be the case for the Toshiba.  in that case you'll need to follow the procedures on [this page ]("https://help.ubuntu.com/community/UEFI")to get it to boot properly.  You must use the 64 bit version of Ubuntu to boot in UEFI Mode. 

Good Luck

If it helps I had an option to turn UEFI off when I installed Lubuntu on my one-year old Toshiba laptop.  It was in the UEFI screen (formerly called the BIOS on older computers).  This computer came with Win 8.1 as well.  Here is a link from Toshiba on how to boot from USB on these computers:  [https://aps2.toshiba-tro.de/kb0/TSB2B03F30002R01.htm](https://aps2.toshiba-tro.de/kb0/TSB2B03F30002R01.htm)

Technically disabling UEFI boot is unnecessary if installing an OS with a secure boot key like Canonical OSes since 12.04 have but that doesn't mean the computer won't have an issue here anyway.  Also, my install was a dual-boot with Lubuntu and Win 8.1 so since you have wiped Win off of your computer altogether my experience will only go so far here.  It is possible that newer Toshibas have something in the UEFI that does not allow elimination of Windows altogether like you are attempting to do -- the manner in which manufacturers are implementing UEFI is screwy at best and leads me to believe Microsoft may be paying them off to not allow installs of different OSes on their computers, some methods of which so far can be circumvented by people more versed in computer programming than I.  HP is a well known problem here at least with their computers made in the past year or so.  

Since it applies to the direction of posts here, rumor has it (I have read this in two different places) that Microsoft will be at least allowing manufacturers installing Win 10 on their computers as the OS (essentially) to design their UEFI in such a manner as to not allow Linux installs.  I hope that rumor is unfounded but with the reports on how some manufacturers have made installs difficult in Win8 already don't leave me much hope on this that the rumor is false or if true that Microsoft relents on this and continues to "require" that Secure Boot be able to be switched off (we all know they found other ways to prevent Linux installs anyway as discussed in this thread).  I think they are steamed that people did not either buy new computers or purchase and install a later Win OS after they cut support for XP with most installing a Linux based OS instead -- likely most of which installed a Canonical OS since those are the best known and supported which did not allow Microsoft and the new computer manufacturers to soak the public financially like they planned on by forcing them (in most cases) to replace their computers before they stopped working on their own. Here is a link discussing this:  [http://www.techradar.com/us/news/software/operating-systems/microsoft-s-windows-10-secure-boot-ruling-spells-trouble-for-linux-lovers-dual-booters-1289096](http://www.techradar.com/us/news/software/operating-systems/microsoft-s-windows-10-secure-boot-ruling-spells-trouble-for-linux-lovers-dual-booters-1289096) .  Here is another:  [http://www.extremetech.com/extreme/201722-linuxs-worst-case-scenario-microsoft-makes-secure-boot-mandatory-locks-out-other-operating-systems](http://www.extremetech.com/extreme/201722-linuxs-worst-case-scenario-microsoft-makes-secure-boot-mandatory-locks-out-other-operating-systems) .  If this does happen I hope that Dell expands their Linux compatible program to lower line computers that don't cost $1300 (most people don't need i7 processors and 16GB of RAM even with the most resource-intensive versions of Linux like Canonical's Edubuntu), preferably offering all of their computers with versions running Linux and a Linux compatible UEFI or BIOS and other manufacturers do likewise and sell computers with Linux pre-installed as well.  Otherwise we will all have to build our own computers (or have them built, fortunately in my area we have one computer shop that still does this) in the future.  I doubt all of the motherboard manufacturers would ignore this market and play along with Microsoft forcing us to use their products by installing non-Linux compatible UEFIs.  Yes, there are a few companies that sell Linux based computers now but they seem to charge a lot more for the privilege even though they save money by not purchasing a Windows license and should pass the savings on to their customers.  I hope those that read this start pondering this issue.  Maybe we should e-mail someone at Dell with this idea, if anyone knows someone there with some power to push this please publish their e-mail address.  End of rant.

---

### Post by GNUway Tech on 2015-04-20
I got it working guys. It turned out I was able to turn off Secure Boot and UEFI. I'd never heard of that problem before, but it's running now. Thank you.

---

### Post by mattharris4 on 2015-04-22
> **GNUway Tech said:**
> I got it working guys. It turned out I was able to turn off Secure Boot and UEFI. I'd never heard of that problem before, but it's running now. Thank you.

You are very welcome.  Enjoy your new computer. My sister has been using her Toshiba (with Win 7) for almost five years now, the only problem she had was when she spilled her Irish Coffee on her keyboard.  Evidently it was easily repairable because she hasn't had a problem since.  She does have an early iteration of the Intel i3 processor and 4GB of RAM which was rare back then.  She uses it for internet and accounting now, she used it for typing needed documents for her university classes as well so her computer is well-used and still works like a charm.

---

