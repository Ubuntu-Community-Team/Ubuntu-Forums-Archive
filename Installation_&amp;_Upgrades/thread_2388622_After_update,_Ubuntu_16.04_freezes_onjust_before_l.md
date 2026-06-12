---
title: "After update, Ubuntu 16.04 freezes on/just before login screen"
date: 2018-04-05
forum: Installation &amp; Upgrades
---

### Post by mkunz.bgc on 2018-04-05
**The initial problem**
I have a Thinkpad P51 with an Intel Core i7 that runs Ubuntu 16.04.. Two days ago (3 April) I installed a bunch of updates via the Ubuntu Software Center. After the update, a reboot was due. However, the system did not reach the login screen again - it froze just before the login screen would appear. The freeze was so complete that not even the Magic Sysreq was doing anything; turning the computer on and off again was the only option.

[B]What I tried so far
[/B]I tried booting into older kernels. While my latest kernel  (4.13.0-38-generic) froze repeatedly, older kernels like  4.13.0-37-generic still booted normally.One of my first guesses was that this issue is related to the Nvidia drivers, so I first tried booting 4.13.0-38-generic with the kernel option "nomodeswitch" and later switching to nouveau (using 'apt-get remove nvidia-384' under 4.13.0-37-generic). Neither helped, booting 4.13.0-38-generic ended in a freeze. At some point, also 4.13.0-37 started to freeze during boot and I was left with only 4.4.0-116-generic still booting. I tried dpkg-reconfigure on linux-signed-image-4.13.0-37-generic, but this did not make it 4.13.0-37-generic boot again.
I checked my root partition (a logical volume on a LUKS-encrypted partition on an SSD) and my home partition (a logical volume on a LUKS-encrypted partition on a hard disk) from a thumbdrive with Ubuntu 16.04 using fsck, which did not report any errors. Also, I used the Lenovo-hardware diagnostics (built into EFI), which did not find problems with the CPU, memory or graphics card.
About that time I read a little more and found a way to look up the recently installed packages ([here]("https://askubuntu.com/questions/34888/is-there-any-way-to-roll-back-the-most-recent-upgrade")) - see List of updates below.

**An important clue?**
When the system freezes, the fan gets somewhat louder, so I think that either the CPU or GPU are busy (however, the disk activity LED is permanently off when the system is frozen). I noticed that new CPU firmware was installed during the problematic update, so I tried switching back from intel-microcode version 3.20180312.0~ubuntu16.03.1 to version 3.20151106.1. This enabled me to start 4.13.0-37-generic again, so I thought I was close to a solution! However, after trying a dpkg-reconfigure with the 4.13.0-38-generic files all my kernels started to freeze just before or when bringing up the login screen (sometimes I am left with the Ubuntu logo and some no-longer-animated dots, sometimes I see a mouse pointer on a black screen and sometimes I see the login screen, but everything is frozen and not even Magic Sysreq helps).

**How I can access the system now**
[LIST=1]
[*]Rescue console does not work with any kernel, I am left with a black screen before I even get a chance to decrypt my disks (one for root, one for home, encrypted using LUKS).
[*]Booting with the kernel option "text" works, I reach the emergency console.
[*]Booting a thumb drive with Ubuntu 16.04.03 works and I can decrypt and chroot to my root partition.
[/LIST]

[B]My request
[/B]Do you have any suggestions what I could try to identify the cause of the trouble and get the system running again? Of course, there is the option to reinstall Ubuntu and I know that I would keep all the files under home. Still, the system is configured in a non-trivial way regarding integration to an institute network and if possible I would avoid repeating this effort.



[I]List of updates
[/I](Most, but not all of these entries are from the update after which the freezing issue started. If I remember correctly, the nvidia* and linux-signed-image-4.13.0-37-generic packages are due to my first attempts of solving the problem, while all the other packages were automatically installed on 3 April.)

