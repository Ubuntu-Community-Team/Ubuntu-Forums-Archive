---
title: "install ubuntu on virtualbox with EFI"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by jagojago on 2013-09-03
Hi

After installing Ubuntu 13.10 on a virtualbox using EFI boot option, the install process finish but after the first reboot it's impossible to go forward.

Already try with rEFInd and boot-repair but nothing changes

Output from boot (some char may be not real) (last line)
[ 3.707153] pi.lx4_smbus0000:00:07.0:SMBus base address uninitialized - upgrade BIOS or use force_addr=Oxaddr

Any ideas?

Tia

jago

-----
1.623028) rtc.cnos r-tc.rmos: setting system clock to 2013-09-03 15:12:29 UTC (1378221149)
1.623780) BIOS EDD facility vO.16 2004-Jun-25, 0 devices found
1.625450) EDD information not available.
1.629108] Freeing unused kernel memory: 1364K (ffffffff81d12000 - ffffffff81e67000)
1.629602] l-Irite protect ing the kernel read-only data: 12288k
1.632496] Freeing unused kernel memory: 992K (ffff880004708000 - ffff880004800000)
[ 1.634694] Freeing unused kernel memory: 808K (ffff880004b36000 - ffff880004COOOOO)
oading, please wait ...
[ 1.6484081 systemd-udevd[92]: starting version 204
[ 1.6667141 el000: module verification failed: signature and/or required key missing - tainting kernel
egin: Loading essential drivers ... done.
egin: Running /scripts/init-premount ... done.
egin: I·\ountingroot file system ... Begin: Running Iscripts/local-top ... done.
[ 1.690718] ahci: SSS flag set, parallel bus scan disabled
[ 1.695787] ahci OOOO:OO:Od.O: AHCI 0001.0100 32 slots 2 ports 3 Gbps Ox3 impl SATA mode
[ 1.696544] ahci OOOO:OO:Od.O: flags: 64bit ncq stag only ccc
[ 1.709085] e 1000: Inte 1(R) PRO/lOOO NetUJorkDr iver - vers ion 7.3.21-k8-NAP I
[ 1.712288] e1000: Copyright (c) 1999-2006 Intel Corporation.
[ 1.720029] scsi2 : ahci
[ 1.724148] scsi3 : ahci
[ 1.724905] ata3: SATA max UDHA/133 abar m81921l!0x84424000port Ox84424100 irq 21
[ 1.725565] ata4: SATA max UDHA/133 abar m81921l!0x84424000port Ox84424180 irq 21
[ 2.170982] e1000 0000:00:03.0 etho: (PCI:33HHz:32-bit) 08:00:27:32:f3:b8
[ 2.174330] e1000 0000:00:03.0 etno: Intel(R) PRO/lOOO NetrrorkConnection
[ 2.241410J ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2.2544741 ata3.00: ATA-6: vaox HARDDISK, i.o, max UDHA/133
[ 2.257281] ata3.00: 16777216 sectors, multi 128: LBM8 NCQ (depth 31/32)
[ 2.263846] ata3.00: configured for UDHA/133
[ 2.274077] scsi 2:0:0:0: Direct-Access ATA VBOX HARDDISK 1.0 PQ: 0 ANSI: 5
[ 2.277352] sd 2:0:0:0: [sda] 16777216 512-byte logical blocks: (8.58 G8/8.00 GIB)
[ 2.279723] sd 2:0:0:0: [sda] Write Protect is off
[ 2.283629] sd 2:0:0:0: Attached scsi generiC sgl type 0
[ 2.286084] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.292432] sda: sdal sda2 sda3
[ 2.293819] sd 2:0:0:0: [sda] Attached SCSI disk
[ 2.589518] SUJitchedto clocksource tsc
[ 2.602383] ata4: SATA link dOUJn (SStatus 0 SControl 300)
Begin: Running /scripts/local-premount ... done.
[ 2.696187] EXT4-fs (sda2l: INFO: recovery required on readonly filesystem
[ 2.696820] EXT4-fs (sda2l: write access will be enabled during recovery
[ 2.712753J EXT4-fs (sda2): recovery complete
[ 2.7165631 EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running Iscripts/init-bottom ... done.
[ 3.282452) Adding 2096124k sUJapon Idev/sda3. Priorit~:-1 extents:1 across:2096124k FS
[ 3.707153] pi.lx4_smbus0000:00:07.0:SMBus base address uninitialized - upgrade BIOS or use force_addr=Oxaddr

---

### Post by godloveme_zhu on 2013-11-17
Hi,

I'm having the same issue here. And the same error message. I've tried tweaked settings for the virtual machine but they are all failing.

In the meanwhile, I noticed although the GUI or desktop cannot show up the console does come out and is running happily.

Anyone knows how to solve this?

Or shall I revert to some earlier version to try my luck?

Thanks,
Julian

---

### Post by godloveme_zhu on 2013-11-18
Hi,

I've managed to start up the desktop now though the resolution is still very low only at 1024x768 at the moment.

The error message regarding the bus stuff is irrelevant. So forget about it.

The only issue matters here is regarding the video driver. Not sure if it is a Ubuntu bug or Oracle VB's issue. Nevertheless, in RedHats they have similar issues before and they kindly got it fixed years ago. See here "[https://bugzilla.redhat.com/show_bug.cgi?id=546166](https://bugzilla.redhat.com/show_bug.cgi?id=546166)" and I'm really surprised that Ubuntu just has ignored this for so long.

So if you are just like me doing some UEFI test and can tolerate the low 1024 * 768 resolution then here is the remedy.
1. Install Ubuntu under UEFI as normal and when it finishes you will find you cannot boot to the desktop but only a console. Note sometimes the focus will not stop at the VT1 and so you need to manually switch by Crl+Alt+F1 to the virtual terminal.

2. Run "Sudo X -configure" and copy the resulting file into your "/etc/X11" folder using the command "sudo cp xorg.conf.new /etc/X11/xorg.conf" and then modify it.

3. Basically you need to add one line into that file but I'm not sure if it really makes sense. I guess it might also be fine without that line. Nevertheless let's just add it. What need to be edited in xorg.conf is to add a line for "Modes" in the Display subsection of the Screen section at the end of config file. 
        > SubSection "Display"
                Viewport   0 0
                Depth     24
                _**Modes   "1024x768"**_
        EndSubSection
Note: There're many "Screens" in the file and you need to change the one whose Device section is fbdev.
> Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # <str>
        #Option     "fbdev"                     # <str>
        #Option     "debug"                     # [<bool>]
[U][B]        Identifier  "Card0"
        Driver      "fbdev"
[/B][/U]        VendorName  "InnoTek Systemberatung GmbH"
        BoardName   "VirtualBox Graphics Adapter"
        BusID       "PCI:0:2:0"
EndSection
4. Then, start the graphical server with this command:
> 
  startx 
[LEFT]and at this stage you should see your desktop is back.

5. The final step is to make VB automatically start the Unbuntu system. Unfortunately, Oracle's UEFI implementation has lots quirks and one of the most annoying one is it has a goldern fish's memory on the NVRAM. Whatever you assigned as a new value to the vars in NVRAM once virtual machine is turned off or just restarted all your values are gone. So I'm really wondering if that is the case, how can it be called NVRAM (non-volatile RAM) then?

This is just the reason why so many people after installing Ubuntu under UEFI in VB only to get a shell when re-start their machines.

Luckily, this issue is quite easy to fix and my approach here is a one-off approach so that next time when you boot your machine you will get your desktop in a straight way.

To do it, simply follow the steps here. Note you need "sudo" to do all of it.
5.1
> cd /boot/efi/EFI
          mkdir -p Microsoft/BOOT
          echo "1" > Microsoft/BOOT/bootmgfw.efi
    5.2 Install Ubuntu's "Boot-repair" tool (I'm sure you know how to get it) and then run it.

    5.3 Choose "Advanced Options" -> "Main Options" and make sure "Use the Standard EFI file" and the following "Backup windows EFI file" is enabled.

    5.4 If you want quick fix then go to "Other options" and disable all the options there and then apply.

At this moment you should find when restarting your machine the familiar menu will come up and when you choose Ubuntu it will take you all the way through to the desktop.

Hope this can help people still seeking a solution to the issue.

Regards,
Julian[/LEFT]

---

### Post by godloveme_zhu on 2013-11-18
Hi,

Just add some points.

1. Ubuntu 12.04 LTS is facing the same issue here and I guess it is also the case for 12.10.
2. The final trick I introduced requires you haven't install Windows under UEFI in VB but I guess that is true for all of us since Oracle has mentioned its UEFI implementation does not support to install Windows at the moment.
3. Regarding this trick what is behind the scene is this. Upon start-up, because there are no boot files registered in VB's NVRAM (if there are any a virtual machine restart or shutdown will clear all of these) the system falls back default boot option, i.e. DVD, harddisk, and so on. If hard disk is the only media to be found, the system will go to the ESP partition to look for "/EFI/BOOT/boot<arch>.efi" (<arch> for 64bit machine is "x64") and run it. The unfortunate thing is Ubuntu does not generate this file by default as it assumes it can always successfully register the boot file with the system which is false in Oracle's virtual machine. Hence, what the role that boot-repair tool plays here is to help generate that "boot<arch>.efi" file for us. Yet I find in Ubuntu 12.04 LTS, unless you have Microsoft's boot file in place ("Microsoft/BOOT/bootmgfw.efi") the repair tool will refuse to generate that desired file. And so what we need to do is blindly generate a dummy file here to make the tool believe we have "installed" Windows and need to fully repair the whole thing.

Hope this clarifies things a bit.

Regards,
Julian

---

### Post by godloveme_zhu on 2013-11-18
Hi,

I'd partially take back what I said earlier.

The good news is that I now can make my Ubuntu 12.04 LTS running happily under the UEFI mode with 1920x1080 resolution. Cool!

The only thing which I may take back is what I said about the final tricky point. I thought the "EFI\BOOT\boot<arch>.efi" file will call the "EFI\ubuntu\shimx64.efi" and then trigger the Ubuntu boot menu to show up. But that seems not right.

Nevertheless, to fix it is still very easy. You just simply copy whatever is in the "EFI\ubuntu" folder to the "EFI\BOOT" folder. Note by default "EFI\BOOT" folder does not exist and so you need to make it by yourself. Also note you need to do this by "sudo" command. After the copy rename "shimx64.efi" to "boot<arch>.efi" and it will do the magic.

Regarding the resolution issue. I just deleted the X configure file we generated and copied (to "/etc/X11" folder) as I mentioned in my previous post. And then I installed the VB guest addition and restart and then magic happens. Based on this, I guess the easiest solution to the original issue should be simply insert the guest addition CD and install the guest addition using the console. But that's just my assumption since now I have the Ubuntu running happily I don't bother to try that out.

Regards,
Julian

---

### Post by Nick_NS on 2014-08-21
Another option I found over on the [VirtualBox forums]("https://forums.virtualbox.org/viewtopic.php?f=6&t=63225") involves using the built-in startup.nsh functionality to allow VirtualBox to load grubx64.efi (or any other boot option) without the need for any workarounds. There are two options to make the file.

From the VirtualBox EFI shell:
[LIST=1]
[*]Wait for the EFI shell to leave you at the terminal.
[*]Type: edit startup.nsh
[*]Type the path to your desired .efi file. Typically: fs0:/EFI/ubuntu/grubx64.efi
[*]Ctrl+S to save.
[*]Enter to confirm.
[*]Ctrl+Q to exit back to shell.
[*]Reboot the VM. It will still display the EFI shell but will load Grub automatically.
[*]
[/LIST]

or from within the Guest OS:
[LIST=1]
[*]Launch your favorite editor with sudo privileges.
[*]Type the EFI shell path to your desired .efi file. Typically: fs0:/EFI/ubuntu/grubx64.efi
[*]Save the file as /boot/efi/startup.nsh
[*]Reboot the VM. It will still display the EFI shell but will load Grub automatically.
[*]
[/LIST]

Hope this helps.

Credit to Perryg and AnrDaemon over at the VirtualBox forums.

---

### Post by PJSingh5000 on 2015-03-15
Small corrrection to Nick_NS's excellent solution:  the forward-slashes "/" should be back-slashes "\", as follows.

From the VirtualBox EFI shell:

[LIST=1]
[*] Wait for the EFI shell to leave you at the terminal.
[*] Type: edit startup.nsh
[*] Type the path to your desired .efi file. Typically: **fs0:\EFI\ubuntu\grubx64.efi**
[*] Ctrl+S to save.
[*] Enter to confirm.
[*] Ctrl+Q to exit back to shell.
[*] Reboot the VM. It will still display the EFI shell but will load Grub automatically.
[/LIST]

(FYI, this works on VirtualBox 4.3.18 and Ubuntu Gnone 4.10 x64).

---

