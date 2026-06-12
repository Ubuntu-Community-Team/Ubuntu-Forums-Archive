---
title: "Schedule updates for a certain time of day"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by agadd09 on 2011-08-20
My Internet service provider here in South Africa is Vodacom (Vodafone) and I pay a huge amount of cash for 2.5Gigs per month. They do, however, give me the same amount of data for free that I can make use of between midnight and 5.00am. 
 
For this reason, I would like to be able to schedule my update manager to download all updates at, say, 10 past midnight.
 
Can any of you guys out there offer any suggestions or is there a way that we can make a request for the Ubuntu developers to include this in "Update Manager"? 
 
Many thanks.

---

### Post by sanderd17 on 2011-08-20
you can set up a cron job I believe. Read this page: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

The commands that you need to execute would be
```

apt-get update
apt-get upgrade

```

Off course as root.

So you would need to do
```

sudo crontab -e

```

and in that file type
```

10 00 * * * apt-get update && apt-get upgrade

```

---

### Post by agadd09 on 2011-08-20
Thanks a lot, I'll give it a bash.
Regards,
Alistair

---

