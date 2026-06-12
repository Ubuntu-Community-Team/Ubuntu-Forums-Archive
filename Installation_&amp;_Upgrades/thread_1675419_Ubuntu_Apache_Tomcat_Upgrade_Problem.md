---
title: "Ubuntu Apache Tomcat Upgrade Problem"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by howtechstuffworks on 2011-01-25
HI All,
      I got an update newsletter from ubuntu thread. I am not sure how to Upgrade since I am already running an server in apache Tomcat. Is it possible to update with apt-get....???

Thanks everyone.

****************************************************************
Send ubuntu-security-announce mailing list submissions to
       [email]ubuntu-security-announce@lists.ubuntu.com[/email]

To subscribe or unsubscribe via the World Wide Web, visit
       [https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)
or, via email, send a message with subject or body 'help' to
       [email]ubuntu-security-announce-request@lists.ubuntu.com[/email]

You can reach the person managing the list at
       [email]ubuntu-security-announce-owner@lists.ubuntu.com[/email]

When replying, please edit your Subject line so it is more specific
than "Re: Contents of ubuntu-security-announce digest..."


Today's Topics:

  1. [USN-1047-1] AWStats vulnerability (Marc Deslauriers)
  2. [USN-1048-1] Tomcat vulnerability (Marc Deslauriers)


----------------------------------------------------------------------

Message: 1
Date: Mon, 24 Jan 2011 09:45:30 -0500
From: Marc Deslauriers <marc.deslauriers@canonical.com>
To: [email]ubuntu-security-announce@lists.ubuntu.com[/email]
Cc: [email]full-disclosure@lists.grok.org.uk[/email], [email]bugtraq@securityfocus.com[/email]
Subject: [USN-1047-1] AWStats vulnerability
Message-ID: <1295880330.3101.107.camel@localhost>
Content-Type: text/plain; charset="utf-8"

===========================================================
Ubuntu Security Notice USN-1047-1          January 24, 2011
awstats vulnerability
CVE-2010-4369
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 6.06 LTS
Ubuntu 8.04 LTS
Ubuntu 9.10
Ubuntu 10.04 LTS
Ubuntu 10.10

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 6.06 LTS:
 awstats                         6.5-1ubuntu1.4

Ubuntu 8.04 LTS:
 awstats                         6.7.dfsg-1ubuntu0.2

Ubuntu 9.10:
 awstats                         6.9~dfsg-1ubuntu3.9.10.1

Ubuntu 10.04 LTS:
 awstats                         6.9~dfsg-1ubuntu3.10.04.1

Ubuntu 10.10:
 awstats                         6.9.5~dfsg-3ubuntu0.1

In general, a standard system update will make all the necessary changes.

Details follow:

It was discovered that AWStats did not correctly filter the LoadPlugin
configuration option. A local attacker on a shared system could use this
to inject arbitrary code into AWStats.


Updated packages for Ubuntu 6.06 LTS:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5-1ubuntu1.4.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5-1ubuntu1.4.diff.gz)
     Size/MD5:    20512 a821b60de3f940338b9e43e5ff5d29f1
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5-1ubuntu1.4.dsc](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5-1ubuntu1.4.dsc)
     Size/MD5:     1426 403908718ed4d34bb4c728223e810a12
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5.orig.tar.gz)
     Size/MD5:  1051780 aef00b2ff5c5413bd2a868299cabd69a

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5-1ubuntu1.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.5-1ubuntu1.4_all.deb)
     Size/MD5:   853586 4c2853cd9169247899b6036dc7cfa198

Updated packages for Ubuntu 8.04 LTS:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg-1ubuntu0.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg-1ubuntu0.2.diff.gz)
     Size/MD5:    23771 4776192ee160583ce30b21f5fbe66003
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg-1ubuntu0.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg-1ubuntu0.2.dsc)
     Size/MD5:     1620 492ba4f3e2f2ffe51aa9a97fca7783c6
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg.orig.tar.gz)
     Size/MD5:  1093568 98a5fad9c379ac4884d7af90db6e087b

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg-1ubuntu0.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.7.dfsg-1ubuntu0.2_all.deb)
     Size/MD5:   908096 e8f1bd0f9db064a57cf9c23a3fe20686

