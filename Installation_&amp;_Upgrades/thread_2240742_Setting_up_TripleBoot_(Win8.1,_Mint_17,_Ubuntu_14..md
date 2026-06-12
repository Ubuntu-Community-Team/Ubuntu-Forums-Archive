---
title: "Setting up TripleBoot (Win8.1, Mint 17, Ubuntu 14.04) on a UEFI-based system,w-rEFInd"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by eRCaGuy on 2014-08-21
**SOLVED****...16~20 hrs. of work later.....ON **[B]23 Aug. 2014, 10:35 PM

[SIZE=5]SEE POST 8 BELOW FOR "[/SIZE][/B][SIZE=5]**MY STEPS TO GET A GOOD, FUNCTIONAL TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM:"**[/SIZE]

============================================================================================================================

I just ran Boot Repair, but m[FONT=arial]y boot still fails.  

Here's the scoop:
I have a brand new laptop ([Toshiba Satellite shown here]("http://www.toshiba.com/us/computers/laptops/satellite/C50/C55T-B5109")[/FONT][FONT=arial]) with UEFI.  First thing I did was install Linux Mint 17 ([/FONT][http://linuxmint.com/rel_qiana_cinnamon.php](http://linuxmint.com/rel_qiana_cinnamon.php)[FONT=arial]) to have a dual boot with Windows 8, per these instructions here ([/FONT][http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/)[FONT=arial]).  It worked perfectly.  My efi partition is sda2, so thats where I had the installation place the bootloader.[/FONT][FONT=arial]Please note that per the upper link above, "[COLOR=#333333][FONT=Trebuchet MS]Linux Mint 17 places its boot files in /boot/efi/EFI/ubuntu to work around [/FONT][/COLOR][this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417")"[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I wanted Ubuntu too, so that I would then have a triple-boot option (Win 8, Mint, Ubuntu).  I installed Ubuntu 14.04 LTS and my computer would no longer show GRUB when booting.  **Instead, it would boot straight into Windows 8.  **[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Please note that I used the latest version of unetbootin to make my USB installation drives for both Linux and Ubuntu.  I downloaded the .iso files manually, however, from the respective sites.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]After Ubuntu messing up my GRUB, I booted onto my Linux Mint 17 usb and typed the commands shown here ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) to run Boot Repair. I did the "recommended repair" option.  I got a notice saying "An error occurred during the repair."  I rebooted, and it again went straight into Windows 8.  No GRUB bootloader.  Boot Repair didn't work.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]My URL from the Boot Repair is here: [http://paste2.org/51pk9Cg3](http://paste2.org/51pk9Cg3)

Anyone know how to repair my GRUB so I can choose Win8, Ubuntu, or Linux during the boot-up?  Again, currently it boots straight into Win 8.

I have disabled "secure boot" and Win 8 "fast startup" FYI prior to even doing the Linux Mint install.

Thanks for any help![/FONT]

---

### Post by oldfred on 2014-08-22
Did you also upgrade to Windows 8.1? It seems to automatically reset itself to be first or only boot entry in UEFI. And that often resets to turn on secure boot or fastboot causing issues. You must make sure those are correct regularly.

Did you have Mint booting in UEFI mode?
Normally each system installs its own folder.
But if it usedubuntu then the new install overwrote your Mint boot files in the ubuntu folder.

Perhaps the Mint version of grub works better than the Ubuntu version?

Some systems only boot Windows as they have modified UEFI. And newest Windows 8.1 seems to always reset UEFI to make it first. Windows 8 seemed to only reset it on maintenance.

Did you back up the efi partition before installing Ubuntu? Or do you have the Mint grub/efi boot files?

The Mint entry in grub menu is a BIOS boot entry that will not work.

I thought the newest grub had the fixes for the name or the bug report you link to. Or is Mint using an older version of grub?
I might try creating a /EFI/mint folder in efi partition and installing Mint's boot files into it. And use efibootmgr to add a mint entry to UEFI.

Can you boot ubuntu entry from UEFI menu or one time boot key often f12, but varies?

BootInfo report does not show the grub.cfg in the efi partition. It is just a 3 line entry to set root and configfile link to the real grub in Ubuntu. Not sure if you changed that to your Mint install whether or would work or if grub version is not the same it would not work?

       # from liveDVD or flash and use efibootmgr
modprobe efivars
sudo efibootmgr -v

            [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

Another thought:
backup ubuntu folder in efi partiton and use Boot-Repair to reinstall Mint's grub. You should be able to boot in UEFI mode and in Boot-Repair's advanced mode choose Mint and choose to install to sda.

---

### Post by eRCaGuy on 2014-08-23
hey thanks for the reply!  I appreciate it a lot.  I've been trying a ton of things and am trying to track down how to make GRUB show up again during normal boot.   I was, interestingly-enough, able to get both Mint and Ubuntu to boot if I *manually* typed up a whole bunch of stuff from the grub.cfg file in the /boot/grub folder.  This, however, is certainly NOT practical to do every boot, as it takes several minutes to type it all in.  Here's how I managed that:

1) Boot onto live USB (ex: Mint install USB drive).
2) Mount my partitions where I have Mint and Ubuntu installed.  Open this file: /boot/grub/grub.cfg.  Photograph the boot parameters I need.  Ex: in the file, for my Mint install, I needed this part:
---------------------------------------------------
menuentry 'Linux Mint 17 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda7)' --class ubuntu --class gnu-linux --class gnu --class os {
    [COLOR=#0000ff]recordfail
    gfxmode $linux_gfx_mode[/COLOR][COLOR=#ff0000]
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'[/COLOR]
    if [ x$feature_platform_search_hint = xy ]; then
      [COLOR=#ff0000]search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ad2ac0d1-a653-4e72-b324-fcd3d8b9565d[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root ad2ac0d1-a653-4e72-b324-fcd3d8b9565d
    fi
    [COLOR=#ff0000]linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ad2ac0d1-a653-4e72-b324-fcd3d8b9565d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic[/COLOR]
}
---------------------------------------------------
3) Photograph the above section on your smart phone or camera or whatever, so you can reference it later (key lines are in red)
4) Restart, and use proper function key (F12 for me) to enter boot menu and boot again onto your Live USB.
5) This time, once Grub comes up, press "c" to enter grub command line
6) Type in all of the colored sections above, one line at a time, and press enter after each line.  The blue lines don't work, and it will tell you the command doesn't exist. It doesn't matter though.  The red lines are important.
7) Once you've typed all of the above lines (note: they will be specific to your install), type "boot"
8) It boots up perfectly onto your install.  

