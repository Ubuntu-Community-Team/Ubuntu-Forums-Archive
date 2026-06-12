---
title: "kernel 5.4.0-96 just installed, but 5.4.0-94 still being used"
date: 2022-01-19
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2022-01-19
Usually when the updates include a new kernel, that kernel becomes operative upon re-boot.  

Today I updated from kernel 5.4.0-94-generic to 5.4.0-96-generic. 
Both are installed, but -94 is still the operative kernel.

[I]--> dpkg -l linux-image-\* linux-headers-\* linux-modules-\*

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version      Architecture Description
+++-=====================================-============-============-====
un  linux-headers-3.0                     <none>       <none>       (no description available)
ii  linux-headers-5.4.0-94                5.4.0-94.106 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-94-generic        5.4.0-94.106 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-96                5.4.0-96.109 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-96-generic        5.4.0-96.109 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
un  linux-headers-686-pae                 <none>       <none>       (no description available)
un  linux-headers-amd64                   <none>       <none>       (no description available)
ii  linux-headers-generic                 5.4.0.96.100 amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-94-generic          5.4.0-94.106 amd64        Signed kernel image generic
ii  linux-image-5.4.0-96-generic          5.4.0-96.109 amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.96.100 amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-94-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-96-generic <none>       <none>       (no description available)
ii  linux-modules-5.4.0-94-generic        5.4.0-94.106 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-96-generic        5.4.0-96.109 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-94-generic  5.4.0-94.106 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-96-generic  5.4.0-96.109 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
```
[/I]
What might have caused -96 to not be the currently operative kernel?  And is there a simple command to make -96 operative?

A separate question:  
What is the difference between a kernel (or any other software package) being installed manually as opposed to being "auto-installed"?

---

### Post by Impavidus on 2022-01-19
When installing (or removing) a kernel, a script runs to update the bootloader, which will make the new kernel the default. If the script fails (most commonly due to lack of disk space), the packages are not marked as fully installed, but on your computer they clearly are. You can run that script manually with```
sudo update-grub
```Maybe you have some non-standard configuration in your /etc/default/grub or maybe this system is not in charge of grub. Have you installed two Linux systems, dual booting them?

Installed packages can be marked as manually or automatically installed. The automatically installed packages become autoremovable when no other packages depend on them. But for kernels some special magic is going on, to make sure that one old kernel is not autoremovable, but the older kernels are.

---

### Post by watchpocket on 2022-01-19
> **Impavidus said:**
> You can run that script manually with ```
sudo update-grub
``` 

I've just done the update, no change. 

 [***EDIT:***  *I just now did *`sudo update-grub`[I] on my **other** install (the one that's in charge of GRUB) and that caused the kernel on **this** system to upgrade from 5.4.0-94 to 5.4.0-96.  [B]Problem solved.]
[/B][/I]
> Maybe you have some non-standard configuration in your /etc/default/grub 

I myself cannot identify anything that looks weird here, maybe someone else can:
```
1 # If you change this file, run 'update-grub' afterwards to update                                                                                                                    
  2 # /boot/grub/grub.cfg.
  3 # For full documentation of the options in this file, see:
  4 #   info -f grub -n 'Simple configuration'
  5  
  6 GRUB_DEFAULT=0
  7 GRUB_TIMEOUT_STYLE=menu
  8 GRUB_TIMEOUT=10
  9 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 10 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 11 GRUB_CMDLINE_LINUX=""
 12  
 13 # Uncomment to enable BadRAM filtering, modify to suit your needs
 14 # This works with Linux (no patch required) and with any kernel that obtains
 15 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
 16 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 17  
 18 # Uncomment to disable graphical terminal (grub-pc only)
 19 #GRUB_TERMINAL=console
 20  
 21 # The resolution used on graphical terminal
 22 # note that you can use only modes which your graphic card supports via VBE
 23 # you can see them in real GRUB with the command `vbeinfo'
 24 #GRUB_GFXMODE=640x480
 25  
 26 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
 27 #GRUB_DISABLE_LINUX_UUID=true
 28  
 29 # Uncomment to disable generation of recovery mode menu entries
 30 #GRUB_DISABLE_RECOVERY="true"
 31  
 32 # Uncomment to get a beep at grub start
 33 #GRUB_INIT_TUNE="480 440 1"
 34 GRUB_DISABLE_OS_PROBER=false
