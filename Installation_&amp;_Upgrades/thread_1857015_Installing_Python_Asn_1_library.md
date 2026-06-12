---
title: "Installing Python Asn 1 library"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by rohitgoyal18 on 2011-10-09
Hi.
I was trying to work on "Twisted" for creating a chat client.
To install it, i used the command "sudo apt-get install python-twisted".
As usual, it downloaded the necessary files but got stuck at the point where it installs python-pyasn1 0.0.11a-1. i waited for quite some time but it just wont resume. The process is hanging there.
it says
(Reading database ... 
dpkg: warning: files list file for package `python-pyasn1' missing, assuming package has no files currently installed.
(Reading database ... 207513 files and directories currently installed.)
Preparing to replace python-pyasn1 0.0.11a-1 (using .../python-pyasn1_0.0.11a-1_all.deb) ...
Unpacking replacement python-pyasn1 ...


P.S. I have Python3 pre-installed on my system.

Please Help.

---

### Post by MAFoElffen on 2011-10-09
> **rohitgoyal18 said:**
> Hi.
I was trying to work on "Twisted" for creating a chat client.
To install it, i used the command "sudo apt-get install python-twisted".
As usual, it downloaded the necessary files but got stuck at the point where it installs python-pyasn1 0.0.11a-1. i waited for quite some time but it just wont resume. The process is hanging there.
it says
(Reading database ... 
dpkg: warning: files list file for package `python-pyasn1' missing, assuming package has no files currently installed.
(Reading database ... 207513 files and directories currently installed.)
Preparing to replace python-pyasn1 0.0.11a-1 (using .../python-pyasn1_0.0.11a-1_all.deb) ...
Unpacking replacement python-pyasn1 ...


P.S. I have Python3 pre-installed on my system.

Please Help.
I have the python-pyasn1 package installed here.  I don't know if it will help but:
This is what it says for it's installed files:
```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc-base
/usr/share/doc-base/python-pyasn1
/usr/share/doc/python-pyasn1
/usr/share/doc/python-pyasn1/README
/usr/share/doc/python-pyasn1/THANKS
/usr/share/doc/python-pyasn1/TODO
/usr/share/doc/python-pyasn1/changelog.Debian.gz
/usr/share/doc/python-pyasn1/copyright
/usr/share/doc/python-pyasn1/examples
/usr/share/doc/python-pyasn1/examples/snmp.py
/usr/share/doc/python-pyasn1/examples/sshkey.py
/usr/share/doc/python-pyasn1/examples/x509.py
/usr/share/doc/python-pyasn1/notes.html
/usr/share/pyshared
/usr/share/pyshared/pyasn1
/usr/share/pyshared/pyasn1-0.0.11a.egg-info
/usr/share/pyshared/pyasn1-0.0.11a.egg-info/PKG-INFO
/usr/share/pyshared/pyasn1-0.0.11a.egg-info/SOURCES.txt
/usr/share/pyshared/pyasn1-0.0.11a.egg-info/dependency_links.txt
/usr/share/pyshared/pyasn1-0.0.11a.egg-info/top_level.txt
/usr/share/pyshared/pyasn1/__init__.py
/usr/share/pyshared/pyasn1/codec
/usr/share/pyshared/pyasn1/codec/ber
/usr/share/pyshared/pyasn1/codec/ber/decoder.py
/usr/share/pyshared/pyasn1/codec/ber/encoder.py
/usr/share/pyshared/pyasn1/codec/ber/eoo.py
/usr/share/pyshared/pyasn1/codec/cer
/usr/share/pyshared/pyasn1/codec/cer/decoder.py
/usr/share/pyshared/pyasn1/codec/cer/encoder.py
/usr/share/pyshared/pyasn1/codec/der
/usr/share/pyshared/pyasn1/codec/der/decoder.py
/usr/share/pyshared/pyasn1/codec/der/encoder.py
/usr/share/pyshared/pyasn1/error.py
/usr/share/pyshared/pyasn1/type
/usr/share/pyshared/pyasn1/type/base.py
/usr/share/pyshared/pyasn1/type/char.py
/usr/share/pyshared/pyasn1/type/constraint.py
/usr/share/pyshared/pyasn1/type/error.py
/usr/share/pyshared/pyasn1/type/namedtype.py
/usr/share/pyshared/pyasn1/type/namedval.py
/usr/share/pyshared/pyasn1/type/tag.py
/usr/share/pyshared/pyasn1/type/univ.py
/usr/share/pyshared/pyasn1/type/useful.py
/usr/share/python-support
/usr/share/python-support/python-pyasn1.public

```
Here is the depends packages:
```

python (>=2.3)
python-support(>=0.90.00)

```
??? What I don't see it where python-twisted says it has dependencies to python-pysan1... 

One suggestion- What if you installed from synaptic or from aptitude... They have better dependencies logic than apt-get.

---

### Post by rohitgoyal18 on 2011-10-11
Thanks a LOT for your help. 

> **MAFoElffen said:**
> I have the python-pyasn1 package installed here.  I don't know if it will help but:
This is what it says for it's installed files:
What I don't see it where python-twisted says it has dependencies to python-pysan1... 

One suggestion- What if you installed from synaptic or from aptitude... They have better dependencies logic than apt-get.
Actually python-twisted doesn't have any dependency on Asn, but on Python-dev, which in-turn have some dependency on Asn. I don't know, but this library somehow came up automatically during installation and became a pain of my head. 


Anyways, a frustrated reboot followed by an installation attempt from Synaptic Package Manager did the trick for me. So, the problem is solved. This was some issue of apt-get going mad over something internal to it. I am sure people who would be handling remote computers with a terminal would have faced this problem.

---

