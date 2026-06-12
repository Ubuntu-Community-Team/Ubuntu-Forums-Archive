---
title: "update installing exe (win binaries) now :p"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-24
That's funny. dist-upgrade just made me download a bunch of exe files. Font related:

```

--2009-10-25 01:28:04--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://kent.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-25 01:28:05--  http://kent.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      537K/s   in 0.4s    
2009-10-25 01:28:05 (537 KB/s) - `./andale32.exe' saved [198384/198384]
--2009-10-25 01:28:06--  http://downloads.sourceforge.net/corefonts/arial32.exe
2009-10-25 01:28:07 (892 KB/s) - `./arial32.exe' saved [554208/554208]
etc......

```
It's probably wine related.
It made me go: huh? :D

---

### Post by lisati on 2009-10-24
I've seen similar before. Some .exe files are really "[self extracting]("http://en.wikipedia.org/wiki/Self-extracting_archive")" archive files. It does seem a bit odd however to use them with a Linux-based distro.

---

### Post by sisco311 on 2009-10-24
Microsoft TrueType fonts

---

### Post by zekopeko on 2009-10-24
try doing

locate *.exe

and be surprised that a default install of Ubuntu has .exe files

---

### Post by whoop on 2009-10-25
> **zekopeko said:**
> try doing

locate *.exe

and be surprised that a default install of Ubuntu has .exe files

I know, this is all very unsettling #-o

---

### Post by sisco311 on 2009-10-25
> **whoop said:**
> I know, this is all very unsettling #-o

Why? The fonts are "free" and the .exe files are self-extracting archives.

[http://corefonts.sourceforge.net/faq8.htm]("http://corefonts.sourceforge.net/faq8.htm")

[http://corefonts.sourceforge.net/eula.htm]("http://corefonts.sourceforge.net/eula.htm")

---

### Post by JillSwift on 2009-10-25
> **sisco311 said:**
> Why? The fonts are "free" and the .exe file are self-extracting archives.

[http://corefonts.sourceforge.net/faq8.htm](http://corefonts.sourceforge.net/faq8.htm)

[http://corefonts.sourceforge.net/eula.htm](http://corefonts.sourceforge.net/eula.htm)
A couple of 'em appear to be related to mono/.NET

---

### Post by whoop on 2009-10-25
> **sisco311 said:**
> Why? The fonts are "free" and the .exe files are self-extracting archives.

[http://corefonts.sourceforge.net/faq8.htm]("http://corefonts.sourceforge.net/faq8.htm")

[http://corefonts.sourceforge.net/eula.htm]("http://corefonts.sourceforge.net/eula.htm")

I'm just kidding...

---