Note: this works whether or not you are having GRUB problems.  Give it a shot.  It seems to work no matter what.  

Why do this?  It allows  you to boot into your OS even when GRUB is broken and not coming up automatically for you.

How did it solve my problem?  So far, it hasn't.  I booted in like that and tried doing a GRUB reinstall per these instructions ([http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)), (using the command here:

----------------------
apt-get install --reinstall grub-efi-amd64

or alternatively: 
apt-get install --reinstall grub-efi
update-grub

should the above give you a grub, but not a bootable one
----------------------

) but when I rebooted, I got no GRUB once again, and Windows 8.1 simply started up, as it's been doing.

To answer some of your other questions: I've been running Win 8.1 this whole time.  All of my "windows 8" references above are actually 8.1.  I haven't done any updates.  I verified that SecureBoot is still off and windows "fast startup" is still off.

I did NOT back up my EFI partition prior to installing Ubuntu. (I didn't know how at the time, so I didn't.  I know how to now though).

It *does* appear that Mint and Ubuntu use the same folder within the EFI partition, so I think Ubuntu did overwrite the EFI stuff for Mint.

I'm interested in your last suggestion: "Another thought:
backup ubuntu folder in efi partiton and use Boot-Repair to reinstall  Mint's grub. You should be able to boot in UEFI mode and in  Boot-Repair's advanced mode choose Mint and choose to install to sda."
[B]
But why sda?  Why not sda2, which is my efi partition???[/B]

