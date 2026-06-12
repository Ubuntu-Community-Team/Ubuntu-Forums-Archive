---
title: "grub does not appear after unetbootin install of Ubuntu 12.04.2 on a Win8 laptop"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by BeachBuddah on 2013-08-18
Hello all,
I have tried to follow the directions found here and on IRC to install Ubuntu 12.04.2 from a live CD with no joy.
So, I opted to try the live USB installation using unetbootin.  Some joy.
12.04.2 is indeed installed on my hard drive.  But when booting, I go directly to Windows 8.  GRUB never appears.
To get to Ubuntu, I must interrupt the boot process and choose 'Boot Options'.  Ubuntu is an option on that screen.  
When I highlight and choose that option, I am taken straight to GRUB with the various Ubuntu choices as well as Windows 8.
The question is, 'How do I make that "Ubuntu" option the default when I power up my machine.

Any and all requests for further information will be cheerfully complied with.  TIA for your time and help on this issue.

Also, apologies if this thread exists elsewhere and I am rehashing a solved problem.

---

### Post by oldfred on 2013-08-18
With BIOS you only have one boot loader in the MBR of the drive. And whoever installs last is the boot choice.

But with UEFI you have many boot loaders in one efi partition. So you have to go into UEFI and set which system you want to boot as default. Choose ubuntu. 
Also those settings can now be reset from Windows (maybe Ubuntu should also?) so updates or repairs to Windows may change it back to Windows.

Also grub2's os-prober does not create correct chain load entries to Windows. You need to use Boot-Repair to automatically add correct entries or can manually add as described in bug report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
os-prober fix in grub2_2.00-14 and os-prober_1.58 from Debian

---

### Post by BeachBuddah on 2013-08-18
oldfred,

Thanks for the quick response.  I got into Ubuntu and let boot repair work its magic.  I have two pastes to offer.  the ifrst is before any attempt to fix and the second is after.  I was forewarned by the program that since Ubuntu is on sda6, it is pretty far down the pecking order and my computer may not see it.  This is so, as I am writing this post from Windows8, where I booted right in without so much as a by your leave.  I will work through your other suggestions in your post and respond as I can.  So, here you go:

paste.ubuntu.com/6000573  -  before
paste.ubuntu.com/6000585  -  after

Thanks again.

---

### Post by oldfred on 2013-08-18
So are you booting Windows from UEFI or from grub menu?

What happens on ubuntu choice with UEFI and boot default, or if that does not work boot second choice in menu (or sub-menu) which is a recovery boot?

What video card/chip? As that often causes issues.

The files beyond a certain point on hard drive is primarily BIOS boot and most often BIOS booting from USB drive. I have yet to see a UEFI system that needed a separate boot because of that issue.

HP puts a lot of efi files for booting various recovery or HP utilities in the efi partition. Most other vendors boot those from another partition. But because Boot-Repair found all those efi files it created boot entries. You may not want all of them in grub menu. The link in my signature has some info on manually editing 25_custom to remove the extra entries.

---

### Post by BeachBuddah on 2013-08-18
> **oldfred said:**
> So are you booting Windows from UEFI or from grub menu?
[COLOR="#0000FF"]When I start the laptop, it boots directly into Windows if I do not pause the boot process.  I assume that means I am going through UEFI.
I have the option, if I pause the boot process and choose the Ubuntu option, I go to GRUB and have a choice there to boot to Windows 8.[/COLOR]

What happens on ubuntu choice with UEFI and boot default, or if that does not work boot second choice in menu (or sub-menu) which is a recovery boot?
[COLOR="#0000FF"]Please rephrase this question, oldfred, I have no idea how to respond.[/COLOR]

What video card/chip? As that often causes issues.
[COLOR="#0000FF"]My video is as follows:
Intel HD Graphics 4000
NVIDIA GeForce GT 650M
[/COLOR]
The files beyond a certain point on hard drive is primarily BIOS boot and most often BIOS booting from USB drive. I have yet to see a UEFI system that needed a separate boot because of that issue.
[COLOR="#0000FF"]OK[/COLOR]

HP puts a lot of efi files for booting various recovery or HP utilities in the efi partition. Most other vendors boot those from another partition. But because Boot-Repair found all those efi files it created boot entries. You may not want all of them in grub menu. The link in my signature has some info on manually editing 25_custom to remove the extra entries.
[COLOR="#0000FF"]You're right about the extra boot entries - I have about 8 more than I did before I pushed the 'Fix Common Errors' button.  I'll follow your link, thanks.[/COLOR]

---

### Post by oldfred on 2013-08-18
You have Optimus and which video is active when you boot is important. Intel should just work but some very new versions need boot options. If nVidia you will need to add nomodeset to the grub linux line and that may help with Intel.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

On grub menu you should have this entry one below the default. With grub2 it may be in a sub-menu.


>  menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)'



It may boot and then give options on what to try next.

---

