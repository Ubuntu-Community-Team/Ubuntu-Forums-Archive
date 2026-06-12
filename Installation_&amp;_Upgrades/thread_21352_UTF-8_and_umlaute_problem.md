---
title: "UTF-8 and umlaute problem"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by rwabel on 2005-03-21
all special characters and umlaute are working fine as long as I'm not under X. Nautilus for example shows me st?ck (invalid encoding).
I've generated the locales
Generating locales...
  en_US.ISO-8859-1... done
  en_US.UTF-8... done
  de_CH.ISO-8859-1... done
  de_CH.UTF-8... done
  de_CH.UTF-8... done

but get this strange output, maybe there is the problem related
rwabel@RALPH:~ $ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=de_CH@euro
LC_CTYPE="de_CH@euro"
LC_NUMERIC="de_CH@euro"
LC_TIME="de_CH@euro"
LC_COLLATE="de_CH@euro"
LC_MONETARY="de_CH@euro"
LC_MESSAGES="de_CH@euro"
LC_PAPER="de_CH@euro"
LC_NAME="de_CH@euro"
LC_ADDRESS="de_CH@euro"
LC_TELEPHONE="de_CH@euro"
LC_MEASUREMENT="de_CH@euro"
LC_IDENTIFICATION="de_CH@euro"
LC_ALL=

and when I try this:
rwabel@RALPH:~ $ sudo dpkg-reconfigure localedef
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US.UTF-8",
        LC_ALL = (unset),
        LANG = "de_CH@euro"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Package `localedef' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localedef is not installed

put I've installed it, I used it in the past, as it also worked with the special characters in the past.
I really have no idea, and I don't know if it's related that I've also installed kubuntu through apt-get.

---

### Post by FFL on 2005-04-07
Hi, same problem here. Except I didn't try anything above, just clean install. Any clues?

---

### Post by rwabel on 2005-04-07
I have resolved that thing. Can't remember exactely, but I thought I did put a reply on the forum, maybe it was another one.

you have to mount all your windows harddisks with utf-8, for example
/dev/hda6       /mnt/hda6       vfat    user,rw,exec,auto,umask=000,utf8     0
/dev/hda7       /mnt/hda7       ntfs    user,rw,exec,auto,umask=000,nls=utf8

and I did took everywhere UTF-8, I mean with sudo dpkg-reconfigure locales 
I did also play with dpkg-reconfigure localconf

don't forget to mount also the cdrom with utf-8
/dev/hdc        /media/cdrom0 udf,iso9660 ro,user,noauto,utf8 0 0

and check the forum maybe there you will find more infos I've posted once

---

### Post by jrasmussen0 on 2005-04-08
I've done some investigation and I'm looking at /etc/environment file.

---

### Post by jrasmussen0 on 2005-04-08
It wasn't anything to do with /etc/environment.  I just logged out and selected the Language (US_English) and used it for "Just this Session".  The next time I logged in it worked.  I tested it by running 'perl' from the command prompt.

'sudo dpkg-reconfigure locales' may hav also helped.

---

### Post by Henning Perl on 2005-04-10
[QUOTE=rwabel]you have to mount all your windows harddisks with utf-8, for example
/dev/hda6       /mnt/hda6       vfat    user,rw,exec,auto,umask=000,utf8     0
/dev/hda7       /mnt/hda7       ntfs    user,rw,exec,auto,umask=000,nls=utf8
[/QUOTE]

Thanks a lot! I had this problem for a long time now and I didn't knew it was that easy to resolve. Simply adding 'utf8' to the mountoptions worked fine to get umlauts in the filenames.  :-D

---

### Post by rwabel on 2005-04-10
Yeah it was really so simple!! But I played a whole day around with env and locales and stuff reconfigure reinstall etc...finally I found that little attribute which I needed to add :-)

---

