---
title: "Gutsy Preseed help"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by ScottTFrazer on 2008-03-28
I'm trying to create my first preseed-based automated install, and I'm running into some trouble I was hoping someone could help me with.

My setup starts with the Ubuntu 7.10 JeOS iso image.  I've modified the isolinux/isolinux.cfg file and created my own seed file in preseeds

specifically:

1. Even though my preseed file contains the following lines:
```
d-i passwd/root-password password {mypassword}
d-i passwd/root-password-again password {mypassword}
passwd passwd/make-user boolean false
```
I'm still being asked to create a normal user, and my root user isn't being created / activated

2. During the installation, I'm being asked to Download language support.  how can I turn this off?

3. I'm trying to install openssh-server automatically.  I thought this line would do this, but it doesn't seem to...  what am I doing wrong?
```
d-i pkgsel/install-pattern string ~t^ubuntu-standard$|~n^openssh-server$
```

4.  I'd really like to use the apt-cacher proxy I've set up for package installation to keep my network installation stuff local.  Is there a way to use this during the preseed, and if so does anyone know of a tutorial on how to do it?

Here's my complete preseed file:
```

# Locale sets language and country.
d-i debian-installer/locale string en_US

# Keyboard selection.
d-i console-setup/variant select U.S. English
d-i debian-installer/consoledisplay string kbd=lat0-sun16(utf8)

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# If you prefer to configure the network manually, uncomment this line and
# the static network configuration below.
d-i netcfg/disable_dhcp boolean true

# Static network configuration.
d-i netcfg/get_nameservers string 192.168.0.21 192.168.0.20
d-i netcfg/get_ipaddress string 66.151.6.17
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 66.151.6.1
d-i netcfg/confirm_static boolean true

d-i netcfg/get_hostname string gutsybase
d-i netcfg/get_domain string duoconsulting.net

d-i clock-setup/utc boolean true

d-i time/zone string US/Central
d-i clock-setup/ntp boolean true

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/choose_recipe select All files in one partition (recommended for new users)
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

d-i passwd/root-password password {mypassword}
d-i passwd/root-password-again password {mypassword}

# If you want to skip creation of a normal user account.
passwd passwd/make-user boolean false


#### Boot loader installation.

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if if finds some other OS
# too, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

# Avoid that last message about the install being complete.
d-i prebaseconfig/reboot_in_progress note

d-i pkgsel/install-pattern string ~t^ubuntu-standard$|~n^openssh-server$


```

Thanks in advance!
Scott

---

### Post by ruibernardo on 2008-03-28
Hi,

if you *really* want to set up a root account and don't want to create any user at install, add (or change) the following in your root creation lines in the preseed file:

```
d-i passwd/make-user boolean false
user-setup-udeb passwd/make-user        boolean false
```I think it should work. Here is all I use in that part when I want to install a Debian system with a root account but no users:
```

# Default in Ubuntu! Commented, just for reference.
# Allow login as root?
#user-setup-udeb    passwd/root-login    boolean    false

# Root password, either in clear text
d-i passwd/root-password password root
d-i passwd/root-password-again password root
user-setup-udeb passwd/root-login boolean true

# or encrypted using an MD5 hash.
#d-i passwd/root-password-crypted password [MD5 hash]

# Skip creation of a user account.
d-i passwd/make-user boolean false
user-setup-udeb passwd/make-user        boolean false
```If you want to setup the password at install time, comment this lines:

```
#d-i passwd/root-password password root
#d-i passwd/root-password-again password root
```The line
 ```
user-setup-udeb passwd/root-login boolean true
```will create the account and the installer will ask for the password.

---

### Post by ScottTFrazer on 2008-03-28
Great!  That solved my problem #1. Thanks!

 I'm still having trouble with #2, #3 and #4, though.

Here are the updated sections of the preseed file, for archival purposes :-)

```

# root account
d-i passwd/root-password password {mypassword}
d-i passwd/root-password-again password {mypassword}
user-setup-udeb passwd/root-login boolean true

# If you want to skip creation of a normal user account.
d-i passwd passwd/make-user boolean false
user-setup-udeb passwd/make-user boolean false

```

---

### Post by ruibernardo on 2008-03-28
For #2 I change the isolinux.cfg file and add the following in the boot options:

```
append ... pkgsel/language-pack-patterns= pkgsel/install-language-support=false
```This disables it before the installer is loaded, so the installer doesn't ask for it. "language-pack-patterns=" has a space in front of it.

For #3, "standard" (not ubuntu-standard, at least in Gutsy) is a task. You must use tasksel to install the "standard" system:

```
 ## make sure standard is installed:
tasksel tasksel/first multiselect standard
```To add another task, as "desktop" or "lamp-server", add a comma and the other task.

To install a package after the installation was completed, but before the installer umounts the target chroot, use apt-install:

```
 # This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system.
d-i preseed/late_command string apt-install openssh-server

```I never used proxy, but this link might hopefully help you: [http://www.debuntu.org/book/export/html/197](http://www.debuntu.org/book/export/html/197)

A preseed for Feisty, should work with Gutsy, mostly: [https://help.ubuntu.com/7.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/7.04/installation-guide/i386/appendix-preseed.html)

---

### Post by ScottTFrazer on 2008-04-03
I haven't had a chance to try these suggestions yet (distractions abound) but I wanted to thank you for them!

Scott

---

