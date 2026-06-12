---
title: "boot-repair can't reinstall grub"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by pussinboots on 2013-03-22
My boot-repair url is [http://paste.ubuntu.com/5638657/](http://paste.ubuntu.com/5638657/)

New machine (Gateway DX4380-UR308), came with Win 8.  I tried to install 64-bit Ubuntu 12.04 Desktop (using an iso downloaded ~2 days ago).  I booted from CD, selected install, had the entire disk wiped.  Install seemed to go fine.  I was able to install xfce and a few other things, configure the desktop, etc.  But, when I rebooted, I got a boot error on startup.  I followed the instructions at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  I was able to run boot-repair, but it hung while reinstalling grub.  After waiting ~30 mins, I killed it and rebooted.  I got to a grub prompt, but didn't know what to do at that point.  I tried boot-repair again and had the same problem.

I have disabled SecureBoot in my BIOS.

Any help is appreciated!

Jason

---

### Post by pussinboots on 2013-03-22
I just tried installing 12.10 (64-bit Ubuntu Desktop) and ran into the same problem.  The first reboot after install was successful.  But, when I rebooted a 2nd time, I got the same message as before ("Reboot and Select proper Boot Device or Insert Boot Media in selected device and press a key") at startup.  And, when I try to use boot-repair, it hangs while trying to "Reinstall GRUB.  This may require several minutes..."  "top" shows boot-repair.sh max-ing out a single core (99.9% cpu).

---

### Post by YannBuntu on 2013-03-23
hello,
You are the 2nd one I see with this problem. Please open a terminal, maximize it, run:
**sudo boot-repair -d**
then click Recommended Repair, and look carefully in the terminal. 
What are the last lines before it hangs?  (ignore the "pulse" lines)

---

### Post by pussinboots on 2013-03-23
Here's the last 30 or so lines before it hung.  It was all pulse's after the "Boot EFI files" line.

=> [[ PY ]] => [debug]/mnt/boot-sav/sda2/etc/fstab unchanged for /boot
=> [[ PY ]] => [email]SET@_progressbar1.pulse[/email]()
=> [[ PY ]] => [debug]/mnt/boot-sav/sda2/etc/fstab unchanged for /usr
=> [[ PY ]] => [debug]/mnt/boot-sav/sda2/etc/fstab unchanged for /boot/efi
=> [[ PY ]] => [debug]Freed space function
=> [[ PY ]] => [email]SET@_label0.set[/email]_text('''Checking full partitions. This may require several minutes...''')
=> [[ PY ]] => [debug]force_unmount_and_prepare_chroot
=> [[ PY ]] => [debug]Unmount all OS partitions except / and partition where we reinstall GRUB (sda2)
=> [[ PY ]] => [email]SET@_label0.set[/email]_text('''Unmount all except sda2. This may require several minutes...''')
=> [[ PY ]] => [debug]prepare_chroot
=> [[ PY ]] => [email]SET@_label0.set[/email]_text('''Applying changes. (chroot). This may require several minutes...''')
=> [[ PY ]] => [debug] Already mounted /dev/sda2 on /mnt/boot-sav/sda2
=> [[ PY ]] => [debug] mount_separate_boot_if_required yes , , grub-efi-amd64-signed ,
=> [[ PY ]] => [email]SET@_progressbar1.pulse[/email]()
=> [[ PY ]] => Mount sda1 on /mnt/boot-sav/sda2/boot/efi
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi: /EFI/ubuntu/grub.cfg /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi /EFI/ubuntu /EFI
=> [[ PY ]] => Boot EFI files in /mnt/boot-sav/sda2/boot/efi:
=> [[ PY ]] => [email]SET@_label0.set[/email]_text('''Unhide boot menu. This may require several minutes...''')
=> [[ PY ]] => [email]SET@_progressbar1.pulse[/email]()
=> [[ PY ]] => [debug]End fix /mnt/boot-sav/sda2/etc/grub.d/
[...]
=> [[ PY ]] => grub-install (GRUB) 2.00-7ubuntu11,grub-install (GRUB) 2.
=> [[ PY ]] => 
=> [[ PY ]] => Reinstall the grub-efi-amd64-signed of sda2
=> [[ PY ]] => [email]SET@_label0.set[/email]_text('''Reinstall GRUB . This may require several minutes...''')
[...]
=> [[ PY ]] => Installation finished. No error reported.
=> [[ PY ]] => grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0000,0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => Boot0000* ubuntu
=> [[ PY ]] => exit code of grub-install :0
=> [[ PY ]] => [email]SET@_progressbar1.pulse[/email]()
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi: /EFI/ubuntu/grub.cfg /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi /EFI/ubuntu /EFI
=> [[ PY ]] => Boot EFI files in /mnt/boot-sav/sda2/boot/efi:

---

### Post by pussinboots on 2013-03-23
My first reboot after running boot-repair was successful---it went right into Ubuntu.  But, then I rebooted again and got the BIOS error message ("Select proper Boot Device").

---

### Post by pussinboots on 2013-03-23
One odd thing I've noticed is that sometimes the BIOS uses "UEFI: HL-DT-ST DVDRAM GH82N" to name the DVD drive (in boot priority options); other times it uses a much simpler name like "CD/DVD".  I don't see any option to select whether drives use UEFI mode or not...

---

### Post by darkod on 2013-03-23
Yann can help you more with boot-repair since he developed the software. Also, I don't use UEFI but I have few things to point out:
On new UEFI enabled computers/boards for most boot devices you have two separate devices, the older legacy boot version and the UEFI version (usually with UEFI prefix). That applies to optical drives, usb sticks, etc.

If you don't want to use uefi boot, you should look for an option in bios and whether you can disable it. BUT if windows came preinstalled in uefi mode with your machine, you can't simply disable it, it will not boot windows any more. So, you have to stick with uefi boot.

Having said that, uefi dual boot still has issues, and it doesn't help that manufacturers are thinking only about Microsoft when developing products. One VERY important thing, is that if win8 is in uefi mode you HAVE TO install ubuntu in uefi mode too. In other words, you have to boot the ubuntu cd/usb with the UEFI prefix when installing. If you booted the legacy optical drive, it would load the cd in legacy mode and installing ubuntu in legacy mode (installing legacy version of grub2 instead of the uefi version).

With ubuntu you have options to "switch" grub2 to uefi version, but a new install might be easier.

How did you install ubuntu, which device did you boot?

---

### Post by pussinboots on 2013-03-23
According to [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) my CD/DVD is booting in UEFI mode because I see the boot menu screen with "Try Ubuntu..." "Install Ubuntu" "Check disc...".  I have tried installing directly from CD/DVD (at boot menu, select "install") and first using the live version ("Try Ubuntu") then installing via the desktop icon.

My disk is apparently GPT because when I run "sudo parted -l", it says "partition table: gpt".

I have a CSM option in my BIOS, but enabling that doesn't give me a non UEFI option for my hard disk.

I'm trying to do a clean install---no Windows.

Thanks!

---

### Post by darkod on 2013-03-23
For clean install I would disable UEFI if possible and if you can do that use msdos table instead of gpt. If you decide to use gpt and non-uefi boot make sure you create a small 1MiB partition first with NO filesystem and the bios_grub flag on it. It's necessary for grub2 to install correctly on gpt disks.

It might be some uefi issue with your machine and ubuntu. But if you can't disable uefi I guess you are stuck with it.

Your boot info from post #1 seems correct. I have no idea what could be wrong.

I would try the legacy boot + legacy install but that can only work if you find a way to disable uefi boot in bios.

---

### Post by YannBuntu on 2013-03-23
> **pussinboots said:**
> Here's the last 30 or so lines before it hung.  It was all pulse's after the "Boot EFI files" line.

(..)
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi: /EFI/ubuntu/grub.cfg /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi /EFI/ubuntu /EFI
=> [[ PY ]] => Boot EFI files in /mnt/boot-sav/sda2/boot/efi:

Thanks, this helped. I think I found something. I uploaded a possible fix on [the PPA]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages"): boot-repair 3.197~ppa39 
Please wait about 2hours, then update your boot-sav and boot-repair packages, and check if it still hangs?

---

### Post by pussinboots on 2013-03-23
It looks like it got a bit further (I made sure I was using 3.197 boot-repair and boot-sav).  Below is what the log now looks like before it hangs.  In the mean time, I managed to get my cd/dvd to boot in legacy mode and switched my drive to MBR, but I ended-up with the "...Select proper Boot Device..." error message at boot.  However, with legacy cd/dvd boot and MBR, I was able to boot from cd/dvd into my hard drive, so some progress.  For the below logs, I switched back to UEFI mode and GPT disk (and reinstalled 12.10).  Let me know if you have any other ideas!

[...]
=> [[ PY ]] => Installation finished. No error reported.
=> [[ PY ]] => grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0000,0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => Boot0000* ubuntu
=> [[ PY ]] => exit code of grub-install :0
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi: /EFI/ubuntu/grub.cfg /EFI/ubuntu/shimx64.efi /EFI/ubuntu/grubx64.efi /EFI/ubuntu /EFI
=> [[ PY ]] => Boot EFI files in /mnt/boot-sav/sda2/boot/efi:
=> [[ PY ]] => [email]SET@_progressbar1.pulse[/email]()
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi: /EFI/ubuntu/grub.cfg /EFI/ubuntu/shimx64.efi /EFI/ubuntu/grubx64.efi /EFI/ubuntu /EFI
=> [[ PY ]] => Boot EFI files in /mnt/boot-sav/sda2/boot/efi:
=> [[ PY ]] => cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (& .grb)
=> [[ PY ]] => touch: cannot touch `/mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.grb': No such file or directory
=> [[ PY ]] => cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
=> [[ PY ]] => touch: cannot touch `/mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootx64.efi.grb': No such file or directory
=> [[ PY ]] => cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi (& .grb)
=> [[ PY ]] => touch: cannot touch `/mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi.grb': No such file or directory
=> [[ PY ]] => Add /mnt/boot-sav/sda2/boot/efi efi entries in /mnt/boot-sav/sda2/etc/grub.d/25_custom

---

### Post by YannBuntu on 2013-03-24
> **pussinboots said:**
> => [[ PY ]] => Boot EFI files in /mnt/boot-sav/sda2/boot/efi:

This line shows you are using an old version of Boot-Repair.

To update Boot-Repair, boot your Linux-Secure disk, choose "Try Ubuntu", connect internet, open a terminal, and type the following command:
```
sudo apt-get update; sudo apt-get install boot-sav boot-repair
```

---

### Post by pussinboots on 2013-03-24
Here's what I got this time.  It was all pulse's after the last line.  I let it run for ~10 minutes before giving-up.  When I rebooted, the installed Ubuntu booted normally, but when I tried to restart after that, I got the boot error.  I've seen this pattern (1st reboot okay, 2nd reboot fails) many times---any idea why?

=> [[ PY ]] => Installation finished. No error reported.
=> [[ PY ]] => grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0000,0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => Boot0000* ubuntu
=> [[ PY ]] => exit code of grub-install :0
=> [[ PY ]] => [email]SET@_progressbar1.pulse[/email]()
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi: /EFI /EFI/ubuntu /EFI/ubuntu/shimx64.efi /EFI/ubuntu/grubx64.efi /EFI/ubuntu/grub.cfg

---

### Post by YannBuntu on 2013-03-24
> **pussinboots said:**
> 1st reboot okay, 2nd reboot fails) many times---any idea why?

Unfortunately no.

I uploaded another update, that might give us additional clues on why it hangs. It is available now.

---

### Post by pussinboots on 2013-03-24
Latest output.  It stalls at "(debug) endlsefi1 ubuntu/shimx64.efi ; ubuntu ."  I checked that the version was ppa40 (sorry about earlier, I didn't realize the ppa version was the important one).

=> [[ PY ]] => Installation finished. No error reported.
=> [[ PY ]] => grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => BootCurrent: 0003
=> [[ PY ]] => Timeout: 2 seconds
=> [[ PY ]] => BootOrder: 0000,0003,0002,0001
=> [[ PY ]] => Boot0001  Windows Boot Manager
=> [[ PY ]] => Boot0002* UEFI: ST31000524AS
=> [[ PY ]] => Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
=> [[ PY ]] => Boot0000* ubuntu
=> [[ PY ]] => exit code of grub-install :0
=> [[ PY ]] => Files in /mnt/boot-sav/sda2/boot/efi are: /EFI/ubuntu/shimx64.efi /EFI/ubuntu/grubx64.efi /EFI/ubuntu/grub.cfg /*/*/*/*
=> [[ PY ]] => (debug) endlsefi1 ubuntu/shimx64.efi ; ubuntu .

---

### Post by YannBuntu on 2013-03-24
Thank you.
Looks like it hangs in a loop, but I don't know why. (for coders willing to help, it is located in /usr/share/boot-sav/gui-action-grub.sh, lines 344~370)
I uploaded a new version (ppa41) , with even more debugging items. Please try it in about 2hours.

---

### Post by pussinboots on 2013-03-24
I added some debug statements and found that it gets stuck in the 2nd time through that loop at "ls_efi_partition" when EFIDOFI=/mnt/boot-sav/sda2/EFI.  In the first loop EFIDOFI=/mnt/boot-sav/sda2/boot/efi/EFI.  I added a debug statement inside ls_efi_partition and it looks like it is iterating over all files on sda2 (i.e. the entire Ubuntu install).  I'm happy to hack-in changes if you give me an idea of what to do.  Thanks!

---

### Post by YannBuntu on 2013-03-24
Wonderful ! :)
I will code a workaround ASAP, until I find a nicer solution.

EDIT: version 3.197~ppa43 will be available in ~2h

---

### Post by pussinboots on 2013-03-24
The good news: boot-repair completes successfully; when I rebooted, I got a nice grub2 menu; Ubuntu loaded as expected. :)

The bad news: when I rebooted a 2nd time, I got the all-too-familiar boot error message "...Select proper Boot Device..." :(

BUT! Then I tried boot-repair again and unchecked the "SecureBoot" option before proceeding.  After it completed successfully, I rebooted twice and got the grub menu (woo hoo!).  I rebooted a third time and got the grub menu again! :-} The only other thing I did differently besides unchecking "SecureBoot" was to do a hard powercycle (shut down instead of restart, then power button to turn on).  If you'd like to understand what exactly made the difference for me, I'm happy to do more testing.  FWIW, when running with SecureBoot unchecked, I had to copy-n-paste 4 apt-get commands to the terminal.

Thank you Yann!

This may not be important, but there was one thing I didn't understand.  When boot-repair finished, it said "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!"  Is this something I should have set in my BIOS?  I don't recall seeing anything in my BIOS that would have let me do this.

In case it's useful, here are the two urls from this message:

Default settings: [http://paste.ubuntu.com/5645074](http://paste.ubuntu.com/5645074)
Uncheck SecureBoot: [http://paste.ubuntu.com/5645090/](http://paste.ubuntu.com/5645090/)

---

### Post by oldfred on 2013-03-25
From UEFI, do you just see ubuntu (the folder) or do you see the files in the efi/ubuntu folder?

 EFI/ubuntu/grubx64.efi
  /EFI/ubuntu/shimx64.efi 

Your BootInfo shows this with two different BootOrders which is from your UEFI:


 BootOrder: 0003,0002,0001
Boot0001  Windows Boot Manager
Boot0002* UEFI: ST31000524AS
Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,0003,0002,0001
Boot0001  Windows Boot Manager
Boot0002* UEFI: ST31000524AS
Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
Boot0000* ubuntu

---

### Post by YannBuntu on 2013-03-25
> **pussinboots said:**
> Then I tried boot-repair again and unchecked the "SecureBoot" option before proceeding.  After it completed successfully, I rebooted twice and got the grub menu (woo hoo!).  I rebooted a third time and got the grub menu again! :-}

Glad it worked.

One question: is SecureBoot enabled or disabled in your BIOS ?  (don't change anything) 


You can ignore the "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!"  message. It helps only for old firmwares.

---

### Post by pussinboots on 2013-03-25
SecureBoot is disabled in my BIOS.  I figured disabling it would simply the boot process, but maybe I assumed wrong?  SecureBoot was enabled when I got the machine.

---

### Post by pussinboots on 2013-03-25
oldfred: I can see /boot/efi/EFI/ubuntu/shimx64.efi (using "ls" in an xterm), but I'm not sure what you mean by "From UEFI".  UEFI partition?  My UEFI partition is /dev/sda1 which is mounted as /boot/efi.

My problem is fixed, so you can certainly mark this thread as [SOLVED].

---

### Post by BlinkinCat on 2013-03-25
> **pussinboots said:**
> 

My problem is fixed, so you can certainly mark this thread as [SOLVED].

Hi, 

You can mark thread as solved - here's how -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by YannBuntu on 2013-03-26
I guess Oldfred meant "from the UEFI firmware menu" (="from the BIOS menu").

> **pussinboots said:**
> SecureBoot is disabled in my BIOS.

ok. Please don't change it.

Please could you :
1) Check in your BIOS that there is only one way to disable/enable SecureBoot ?  (eg is there a way to disable it only for HDD, and another to disable it only for DVD/USB ?). Please don't change anything in your BIOS.
2) From your installed session, run Boot-Repair --> Create Boot-Info, and tell me the new URL (URL n°1)
3) Boot on your Ubuntu-64bit DVD (or liveUSB), then run Boot-Repair --> Create Boot-Info, and indicate the new URL (URL n°2)

This won't change your boot. Your answers will help me improving Boot-Repair.

---

