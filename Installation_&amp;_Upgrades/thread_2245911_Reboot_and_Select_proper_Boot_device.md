---
title: "Reboot and Select proper Boot device"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by marce2 on 2014-09-27
I'm getting the problem stated on the title. I will first provide some background.

After some residential intermittent electrical faults, I was unable to boot:
> Gave up waiting for root device. Common problems:
  - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/932ff6... does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframs) 


It was solved --I could boot from my primary HDD-- by replacing the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` with
```
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=60 quiet splash"
```
in /etc/default/grub

Then I notied that my secondary disk was not working, and removed it from the box.

I've been unable to boot ("Reboot and Select proper Boot device") since then.

Booting from a LiveCD pendrive, I can fully access my HDD. I tried to run boot-repair (booting both in EFI and Legacy modes), but I get
> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Here is a pastebin of the information collected by boot-repair
[URL="http://paste.ubuntu.com/8436326/"]http://paste.ubuntu.com/8436326/
[/URL]
Here is the output for efiboot
```
$ sudo efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0006,0005,0001,0002
Boot0001* Hard Drive     BIOS(2,0,00)AMGOAMNO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.0.0.B.N.5.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.3.C.1.F.1.4.7.8.4.2......AMBOAMNO........y.K.i.n.g.s.t.o.n.D.a.t.a.T.r.a.v.e.l.e.r. .2...0....................A.............................F..Gd-.;.A..MQ..L.K.i.n.g.s.t.o.n.D.a.t.a.T.r.a.v.e.l.e.r. .2...0......AMBO
Boot0002* CD/DVD Drive     BIOS(3,0,00)AMGOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.K.0.8.6.D.E.0.A.9.0.3.1. . . . . . ......AMBO
Boot0005* ubuntu    HD(1,800,100000,179d6d2d-e4df-0946-9507-286ed79ab1fb)File(EFI\Ubuntu\grubx64.efi)
Boot0006* UEFI: KingstonDataTraveler 2.0    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(5,0)HD(1,3e,3d7442,000984e1)AMBO

