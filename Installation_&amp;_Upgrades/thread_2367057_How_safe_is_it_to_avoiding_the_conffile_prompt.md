---
title: "How safe is it to avoiding the conffile prompt?"
date: 2017-07-25
forum: Installation &amp; Upgrades
---

### Post by andypike on 2017-07-25
Hi,

Currently our security updates (unattended-upgrades) are failing when manual intervention is required due to the conffile prompt:

```

Package 'unattended-upgrades' has conffile prompt and needs to be updated manually

```

I know I can add the below to /etc/apt/apt.conf.d/50unattended-upgrades which will only overwrite config files when they have not been edited.  A colleague has suggested that this may cause issues with with PHP security upgrades.  Is this true?  Are there any other reason not to enable the below?  Is it safe?

```

Dpkg::Options {
     "--force-confdef";
     "--force-confold";
};

```

Thanks for your help :-)

---

### Post by andypike on 2017-08-03
bump ):P

---

