---
title: "Dual boot win8 w/ ubuntu issue"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by dpar18 on 2012-12-04
Hello,

I recently installed ubuntu on my laptop that came with windows 8. I was unable to access/run the installed ubuntu, because of problems with the windows 8 boot loader, so I booted into ubuntu from a live-usb and ran boot-repair. This boot-repair allowed me to boot into ubuntu using grub, but the other boot options (windows 8 ) had some sort of problem regarding EFI's. I am effectively stuck with my only working boot option being Ubuntu.

I ran boot-repair again to see if any problems would be fixed, but nothing helped. Running boot-repair yields the following information [http://paste.ubuntu.com/1409675/](http://paste.ubuntu.com/1409675/) .

I was wondering if you could help me change grub or something to allow me to choose to boot into either windows 8 or ubuntu.

Thanks.

---

### Post by grahammechanical on 2012-12-04
Did you see this?

> Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!

I do not know if that makes a difference. You also say this:

>  the other boot options (windows 8 ) had some sort of problem regarding EFI's.

It would help if you gave us the error messages you get when you select the Windows 8 options from the Grub menu.

Regards.

---

### Post by oldfred on 2012-12-04
Grub2's os-prober does not create correct chain load entries for Windows, it still does BIOS type not efi type. Boot-Repair added a correct entry for standard Widnows.

Should work:
Windows UEFI loader

Will not work:
Windows 8 (loader) (on /dev/sda4)

But you have some efi files, that I have not seen that look like you may have encryption?  Or is that just for HP's BIOS (UEFI) update?

From UEFI menu you should get several boot options, now including ubuntu, windows and the other HP options. If the standard windows boot works then the chain load entry that Boot-Repair added should work from the ubuntu entry.

---

### Post by YannBuntu on 2012-12-05
Welcome among us !

> **dpar18 said:**
> Running boot-repair yields the following information [http://paste.ubuntu.com/1409675/](http://paste.ubuntu.com/1409675/) 

I'm sorry there was a bug in the Boot-Repair version you used.
Please :
1) wait that all packages have a green check in this page: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
2) then update and retry Boot-Repair

---

### Post by dpar18 on 2012-12-05
Hello and thank you all for the help so far,

Still encountering the same boot issue. 
I ran apt-get update followed by apt-get upgrade, which, correct me if I'm wrong, I believe correctly updated boot-repair.

Running boot-repair once again yields:
[http://paste.ubuntu.com/1413771/](http://paste.ubuntu.com/1413771/)

In response to a previous post, I've recorded the following error messages via pen and paper; at the grub menu, I am given the following windows related options:

Windows UEFI loader
Windows Boot UEFI bootx64.efi.bkp
Windows 8 loader (on /dev/sda4)

When selecting 'Windows UEFI loader' I receive the following messages:
/EndEntire
file path:/ACPI(a0641d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,c8800,82000,2b19d1dca1b85548,88,e0)/File(\\Microsoft\Boot)/File(bootmgfw.efi.bkp)/EndEntire
error: cannot load image.

When selecting 'Windows Boot UEFI bootx64.efi.bkp' I receive the following:
/EndEntire
file  path:/ACPI(a0641d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,c8800,82000,2b19d1dca1b85548,88,e0)/File(\\EFI\Boot)/File(bootmgfw.efi.bkp)/EndEntire
error: cannot load image.

When selecting 'Windows 8 loader (on /dev/sda4):
error: Secure Boot forbids loading module from (hd0,gpt6)/boot/grub/x86_64-efi/ntfs.mod
error: failure reading sector 0x0 from 'cd0'.
error: failure reading sector 0x0 from 'cd0'.
error: no such device: 02BA4919BA490B1D
error: can't find command 'drivemap'.
error: invalid EFI file path

It would seem that running the updated boot-repair was unable to fix the bug, and I also noticed a 'Repair Windows boot files' option, but the selection was grayed-out, and I was unable to select it.

Hope this can help you guys help me, and thanks again for the help!

---

### Post by oldfred on 2012-12-06
That the third entry does not work is correct. Grub currently does not create a correct entry. That entry is an old BIOS type entry.

But the other two should.
But in you Windows partition you show both bootmgr & the BCD. Those normally are there only with BIOS Windows installs. The efi bootmgr is the one used with UEFI install and BCD is not shown but I think it is also in the efi partition.

Was this originally a BIOS Windows install? It does not look like it as you have many efi files and efi files for HP & system diagnostics. 

Have you turned off quick boot and secure boot?

HP seems to have the logic reversed.

> If you want to launch non&#8211;HP-signed EFI applications for development purposes, follow these steps:
1. Access the Computer Setup utility and select System Configuration.
2. Select Device Configurations, select UEFI Boot Mode, and then select Enabled.


---

### Post by YannBuntu on 2012-12-06
> **dpar18 said:**
> correct me if I'm wrong, I believe correctly updated boot-repair.

Yes, you correctly updated and used it.


As OldFred said, the "Windows 8 loader (on /dev/sda4)" is not expected to work. But the 2 other entries (created by Boot-Repair) should have worked, i don't know why they don't.

Currently you have SecureBoot enabled.

If i were you, i would do this:
**1)** in the firmware (~BIOS), disable "QuickBoot" if you can. Then reboot and check if that helps. If not, do next step:
**2)** run Boot-Repair --> Advanced options --> untick "Create backup and rename EFI files" --> tick "Restore EFI backups" --> Apply. Tell us the new URL that will appear. Reboot and tell us what you observe.
If still not good, do next step:
**3)** in the firmware (~BIOS), disable "SecureBoot". Then run Boot-Repair --> Recommended Repair. Tell us the new URL that will appear. Reboot and tell us what you observe. If still not good, do next step:
**4)** run Boot-Repair --> Advanced options --> untick "Create backup and rename EFI files" --> tick "Restore EFI backups" --> Apply. Tell us the new URL that will appear. Reboot and tell us what you observe.

