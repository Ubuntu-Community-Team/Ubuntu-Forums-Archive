---
title: "Segmentation Fault when exiting from su ubuntu 16.04 and 18.04"
date: 2018-08-22
forum: Installation &amp; Upgrades
---

### Post by donald-flissinger on 2018-08-22
[COLOR=#000000][COLOR=#000000]Hi,[/COLOR][/COLOR]

[COLOR=#000000]I don't know where to put this topic, so I'm trying it here.[/COLOR]

[COLOR=#000000][COLOR=#000000]Strange segmentation fault when exiting from su,[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]I'm on Ubuntu Server release:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]root@ubuntu-server:/home/donald# uname -a[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Linux ubuntu-server.flissinger.local 4.4.0-133-generic #159-Ubuntu SMP Fri Aug 10 07:31:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]root@ubuntu-server:/home/donald# cat /etc/lsb-release[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]DISTRIB_ID=Ubuntu[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]DISTRIB_RELEASE=16.04[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]DISTRIB_CODENAME=xenial[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]DISTRIB_DESCRIPTION="Ubuntu 16.04.5 LTS"[/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000]dmesg gives:[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000][389161.916804] traps: su[64329] general protection ip:7f7295ad1cc0 sp:7fffb5301370 error:0 in libc-2.23.so[7f7295a83000+1c0000][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][389358.155893] traps: su[102473] general protection ip:7f8916169cc0 sp:7ffdd9b10250 error:0 in libc-2.23.so[7f891611b000+1c0000][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][389374.965757] traps: su[102987] general protection ip:7fcb59daacc0 sp:7ffd571f9f90 error:0 in libc-2.23.so[7fcb59d5c000+1c0000][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][390430.144714] traps: su[103041] general protection ip:7fa4b84facc0 sp:7fff7021ec10 error:0 in libc-2.23.so[7fa4b84ac000+1c0000][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][390451.290534] traps: su[108098] general protection ip:7fb296340cc0 sp:7ffd000b78f0 error:0 in libc-2.23.so[7fb2962f2000+1c0000][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000]root@ubuntu-server:/home/donald# exit[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]exit[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Segmentation fault (core dumped)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]donald@ubuntu-server:~$[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]How to debug?[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Best Regards,[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Donald.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]edit:[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Just upgraded to 18.04 LTS via do-release-upgrade but the error still persists, anyone?[/COLOR][/COLOR]

---

