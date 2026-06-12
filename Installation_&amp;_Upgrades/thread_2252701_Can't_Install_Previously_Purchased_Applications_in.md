---
title: "Can't Install Previously Purchased Applications in Ubuntu 14.10"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by stevedude on 2014-11-13
I tried to upgrade from Ubuntu 14.04 to 14.10, 64-bit, but had issues, so I did a fresh install of 14.10, 64-bit. I had previously purchased a few programs via the Ubuntu Software Center (USC) like the "Steel Storm" game, a MP3 convertor, and a few others. Typically, if I had to reinstall these programs, Ubuntu Software Center's File Menu had a menu choice labeled "Previously installed purchases.." that listed your programs and by clicking on them, would reinstall them on your system.

The list still appears and my programs are listed, but when I attempt to install them, I get a warning in USC stating "Purchased on *XYZ DATE*, but not available for your current Ubuntu version. Please contact the vendor for an update".

I have never had that happen before. I am contacting the vendors, however, this is very inconvenient. Anyone else run into this? I never read/heard of any news that this type of thing would happen with this version of Ubuntu.

---

### Post by TheFu on 2014-11-13
The OS is changed. Old versions of programs may or may not work under the new OS. This is due to some of the core libraries being changed. Sometimes these are not backwards compatible. Whether that is the case for these specific applications or not, only the vendor knows.  Canonical just provides a market, support for the programs is completely up to each vendor.

Being on a non-LTS release may not be a good idea if system stability is required.  There are [other reasons]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release") to only use LTS too, IMHO.

---

### Post by stevedude on 2014-11-14
Thanks for the feedback.
Steel Storm, as one example, is still in the apps directory. I D/L and installed a demo that is working, so I know its not a compatibility issue. Youtube to M3 convertor was another program. I obtained a copy from the developer and it runs fine. I could see a few of them not being available, but all of them?  I'll check around for bug reports to see if this is a known issue that others reported too.

Still scratching my head on this one...

---

### Post by stevedude on 2014-11-14
As I suspected - A bug, filed under Bug #1391166, Ubuntu Software Center

---

### Post by TheFu on 2014-11-15
I'm thinking either the vendors were too specific on the required versions when they built the packages - "version X=y.zz" instead of saying
"version X >= y.zz" .... or Canonical's vendor store doesn't support that and requires the vendors to agree to some new change in policy for every release.

To be clear, I don't know - never used software center in my life and only use F/LOSS programs these days.

---

