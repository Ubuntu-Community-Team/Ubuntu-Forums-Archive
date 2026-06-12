---
title: "acpi and fnfxd not working on toshiba A70 PIV"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by cantormath on 2006-03-22
Hello everyone, I need a direction and a little instruction....

1st
lshw and dmesg files are below:
[lshw]("http://vwsporttech.com/lshw.html")
[dmesg]("http://vwsporttech.com/dmesg.html")

I have a Toshiba A70 with a Pentium IV 3.06 mhz chip, ATI Radeon AGP(9100 IGP) etc... video card.  These two things have been a combination of problems.

issue:
I have the not so uncommon problem of my ACPI not working properly.  Breezy has been the closest, ie battery meter works, and warns me when power is low and screen will shut off after none use.  The problem is I am not able to hibernate and my fan runs twice as much as it does under windows, an on going problem with this laptop.  I have tried install the fnfxd and fnfx-client, but it fail to intiate because there is no "proc/acpi/toshiba" file......  From what I can tell, my acpi seems to be picking up alright, so I can't tell what's going wrong.
Note: I have toshset install (installed on installation) no toshutils (wasn't installed on installation) and fnfxd was not installed on installation.

The people at [Fnfx]("http://fnfx.sourceforge.net/index.php?section=doc") say:
[I][INDENT]
"To check if ACPI and ACPI Toshiba support are enabled check the following proc entries exists:
/proc/acpi
/proc/acpi/toshiba
-If they do exist, FnFX will work on that system. If they do not exist try `modprobe toshiba_acpi' as root. If this throws errors like 'FATAL: Module toshiba_acpi not found' the kernel is most likely not compiled with CONFIG_ACPI and CONFIG_ACPI_TOSHIBA.
-Please recompile your kernel with the ACPI drivers or have a look for a precompiled kernel for your distribution which has ACPI and ACPI Toshiba support."[/INDENT][/I]
I urname -r:
[I][INDENT]cantormath# uname -r
2.6.12-10-386[/INDENT][/I]
so I modprobe as root:
[I][INDENT]cantormath# modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-10-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device[/INDENT][/I]
so either toshiba_acpi is not there, or it is there and cannot be inserted..?
I have no idea, so, I came to the forum ::grin::
Please help or tell me what you need to know to help.. ](*,) 

My video card problems are for another post...

cantormath...

---

