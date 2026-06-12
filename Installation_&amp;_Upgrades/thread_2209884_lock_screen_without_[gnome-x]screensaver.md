---
title: "lock screen without [gnome-|x]screensaver"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2014-03-07
We use ldap authentication.  Neither gnome-screensaver nor xscreensaver can unlock the screen once locked when using ldap.

This looks to be documented all over the place but with no solution that I've found short of recompiling the screensavers with pam support.

Is there any way to just lock the screen?  I don't care about pretty patterns, I just want to lock the screen and be able to get back in.

---

### Post by cpdondo on 2014-03-07
Status update:

xscreensaver never lets me in; password authentication always fails
gnome-screensaver never lets me in; password authentication always fails
slock never brings up a password dialog; just locks the screen and turns off the monitors
xlock never lets me in; password authentication always fails
light-locker doesn't work with 12.04

Any others I can try?

---

### Post by cpdondo on 2014-03-08
Some minimal progress.  I followed this:

[http://poisson.phc.unipi.it/~mantova/pam-sasl.html](http://poisson.phc.unipi.it/~mantova/pam-sasl.html)

pam_sasl installed fine on my 12.04LTS.

Now I get:

Mar  7 20:55:03 selene gnome-screensaver(pam_sasl)[6161]: error checking password: generic failure
Mar  7 20:55:03 selene gnome-screensaver-dialog[6161]: DIGEST-MD5 common mech free
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: Gck: gck_module_new: assertion `funcs' failed
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: module_instances: assertion `module' failed
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: egg_error_message: assertion `error' failed
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: couldn't find secret store module: (unknown)
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: lookup_login_keyring: assertion `GCK_IS_SESSION (session)' failed
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: create_credential: assertion `GCK_IS_SESSION (session)' failed
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: egg_error_message: assertion `error' failed
Mar  7 20:55:03 selene gnome-keyring-daemon[5828]: couldn't create login credential: (unknown)
Mar  7 20:55:03 selene gnome-screensaver-dialog[6161]: gkr-pam: the password for the login keyring was invalid.

This should not be so complicated......

---

