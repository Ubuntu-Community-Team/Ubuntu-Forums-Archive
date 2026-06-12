---
title: "Man pages"
date: 2017-05-03
forum: Installation &amp; Upgrades
---

### Post by zkab on 2017-05-03
I made a fresh installation of 17.04 (desktop & 64 bits).
Discovered that man pages are not there ... never seen that before.

loke@loke:~$ man ls
man: can't execute most: No such file or directory
man: command exited with status 255: sed -e '/^[[:space:]]*$/{ N; /^[[:space:]]*\n[[:space:]]*$/D; }' | (cd <fd 3> && LESS=-ix8RmPm Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$PM Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$ MAN_PN=ls(1) most)

Where do I find them ?

---

### Post by #&amp;thj^% on 2017-05-03
does this help....or run this this I should say.
```
**mandb** 
```

---

### Post by steeldriver on 2017-05-03
Do you have a $PAGER or $MANPAGER environment variable set? 

```

echo $MANPAGER

echo $PAGER

```

Does

```

MANPAGER=less man ls

```

work?

---

### Post by zkab on 2017-05-03
No success ...

```
loke@loke:~$ mandb
0 man subdirectories contained newer manual pages.
0 manual pages were added.
0 stray cats were added.
0 old database entries were purged.

loke@loke:~$ man ls
man: can't execute most: No such file or directory
man: command exited with status 255: sed -e '/^[[:space:]]*$/{ N; /^[[:space:]]*\n[[:space:]]*$/D; }' | (cd <fd 3> && LESS=-ix8RmPm Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$PM Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$ MAN_PN=ls(1) most)

loke@loke:~$ sudo mandb
Purging old database entries in /usr/share/man...
Processing manual pages under /usr/share/man...
Purging old database entries in /usr/share/man/zh_TW...
Processing manual pages under /usr/share/man/zh_TW...
Purging old database entries in /usr/share/man/da...
Processing manual pages under /usr/share/man/da...
Purging old database entries in /usr/share/man/cs...
Processing manual pages under /usr/share/man/cs...
Purging old database entries in /usr/share/man/hu...
Processing manual pages under /usr/share/man/hu...
Purging old database entries in /usr/share/man/sl...
Processing manual pages under /usr/share/man/sl...
Purging old database entries in /usr/share/man/fr.ISO8859-1...
Processing manual pages under /usr/share/man/fr.ISO8859-1...
Purging old database entries in /usr/share/man/uk...
Processing manual pages under /usr/share/man/uk...
Purging old database entries in /usr/share/man/fr...
Processing manual pages under /usr/share/man/fr...
Purging old database entries in /usr/share/man/gl...
Processing manual pages under /usr/share/man/gl...
Purging old database entries in /usr/share/man/ja...
Processing manual pages under /usr/share/man/ja...
Purging old database entries in /usr/share/man/tr...
Processing manual pages under /usr/share/man/tr...
Purging old database entries in /usr/share/man/fr.UTF-8...
Processing manual pages under /usr/share/man/fr.UTF-8...
Purging old database entries in /usr/share/man/id...
Processing manual pages under /usr/share/man/id...
Purging old database entries in /usr/share/man/ca...
Processing manual pages under /usr/share/man/ca...
Purging old database entries in /usr/share/man/es...
Processing manual pages under /usr/share/man/es...
Purging old database entries in /usr/share/man/el...
Processing manual pages under /usr/share/man/el...
Purging old database entries in /usr/share/man/zh_CN...
Processing manual pages under /usr/share/man/zh_CN...
Purging old database entries in /usr/share/man/lt...
Processing manual pages under /usr/share/man/lt...
Purging old database entries in /usr/share/man/nl...
Processing manual pages under /usr/share/man/nl...
Purging old database entries in /usr/share/man/pt...
Processing manual pages under /usr/share/man/pt...
Purging old database entries in /usr/share/man/sr...
Processing manual pages under /usr/share/man/sr...
Purging old database entries in /usr/share/man/sv...
Processing manual pages under /usr/share/man/sv...
Purging old database entries in /usr/share/man/de...
Processing manual pages under /usr/share/man/de...
Purging old database entries in /usr/share/man/it...
Processing manual pages under /usr/share/man/it...
Purging old database entries in /usr/share/man/ar...
Processing manual pages under /usr/share/man/ar...
Purging old database entries in /usr/share/man/ko...
Processing manual pages under /usr/share/man/ko...
Purging old database entries in /usr/share/man/pl...
Processing manual pages under /usr/share/man/pl...
Purging old database entries in /usr/share/man/ru...
Processing manual pages under /usr/share/man/ru...
Purging old database entries in /usr/share/man/ug...
Processing manual pages under /usr/share/man/ug...
Purging old database entries in /usr/share/man/pt_BR...
Processing manual pages under /usr/share/man/pt_BR...
Purging old database entries in /usr/share/man/fi...
Processing manual pages under /usr/share/man/fi...
Processing manual pages under /usr/local/man...
0 man subdirectories contained newer manual pages.
0 manual pages were added.
0 stray cats were added.
0 old database entries were purged.

loke@loke:~$ man ls
man: can't execute most: No such file or directory
man: command exited with status 255: sed -e '/^[[:space:]]*$/{ N; /^[[:space:]]*\n[[:space:]]*$/D; }' | (cd <fd 3> && LESS=-ix8RmPm Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$PM Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$ MAN_PN=ls(1) most)
loke@loke:~$ 

```