---

### Post by dpar18 on 2012-12-06
So to see what happens, I deselected Secure Boot from the advanced options for boot-repair.([http://paste.ubuntu.com/1415390/](http://paste.ubuntu.com/1415390/)) Boot-repair then asked me to input a set of commands into the terminal which I believe purged grub or something. After rebooting, the computer first gives me a message:
Selected boot image did not Authenticate. Press <Enter> to Continue.

After pressing enter, I am given what I believe is the computers built in boot manager. And given the following options:
OS boot Manager
Ubuntu (Hitachi HTS547575A9E384)
Boot From EFI File

The 'OS boot Manager' and 'Ubuntu (Hitachi HTS547575A9E384)' options both give me the same error message as before.
Selecting 'Boot From EFI File' first displays a message:
NO VOLUME LABEL, (some long address)

I am then given the ability to navigate my boot files via the "File Explorer", and can navigate to different .efi files in my system, however the only one that works is located at EFI/Boot/bootx64.efi.bkp, which boots my system into windows. 

So currently, I have a (nasty) way of booting into windows, and no way to boot into ubuntu. However I do have to option of booting from a live-USB and re-running boot-repair, which is how I got where I am in the first place.

Would it be advisable to re-enable Secure Boot? Or is there somewhere I can go from here?

---

### Post by dpar18 on 2012-12-06
> **oldfred said:**
> Was this originally a BIOS Windows install? It does not look like it as you have many efi files and efi files for HP & system diagnostics. 

Have you turned off quick boot and secure boot?


I bought the computer new with windows 8 installed on it, and installed Ubuntu 12.10 via a live-usb.

---

### Post by oldfred on 2012-12-06
This user had HP and two drives that worked.

       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by YannBuntu on 2012-12-06
> **dpar18 said:**
> the only one that works is located at EFI/Boot/bootx64.efi.bkp, which boots my system into windows.

ok , so you did Step 3) of my previous message.

Now, please do Step 4) :

> 4) run Boot-Repair --> Advanced options --> untick "Create backup and rename EFI files" --> tick "Restore EFI backups" --> Apply. Tell us the new URL that will appear. Reboot and tell us what you observe. 

(I expect the "OS boot Manager" entry to work)

---

### Post by dpar18 on 2012-12-10
Hello,

I apologize on the slow response to your last post. I was able to find the kindof hacky work around of, when wanting to boot to windows, spamming the f9 key before the computer reaches the grub menu, allowing me to choose the boot order. This lets me navigate to the windows 8 .efi file. If I don't want windows 8, I just wait for the computer to reach the grub.

I currently use my computer heavily, and this workaround works, however I plan to follow up and try the other fixes when I have more time. I just wanted to keep it at a fully functional state while I finish off the semester, in case any problems arise when trying the fixes.

Shall I mark the thread as solved until I plan to return to it?

Thanks a lot for all of the help so far!

---