Updated packages for Ubuntu 9.10:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.9.10.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.9.10.1.diff.gz)
     Size/MD5:    45789 b44d3b7fcf2d4bc5a0eeda3dec3fc412
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.9.10.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.9.10.1.dsc)
     Size/MD5:     2198 82f778a33dc5bc99d38e270902caf233
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg.orig.tar.gz)
     Size/MD5:  1127895 460c03a07b2e4d9a9ada6a7f320d46e8

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.9.10.1_all.deb)
     Size/MD5:   951444 83e6faf9324669b08ba9ce95dc5ecc00

Updated packages for Ubuntu 10.04 LTS:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.10.04.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.10.04.1.diff.gz)
     Size/MD5:    45789 f21c60b02413fc47263702e37bbd317c
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.10.04.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.10.04.1.dsc)
     Size/MD5:     2202 2536cf6fe0fbec527f16cf6e5e3ada47
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg.orig.tar.gz)
     Size/MD5:  1127895 460c03a07b2e4d9a9ada6a7f320d46e8

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9~dfsg-1ubuntu3.10.04.1_all.deb)
     Size/MD5:   951338 abc39ddeee9b7efd15c68baf255fa419

Updated packages for Ubuntu 10.10:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg-3ubuntu0.1.debian.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg-3ubuntu0.1.debian.tar.gz)
     Size/MD5:    39502 4b1e14b2bdf3439924c392b6a18d8cd6
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg-3ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg-3ubuntu0.1.dsc)
     Size/MD5:     2184 8ea4ef44ccb7af39a7cbf04505e05f6f
   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg.orig.tar.gz)
     Size/MD5:  1145006 af006dff266dfebd66baf5361350a805

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg-3ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/awstats/awstats_6.9.5~dfsg-3ubuntu0.1_all.deb)
     Size/MD5:   973788 4178bd568c444de4508131d828f43322



-------------- next part --------------
A non-text attachment was scrubbed...
Name: signature.asc
Type: application/pgp-signature
Size: 836 bytes
Desc: This is a digitally signed message part
URL: <https://lists.ubuntu.com/archives/ubuntu-security-announce/attachments/20110124/a1f49473/attachment-0001.pgp>

------------------------------

Message: 2
Date: Mon, 24 Jan 2011 09:46:09 -0500
From: Marc Deslauriers <marc.deslauriers@canonical.com>
To: [email]ubuntu-security-announce@lists.ubuntu.com[/email]
Cc: [email]full-disclosure@lists.grok.org.uk[/email], [email]bugtraq@securityfocus.com[/email]
Subject: [USN-1048-1] Tomcat vulnerability
Message-ID: <1295880369.3101.109.camel@localhost>
Content-Type: text/plain; charset="utf-8"

===========================================================
Ubuntu Security Notice USN-1048-1          January 24, 2011
tomcat6 vulnerability
CVE-2010-4172
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 9.10
Ubuntu 10.04 LTS
Ubuntu 10.10

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 9.10:
 tomcat6-admin                   6.0.20-2ubuntu2.3

Ubuntu 10.04 LTS:
 tomcat6-admin                   6.0.24-2ubuntu1.6

Ubuntu 10.10:
 tomcat6-admin                   6.0.28-2ubuntu1.1

In general, a standard system update will make all the necessary changes.

Details follow:

It was discovered that Tomcat did not properly escape certain parameters in
the Manager application which could result in browsers becoming vulnerable
to cross-site scripting attacks when processing the output. With cross-site
scripting vulnerabilities, if a user were tricked into viewing server
output during a crafted server request, a remote attacker could exploit
this to modify the contents, or steal confidential data (such as
passwords), within the same domain.


