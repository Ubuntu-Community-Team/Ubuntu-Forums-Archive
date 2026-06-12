---
title: "[SOLVED]Ubuntu default plymouth don't works after upgrade(LTSEnablementStack)."
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by hectorsales on 2015-03-27
Hello I have upgrade recently from Ubuntu version 14.04.1 to 14.04.2 version( **LTSEnablementStack**)... and everything was Ok .. except for one small detail, if i boot with the kernel series 3.16.x the default ubuntu plymouth theme don't appears .. however if I starter with the kernel series 3.13.x this if it appears...I try this:


```
~$ sudo update-alternatives --config default.plymouth
```

> 
There are 2 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                           Priority   Status
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth           100       auto mode
  1            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo-scale-2.plymouth   99        manual mode
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth           100       manual mode

Press enter to keep the current choice
[*], or type selection number:
 


**I press enter ...after:**


```
~$ sudo update-initramfs -u
```

> update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic

Finally:

```
~$ sudo reboot
```

 ....but unfortunately this does not work for me

**Note:** I have radeonsi(Bonaire XTX [Radeon R7 260X]) and mesa stack 10.3.2.** If I boot with the kernel series 3.13.x the ubuntu default plymouth theme works ..**

Any suggestion ..please.

**Edit:** Sorry .. I think it's a bug on ubuntu's plymouth package:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707)

Regards.

---

### Post by dcharlespyle on 2015-03-28
I can confirm the same behavior when running a 3.16 kernel in 14.04.2 LTS.  (My current kernel version is 3.16.0-34.)  Following is the workaround I used to get plymouth's startup screen to display during booting.  I am running 14.04.2 in a Wubi install, so if you aren't running in a Wubi install and/or never migrated a Wubi install to a standard install, you likely will not have one of the files to be corrected in what I am about to write.

1.  Run ```
gksu gedit /etc/grub.d/10_linux
```

2.  Modify the line ```
vt_handoff="1"
``` to ```
vt_handoff="0"
```

3.  Save the file.  (If you are running in a Wubi installation or still have the 10_lupin file in /etc/grub.d, continue to the next step.  If you aren't and never have, skip to step 7 unless the 10_lupin file is present).

4.  Run ```
gksu gedit /etc/grub.d/10_lupin
```

5.  Modify the file by commenting out the following lines:

```
[COLOR=#333333][FONT=monospace]for word in $GRUB_CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT; do[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] if [ "$word" = splash ]; then[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  GRUB_CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]"$GRUB_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT \$vt_handoff"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] fi[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]done[/FONT][/COLOR]
```

like so:

```
[COLOR=#333333][FONT=monospace]#for word in $GRUB_CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT; do[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# if [ "$word" = splash ]; then[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]#  GRUB_CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]"$GRUB_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT \$vt_handoff"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# fi[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]#done[/FONT][/COLOR]
```

6.  Save the file.

7.  Run in a terminal ```
sudo update-grub
```

8.  Reboot.

That should be all that needs to be done if the plymouth splash screen was working for you before installing the LTSEnablementStack upgrade and with it a 3.16 kernel.  For some, they might need to run a fixplymouth script as well.  You can find those on the internet.

---

### Post by hectorsales on 2015-03-30
Yeah.. dcharlespyle, your workaround works find here:

 
```
~$ sudo nano /etc/grub.d/10_linux
```

> 

.....................................................
.....................................................

prefix="/usr"
exec_prefix="/usr"
datarootdir="/usr/share"
ubuntu_recovery="1"
quiet_boot="1"
quick_boot="1"
gfxpayload_dynamic="1"
**vt_handoff="0"**




**... after:**

```

~$ sudo update-grub2

~$ sudo reboot

```


Thanks so much !!!.

---

