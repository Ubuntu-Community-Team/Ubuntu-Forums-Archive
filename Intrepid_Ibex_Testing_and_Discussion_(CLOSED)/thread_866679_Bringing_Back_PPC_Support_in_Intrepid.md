---
title: "Bringing Back PPC Support in Intrepid?"
date: 2008-07-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by travnewmatic on 2008-07-22
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

Look under "snapshot intrepid" and then in the "Processor Architecture"...  is that a typo, or are they really going to support PPC in the next release?

---

### Post by stream303 on 2008-07-22
Support has never been dropped, so Intrepid should shape up nicely for PPC.  This is widely misunderstood.  

Shortly after Dapper 6.06, support changed from commercial to a community-based effort of devs and users, much like Debian, Fedora, Gentoo, etc.

Once you come to the forums, you find out where all the community downloads are - these aren't currently mentioned on the commercial Canonical website, except for the older Dapper 6.06.

The day that ppc won't be supported by Ubuntu will be the day that the install images stop being released.

Xubuntu brought PPC to the last Hardy beta and then stopped just short of a real release.  Maybe they ran out of resources for ppc.  Maybe some Xubuntu ppc users can comment on if they are getting updates after the late beta?  In any case, I'd like to thank them for the hard work they've put into Xubuntu in the past.

This concerns me as I'd hate to be part of Intrepid's bug-testing, only to find the entire ppc project dropped a day or two before the actual release.

Thing is, despite the gloom and doom predictions, and incorrect electronic media spins about the lack of ppc support, for the most part we are ticking along quite nicely.

---

### Post by Phonan on 2008-07-22
Stream, if you check the page, though, it appears to just be talking about just commercial support. For Hardy, no ppc is shown. If this isn't a bug it would be very interesting to have commercial ppc support.

---

### Post by stream303 on 2008-07-22
It's not a bug, it is official policy - there is no commercial support for PPC anymore, and it is very unlikely to be resuscitated in the future - hence the reason there is no mention of anything beyond Dapper on the commercial website.

Unfortunately, people tend to read more into that, and think that there are no more ppc releases at all, which we know isn't true.

As we've found out, what you **don't** say, can be detrimental to the community effort, even though it may be the absolute truth. :)

Let's put a reverse-spin on things in regards to other distros that support PPC.  Imagine this headline:

> 
Imagine this fictitious news article:

**July 22 2008 - Leading distro's decide fate of PPC..**

Today, a meeting of minds took place, and the leaders of Debian, Fedora, and Gentoo have determined that they will not provide commercial support for their PPC release, even though downloads of it continue.

You have to read it very carefully to determine the spin. :)

---

### Post by cyberdork33 on 2008-07-22
I just looked through the packages for intrepid. There were absolutely no PPC binaries in there. I think DW just made a typo or is recognizing the community effort by the PPC Ubuntu folks.

---

### Post by stream303 on 2008-07-22
Interesting.  Seems like they are following the same route that Hardy went.  It was only when PPC reached the beta-stage, did ppc binaries become available for testing.  I guess we'll see.

At any rate, I'm very thankful that someone at Ubuntu can sneak in the resources during the down times to keep the repos and releases going for the community.

---

### Post by cyberdork33 on 2008-07-22
Interesting note in the package server changelog though:
> 
2008-04-26 Adapted for hardy release. Removed the obsolete powerpc data for hardy. I'm currently evaluation if and how I should include information about ports.ubuntu.com packages here. Since archive.ubuntu.com is currently unusable I use nl.archive.ubuntu.com as source for the data until the situation normalizes again.

and the PPC packages are on ports.ubuntu.com as they should be.

---

### Post by stream303 on 2008-07-22
That rang alarm bells too, although it appears they are trying to figure out the best way to put them on the new port repos, ports.ubuntu.com.  Makes sense to keep it out of the way of the main archives.

My eyes did bug-out on "obsolete", but these days I've learned not to trust words, but action. :)

The hardware requirements page about Hardy 8.04 users having to download specific smp kernels for PPC is wrong.  Hope they fix that if they decide to go ahead with Intrepid. :)

---

### Post by cyberdork33 on 2008-07-22
> **stream303 said:**
> My eyes did bug-out on "obsolete", but these days I've learned not to trust words, but action. :)I don't think he was saying PPC packages were obsolete, rather, that there were some obsolete packages, that happened to be PPC binaries.

---