```

I have also tried fsck, testdisk, and read many post on the net... with elusive luck. I'd very much appreciate a good advice...

---

### Post by oldfred on 2014-09-27
You have an UEFI install with gpt partitioning. You should just be able to go into UEFI can choose ubuntu entry to boot. But you must have UEFI on and CSM/BIOS/Legacy off. Some have a setting for both. And a few vendor systems only want to boot Windows in UEFI mode and we have to create work arounds.

You must have booted Boot-Repair in BIOS mode and it then is suggesting to convert to BIOS boot. In BIOS boot mode you need a bios_grub unformatted partition of 1 or 2MB for grub to install correctly. Boot-Repair does not auto create that for you. But you should not need it. Just boot in UEFI mode.

It looks like you are using a device like /dev/sda6 to try to mount a data partition, but now swap is sda6 when it was originally sda3 per your fstab. And your data mount is malformed.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

Your entry should look more like this, except with your UUID and mount:

 fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

And it may be taking so long as it is trying to find a data partition where one does not exist, or fstab is not correct.

---

### Post by marce2 on 2014-10-03
Oldfred, thank you very much for your kind reply.
  
This problem is happening at my parents Desktop, and I have not been able to visit them since my last post.
  
I agree that the disk has an UEFI install with GPT partitioning. On the other hand, I am  pretty sure I have selected UEFI boot from the firmware at startup. What I  don't know is whether it is possible that ubuntu was installed on the pendrive so  that it cannot be boot in UEFI mode. Can we infer any information from  the efiboot line
  > Boot0006* UEFI: KingstonDataTraveler 2.0    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(5,0)HD(1,3e,3d7442,000984e1)AMBO?

I am very impressed that you spotted that sda6 has taken the place of  sda3 (and bewildered as to how it happened). I will try to correct the  fstab table, and see if it brings the disk to boot again.
  
Again, I am very grateful for your help.

---

### Post by oldfred on 2014-10-03
The Ubuntu installer is both UEFI and BIOS boot.

And UEFI has its own NVRAM so it remembers previous boots. In fact you have to manually erase them to delete old ones. So that it remembers your boot from the flash drive should be normal, but I notice my new system does not include that entry.

I think it is both the swap & data partition entries in fstab that are causing issues.

---

### Post by Dennis N on 2014-10-04
The appearance of the KIngston Data Traveler in the UEFI Boot Manager should be only temporary until you can remove it - it is then not detected at the next startup and no longer shown. That is my experience.

---

### Post by marce2 on 2014-10-05
[COLOR=#000][FONT=HelveticaNeue][FONT=arial][SIZE=3]Oldfred, thanks again for your help.[/SIZE][SIZE=3]
[/SIZE][/FONT]
[COLOR=#000000][FONT=HelveticaNeue][FONT=arial][SIZE=3]I have made sure I selected UEFI boot at startup (both for pendrive and HDD), and I have commented out from fstab the line[/SIZE][/FONT]
[/FONT][/COLOR]> [COLOR=#000000][FONT=HelveticaNeue][FONT=arial][SIZE=3]/dev/sda6   /home/DATA   ext4   user[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue][FONT=arial][SIZE=3]
I have tried again boot-repair, with similar results. Here is the new [http://paste.ubuntu.com/8496889/](http://paste.ubuntu.com/8496889/)[/SIZE][/FONT][URL="http://paste.ubuntu.com/8496889/"]
[/URL][/FONT][/COLOR][COLOR=#000000][FONT=HelveticaNeue][FONT=arial]
[/FONT][COLOR=#000000][FONT=HelveticaNeue][FONT=arial][SIZE=3]I don't see any problem with my swap partition now (it appears to be  consistently in sda6).
[/SIZE][/FONT][/FONT][/COLOR]
[FONT=arial][SIZE=3]It has caught my attention that even if I have booted in EFI mode:[/SIZE][/FONT][/FONT][/COLOR]

[LIST]
[*][FONT=arial]line 767:[/FONT][FONT=arial]
=================== UEFI/Legacy mode:[/FONT][FONT=arial]
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.[/FONT] 
[*][FONT=arial]I still get the same error from boot-repair:[/FONT][FONT=arial]
line 965:[/FONT][FONT=arial]
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.[/FONT] 
[*][FONT=arial]line 967:
[/FONT][FONT=arial]The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk,  boot flag).
Do you want to continue?[/FONT] 
[/LIST]
[COLOR=#000000][FONT=HelveticaNeue]
The "unusual EFI" line may be signaling some bug?

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0005,0006,0001,0002
Boot0001* Hard Drive     BIOS(2,0,00)AMGOAMNO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.0.0.B.N.5.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.3.C.1.F.1.4.7.8.4.2......AMBOAMNO........y.K.i.n.g.s.t.o.n.D.a.t.a.T.r.a.v.e.l.e.r. .2...0....................A.............................F..Gd-.;.A..MQ..L.K.i.n.g.s.t.o.n.D.a.t.a.T.r.a.v.e.l.e.r. .2...0......AMBO
Boot0002* CD/DVD Drive     BIOS(3,0,00)AMGOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.K.0.8.6.D.E.0.A.9.0.3.1. . . . . . ......AMBO
Boot0005* ubuntu    HD(1,800,100000,179d6d2d-e4df-0946-9507-286ed79ab1fb)File(EFI\Ubuntu\grubx64.efi)
Boot0006* UEFI: KingstonDataTraveler 2.0    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(6,0)HD(1,3e,3d7442,000984e1)AMBO

```
Does efibootmgr output mean that fstab is corrupted?
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by marce2 on 2014-10-05
Thanks Dennis N. I have tried to boot after removing the pendrive, and still get the error of the title.

---

### Post by oldfred on 2014-10-05
Boot-Repair is trying to install grub in BIOS boot mode as that requires you to with gparted create a 1 or 2MB bios_grub partition.

But it is saying it cannot now find an efi partition? That normally is one of the first partitions and is FAT32 formatted. In gparted you use boot flag to identify it as the efi partition, but that is not the same boot flag as used in BIOS/MBR systems. But you could not boot in secure boot mode without an efi partition. With secure boot on, neither UEFI (without secure boot) nor CSM/BIOS will not work.

