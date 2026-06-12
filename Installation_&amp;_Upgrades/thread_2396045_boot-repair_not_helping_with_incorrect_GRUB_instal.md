---
title: "boot-repair not helping with incorrect GRUB installation on Dell XPS 13 (2018)"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by ruenzuo on 2018-07-10
I've bought a Dell XPS 13 (2018) and I'm currently trying to set up dual boot for Windows and Ubuntu. I think I've pretty much the setup working in terms of partitions and BIOS settings, but my GRUB configuration doesn't work. I've tried a lot of different settings, by now I already installed Ubuntu/Windows more than 10 times, but this is what I've got so far:


[LIST]
[*]BIOS settings: fast boot, secure boot, load legacy ROM are disabled.
[*]Computer boots straight into the GRUB> console, so the boot sequence is actually happening, it's just the menu not rendering correctly
[*]After locating my boot partition I can do: `configload (hd0,gpt5)/boot/grub/grub.cfg` and successfully get a working menu, with entries for both Ubuntu and Windows. But I have to do this every single time I turn on the computer.
[*]I found this thread that has a lot of similarities with my case, although I tried the final suggestion without success: [https://forums.fedoraforum.org/showthread.php?185398-grub-issue-configfile-not-automatically-loaded](https://forums.fedoraforum.org/showthread.php?185398-grub-issue-configfile-not-automatically-loaded)
[*]Running boot-repair doesn't work for me. It messes up my grub.cfg (it adds 3 more entries to the menu that I don't need) but it still doesn't load the configuration automatically.
[*]My boot-repair report: [http://paste.ubuntu.com/p/ZrdB6PKt2F/](http://paste.ubuntu.com/p/ZrdB6PKt2F/)
[/LIST]

Any help would be greatly appreciated!

---

### Post by powerjas on 2018-07-10
Try turning off wifi and unpluging network cables then install ubuntu. That seems to be the trick right now to get installed.

---

### Post by ruenzuo on 2018-07-10
I would prefer to avoid reinstall Ubuntu, as I already set up all my tools. I've got a working setup, I just need some advice on how to configure grub to load the proper file at boot time, which I'm currently doing manually for every time I turn on the computer.

---

### Post by ajgreeny on 2018-07-10
I wonder if you installed Ubuntu using the legacy BIOS mode and not UEFI which you should have used for a new Windows 10 machine such as yours.

The Boot-Repair output near the top
> ============================ Drive/Partition Info: =============================

no valid partition table found is worrying as that should not be the case.

I also believe that some Dell machines need updated UEFI firmware and drivers for the Nvme SSD disk that you have.
See [https://ubuntuforums.org/showthread.php?t=2376851](https://ubuntuforums.org/showthread.php?t=2376851) for a thread about this problem; I can say this is the same as yours but it sounds similar.

---

### Post by ruenzuo on 2018-07-10
The computer was configured to boot using UEFI and security boot disable, I'm pretty sure Ubuntu is installed in UEFI mode because I have `/sys/firmware/efi` in my system.

I did the UEFI firmware update (suggested by Ubuntu Software Centre) but this was after the last installation of Ubuntu that I did, so I haven't installed Ubuntu on the new UEFI firmware. Do you think it's worth the chance reinstalling Ubuntu? Like I said, I'd really like to avoid that, given that I have everything set up and everything works, it's just the damn GRUB installation not loading the proper configuration file and displaying the right menu.

---

### Post by oldfred on 2018-07-10
Are you getting this:
grub>
If so can you boot with this, assumes NVMe drive is hd0 in grub:
       manual boot:
grub> set root=(hd0,gpt5)
grub> configfile /boot/grub/grub.cfg 

Your are the 4th post with /EFI/grub. Looks like the error in 18.10 supposedly fixed, was rolled out to 18.04 before the fix. It installs /EFI/grub, not /EFI/ubuntu.
      
 Ubuntu 18.10 Cosmic installed /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743)

If you can then boot, try copying /boot/efi/EFI/grub to /boot/efi/EFI/ubuntu. You may just need /EFI/grub.cfg which is a configfile entry similar to the manual boot comands above.

Not sure if reinstall of grub or just copy of files as temporary fix is all that is needed.

See similar post:
[https://ubuntuforums.org/showthread.php?t=2396050](https://ubuntuforums.org/showthread.php?t=2396050)

---

### Post by ruenzuo on 2018-07-10
Thank you so much! I can confirm that updating the package `grub-efi-amd64` and running update-grub fixes the issue. For anyone else experiencing the same, after booting Ubuntu:

$ sudo apt-get install grub-efi-amd64
$ sudo update-grub

This will create the proper cfg file in the right place. You just have to be sure that the BIOS is using `/boot/efi/EFI/ubuntu/shimx64.efi`.

---