```
thunderbird-locale-en-gb
thunderbird-locale-en-us
libmono-data-tds4.0-cil
intel-microcode
nvidia-384
libmono-system-identitymodel-selectors4.0-cil
libmono-system-web-dynamicdata4.0-cil
linux-image-4.13.0-38-generic
ca-certificates-mono
chromium-codecs-ffmpeg-extra
libmono-system-web-extensions-design4.0-cil
initramfs-tools
libmono-system-web-http4.0-cil
libmono-system-messaging4.0-cil
initramfs-tools-core
initramfs-tools-bin
libmono-system-web-http-selfhost4.0-cil
libplymouth4:amd64
plymouth-theme-ubuntu-text
linux-signed-image-4.13.0-37-generic
plymouth
nvidia-opencl-icd-384
plymouth-theme-ubuntu-logo
plymouth-label
libraw15:amd64
linux-image-extra-4.13.0-38-generic
linux-generic-hwe-16.04
linux-image-generic-hwe-16.04
mono-complete
libssl-doc
libmono-system-servicemodel4.0a-cil
libmono-db2-1.0-cil
mono-devel
linux-signed-image-4.13.0-38-generic
libmono-system-web-http-webhost4.0-cil
libmono-sqlite4.0-cil
libmono-cil-dev
libmono-system-servicemodel-activation4.0-cil
libmono-system-componentmodel-dataannotations4.0-cil
libmono-system-xml4.0-cil
libmono-system-web-mobile4.0-cil
libmono-system-web-extensions4.0-cil
libmono-system-drawing4.0-cil
libmono-system4.0-cil
libssl-dev:amd64
libmono-system-runtime-serialization-formatters-soap4.0-cil
libmono-security4.0-cil
libmono-system-servicemodel-web4.0-cil
libmono-system-web-applicationservices4.0-cil
libmono-system-web-razor2.0-cil
libmono-system-security4.0-cil
libmono-system-data-services4.0-cil
libmono-system-configuration4.0-cil
libmono-webbrowser4.0-cil
libmono-posix4.0-cil
libmono-system-web-webpages-deployment2.0-cil
libmono-system-deployment4.0-cil
libmono-i18n4.0-cil
libmono-system-core4.0-cil
libicu-dev:amd64
libmono-system-drawing-design4.0-cil
linux-signed-generic-hwe-16.04
libmono-system-io-compression4.0-cil
libmono-i18n4.0-all
libmono-system-web-webpages2.0-cil
libmono-microsoft-build-framework4.0-cil
libmono-system-dynamic4.0-cil
libmono-i18n-cjk4.0-cil
libmono-microsoft-build-utilities-v4.0-4.0-cil
libmono-system-web-webpages-razor2.0-cil
libssl1.0.0:amd64
libmono-microsoft-build-engine4.0-cil
libmono-i18n-mideast4.0-cil
libmono-system-io-compression-filesystem4.0-cil
libmono-xbuild-tasks4.0-cil
libmono-i18n-other4.0-cil
libmono-system-web-mvc3.0-cil
libmono-microsoft-build-tasks-v4.0-4.0-cil
libmono-system-json4.0-cil
linux-signed-image-generic-hwe-16.04
libmono-system-transactions4.0-cil
libmono-i18n-rare4.0-cil
icu-devtools
libmono-system-enterpriseservices4.0-cil
libmono-system-web-regularexpressions4.0-cil
libmono-i18n-west4.0-cil
libmono-system-json-microsoft4.0-cil
libmono-system-numerics4.0-cil
libmono-system-data4.0-cil
libmono-system-windows-forms4.0-cil
linux-headers-4.13.0-38
libmono-system-servicemodel-internals0.0-cil
libmono-system-ldap-protocols4.0-cil
libmono-system-web-routing4.0-cil
libmono-system-design4.0-cil
libmono-system-runtime-serialization4.0-cil
libicu55:amd64
libmono-system-xml-linq4.0-cil
libmono-ldap4.0-cil
libmono-system-management4.0-cil
mono-xbuild
libmono-system-ldap4.0-cil
libmono-system-windows4.0-cil
mono-roslyn
libmono-system-net4.0-cil
mono-utils
libmono-system-web-services4.0-cil
pciutils
libmonoboehm-2.0-1
libmono-system-web4.0-cil
libmono-system-net-http4.0-cil
libmono-system-windows-forms-datavisualization4.0a-cil
libmono-microsoft-csharp4.0-cil
libmono-http4.0-cil
mono-mcs
libpci3:amd64
libmono-system-net-http-formatting4.0-cil
libmono-corlib4.5-cil
libmono-management4.0-cil
libmono-accessibility4.0-cil
libmono-system-workflow-activities4.0-cil
lshw
libmono-messaging4.0-cil
libmono-system-net-http-webrequest4.0-cil
libmono-cairo4.0-cil
libmono-debugger-soft4.0a-cil
libmono-rabbitmq4.0-cil
libmono-sharpzip4.84-cil
libmono-system-numerics-vectors4.0-cil
libmono-system-workflow-componentmodel4.0-cil
libmono-messaging-rabbitmq4.0-cil
monodoc-base
libmono-codecontracts4.0-cil
openssl
libmono-microsoft-build4.0-cil
libmono-system-reactive-interfaces2.2-cil
libmono-cecil-private-cil
libmono-microsoft-visualc10.0-cil
libmono-system-workflow-runtime4.0-cil
libmono-compilerservices-symbolwriter4.0-cil
libmono-system-reactive-core2.2-cil
libmono-microsoft-web-infrastructure1.0-cil
libmono-cscompmgd0.0-cil
libmono-system-xml-serialization4.0-cil
libmono-system-reactive-linq2.2-cil
libmono-oracle4.0-cil
libmono-csharp4.0c-cil
libmono-webmatrix-data4.0-cil
libmono-system-reactive-debugger2.2-cil
firefox-esr
libmono-btls-interface4.0-cil
libmono-parallel4.0-cil
libmono-custommarshalers4.0-cil
libmono-system-reactive-experimental2.2-cil
libmono-tasklets4.0-cil
libmono-peapi4.0a-cil
libtiff5-dev:amd64
libmono-system-reactive-providers2.2-cil
libmono-relaxng4.0-cil
mono-runtime
libmono-simd4.0-cil
libmono-system-reactive-observable-aliases0.0-cil
libtiffxx5:amd64
mono-runtime-sgen
libmono-smdiagnostics0.0-cil
libmono-system-reactive-platformservices2.2-cil
libmono-system-componentmodel-composition4.0-cil
libmono-system-reactive-runtime-remoting2.2-cil
libtiff5:amd64
libmono-system-configuration-install4.0-cil
libtiff-tools
libmono-system-reactive-windows-forms2.2-cil
mono-runtime-common
libmono-system-data-datasetextensions4.0-cil
libmono-system-xaml4.0-cil
ocqt562+240-libqt5core5a:amd64
mono-gac
libmono-system-data-entity4.0-cil
libmono-windowsbase4.0-cil
libmono-system-data-linq4.0-cil
mono-4.0-gac
libmono-system-data-services-client4.0-cil
libmono-system-reactive-windows-threading2.2-cil
ocqt562+240-libqt5dbus5:amd64
libmono-2.0-dev
libmono-system-identitymodel4.0-cil
libmono-system-reflection-context4.0-cil
ocqt562+240-libqt5network5:amd64
libmonosgen-2.0-dev
libmono-system-runtime4.0-cil
libmono-2.0-1
libmono-system-runtime-caching4.0-cil
ocqt562+240-libqt5gui5:amd64
libmono-system-runtime-durableinstancing4.0-cil
libmonosgen-2.0-1
libmono-system-servicemodel-discovery4.0-cil
ocqt562+240-libqt5keychain1
libmono-system-servicemodel-routing4.0-cil
libmono-profiler
libmono-system-serviceprocess4.0-cil
mono-jay
ocqt562+240-libqt5widgets5:amd64
libmono-system-threading-tasks-dataflow4.0-cil
mono-csharp-shell
libmono-system-web-abstractions4.0-cil
ocqt562+240-libqt5printsupport5:amd64
mono-4.0-service
monodoc-manual
ocqt562+240-libqt5sql5:amd64
ocqt562+240-libqt5sql5-sqlite:amd64
ocqt562+240-libqt5xml5:amd64
openjdk-8-jdk:amd64
openjdk-8-jdk-headless:amd64
openjdk-8-jre:amd64
openjdk-8-jre-headless:amd64
screen-resolution-extra
thunderbird-locale-en
linux-headers-4.13.0-38-generic
thunderbird
linux-headers-generic-hwe-16.04
thunderbird-gnome-support
python-crypto 
```

