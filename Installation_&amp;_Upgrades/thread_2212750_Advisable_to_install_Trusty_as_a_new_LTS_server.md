---
title: "Advisable to install Trusty as a new LTS server?"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2014-03-22
Hi,

I'm trying to install a new LTS server.  I'm contemplating using 14.04 since it is supposed to go live in a month or less.

Is it stable enough for that?

I need a QEMU host, and also VMs on it and on another existing server which will be build boxes and test/support infrastructure for software development.

Thanks.

---

### Post by Doug S on 2014-03-22
For the Qemu part: Please know that Qemu 2.0 is being tested, as a ppa, right now with 14.04 server. It seems pretty good.

references:
[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1284793](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1284793)
[https://lists.ubuntu.com/archives/ubuntu-server/2014-February/006823.html](https://lists.ubuntu.com/archives/ubuntu-server/2014-February/006823.html)
[https://lists.ubuntu.com/archives/ubuntu-server/2014-March/006826.html](https://lists.ubuntu.com/archives/ubuntu-server/2014-March/006826.html)
[https://launchpad.net/~ubuntu-virt/+archive/candidate](https://launchpad.net/~ubuntu-virt/+archive/candidate)

I can not answer your actual question.
A lot of users that need a stable production machine tend to wait a bit (a month or two) after LTS release before using it. I have been using 14.04 server development version for a few months, and I think it runs fine.

---

### Post by 1clue on 2014-03-23
This will become a production machine, but I expect it to be in actual production about 3 months from now.

And it's not a customer-facing machine, if you get what I'm saying.  This is production, but for developers and support staff with a mostly knowledgeable staff.

---

### Post by 1clue on 2014-03-23
And BTW I understand exactly what you're saying.  "Production" means different things to different people.  Something that is just fine as a production print server is not good enough for financial information, and likewise what's OK for the financial system might not be trusted to keep an airplane in the air.

---

### Post by Doug S on 2014-03-24
> **1clue said:**
> This will become a production machine, but I expect it to be in actual production about 3 months from now.Then if it were me, I would definitely go with 14.04 server. You can start today from the [daily iso]("http://iso.qa.ubuntu.com/qatracker/milestones/308/builds").

---

### Post by 1clue on 2014-03-24
I think I'm gonna try it.  Thanks.

---

### Post by Doug S on 2014-03-24
Oh, by the way, there should be a preliminary version of the 14.04 Ubuntu Serverguide published on [help.ubuntu.com]("https://help.ubuntu.com/") by the end of the week. (we are a little late this cycle with the preliminary). If you want it sooner, PM me your e-mail address and I will send you the PDF.

---

### Post by 1clue on 2014-03-24
Thanks.  It might actually wait until the docs are available.  This is not a top priority right now, still in planning stages.

---

