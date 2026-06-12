---
title: "which package has &quot;mimencode&quot;?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-02-14
I'm looking for the program called "mimencode".  This does the same MIME base-64 encoding/decoding that is done for MIME attachments for email and such.  But it does it as a command for stdin/stdout suitable for use in scripts.  On Slackware, it is in the "metamail-2.7" package.  Ubuntu does have a package called "metamail" but it doesn't appear to be available.  One of the dependencies shows that same version number.

```
lorentz/root /root 77# apt-get install metamail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package metamail is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'metamail' has no installation candidate
lorentz/root /root 78# aptitude show metamail
No current or candidate version found for metamail
Package: metamail
State: not a real package

lorentz/root /root 79# apt-cache dump | awk '{if($1=="Package:"){pre=$2;};print pre ":",$0}' | fgrep metamail
slrn:   Depends: metamail (null)
metamail: Package: metamail
nmh:   Depends: metamail (null)
tin:   Depends: metamail (null)
mime-support:   Depends: metamail 2.7-44
exmh:   Depends: metamail (null)
crm114:   Depends: metamail (null)
topal:   Depends: metamail (null)
lorentz/root /root 80# 
```

---

### Post by anglican on 2011-02-15
> **Skaperen said:**
> I'm looking for the program called "mimencode".  This does the same MIME base-64 encoding/decoding that is done for MIME attachments for email and such.  But it does it as a command for stdin/stdout suitable for use in scripts.  On Slackware, it is in the "metamail-2.7" package.  Ubuntu does have a package called "metamail" but it doesn't appear to be available.  One of the dependencies shows that same version number.

Well you can get it from:

[https://launchpad.net/ubuntu/lucid/+package/metamail](https://launchpad.net/ubuntu/lucid/+package/metamail)

H

---

### Post by Skaperen on 2011-02-16
> **anglican said:**
> Well you can get it from:

[https://launchpad.net/ubuntu/lucid/+package/metamail](https://launchpad.net/ubuntu/lucid/+package/metamail)

H
So what's the deal with this not being available to just "apt-get install metamail"?

---

### Post by anglican on 2011-02-18
> **Skaperen said:**
> So what's the deal with this not being available to just "apt-get install metamail"?Looks like this package is no longer maintained. It's been removed from debian and there's no sign of any activity on it since 2008. Not sure what alternatives there are!

H

---

### Post by Skaperen on 2011-02-23
> **anglican said:**
> Looks like this package is no longer maintained. It's been removed from debian and there's no sign of any activity on it since 2008. Not sure what alternatives there are!

H
If Ubuntu drops packages that are not maintained, what does that mean for a package that works fine and has no bugs?  Would it be treated as "mot maintained" if no updates happen for years?

---

### Post by bluesterror on 2011-08-25
Google sent me here with the same question, so here's an alternative I found (at least in debian):

```

$ munpack file
tempdesc.txt: File exists
xyz.pdf (application/octet-stream)

$ apt-cache show mpack
Package: mpack
Priority: optional
Section: mail
Installed-Size: 84
Maintainer: Anibal Monsalve Salazar <anibal@debian.org>
Architecture: amd64
Version: 1.6-6
Depends: libc6 (>= 2.7-1)
Suggests: mail-transport-agent, inews
Filename: pool/main/m/mpack/mpack_1.6-6_amd64.deb
Size: 41850
MD5sum: d674d9dbfa600464a626e65fbc054e67
SHA1: 3436217fb7f6734cf8264e1a979bc57036a4e3a5
SHA256: b570f68f30aa868297d4ebc1e8c7b857276a3e064e9c6d4252d9e7cfc48ceff8
Description: tools for encoding/decoding MIME messages
 Mpack and munpack are utilities for encoding and decoding
 (respectively) binary files in MIME (Multipurpose Internet
 Mail Extensions) format mail messages. For compatibility
 with older forms of transferring binary files, the munpack
 program can also decode messages in split-uuencoded format.
Homepage: ftp://ftp.andrew.cmu.edu/pub/mpack/
Tag: interface::commandline, role::program, scope::utility, use::storing, works-with::archive, works-with::mail

```

---

### Post by Skaperen on 2011-11-08
> **bluesterror said:**
> Google sent me here with the same question, so here's an alternative I found (at least in debian):

```

$ munpack file
tempdesc.txt: File exists
xyz.pdf (application/octet-stream)

$ apt-cache show mpack
Package: mpack
Priority: optional
Section: mail
Installed-Size: 84
Maintainer: Anibal Monsalve Salazar <anibal@debian.org>
Architecture: amd64
Version: 1.6-6
Depends: libc6 (>= 2.7-1)
Suggests: mail-transport-agent, inews
Filename: pool/main/m/mpack/mpack_1.6-6_amd64.deb
Size: 41850
MD5sum: d674d9dbfa600464a626e65fbc054e67
SHA1: 3436217fb7f6734cf8264e1a979bc57036a4e3a5
SHA256: b570f68f30aa868297d4ebc1e8c7b857276a3e064e9c6d4252d9e7cfc48ceff8
Description: tools for encoding/decoding MIME messages
 Mpack and munpack are utilities for encoding and decoding
 (respectively) binary files in MIME (Multipurpose Internet
 Mail Extensions) format mail messages. For compatibility
 with older forms of transferring binary files, the munpack
 program can also decode messages in split-uuencoded format.
Homepage: ftp://ftp.andrew.cmu.edu/pub/mpack/
Tag: interface::commandline, role::program, scope::utility, use::storing, works-with::archive, works-with::mail

```
It doesn't have "mimencode".  It does have "mpack".  But that doesn't work the same way.  At adds headers as part of the encoding (I want the encoding alone).  The "munpack" program (instead of "mimencode -u") can't handle a file with just the encoding.

---

### Post by leclercqpl on 2013-04-08
Since I've passed a long time looking for "*mimencode*" for Debian Squeeze, I've found that the "**xemacs21-bin**" package provides "*mmencode*". Just add a symlink and you're right.

Works for me :)

Rel.

---

### Post by oldos2er on 2013-04-08
Old thread closed, please don't bump old threads.

---

