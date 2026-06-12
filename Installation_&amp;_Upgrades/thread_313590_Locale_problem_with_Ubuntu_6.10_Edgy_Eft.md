---
title: "Locale problem with Ubuntu 6.10 Edgy Eft"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by jthompson on 2006-12-06
I'm new to Ubuntu, I recently came over from Gentoo (mainly because compiling everything from source and updating things took way too long).  I still like Gentoo, its just that in the commercial world, you have to move fast.  But I digress...

I did a fresh install of 6.10 on a server that I have.  I acutally used the alternate cd x86 (so I'm 32 bit).  I wanted to use lvm so I chose that one.  I did an OEM installation and GNOME was also installed.  I had not planned on putting any GUI stuff on there, but, it does make things easier, so I'll probably leave it.

However, this little locale problem is driving me nuts, and I have tried suggestions in this forum to no avail.

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

So I have tried...

[http://www.ubuntuforums.org/showthread.php?t=138022&highlight=Setting+locale+failed](http://www.ubuntuforums.org/showthread.php?t=138022&highlight=Setting+locale+failed)
[http://www.ubuntuforums.org/showthread.php?t=11353&highlight=Setting+locale+failed](http://www.ubuntuforums.org/showthread.php?t=11353&highlight=Setting+locale+failed)

The other interesting thing is this.  There doesn't seem to be the locale en_US.ISO-8859-1 on my system.

```
sudo locale-gen --purge en_US.ISO-8859-1
Error: 'en_US.ISO-8859-1' is not a supported language or locale
```

Any suggestions would be helpful.

---

### Post by dinoj on 2006-12-06
You can try to add missing locale to /var/lib/locales/supported.d/en file. May be something like this:
en_US.ISO-8859-15  ISO-8859-15
and run locale-gen

---

### Post by jthompson on 2006-12-06
I tried your suggestion and this is what I get...

```
sudo dpkg-reconfigure locales
```
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 column s wide.)
debconf: falling back to frontend: Readline
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... basadmin@bas-backup:~$ done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.ISO-8859-1... done
  en_US.ISO-8859-1... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
```

However, I still get those locale errors on some commands.

---

### Post by jthompson on 2006-12-06
Hmmm, I changed the file /etc/default/locale to:

```
LANG="en_US.UTF-8"
```

I rebooted, and wala.  I don't get the error message anymore.  Perhaps the ISO locales aren't supported anymore?  I guess I must have selected an unsupported locale on install.  Anyone who can enlighten me, please do so.

---