Updated packages for Ubuntu 9.10:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20-2ubuntu2.3.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20-2ubuntu2.3.diff.gz)
     Size/MD5:    27239 0cc20bab1a9b311bdebf30b7906a19a7
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20-2ubuntu2.3.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20-2ubuntu2.3.dsc)
     Size/MD5:     2204 34fb37d15fe193f6def5becb76b0dbaf
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20.orig.tar.gz)
     Size/MD5:  3590562 44f49e7e14028b6a53c3c346bd18c72f

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java-doc_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java-doc_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:   247424 a14215f5c3cb7ac653b68f16053b945d
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:   183264 4b6b468e0f349e856f56d599573c1600
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:  2914890 6007d0180bd5bfd7430cee707dd60336
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-admin_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-admin_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:    39086 c6667d042139ff18b6ce16a4a7d136f9
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:    36804 cf0938f04b4264bbb828eb038d6a2f7b
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-docs_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-docs_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:   480290 9963984b5b9af8ca130cfd714d7be6b9
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-examples_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-examples_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:   419290 4ac9738375f53bf57ba4a00dad5c234a
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-user_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-user_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:    21918 b2f4ab22cfa41f0f3a16af0eb75355ff
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.20-2ubuntu2.3_all.deb)
     Size/MD5:    26318 1a1de7f4532d0b13c778d9d9c181fe74

Updated packages for Ubuntu 10.04 LTS:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24-2ubuntu1.6.debian.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24-2ubuntu1.6.debian.tar.gz)
     Size/MD5:    32782 d369c0e8ab9ef06c320a74ba10c5e361
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24-2ubuntu1.6.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24-2ubuntu1.6.dsc)
     Size/MD5:     2405 2ee1921228239791f5aab04bc2bf6c48
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24.orig.tar.gz)
     Size/MD5:  3262568 0bc48af723d6fee31e404434b3744f66

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java-doc_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java-doc_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:   255532 3e126e0a1561b296d78e5713c42b6196
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:   190776 82973dee7e623299449cced7e3bafd50
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:  3008498 cfc272e2ad4ae852f0507d2ada8f0ad8
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-admin_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-admin_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:    42094 19948285f4a71219c5f4683f8b4707a8
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:    46300 bff1f177657f45b5de8f9a6b4b875bd9
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-docs_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-docs_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:   509958 95aacb34a537e9c8f80cc0b6c20272c6
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-examples_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-examples_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:   157790 4e30309eb658f3e0d272d7a80afe3ddd
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-user_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-user_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:    25402 c4b54a4b984665b2a8ba0f7aaf49f6f6
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24-2ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.24-2ubuntu1.6_all.deb)
     Size/MD5:    31424 376f9f72e7ed8b763bf9ad9bd5845003

Updated packages for Ubuntu 10.10:

 Source archives:

   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28-2ubuntu1.1.debian.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28-2ubuntu1.1.debian.tar.gz)
     Size/MD5:    34180 9a58889c9a818f3932ab3fb06e07a0c2
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28-2ubuntu1.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28-2ubuntu1.1.dsc)
     Size/MD5:     2360 b88dde12cb761f398c6cb2848a68d5ca
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28.orig.tar.gz)
     Size/MD5:  3114279 c3d696609054be07a55c14a7de1b8ddf

 Architecture independent packages:

   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java-doc_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java-doc_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:   247884 76667eab1aea739baa2f6e94bf77922a
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:   191520 5a00687018dd7bc449d003a0183e32ac
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:  3025018 77ef8e9a0eb75bd69c1425f3633ae88e
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-admin_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-admin_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:    42388 41a06ce99f6d62589b2bf9ed2d015759
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:    47302 91d28d83c8c1ef5f39f517882b01151e
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-docs_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-docs_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:   513714 141ddd468004ffc97660ab49f2b7e6f9
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-examples_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-examples_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:   160756 1878b3c23e566f3c5478ea5dc783fd80
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-user_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-user_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:    25938 9484ebad8612001220014e38807e9359
   [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.28-2ubuntu1.1_all.deb)
     Size/MD5:    32822 93254c4418a7645582196bea71a3aff6



-------------- next part --------------
A non-text attachment was scrubbed...
Name: signature.asc
Type: application/pgp-signature
Size: 836 bytes
Desc: This is a digitally signed message part
URL: <https://lists.ubuntu.com/archives/ubuntu-security-announce/attachments/20110124/8164e62f/attachment-0001.pgp>

------------------------------

--
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)


End of ubuntu-security-announce Digest, Vol 76, Issue 12
********************************************************

---

