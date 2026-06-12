---
title: "I get an ERROR using RarCrack? Help?!"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by Edgar117 on 2011-03-01
Today i installed RarCrack *Perfect*
But when i put # rarcrack tropa de elite.rar --3 --type rar
It gives me this error:
RarCrack! 0.2 by David Zoltan Kedves (kedazo@gmail.com)

ERROR: The specified file (--3) is not exists or 
       you don't have a right permissions!
edgar88@edgar88-laptop:~/Downloads/rarcrack-0.2$ 


Then i tried putting it to my Home Folder but the same ERROR keeps on coming

Any help:popcorn:

---

### Post by linuxd00 on 2011-03-09
try renaming your file so it does not contains any spaces in the filename

---

### Post by mikeannike on 2011-05-16
How did you get it to install properly.  This what i get when i install it.

 
  gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
/bin/sh: xml2-config: not found
In file included from rarcrack.c:21:
rarcrack.h:25:48: error: libxml/xmlmemory.h: No such file or directory
rarcrack.h:26:27: error: libxml/parser.h: No such file or directory
rarcrack.h:27:36: error: libxml/parserInternals.h: No such file or directory
rarcrack.h:28:25: error: libxml/tree.h: No such file or directory
rarcrack.h:29:28: error: libxml/threads.h: No such file or directory
rarcrack.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pwdMutex’
rarcrack.c:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘status’
rarcrack.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘finishedMutex’
rarcrack.c: In function ‘savestatus’:
rarcrack.c:46: error: ‘xmlNodePtr’ undeclared (first use in this function)
rarcrack.c:46: error: (Each undeclared identifier is reported only once
rarcrack.c:46: error: for each function it appears in.)
rarcrack.c:46: error: expected ‘;’ before ‘root’
rarcrack.c:47: error: expected ‘;’ before ‘node’
rarcrack.c:48: error: ‘xmlChar’ undeclared (first use in this function)
rarcrack.c:48: error: ‘tmp’ undeclared (first use in this function)
rarcrack.c:49: error: ‘status’ undeclared (first use in this function)
rarcrack.c:50: error: ‘root’ undeclared (first use in this function)
rarcrack.c:52: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:53: error: ‘node’ undeclared (first use in this function)
rarcrack.c:55: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c:56: error: expected ‘)’ before ‘xmlChar’
rarcrack.c:66: error: expected ‘)’ before ‘xmlChar’
rarcrack.c: In function ‘loadstatus’:
rarcrack.c:87: error: ‘xmlNodePtr’ undeclared (first use in this function)
rarcrack.c:87: error: expected ‘;’ before ‘root’
rarcrack.c:88: error: expected ‘;’ before ‘node’
rarcrack.c:89: error: ‘xmlParserCtxtPtr’ undeclared (first use in this function)
rarcrack.c:89: error: expected ‘;’ before ‘parserctxt’
rarcrack.c:96: error: ‘status’ undeclared (first use in this function)
rarcrack.c:99: error: ‘root’ undeclared (first use in this function)
rarcrack.c:103: error: ‘parserctxt’ undeclared (first use in this function)
rarcrack.c:104: error: ‘node’ undeclared (first use in this function)
rarcrack.c:108: error: ‘XML_SUBSTITUTE_BOTH’ undeclared (first use in this function)
rarcrack.c:127: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c: In function ‘nextpass’:
rarcrack.c:170: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c: In function ‘status_thread’:
rarcrack.c:182: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:188: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:206: warning: comparison between pointer and integer
rarcrack.c:208: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:205: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
rarcrack.c: In function ‘init’:
rarcrack.c:250: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c:251: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:283: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘char (*)[300]’
rarcrack.c:317: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
rarcrack.c: In function ‘main’:
rarcrack.c:351: error: ‘status’ undeclared (first use in this function)
rarcrack.c:353: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c:354: error: ‘finishedMutex’ undeclared (first use in this function)
make: *** [all] Error 1

I looked for libxml2-dev .  But this is whats out: libxml++2.6-2.
Thanks for any help.

---

