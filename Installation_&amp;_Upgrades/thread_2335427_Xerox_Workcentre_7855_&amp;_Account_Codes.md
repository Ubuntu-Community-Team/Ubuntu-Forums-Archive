---
title: "Xerox Workcentre 7855 &amp; Account Codes"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by misterman2100 on 2016-08-28
So, let me preface this by stating that I have looked around various forums, including this one, and have not found a viable solution to my issue.

The issue is this: I have Ubuntu 16.04 installed on my laptop and where I work has a Xerox Workcentre 7855 with accounting enabled. While I thought I could add whatever drivers and then modify the ppd file, I continually received error codes on whatever the output was.

I decided then to try to the Xerox drivers listed on their site. Easy to install. Discovered my device, set up the necessary information via their print manager (sudo xerxprtmgr), but still nothing.
Has anyone else had experience with setting up one of these Workcentres successfully using Xerox's drivers? Should I stick with the Xerox deb package or use the recommended settings Ubuntu provides and figure out the accounting issue?

Any help would be very much appreciated at this point!

---

### Post by misterman2100 on 2016-08-28
I was reading that Xerox automatically creates a default group as "xrx_def" when one is not defined. I left the group setting as default. I'll check tomorrow and report back if this simple issue was the culprit.

---

### Post by misterman2100 on 2016-08-29
Well, what was stated above did not work. However, I did manage to get everything working. I used the Xerox provided drivers from their website, did a quick install, and configured it for accounting. I double-backed into the set-up for the printer configuration, copied the URI into the new Xerox printer, and then it totally worked! So, in summation, watch out for the device URI if you are using Xerox print drivers from their website. It will NOT auto-config it for you, though it seems to give that impression.

I hope this is useful for someone out there!

---

