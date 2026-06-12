---
title: "GnuCash S/W Level Issue"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by asearles on 2007-09-26
I have been using Red Hat and Fedora for the past 5-6 yers, and I recently had the impulse to jump to a Debian-based distribution... so I backed up what I needed... formated my hard drives... and installed Ubuntu.

So far, I have been quite please with Ubuntu. I was quite comfortable using an RPM-based dist, but I am hoping to learn more about Debian systems.

Anyway... one small problem I have found concerns GnuCash. The version I left Fedora with was  GnuCash 2.2.1-2...... but under Ubuntu the version is  2.0.1-1.

Now, when I restore my GnuCash data, (all my home accounting info), the (Ubuntu) GnuCash is detecting invalid data. Bottom-line I need to upgrade my GnuCash.

Not being too familiar with the Debian system, I am wondering if I should...
      a) wait for the next release of Ubuntu... and hope that GnuCash is at version 2.2.1-2 or greater.... would sound like a long wait... I don't know
      b) search the Internet for a Debian package for GnuCash 2.2.1-2 ..... but I am wondering if there might be some conflicts with Ubuntu..... or maybe not
      c)  un-install GnuCash 2.0.1-1 from my system... and then download/install a GZ tarball package... and build-install the code directly

Suggestions would be appreciated. Thanks.

/Alan

---

### Post by mdebusk on 2007-09-26
> **asearles said:**
> 
c)  un-install GnuCash 2.0.1-1 from my system... and then download/install a GZ tarball package... and build-install the code directly

I found that [these instructions](http://wiki.gnucash.org/wiki/Building#Feisty) were all I needed to get GnuCash compiled on my Feisty system. (I haven't tried moving my Quicken data to it yet, though. Too many demands on my time, and too little resolve to say "no" to them.)

---

### Post by elsaturnino on 2007-09-26
I actually compiled the latest version of GNUCash on Feisty about a week ago. Other than installing several dev packages to satisfy dependencies, it went off without a hitch.  You could do that and install it to some non-default directory (e.g. /opt/gnucash) so that once the official ubuntu package version catches up, you can switch to that.

---

### Post by arthurginspain on 2007-09-27
go here for .deb file  its gnucash 2.2.1

[http://www.getdeb.net/search.php?keywords=gnucash](http://www.getdeb.net/search.php?keywords=gnucash)


good luck

---

### Post by asearles on 2007-09-27
Thanks for the suggestions... I decided to download the  .deb files.  So I now have the following three files sitting on my harddrive:

   gnucash-docs_2.2.0-1~getdeb1_all.deb
   gnucash-common_2.2.1-1~getdeb1_all.deb
   gnucash_2.2.1-1~getdeb1_i386.deb

Now if I were in familiar territory, (Fedora Linux), and I had a handful of  RPMs in a folder, I could simply issue the command...   rpm  -i  package1 package2      .... and they would be magically installed.

However, now I am working within a debian environment.

I am assuming there would be a similar CLI command to install   .deb  files sitting in a local directory. Does anyone know what it is??????  I am aware of  "apt-get", "aptitude", and "Synaptic Package Manager".... but they appear to want to install  .deb files from the Internet... not a local folder. (But then, I could be totally wrong)

Thanks.

/Alan

---

### Post by arthurginspain on 2007-09-28
you need t o install using the Gdebi package installer this sits in 

1.
applications
system tools
Gdebi

if you can't see the system tools menu go to applications

right click on applications
Edit Menus

look for system tools it should have a tick in the box if not click on the box to enable - then do the above

2. or you could just double click on the deb files which will bring up gdebi - then click on install

regards

---

### Post by asearles on 2007-09-28
Gdebi did the trick !!!  All is well. Thanks very much for your help.

/Alan

---

### Post by arthurginspain on 2007-09-29
good to hear your working ok

take care

---