But Boot-Repair is also saying you still have secure boot on. If you installed Ubuntu in UEFI mode without secure boot, UEFI will not let it boot. 
You must turn off fast boot in Windows and usually better to turn off secure boot.

Boot-Repair flags a lot of UEFI as unusual. And most of those only boot Windows and need various work arounds to get Ubuntu to boot.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by marce2 on 2014-10-05
[COLOR=#000000][FONT=HelveticaNeue]Thanks oldfred.[/FONT][/COLOR][COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]Since I see this [http://pix.toile-libre.org/upload/original/1347445084.png](http://pix.toile-libre.org/upload/original/1347445084.png) at startup, I am booting in EFI mode.
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]The  EFI partition is on sda1, and is FAT32. Windows is not installed in  this machine and never has (there is a partition that I have left for this  purpose, but have never used it). Boot-repair says I have secure boot on.  How can I tell if I have installed Ubuntu in UEFI mode without secure  boot?[/FONT][/COLOR]

[COLOR=#000000][FONT=HelveticaNeue]How  can I correct  it? Before removing my secondary failing HDD, the system  was working fine, so I imagine that UEFI should not be that  problematic...
[/FONT][/COLOR]
What options do I have now? One option is trying to fresh install Ubuntu in sda4 (labelled WD_1TB_ubuntu2_7), an empty partition at the moment, and then see if I can make sda2 (labelled WD_1TB_ubuntu1_7) to boot again. Can you think of a better approach?

---

### Post by oldfred on 2014-10-05
If you have one of those UEFI that only boot Windows and you do not have Windows we create an efi folder with Microsoft and copy grub or shim for secure boot into that folder and rename it to bootmfgw.efi. UEFI thinks it boots Window, but just boots grub. Since shim uses the same signing key as Microsoft you should be able to boot in secure boot mode also.

You probably have to go into UEFI and turn off secure boot. Some have you even create your own password (never lose that) to let you get into the settings to turn off secure boot. Others hide it in a sub-menu. On my motherboard I have to change default from Windows UEFI to other and then go into CSM settings to turn on UEFI. Go figure that you have to go into BIOS settings to change UEFI mode.

         Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)
    From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/EFI

       use ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi

---

### Post by marce2 on 2014-10-05
I presume this UEFI not only boots in Windows, since before removing my failing secondary HDD, it was working fine. Right?

I will now try to go into UEFI an turn secure boot off.

---

### Post by oldfred on 2014-10-05
Also if you had another drive with UEFI booting and an efi partition, you may not have created an efi partition on the second drive. And that may be then why Boot-Repair and missing partition errors keep appearing. Always best to have an efi partition and gpt partitioning type on every drive if booting in UEFI mode from any drive.

Post this:
sudo parted -l

---

### Post by marce2 on 2014-10-05
Oldfred: thank you so much for helping me solve this problem.

Here is what worked:
[LIST=1]
[*]Clicked on "advanced" in the Asus setup firmware, and clicked on "Boot". [Image 4] 
[*]Clicked on Option ROM Messages and selected Keep Current (not sure if this step was needed). [Image 3] 
[*]Dissabled Fast boot. [Image 2] 
[*]Clicked on "Secure Boot". 
[*]Clicked on OS Type and selected "Other OS" (instead of Windows). [Image 1] 
[/LIST]

And voila!

Puzzled: I have no idea how "OS Type" became "Windows", I have never seen that screen before. It happened exactly after I removed the failing secondary HDD. Any thoughts?

I'd like to mark this thread as solved, but (I am ashamed to admit) I don't find the "thread tool" :(

---

### Post by oldfred on 2014-10-05
I wish I had known it was an Asus. That is exactly what I had to go thru. :)

I am still experimenting with UEFI/BIOS settings. But have a list of changes I did. 
I document my settings as older system always totally reset to defaults after a BIOS update. With UEFI, it has NVRAM and should save some or most settings on an update, but I am not sure.

Above first post is the thread tools.

---

### Post by marce2 on 2014-10-05
I am sorry I did not pay much attention to it, I realized it was an Asus when I was taking the pictures to document the experiments...

---

