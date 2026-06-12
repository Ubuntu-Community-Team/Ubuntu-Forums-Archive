---
title: "Upgrading 12.10 via fresh install of 14.04 - boot problems"
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by Ck.asdf on 2014-06-16
Hello, I had Ubuntu 12.10 on my laptop (details in signature), and tried to upgrade to 14.04.   This is on a Windows 7 & Ubuntu dual-boot system, using UEFI.  First, my partition layout:

/dev/sda1  - /boot/efi     (boot flag)
/dev/sda2  - "unknown"   (msftres flag)
/dev/sda3  - Windows 7
/dev/sda4  - /boot
/dev/sda8  - /
/dev/sda5  - /home
/dev/sda6  - swap
/dev/sda7  - /personaldata

Not sure why sda8 is stuck where it is.  sda7 is just my big dump partition for my music, pictures, etc.  Sort of an overflow for /home.  All the ext4 partitions and Windows (NTFS) are listed with the flag "msftdata."

My process for installing:
*Boot to USB Ubuntu 14.04 Live
*Request to install Linux
*Choose "something else" for partition layout
*Set all applicable partitons for use as ext4 with their respective mount-points
*Mark / for formatting
*Keep default of installing bootloader to /dev/sda

After this, restart, and get some kind of unknown grub error, dropping me into grub rescue.  Knowing my boot partition is on sda4, I tried the information at this link:
[http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash)
```

grub rescue>  set root=(hd0,gpt4)/boot
grub rescue>  insmod linux
grub rescue>  linux (hd0,gpt4)/boot/vmlinuz-2.6.32-33-generic  
grub rescue>  initrd (hd0,gpt4)/boot/initrd.img-2.6.32-33-generic  
grub rescue>  boot

```