PS. I also just reinstalled Mint, and that didn't fix my missing GRUB either.  So, I just reformatted my Mint and Ubuntu partitions and will next reinstall Mint yet again, this time with Ubuntu being totally wiped off, to see if that works now. This stinks. :)

---

### Post by eRCaGuy on 2014-08-23
oldfred, your links to efibootmgr have been very useful.  After many more Mint re-installs, to no avail, and then a strange success (to at least get back to my Mint/Win 8 dual boot), I am beginning to see the problem.

It appears that my Toshiba C55T-B5109 laptop has a really minimal UEFI boot manager.  It is so minimal, that I do not even have a menu to choose which UEFI OS I want to boot.  Rather, my menu permits me to choose the drive source ONLY (ex: Hard drive, USB drive (one choice only), optical disk drive).  The only two special keys that I have discovered during boot are F2, to enter the "BIOS" (UEFI settings), and F12, to open the boot menu (which drive do you want to boot from, but NOT which OS).  

So, after many more Mint installs, and a bunch of reading, it dawned on me that my Toshiba firmware had set Windows 8.1 as the default bootloader on my hard drive, and that GRUB was in fact installed correctly and present, but just not launching.  Since there is no UEFI boot menu for me to select the OS, nor any settings in the "BIOS" that I could change to tell it to load GRUB instead of the Windows Bootloader,[SIZE=3][SIZE=2]I thought that if I fiddled with other UEFI-related settings, it might force a reset.  

So, I used F2 to enter the "BIOS" settings, and I turned Secure Boot  back *on*.  I then went back in and turned Secure Boot back *off*.   Boom, GRUB loaded on the next restart.  By this time, however, I had  removed Mint and Ubuntu, so it was just the GRUB command prompt.  I  reinstalled Mint and it worked!  Turns out that for my Toshiba laptop,  with a crappy UEFI firmware/"BIOS", the settings just don't exist for me  to properly select which OS is default, so toggling the "Secure Boot"  setting mystically did the trick, by apparently also forcing a change to  the default boot device.

