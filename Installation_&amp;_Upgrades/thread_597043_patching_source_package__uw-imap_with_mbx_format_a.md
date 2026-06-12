---
title: "patching source package / uw-imap with mbx format as default"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by stbe on 2007-10-30
Hi,

I'm just installing an Ubuntu 7.10 server. I'm familar with Slackware which lacks some really good integrated package management system. So I hope Ubuntu fits my needs. I have my first "problem":

I need an uw-imap server with tools (uw-mailutils contains e.g. dmail) with default mailbox format "mbx". The default ist mbox (unix). The uw-packages of Ubuntu use mbox by default and on Slackware I had to compile uw-imap and imap-tools myself. What's the best way to do this in Ubuntu?

I know how to compile but I'm quite sure that this will break the Ubuntu package management:
- download source of uw-imap
- patch code (for mbx default)
- "make slx"
- make install (or copy executables)

What I'm looking for is something like a source package for uw-* and an automated way to apply my patch before compiling&installing. I can build a patch file (using diff) but do not know how to integrate it so it will be used by something like apt-get update/upgrade.

BTW: the code patch is necessary so IMAP clients will create mbx format mailboxes. I know that I can give the #driver.mbx/ option to uw-mailutils like dmail...

Any hints?

---

### Post by stbe on 2007-10-30
I testet apt-get source and applied my patch. After building my own package I installed it using "dpkg -i".

Is there a way to automate this? The patch is a file which should be applied automatically if I upgrade this package. Is this possible?

The source package has another problem: apt-get update/upgrade will overwrite it on the next run. I do not want to tamper with debian/changelog. I want to get the code improvements by newer packages, too.

I tried aptitude and marked the package "hold and manual" so I could make updates manually (until I find some automatic solution). But this does not work with apt-get! If I accidently run "apt-get upgrade" I will get unpatched versions. Why does apt-get likes binary packages more than my patched source package?

Any hints?

---

