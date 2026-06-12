---
title: "Remove python3-espeak"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by moondragon2009 on 2014-11-23
Hi, I can not remove python3-espeak:
```
sudo apt-get purge --auto-remove python3-espeak
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Pacchetti virtuali come "python3-espeak" non possono essere rimossi
0 aggiornati, 0 installati, 0 da rimuovere e 1 non aggiornati.
1 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Configurazione di python3.3-minimal (3.3.6-1+precise1)...
Traceback (most recent call last):
  File "/usr/lib/python3.3/py_compile.py", line 8, in <module>
    import imp
ImportError: No module named 'imp'
dpkg: errore nell'elaborare python3.3-minimal (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
Si sono verificati degli errori nell'elaborazione:
 python3.3-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
additional information of the problem:
```
aptitude -f install
I seguenti pacchetti parzialmente installati saranno configurati:
  python3.3-minimal 
Nessun pacchetto verrà installato, aggiornato o rimosso.
0 pacchetti aggiornati, 0 installati, 0 da rimuovere e 1 non aggiornati.
È necessario prelevare 0 B di archivi. Dopo l'estrazione, verranno occupati 0 B.
Configurazione di python3.3-minimal (3.3.6-1+precise1)...
Traceback (most recent call last):
  File "/usr/lib/python3.3/py_compile.py", line 8, in <module>
    import imp
ImportError: No module named 'imp'
Segnalazione apport non scritta poiché è stato raggiunto il valore massimo di MaxReports
        dpkg: errore nell'elaborare python3.3-minimal (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
Si sono verificati degli errori nell'elaborazione:
 python3.3-minimal
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
Errore durante l'installazione di un pacchetto. Tentativo di ripristino:
Configurazione di python3.3-minimal (3.3.6-1+precise1)...
Traceback (most recent call last):
  File "/usr/lib/python3.3/py_compile.py", line 8, in <module>
    import imp
ImportError: No module named 'imp'
dpkg: errore nell'elaborare python3.3-minimal (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di python3-espeak:amd64:
 python3-espeak:amd64 dipende da libc6 (>= 2.1.3).
 python3-espeak:amd64 dipende da libespeak1 (>= 1.30).
 python3-espeak:amd64 dipende da python3 (<< 3.5).
 python3-espeak:amd64 dipende da python3 (>= 3.3).
dpkg: errore nell'elaborare python3-espeak:amd64 (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 python3.3-minimal
 python3-espeak:amd64
```
I tried then to see from synaptic but the package is not installed
son went online and I download package for 14:04 (12:04 I have the i386) and that's what gives me if I try to install it:
```
sudo dpkg -i --force-all python3-espeak_0.5-1build1_i386.deb
dpkg: errore nell'elaborare python3-espeak_0.5-1build1_i386.deb (--install):
 python3-espeak:  0.5-1build1 (Multi-Arch: no) is not co-installable with  python3-espeak:amd64 0.5-1 (Multi-Arch: no) which is currently installed
Si sono verificati degli errori nell'elaborazione:
 python3-espeak_0.5-1build1_i386.deb
```
Sorry for the bad English,
NB: I have i386  because you see amd64 ?
how do I fix?

---

### Post by ian-weisser on 2014-11-23
Please show us the first 15 lines of the file /usr/lib/python3.3/py_compile.py

That file is provided by the libpython3.3-minimal package...but that package is no longer in the Ubuntu repositories.
If it were, reinstalling that package would be trivial.
What version of Ubuntu are you using?

---

### Post by moondragon2009 on 2014-11-24
Thank you, here are the 15 lines of the file: ```
"""Routine to "compile" a .py file to a .pyc (or .pyo) file.

This module has intimate knowledge of the format of .pyc files.
"""

import builtins
import errno
import imp
import marshal
import os
import sys
import tokenize
import traceback

MAGIC = imp.get_magic()
```

I added the ppa to update blender, then I must have the wrong hand adding something but can not remember; I ubuntu 12.04.5 i386

---

### Post by ian-weisser on 2014-11-24
Well, either that file has changed _completely_ between python 3.3 and 3.4, or something overwrote it.
Perhaps someone will have a better idea...
I would uninstall all non-Ubuntu software (including PPA software), then reinstall the python-minimal package from the Ubuntu repositories.

---

### Post by moondragon2009 on 2014-11-28
I thank you for the answer :)
I gave the following commands:```
sudo ppa-purge ppa:irie/python3.3
sudo ppa-purge ppa:fkrull/deadsnakes
sudo apt-get purge python3 python3-minimal python3.2-minimal python3.3-minimal python3.4-minimal

```
But I had to give up blender 2.71, back to version 2.62 that installed as dependency python3.2 python3.2-minimal

The problem seems to be solved! thank you :p

---

