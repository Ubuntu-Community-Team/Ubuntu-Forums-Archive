---
title: "Win8/Ubuntu dual boot"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by Choobie on 2013-05-15
Hi,

I've been working on this for a while and would appreciate some help:

Using Ubuntu Gnome 13.04.

When I select Windows 8 from grub, I get: 
```
can't find command 'drivemap'
invalid EFI filepath
```
This is from the automatically generated menuitem.

When I created my own menuitem in /etc/grub.d/40_custom I appended this in:

```
menuentry "Microsoft Windows 8 x86_64 UEFI-GPT" {
        insmod part_gpt
        insmod fat
        insmod search_fs_uuid
        insmod chain
        search --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5 D08832F78832DC22

        chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

and got this error when selecting my custom Windows 8 menuitem:

```
unspecified search type
file '/EFI/Microsoft/Boot/bootmgfw.efi' not found
```

I based the text I put into 40_custom off what I read in the archwiki here: [https://wiki.archlinux.org/index.php/GRUB#Multiboot_2](https://wiki.archlinux.org/index.php/GRUB#Multiboot_2)
and from my boot-repair output here: [http://paste.ubuntu.com/5666639/](http://paste.ubuntu.com/5666639/)
I found others who had the same laptop model as mine, they said running boot-repair from a liveCD fixed the issue, unfortunately that didn't work for me.


Ubuntu boots fine, but I can't get Win8 to boot because of the above errors. I can't figure out what is going wrong, but knowing my luck and it being late I probably just misspelled something.

Thank you for your help!

Choobie

---

### Post by bluenova on 2013-05-15
insmod fat

shouldn't that be ntfs?

---

### Post by fantab on 2013-05-15
Delete that entry fro 40_custom and run [BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair")... if you still have problems then post the output of "Bootinfo Summary" that Boot-Repair genarates.

---

### Post by oldfred on 2013-05-15
You cannot chain load or boot another system installed if not in same boot mode. UEFI and BIOS write system info and internally work differently. You have Ubuntu in BIOS mode therefore you cannot from grub menu boot Windows. You can dual boot only by going into UEFI/BIOS turn on UEFI and boot Windows. You may need secure boot on. Many systems only boot with secure boot. And to Boot Ubuntu you have to go into UEFI/BIOS turn off secure boot, turn off UEFI and turn on CSM/BIOS to boot Ubuntu. Not an easy way to dual boot.

But Boot-Repair can convert a BIOS install (if on gpt drive) to UEFI install by uninstalling grub-pc (BIOS) and installing grub-efi(UEFI). There are really three versions, BIOS, UEFI and UEFI Secure boot with signed grub & kernel. If you can boot Windows with secure boot off you do not have to install the secure boot version. But some also have internally modified UEFI to only boot Windows efi file. Boot-Repair has another work around to backup Window files and rename grub files to make it work.

Just a note.
 How you boot install media, is how it installs. So from UEFI menu if you boot the efi choice it will install in UEFI mode. If you boot something called CSM/Legacy/BIOS then it installs in BIOS mode.
Also with UEFI any manual chain load entries are back to the efi partition not any other. Boot-Repair automatically creates correct chain load entries as grub2's os-prober still has a bug and only creates BIOS type entries that do not work.

---

### Post by Choobie on 2013-05-15
Hi everyone, thank you for your responses.

bluenova; I tried that out since it was quick and easy to test, unfortunately it didn't work.

Oldfred: In my BIOS (or whatever the UEFI equivalent is) I have two options for boot mode: UEFI and Legacy. If I select Legacy, another option called Boot Priority pops up with two choices: UEFI First and Legacy First. I also have the option to set boot orders for both UEFI and Legacy.

What I have done:

[LIST=1]
[*]Installed Ubuntu in UEFI Boot mode. I could not use the "Try Ubuntu First" option because it black screens. I was able to set nomodeset=1 on "Install Ubuntu" and get into a graphical installer (though the resolution was wrong).
[*]After install, still on UEFI Boot mode, Windows will boot if it is set first in the boot order. If Ubuntu/grub is set first in the boot order, windows fails to boot with the error "Can't find command 'drivemap'" etc., while Ubuntu gives me a black screen. Setting ubuntu to boot with nomodeset=1 will bootinto text mode. From there, running startx complains about not finding a screen to boot to. Maybe i just need to install the proprietary NVIDIA drivers?
[*]I go back the BIOS options, change boot mode from UEFI to Legacy, boot priority to UEFI First. Ubuntu boots just fine with graphics and everything. No NVIDIA drivers installed yet (I think it is using the open source ones, or the generic open source ones). Windows still gives the "Can't find 'drivemap' error.
[/LIST]

 I have not run boot-repair on this current install because I can't boot a graphical liveUSB in UEFI Boot mode. If I set Legacy->UEFI boot options I can and I can run boot-repair, but then I am back to where I started. Running boot-repair from my installed system, and just having it print out the info gives this: [http://paste.ubuntu.com/5669361/](http://paste.ubuntu.com/5669361/)

Thank you for your help,

Choobie

---

### Post by ubfan1 on 2013-05-15
Maybe the "--fs-uuid --set=root" got left out of your menu item on the search line?  "root" would have to be defined earlier in grub.cfg otherwise.

---

### Post by oldfred on 2013-05-15
You can add boot repair to your existing installer or download the repair only version that is just a lightweight Linux repair tool.

If you need nVidia drivers and can boot Ubuntu, you should install them. They are in system settings or you can use command line.
       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

There are several versions.

 #To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*

Is the issue of booting Windows from the grub menu? If you cannot run boot repair you have to manually add correct boot stanza, examples in bug report.
      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

