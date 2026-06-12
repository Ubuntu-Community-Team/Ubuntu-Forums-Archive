---
title: "another &quot;no such partition&quot; ...but like no other"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by ArheoTip on 2016-09-02
Hi, 

I know this has been an often problem, but all the solutions I've googled won't do anything in my case...

I had dual boot Win7 / Ubuntu and I decided to uninstall Ubuntu with Wubi in the Windows "Programs and Feature".
After the restart I got the message:
[B]error: no such partition
Entering rescue mode

[/B]The "ls" command lists:
[B](hd0) (hd0, msdos5) (hd0, msdos4) (hd0, msdos3) (hd0, msdos1)

[/B]Almost whatervercommand I try with the partitions, I get the** "Filesystem is unknown"**. I cannot get into BIOS and I've tried boot discs with WinXP, couple of Win7 versions and USB with Ubuntu. Nothing works.[B]


I've tried :

[/B]grub rescue > set root=(hd0,msdos2)
grub rescue > set prefix=(hd0,msdos2)/boot/grub # or wherever grub is installed
grub rescue > insmod normal # if this produced an error, reset root and prefix to something else ..
grub rescue > normal
but it says **"no such partition" **after **"insmod"** command.

Thank you for your help - getting pretty desperate here...

---

### Post by ajgreeny on 2016-09-02
There must be a way to get to the BIOS as an OS never has any effect on BIOS or its settings; you do not even need an OS on the computer to get to BIOS so I think you must be missing some info on how to do so.

Have you tried all the F# keys, on by one, or Del or Esc at power-on to see if that gets to the BIOS setup? There is often a momentary message on screen which tells you what key to press to get to setup so watch very carefully at power-on.

If you are getting a grub rescue prompt it suggests that you must have had grub on the MBR of your disk which you would not have had using wubi, so are you certain that the wubi installation was the only Ubuntu OS that you had.
Have you, for some reason installed grub to MBR in the past using a command such as ```
sudo grub-install /dev/sda
```
I have no real knowledge of what that command would do if run from a wubi installed Ubuntu system, so I'm just thinking as I write here, but it may give you some ideas.

---

### Post by hakuna_matata on 2016-09-03
> **ArheoTip said:**
> I decided to uninstall Ubuntu with Wubi in the Windows "Programs and Feature".
i.e. You also installed Ubuntu with Wubi. Otherwise it is not possible to uninstall it with Wubi.

Wubi installs a boot loader chain like this:
```

MBR -> Windows Boot Manager -> Windows (default)
                            -> GRUB4DOS -> GRUB2 -> Ubuntu

```
You can use Windows boot menu to select Windows (default) or Ubuntu. Because the installed boot loader chain still uses Windows Boot Manager it should be always possible to use function keys for Windows e.g.: [F8 key]("https://neosmart.net/wiki/f8-key") before booting into GRUB2 or Ubuntu.

If you uninstall Ubuntu with Wubi, it deletes only an Ubuntu installed by Wubi. Maybe, you also installed an Ubuntu without Wubi and your boot loader chain looks like this:
```

MBR -> GRUB2 -> Ubuntu (default) installed without Wubi
             -> Windows Boot Manager -> Windows
                                     -> GRUB4DOS -> GRUB2 -> Ubuntu installed by Wubi

```

 Maybe, you also changed your Windows boot menu with programs like [EASYBCD]("https://neosmart.net/wiki/open-source/easybcd/"). EASYBCD can use a boot loader technique like Wubi but of course Wubi doesn't uninstall all changes of EASYBCD.

Helpful information could be also: [URL="https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F"]How_do_I_manually_uninstall_Wubi
[/URL]
But it is difficult to help you without knowing details. e.g.: Did you also install Ubuntu without Wubi ?

---

