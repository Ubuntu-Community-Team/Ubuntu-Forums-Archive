---
title: "Wine wont run on Ubuntu 8.04"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by Hozza on 2008-07-08
Hi,

please can someone help me!

my wine installation wont work!

i may have deleted one or more of the files that wine uses :oops:

I have tried doing a full uninstall and then reinstall, i then ran the command "winecfg" to set up the .wine directory in my home folder. It then gave me this....

```

hozza@hozza-laptop-ubuntu:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/hozza/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Could not load Mozilla. HTML rendering will be disabled.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:seh:setup_exception_record stack overflow 840 bytes in thread 0009 eip 7bc65706 esp 7f120fe8 stack 0x7f120000-0x7f121000-0x7f220000
wine: wineprefixcreate failed while creating '/home/hozza/.wine'.
hozza@hozza-laptop-ubuntu:~$ wineserver: could not save registry branch to /home/hozza/.wine-rbG3ed/system.reg : No such file or directory
wineserver: could not save registry branch to /home/hozza/.wine-rbG3ed/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/hozza/.wine-rbG3ed/user.reg : No such file or directory
hozza@hozza-laptop-ubuntu:~$ 

```

please someone help!!!!!
I cant live without CS3!!!!!!

:cry:

---

### Post by rothalem on 2008-07-08
I know little about Linux and even less about wine, but I would like to get wine working on my machine. It installed and seems fine, havnt installed anything windows related on it yet though.

It looks as though wine cannot access memory somewhere (assuming ram).

I would reboot the PC (if you havn't since you installed it) then try redownload/install using the package manager. Reboot again and see what happens. Hope that is not what you meant by "reinstalled".

You imply you updated ubuntu and then installed your old wine. You might need a newer version of wine.

Hope something I said helps, tbh I dont know anything myself.

---

