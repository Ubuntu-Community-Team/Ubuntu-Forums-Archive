---
title: "Gutsy: Update Error with packet &quot;gdb&quot;"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by DaVinciXL on 2007-08-06
Hey everyone.

I just tried to update my Gutsy Gibbon using sudo aptitude update  and  sudo aptitude upgrade - as usual.

The error messages are mostly in German - but I'll deliver a translation:

> 
Vorbereiten zum Ersetzen von gdb 6.6.dfsg-1ubuntu3 (durch .../gdb_6.6.dfsg-1ubuntu4_i386.deb) ...
Entpacke Ersatz für gdb ...
dpkg: Warnung - kann kein stat auf altes post-removal-Skript »/var/lib/dpkg/info/gdb.postrm« durchführen: Permission denied
[COLOR="Red"]Cannot perform stat on old post-removal-script [...][/COLOR]
dpkg - probiere stattdessen Skript aus dem neuen Paket ...
[COLOR="Red"]dpkg - trying script from new package instead[/COLOR]
dpkg: ... sieht so aus, als hätte das geklappt.
[COLOR="Red"]dpkg: ... looks, as if that worked.[/COLOR]
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/gdb_6.6.dfsg-1ubuntu4_i386.deb (--unpack):
 Kann neue (vermeintliche) Info-Datei »/var/lib/dpkg/tmp.ci/md5sums« nicht installieren: Permission denied
[COLOR="Red"]Cannot install (probably) new Info file [...] Permission denied].
Vorbereiten zum Ersetzen von apt 0.7.6ubuntu1 (durch .../apt_0.7.6ubuntu2_i386.deb) ...
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/gdb_6.6.dfsg-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Permission denied? I'm working as root (sudo)! Any ideas, folks?

---

### Post by rillip on 2007-08-06
As Gusty is still in development, you probably need to post this under the dev forum.  But browsing through this real quick... the file isn't set to immutable is it?   I'm not entirely sure what it's doing here, but it looks like it's trying to run a script after removal of... something.  Does that script have correct permissions?  I really can't offer too much more than that, as I don't understand exactly what the command to dpkg is here.

---

### Post by DaVinciXL on 2007-08-06
Well... that looks odd indeed...

> 
sebastian@iljbmtl:/var/lib/dpkg/info$ ls -l | grep gdb
-rw-r--r-- 1 root root     623 2007-08-06 21:17 gdb.list
?--------- ? ?    ?          ?                ? gdb.md5sums
?--------- ? ?    ?          ?                ? gdb.postinst
?--------- ? ?    ?          ?                ? gdb.postrm
-rw-r--r-- 1 root root     255 2007-07-17 20:48 libgdbm3.list
-rwxr-xr-x 1 root root      66 2006-06-15 23:19 libgdbm3.postinst
-rwxr-xr-x 1 root root      63 2006-06-15 23:19 libgdbm3.postrm
-rw-r--r-- 1 root root      45 2006-06-15 23:19 libgdbm3.shlibs


Guess I'll have to fiddle around with that as soon as I get back right in front of that machine (the above was an attempt of a remote update).

Could anybody  please have a look at his files and post what rights those should have?

Wonder what went wrong there...

---

### Post by DaVinciXL on 2007-08-06
Damn, I'm just too curious and tried to fix that from remote but got another unpleasent error:

> 
sebastian@iljbmtl:/var/lib/dpkg/info$ sudo chown root gdb*
chown: Zugriff auf &#8222;gdb.md5sums&#8220; nicht möglich: Permission denied
chown: Zugriff auf &#8222;gdb.postinst&#8220; nicht möglich: Permission denied
chown: Zugriff auf &#8222;gdb.postrm&#8220; nicht möglich: Permission denied
sebastian@iljbmtl:/var/lib/dpkg/info$ sudo chmod +x gdb*
chmod: Zugriff auf &#8222;gdb.md5sums&#8220; nicht möglich: Permission denied
chmod: Zugriff auf &#8222;gdb.postinst&#8220; nicht möglich: Permission denied
chmod: Zugriff auf &#8222;gdb.postrm&#8220; nicht möglich: Permission denied
sebastian@iljbmtl:/var/lib/dpkg/info$


Either that's remote-sudo-problem or these files are seriously broken... could anybody please send me those three files (or attach 'em here) - mail address is [email]sebastian.schack@gmail.com[/email].

---

