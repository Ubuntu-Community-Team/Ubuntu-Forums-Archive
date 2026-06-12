---
title: "No &quot;Recovery&quot; items in GRUB boot-menu"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by TroublemakerDV on 2013-01-19
XU12.10 with all latest updates. Fresh install. grub-update (or whatever) was launched many times because of kernel upgrades.

Linux my-host **3.5.0-22-generic #34**-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

 **grub-pc                2.00-7ubuntu11   amd64**

No "recovery mode" items in boot menu, although:

GRUB_DISABLE_RECOVERY="**false**"

is uncommented in /etc/default/grub.
I can't guess what's wrong. Any suggestions please?

---

### Post by dino99 on 2013-01-20
on a single OS system installation, the grub menu is hidden by default. To see it, hit "shift" key down at bios end process. Then pick up the second line to boot in recovery mode.

---

### Post by Elfy on 2013-01-20
Recovery mode is in the Advanced menu under the normal kernel option I believe.

---

### Post by TroublemakerDV on 2013-01-20
> **Elfy said:**
> Recovery mode is in the Advanced menu under the normal kernel option I believe.
Can I check it without reboot? grub.cfg contains no word of "advanced"

---

### Post by TroublemakerDV on 2013-01-20
> **dino99 said:**
> on a single OS system installation, the grub menu is hidden by default. To see it, hit "shift" key down at bios end process. Then pick up the second line to boot in recovery mode.
Sorry, but I did not asked how to display the menu, and I did not said a word about single OS, because I see the menu and have multi-OS install: XU12.10/32 and /64, amongst with two different WXP installs.

---

### Post by Elfy on 2013-01-20
> **TroublemakerDV said:**
> Can I check it without reboot? grub.cfg contains no word of "advanced"

```
cat /boot/grub/grub.cfg |grep menuentry
```

Will show you all the menu entries

Look in the sub-menu and you should see similar to 

```
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-69807907-dc94-48ba-b03b-35f433d8e584' {
	menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-69807907-dc94-48ba-b03b-35f433d8e584' {
	menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-[COLOR="Red"]recovery[/COLOR]-69807907-dc94-48ba-b03b-35f433d8e584' {
```

---

### Post by TroublemakerDV on 2013-01-20
> **Elfy said:**
> ```
cat /boot/grub/grub.cfg |grep menuentry
```Will show you all the menu entries
Alas!

```
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry "Ubuntu /64" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-920de3a2-af24-4507-bf80-300a3c2ac881' {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Microsoft Windows XP Professional (&#1085;&#1072; /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-chain-4754-6E11' {
menuentry "Ubuntu 12.10 (12.10) /32" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
menuentry "Microsoft Windows XP Professional (&#1085;&#1072; /dev/sdb1)" --class windows --class os $menuentry_id_option 'osprober-chain-4754-6E11' {
```

What else should I check or copy here?

---

### Post by Elfy on 2013-01-20
> **TroublemakerDV said:**
> ...
 GRUB_DISABLE_RECOVERY="false"
is uncommented in /etc/default/grub.
I can't guess what's wrong. Any suggestions please?

My grub config file in /etc/default is 

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

You could try changing your grub disable recovery line to the same or just put # at the beginning of the line

Backup and edit the file, then save changes

```
sudo cp /etc/default/grub /etc/default/grub.200113 && gksudo gedit /etc/default/grub
``` 

then update and see if you get recovery options

```
 sudo update-grub && cat /boot/grub/grub.cfg |grep recovery
```

---

### Post by TroublemakerDV on 2013-01-20
> **Elfy said:**
> My grub config file in /etc/default is 

```

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

```You could try changing your grub disable recovery line to the same or just put # at the beginning of the line

I tried your suggestions. No luck.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="noquiet nosplash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

