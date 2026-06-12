---
title: "Upgrading from 6.06LTS to 8.04LTS"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by JasonRivers on 2007-11-02
Hi all,

I'm just wondering about upgrading from 6.06LTS Server, when 8.04 LTS is release, will there be some documentation on how to do this safely and direct from 6.06 to 8.04? as I like to keep my servers on LTS to avoid upgrading the OS every 6months to a year.

documentation on doing this would be a real help to most sysadmins I think, especially if we can go from 6.06 straight to 8.04 without having to goto 6.10 > 7.04 > 7.10 > 8.04.

Thanks.

Jason.

---

### Post by zach12 on 2007-11-02
They should find a way

---

### Post by rdoolen on 2007-11-02
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by confused57 on 2007-11-02
> **JasonRivers said:**
> Hi all,

I'm just wondering about upgrading from 6.06LTS Server, when 8.04 LTS is release, will there be some documentation on how to do this safely and direct from 6.06 to 8.04? as I like to keep my servers on LTS to avoid upgrading the OS every 6months to a year.

documentation on doing this would be a real help to most sysadmins I think, especially if we can go from 6.06 straight to 8.04 without having to goto 6.10 > 7.04 > 7.10 > 8.04.

Thanks.

Jason.
Someone correct me if I'm wrong, but I believe the next Desktop LTS will be 9.04 and I think the server is supported for 5 years?  I've "heard" that it will be possible to upgrade directly from 6.06 to the next LTS.

---

### Post by Pumalite on 2007-11-02
Maybe it's old news:

[http://adventuresinopensource.blogspot.com/2007/07/next-ubuntu-lts-release-announced.html](http://adventuresinopensource.blogspot.com/2007/07/next-ubuntu-lts-release-announced.html)

---

### Post by confused57 on 2007-11-02
> **Pumalite said:**
> Maybe it's old news:

[http://adventuresinopensource.blogspot.com/2007/07/next-ubuntu-lts-release-announced.html](http://adventuresinopensource.blogspot.com/2007/07/next-ubuntu-lts-release-announced.html)

Thanks Pumalite...I was "confusing" Dapper's 3 year LTS support with the next LTS release.  Got some catching up to do.

---

### Post by Pumalite on 2007-11-02
No 'problema'. Cheers.

---

### Post by whatever69 on 2008-03-29
I too have 6.04.  If I run:

gksu "update-manager -c" 

I do not get 6.10 as the next version to upgrade.

If I run:

gksu "update-manager -d" 

I get 8.04 as the next version to upgrade to.

Are we supposed to try to update to 8.04?  I thought it was advisable to upgrade only one distro version at a time? As explained here:  [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Can someone please clarify the correct path, and how to accomplish it?

Thanks

---

### Post by Pumalite on 2008-03-29
You can go straight from 6.06 to 8.04, but you have to wait for the Final Release.

---

### Post by whatever69 on 2008-03-30
Thanks.  I'll wait for the final release and then update.  :)

---

### Post by zvacet on 2008-03-30
>  I thought it was advisable to upgrade only one distro version at a time?

You are right,but this is something different.Dapper is LTS and Hardy is LTS too.Because of that you can directly upgrade from Dapper to Hardy.It is LTS>LTS upgrade.

---

### Post by whatever69 on 2008-05-11
I waited for the final release and then upgraded.  I had so many problems.  The upgrade crashed/froze too many times to count.  Lots of small bugs also drove me crazy as they were very sneaky like the VNC pam bug and the pam bug that filled up my logs and like the fact that it didn't recognize my 4 disk raid that I setup in 6.10.

In the end, I gave up and simply formated the OS.  I installed 8.04 and everything was great.

I think something something that the developers need to do is have some regression testing by upgrading from various X.YZ LTS releases to the other.  I know some people will eventually have some tweaks in a 2 year period, but the upgrade was a fail.  I really tried to make it work, but simply had to give up after 5 days.

Like I said though, a clean install works.  Ubuntu is a great OS, no doubt there.

---

