---
title: "grub error"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by springring on 2011-07-20
[SIZE=2]Hi,[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]  My machine is IBM system x3500 m3 which use GPT basis on EFI module.[/SIZE]
[SIZE=2]I install ubuntu desktop on it successfully.[/SIZE]
[SIZE=2]  But after system update grub  and restart, it show error as:[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]error:file not found[/SIZE]
[SIZE=2]grub rescue>[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]   when I key in command "ls" it reply:[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2][SIZE=2](hd0)[/SIZE][SIZE=2](hd0,gpt3)[SIZE=2](hd0,gpt2)[SIZE=2](hd0,gpt1)(cd0)[/SIZE][/SIZE][/SIZE]
 
   then I key in "set" it show:
 
prefix=(hd0,gpt2)/boot/grub
root=hd0,gpt2
 
    when key in "ls (hd0,gpt2)/" it show there is directory "boot"
so, why it can not find the file?
 
Thks.
 
Ring

[/SIZE]

---

### Post by srs5694 on 2011-07-20
My experience is that GRUB's EFI/UEFI support is unreliable, particularly in the builds provided by Ubuntu. My own personal preference is to use [ELILO](http://elilo.sourceforge.net/cgi-bin/blosxom) instead. To do so:


[list=1]
[*]Create a suitable directory on your EFI System Partition (ESP). In Linux, /boot/efi/EFI/elilo should do, but be sure the ESP is mounted at /boot/efi. You'll presumably need to do this from a rescue CD.
[*]Unpack the elilo.efi file to the directory you created in the previous step.
[*]Copy your kernel (/boot/vmlinuz*) and initial RAM disk (/boot/initrd.img*) files to the ELILO directory on the ESP.
[*]Create an elilo.conf file in the ELILO directory on the ESP. (See below.)
[*]Add ELILO to the EFI's boot options. You can probably do this using the firmware's own interface, but details vary greatly from one EFI implementation to another. Alternatively, you can use the efibootmgr command in Linux, but I don't recall the precise syntax offhand; you'll need to consult the program's man page or find documentation elsewhere.
[/list]


The ELILO configuration file can be quite simple compared to a GRUB 2 configuration file. Here's a working sample:

```

prompt
timeout=50
default=linux
#chooser=textmenu

image=bzImage-2.6.39
        label=linux
        initrd=initrd.img-2.6.39
        read-only
        root=/dev/sda2
        append="reboot=a,w"

```

Change your kernel filename, initial RAM disk filename, and "root=" options, as necessary. You can also change kernel options, which are passed using the "append=" line; this example adds options that fix a [known hang-on-reboot bug.](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721576)

Note that if you use ELILO, you'll have to manually update your kernel in the ELILO configuration. Also, ELILO can't redirect the boot process to a non-Linux OS, so if you're dual-booting with Windows or some other OS, you'll need to either use your firmware for that or use another boot loader, such as rEFIt. (There's a version in the Ubuntu repositories. In my experience, the 64-bit version works on UEFI-based PCs, but the mixed 32-/64-bit version works only on Macs.)

If you prefer not to switch to ELILO, I've had better luck compiling GRUB 2 from scratch and installing it all in the ESP, as described [here,](https://help.ubuntu.com/community/UEFIBooting) rather than using Ubuntu's package.

---

### Post by coverify on 2011-07-21
> **springring said:**
> [SIZE=2]Hi,[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]  My machine is IBM system x3500 m3 which use GPT basis on EFI module.[/SIZE]
[SIZE=2]I install ubuntu desktop on it successfully.[/SIZE]
[SIZE=2]  But after system update grub  and restart, it show error as:[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]error:file not found[/SIZE]
[SIZE=2]grub rescue>[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]   when I key in command "ls" it reply:[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2][SIZE=2](hd0)[/SIZE][SIZE=2](hd0,gpt3)[SIZE=2](hd0,gpt2)[SIZE=2](hd0,gpt1)(cd0)[/SIZE][/SIZE][/SIZE]
 
   then I key in "set" it show:
 
prefix=(hd0,gpt2)/boot/grub
root=hd0,gpt2
 
    when key in "ls (hd0,gpt2)/" it show there is directory "boot"
so, why it can not find the file?
 
Thks.
 
Ring

[/SIZE]

I faced the same issue a week back. I had upgraded my usbuntu machine using aptitude. I noticed that aptitude replaced grub-efi with grub-pc.

What followed was a boot failure just as you are describing. I suggest that you boot into your system and then replace grub-pc with grub-efi.

---

### Post by springring on 2011-07-21
Thanks srs and coverify,
 
    the first method is a little difficult for me, so I will try grub-efi first.
 
Thank you very much.
 
Ring

---

