---
title: "Windows 11 and Ubuntu Dual Boot - Windows Hibernation broken"
date: 2022-06-30
forum: Installation &amp; Upgrades
---

### Post by azsde on 2022-06-30
[COLOR=#222222][FONT=Verdana]Hello everyone,[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I am facing an annoying issue which I am trying to resolve.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I have a laptop with two different SSDs installed:[/FONT][/COLOR]

[LIST]
[*]On the 1st one, I have my Windows installation 
[*]On the 2nd one, my Ubuntu installation. 
[/LIST]

[COLOR=#222222][FONT=Verdana]My bios is set up to boot from the 2nd drive, as grub is installed onto it, and grub can get me fine into my two OS.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]The issue happens when I try to put my Windows session into hibernation, if I boot from grub, the session is not restored and windows acts like the PC was shut down forcefully.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]However, if I boot directly from my 1st drive, using the Windows Boot Manager, the hibernation session is correctly restored.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]My windows drive has the following partitions:[/FONT][/COLOR]

[IMG]https://i.imgur.com/FrBumWH.jpeg[/IMG]

[COLOR=#222222][FONT=Verdana]The windows entry of my grub.cfg is the following:[/FONT][/COLOR]

```

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 11" --class windows --class os $menuentry_id_option 'osprober-efi-5CDF-1C88' {
        insmod part_gpt
        insmod fat
        search --no-floppy --fs-uuid --set=root 5CDF-1C88
        chainloader /efi/Microsoft/Boot/bootmgfw.efi
}


set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober_proxy ###

```


[COLOR=#222222][FONT=Verdana]Is there something wrong with my configuration which could prevent Windows from restoring the hibernated session ?[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I thank you in advance for your answers.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Regards,[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Azsde.[/FONT][/COLOR]

---

### Post by oldfred on 2022-06-30
[https://askubuntu.com/questions/1416625/windows-11-and-ubuntu-dual-boot-windows-hibernation-broken](https://askubuntu.com/questions/1416625/windows-11-and-ubuntu-dual-boot-windows-hibernation-broken)

Looks familiar:

Grub only boots working Windows and that  means hibernation or fast start up which sets hibernation flag must be  off. 

If you really want hibernation in Windows, you can directly boot  from UEFI boot menu, not grub. 

But you cannot mount any NTFS partitions  as read/write. You may be able to force mount as read/only but default  mounts are read/write and will then error out.

---

### Post by azsde on 2022-07-01
Yes sorry I didn't know where I would be most likely to get an answer.

Thank you for your answer :)

---

