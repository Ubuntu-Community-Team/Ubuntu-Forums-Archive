---
title: "Preseed Configuration of 18.04.4 LTS / unattended install - lang prompting"
date: 2020-02-18
forum: Installation &amp; Upgrades
---

### Post by captainbee on 2020-02-18
Hello and a good morning to all !

after a ten years break, i came back to Linux (yay!) and got a new challenge ;-)

I'm working on a preseed-image for my environment, testing "Cubic" and most things are working.
But there are still the questions at boot-time for region, language and country. So i think, there must be still something wrong and i hope you can help me a little.

The goal is, to get the system for de_DE-locale at finish, but i don`t really care about the installation dialog, could be in english, but i dont want to get any dialog, because the installation should run totally unattended.


Here is my preseed-file :


mybeaver.seed (ok, this name is just for example ;-) 

```
# The Beaver Preseed
# Test 18.02.2020 09:38
#




### Unattended Installation
d-i auto-install/enable boolean true
d-i debconf/priority select critical
d-i debian-installer/quiet boolean false


#### Locales
d-i debian-installer/locale string de_DE
d-i debian-installer/language string de
d-i debian-installer/country string DE


d-i debian-installer/fallbacklocale en_US.UTF-8


d-i localechooser/continentlist select Europe
d-i localechooser/countrylist/Europe select DE
d-i localechooser/shortlist/de select Germany


d-i localechooser/languagelist string de
d-i localechooser/supported-locales multiselect de_DE


d-i localechooser/preferred-locale string de_DE.UTF-8 UTF-8


d-i locales/locales_to_be_generated multiselect de_DE.UTF-8 UTF8




# No language support packages.
d-i pkgsel/install-language-support boolean false


### Time
d-i clock-setup/utc boolean true


d-i time/zone string Europe/Berlin


tzsetup-udeb time/zone string Europe/Berlin
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server string ntp.blablubb.local




### Console/Keyboard
d-i console-setup/ask_detect boolean false
d-i console-setup/detect boolean false
d-i console-tools/archs select de


d-i console-keymaps-at/keymap select de


d-i console-setup/modelcode string pc105
d-i console-setup/variantcode string nodeadkeys


#d-i keyboard-configuration/xkb-keymap select de
d-i keyboard-configuration/xkb-keymap select Deutsch


d-i keyboard-configuration/layoutcode string de


d-i keyboard-configuration/variantcode string nodeadkeys
d-i keyboard-configuration/layout string Deutsch
d-i keyboard-configuration/model select Generische PC-Tastatur mit 105 Tasten (Intl)
d-i keyboard-configuration/variant select Deutsch - Deutsch (ohne Akzenttasten)




d-i keyboard-configuration/unsupported_config_options  boolean true
d-i keyboard-configuration/unsupported_options   boolean true
d-i keyboard-configuration/modelcode string  pc105
d-i keyboard-configuration/unsupported_config_layout boolean true
d-i keyboard-configuration/unsupported_layout  boolean true




### Network Config


# will  be changend by dhcp
d-i netcfg/get_hostname string xxxxx
d-i netcfg/get_domain string bla.blubb.local




d-i netcfg/link_wait_timeout string 3
d-i netcfg/get_nameservers string ns1 ns2 ns3


d-i netcfg/dhcp_timeout string 5
#d-i netcfg/dhcpv6_timeout string 1


d-i netcfg/enable boolean true
d-i netcfg/choose_interface select auto
### Mirror settings


d-i mirror/suite string bionic
d-i mirror/country string de
d-i mirror/protocol string http
d-i mirror/http/hostname string de.archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string http://ourinternalproxy.local:3142






### Base system installation
d-i base-installer/install-recommends boolean true


d-i debconf debconf/frontend select Noninteractive


popularity-contest popularity-contest/participate boolean false




# APT Config
d-i apt-setup/universe boolean true
d-i apt-setup/services-select multiselect security, updates
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu


### Package selection
d-i tasksel/first multiselect standard








### Partition
# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /var, and /tmp partitions




d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-auto/method string lvm




d-i partman/default_filesystem string ext4


# Maxium Space on first disk
d-i partman-auto-lvm/guided_size string max




### First Installation User


d-i passwd/user-fullname string xxxxxxxx
d-i passwd/username string xxxxxxx
d-i passwd/user-password-crypted password $6xxx
d-i passwd/user-password-crypted-again password $6$Txxx
# apt-install whois && mkpasswd -m sha-512






### Bootloader/GRUB


d-i grub-installer/only_debian boolean true
d-i grub-installer/bootdev  string default




### Post-Install
d-i finish-install/reboot_in_progress note



```

additionaly, i changed :

/boot/grub/grub.conf

```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
set default=0
set timeout=5


menuentry "Install Mybeaver" {
set gfxpayload=keep
    linux /install/vmlinuz boot=casper 
    boot=casper 
    file=/cdrom/preseed/mybeaver.seed
    auto=true 
    debian-installer/country=de
    debian-installer/locale=de_DE 
    debian-installer/language=de 
    keyboard-configuration/layoutcode=de 
    localechooser/translation/warn-light=false 
    localechooser/translation/warn-severe=false
    vga=791
    initrd /install/initrd.gz
}

```

then, 
/isolinux/txt.cfg

```
default install
label install
  menu label ^Install HISonic Beaver
  kernel /install/vmlinuz
  append  boot=casper BOOT_DEBUG=2 file=/cdrom/preseed/mybeaver.seed debian-installer/locale=de_DE debian-installer/country=de debian-installer/language=de keyboard-configuration/layoutcode=de localechooser/translation/warn-light=false localechooser/translation/warn-severe=false  vga=791 initrd=/install/initrd.gz



```

in /isolinux/langlist
i deleted everything but 'de'

and i changed timeout in 

/isolinux/isolinux.cfg

to 30 what means 3 sec.


So, i think many of that options are redundant and maybe i dont need them.


With the Cubic-Tool, i was able to preinstall some progs, so i got a very nice Install-ISO. 

So, i would thank you very much for a little help with my challenge :-)

Bye and THX

JB

---

