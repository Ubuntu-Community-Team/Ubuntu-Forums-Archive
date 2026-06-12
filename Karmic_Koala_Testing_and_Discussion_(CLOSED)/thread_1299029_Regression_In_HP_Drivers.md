---
title: "Regression In HP Drivers?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2009-10-23
I just did a fresh install of Karmic Release Candidate...Kubuntu 64 bit.  I installed the hp-gui, as I have done with all previous versions and ran sudo hp-setup to set up my HP OfficeJet 6300 Series multi-function printer (on my network)

The HP Setup GUI ran as it normally does, but unlike with the Beta and previous Alpha's, it's unable to find the fax ppd.

Here is the error I'm getting:

Unable to locate the HPLIP Fax PPD File:
HP-fax-hpcups.ppd.gz
Fax setup has been disabled

The printer would set up normally, however the fax ppd seems to be missing.  This has not been a problem up until this Release Candidate.

Is anyone else encountering issues with setting up the printer?

I just filed Bug #459275.

Regards,
zenarcher

---

### Post by zenarcher on 2009-10-26
Has anyone else experienced issues with the hplip package?  With my netbook, I have 9.10 Beta installed and the fax set up fine.  I have all the latest updates in it and it's still working fine.  But, on my two desktop systems, where I did a fresh install of RC, hp-setup cannot find the fax driver, yet all are using the same version of hplip.

Doing some Googling, I see there has been a lot of problems with one part or another of hplip, on again, off again, for quite some time.  I'm just not sure if it's a distribution specific issue or something with the basic Hewlett Packard package.  It's frustrating, at best and I'm wondering if I'm the only one experiencing it, or if there are others.  Or, if there is some sort of workaround.

Cheers,
zenarcher

---

