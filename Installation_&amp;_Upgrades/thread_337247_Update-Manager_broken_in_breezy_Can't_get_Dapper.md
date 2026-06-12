---
title: "Update-Manager broken in breezy Can't get Dapper"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by Tweedicus on 2007-01-12
Hi,

I'm pretty sure my Update Manager is broken in Breezy.

I have Edgy on my laptop with no problems.

I wanted to install Ubuntu on my son's laptop but only had a 5.10 Breezy iso. I don't have a burner on my laptop to download the Edgy or Dapper iso.

Breezy has been installed with no problems everything works fine.

However, the CD iso I used is ages old, and yet update manager is saying my system is up to date, which surely must be wrong, as there have been tonnes of updates.

This means I can't get Dapper. Last time Breezy upgraded to Dapper easily: Update manager told me there was a new distro available. No such thing now. If I refresh it tells me my system is upto date.

I've tried: gksu “update-manager -d”

But I get the same message that my system is up to date.

Any idea how to get it working, or more importantly, how to upgrade to Dapper. I've read the Dapper upgrade guide, but just get my system is upto date.

I've checked my network. I am online.

Thanks.

---

### Post by NeoLithium on 2007-01-12
Change your instances of breezy to dapper in your /etc/apt/sources.list then just
```

sudo aptitude update

sudo aptitude dist-upgrade

```

---

### Post by ciscosurfer on 2007-01-12
> **Tweedicus said:**
> Hi,

I'm pretty sure my Update Manager is broken in Breezy.

I have Edgy on my laptop with no problems.

I wanted to install Ubuntu on my son's laptop but only had a 5.10 Breezy iso. I don't have a burner on my laptop to download the Edgy or Dapper iso.

Breezy has been installed with no problems everything works fine.

However, the CD iso I used is ages old, and yet update manager is saying my system is up to date, which surely must be wrong, as there have been tonnes of updates.

This means I can't get Dapper. Last time Breezy upgraded to Dapper easily: Update manager told me there was a new distro available. No such thing now. If I refresh it tells me my system is upto date.

I've tried: gksu “update-manager -d”

But I get the same message that my system is up to date.

Any idea how to get it working, or more importantly, how to upgrade to Dapper. I've read the Dapper upgrade guide, but just get my system is upto date.

I've checked my network. I am online.

Thanks.I have two suggestions: if the update-manager seems to be giving you trouble, you can try upgrading manually by way of updating your /etc/apt/sources.list repos to reflect Dapper repos (usually, simply changing the word 'Breezy' to 'Dapper', then issuing a **sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade** will take care of the upgrade for you.  You can manually edit your sources.list file by either issuing in a ternial```
sudo gedit /etc/apt/sources.list
```or```
sudo vim /etc/apt/sources.list
```My other suggestion would be to go to [https://shipit.ubuntu.com]("https://shipit.ubuntu.com/") and ordering a free disc that will come in the mail for you.

If you need any further assistance with this, please don't hesitate to ask questions. :-)

---

### Post by Tweedicus on 2007-01-12
The problem is there is nothing in my sources list. It's completely empty.

---

### Post by NeoLithium on 2007-01-12
If it's completely empty; there is a basic dapper sources list here:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Copying and pasting should set you back up for a quick copy and paste and allow you to upgrade to dapper.

---

