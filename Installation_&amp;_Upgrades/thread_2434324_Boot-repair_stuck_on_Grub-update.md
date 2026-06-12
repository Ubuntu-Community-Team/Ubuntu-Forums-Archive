---
title: "Boot-repair stuck on Grub-update"
date: 2020-01-03
forum: Installation &amp; Upgrades
---

### Post by tobiz on 2020-01-03
I thought boot-repair was to be my savior.  My machine is single boot into kubuntu 18.04 (single disc), with all updates applied as of 2020/01/02. After running synaptic auto delete it won't boot, it says the screen resolution is incompatible, or some such and puts you into command mode. I managed to get the machine to boot from a usb stick with kubuntu 18.04 on it (after making some changes to the Azus bios and understanding how to override the hdd as the priority #0 boot drive). I'm now running under the "Try kubuntu" option and am checking my backup drive and what I can copy of the main HDD (which is mounted). I ran boot-repair and it came up with the 2 options, I selected the topmost to 'do standard fixes'.  All ran ok but the grub-update slider slowed down and stopped, no URL was output, the slider just stopped. I found the boot-repair log, the last few meaningful lines of which are:

```

df /dev/sda1
Save and rename /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/Boot/bootx64.efi (/media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/ubuntu/shimx64.efi /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/Boot/bootx64.efi
efi files in sda1/efi: /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/fwupx64.efi /BOOT/fbx64.efi /BOOT/bootx64.efi /BOOT/bkpbootx64.efi 
Add /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi efi entries in /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/etc/grub.d/25_custom
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Adding custom /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/BOOT/bkpbootx64.efi
Adding custom /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/BOOT/fbx64.efi
Adding custom /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/ubuntu/fwupx64.efi
Adding custom /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141/boot/efi/EFI/ubuntu/mmx64.efi
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
..........
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Installing for x86_64-efi platform.
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0

chroot /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141 efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0000,0004,0003,0002
Boot0000* ubuntu    HD(1,GPT,73c08370-c091-4c67-a15d-10dd8abc20bc,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001  UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0002* Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .M...2. .1.T.B....................A...........................>..Gd-.;.A..MQ..L.4.S.5.1.B.N.K.0.1.6.5.0.8.8. .D. . . . ........BO
Boot0003* USB    BBS(HD,,0x0)..GO..NO........s.K.i.n.g.s.t.o.n.D.a.t.a.T.r.a.v.e.l.e.r. .2...0.P.M.A.P....................A.......................F..Gd-.;.A..MQ..L.4.0.8.D.5.C.E.4.C.1.E.E.B.2.2.0.8.9.3.4.9.A.0.F........BO
Boot0004* UEFI: KingstonDataTraveler 2.0PMAP, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x459885a6,0x1f80,0x39ac080)/CDROM(1,0x38cdd4,0x4d00)..BO
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Grub-update. This may require several minutes...''')

chroot /media/kubuntu/6e7cd9fb-dee0-4af4-a290-8ef472296141 update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Found linux image: /boot/vmlinuz-4.15.0-72-generic
Found initrd image: /boot/initrd.img-4.15.0-72-generic
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Found linux image: /boot/vmlinuz-4.15.0-70-generic
Found initrd image: /boot/initrd.img-4.15.0-70-generic
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
....
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
File descriptor 9 (/proc/453/mountinfo) leaked on lvs invocation. Parent PID 11865: /bin/sh
File descriptor 63 (pipe:[1156571]) leaked on lvs invocation. Parent PID 11865: /bin/sh
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()

```

The remaining lines are SET@.......

Has this issue bee seen before?  What's gone wrong? If needed I can supply the full log.

I've just noticed from KSysGuard that boot-repair is a "zombie" (not unsurprisingly)

---

### Post by oldfred on 2020-01-04
Please use code tags for terminal or longer output. 
Easy to add with forum's advanced editor and # icon.

Post link to summary report from Boot-Repair.
It primarily reinstalls grub and may do some other minor fixes. But if you uninstalled something essential it probably does not know how to fix that.

