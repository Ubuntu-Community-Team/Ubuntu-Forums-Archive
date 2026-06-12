---
title: "Want to make clean ubuntu install with windows dual boot"
date: 2017-01-03
forum: Installation &amp; Upgrades
---

### Post by vdashv on 2017-01-03
Dear Ubuntu Community,

I've installed Ubuntu alongside a Windows 10.

Ever since I've done that my Windows 10 runs very very very very snail pace slow. Someone suggested that the linux partition must "boot" "simultaneously" with the Windows for this to happen. I investigated further and found the following:

1.)          [https://www.quora.com/Why-is-my-laptop-too-slow-after-dual-boot](https://www.quora.com/Why-is-my-laptop-too-slow-after-dual-boot)
2.)          [https://ubuntuforums.org/showthread.php?t=2209037](https://ubuntuforums.org/showthread.php?t=2209037)
[B]3.)          [https://ubuntuforums.org/showthread.php?t=2083684&p=12353102#post12353102](https://ubuntuforums.org/showthread.php?t=2083684&p=12353102#post12353102)  [<------ PARTICULARLY THIS VERY VERY IMP]

[/B]I'm planning to install another copy of Windows on the same laptop. This time I hope to make a clean install. Please guide me on how to install it alongside ubuntu so that both Windows and ubuntu can be at peace with each other. I'm forced to use Windows due to work, otherwise my primary OS is the U.

Thanks for reading

vdashv

---

### Post by oldfred on 2017-01-03
Is system UEFI or BIOS?

What version of Windows are you installing. If Windows 7 and UEFI system, you must copy Windows DVD to flash drive and copy & rename some boot files to make it UEFI bootable.

You cannot have Windows in UEFI & BIOS on same drive.
Windows with UEFI has to have gpt partitioning. Boot flag then is only for UEFI on ESP - efi system partition.
Windows with BIOS has to have MBR(msdos) partitioning and only boots from a primary NTFS partition with boot flag.

Slow Windows is often too small of a NTFS partition. Windows really wants 30% free to work well. If at 10% free, you may not be able to defrag as no working room.
Are you regularly running chkdsk & defrag?

---

### Post by ian-weisser on 2017-01-03
A wonderful feature of running Windows in a Virtual Machine is that you really can use applications on both OS at the same time.
Essential for my work. I'm never going back to dual-booting.

---

### Post by vdashv on 2017-01-03
> **oldfred said:**
> Is system UEFI or BIOS?

What version of Windows are you installing. If Windows 7 and UEFI system, you must copy Windows DVD to flash drive and copy & rename some boot files to make it UEFI bootable.

You cannot have Windows in UEFI & BIOS on same drive.
Windows with UEFI has to have gpt partitioning. Boot flag then is only for UEFI on ESP - efi system partition.
Windows with BIOS has to have MBR(msdos) partitioning and only boots from a primary NTFS partition with boot flag.

Slow Windows is often too small of a NTFS partition. Windows really wants 30% free to work well. If at 10% free, you may not be able to defrag as no working room.
Are you regularly running chkdsk & defrag?

Hi oldfred,

My windows is UEFI.

No do not run chkdsk or defrag [will do so from now on after successful installation]

Can I install a windows 7 BIOS alongside Ubuntu? Not using UEFI at all? Would that be better? 

What about "secure boot" option, I came across it too, along with "legacy"?

Thanks,

vdashv

---

### Post by vdashv on 2017-01-03
> **ian-weisser said:**
> A wonderful feature of running Windows in a Virtual Machine is that you really can use applications on both OS at the same time.
Essential for my work. I'm never going back to dual-booting.

I would do that but I need to use some pretty heavy applications in windows. The overhead from the Virtual Box running Windows running Heavy app accumulates very easily.

---

### Post by oldfred on 2017-01-03
You cannot have Windows 7 in BIOS mode on same drive as Windows 10 in UEFI.

Windows 7 default install is BIOS/MBR only. But can be relatively easily converted to UEFI boot/install.
While Windows 7 can be UEFI, it does not support UEFI Secure Boot.

       Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/](https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/)
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)

I am a proponent of UEFI/gpt, newer & better. But it is also more complex as it has 3 boot modes UEFI with Secure boot, standard UEFI & BIOS/CSM/Legacy. And while we often had to change one or two settings in BIOS, now there are a lot more and more with UEFI that may need changing from vendor defaults.
So some that are used to BIOS/MBR issues still prefer BIOS. But BIOS is 35 years old.

---

### Post by vdashv on 2017-01-04
> **oldfred said:**
> You cannot have Windows 7 in BIOS mode on same drive as Windows 10 in UEFI.

Windows 7 default install is BIOS/MBR only. But can be relatively easily converted to UEFI boot/install.
While Windows 7 can be UEFI, it does not support UEFI Secure Boot.

       Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/](https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/)
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)

I am a proponent of UEFI/gpt, newer & better. But it is also more complex as it has 3 boot modes UEFI with Secure boot, standard UEFI & BIOS/CSM/Legacy. And while we often had to change one or two settings in BIOS, now there are a lot more and more with UEFI that may need changing from vendor defaults.
So some that are used to BIOS/MBR issues still prefer BIOS. But BIOS is 35 years old.

Hello

I want to *overwrite* Win7 BIOS over Win10 UEFI. I think both OS's in BIOS / Legacy would make Ubuntu and Win7 be less at each other throats. Is this possible? 

Thanks
vdashv

---

### Post by vdashv on 2017-01-04
Also could the ubuntu in Legacy and Windows in UEFI make windows slow?

---

### Post by oldfred on 2017-01-04
How you boot should not make a difference once booted into the system. And if dual booting each is still separate. 

Many have dual booted in BIOS for years. And now many dual boot with UEFI.

With BIOS you only have the MBR, so only one system can control boot from BIOS. Grub will boot Windows, but only boots working Windows. So when Windows breaks, you need a Windows repair console. Typically chkdsk but possibly other repairs.

With UEFI the ESP - efi system partition has boot loaders for every system you install. Although Ubuntu only has one & Windows only has one, but you still can add other systems. And then choose each system from UEFI. You can multi-boot from grub, but again grub only boots working Windows. But with UEFI you can still directly boot Windows and possibly get into internal repair console. You still should have Windows repair/recovery flash drive.

---

