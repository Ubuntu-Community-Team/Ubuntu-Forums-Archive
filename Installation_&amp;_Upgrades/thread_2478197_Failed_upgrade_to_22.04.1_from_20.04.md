---
title: "Failed upgrade to 22.04.1 from 20.04"
date: 2022-08-19
forum: Installation &amp; Upgrades
---

### Post by fraCPH on 2022-08-19
I'm trying to upgrade to the new LTS but the upgrade process fails with the following error message:
```

Error in function: install

apt_pkg.Error: E:Impossibile configurare "libc6:i386". , E:Impossibile eseguire immediatamente la configurazione su "libgcc-s1:i386". Per maggiori informazioni, consultare "man 5 apt.conf" alla sezione "APT::Immediate-Configure" (2).
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/problem_report.py", line 477, in add_to_existing
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 430, in write
    block = f.read(1048576)
  File "/usr/lib/python3.8/codecs.py", line 322, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte

Original exception was:
apt_pkg.Error: E:Impossibile configurare "libc6:i386". , E:Impossibile eseguire immediatamente la configurazione su "libgcc-s1:i386". Per maggiori informazioni, consultare "man 5 apt.conf" alla sezione "APT::Immediate-Configure" (2).
Error in function: install

apt_pkg.Error: E:Impossibile eseguire immediatamente la configurazione su "libc6:amd64". Per maggiori informazioni, consultare "man 5 apt.conf" alla sezione "APT::Immediate-Configure" (2).
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/problem_report.py", line 477, in add_to_existing
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 430, in write
    block = f.read(1048576)
  File "/usr/lib/python3.8/codecs.py", line 322, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte

Original exception was:
apt_pkg.Error: E:Impossibile eseguire immediatamente la configurazione su "libc6:amd64". Per maggiori informazioni, consultare "man 5 apt.conf" alla sezione "APT::Immediate-Configure" (2).

Impossibile installare gli avanzamenti di versione 

L'avanzamento si è interrotto: il sistema potrebbe essere in uno 
stato inutilizzabile. Verrà avviato un ripristino (dpkg --configure 
-a). 


Avanzamento impraticabile 

``` 
All the PPAs are disabled.
Can anyone help me?

---

### Post by ubfan1 on 2022-08-19
After disabling the extra PPAs, did you rerun sudo apt-get update   then sudo apt-get dist-upgrade  then try the 22.04 upgrade.

---

### Post by fraCPH on 2022-08-19
Yes, that's what I did.

---

### Post by fraCPH on 2022-08-22
Solved by adding focal-updates to sources.list, somehow it was missing

---

