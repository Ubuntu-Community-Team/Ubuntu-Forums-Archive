---
title: "Latest updates - What's this MIB thing ?"
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-12-01
While doing some updates today via terminal 
```
sudo aptitude safe-upgrade
```
I got this:
```
Downloading RFCs and IANA documents and extracting MIB files.
This will take some minutes.

In case this process fails, it can always be repeated later by executing
cd /usr/share/mibs
make -f Makefile.mib

[ -d /usr/share/mibs/iana.orig ] || mkdir /usr/share/mibs/iana.orig
cat ianalist | while read file mibs; \
		do \
		  if [ "$file" != "#" ]; \
		  then \
		    ./mibfetch -d /usr/share/mibs/iana.orig -x http://www.iana.org assignments $file $mibs; \
		  fi; \
		done
[ -d /usr/share/mibs/ietf.orig ] || mkdir /usr/share/mibs/ietf.orig
cat rfclist | while read rfc mibs; \
		do \
		  if [ "$rfc" != "#" ]; \
		  then \
		    ./mibfetch -d /usr/share/mibs/ietf.orig http://www.rfc-editor.org rfc $rfc $mibs; \
		  fi; \
		done
NOTE: SMUX: ignored.
NOTE: FIZBIN-MIB: ignored.
NOTE: : ignored.
NOTE: : ignored.
NOTE: IANA-PRINTER-MIB: ignored.
NOTE: IANA-FINISHER-MIB: ignored.
NOTE: IANA-ITU-ALARM-TC-MIB: ignored.
NOTE: IANA-GMPLS-TC-MIB: ignored.
NOTE: IANA-MAU-MIB: ignored.
patch -d /usr/share/mibs/ietf.orig < rfcmibs.diff; \
	rm -f /usr/share/mibs/ietf.orig/*orig
patching file ADSL-LINE-MIB
patching file DLSW-MIB
patching file DSA-MIB
patching file FDDI-SMT73-MIB
patching file HPR-MIB
patching file MIP-MIB
patching file Modem-MIB
patching file PPP-LCP-MIB
patching file RDBMS-MIB
patching file RFC1414-MIB
patching file SNA-NAU-MIB
patching file TCPIPX-MIB
patching file UPS-MIB
patching file SMUX-MIB
rm -fr /usr/share/mibs/iana
rm -fr /usr/share/mibs/ietf
mkdir /usr/share/mibs/iana
mkdir /usr/share/mibs/ietf
cp /usr/share/mibs/iana.orig/* /usr/share/mibs/iana
cp /usr/share/mibs/ietf.orig/* /usr/share/mibs/ietf
rm -fr *orig

```
What's this and did it fail?

---

### Post by knarf on 2009-12-01
MIB stands for Management Information Base. The files contain formal descriptions of management interfaces for use by SNMP and other remote management protocols. The files are written in (a subset of) ASN.1 which is Another Fine Acronym for Abstract Syntax Notation version 1, a standard notation for describing data structures. Have a look at those files, they are quite readable...

As to whether the process failed I have no idea, the update has not shown up here yet...

edit:

It looks like it did not fail by the way...

---

### Post by Kevbert on 2009-12-01
Thanks. I'm connected to the main server for updates. It's the first time I've seen a script running when installing updates.

---

### Post by philinux on 2009-12-01
Same here. Not sure if it was successful or not. :confused:

---

### Post by hikaricore on 2009-12-01
Men In Black  ^_^

---

### Post by ranch hand on 2009-12-01
> **hikaricore said:**
> Men In Black  ^_^
Now see, we can all learn something new.

I hope that my box doesn't "flash" me.

---

### Post by Kevbert on 2009-12-01
Well I know we've been having problems with flash, but I didn't think it was this.:P:p:P

---

### Post by BwackNinja on 2009-12-01
I had that, and it didn't seem like it failed and it looked like yours, it just took a really long time.

---

### Post by mrsurb on 2009-12-01
Mine's been going for a bit over an hour so far:

```


Downloading RFCs and IANA documents and extracting MIB files.
This will take some minutes.

In case this process fails, it can always be repeated later by executing
cd /usr/share/mibs
make -f Makefile.mib

[ -d /usr/share/mibs/iana.orig ] || mkdir /usr/share/mibs/iana.orig
cat ianalist | while read file mibs; \
                do \
                  if [ "$file" != "#" ]; \
                  then \
                    ./mibfetch -d /usr/share/mibs/iana.orig -x http://www.iana.org assignments $file $mibs; \
                  fi; \
                done
WARNING: Module(s) not found: IANAifType-MIB 
WARNING: Module(s) not found: IANA-LANGUAGE-MIB 
WARNING: Module(s) not found: IANA-ADDRESS-FAMILY-NUMBERS-MIB 
WARNING: Module(s) not found: IANA-RTPROTO-MIB 
WARNING: Module(s) not found: IANATn3270eTC-MIB 
WARNING: Module(s) not found: IANA-MALLOC-MIB 
WARNING: Module(s) not found: IANA-CHARSET-MIB 
WARNING: Module(s) not found: IANA-PRINTER-MIB 
WARNING: Module(s) not found: IANA-FINISHER-MIB 
WARNING: Module(s) not found: IANA-ITU-ALARM-TC-MIB 
[ -d /usr/share/mibs/ietf.orig ] || mkdir /usr/share/mibs/ietf.orig
cat rfclist | while read rfc mibs; \
                do \
                  if [ "$rfc" != "#" ]; \
                  then \
                    ./mibfetch -d /usr/share/mibs/ietf.orig http://www.rfc-editor.org rfc $rfc $mibs; \
                  fi; \
                done
WARNING: Module(s) not found: RFC1155-SMI 


```

I'll take people's word for it that this is working. I hope that the process can be somewhat streamlined or made more informative for all the people upgrading from karmic to lucid in April next year.

---

### Post by ranch hand on 2009-12-01
A hour seems a little on the long side.  Mine might have taken 10 to 12 minutes on the three 10.04 installs I have.  They were all about the same even with three fairly different backgrounds.

---

### Post by Kevbert on 2009-12-01
Same sort of time, 10-15 minutes, on 2 separate installs.

---

### Post by Gina on 2009-12-02
I have the flash problem on my laptop (only).  Removing "flash" from the boot line got round it by not showing the flash screen.

I like the Men In Black quip :lolflag:

---

