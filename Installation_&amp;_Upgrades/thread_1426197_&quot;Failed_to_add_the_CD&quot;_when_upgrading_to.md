---
title: "&quot;Failed to add the CD&quot; when upgrading to 8.10"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by brent.of.all.people on 2010-03-10
Hi,
 
I have an old 8.04.02 installation that I would like to upgrade to 9.10. I'm trying to use the incremental upgrade path: 8.04 -> 8.10 -> 9.04 -> 9.10. Unfortunately, that computer can't use the internet for some reason, so I have to use the alternate CD. (A partition with a fresh 9.10 installation can use the internet just fine, but I want to carry over everything from the 8.04 installation into 9.10 -- and finally use the internet again).
 I tried following the directions at [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) . I inserted the disc and went through the automatic upgrade dialogs. After clicking "No" on the "Include latest updates from the Internet?" dialog box, the upgrade starts then instantly returns this error message:

---
Failed to add the CD.

 There was a error adding the CD, the upgrade will abort. Please report this as a bug if this is a valid Ubuntu CD.
 
The error message was:
'Unable to locate any package files, perhaps this is not an Ubuntu disc or the wrong architecture?'
---
 
I get the same thing if I try this on the command line: gksu "sh /media/cdrom/cdromupgrade"

I checked the architecture. My computer uses amd64 and the alternate CD is for amd64.
 
I got the disc image from [http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-amd64.iso](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-amd64.iso) so I think it's a valid Ubuntu CD.
 
I tried finding a solution in the forums and within the bug reports, but so far no luck. Some people had the same problem, but I didn't see any sort of solution. Can anyone help me?

Thanks,
Brent

PS: Also posted as a bug report at [URL="https://bugs.launchpad.net/ubuntu/+bug/534240"]https://bugs.launchpad.net/ubuntu/+bug/534240
[/URL] I'm just hoping someone has either experience or a workaround that can get me on my feet again.

---

### Post by slakkie on 2010-03-10
If you wait to months (till the end of april) then you should be able to upgrade to 10.04 directly from 8.04.x.

Not that it will help you with the current problem, but I think it is worth the wait.

---

### Post by brent.of.all.people on 2010-03-10
> **slakkie said:**
> If you wait to months (till the end of april) then you should be able to upgrade to 10.04 directly from 8.04.x.

Not that it will help you with the current problem, but I think it is worth the wait.

Maybe. But I'll be busy at the end of April and there's some projects stewing in the back of mind that I'd like to do on this computer in the meantime. Plus, I have no guarantee that the computer will handle the 10.04 CD any better [shrugs].

---

