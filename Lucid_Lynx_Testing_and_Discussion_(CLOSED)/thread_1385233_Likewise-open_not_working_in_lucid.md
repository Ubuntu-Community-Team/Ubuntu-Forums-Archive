---
title: "Likewise-open not working in lucid"
date: 2010-01-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pinguino99 on 2010-01-19
Last lucid alpha 2, full updated.
sudo apt-get install likewise-open (it's version 5.4.0.39949-3)

Then:
sudo domainjoin-cli --loglevel verbose join mydomain.com administrator

Joining to AD Domain:   mydomain.com
With Computer DNS Name: zubu1004.mydomain.com

[email]administrator@MYDOMAIN.COM[/email]'s password:
SUCCESS
You should reboot this system before attempting GUI logins as a domain user

Then, i sudo visudo and entered the line
%MYDOMAIN\\domain^users ALL=(ALL) ALL

I reboot, i try enter username  mydomain/myuser  or   mydomain+user  or  user  and i DON'T get prompted for the password, asking again to the username screen.

Here is auth.log interesting lines:
zubu1004 gdm-session-worker[1652]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "mydomain\myuser"
Jan 19 16:13:14 zubu1004 gdm-session-worker[1652]: pam_unix(gdm:auth): conversation failed
Jan 19 16:13:14 zubu1004 gdm-session-worker[1652]: pam_unix(gdm:auth): auth could not identify password for [mydomain\myuser]

In intrepid (but also karmic) likewise open worked.
Any suggestions ?

Thanks and regards
Pinguino99

---

### Post by fschnittke on 2010-03-08
Hi:

I can't get likewise to work either, since upgrading to Lucid BETA 3. I had problems during the upgrade of BETA3:


[LIST]
[*]E: likewise-open: subprocess installed post-installation script returned error exit status 1
[*]E: likewise-open-gui: dependency problems - leaving unconfigured
[/LIST]
Just wondering if you've come across a resolution for the likewise issues?

Thanks....


Fred

---

### Post by step5 on 2010-03-29
Same problem here... (german version)

```

Richte likewise-open ein (5.4.0.42111-1) ...
 * Starting Likewise Service Manager: lwsmd                              [fail] 
 * Reloading Likewise Service Manager configuration                      [ OK ] 
dpkg: Fehler beim Bearbeiten von likewise-open (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von likewise-open-gui:
 likewise-open-gui hängt ab von likewise-open; aber:
  Paket likewise-open ist noch nicht konfiguriert.
  Paket likewise-open, das likewise-open bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von likewise-open-gui (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Fehler traten auf beim Bearbeiten von:
 likewise-open
 likewise-open-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

seems like there are some dependence errors

---

