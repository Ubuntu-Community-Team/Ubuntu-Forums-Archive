---
title: "Automated Installation Snag"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by msp3k on 2011-02-09
Hi guys,

I'm trying to modify an Ubuntu install CD for a (nearly) hands-off installation experience.  I have almost everything working the way that I want except for one thing: Choosing the keyboard.

1) I can boot the CD

2) I am asked, via what looks like a grey GUI menu, which language I want.  

Problem #1: I don't know how to bypass this and force the menu to accept "English".

3) I have added my own label to isolinux/txt.cfg for my installation, and it shows up on the install CD menu: "Install NIMBioS Enterprise"; and it's highlighted by default.

4) I press RETURN to begin the installation.

Problem #2: For some reason, the installer displays the "Ubuntu installer main menu", with "Configure the keyboard" highlighted.  During a regular, unmodified installation the installer automatically goes into the "Configure the Keyboard" without me having to select it from this menu.  I'm not sure why this is the case.

5) I press RETURN to select "Configure the keyboard"

Problem #3: I am then asked, "Country of origin for the keyboard".  No matter what I try as a preseed argument in txt.cfg, I can't make this go away.

6) Press RETURN to accept "USA", and everything else goes on automatic.

Here is the contents of my isolinux/txt.cfg file:

```

default nimbios
label nimbios
  menu label ^Install NIMBioS Enterprise
  kernel /install/vmlinuz
#  append  debian-installer/locale=en_US console-setup/layoutcode=us localechooser/translation/warn-light=true localechooser/translation/warn-severe=true file=/cdrom/nimbios/preseed.cfg vga=788 initrd=/install/initrd.gz noapic nolapic acpi=off reboot=pci --
#  append  file=/cdrom/nimbios/preseed.cfg vga=788 initrd=/install/initrd.gz noapic nolapic acpi=off reboot=pci --
  append  debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=en debian-installer/country=US keyboard-configuration/model=USA keyboard-configuration/variant=USA file=/cdrom/nimbios/preseed.cfg vga=788 initrd=/install/initrd.gz noapic nolapic acpi=off reboot=pci --
#  append  debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us file=/cdrom/nimbios/preseed.cfg vga=788 initrd=/install/initrd.gz noapic nolapic acpi=off reboot=pci --
label install
  menu label ^Install Ubuntu Server
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet --
label cloud
  menu label Install Ubuntu ^Enterprise Cloud
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/cloud.seed vga=788 initrd=/install/initrd.gz quiet --
label check
  menu label ^Check disc for defects
  kernel /install/vmlinuz
  append  MENU=/bin/cdrom-checker-menu vga=788 initrd=/install/initrd.gz quiet --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80

```

Note the appearance of multiple "append" lines, commented out.  These are all separate attempts at automation.  The one line that is uncommented is the closest that I have been able to get to total automation, and it yields the aforementioned behavior.

I have tried following the directions from here:
[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")
Which says:

[INDENT]For totally automatic installation with a predefined language (in this example, Estonian), you need to add some more parameters:

```
LABEL firewall
  menu label ^Firewall installation (Estonian)
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/firewall.seed debian-installer/locale=et_EE console-setup/layoutcode=et localechooser/translation/warn-light=true localechooser/translation/warn-severe=true initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet
 --
```[/INDENT]

You will see one of the above commented "append" lines follows this example.  However, this doesn't seem to work.

Anyone have a clue?

---

### Post by vener on 2011-03-20
I am having the same problem, using 10.10 alternate i386 ISO

---

### Post by Dwaalspoor98 on 2011-04-17
Those options should work for 11.04 ;)

quiet preseed/url=http://foo.com/seedfile hostname=seed001 domain=bla.local locale=en_US.UTF-8 text interface=eth0 keyboard-configuration/layout=USA keyboard-configuration/variant=USA console-setup/ask_detect=false

Those options should work for 10.10 ;) :)

quiet preseed/url=http://foo.com hostname=seed002 domain=bla.local locale=en_US.UTF-8 text interface=eth0 console-setup/ask_detect=false countrychooser/shortlist=NL console-setup/layoutcode=us console-setup/charmap=UTF-8

---

### Post by nutnut on 2011-05-12
After hours on this and reading the few documents google turned up, I think it must broken.
With Natty 11.04, I have tried:
append  keyboard-configuration/layout=USA keyboard-configuration/variant=USA console-setup/ask_detect=false

Also tried:
console-setup/layoutcode=ch country=CH

 debug debug-ubiquity console-setup/layoutcode=pc105 console-setup/variantcode= console-setup/modelcode=skip

localechooser/translation/warn-light=true localechooser/translation/warn-severe=true

Is there a way for the boot phase to be verbose and explain what options it sees, which ones it accepts/ignores?

With just the following, the first and only  prompt is for the keyboard:
append url=http://myserver/cdimage/preseed/sda-natty-11.04.seed locale=en_US console-setup/layoutcode=ch interface=auto netcfg/get_hostname=UBUNTU initrd=initrd.gz --

Well until its asks something about a citadel server. No examples in 
[https://help.ubuntu.com/11.04/installation-guide/hppa/preseed-using.html](https://help.ubuntu.com/11.04/installation-guide/hppa/preseed-using.html)
for that though.


Some resources for reading..
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/11.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/11.04/installation-guide/i386/appendix-preseed.html)
[https://help.ubuntu.com/11.04/installation-guide/i386/preseed-contents.html](https://help.ubuntu.com/11.04/installation-guide/i386/preseed-contents.html)
[https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole)
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