If you update UEFI/BIOS, you have to redo all the changes. With my Asus motherboard I had multiple changes, some essential and some optional to improve things. I have to keep a list. With old BIOS I did photos. Newer system does screenshots as long as I have a FAT32 partition to save them to.

Asus Z97-a BIOS only install , settings for UEFI  
[http://ubuntuforums.org/showthread.php?t=2296538%20%20%20](http://ubuntuforums.org/showthread.php?t=2296538%20%20%20)
Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by tobiz on 2020-01-05
It's a long time since I've used this forum and apologize for not having used the CODE tags correctly. For the long log files I've used ubuntu paste-bin.

I ran boot-repair twice, first time it ran and produced the 2 options; I exited the program having, I thought told it to do nothing. Second run selected the Take Default action and it eventually hung.

The only change I made to the AZUS BIOS was to move the USB boot option to  priority #1. I discovered this made no difference, it always booted from the SSD drive (the only 'drive' on the machine). I solved this by seeing that there is a Boot Override option which is set to the SSD. I found the way to override this "override" is to completely power down the machine and then boot, this then uses the boot # priority sequence (ignores the Boot Override), so used the kubuntu usb iso and booted into the 2 options for an install: #1 try kubuntu and #2 new install.  New install was obviously not the best option as it only offered disc reformatting, no option to retain existing data.  This is the point when I discovered boot-repair, tried that and that's where I am now.  

The machine is at most 2 years old. Kubuntu 18.04 was installed by the manufacturer for me and probably uses UEFI.  The BIOS boot priority options where originally: #1 UEFI HDD; #2 UEFI CD; #3 UEFI LAN; #4 Legacy HDD; #5 Legacy CDROM; #6 Legacy LAN; #7 UEFI USB; #7 Legacy USB.

I'm beginning to think the only way out of this is to backup the total SDD (sudo cp -a "ssd/" "usb-external-drive"), get the manufacturer to re-install Kubuntu 18.04 and slowly recover may data from the backup plus recover installed programs from apt-get (not sure how), plus anything else that can be salvaged. 

The log files are included at: log #1  [https://paste.ubuntu.com/p/s3BpjWVFTY/http://]("https://paste.ubuntu.com/p/s3BpjWVFTY/http://") and log #2 [https://paste.ubuntu.com/p/xQJJbjrc9r/]("https://paste.ubuntu.com/p/xQJJbjrc9r/")

TIA

---

### Post by oldfred on 2020-01-05
Your first link does not work, and second is the total log file of Boot-Repair, not the Summary Report.
Please post Summary Report, you probably do not need a full install. 
Some just do a new install as that can be as little as 10 min to install, 20min to update apps & copy /home back and some reconfiguration. Or about an hour if you  have procedure down pat.

You currently show UEFI default boot as 0004 which is your flash drive.

While now older, this is my backup using rsync. I basically copy /home, my data partition(s), and list of installed apps. I also like to export various hardware configuration, just to have the info. I now run a houseclean script and still exclude some data in backup.  I do end up also copying some critical data to DVD, and several flash drives. And have all data on another system in another state.
Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 

Better than my procedure.
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)

---

### Post by tobiz on 2020-01-05
I killed boot-repair, installed boot-info, which produced [http://paste.ubuntu.com/p/D7hM77RVFg/]("http://paste.ubuntu.com/p/D7hM77RVFg/"), (I checked it's there).

From the manufacturers website it claims their systems motherboards have "ASUS Self-recovering BIOS", see [https://www.asus.com/Motherboards/PRIME-H310T/#LEARNMORE]("https://www.asus.com/Motherboards/PRIME-H310T/#LEARNMORE") which suggests the bios should be ok, so the problem is higher up the chain.

Does that help?

---

### Post by oldfred on 2020-01-05
It is not showing the normal boot folders & files in the ESP - efi system partition, your sda1.
Are /EFI/Boot & /EFI/ubuntu in that partition?
Or is partition corrupted and that is why a grub re-install is not working?

If files are not there, try this:
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

