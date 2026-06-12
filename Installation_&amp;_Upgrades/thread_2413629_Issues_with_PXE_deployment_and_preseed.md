---
title: "Issues with PXE deployment and preseed"
date: 2019-02-28
forum: Installation &amp; Upgrades
---

### Post by cptkeys on 2019-02-28
Hey all,

Been working on configuring a deployment for 18.04.2 with Desktop and Server as available options.

I have the preseed working enough to get Desktop to finish

The main issue I have after completion is that DHCP is entirely not working until editing network-manager files, or running dhclient

What I need is for the preseed to configure the dhcp and keep the dhcp settings working (whether by late_command or other)

This is the pxelinus menu config:

> 
LABEL Ubuntu 18.04 Desktop - Full erase    MENU LABEL Install Ubuntu 18.04 Desktop - Full erase
    kernel Linux/Ubuntu/Desktop/18.04/casper/vmlinuz
    append boot=casper automatic-ubiquity netboot=nfs nfsroot=10.2.1.72:/Linux/Ubuntu/Desktop/18.04/ initrd=/Linux/Ubuntu/Desktop/18.04/casper/initrd.lz auto=true url=http://10.2.1.72/preseed/preseedfullerase.cfg toram




There are commented lines from where I have been testing different methods to get dhcp to function.

The reference to */install.sh is a script file that purely runs (but still fails to do anything):
> sudo sed -i 's/^managed=false/managed=true/' /etc/NetworkManager/NetworkManager.conf

