---
title: "Simple Openstack Question."
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by rayj00 on 2013-03-20
I read on the main Ubuntu site that 12.04 LTS comes with Openstack,
yet I am seeing tutorials such as this:[ Installing OpenStack on Ubuntu 12.04 LTS in 10 Minutes]("http://www.stackgeek.com/guides/gettingstarted.html")

What am I missing here?

Thanks,

Ray

---

### Post by TheFu on 2013-03-20
> **rayj00 said:**
> I read on the main Ubuntu site that 12.04 LTS comes with Openstack,
yet I am seeing tutorials such as this:[ Installing OpenStack on Ubuntu 12.04 LTS in 10 Minutes]("http://www.stackgeek.com/guides/gettingstarted.html")

What am I missing here?

"Comes with" could mean "is available in the repositories."
No install of stock Ubuntu will have any core part of openstack included.

If you are familiar with openstack, you know that at least 3 physical machines are needed to make a starter stack, unless you want to run everyone on 1 box like a developer would, but that is next to worthless for any real production uses.

Openstack is interesting for many reasons, including the pure search for knowledge.

Openstack is probably too complex for anyone wanting less than 50 VMs. There are easier methods.  Somewhere between 50 and 100 VMs it becomes harder to decide if all the hassle of OS is useful or not.

Clearly, everything I've said needs an "IMHO" at the end. ;)

If you are following that guide, it appears he has made some scripts to aid with the installation and configuration of a development install.  I think there are many others like his/hers available.

I've been following OpenStack for a few years, but have not installed it. I've discussed it at length with friends who are doing large scale deployments (1000+ physical servers) for clients, so I'm fairly certain my "hassle" level is accurate.

Did you have some other question? - BTW, this probably belongs in the "virtualization" thread.

---

### Post by tgalati4 on 2013-03-20
Also checkout [http://devstack.org](http://devstack.org) if you want to play with a developer or personal cloud stack--a lot of the heavy-lifting has been done using clever installation scripts.

---

### Post by rayj00 on 2013-03-21
> **TheFu said:**
> "Comes with" could mean "is available in the repositories."
No install of stock Ubuntu will have any core part of openstack included.

If you are familiar with openstack, you know that at least 3 physical machines are needed to make a starter stack, unless you want to run everyone on 1 box like a developer would, but that is next to worthless for any real production uses.

Openstack is interesting for many reasons, including the pure search for knowledge.

Openstack is probably too complex for anyone wanting less than 50 VMs. There are easier methods.  Somewhere between 50 and 100 VMs it becomes harder to decide if all the hassle of OS is useful or not.

Clearly, everything I've said needs an "IMHO" at the end. ;)

If you are following that guide, it appears he has made some scripts to aid with the installation and configuration of a development install.  I think there are many others like his/hers available.

I've been following OpenStack for a few years, but have not installed it. I've discussed it at length with friends who are doing large scale deployments (1000+ physical servers) for clients, so I'm fairly certain my "hassle" level is accurate.

Did you have some other question? - BTW, this probably belongs in the "virtualization" thread.

Thanks for the response.

I am considering a single box for the simple purpose of learning Openstack and Cloud in general.
Of course, I can't do squat until I actually build my PC....

---

