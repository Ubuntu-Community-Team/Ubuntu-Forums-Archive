---
title: "Clamav installation errors!"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by Hybrid86 on 2007-07-16
I just tried to instll clamav through synaptic, and got this error
```
E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-daemon: dependency problems - leaving unconfigured
```

I went back to synaptic afterward, and several clamav packages reamained unchecked. Confused, I re checked them and reinstalled everything. The second installation went slow but with no error messages. After it was done, I looked around on my computer for clamav... but it was no where to be found on any menu. After going back to synaptic, I found "clamav-data" unchecked. I tried marking it for installation, but it warned that if I did, "clamav-freshclam", "clamav-getfiles", and "clamtk" would be removed.

Can anybody help me?

---

### Post by Gremlinzzz on 2007-07-16
sudo aptitude remove clamav 

sudo aptitude install clamav

---

### Post by Hybrid86 on 2007-07-16
> **Gremlinzzz said:**
> sudo aptitude remove clamav 

sudo aptitude install clamav

Zilch. Clamav still does not appear on any menu :(

---

### Post by Gremlinzzz on 2007-07-16
antivirus scanner for Unix
Clam AntiVirus is an anti-virus toolkit for Unix. The main purpose of this
software is the integration with mail servers (attachment scanning). The
package provides a flexible and scalable multi-threaded daemon in the
clamav-daemon package, a commandline scanner in the clamav package, and a tool
for automatic updating via Internet through the clamav-freshclam package. The
programs are based on libclamav2, which you can use in your own software.

This package contains the command line interface.  It has:
  * built-in support for RAR (2.0), Zip, Gzip, Bzip2, Tar, MS OLE2, MS Cabinet
    files, MS CHM (Compressed HTML), MS SZDD
  * built-in support for mbox, Maildir and raw mail files
  * built-in support for Portable Executable files compressed with UPX, FSG,
    and Petite

For scanning to work you'll need a virus database. You have 2 alternatives:
 * clamav-freshclam: updates the database from Internet. This is
   recommended if you have Internet access.
 * clamav-data: for users without Internet access.  Isn't updated at all
   once it's installed. You can easily create your own updated package from
   an Internet connected computer however, using clamav-getfiles.

---

### Post by Gremlinzzz on 2007-07-16
> **Gremlinzzz said:**
> antivirus scanner for Unix
Clam AntiVirus is an anti-virus toolkit for Unix. The main purpose of this
software is the integration with mail servers (attachment scanning). The
package provides a flexible and scalable multi-threaded daemon in the
clamav-daemon package, a commandline scanner in the clamav package, and a tool
for automatic updating via Internet through the clamav-freshclam package. The
programs are based on libclamav2, which you can use in your own software.

This package contains the command line interface.  It has:
  * built-in support for RAR (2.0), Zip, Gzip, Bzip2, Tar, MS OLE2, MS Cabinet
    files, MS CHM (Compressed HTML), MS SZDD
  * built-in support for mbox, Maildir and raw mail files
  * built-in support for Portable Executable files compressed with UPX, FSG,
    and Petite

For scanning to work you'll need a virus database. You have 2 alternatives:
 * clamav-freshclam: updates the database from Internet. This is
   recommended if you have Internet access.
 * clamav-data: for users without Internet access.  Isn't updated at all
   once it's installed. You can easily create your own updated package from
   an Internet connected computer however, using clamav-getfiles.

a commandline scanner  i dont know the command

---

### Post by Gremlinzzz on 2007-07-16
seems theres more parts to it 
GTK frontend for the Clam AntiVirus scanner (ClamAV)
avscan is a GTK frontend for the Clam AntiVirus scanner (ClamAV).

[http://wolfpack.twu.net/Endeavour2/contrib/#avscan](http://wolfpack.twu.net/Endeavour2/contrib/#avscan)
sudo apt-get install avscan
then put avscan in the terminal or add it to menu

---

### Post by Gremlinzzz on 2007-07-16
It works just add it to the main menu as a new item the name and command is the same avscan
:guitar:

---

### Post by Gremlinzzz on 2007-07-16
sudo aptitude install clamav
sudo aptitude install avscan
just add it to the main menu as a new item the name and command is the same avscan
:guitar:

---

### Post by Hybrid86 on 2007-07-16
> **Gremlinzzz said:**
> seems theres more parts to it 
GTK frontend for the Clam AntiVirus scanner (ClamAV)
avscan is a GTK frontend for the Clam AntiVirus scanner (ClamAV).

[http://wolfpack.twu.net/Endeavour2/contrib/#avscan](http://wolfpack.twu.net/Endeavour2/contrib/#avscan)
sudo apt-get install avscan
then put avscan in the terminal or add it to menu

I'm sorry, I'm a total noob. How exactly do I add it to the menu? :oops:

---

### Post by Gremlinzzz on 2007-07-16
click system / preferences / main menu / click + new item / type where it says name avscan and type avscan where it says command  then click ok .the icon will be in appilications
:guitar:

---

### Post by Hybrid86 on 2007-07-16
Hmm... avscan didn't seem to work. I noticed though that clamscan had it's own GUI called "clamtk"
When I opened that though, I got the same message I got with avscan:
```
Unable to view ClamAV's information file.
This will affect
how ClamTk views the number of viruses and version information.
```
If I try to scan anyway, I get this:
```
You do not appear to have virus definitions!

Running "freshclam -v" as root may fix the problem.
```
I'm assuming this has to do with this "root mode" I've heard mentioned. What exatly do I do to enter this mode? (sorry again, I've very new to this but I hope to get better as I go)

---

### Post by Gremlinzzz on 2007-07-16
sudo freshclam -v
sudo is root

---

### Post by Gremlinzzz on 2007-07-16
I didnt have any problems with the avscan command if ya cant fix it start over.
sudo aptitude remove clamav 
sudo aptitude remove avscan
then install
sudo aptitude install clamav
sudo aptitude install avscan
then type in terminal avscan  if that works like it does for me add it to the menu

---

### Post by Hybrid86 on 2007-07-17
> sudo freshclam -v
sudo is root
Typed it and got this.
```
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Mon Jul 16 23:51:07 2007
Querying current.cvd.clamav.net
TTL: 900
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd version from DNS: 43
main.cvd is up to date (version: 43, sigs: 104500, f-level: 14, builder: sven)
daily.cvd version from DNS: 3684
Retrieving http://db.local.clamav.net/daily-3684.cdiff
Trying to download http://db.local.clamav.net/daily-3684.cdiff (IP: 208.67.80.27)
Downloading daily-3684.cdiff [100%]
cdiff_apply: Parsed 12 lines and executed 12 commands
Removing backup directory ./clamav-8f94213f0ad2a94dcec34b8cfc17e583
daily.inc updated (version: 3684, sigs: 33540, f-level: 16, builder: ccordes)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 15, recommended = 16
DON'T PANIC! Read http://www.clamav.net/support/faq
Database updated (138040 signatures) from db.local.clamav.net (IP: 208.67.80.27)

```
Needless to say, it still doesnt work. I followed the [link]("Read http://www.clamav.net/support/faq") given, and it said I needed to uninstall clamav and then install it from the source. I don't quite understand the instructions it gives though; do I type that stuff in the terminal?
Or... Is there a simpler way to do this that it doesnt mention?
(thank you for your patience with me on this btw)

EDIT: Tried reinstalling everything like you said. Avscan gives a giant list of these when I scan (It did this before too):
"libclamAV error:cli_readn: read error: is a directory"

---

### Post by Gremlinzzz on 2007-07-17
I dont know i'm trying to figure out why it works for me and not you! the only thing i can think of is i extra  added  repositories. just wondering did you add Medibuntu

---

### Post by Gremlinzzz on 2007-07-17
[http://www.clamav.net/](http://www.clamav.net/)
the home page if you want to do from source.

---

### Post by Gremlinzzz on 2007-07-17
> **Gremlinzzz said:**
> [http://www.clamav.net/](http://www.clamav.net/)
the home page if you want to do from source.

ya didnt answer so how to
[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

---

### Post by Hybrid86 on 2007-07-17
> just wondering did you add Medibuntu I have the restriced extras package, but that's it.
btw, shouldn't I uninstall clamav and avscan before installing from the source?

EDIT: NVM, that didn't work either. I'll just try another antivirus program like aegis or avast. Thanks for your help/patience.

---