GRUB_TERMINAL_INPUT="at_keyboard"
GRUB_BACKGROUND_IMAGE="/boot/grub/&#1089;&#1090;&#1077;&#1082;&#1083;&#1091;&#1073;&#1091;&#1085;&#1090;&#1091;.png"
```
```
$ sudo update-grub && cat /boot/grub/grub.cfg |grep recovery
[sudo] password for you: 
&#1043;&#1077;&#1085;&#1077;&#1088;&#1080;&#1088;&#1091;&#1077;&#1090;&#1089;&#1103; grub.cfg …
Found background image: &#1089;&#1090;&#1077;&#1082;&#1083;&#1091;&#1073;&#1091;&#1085;&#1090;&#1091;.png
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; linux: /boot/vmlinuz-3.5.0-22-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; initrd: /boot/initrd.img-3.5.0-22-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; linux: /boot/vmlinuz-3.5.0-21-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; initrd: /boot/initrd.img-3.5.0-21-generic
Found memtest86+ image: /boot/memtest86+.bin
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; Microsoft Windows XP Professional &#1085;&#1072; /dev/sda1
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; Ubuntu 12.10 (12.10) &#1085;&#1072; /dev/sda8
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; Microsoft Windows XP Professional &#1085;&#1072; /dev/sdb1
done

```grep could not find any "recovery" again. Search for "menuentry" produced exactly same null results as before,

Right now it is not urgent - the system boots almost fine, but I prefer to have a back door to boot it in "safe" mode.

---

### Post by grahammechanical on 2013-01-20
> Can I check it without reboot? grub.cfg contains no word of "advanced"

Rebooting will be proof of the changes. Also sudo update-grub will not identify recovery mode options. 

You may even need to run

```
sudo grub-install /dev/sda
```

if sda is the hard disk that you want grub installed into the MBR. The command grub-install will copy grub images into /boot/grub and then it will use grub-setup to install grub into the boot sector.

As a last resort, if you need to boot into recovery mode you can edit the boot parameters. At the Grub menu select Ubuntu and press E. Grub will now be in Edit mode. The countdown timer will be stopped.

Look for the line which has quiet splash in it and add

> ro recovery

in front of quiet splash and press Esc to back out of Edit mode or F10 to boot.

I have a question for you? Which version of Xubuntu was the last Xubuntu to be installed? The last Xubuntu will put it's Grub into the MBR. You must be in that last Xubuntu to be installed for update-grub to take effect.

If you are using the other version of Xubuntu then running update-grub will not have any effect unless you run grub-install /dev/sda.

Regards.

---

### Post by TroublemakerDV on 2013-01-21
> **grahammechanical said:**
> Rebooting will be proof of the changes. 
Rebooted. Saw no "advanced" neither "recovery" options. Getting mad a bit.

I know how about "single" option in boot menu item. But my question is why no these items by default, if they were there recently?

As to XU version, see details in the start of the thread: fresh install, 12.10 with latest upgrades.

Well, it shares /home with another installation, but that another one is also 12.10 (/32 gradually upgraded from fossils). And the grub was installed onto another physical drive.

Older grub.cfg HAVE recovery items:

("&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;" stands for "recovery mode" in Russian)

```
$ cat grub.cfg|grep menuen
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
submenu '&#1044;&#1086;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1077; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; &#1076;&#1083;&#1103; Ubuntu' $menuentry_id_option 'gnulinux-advanced-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
    menuentry 'Ubuntu, &#1089; Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
    menuentry 'Ubuntu, &#1089; Linux 3.5.0-18-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
    menuentry 'Ubuntu, &#1089; Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
    menuentry 'Ubuntu, &#1089; Linux 3.5.0-17-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-f1778910-6b5b-48e4-aa5b-1e1a7ce1cf94' {
menuentry "Ubuntu, &#1089; Linux 3.5.0-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, &#1089; Linux 3.5.0-18-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, &#1089; Linux 3.5.0-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, &#1089; Linux 3.5.0-17-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry 'Microsoft Windows XP Professional (&#1085;&#1072; /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-4754-6E11' {
menuentry 'Microsoft Windows XP Professional (&#1085;&#1072; /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-4754-6E11' {

```

I will compare this config sources with newer ones...

---