---

### Post by zkab on 2017-05-03
loke@loke:~$ MANPAGER=less man ls ... works OK but the env variables gives as follows:

loke@loke:~$ echo $MANPAGER
loke@loke:~$ echo $PAGER
most

---

### Post by #&amp;thj^% on 2017-05-03
```
$ apt policy manpages
manpages:
  Installed: 4.09-2
  Candidate: 4.09-2
  Version table:
 *** 4.09-2 500
        500 http://archive.ubuntu.com/ubuntu zesty/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu zesty/main i386 Packages
        100 /var/lib/dpkg/status


```

---

### Post by zkab on 2017-05-03
Still the same problem ... don't understand what ... man: can't execute most: No such file or directory ... means

```
loke@loke:~$ sudo apt policy manpages
manpages:
  Installed: 4.09-2
  Candidate: 4.09-2
  Version table:
 *** 4.09-2 500
        500 http://se.archive.ubuntu.com/ubuntu zesty/main amd64 Packages
        500 http://se.archive.ubuntu.com/ubuntu zesty/main i386 Packages
        100 /var/lib/dpkg/status
loke@loke:~$ man ls
man: can't execute most: No such file or directory
man: command exited with status 255: sed -e '/^[[:space:]]*$/{ N; /^[[:space:]]*\n[[:space:]]*$/D; }' | (cd <fd 3> && LESS=-ix8RmPm Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$PM Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$ MAN_PN=ls(1) most)

```

---

### Post by steeldriver on 2017-05-03
It's looking for a pager called `most` (because you - or some software you have installed) has defined PAGER=most somewhere (possibly in your ~/.bashrc or ~/.profile, or one of the system-wide equivalents)

If you want the default behavior, you will need to find where that variable is getting defined and remove/change it

---

### Post by #&amp;thj^% on 2017-05-03
Can you run:
```
export MANPAGER=less
```
and then run:
```
/usr/bin/man bash
```
the above will take a small amount of time to populate.

+1 to steeldrivers reply

---

### Post by steeldriver on 2017-05-03
. . . another place to check would be the update-alternatives database

```

update-alternatives --query pager

```

---

### Post by zkab on 2017-05-03
OK - I removed [COLOR="#0000CD"]export PAGER="most"[/COLOR]  in ~/.bashrc and then it worked ...
Thanks !

---

