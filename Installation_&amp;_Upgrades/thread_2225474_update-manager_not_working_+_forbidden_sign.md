---
title: "update-manager not working + forbidden sign"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by r-gatani on 2014-05-21
Hi, i hope this is the right section to post my problem, if it's not, i'm sorry.
English is not my native language (i'm italian), i hope you can understand me anyway; i tried to post my problem in ubuntu-it but they couldn't help me and i tried to check in this forum for a problem like mine, but i didn't find it.

Since 3 weeks the update-manager doesn't work anymore, neither using terminal nor dash. Further a forbidden icon popped up near my clock (top right). When i click the icon, it's written in grey (not selectable) "There is a problem when checking for update" (the sentence is italian, but this is the translation).

I have Ubuntu 13.10.

Here, it's what i get when i write from terminal ```
sudo apt-get update
```
```
kente@kente-Aspire-5742G:~$ sudo apt-get update
Trovato http://repo.steampowered.com precise InRelease
Ign http://at.archive.ubuntu.com saucy InRelease                               
Trovato http://repo.steampowered.com precise/steam Sources                     
Ign http://at.archive.ubuntu.com saucy-updates InRelease                       
Ign http://at.archive.ubuntu.com saucy-backports InRelease                     
Trovato http://repo.steampowered.com precise/steam amd64 Packages              
Trovato http://at.archive.ubuntu.com saucy Release.gpg
Ign http://archive.canonical.com saucy InRelease                               
Trovato http://repo.steampowered.com precise/steam i386 Packages               
Trovato http://archive.canonical.com saucy Release.gpg                         
Trovato http://at.archive.ubuntu.com saucy-updates Release.gpg
Trovato http://archive.canonical.com saucy Release   
Trovato http://at.archive.ubuntu.com saucy-backports Release.gpg           
Trovato http://archive.canonical.com saucy/partner i386 Packages               
Trovato http://at.archive.ubuntu.com saucy Release                             
Trovato http://at.archive.ubuntu.com saucy-updates Release                     
Trovato http://at.archive.ubuntu.com saucy-backports Release                   
Trovato http://at.archive.ubuntu.com saucy/main Sources                        
Trovato http://at.archive.ubuntu.com saucy/restricted Sources                  
Trovato http://at.archive.ubuntu.com saucy/universe Sources
Scaricamento di:1 https://private-ppa.launchpad.net saucy InRelease [355 B]
Ign https://private-ppa.launchpad.net saucy InRelease                          
Trovato http://at.archive.ubuntu.com saucy/multiverse Sources                  
Trovato https://private-ppa.launchpad.net saucy Release.gpg                    
Trovato http://at.archive.ubuntu.com saucy/main i386 Packages                  
Trovato https://private-ppa.launchpad.net saucy Release                        
Trovato http://at.archive.ubuntu.com saucy/restricted i386 Packages            
Trovato https://private-ppa.launchpad.net saucy/main i386 Packages             
Trovato http://at.archive.ubuntu.com saucy/universe i386 Packages              
Scaricamento di:2 https://private-ppa.launchpad.net saucy/main Translation-it_IT [377 B]
Trovato http://at.archive.ubuntu.com saucy/multiverse i386 Packages            
Trovato http://at.archive.ubuntu.com saucy/main Translation-it                 
Trovato http://at.archive.ubuntu.com saucy/main Translation-en
Ign http://archive.canonical.com saucy/partner Translation-it_IT
Trovato http://at.archive.ubuntu.com saucy/multiverse Translation-it
Ign http://archive.canonical.com saucy/partner Translation-it
Trovato http://at.archive.ubuntu.com saucy/multiverse Translation-en           
Ign http://archive.canonical.com saucy/partner Translation-en                  
Trovato http://at.archive.ubuntu.com saucy/restricted Translation-it
Trovato http://at.archive.ubuntu.com saucy/restricted Translation-en
Trovato http://at.archive.ubuntu.com saucy/universe Translation-it
Trovato http://at.archive.ubuntu.com saucy/universe Translation-en
Trovato http://at.archive.ubuntu.com saucy-updates/main Sources
Trovato http://at.archive.ubuntu.com saucy-updates/restricted Sources
Ign https://private-ppa.launchpad.net saucy/main Translation-it_IT
Trovato http://at.archive.ubuntu.com saucy-updates/universe Sources
Ign https://private-ppa.launchpad.net saucy/main Translation-it
Trovato http://at.archive.ubuntu.com saucy-updates/multiverse Sources
Trovato http://at.archive.ubuntu.com saucy-updates/main i386 Packages
Ign https://private-ppa.launchpad.net saucy/main Translation-en
Trovato http://at.archive.ubuntu.com saucy-updates/restricted i386 Packages    
Trovato http://at.archive.ubuntu.com saucy-updates/universe i386 Packages      
Trovato http://at.archive.ubuntu.com saucy-updates/multiverse i386 Packages    
Trovato http://at.archive.ubuntu.com saucy-updates/main Translation-it
Trovato http://at.archive.ubuntu.com saucy-updates/main Translation-en
Trovato http://at.archive.ubuntu.com saucy-updates/multiverse Translation-it
Trovato http://at.archive.ubuntu.com saucy-updates/multiverse Translation-en
Trovato http://at.archive.ubuntu.com saucy-updates/restricted Translation-it
Trovato http://at.archive.ubuntu.com saucy-updates/restricted Translation-en
Trovato http://at.archive.ubuntu.com saucy-updates/universe Translation-it
Trovato http://at.archive.ubuntu.com saucy-updates/universe Translation-en
Trovato http://at.archive.ubuntu.com saucy-backports/main Sources
Trovato http://at.archive.ubuntu.com saucy-backports/restricted Sources
Trovato http://at.archive.ubuntu.com saucy-backports/universe Sources
Trovato http://at.archive.ubuntu.com saucy-backports/multiverse Sources
Trovato http://at.archive.ubuntu.com saucy-backports/main i386 Packages
Trovato http://at.archive.ubuntu.com saucy-backports/restricted i386 Packages
Trovato http://at.archive.ubuntu.com saucy-backports/universe i386 Packages    
Trovato http://at.archive.ubuntu.com saucy-backports/multiverse i386 Packages  
Trovato http://at.archive.ubuntu.com saucy-backports/main Translation-en       
Trovato http://at.archive.ubuntu.com saucy-backports/multiverse Translation-en
Trovato http://at.archive.ubuntu.com saucy-backports/restricted Translation-en
Trovato http://at.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://at.archive.ubuntu.com saucy/main Translation-it_IT
Ign http://at.archive.ubuntu.com saucy/multiverse Translation-it_IT
Ign http://at.archive.ubuntu.com saucy/restricted Translation-it_IT            
Ign http://at.archive.ubuntu.com saucy/universe Translation-it_IT              
Ign http://at.archive.ubuntu.com saucy-updates/main Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-updates/multiverse Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-updates/restricted Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-updates/universe Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-backports/main Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-backports/main Translation-it
Ign http://at.archive.ubuntu.com saucy-backports/multiverse Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-backports/multiverse Translation-it
Ign http://at.archive.ubuntu.com saucy-backports/restricted Translation-it_IT  
Ign http://at.archive.ubuntu.com saucy-backports/restricted Translation-it     
Ign http://at.archive.ubuntu.com saucy-backports/universe Translation-it_IT
Ign http://at.archive.ubuntu.com saucy-backports/universe Translation-it
Ign http://repo.steampowered.com precise/steam Translation-it_IT
Ign http://repo.steampowered.com precise/steam Translation-it
Ign http://repo.steampowered.com precise/steam Translation-en
Lettura elenco dei pacchetti... Fatto
kente@kente-Aspire-5742G:~$ 
```
(*trovato=found*)

Here, when i write from terminal ```
sudo apt-get upgrade
```
```
kente@kente-Aspire-5742G:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
kente@kente-Aspire-5742G:~$
```
(here basically it said there is no upgrade to do)

Here, when i try to open update-manager from terminale
```
kente@kente-Aspire-5742G:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 21, in <module>
    from urllib.request import urlopen
  File "/usr/lib/python3.3/urllib/request.py", line 88, in <module>
    import http.client
  File "/usr/lib/python3.3/http/client.py", line 69, in <module>
    import email.parser
  File "/usr/lib/python3.3/email/parser.py", line 12, in <module>
    from email.feedparser import FeedParser, BytesFeedParser
  File "/usr/lib/python3.3/email/feedparser.py", line 27, in <module>
    from email import message
  File "/usr/lib/python3.3/email/message.py", line 16, in <module>
    from email import utils
  File "/usr/lib/python3.3/email/utils.py", line 36, in <module>
    from email._parseaddr import quote
  File "/usr/lib/python3.3/email/_parseaddr.py", line 16, in <module>
    import time, calendar
ImportError: No module named 'calendar'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
kente@kente-Aspire-5742G:~$ 

```

every help is appreciated

---

### Post by grahammechanical on 2014-05-21
What is Trovato?

Go into System Settings>Software and Updates>Other Software tab and disable any PPAs and then run again

```
sudo apt-get update
```

and if that works without the error messages, run

```
sudo apt-get upgrade
```

Regards.

---

### Post by r-gatani on 2014-05-21
> **grahammechanical said:**
> What is Trovato?

trovato = found

> Go into System Settings>Software and Updates>Other Software tab and disable any PPAs and then run again

i can't go there, when i try to open Software and Updates, it doesn't open nothing (i forgot to mention that)

---

### Post by bapoumba on 2014-05-21
May be this ?
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/213929](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/213929)

---

### Post by r-gatani on 2014-05-21
> **bapoumba said:**
> May be this ?
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/213929](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/213929)

i tried to give the commands
```
sudo rm `find /usr/lib/python3/dist-packages/ -name *.pyc`
sudo apt-get install --reinstall python3-gi


```

but it still doesn't work, that is what i get when i run update-manager
```
kente@kente-Aspire-5742G:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 21, in <module>
    from urllib.request import urlopen
  File "/usr/lib/python3.3/urllib/request.py", line 88, in <module>
    import http.client
  File "/usr/lib/python3.3/http/client.py", line 69, in <module>
    import email.parser
  File "/usr/lib/python3.3/email/parser.py", line 12, in <module>
    from email.feedparser import FeedParser, BytesFeedParser
  File "/usr/lib/python3.3/email/feedparser.py", line 27, in <module>
    from email import message
  File "/usr/lib/python3.3/email/message.py", line 16, in <module>
    from email import utils
  File "/usr/lib/python3.3/email/utils.py", line 36, in <module>
    from email._parseaddr import quote
  File "/usr/lib/python3.3/email/_parseaddr.py", line 16, in <module>
    import time, calendar
ImportError: No module named 'calendar'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
kente@kente-Aspire-5742G:~$ 

```

---

### Post by bapoumba on 2014-05-21
Hmm.
Can you try to reinstall python and its dependencies ?
[http://packages.ubuntu.com/trusty/python](http://packages.ubuntu.com/trusty/python)

---

### Post by r-gatani on 2014-05-21
> **bapoumba said:**
> Hmm.
Can you try to reinstall python and its dependencies ?
[http://packages.ubuntu.com/trusty/python](http://packages.ubuntu.com/trusty/python)

i tried, but there is an error

```
kente@kente-Aspire-5742G:~$ sudo dpkg -i python_2.7.5-5ubuntu3_i386.deb
[sudo] password for kente: 
(Lettura del database... 407336 file e directory attualmente installati.)
Preparativi per sostituire python v.2.7.5-5ubuntu1 (utilizzando python_2.7.5-5ubuntu3_i386.deb)...

Estrazione del sostituto di python...
dpkg: problemi con le dipendenze impediscono la configurazione di python:
 python dipende da python-minimal (= 2.7.5-5ubuntu3); comunque:
  La versione di python-minimal nel sistema è 2.7.5-5ubuntu1.
 python dipende da libpython-stdlib (= 2.7.5-5ubuntu3); comunque:
  La versione di libpython-stdlib:i386 nel sistema è 2.7.5-5ubuntu1.

dpkg: errore nell'elaborare python (--install):
 problemi con le dipendenze - lasciato non configurato
Elaborazione dei trigger per man-db...
Elaborazione dei trigger per doc-base...
Processing 1 changed doc-base file...
Si sono verificati degli errori nell'elaborazione:
 python
kente@kente-Aspire-5742G:~$ 

```

i'm not sure how translate "Estrazione del sostituto di Python", maybe something like "extracting the replacement of Python". Anyway there are some errors with the dependencies python-minimal, libpython-stdlib:i386.
Then, there is an error during the processing python and the process stop

if you need a more accurate translation of the error's message, i can translate in detail

edit: i just noticed the link you give me it's for trusty 14.04 but i still have saucy 13.10, now i try with the saucy link

---

### Post by r-gatani on 2014-05-21
> **r-gatani said:**
> 
edit: i just noticed the link you give me it's for trusty 14.04 but i still have saucy 13.10, now i try with the saucy link

with this file [http://packages.ubuntu.com/saucy/python](http://packages.ubuntu.com/saucy/python) the installation occurs, but i still get the errors for the update manager

```
kente@kente-Aspire-5742G:~$ update-managerTraceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 21, in <module>
    from urllib.request import urlopen
  File "/usr/lib/python3.3/urllib/request.py", line 88, in <module>
    import http.client
  File "/usr/lib/python3.3/http/client.py", line 69, in <module>
    import email.parser
  File "/usr/lib/python3.3/email/parser.py", line 12, in <module>
    from email.feedparser import FeedParser, BytesFeedParser
  File "/usr/lib/python3.3/email/feedparser.py", line 27, in <module>
    from email import message
  File "/usr/lib/python3.3/email/message.py", line 16, in <module>
    from email import utils
  File "/usr/lib/python3.3/email/utils.py", line 36, in <module>
    from email._parseaddr import quote
  File "/usr/lib/python3.3/email/_parseaddr.py", line 16, in <module>
    import time, calendar
ImportError: No module named 'calendar'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
kente@kente-Aspire-5742G:~$ 

```

---

### Post by r-gatani on 2014-05-22
i will bump this thread every once in a while, every help is accepted

---

### Post by bapoumba on 2014-05-22
> **r-gatani said:**
> i will bump this thread every once in a while, every help is accepted
I will have a look again later on. In general, bumping once per 24h is accepted. Thanks.

---

### Post by bapoumba on 2014-05-22
Maybe another suggestion : try the same procedure to reinstall python2.7 and python-minimal with dpkg.

---

### Post by r-gatani on 2014-05-22
> **bapoumba said:**
> Maybe another suggestion : try the same procedure to reinstall python2.7 and python-minimal with dpkg.

i'm not sure if i understood well, did you mean using in the terminal the follow command line? ```
sudo dpkg -i name_package
```

anyway i did it for both package and still i got the error 

```
kente@kente-Aspire-5742G:~$ update-managerTraceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 21, in <module>
    from urllib.request import urlopen
  File "/usr/lib/python3.3/urllib/request.py", line 88, in <module>
    import http.client
  File "/usr/lib/python3.3/http/client.py", line 69, in <module>
    import email.parser
  File "/usr/lib/python3.3/email/parser.py", line 12, in <module>
    from email.feedparser import FeedParser, BytesFeedParser
  File "/usr/lib/python3.3/email/feedparser.py", line 27, in <module>
    from email import message
  File "/usr/lib/python3.3/email/message.py", line 16, in <module>
    from email import utils
  File "/usr/lib/python3.3/email/utils.py", line 36, in <module>
    from email._parseaddr import quote
  File "/usr/lib/python3.3/email/_parseaddr.py", line 16, in <module>
    import time, calendar
ImportError: No module named 'calendar'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 37, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 41, in <module>
    from gettext import gettext as _
ImportError: No module named 'gettext'
kente@kente-Aspire-5742G:~$ 

```

anyway, thank you for the support. During the weekend i will be out of town, so i will check again next week

---

### Post by bapoumba on 2014-05-22
Did you download them first from the Ubuntu package site ? If the files are corrupted, reinstalling the same wont do much.
[http://packages.ubuntu.com/saucy/python-minimal](http://packages.ubuntu.com/saucy/python-minimal)
[http://packages.ubuntu.com/saucy/python2.7](http://packages.ubuntu.com/saucy/python2.7)

---

### Post by r-gatani on 2014-05-22
> **bapoumba said:**
> Did you download them first from the Ubuntu package site ? If the files are corrupted, reinstalling the same wont do much.
[http://packages.ubuntu.com/saucy/python-minimal](http://packages.ubuntu.com/saucy/python-minimal)
[http://packages.ubuntu.com/saucy/python2.7](http://packages.ubuntu.com/saucy/python2.7)

yes, i downloaded from the Ubuntu package site, exactly those link

---

### Post by bapoumba on 2014-05-22
> **r-gatani said:**
> yes, i downloaded from the Ubuntu package site, exactly those link

Well, I'm sorry then. I'll keep on looking and will post back if I find anything or get any idea :(

---

### Post by r-gatani on 2014-05-22
> **bapoumba said:**
> Well, I'm sorry then. I'll keep on looking and will post back if I find anything or get any idea :(

thank you anyway, my last resort is formatting and reinstalling the os, but i will check again next week

---

### Post by r-gatani on 2014-05-26
i'm still searching for help, if anyone has

---

