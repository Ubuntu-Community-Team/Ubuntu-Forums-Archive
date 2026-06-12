---
title: "Tracker-extract"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by flamer on 2007-10-20
In gutsy I have a process called tracker-extract and it's using around 50% of my processor. 

I can't kill the process i can only stop it.  Is this a bug?

[[img]http://shrani.si/t/37/PV/25gn9YNc/screenshot1.jpg[/img]](http://shrani.si/?37/PV/25gn9YNc/screenshot1.png)

---

### Post by Ted_Smith on 2008-01-19
> 
 tracker-extract - extract metadata from file and display them.

SYNOPSYS
       tracker-extract file

DESCRIPTION
       tracker-extract  read  the  file  provided in paramater and extract the
       metadata from this file; then it displays the metadata on the  standard
       output.

SEE ALSO
       trackerd(1)


It's apparently an indexer for desktop searches to make your searches faster.

---

### Post by mcduck on 2008-01-19
I've had the same problem for last couple of days. Probably I have some file somewhere that causes problems for Tracker.

I've solved the problem simply by killing trackerd (with 'killall trackerd').

---