But after the linux(hd0... line I got a message about an unknown operating system, and then a memory pointer error after the initrd line.

After that, I tried running boot-repair by installing it with the trick of changing repositories to the earlier Ubuntu, but it failed too.
[http://paste.ubuntu.com/7650988](http://paste.ubuntu.com/7650988)

After this, i decide to try again.  Same partition layout as above, requesting / and /boot be formatted.  Once I got to the bottom where it asks where to install the bootloader, I found this link:
[http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash)
```

While with BIOS/MBR systems you install to the MBR and almost never to a partition, with UEFI you always install to the efi partition. It actually should default to install to that partition anyway and you can only have one efi partition (with boot flag) per drive.

```

Install finishes, I get this after reboot:

```

error: symbol 'grub_term_highlight_color' not found.
grub rescue> _

```

When I use supergrub2, then choose "Everything" from the first menu, I get a long list that looks something like this:

```

 ---- Operating Systems ----
     (hd0,gpt1)/efi/Boot/bootx64.efi (hd0,gpt1)
     (hd0,gpt1)/efi/Ubuntu/grubx64.efi (hd0,gpt1)
     [...]
     (hd0,gpt1)/efi/Microsoft/Boot/bootmgr.efi (hd0,gpt1)
     [...]
 ---- grub.cfg - Extract entries ----
   --  Entries from... (memdisk)/boot/grub/grub.cfg --
   --  Entries from... (hd0,gpt4)/grub/grub.cfg --
ubuntu
Advanced options for Ubuntu
Windows Boot Manager (on /dev/sda1)
 ---- grub.cfg - (GRUB2 configuration files) ----
          (memdisk)/boot/grub/grub.cfg
          (hd0,gpt4)/grub/grub.cfg
     [...]
 <-- Return to main menu

```

If I hit Ubuntu or Advanced options for Ubuntu, it'll let me boot to my new 14.04 desktop.  According to the supergrub site, they recommend I run "grub-install /dev/sda" but that does nothing for me, it runs without error. I've also tried "grub-install /dev/sda1" per the inspiration of the above link regarding BIOS vs UEFI.


One last piece of information, no idea whether this is helpful, but when I look at /dev/sda1, the directory layout looks messy/redundant.
```

/mnt/sda1/
                  Boot/
                                bootx64.efi
                                bootx64.efi.grb
                  EFI/
                                Boot/
                                              bootx64.efi
                                              bootx64.efi.bkp
                                Microsoft/
                                              Boot/
                                                     [LOTS of stuff]
                                ubuntu/
                                              grub.cfg
                                              grubx64.efi
                                              MokManager.efi
                                              shimx64.efi
                  Microsoft/
                                Boot/
                                        bootmgfw.efi
                                        bootmgfw.efi.grb
                                        bootx64.efi
                                        bootx64.efi.grb

```
Could this be part of the cause for confusion?

No idea on where to proceed from here.  Thoughts?  Thanks in advance for any help!

---

### Post by squakie on 2014-06-16
After you boot using supergrub, try the following:

- open a terminal windows (ctrl/alt/F1)
- type:

sudo update-grub <press enter>  use your normal password - it won't be echoed to the screeen

sudo shutdown -r now <press enter>  to force a reboot


After the system goes through boot do you still have the errors?

---

### Post by Ck.asdf on 2014-06-16
Hello, thanks for the response.  Still a no-go.  grub-rescue still came up.

After I ran update-grub from within installed 14.04, it says:

> 
ck@ckvaio:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
done
ck@ckvaio:~$ _


---

### Post by oldfred on 2014-06-16
Even with UEFI you still install to sda not sda1, but actual files are installed in sda1 or whatever efi partition is. 
Part of issue can be that some users with UEFI systems install in BIOS mode and if they install to the efi partition it will not work.

It says grub installed correctly, but script is not showing files in efi partition that post above are there??

I might try this, since with Supergrub you can get into your install, but I am not sure if command is grub-pc as that really is only the BIOS boot version of grub or really should be grub-efi?? 
I would think it should be grub-efi or grub-efi-amd64? And reinstall to sda.

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

The other option is to do a full purge & reinstall of grub. If you cannot get into system then you can use Boot-Repair to chroot into it and it will walk you thru it.

But if in your system, you should be able to purge and reinstall. Just make sure you have working Internet as after a purge, system will be unbootable until new version installed.

Asrock's have some issues:

 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by Ck.asdf on 2014-06-16
I'll check your suggestions when home. But to answer your BIOS/UEFI install question, I installed it in UEFI mode (live USB boot looks different in UEFI vs BIOS).

---

### Post by Ck.asdf on 2014-06-17
So I tried each item above.  I ran sudo apt-get install grub-efi grub-efi-amd64 and it said it did its magic installation.  Ran sudo dpkg-reconfigure grub-efi-amd64, got:

> 
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found Windos Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
done


FYI, following the steps below for purging & reinstalling using grub-efi, it tells me the location of grub is /dev/sda4  (which is my /boot partition).  That's not where it's supposed to be, is it?
> 
grub-probe -t device /boot/grub
/dev/sda4
grub-install /dev/sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-probe -t device /boot/grub
/dev/sda4


Even tried purging and reinstalling GRUB.  Nothing still working.

I was about to just wipe & reinstall both Windows & Ubuntu as I was frustrated, but when I booted the Windows disc, I decided to try a repair.  I asked it to repair its boot process.
Now, when booting to the drive, instead of getting a grub error, it just boots Windows straight up, no question about Ubuntu or anything else.  Re-running grub install, etc, gets me nothing.  So now the question is how to overwrite the Windows boot process to show GRUB, to ask for Linux or Windows to boot up.

I really appreciate all the efforts given thus far.  Any thoughts on this continued journey?

---

### Post by oldfred on 2014-06-17
When you say nothing is working what happens? Just grub rescue or blank screen or ??

Your repair to Windows just reset it to be first in UEFI boot menu, so on reboot it loaded.

There is a bug on upgrades and usually the dpkg or total reinstall work.

       Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

---

### Post by Ck.asdf on 2014-06-17
Sorry for the vague answer. When I say "nothing working" I just mean that unfortunately none of your suggestions have succeeded in working.  While starting the computer now boots directly to Windows, I cannot get back to Ubuntu unless I use the supergrub disc.  As I mentioned near the end of my last post, GRUB is being installed (it would seem to my understanding) to /dev/sda4, whereas you're saying it should be installed to /dev/sda - so how do I tell it to leave /dev/sda4 alone?

---

### Post by oldfred on 2014-06-17
When you ran this, did you choose only sda?
sudo dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Ck.asdf on 2014-06-17
Initially, I starred both sda and sda4, but later I ran it again and only starred sda.

Maybe my first go has messed it up? Should I try to remove it from sda4 and run it again?

---

### Post by oldfred on 2014-06-17
As long as you installed to sda that should be ok. The install to sda4 should not matter, but with the UEFI version I am not sure what it does. With BIOS version it installs to the Partition PBR which is not otherwise used.
It may have overwritten a /boot partition or added one?

Post new link to BootInfo report.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Ck.asdf on 2014-06-17
I re-installed boot-repair, and on first run it told me I didn't have the necessary [linux] packages.  Not sure what that meant.

The computer got very unresponsive, and I had to use a TTY session to kill Xorg.  After logging back in, I ran boot-repair again, and this time it said "Purge kernels then reinstall last kernel sda8 (ins). This may require several minutes."

  I allowed it to run for a while, came back, and got:

> 
An error occurred during the repair.
[http://paste.ubuntu.com/7661344](http://paste.ubuntu.com/7661344)

(Edit: pasted a broken link; have corrected it.)

---

### Post by oldfred on 2014-06-17
Boot-Repair picks up some errors that are not vital or even relavent.

grub-install /dev/sda: exit code of grub-install /dev/sda:0

Since error code is 0 it says grub reinstalled ok.

But you do not show any efi files in your efi partition sda1. Are they there?
You should have both a Windows folder and an Ubuntu folder with efi files and others.
It looks like it may need chkdsk from Windows or similar check from Linux.

Must be unmounted
sudo fsck -t vfat /dev/sda1
or
sudo dosfsck -t -a -w /dev/sda1
see also 
man dosfsck

When Boot-Repair runs some of the updates, it may pick up other updates you would be installing also.

---

### Post by Ck.asdf on 2014-06-17
I do have files / folders within sda1.  There are three folders in the root of /boot/efi (where sda1 is mounted): Boot, EFI, and Microsoft.

I ran the fsck command and found:

> 
0x41: Dirty bit is set.  Fs was not properly unmounted and some data may be corrupt.


It asked me if I wanted to remove the dirty bit, and once I answered yes, it said leaving filesystem unchanged.

Ran the dosfsck command, gave the same 0x41 message, but then said "Automatically removing dirty bit.  Performing changes."  After this, running fsck again didn't mention dirty bits.

Now that I've "cleaned" sda1, suggestions on how to proceed?

----- ALL THE BELOW WAS WRITTEN BEFORE YOUR RESPONSE -----

While waiting (before your response about fsck), I decided to re-install one more time, considering that I'd changed the boot process by running the Windows repair.  I chose /dev/sda as the install point for GRUB, and this time I wiped out /dev/sda4 (/boot) and /dev/sda8 (/) replacing them with a single /dev/sda4 (/ by itself, which would include /boot within it).

The first thing I did after the fresh install was to install & run boot-repair.
[http://paste.ubuntu.com/7661482/](http://paste.ubuntu.com/7661482/)  (most recent)

Still, when I boot the drive by itself, it boots Windows only (which is different than the start of the thread, which wouldn't boot at all).

Using supergrub2, I can boot to Ubuntu.  Running the following completes with no errors:
dpkg-reconfigure grub-efi-amd64 
grub-install --target=x86_64-efi /dev/sda

However, I still have no GRUB upon boot.  Most recently, I found this article which looked promising. While I don't have Windows 8, I do have Windows 7 and a complete EFI environment (meaning not mixed MBR/EFI).
[https://sites.google.com/site/easylinuxtipsproject/6](https://sites.google.com/site/easylinuxtipsproject/6)

Ran through the instructions there with no luck.

Reading through various places, it seems I need to get GRUB installed on sda1 to reside in the same spot as where the EFI boot files for Windows are.  Oddly enough, on my desktop (Ubuntu 14.04 only), grub-probe reports that GRUB is installed on /dev/sda3 (/) instead of /dev/sda1 (EFI partition).

---

### Post by oldfred on 2014-06-18
It now mounted and shows all the efi files in your sda1 efi partition.

You show both Windows & ubuntu in efi partition.
From UEFI menu can you boot ubuntu entry?

You also show copies of grub in the MBR for BIOS boot and in your older BootInfo in the PBR or partition boot sector of sda4. New version of BootInfo does not show grub in PBR. I have never seen it erased, but it is not used, so never really matters. Did you say you totally reinstalled? That would have reformatted it.

This should be what you have in UEFI menu:
>  BootOrder: 0001,0000,0002
Boot0000* EFI DVD/CDROM
Boot0002* Windows Boot Manager
Boot0001* ubuntu.

Some laptops have lots of issues with modified UEFI. I would not expect that issue with a motherboard.
Some manually rename bootx64.efi and make that name be shim. then when you boot hard drive it boots grub.
Others like rEFInd.

 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)






Do you still get grub rescue or blank screen?

---

### Post by Ck.asdf on 2014-06-18
THANK YOU THANK YOU THANK YOU!
As soon as you said "UEFI menu" it got me thinking of the differences between my ASRock desktop motherboard and Sony Vaio S motherboard.  My Sony, as you edited your post to include extra info for, doesn't really have a UEFI menu or whatnot ... it's very basic support, maybe because of it being an earlier version, whereas my desktop has all kinds of UEFI stuff.

Once I realized that, I did a Google search and found the link below, which suggested exactly what you added to your post - renaming the files.
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)


So, my final question (which may be answered above - apologies if it is, I'm quite tired from all this haha), is now that I've renamed bootmgfw.efi to bootmgfw.efi.old, how can I link to it in GRUB with the new name (or would I just run an update-grub or similar for it to find that)?  Obviously now, when I choose Windows from the list, it tells me that it can't be found.

I thank you so much for staying with me through this past few days.  EFI still seems to be in the frustrating stages of "infancy," but it does seem to have performance benefits to old-school BIOS.

---

### Post by oldfred on 2014-06-18
Boot-Repair used to do the Windows file rename and add a boot stanza to 25_custom. Most of us edit 40_custom, but it depends on where you want the Windows entry in the boot order. Grub processes the scripts in number order.
So if you want Windows first copy 40_custom to 06_custom and make it executeable. Then add your custom boot stanza for your renamed Windows.

I stopped suggesting renaming the Windows efi file as first option as any Windows update will rewrite the Window file undoing the rename. I do not have UEFI so not tested myself but many rename /EFI/Boot/bootx64.efi     or install rEFInd which also has a gui for booting.

If you update Windows undo the rename before update, as it will revert it to being the actual Windows file, or remember to go back and rename again.

You can use this for editing any of the custom files, just change name.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub



You may want to turn off os-prober as it now is not doing anything useful. If you add another system and want it to work just turn on executeable bit again.

 # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub

One example, you must change to your efi partition from sda2 and change to correct UUID. These show the standard bootmgfw.efi name. Change that to whatever you used for your actual Windows file.
Boot-Repair in its 25_custom version used bkpbootmgfw.efi, so whatever name you use should not matter.

 Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 8 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

Two more examples. You only need a set root or a search line not both. The idea is that the set root should be correct but if not then the search line overides the set root. I would think a search by file might be slower. Search by UUID should be a bit quicker. The full stanza above includes both set root & search by UUID which should be the same partition that is you efi partition.


 menuentry "Windows bootmgfw.efi UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
x
menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root 18FE-69D8
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

