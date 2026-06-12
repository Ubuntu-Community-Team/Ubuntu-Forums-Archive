---
title: "unable to get to grub on dual boot alongside win10"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2018-09-16
I installed lubuntu LTS on lenovo ideapad 110 using the alongside windows 10 option. installation finished OK. during the install it asked me to setup a separate password for bypassing some UEFI restrictions and said boot was going to ask me for that password after restart. after restart it kept showing me the lenovo logo and then restarting again. it can't get to the grub screen. it did not ask the special password.
i went to Bios and saw that ubuntu was listed as a device there at the top. windows was shown as another device. after moving windows to top I was able to get to windows.
is there a solution to this so I can use lubuntu on this laptop?

thanks everybody.

---

### Post by oldfred on 2018-09-16
Did you do an encrypted install, or was it installing a proprietary driver and wanted to turn off UEFI Secure Boot?

 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

 Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

### Post by stephenbbb on 2018-09-17
I clicked on install third party drivers. 

I will run boot-info and post the link tonite. You are very helpful and you helped me 2-3 year ago with installing over win8.1. back then I had to disable sth in Bios.

I encourage you to setup a gofundme page, so people can send some gratitude your way.

---

### Post by stephenbbb on 2018-09-18
[http://paste.ubuntu.com/p/6T8KVwKc4v/](http://paste.ubuntu.com/p/6T8KVwKc4v/)

let me know what can be done.

---

### Post by oldfred on 2018-09-18
As Boot-Repair says, try with UEFI Secure Boot off.
It shows you have the generic kernels installed not the signed versions for Secure Boot.

Have you updated UEFI to newest available?
You may have one now that can be updated from Ubuntu.
       [URL="https://fwupd.org/lvfs/devicelist"]https://fwupd.org/lvfs/devicelist

      [/URL]
 but this user seemed to have update, but no notice?
[URL="https://ubuntuforums.org/showthread.php?t=2401445"]https://ubuntuforums.org/showthread.php?t=2401445


[/URL] 

    [URL="https://fwupd.org/lvfs/devicelist"]
[/URL]

---

### Post by stephenbbb on 2018-09-19
does that mean go in Bios/Boot and disable the UEFI setting? Can you refer me to how to do Secure Boot off??
also, after I disable, what device should be #1 in the boot sequence? ubuntu or point to the hard disk?
I want to see the grub menu, which allows me to choose between ubuntu and win10.

again: I will donate if you setup a gofundme page.

---

### Post by oldfred on 2018-09-19
Every UEFI is different.
My system says under OS type "Windows" or "Other" but fine print says if using Windows 7 in UEFI boot mode, you must use "Other". That is because Windows 7 does not support UEFI Secure Boot. Attached is mine, some others:
       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

Generally you want the ubuntu entry first. If you have run Boot-Repair it changes the hard drive or fallback entry to shimx64.efi which is grub for secure boot but works if Secure Boot is on or off. 
The fallback/hard drive entry is /EFI/Boot/bootx64.efi. But that file normally is a copy of Windows .efi boot file.

Since grub only boots working Windows, and Windows will turn fast start up back on with updates or be corrupted and need chkdsk, you need to be able to directly boot from UEFI boot menu. But best to also have the Windows repair flash drive.

Next time I am in town, you can buy me a cup of coffee (or a beer). :)
We all are volunteers, and offer whatever help we can.

---

### Post by stephenbbb on 2018-09-20
There is a Security tab in Bios and there I clicked Secure Boot disabled (it was enabled). I set the hard disk as #1 in the boot sequence and that got me straight to Win10. my daughter then took over the laptop so I was not able to try ubuntu at the top.
I have not run boot-repair. 
should I run boot-repair?

---

### Post by oldfred on 2018-09-20
I think Boot-Repair's summary report is always good to have.
I run it regularly and it uses the older command line bootinfoscript as first part of report & I run that script as part of my backup script.

Most times Boot-Repair works. Occasionally it makes some assumption on system that is not the best. If running it often better to use its advanced mode for fixes.

---

### Post by stephenbbb on 2018-09-21
solved. setting ubuntu at the top of the boot, after disabling secure boot, got me to the grub menu.
HAPPY :-)

---