Note: for some odd reason, efibootmgr in linux also does not  allow me to permanently change the UEFI boot order.  Even if I use the  -o option (described here: [http://linux.dell.com/files/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt](http://linux.dell.com/files/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt)),  it does not *permanently* change the boot order.  Rather, it will  temporarily change it until I restart, then it goes back to whatever it  was.  the -n option *does* work, interestingly enough, but *not* the -o  option.  Can you explain this?[/SIZE][/SIZE]

Here are some links that I have found very helpful in understanding this EFI stuff:
1 - [http://nwrickert2.wordpress.com/2013/05/13/notes-on-uefi-windows-and-linux/](http://nwrickert2.wordpress.com/2013/05/13/notes-on-uefi-windows-and-linux/) -explains why my GRUB kept **appearing** to be deleted! - he alsoexplains a whole slew of UEFI boot bugs & fixes, including stuffI needed for my boot problems!
2 - [http://reboot.pro/topic/19363-efibootmgr-not-changing-boot-order-permanently/](http://reboot.pro/topic/19363-efibootmgr-not-changing-boot-order-permanently/)- explains that HP seems to hard-code which efi OS is loaded, orsomething like that....similar to what my Toshiba is doing
3 - [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) - rEFInd boot manager - something I plan to install from Linux to see how well it works, since I cannot get efibootmgr to permanently edit my UEFI boot order, via the -o command :(

Additional note: it is possible to enter a special UEFI boot device screen upon startup, by going through a special process in Windows 8.1.  See here: [http://www.tomshardware.com/faq/id-1877214/access-advanced-boot-options-windows.html](http://www.tomshardware.com/faq/id-1877214/access-advanced-boot-options-windows.html)
-Select the "Use a Device" option, and I can see "ubuntu" [which is actually Mint] as one of the startup options.  When I choose it, it loads my GRUB 2 loader, from which I can select Ubuntu *or* Windows!  However, this is impractical to boot into Windows every time I want to load the GRUB.  Pretty dumb.

---

### Post by eRCaGuy on 2014-08-23
IMPORTANT DISTINCTION TO MAKE:

When I had my problem after installing Ubuntu, I thought it was my GRUB2 boot*loader* that had the issue. I was wrong. Rather, it was my Toshiba boot *manager* with the issue.  I just installed rEFInd, and it works great!  It allows me to choose the boot *manager*, or device (OS), as I see fit, during startup.

Here's how the two differ, from what I gather:
[SIZE=3][B]
Boot Manager vs Bootloader:[/B][/SIZE]

**Boot Manager -** the closest thing to the computer firmware (UEFI/BIOS); it chooses which "device" or bootloader to directly load. 

**Bootloader **- the program called by the Boot Manager; it chooses which kernel & operating system to load.  Oftentimes a bootloader has no menu, but just starts something up, so people tend to confuse a boot manager and bootloader. ex: the Windows Boot Manager calls the Windows bootloader, which has no selection screen, so when Windows opens you don't even realize a bootloader was called.  Compare this to: you use the rEFInd Boot Manager to load the GRUB2 bootloader, which you then select to load Windows.  In both cases, the sequence was Boot Manager --> Bootloader, it's just that this sequence wasn't obvious in the first case, but it was very obvious in the 2nd case.

---

### Post by eRCaGuy on 2014-08-23
PS. install the rEFInd Boot Manager as follows, in a Linux shell/terminal:

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
apt-get install refind

source: 
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
and [http://www.rodsbooks.com/refind/installing.html#packagefile](http://www.rodsbooks.com/refind/installing.html#packagefile)

---

### Post by oldfred on 2014-08-23
I have heard several other say rEFInd works for limited UEFI systems. One or two still had issues.

When installing grub you specify a drive, With BIOS it installs to the MBR, With UEFI it installs to the efi partition.When you install grub to a partition it really goes into the PBR or partition boot sector. I think with UEFI it does not matter what you specify it will install correctly to the efi partition.

With Debian based systems that have links to the most current kernel you you can often boot with just a few lines. UEFI may need a couple more.

Sometimes with UEFI or BIOS this works if you specify correct partition to find actual grub.cfg. Change gpt to msdos if BIOS install. This works if grub menu ok.
 configfile (hd0,gpt8)/boot/grub/grub.cfg

      
 Not booting in UEFI mode This then should work if kernel & initrd.img are ok.
Manual boot works, sometimes additional insmod commands are required to load extra grub drivers:
set root=(hd0,gpt8)
set prefix=(hd0,gpt8)/boot/grub
insmod linux
linux /vmlinuz root=/dev/sda8 ro
initrd /initrd.img
boot

---

### Post by eRCaGuy on 2014-08-23
oldfred, thanks for the info!  I have spent ~20 hrs. (with 12 of that today) on making my system triple boot (Win8.1, Linux Mint 17, & Ubuntu 14.04), with about 16 of that being due to UEFI problems on my system, so to save others TONS of time, I'm going to explain how to get this triple boot system, based on my experiences.  I'd like to mention that for my system, the rEFInd program works great, and is the *only* solution I found, period, that met my needs.  I haven't seen any bugs, and I just triple checked that all my OS's are booting properly.

[B]I know you have a lot of influence as an administrator, so if you see any cases where rEFInd could do someone some good, I'd encourage you to make the recommendation.  I would use this as the criteria to decide if they should go that route or not.
[SIZE=4]Do I need a 3rd party UEFI Boot Manager, such as rEFInd?[/SIZE][/B]
1) does their firmware already have a UEFI Boot Manager, which allows selecting an OS/device to boot, NOT just a drive to boot from? (mine does not)
2) does the built-in Linux "sudo efibootmgr" application work?  Can you use it to permanently set a new UEFI boot order? (my PC cannot) Or does the PC's firmware revert the UEFI boot order to some hard-coded value after each reboot, regardless of the efibootmgr's commands? (this is what mine does: so ultimately I cannot use efibootmgr to set the UEFI boot order).
3) If neither of the above two methods work to manually set a UEFI boot order, I very highly recommend the 3rd-party, open source rEFInd Boot Manager for UEFI systems. (it works perfectly for me!)

[SIZE=4]**MY STEPS TO GET A GOOD, FUNCTIONAL TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM:**[/SIZE]

My laptop is *brand new* (purchased July 2014).  It is a Toshiba satellite C55T-B5109 (link in first post).
-This is important, as different brands and models have different UEFI firmwares....some of which kind of suck (like mine)....thereby requiring a 3rd party UEFI Boot Manager (like rEFInd...see above).

-My laptop came pre-loaded with Win8.1, so this tutorial assumes yours does too.


[LIST=1]
[*]Turn off Win 8 "fast        startup" before installing Linux (recommended [here]("http://www.rodsbooks.com/linux-uefi/");        explained [here]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")):        Control Panel --> Power Options --> Choose what the power        button does --> Change settings that are currently unavailable        --> uncheck "Turn on fast startup..."
[*]Turn off "Secure        Boot" in the UEFI (BIOS-replacement), if not done yet (enter        this menu via F2 during startup, for my laptop).
[*]Do Windows Recovery        onto a USB thumb drive (16GB or larger drive)
[LIST=1]
[*]Use a 16GB+ USB drive            to create a recovery thumb drive (since modern laptops don't come            with any recovery CDs to reinstall Windows
[*]Control Panel -->            Recovery --> Create a Recovery Drive
[LIST=1]
[*]follow instructions;                this will allow you to "copy the recovery partition from the                PC to the recovery drive."
[*]Once done, leave the                Recovery Partition on the drive, since it's only 9GB of data or                so (you may optionally choose the setting to delete the partition otherwise)
[/LIST]
        
[/LIST]

[*]Shrink the Windows C        drive using the Windows "Disk Management" tool in the        "Computer Management" settings
[LIST=1]
[*]Free up a block large            enough for the following items:
[LIST=1]
[*]Swap (equal to RAM                size, so that hibernate is possible in Linux) – (4 GB, or 1024 x 4 MB, exactly, for my PC)
[*]Mint partition (20                GB)
[*]Ubuntu partition (20                GB) (15~25 GB is recommended [here]("https://help.ubuntu.com/community/DiskSpace"))
[*]Alternate Linux                distro free space (20 GB) (optional)
[*]extra space (for SSD                failed sectors—in the future) (1 GB – leave empty) <--my recommendation [untested], since Solid State Drives get bad sectors and shrink in total size over time, and I want to be able to use CloneZilla to do backups periodically.
[/LIST]
        
[/LIST]

[*]Install Linux Mint 17        (these steps are good:        [http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/)); I chose to use just one 20GB partition, mounted at "/", however, rather than using multiple partitions.
-notice near the end that he has a UEFI Boot Manager (see image just before the GRUB menu he shows) that came on his system.  My system does NOT have any similar type of menu, so I will need to use either efibootmgr, built-in to Linux, or a 3rd party UEFI Boot Manager--which is what I end up having to do.
[*]System UEFI Boot        Manager notes:
[LIST=1]
[*]Your system (ex:            Toshiba) **should** have a            good UEFI firmware which allows you to choose which OS to boot to.             If it does NOT, however (like my Toshiba Satellite PC, which            has a crappy UEFI firmware), you need to do something else:
[*]First,            try the efibootmgr, which comes with Linux systems, such as Mint:
[LIST=1]
[*]in a terminal, type                "sudo efibootmgr"! (see here:                [http://linux.dell.com/files/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt](http://linux.dell.com/files/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt))
[LIST=1]
[*]Don't forget to use                    the "modprobe efivars" command beforehand.
[*]On my Ubuntu forum                    thread [here]("http://ubuntuforums.org/showthread.php?t=2240742") (this thread), oldfred recommends the following commands [these commands are                    also recommended and described in the efibootmgr.txt link above                    too!]:
[LIST=1]
[*]modprobe efivars
[*]sudo efibootmgr -v
[/LIST]

[*]to change the boot                    order, use the -o command (ex: "sudo efibootmgr -o 0,1"                    to make the default boot order 0 then 1)
[*]If this is **reset                    during each reboot, and doesn't actually take effect, however**,                    then you will need to install a 3[SUP]rd[/SUP]                    party UEFI Boot Manager, such as rEFInd:
[/LIST]
            
[/LIST]

[*]In a Mint terminal,            install rEFInd Boot Manager (which is at a lower level than a            bootloader, fyi): [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/).             Install instructions here:            [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)            and here:            [http://www.rodsbooks.com/refind/installing.html#packagefile](http://www.rodsbooks.com/refind/installing.html#packagefile)
[LIST=1]
[*]sudo                apt-add-repository ppa:rodsmith/refind
                sudo apt-get update
                apt-get install refind
[*](my preferences): Configure rEFInd to                have a timeout of 5, and a default selection of the GRUB2                bootloader [ex: by setting "default_selection = 3"                <--this val is 1-based] (see config instructions here:                [http://www.rodsbooks.com/refind/configfile.html](http://www.rodsbooks.com/refind/configfile.html))
[LIST=1]
[*]Edit refind.conf on                    the efi partition (sda2 for my computer) to make the above changes                    here:
[*]sudo nemo -->                    navigate to "/boot/efi/EFI/refind/refind.conf"
[/LIST]
            
[/LIST]
        
[/LIST]

[*]In Mint, set default        GRUB bootloader inside the grub config file (sudo nemo --> "/etc/default/grub")
[LIST=1]
[*]then run            "update-grub"
[/LIST]

[*]Backup the efi        partition **(****THIS IS ****IMPORTANT!!!) -- save it        somewhere so that you can restore it if you ever decide to remove        Ubuntu in the future (this way you can go right back to how the efi        partition was at the time it was functioning with just Mint and a        UEFI Boot Manager).**
[*]NOW THAT YOU HAVE A        FUNCTIONAL UEFI BOOT MANAGER (whether stock, using Mint's/Linux's        efibootmgr, or the 3[SUP]rd[/SUP] party rEFInd), you can **install        Ubuntu 14.04. **
[*]Install        Ubuntu, following the same concept as when you installed Mint        above.
[*]The Ubuntu install        will automatically link **both**        Ubuntu AND Mint with        a new GRUB2 loader, which        will now be managed by Ubuntu.  This means that if you want to make        changes to the GRUB2 bootloader, **you must now do it from        within Ubuntu (NOT Mint), or else the changes will not take effect,        since Ubuntu's GRUB is now in charge here.**
[*]From Ubuntu, update        the GRUB bootloader to boot Windows by default (this is my personal preference).
[*]Back up the efi        partition **(IMPORTANT—JUST IN CASE you ever need to restore it        later)**
[*]LINUX        INSTALLS DONE!  You now have a triple-boot setup! Windows 8.1,        Linux Mint 17 (which controls the rEFInd Boot Manager, if        applicable, via the Mint package manager), & Linux Ubuntu 14.04        (which controls the most-recently-installed GRUB2 bootloader that        is now in charge).
[/LIST]

[SIZE=3][B]I hope this helps out some other poor folks like me. :)

Sincerely,

Gabriel Staples
[http://ElectricRCAircraftGuy.blogspot.com/](http://ElectricRCAircraftGuy.blogspot.com/)[/B][/SIZE]

---

