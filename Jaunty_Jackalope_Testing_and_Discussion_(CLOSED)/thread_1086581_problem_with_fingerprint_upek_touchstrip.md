---
title: "problem with fingerprint upek touchstrip"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-03-04
hi, i have acer 6930 with fingerprint upek touchstrip. fingerprint doesn't works with fprint (no device found). i tried fingerprinter GUI and it works well but every boot, i must give this cmd:
 sudo chmod -R 777 /dev/bus/usb/002

is it possible to set this mode perm? i tried this code in udev but it doesn't works:
SUBSYSTEM=="usb", ATTRS{idVendor}=="147e", ATTRS{idProduct}=="1000", MODE="0664", GROUP=="plugdev", OPTIONS+="last_rule"

or 
SUBSYSTEM=="usb", ATTRS{idVendor}=="147e", ATTRS{idProduct}=="1000", MODE="0777", GROUP=="plugdev", OPTIONS+="last_rule"

---

### Post by RaZoR1394 on 2009-04-06
I have a UPEK TouchStrip (USB) I use with my desktop. I have managed to to enroll all fingers on both hands without problems with the gui. I managed to use the pam cli version as well both with sudo and standard user.

However logging in is not working fully ok with gdm. I write my user, press enter, it hangs, I use my finger on the UPEK, the password field appears, I write my password, press enter and I log in.

Currently It's working as an extra security but I want to use it as the only security. Is this possible?

I followed this guide (It's for Hardy however and is a bit different from the howto on the pam fprint page, [http://reactivated.net/fprint/wiki/Pam_fprint):](http://reactivated.net/fprint/wiki/Pam_fprint):)

[http://ubuntuforums.org/showthread.php?t=760018&highlight=fprint](http://ubuntuforums.org/showthread.php?t=760018&highlight=fprint)

According to pam_fprint my reader only has verify and not identify capability. Could this be related?

edit:

I'm having a problem with the madman2k jaunty ppa as well...

```

kaiser@leonis:/media/hotdog/temp/linux$ sudo apt-get install python-gnome2-extras python-pexpect

Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
python-gnome2-extras är redan den senaste versionen.
python-pexpect är redan den senaste versionen.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
1 är inte helt installerade eller borttagna.
Efter denna åtgärd kommer ytterligare 0B utrymme användas på disken.
Ställer in hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: fel vid hantering av hotkey-setup (--configure):
 underprocess post-installation script gav felkod 2
Fel uppstod vid hantering:
 hotkey-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

My /etc/pam.d/common-auth

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

auth sufficient pam_fprint.so

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

---