---

### Post by dga2 on 2018-04-06
I've had almost the same problem and it started at about the same time (about 3 days ago maybe). The main differences are that for me 4.4.0-112-generic is the most recent kernel to work. 4.4.0-116-generic and 4.4.0-119-generic both freeze at or just before the login. Also, for me the grub entries containing '(upstart)' and '(recovery mode)' both work. I assume that when you say that the rescue console doesn't work, you mean the option containing '(recovery mode)' doesn't let you get into a root terminal.

Initially, changing the login manager from lightdm to sddm fixed the problem. I did this using the command (in the root recovery mode):

```
dpkg-reconfigure sddm
```

and then selected sddm instead of lightdm.

But, alas, I ran some more updates today (firefox and firefox-locale-en) and now even sddm freezes. With sddm it freezes with a blank screen except for a frozen cursor at the top left and with lightdm it freezes with a blank screen except for a frozen mouse pointer in the middle.

My workaround now is to boot into terminal mode and then start the login manager manually. It's a pain but at least I get in. Here's what I did in case it is any help:

1. I updated /etc/default/grub to take out the 'quiet splash' and include the following lines:

```
GRUB_CMDLINE_LINUX="3"
GRUB_TERMINAL=console

```

Altogether, the file has these contents:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="3"
#GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=800x600x32
#GRUB_GFXPAYLOAD=keep


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

