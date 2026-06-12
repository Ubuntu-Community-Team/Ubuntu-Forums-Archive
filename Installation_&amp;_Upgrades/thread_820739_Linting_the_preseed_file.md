---
title: "Linting the preseed file"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by pocketchange on 2008-06-06
Does anyone know of a way to lint the presseed file and see if it has errors in it?  I'm creating a custom remaster disc and the preseed is stored on the cd-rom (so it's read-only).  Is there a tool in hardy I can lint the file with before I burn it onto a disc?

---

### Post by pocketchange on 2008-06-06
Ok, I found how to do this:

sudo debconf-set-selections -c file.seed

This did the syntax check, but it actually didn't work.  I had a few blank lines in the file and it passes debconf's scrutiny, but when I actually tried to use the seed file with the debian installer, it barfs saying it's corrupted.  I fixed the errors reported by debconf-set-selections and removed the newlines and it appears to work.

---

### Post by atoponce on 2008-06-10
Preseed needs a lot of work.  From my point of view, Kickstart is much more mature, flexible and user-friendly.  Further, Kickstart is documented through the nose.  Preseed has maybe a dozen sites on how to start a preseed install, but not on how to setup a preseed config.  If you have experience setting one up, I would be very interested.

---

### Post by pocketchange on 2008-06-11
This is what I have so far and it appears to be working:

```
# Keyboard & Locale
d-i     debian-installer/locale string en_US
d-i     console-keymaps-at select us

# Network/Host
d-i     netcfg/choose_interface select auto
d-i     netcfg/get_domain string localdomain.com

# Clock/Time
d-i     time/zone string US/Eastern
d-i     clock-setup/ntp boolean true
d-i     clock-setup/ntp-server ntp.ubuntu.com

# NIS
d-i     nis/domain string dom.host.localdomain.com

# Apt
d-i     apt-setup/local0/repository string http://host.localdomain.com/kubuntu stable main
d-i     apt-setup/local0/comment string Site-Specific Software.  Do not distribute.
d-i     apt-setup/local0/source boolean true
d-i     debian-installer/allow_unauthenticated string true
d-i     mirror/http/proxy http://host.localdomain.com:3142

# Configuring users
d-i     passwd/root-password-crypted password <md5 hash here> 
d-i     passwd/user-fullname string Tech User
d-i     passwd/user-password-crypted password <md5 hash here>
d-i     passwd/user-uid string 1010

# Packages
d-i     pkgsel/include string autofs nis nfs-common nfs-kernel-server openssh-server build-essential subversion tcl8.4-dev dupload lintian fakeroot devscripts sysv-rc-conf 

# Late Command
d-i     preseed/late_command string in-target sed -i -e '$ a\\+' group passwd shadow
```

The thing I'm having trouble with is the preseed/late_command at the very end that's supposed to append the "+" operator to the group, passwd, and shadow files.  It gives me an error and doesn't execute.  I think this command changed recently (I think it was debian-installer/late_command previously, but I'm not sure).  I've seen posts of others saying they had trouble getting the late_command to work as well.

One thing I've noticed about my configuration is that the network commands are useless.  I'm still asked whether I want to setup the network and it doesn't seem like it reads this file until after that.  I also get a strange PPPoE concatenator error that I'm unsure of how to override using the correct d-i command.  I've noticed the same with the keyboard layout.  I'm STILL prompted to set it up after seeding this file.

---

