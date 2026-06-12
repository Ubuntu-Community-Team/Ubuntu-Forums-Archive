---
title: "Cannot de-install gpar2"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by supahfly on 2006-11-01
HI ,

I recently tried to install gpar2, and it somewhere got stuck .
NowI have in the adept-manager gpar2 >>> broken
Everytime I try to install something, it first tries to deinstall gpar2 which does not seem to work. When I try it in cmd-line:

$ sudo apt-get install vsftpd
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
The following packages were automatically installed and are no longer required:
  gpar2
Use 'apt-get autoremove' to remove them.
De volgende pakketten zullen VERWIJDERD worden:
  gpar2
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  vsftpd
0 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 1 verwijderen en 6 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 112kB aan archieven opgehaald worden.
Na het uitpakken zal er 217kB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]?
Ophalen:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) edgy/main vsftpd 2.0.4-0ubuntu5 [112kB]
112kB opgehaald in 5s (19,4kB/s)
(Database inlezen ... 85035 bestanden en mappen geïnstalleerd.)
gpar2 wordt verwijderd ...
***
* Updating MIME database in /usr/share/mime...
Wrote 477 strings at 20 - 2790
Wrote aliases at 2790 - 2944
Wrote parents at 2944 - 32f4
Wrote literal globs at 32f4 - 3350
Wrote suffix globs at 3350 - 6648
Wrote full globs at 6648 - 666c
Wrote magic at 666c - bc7c
Wrote namespace list at bc7c - bc8c
***
/var/lib/dpkg/info/gpar2.postrm: 33: update-desktop-database: not found
dpkg: fout bij afhandelen van gpar2 (--remove):
 subproces post-removal script gaf een foutwaarde 127 terug
Fouten gevonden tijdens behandelen van:
 gpar2
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is ther someway I can get this gpar2 of my system ?

Thanks

---

### Post by robert114 on 2006-11-02
Well this is what helped me installing gpar2:

I manually removed those files listed by "dpkg -L packagename", and edited the /var/lib/dpkg/status file by hand to change the status to "purge ok not-installed". 

from: [http://linux.derkeiler.com/Mailing-Lists/Debian/2004-06/0230.html]("http://linux.derkeiler.com/Mailing-Lists/Debian/2004-06/0230.html")

But I was still unable to install gpar2 after I've installed the depencies

---

### Post by supahfly on 2006-11-02
thx for the info!
I tried to install quickpar via wine.
It installed but I am unable to make it work on checking and repairing files.
Anybody knows a graphical par2 app for tux ?

---

### Post by robert114 on 2006-11-02
Well i just got gpar2 working for Ubuntu you'll only need Ubuntu 32 bit version. It solved a lot of other problems witch I had.

I'm now happily using gpar

---

### Post by supahfly on 2006-11-06
Where can i find gpar ?
I have been looking for it but cannot find it ...
Something called gparted, but its a partitioner .

---

### Post by robert114 on 2006-11-06
unfortunately it is not in the Ubuntu repo, but you can download the 2 deb's manually from:
[URL="http://sourceforge.net/project/showfiles.php?group_id=30568"]
http://sourceforge.net/project/showfiles.php?group_id=30568[/URL]

---

### Post by pt123 on 2007-03-14
To get quickpar to work in Wine you have open quick par then choose "Open" button at the bottom left, then from that select your par file.

---