Then I ran update-grub.

```
update-grub
```

2. Now it boots into a terminal although it froze once here too. To get the graphical environment going, each time I have to log in to the console, then issue the command

```
sudo service lightdm start

``` 

and then the login manager comes up and I have to login yet again.

It's a pain in the neck. I have an older laptop with the exact same configuration and it has no problems. 

Anyway, I hope this is of some help and I wish you luck in finding a solution.

David

---

### Post by mkunz.bgc on 2018-04-08
Thanks for your input, David!
> **dga2 said:**
>  I assume that when you say that the rescue console doesn't work, you mean the option containing '(recovery mode)' doesn't let you get into a root terminal.

Yes, that's exactly what I mean.

My system is now booting reliably again, without a clear indication of what was wrong. What I did was booting into the emergency console using the kernel option "text", manually setting up my internet connection and then as root performing (typed from memory, might contain errors)
```
apt-get update
dpkg --configure -a
apt-get install -f
apt-get install --reinstall nvidia-384
apt-get install --reinstall plymouth

```.

Plymouth, which was broken before these actions, did not work properly afterwards (i.e. every other boot hung at an early stage, but a restart with Ctrl+Alt+Del worked). Since I disabled plymouth via GRUB, every boot was successfull.
Both 'dpkg --configure -a' and 'apt-get install -f' returned quickly and did not produce output that looked like any problems had been detected.This leaves the reinstallation of the nvidia drivers as the most likely reason for the cure - which is strange, as I had tried that before without success.

Well, let's see whether the problem comes back.

---

### Post by mkunz.bgc on 2018-05-08
After weeks of daily use without problems, the freezing is occuring again. This time, I did not install any updates before the problem came up. After switching from dedicated graphics to internal graphics using the Nvidia Settings Manager I tried to log out, which left me with a working mouse cursor on blank background. I switched to the text console and tried to reboot using shutdown, but this did not work because of a problem with systemd-sleep. Hence I had to do an emergency sync using SysRq+S. After that I turned off the laptop by pressing the power button for sevetal seconds. Since that point my system freezes whenever it brings up the login screen after booting.

Things that I tried but did not help:
[LIST=1]
[*]The steps listed in #3
[*]Uninstalling the Nvidia drivers and related software (Prime, Settings)
[*]Installing nvidia-396 from the graphics-drivers ppa
[*]Booting with "Dedicated graphics" selected in the BIOS instead of "Hybrid graphics"
[*]Reinstalling Xorg as described [here]("https://www.computersnyou.com/4945/re-install-xorg-xserver-completely-ubuntu/").
[/LIST]

Any ideas what else I could do?

---

