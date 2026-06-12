---
title: "Installing AMD Catalyst 13.12"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by Raymond_Beltran on 2014-02-21
here is the log 
> 
Supported adapter detected.
Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Dryrun uninstall succeeded continuing with installation.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.11.0-17-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-17-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c: In function &#8216;KCL_ACPI_ParseTable&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c:999:5: warning: passing argument 1 of &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217; makes integer from pointer without a cast [enabled by default]
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c:999:5: note: expected &#8216;u32&#8217; but argument is of type &#8216;struct acpi_table_header *&#8217;
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217;
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-17-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
[Reboot] Kernel Module : update-initramfs


What seems to be the problem sir im kinda new so im not that good in reading just need a right explaination for this.

---

### Post by Bashing-om on 2014-02-22
Raymond_Beltran;

We need to know what it is we are working with:
post the output - between code tags - of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
To see your graphics card and info.


code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Better advise depends on
[INDENT][INDENT]better info
[/INDENT][/INDENT]

---

### Post by Raymond_Beltran on 2014-02-23
> **Bashing-om said:**
> Raymond_Beltran;

We need to know what it is we are working with:
post the output - between code tags - of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
To see your graphics card and info.


code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Better advise depends on[INDENT][INDENT]better info
[/INDENT]
[/INDENT]


sudo lshw -C display

```
  *-display UNCLAIMED            description: VGA compatible controller
       product: Pitcairn
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fdd80000-fddbffff ioport:ee00(size=256) memory:fdd00000-fdd1ffff

```[COLOR=#000000]


[/COLOR]
lspci -nnk | grep -iA3 vga

```

Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn [1002:6810]
    Subsystem: PC Partner Limited / Sapphire Technology Device [174b:e271]
    Kernel modules: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]




```

---

### Post by Bashing-om on 2014-02-26
Raymond_Beltran; Hey !

Sorry to have left ya high and dry. I have lost my internet connectivity and am working to find a solution.

As soon as I can I will return to this. Perhaps others in the meantime will pick up my slack.

Those things !

[INDENT][INDENT]that are beyond our control
[/INDENT][/INDENT]

---

### Post by an-sharma on 2014-02-26
I'm in the same boat, same exact error. Running an R9 270, which shows up as a Pitcairn Radeon 7700/7800 series when I use the "lspci -nnk | grep -iA3 vga" command.

---

### Post by Bashing-om on 2014-02-27
Raymond_Beltran & an-sharma;

A quick look at some bug reports seems to indicate that the package "psensors" must be installed.
see:
[http://wpitchoune.net/psensor/doc/faq.html](http://wpitchoune.net/psensor/doc/faq.html)
[http://wpitchoune.net/blog/psensor/ubuntu-integration/](http://wpitchoune.net/blog/psensor/ubuntu-integration/)

Might be worth a shot, and I do not see how installing "psensor" could hurt.
Other reports indicate to update BIOS.

[INDENT][INDENT]try'n to help
[/INDENT][/INDENT]

---

### Post by Raymond_Beltran on 2014-03-12
> **an-sharma said:**
> I'm in the same boat, same exact error. Running an R9 270, which shows up as a Pitcairn Radeon 7700/7800 series when I use the "lspci -nnk | grep -iA3 vga" command.

did you find any solution?


> **Bashing-om said:**
> Raymond_Beltran & an-sharma;

A quick look at some bug reports seems to indicate that the package "psensors" must be installed.
see:
[http://wpitchoune.net/psensor/doc/faq.html](http://wpitchoune.net/psensor/doc/faq.html)
[http://wpitchoune.net/blog/psensor/ubuntu-integration/](http://wpitchoune.net/blog/psensor/ubuntu-integration/)

Might be worth a shot, and I do not see how installing "psensor" could hurt.
Other reports indicate to update BIOS.[INDENT][INDENT]try'n to help
[/INDENT]
[/INDENT]

installing ps sensors still this shows up


> Supported adapter detected.Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Dryrun uninstall succeeded continuing with installation.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.11.0-17-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-17-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c: In function &#8216;KCL_ACPI_ParseTable&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c:999:5: warning: passing argument 1 of &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217; makes integer from pointer without a cast [enabled by default]
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c:999:5: note: expected &#8216;u32&#8217; but argument is of type &#8216;struct acpi_table_header *&#8217;
/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217;
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-17-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
[Reboot] Kernel Module : update-initramfs



---

### Post by spectatorx on 2014-03-12
I think you should try to install drivers following this guide here:
<snip>


And for r7/r9 gpus i would suggest installing latest driver which is 14.2 beta v1.3.

---

### Post by QIII on 2014-03-12
@spectatorx

I've snipped the url from your post because the blogger advocates piracy.  We do not.

I did review the instructions, which are themselves good and a standard approach.

Suggest you copy and paste them, after editing them for what is common knowledge and what is the blogger's added content.

---

### Post by spectatorx on 2014-03-13
Hm... weird, i think i've never spotted in there anything about piracy, but if you say so i won't argue with you.

I will just copy-paste this article here:

> 

So&#8230; how to install AMD Catalyst driver? Here we go:

1. Before we start it is needed to install updates. Install all available updates for your Ubuntu and reboot computer (if needed).

2. After reboot open terminal and paste (ctrl+shift+v) this line:

sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic lib32gcc1

hit enter and follow instructions, if any will show up.

3. Next step is to download driver. Save file in /home folder. This is very important to keep downloaded file in this folder, it will make many things much easier. If downloaded file is .zip unpack it, if downloaded file is .run go to another step.

4. Default file name is pretty long and complicated, make it simpler and rename it to, for example catalyst.run.

5. Here comes first part of installation: open terminal, paste line:

sudo sh ./catalyst.run --buildpkg Ubuntu/quantal

In the end of line you can see phrase &#8220;Ubuntu/quantal&#8221;. Ubuntu stands for name of Linux distribution, quantal stands for version of Ubuntu. quantal is Ubuntu 12.10, precise &#8211; 12.04, oneiric &#8211; 11.10, raring &#8211; 13.04, saucy - 13.10, trusty - 14.04.

This step creates installable .deb packages of driver and saves them in your /home directory. This process can take even few minutes.

6. Great! Packages are created and now you have to install them. There are two ways to do so. With one command line or with manual installing packages. Both are simple.

Command line? Paste this line into terminal:

sudo dpkg -i fglrx*.deb

Manual? Go to /home folder and open .deb packages and install them, one after another.

7. Reboot computer and check if everything runs fine.

All this I can short into one sentence: download driver, if needed unpack, create packages for ubuntu and install them, reboot. Simple as that.

Now your drivers are installed! It is not so difficult, isn&#8217;t it?  I hope this little instruction will help to many of you.

If you installed beta driver you may have visible on desktop watermark with message &#8220;AMD Testing use only&#8221;.

Install steam and download some nice games  Or just use Ubuntu Software Center to try some games.

Tested on Ubuntu 12.10 amd64 and Radeon HD6850 with AMD Catalyst 13.2 Beta 3 for linux.



---

### Post by Raymond_Beltran on 2014-03-14
> **spectatorx said:**
> Hm... weird, i think i've never spotted in there anything about piracy, but if you say so i won't argue with you.

I will just copy-paste this article here:


it still wont work T_T

---

### Post by ahaugis on 2014-06-12
Hi
Don't know if after this time help is still needed, but here goes. You might have compatibility issiues with the 3.11 kernel. The instructions on this page fixed it for me: [https://gist.github.com/moldcraft/8116528](https://gist.github.com/moldcraft/8116528)
Hope it helps!

---

