---
title: "How to make cron auto update ubuntu"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by sky5564 on 2012-06-16
So i got tired of that annoying update manager and removed it from my system, I dont miss it one bit lol but i would like to set a cron job to automate the update process, How would i go about doing this? I want cron to automatically download and install any available updates.

---

### Post by codemaniac on 2012-06-16
> **sky5564 said:**
> So i got tired of that annoying update manager and removed it from my system, I dont miss it one bit lol but i would like to set a cron job to automate the update process, How would i go about doing this? I want cron to automatically download and install any available updates.

You might be interested in cron-apt .it was there on Universe repos .

---

### Post by sky5564 on 2012-06-16
> **codemaniac said:**
> You might be interested in cron-apt .it was there on Universe repos .

How do i use this cron-apt you speak of?

---

### Post by SeijiSensei on 2012-06-16
Quick solution is to edit /etc/crontab (as root with sudo) and add the entry:

```
0 3 * * * root /usr/bin/apt-get upgrade -q -y >> /var/log/apt/myupdates.log
```

This will run the update at 3:00 am each day and append the output to /var/log/apt/myupdates.log.

---

### Post by sky5564 on 2012-06-16
> **SeijiSensei said:**
> Quick solution is to edit /etc/crontab (as root with sudo) and add the entry:

```
0 3 * * * root /usr/bin/apt-get upgrade -q -y >> /var/log/apt/myupdates.log
```

This will run the update at 3:00 am each day and append the output to /var/log/apt/myupdates.log.

How can i make it run at 9PM instead?

Will this also install the updates too or just download them?

---

### Post by codemaniac on 2012-06-16
> **sky5564 said:**
> How do i use this cron-apt you speak of?

Hi ,

cron-apt has been documented in the below link .hope this helps .

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

---

### Post by matt_symes on 2012-06-16
Hi

I would update as well, if you don't use cron-apt.

```
0 3 * * * root /usr/bin/apt-get update && /usr/bin/apt-get upgrade -q -y >> /var/log/apt/myupdates.log
```

Kind regards

---

### Post by N0oki3 on 2012-06-16
> **sky5564 said:**
> How can i make it run at 9PM instead?

Will this also install the updates too or just download them?

```
9 0 * * * root /usr/bin/apt-get update && /usr/bin/apt-get upgrade -q -y >> /var/log/apt/myupdates.log
```

but i might be wrong

---

### Post by SeijiSensei on 2012-06-16
That would make the update run at nine minutes past midnight.  The minutes field is first, the hours field second.  So to run at 9:00 pm you'd use:

```
0 21 * * * ...
```

I thought the only reason to run "apt-get update" is when you change your repository list.  That's why I didn't include it before, though it certainly doesn't do any harm to run it each time.

---

### Post by matt_symes on 2012-06-16
Hi

I wasn't going to post this but for the record...

From ```
man apt-get
```

> update
           update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the location(s) specified in
           /etc/apt/sources.list. For example, when using a Debian archive, this command retrieves and scans the Packages.gz files, so that information about new and
           updated packages is available. An update should always be performed before an upgrade or dist-upgrade. Please be aware that the overall progress meter will
           be incorrect as the size of the package files cannot be known in advance.

Kind regards

---

### Post by SeijiSensei on 2012-06-16
Thanks!  That was very informative.

---

### Post by sky5564 on 2012-06-16
Ok thanks for the help everyone, I will give it a try and see what happens.

---

### Post by sky5564 on 2012-06-26
> **sky5564 said:**
> How can i make it run at 9PM instead?

Will this also install the updates too or just download them?

Yes this works for me.

---

### Post by sky5564 on 2012-06-26
> **matt_symes said:**
> Hi

I would update as well, if you don't use cron-apt.

```
0 3 * * * root /usr/bin/apt-get update && /usr/bin/apt-get upgrade -q -y >> /var/log/apt/myupdates.log
```

Kind regards

This worked for me.

---