See below preseed file. Lots of pieces used from the origin preseed that was used, and other options added from preseeds found online
> [INDENT=2]# Language setting[/INDENT]
[INDENT=2]d-i debian-installer/language                   string          en[/INDENT]
[INDENT=2]d-i debian-installer/country                    string          US[/INDENT]
[INDENT=2]d-i debian-installer/locale                     string          en_US.UTF-8[/INDENT]
[INDENT=2]d-i debian-installer/splash                     boolean         false[/INDENT]
[INDENT=2]d-i localechooser/supported-locales             multiselect     en_US.UTF-8[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# Keyboard setting[/INDENT]
[INDENT=2]d-i console-setup/ask_detect                    boolean         false[/INDENT]
[INDENT=2]d-i console-setup/layoutcode                    string          us[/INDENT]
[INDENT=2]d-i console-setup/charmap                       select          UTF-8[/INDENT]
[INDENT=2]d-i keymap                                      select          us[/INDENT]
[INDENT=2]d-i keyboard-configuration/xkb-keymap           select          us[/INDENT]
[INDENT=2]d-i keyboard-configuration/layoutcode           string          us[/INDENT]
[INDENT=2]d-i keyboard-configuration/modelcode            string          us[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i preseed/early_command string curl -k [http://10.2.1.72/preseed/install.sh;](http://10.2.1.72/preseed/install.sh;)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]### Network configuration[/INDENT]
[INDENT=2]# netcfg will choose an interface that has link if possible. This makes it[/INDENT]
[INDENT=2]# skip displaying a list if there is more than one interface.[/INDENT]
[INDENT=2]d-i netcfg/choose_interface                     select          auto[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# Just in case our DHCP server is busy.[/INDENT]
[INDENT=2]d-i netcfg/dhcp_timeout                         string          60[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# Any hostname and domain names assigned from dhcp take precedence over[/INDENT]
[INDENT=2]# values set here. However, setting the values still prevents the questions[/INDENT]
[INDENT=2]# from being shown, even if values come from dhcp.[/INDENT]
[INDENT=2]d-i netcfg/get_hostname                         string          unassigned-hostname[/INDENT]
[INDENT=2]d-i netcfg/get_domain                           string          unassigned-domain[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i preseed/early_command string curl -k [http://10.2.1.72/preseed/install.sh;](http://10.2.1.72/preseed/install.sh;)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# paritioning.[/INDENT]
[INDENT=2]d-i partman-auto/method                         string          regular[/INDENT]
[INDENT=2]d-i partman-auto/choose_recipe                  select          atomic[/INDENT]
[INDENT=2]d-i partman-partitioning/confirm_write_new_label boolean        true[/INDENT]
[INDENT=2]d-i partman/choose_partition                    select          finish[/INDENT]
[INDENT=2]d-i partman/confirm                             boolean         true[/INDENT]
[INDENT=2]d-i partman/confirm_nooverwrite                 boolean         true[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# Clock setting[/INDENT]
[INDENT=2]d-i clock-setup/utc                             boolean         true[/INDENT]
[INDENT=2]d-i time/zone                                   string          Brisbane[/INDENT]
[INDENT=2]d-i clock-setup/ntp                             boolean         true[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i pkgsel/include                              string          wget net-tools git[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# User setting[/INDENT]
[INDENT=2]d-i passwd/root-login                           boolean         false[/INDENT]
[INDENT=2]d-i passwd/make-user                            boolean         false [/INDENT]
[INDENT=2]d-i passwd/root-password                        password        Test123[/INDENT]
[INDENT=2]d-i passwd/root-password-again                  password        Test123[/INDENT]
[INDENT=2]d-i user-setup/allow-password-weak              boolean         true[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i passwd/user-fullname                        string          administrator[/INDENT]
[INDENT=2]d-i passwd/username                             string          administrator[/INDENT]
[INDENT=2]d-i passwd/user-password                        password        Test123    [/INDENT]
[INDENT=2]d-i passwd/user-password-again                  password        Test123[/INDENT]
[INDENT=2]d-i passwd/user-default-groups                  string          adm cdrom dialout lpadmin plugdev sambashare[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]### Mirror settings[/INDENT]
[INDENT=2]d-i mirror/country                              string          manual[/INDENT]
[INDENT=2]d-i mirror/protocol                             string          http[/INDENT]
[INDENT=2]d-i mirror/http/hostname                        string          10.3.1.31[/INDENT]
[INDENT=2]d-i mirror/http/directory                       string          /ubuntu[/INDENT]
[INDENT=2]d-i mirror/http/proxy                           string[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]tasksel tasksel/first multiselect standard,ssh-server[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i pkgsel/upgrade select full-upgrade[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]#d-i preseed/late_command string \[/INDENT]
[INDENT=2]#    in-target tftp 172.16.0.1 -c get postpreseed.sh; \[/INDENT]
[INDENT=2]#    in-target chmod +x postpreseed.sh; \[/INDENT]
[INDENT=2]#    in-target /bin/bash -x postpreseed.sh; \[/INDENT]
[INDENT=2]#    in-target rm -f postpreseed.sh;[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i preseed/late_command string \[/INDENT]
[INDENT=2]cd /target; \[/INDENT]
[INDENT=2]wget [http://10.2.1.72/preseed/install.sh;](http://10.2.1.72/preseed/install.sh;) \[/INDENT]
[INDENT=2]chmod +x ./install.sh; \[/INDENT]
[INDENT=2]chroot ./ ./install.sh; \[/INDENT]
[INDENT=2]#rm -f ./install.sh;    [/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]#d-i preseed/run string install.sh[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]d-i preseed/late_command string curl -k [http://10.2.1.72/preseed/install.sh;](http://10.2.1.72/preseed/install.sh;)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]#d-i preseed/late_command                        string          in-target sed -i 's/^managed=false/managed=true/' /etc/NetworkManager/NetworkManager.conf;[/INDENT]
[INDENT=2]#in-target wget -O /target/etc/install.sh; [http://10.2.1.72/preseed/install.sh;](http://10.2.1.72/preseed/install.sh;) \[/INDENT]
[INDENT=2]#chmod 700 /target/etc/install.sh; \[/INDENT]
[INDENT=2]#in-target sh /target/etc/install.sh[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# reboot at the end[/INDENT]
[INDENT=2]d-i finish-install/reboot_in_progress           note[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]#Grub[/INDENT]
[INDENT=2]d-i debian-installer/exit/shutdown              boolean         true[/INDENT]


---

### Post by cptkeys on 2019-02-28
Manually configuring the interface with IP Address, gateway etc and works correctly
As soon as it is set back to dhcp4: true, i have to run dhclient to get an ip

After rebooting the machine, I am halted on boot with the loading message of
> A start job is running for Wait for Network to be Configured (1min 24s / no limit)

---

