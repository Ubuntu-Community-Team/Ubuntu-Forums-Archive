---
title: "ubuntu lucid preseeding not giving desired results and pxe booting issues"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by madubuntuer on 2010-05-05
here's my pxelinux.cfg/default
LABEL install64
      kernel amd64/ubuntu-installer/amd64/linux
        append vga=normal locale=en_GB console-setup/layoutcode=uk console-setup/ask_detect=false   preseed/url=preseed.txt  initrd=amd64/ubuntu-installer/amd64/initrd.gz

Basically when I run the installer I get a screen asking the following

origin of keyboard
ubuntu package sources
how to apply updates
manually select packages to install screen

I want the above to be all automatically set using preseed file so that it's truly unattended.

Also is it possible to boot an iso using pxe instead of downloading off the net. I want to do offline installation.

Here's my preseed file so far
```

d-i debian-installer/locale string en_UK
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string uk
d-i console-setup/layout	select	United Kingdom
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i mirror/protocol string http
d-i mirror/country string GB 
d-i mirror/http/hostname string gb.archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string
d-i clock-setup/utc boolean true
d-i time/zone string Europe/London
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
d-i finish-install/reboot_in_progress note
tasksel	tasksel/desktop	multiselect	gnome

```

---

