---
title: "Windows corrupt my uefi"
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by keepitperso on 2013-12-20
Hi there,

I have installed ubuntu on my HP PC, brand new and shinny with uefi. Everything went fine, grub got both install and I can choose ubuntu or windows 8.

As long as I boot from ubuntu, everything works. If I but on windows, windows 8 starts, but when I shut it down from windows 8 or restart it, all hell break lose and the UEFI doesn't work anymore, I have to manually select the ubuntu UEFI (something shimx64...) then Ubuntu starts, I run boot-repair and grub is back at the startup and as long as I stay in Ubuntu everything is great, however, if shutdown from windows, the UEFI stops working again.

I hope this is somewhat understable, any ideas would be very welcome!

---

### Post by fantab on 2013-12-20
How are you booting Win8, from Grub menu or UEFI/BIOS menu?
Do you have 'Secure Boot' enabled or disabled?
How about 'FastStartup', it is disabled?
Did Windows update recently?
Run 'Boot-Repair' again but this time 'Create a Bootinfo Summary', and note the Link it creates. Post the LINK here.

---

### Post by keepitperso on 2013-12-20
Windows is booting from grub.

Windows boot with or without 'secure boot', but even with secure boot off, it changes the UEFI
Ubuntu only start if secure boot is activated, otherwise it hangs, same for the live CD.

It is a brand new install of both. Windows is up to date and start well after a boot repair. the uefi crashes once windows has been turned off.

Here is the link for the summary [http://paste.ubuntu.com/6605571](http://paste.ubuntu.com/6605571)

Thank you for your help.

---

### Post by fantab on 2013-12-20
Disable 'Secure boot' and see how it goes with Windows.
Is 'FastStartup'/Hibernation disabled in Windows?

I suspect the problem is on Windows side...

---

### Post by oldfred on 2013-12-20
It looks like Boot-Repair did its rename for 'buggy' UEFI. That is for those UEFI that are hard coded internally to only boot the Windows efi file. If you can boot ubuntu from UEFI, I would undo the rename.

       Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by keepitperso on 2013-12-20
as stated before, same windows start well whether secureboot is enabled or not, after i have done a boot repair. Once I shut windows down, the uefi path is not correct anymore.

Ubuntu and ubuntu live CD will not boot if secureboot is disabled.

When secure boot is enable, grub and ubuntu will load and restart perfectly as long as I do not start and shutdown windows.

---

### Post by keepitperso on 2013-12-20
Thank you oldfred for the insight.

So I have undo the rename, and it booted normally on Windows, with no grub. Went back to ubuntu and done a boot-repair with the option of rewrite for hard coded uefi as advised in some of the posts. Now grub comes as long as I don't boot windows, but as soon as it boot windows, the uefi is overwritten, and now, it is just windows that starts. I am desperatly looking for the option in windows that change the boot-repair modifications...

Any ideas?

---

### Post by oldfred on 2013-12-20
After you undid the rename, did you try to boot ubuntu entry in UEFI menu? You got Windows boot as it was the default and with the rename was really booting a copy of grub2's shim file.

If you can boot ubuntu from UEFI then undo rename, can change UEFI or try one time boot entry (f12 on my system, but varies) to see if you can directly boot ubuntu.

Boot-Repair dumps your UEFI internal boot choices with this command, so ubuntu should be there.

 efibootmgr -v


>  Boot0000* ubuntu	HD(2,200000,b4000,80218841-af27-4b91-a32c-ac396fd8cf30)File(EFIubuntushimx64.efi)



---

### Post by keepitperso on 2013-12-20
Once I have restarted windows and lost the automatic grub, I can manually boot from ubuntu (by pressing escape right at the beginning and select the ubuntu uefi, then I get the grub selection) and I can start ubuntu or windows fine, but despite my repair attempts, every time I load windows, I lose the automatic startup of grub uefi, it reset to windows uefi, which I would like to change. I am pretty sure it is a windows feature, and I know we are in a ubuntu forum, but I just wanted to know how I can always start from grub uefi.

Thank you again and again for trying to help me.

---

### Post by fantab on 2013-12-20
If it were a 'renaming' issue like oldfred suspected then, in my experience, Windows will NOT start at all from Grub menu.
However in your case Windows starts alright from grub menu but it creates problems you describe when you try to shut it down.

I am not sure what could be causing that. I suggest you raise your question/problem [HERE]("http://www.eightforums.com/"). Perhaps Win8 users are familiar with this issue.

---

### Post by oldfred on 2013-12-20
I saw this in askubuntu.

 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

---

### Post by keepitperso on 2013-12-21
Thank you oldfred, the link you gave me explained the solution to the problem I have found. The problem does come indeed from inside windows, I have followed the link below.

To resume, in windows run command prompt as administrator and paste the following
> bcdedit /set {bootmgr} path \EFI\refind\refind_x64.efi

Change the path with your Grub/SYSLINUX/Gummiboot/whatever if you don't use rEFInd. Boot-repair usually gives the path to you once finished.

Here is the original solution : [https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

The only thing is now it boot straight into ubuntu, and I cannot get grub to display, here is my new paste link: [http://paste.ubuntu.com/6610548/](http://paste.ubuntu.com/6610548/). What is annoying is it was working fine for a while, I just rerun boot-repair a last time to change the time grub was displayed and now I cannot see grub, even if I change the time again!

---

### Post by keepitperso on 2013-12-21
Discard my last request, everything is working perfectly, it is my screen. Exceptionally I am using a TV instead of a computer screen, and every time the signal reset it takes a few second to turn on the screen, which means that due to my short grub time I didn't see it as the tv was off ! Now that I know, I can handle it! Very stupid to waste an hour for this!

---

### Post by oldfred on 2013-12-21
Glad you got it working. :)

---

