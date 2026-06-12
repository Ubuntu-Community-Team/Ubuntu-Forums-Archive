---
title: "apt-get failing due to missing dependency"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by robertmazur on 2012-03-14
Who do I alert about apt-get failing due to a missing dependency?

In my specific case, trying to install openjdk-7-jdk is failing due to a missing file in the repository.  Of course anything that depends on openjdk, like Eclipse, also fails.

What is the protocol for reporting this?

Thanks,
Rob

---

### Post by cortman on 2012-03-14
Some info [here]("http://www.google.com/#hl=en&output=search&sclient=psy-ab&q=how+to+report+bugs+in+ubuntu&oq=how+to+report+bugs+in+ubuntu&aq=f&aqi=g-v1&aql=&gs_sm=3&gs_upl=644l3606l0l3825l28l20l0l7l7l2l258l3685l0.15.5l26l0&gs_l=hp.3..0i15.644l3606l0l3826l28l20l0l7l7l2l258l3685l0j15j5l26l0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=b069f4a440ee70e1&biw=1366&bih=653")...?

---

### Post by robertmazur on 2012-03-14
Thank you for the tip, cortman.  I had considered submitting a bug, but considered a bug to be a crash of a running program, or part of the OS itself, etc.  Not necessarily the inability to download a package.

But upon reviewing the bugs at Launchpad, I see that this IS the place to report such an issue.  Upon searching for my same issue and finding nothing already reported, I registered and submitted a report.

Thanks for the help,
Rob

---

### Post by cortman on 2012-03-14
> **robertmazur said:**
> Thank you for the tip, cortman.  I had considered submitting a bug, but considered a bug to be a crash of a running program, or part of the OS itself, etc.  Not necessarily the inability to download a package.

But upon reviewing the bugs at Launchpad, I see that this IS the place to report such an issue.  Upon searching for my same issue and finding nothing already reported, I registered and submitted a report.

Thanks for the help,
Rob

Glad to be of any help. Although I would suspect it's probably an issue with your filesystem rather than the repository. If you'd like to pursue that I'd be happy to help. If you're convinced otherwise that's fine as well.

---

### Post by robertmazur on 2012-03-15
Ya as it turns out, the bug folks over at Launchpad recommended that I convert my Bug Report to a question in the Answers locations of that site.  In fact, they moved/converted the bug report for me, and then answered it.  A member there stated:

> tzdata-java was updated recently, please update your apt-cache before attempting to install this with the following command:
sudo apt-get update

And sure enough that resolved the issue.

Ya, I didn't really think it was a bug.  But having seen many other instances of folks filing a bug report for a similar issues, I followed suit.  Live and learn.  I now better understand the protocol.

Thanks for your help.
Rob

---

### Post by cortman on 2012-03-15
> **robertmazur said:**
> Ya as it turns out, the bug folks over at Launchpad recommended that I convert my Bug Report to a question in the Answers locations of that site.  In fact, they moved/converted the bug report for me, and then answered it.  A member there stated:



And sure enough that resolved the issue.

Ya, I didn't really think it was a bug.  But having seen many other instances of folks filing a bug report for a similar issues, I followed suit.  Live and learn.  I now better understand the protocol.

Thanks for your help.
Rob

Sure. Reporting bugs is a valuable service to the community, don't be afraid to if you're pretty sure something's messed up.

---

