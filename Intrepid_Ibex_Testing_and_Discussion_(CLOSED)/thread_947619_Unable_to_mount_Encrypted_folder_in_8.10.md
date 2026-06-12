---
title: "Unable to mount Encrypted folder in 8.10"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bineeshm on 2008-10-14
Hi!

I'm unable to log into the new Encrypted folder in 8.10 Beta. I typed below command:

mount.ecryptfs_private 

and got below error,

keyctl_search: Required key not available

Can someone help in accessing the folder?

Regards,

---

### Post by overdrank on 2008-10-14
Hi and intrepid is still in testing stage
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by plun on 2008-10-14
I can only help you and point to the wiki

[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

Maybe this ?

> Do NOT move ~/.ecryptfs into ~/Private!!! The ~/.ecryptfs directory contains a key signature required to mount ~/Private, and the only valuable data (your key) is already encrypted in that directory. Should you do something silly like this, to recover your data, you will need to manually mount ~/Private as root, and using the unwrapped passphrase.

The testing part also includes more info.

---

### Post by b.q.wemer on 2008-10-22
Hi,

run ecryptfs-insert-wrapped-passphrase-into-keyring

log out, log in again should help. Maybe you changed the passphrase in the meantime.

HTH

---

### Post by sheepshearer on 2008-10-28
i had exactly this problem after i explicitly unmounted Private (doh!)

i recovered with:

% [COLOR="Blue"]ecryptfs-insert-wrapped-passphrase-into-keyring  ~/.ecryptfs/wrapped-passphrase "this is my passphrase (not my login password) it has spaces so i put quotes around it"[/COLOR]
Unable to read salt value from user's .ecryptfsrc file; using default
Inserted auth tok with sig [7dc9ab149c4aebee] into the user session keyring
% [COLOR="Blue"]mount.ecryptfs_private[/COLOR]
%

and you should be done

---

### Post by b.q.wemer on 2008-10-29
Hi,

I really like to use this awesome feature but every time I wiped the old setup and did it from scratch, it ended up with the error: ```
Required key not available. 

```
After reading some time through launchpad.net, I found out that this is caused by gnome-keyring, witch is not able to store the key properly. Especially after dist-upgrade from hardy to intrepid (like my system) this problem occurs.

auth.log says:```
Oct 29 08:24:04 WG3 gdm[6247]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter http://www.gnome.org/projects/gconf/ erhalten Sie weitere Informationen (Details -  1: Verbindung zur Sitzung konnte nicht abgerufen werden: dbus-launch failed to autolaunch D-Bus session: No protocol specified 
```

If someone knows a solution or at least a workaround, I would be glad to hear it. :D

---

### Post by sheepshearer on 2008-10-29
just had to do this again (that'll teach me to log out)

```
ubuntu[pb] mount.ecryptfs_private
keyctl_search: Required key not available
ubuntu[pb] ecryptfs-insert-wrapped-passphrase-into-keyring ~/.ecryptfs/wrapped-passphrase "this is my secret"
Unable to read salt value from user's .ecryptfsrc file; using default
Inserted auth tok with sig [ec4a7e49db1ebc9a] into the [COLOR="Red"]user session keyring[/COLOR]
ubuntu[pb] mount.ecryptfs_private
```

so that's the "session" keyring? i don't know what that is, but its name would imply that it's valid only for the current session - so don't log out

---

