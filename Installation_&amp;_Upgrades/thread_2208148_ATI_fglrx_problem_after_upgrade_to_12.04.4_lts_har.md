---
title: "ATI fglrx problem after upgrade to 12.04.4 lts hardware stack"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by fig_wright on 2014-02-26
I upgraded to the 12.04.4 lts saucy stack from 12.04.3:
```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
```
That installed the 3.11 kernel to go with the 3.8 I had previously. However, when logging in I see I am in fallback mode, and fglrx is nowhere to be seen, from Xorg.0.log:
```
Loading extension GLX
FATAL: Module fglrx not found.
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
FATAL: Module fglrx not found.
Loading extension FGLRXEXTENSION
```
I cant load it directly either:
```
 > sudo modprobe fglrx
FATAL: Module fglrx not found.
```
If I boot with the old 3.8 kernel everything is hunkey-dorey. No probs at all.

I think this might be some kind of dkms problem. In /lib/modules I have:
```
drwxr-xr-x 4 root root 4096 Feb 10 20:43 3.8.0-35-generic
drwxr-xr-x 4 root root 4096 Feb 24 20:36 3.11.0-17-generic
```
However:
```
 > ls -l /var/lib/dkms/fglrx/13.251/
total 8
drwxr-xr-x 3 root root 4096 Feb  5 22:05 3.8.0-35-generic
drwxr-xr-x 4 root root 4096 Feb 24 20:36 build
lrwxrwxrwx 1 root root   21 Dec 27 17:06 source -> /usr/src/fglrx-13.251
```
Shouldnt there be a 3.11 kernel entry there? How to I refresh dkms to see the new kernel that just got installed? Or is that not the problem?

---

### Post by fig_wright on 2014-02-27
Bump?

---

### Post by Bashing-om on 2014-02-27
fig_wright; Hi !

I can not answer your questions, others too may have that difficulty. Please provide amplifying information:
To see your graphics card and info:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To show what release and related kernel you are indeed booting:
```

lsb_release -a
uname -a

```
Then trouble shooting efforts can be directed to cause and effect.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by fig_wright on 2014-03-01
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D] [1002:964a]
	Subsystem: ASUSTeK Computer Inc. Device [1043:84c8]
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

Linux {hostname} 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:24:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

12.04.4

```

---

### Post by Bashing-om on 2014-03-01
fig_wright; Hey ,

 A bit of looking about indicates that better performance with that card is from the open source drivers.
For instance:
[http://ubuntuforums.org/showthread.php?t=2121969http://ubuntuforums.org/showthread.php?t=2121969](http://ubuntuforums.org/showthread.php?t=2121969http://ubuntuforums.org/showthread.php?t=2121969)

Possible avenue to resolution: fglrx: -> aticonfig:
[http://forum.xbmc.org/showthread.php?tid=154557](http://forum.xbmc.org/showthread.php?tid=154557)

Problem summary:
[http://forums.linuxmint.com/viewtopic.php?f=68&t=86750&start=20](http://forums.linuxmint.com/viewtopic.php?f=68&t=86750&start=20)

Take your best shot at installing a driver, and
[INDENT][INDENT]we will pick it up from there
[/INDENT][/INDENT]

---

### Post by fig_wright on 2014-03-03
Got it! :-)

Critical error was this:
> Error! Bad return status for module build on kernel: 3.11.0-17-generic (i686)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.

This led me to the solution:

```
    sudo gedit /usr/src/fglrx-13.251/kcl_acpi.c
```

Delete these last 3 lines in the file:

```
         ((acpi_table_handler)handler)(hdr);
         return KCL_ACPI_OK;
    }
```

replace them with:

```
    #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,9,1)
        ((acpi_tbl_table_handler)handler)(hdr);
    #else
        ((acpi_table_handler)handler)(hdr);
    #endif
        return KCL_ACPI_OK;
    }
```

Then run:

```
    sudo dkms install -m fglrx -v 13.251 -k 3.11.0-17-generic
```

Then reboot. Worked for me - working kernel 3.11 and fglrx now!

I worked this out from this page: [https://gist.github.com/moldcraft/8116528](https://gist.github.com/moldcraft/8116528)

PS People attempting to install ATI driver 13.12 onto 3.11 kernel will have to extract the driver archive and edit the extracted file at catalyst/common/lib/modules/fglrx/build_mod/kcl_acpi.c instead, as detailed in the github.com URL above.

---

### Post by Bashing-om on 2014-03-03
fig_wright; WOW !

Now that is some good trouble shooting on your part ! Thanks for sharing that solution .

Once more affirmation that when there is a problem, linux will tell you, bleeding hints all over !

[INDENT][INDENT]look
[INDENT][INDENT]and ye shall find
[/INDENT][/INDENT][/INDENT][/INDENT]

---

