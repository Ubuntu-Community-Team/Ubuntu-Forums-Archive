---
title: "Ubuntu 22.04 LTS for Azure download location"
date: 2022-05-06
forum: Installation &amp; Upgrades
---

### Post by ajn3806 on 2022-05-06
Hi Everyone,

I'm new to the forum, so I hope my question is in the right place and is not a silly question.

Is there an official Ubuntu 22.04 LTS for Azure download location?

I see that...

[https://cloud-images.ubuntu.com/focal/current/](https://cloud-images.ubuntu.com/focal/current/)

..is titled "Ubuntu 20.04 **LTS** (Focal Fossa)" (note the LTS), but...

[https://cloud-images.ubuntu.com/jammy/current/](https://cloud-images.ubuntu.com/jammy/current/)

...is titled "Ubuntu 22.04 (Jammy Jellyfish)" (no mention of LTS).

Or am I too early, considering it was only released a little over 2 weeks ago.

Thanks, and kind regards,
ajn3806

---

### Post by TheFu on 2022-05-09
*silly questions* are fine.  ;)  

So, 22.04 **is** an LTS and has 5 yrs of standard support for the main desktop and server versions.  But, immediately after any release, there are issues that thousands of testers missed which will be corrected in the first few months.  For normal users, the upgrade from 20.04 --> 22.04 won't be offered for a few months, I vaguely remember seeing August mentioned.  Effectively, Canonical seems to have decided that for normal users attempting upgrades for their only computer, waiting until the 22.04.1 is released is the best idea to keep people happiest.  Sorta like how many companies don't start moving their desktops to a new version of MS-Windows until the SP1 release happens.

I don't use Azure (seems anti-F/LOSS to me), so I have no idea if there is a special ISO provided by Canonical.  

I suspect that any Cloudy VPS provider will get their ISO from the official one, then modify it for the expected uses in their infrastructure.  A common modification that I've seen in VPSs is they enable the root account, which goes against the actual setup/installer of Ubuntu since the beginning of time. If you pull down any Ubuntu version, the root account isn't directly used. We are expected to use sudo.  It is a security thing.

Today, I wouldn't deploy any production workloads onto 22.04, but I'm fairly cautious. I'm starting to think that moving off 18.04 to 20.04 will need to happen in the next 8 months or so.  A few things in 20.04 didn't work the way I needed at release and some fixes happened in the first year.  I expect the same for 22.04. Of course, some changes in 20.04 don't have official fixes and impacted me and broke some tools we use when different releases are used together. I can see that happening with 22.04.

I'm not in any hurry. But I do have a 22.04 server running in a local VM here just to check some things out.  A few weeks ago, I tested some NFS issues and found that I wasn't impacted, while some others in these forums were due to their NFS server hardware limitations.  The pre-release testing community can't check everything or all the possible interactions between different versions.

With Azure, can't to just provide/upload any ISO Linux you like and install that yourself?  I know other VPS services allow that.

Sorry, you didn't ask a silly question today. ;)

---

### Post by grahammechanical on 2022-05-10
Is this what you are looking for?

[https://ubuntu.com/download/cloud](https://ubuntu.com/download/cloud)

or this?

[http://cloud-images.ubuntu.com/?_ga=2.205330512.1992695948.1652212577-288411274.1649365710](http://cloud-images.ubuntu.com/?_ga=2.205330512.1992695948.1652212577-288411274.1649365710)

Regards

---

### Post by ajn3806 on 2022-05-14
Thank you TheFu, good advice! Yes, perhaps a little early for production workloads.

---

### Post by ajn3806 on 2022-05-14
Thank you grahammechanical.  They were the links I had found too.  I'll take the advice from TheFu and wait a few months before implementing a production workload on 22.04.

---