```


> or maybe this system is not in charge of grub. 

That's it.  I think the 20.04.3 system that's on my other drive (nvme0) is in charge of GRUB.
Yesterday, the update from 5.4.0-94 to -96 went fine on that system.

> Have you installed two Linux systems, dual booting them? 

Yes, that's it exactly.  This drive (the one where the kernel didn't upgrade) is on an SSD (/dev/sda).

---

### Post by Bashing-om on 2022-01-19
watchpocket' Hello =

I too multi-boot and in the past I too have encountered grub inconsistencies due to recursions in the boot config file.
As I am of the opinion - there can be only one - in charge of what is selected to boot - I disable os_prober in all the secondary systems; such then it is my primary system that is not only able to boot the primary but also any secondary system. In the event there is a problem booting the primary system one can select in bios the alternate drive to boot.

[INDENT]just my 2 cents
[/INDENT]

---

### Post by watchpocket on 2022-01-20
> **Bashing-om said:**
>  I disable os_prober in all the secondary systems; such then it is my primary system that is not only able to boot the primary but also any secondary system. 

In my secondary system's /etc/default/grub file, The last line is:
GRUB_DISABLE_OS_PROBER=false

(In my ***main*** system's /etc/default/grub, there is nothing there about os_prober one way or the other, 
thus it would be set there to whatever its default is.)

So: os_prober is activated on the secondary system (where the kernel wasn't updating until I updated grub), but I now am having no identifiable problem with that - the kernel is updated.
 
I did a *sudo update_grub* on my main system (where grub was in control), and that enabled the secondary to update its kernel from 5.4.0-94 to 5.4.0-96.  (Which was the problem I was having yesterday.)

Are you saying that I'd be beter off -- for various reasons -- with os_prober disabled?

---

### Post by ajgreeny on 2022-01-20
I have exactly the same problem with my dual boot system with 20.04 and 22.04 (correction: not really a problem but a bit annoying) with 22.04, being the last installed OS having taken over grub.

In my /etc/default/grub file I have set ***GRUB_DEFAULT=2*** meaning the main 20.04 boots by default but to make sure I get the latest kernel version in that I must run ***sudo update-grub*** in 22.04 each time there is a new kernel version in 20.04.

I imagine there must be a way to make 20.04 manage grub instead of 22.04 but nothing I have tried so far has achieved this for me, eg running the command 
```
sudo grub install /dev/sda
``` from the 20.04 system.

---

### Post by Bashing-om on 2022-01-20
My solution is to disable the 'x' bit on my secondary installs:
```

sudo chmod -x /etc/grub.d/30_os-prober

```

Then each time that the secondary systems' grubs gets updated one only has to:
```

sudo upddate-grub

```
in the primary system to pick up the changes.

[INDENT]many paths to one end
[/INDENT]

---

### Post by watchpocket on 2022-01-21
Hello Bashing-om -- Not sure but It seems I may not need to do that, since I did update grub from the primary system, and that caused the kernel to update on the 2nd system.  And my os_prober file looks like this (x-bit enabled):

12 -rwxr-xr-x 1 root root 12059 Oct  3 23:11 30_os-prober*

---

### Post by Bashing-om on 2022-01-21
watchpocket; Hey :)

If it works for you -
Do not fix it :P

The Xecute bit will be set in your primary grub directory, thus os-prober polls the secondary installs.

[INDENT]one way
[INDENT][INDENT]the other way
any way better than no way
[/INDENT][/INDENT][/INDENT]

---

