---
title: "update manager does not access network"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by michaelvogt on 2010-12-15
Hello everybody.

I upgraded my desktop from 9.10 to 10.04. The updated system works without problem - except that apt-get/Update Manager/Synamptic does not connect to the net anymore.

When I try to check for updates with the update manager, I get the message below. I have set different servers with the same result, and checked if there is a proxy set up somewhere, which is not. I also tried apt-get with the fix flag.

When I access the uri's with a browser, that works without a problem.

Any idea what's the problem here?


Thanks,
Michael


Message from update manager:

Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/Release.gpg](http://mirror.netcologne.de/ubuntu/dists/lucid/Release.gpg)  Could not connect to mirror.netcologne.de:80 (194.8.197.22). - connect (110: Connection timed out)
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/Release.gpg](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/Release.gpg](http://mirror.netcologne.de/ubuntu/dists/lucid-security/Release.gpg)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/main/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/universe/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/Release.gpg](http://mirror.netcologne.de/ubuntu/dists/lucid/Release.gpg)  Could not connect to mirror.netcologne.de:80 (194.8.197.22). - connect (110: Connection timed out)
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/Release.gpg](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/Release.gpg](http://mirror.netcologne.de/ubuntu/dists/lucid-security/Release.gpg)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/main/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid/universe/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/main/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://mirror.netcologne.de/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to mirror.netcologne.de:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by matt_symes on 2010-12-15
Hi

Have you tried a different mirror?

Kind regards

---

### Post by akand074 on 2010-12-15
> **matt_symes said:**
> Hi

Have you tried a different mirror?

Kind regards

I was going to suggest the same thing. 

Go to System > Administration > Synaptic Package Manager (Though software sources might still be in 10.04 if I remember correctly, either way). Once your in Synaptic go to Settings > Repository and in the download from box choose other and have it select best server.

---

### Post by q999 on 2010-12-15
mirror links look good mirror /responds to ftp/
check network.. are you connected?

---

### Post by michaelvogt on 2010-12-20
> **q999 said:**
> mirror links look good mirror /responds to ftp/
check network.. are you connected?

Yes. I write this on the computer that shows the problem. So general internet access is fine.

And yes, as I wrote, I tried different mirrors.

Still stuck with this problem.


Greetings,
Michael

---

### Post by sikander3786 on 2010-12-20
> **michaelvogt said:**
> Yes. I write this on the computer that shows the problem. So general internet access is fine.

And yes, as I wrote, I tried different mirrors.

Still stuck with this problem.


Greetings,
Michael
Did you try the Main Server? Software Center > Edit > Software Sources > Main Server.

And once you switch to Main Server, we need to see the output of apt-get update once more.

The mirror that is configured on your System seems down at the moment. It is not responding here either. So, try the Main Server and keep us posted :-)

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

Thanks.

---

### Post by michaelvogt on 2010-12-22
Hello all.

Thank you for all your help.

It turns out, that the update manager and Synaptic require separate proxy settings, in addition to the proxy set in the network proxy system preference. Once entered, I could at least get Synaptic to work.


Thanks,
Michael

---

### Post by racsoarias on 2011-01-13
Thank you akand07, your method worked very well.
Go to System > Administration > Synaptic Package Manager (Though software sources might still be in 10.04 if I remember correctly, either way). Once your in Synaptic go to Settings > Repository and in the download from box choose other and have it select best server.

---

