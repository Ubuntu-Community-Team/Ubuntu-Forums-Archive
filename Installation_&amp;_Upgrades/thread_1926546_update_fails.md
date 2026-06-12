---
title: "update fails"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by movies1978 on 2012-02-16
Hello,

sorry to post some output which contains some german, but I am a bit desperate:
first part:
sudo apt-get upgrade[sudo] password for mathias: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren.
Die folgenden Pakete haben nicht-erfüllte Abhängigkeiten:
E: Nicht-erfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.

sudo apt-get -f install says:

dpkg: language-pack-de: Abhängigkeitsprobleme, aber entferne es auf Anfrage dennoch:
 language-pack-de-base hängt ab von language-pack-de (>= 1:10.04+20110204).
dpkg: Fehler beim Bearbeiten von language-pack-de (--remove):
 Paket ist in einem sehr schlechten inkonsistenten Zustand - Sie sollten
 es erneut installieren, bevor Sie es zu entfernen versuchen.
Fehler traten auf beim Bearbeiten von:
 language-pack-de
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have no clue howto solve this, especially worried, because I cannot install security updates.

Greetings movies

---

### Post by cortman on 2012-02-16
Don't know German well enough and don't have access to Google Translate here at work. If you could translate it that would sure help.

---

### Post by QIII on 2012-02-16
You might try 

```
sudo apt-get dist-upgrade
```which will attempt to resolve any dependency problems.  You may find that the state of the language-pack-de will be cleaned up.  This command will NOT try to upgrade you to the next version of Ubuntu.  The commands for that are different entirely.

If that doesn't solve it, then since the dpkg failure involves a very bad inconsistent state of  language-pack-de, it might be easiest just to go to your GUI package  manager (such as Synaptic), find language-pack-de and choose reinstall.

That, or 

```
sudo apt-get install --reinstall language-pack-de
```and try the update again -- using dist-upgrade.

Alles Gute!

---

### Post by QIII on 2012-02-16
Sorry folks.

I realize that since I speak German and just read the OP and answered  the question, others might not understand what is going on.

Quite right, cortman.

Since languages are hard to translate literally and still make sense, I'm not sure that trying Babel Fish or something like that would really work.

So here is the OP's issue in an idiomatic translation:

```
sudo apt-get upgrade [sudo] password for mathias:
Reading package lists ... Done
Building Dependency tree
Reading state information ... Done

<something seems to be missing here>

Try "apt-get -f install" to correct this.
The following packages have unmet dependencies:

<something else missing here?>

E: Unmet dependencies. Try to use -f.


sudo apt-get -f install says:


dpkg: language-pack-de: dependency problems, but removing it anyway as requested:
language-pack-de-base depends on language-pack-de (> = +20110204 1:10:04).
dpkg: error processing language-pack-de (- remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting to remove it.
Errors were encountered while processing:
language-pack-de
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cortman on 2012-02-16
Thanks QIII. Glad there are some multilingual folks here!

---

