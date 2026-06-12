---
title: "openoffice upgrade problem with 10.10"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by REHIII on 2011-04-24
Greetings, green user here. Synaptic is telling me I have broken packages. The broken filter lists the openoffice files. Trying to fix using synaptic or, using the terminal gives the same error:

Preparing to replace openoffice.org-core 1:3.2.1-7ubuntu1 (using .../openoffice.org-core_1%3a3.2.1-7ubuntu1.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
xz: (stdin): Unexpected end of input
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a3.2.1-7ubuntu1.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/openoffice/basis3.2/program/liblocaledata_en.so'
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a3.2.1-7ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Suggestions? Until I get this resolved, i can't use the Software Center. Thanks

---

### Post by Dale61 on 2011-04-24
Completely remove OpenOffice, and install LibreOffice.

OpenOffice is now owned by Oracle, who were wanting to make it commercial software, but most of the developers left and started The Document Foundation, and out of that came LibreOffice.

Basically, LO is the same as OO, but with a different name, and continued support.

LibreOffice can be found in Synaptic (at least it is here).

---

### Post by ptn107 on 2011-04-25
It is no longer commercial software[1].

[1]http://www.pcworld.com/businesscenter/article/225357/oracle_gives_up_on_commercial_open_office.html

---

### Post by gpdas on 2011-04-25
Hi
If I type 'libreoffice' in Ubuntu Software Centre' then no item is shown.
Kindly suggest how to install it. Thanks.

---

### Post by Dale61 on 2011-04-25
> **ptn107 said:**
> It is no longer commercial software

I never said it WAS commercial software, only that Oracle were seriously thinking about making it so, and that is why so many of the developers left after the take-over.

---

### Post by Dale61 on 2011-04-25
> **gpdas said:**
> Hi
If I type 'libreoffice' in Ubuntu Software Centre' then no item is shown.
Kindly suggest how to install it. Thanks.

I have it listed in Synaptic, but I honestly can't remember how I got it there.  If you google it, you will find a way to install, but from all reports, it will be the default in 11.04 (which for us in Australia, is only 3 days away - 28 April).

---

### Post by Dale61 on 2011-04-25
Go [here]("http://www.techdrivein.com/2011/01/remove-openoffice-and-install.html") to remove OO and install LO via PPA.

---

### Post by REHIII on 2011-05-01
Solved with upgrade to 11.04 and installation of LibreOffice

---

