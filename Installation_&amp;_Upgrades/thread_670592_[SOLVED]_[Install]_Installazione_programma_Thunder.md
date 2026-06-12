---
title: "[SOLVED] [Install] Installazione programma Thunderbird vers. 0.9"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by Ubm_Fabio on 2008-01-17
Ho seguito la procedura descritta in [http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net) ma dopo aver risposto alle varie domande e scaricato la versione, prima di finire la procedura mi compare il seguente errore a terminale:

"Linking launcher to new thunderbird

dpkg-divert: `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu' è in conflitto con `local diversion of /usr/bin*mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1051, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 212, in start
    ti.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 525, in install
    self.linkLauncher()
  File "/usr/local/bin/ubuntuzilla.py", line 797, in linkLauncher
    self.util.execSystemCommand(executionstring="sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Qualcuno può illuminarmi al riguardo? (Mi sembra di capire che fallisce il comando dpkg-divert ma non so come fare per correggerlo).
Grazie
Ciao

---

### Post by nanotube on 2008-01-17
per favore post output of:
```
dpkg -L mozilla-thunderbird
```

and also output of:
```
dpkg-divert --list
```

---

### Post by Ubm_Fabio on 2008-01-20
SOLVED

Extract the zipped archive

sudo tar -C /opt -zxvf thunderbird-2.0.0.6.tar.gz 

Make launcher command available to all users

sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird 
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
sudo ln -s /opt/thunderbird/thunderbird-bin /opt/thunderbird/mozilla-thunderbird-bin


Thanks

---

