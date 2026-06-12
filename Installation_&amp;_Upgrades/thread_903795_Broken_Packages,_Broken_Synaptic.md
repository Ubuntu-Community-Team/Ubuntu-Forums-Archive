---
title: "Broken Packages, Broken Synaptic"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by globose on 2008-08-28
I'm running Hardy on a 64-bit system.

While browsing the options in Synaptic, I decided I would upgrade every package I could by using the upgradeable (upstream) filter and then clicked on "upgrade all" or something like that.  The upgrade aborted partway through (unfortunately I didn't save the error that it gave at that time).

The end result is that synaptic says I have three broken packages: Perl, libperl5.10, and libhtml-parser-perl.  If I try to fix broken packages, I get this error:

> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I thought maybe I could fix the problem by uninstalling perl 5.10 (all three broken packages) and reinstall 5.8, but when I choose "mark for complete removal" (mark for removal is not available), it mandates that I delete every program that depends on perl (which seems to be almost everything).

I also tried to force version back to 5.8, but that also mandates that I delete all the programs that depend on it.

If I try sudo apt-get -f install , I get this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libhtml-parser-perl: Depends: perlapi-5.10.0 but it is not installable
  libperl5.10: Depends: perl-base (= 5.10.0-11.1) but 5.8.8-12 is installed
  perl: Depends: perl-base (= 5.10.0-11.1) but 5.8.8-12 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


Is there anybody who has any suggestions on what else I should try?  Otherwise I guess my only other option is to do a fresh install of Hardy.

---

### Post by rx8mep on 2008-08-28
I'm actually having a similar problem for about a week or two now. I will click on my Red arrow that shows i need a update for my ubuntu hardy 8.04 and I get this now: 

Not all updates can be installed. 

It gives me the options to do a partial upgrade. I have my ubuntu looking like a mac, with the AWN on the bottom and I installed some unofficeal packages, so I understand that I have to do a partial upgrade. I followed this guide, actually: 
[http://www.rowtheboat.com/archives/17](http://www.rowtheboat.com/archives/17)

But when I actually tried to run the partial upgrade it says:

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

libtag1c2a

I don't know what that is, but I'm assuming that if I get rid of that then I will be able to do my system updates.

EDIT: If it makes any difference it was working for a good two months with the mac-like installations that I've done before I've had this problem.

---

