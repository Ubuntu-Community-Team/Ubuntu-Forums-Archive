---
title: "Karmic repos failures"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by WDYSUN on 2011-12-02
Dear All

I have Karmic box, it's two days now that I am not able to install packages from apt-get anymore. If I update indexes I got


W: Failed to fetch http:// ... etc

and things do not change if I change repo.


Can anybody tell me what the hell is happening?

Pierre

---

### Post by mikewhatever on 2011-12-02
Karmic has reached End of Life in April 2011. It's time to move on to a more recent release.

---

### Post by lisati on 2011-12-02
Your options include pointing your sources.list file to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) but you're not likely to receive anything new beyond being able to upgrade your release.

---

### Post by WDYSUN on 2011-12-02
> **lisati said:**
> Your options include pointing your sources.list file to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) but you're not likely to receive anything new beyond being able to upgrade your release.

Thanks.

Do you think I'll have any problems if I point to Hardy or Lucid repos, I just need it for new software rather than upgrading the system

Best
Pierre

---

### Post by lisati on 2011-12-02
> **WDYSUN said:**
> Thanks.

Do you think I'll have any problems if I point to Hardy or Lucid repos, I just need it for new software rather than upgrading the system

Best
Pierre
It's usually best to use the repos for the particular release you're using. Using repos for a different release introduces a risk of breaking something due to changes between releases.

---

### Post by WDYSUN on 2011-12-02
> **lisati said:**
> It's usually best to use the repos for the particular release you're using. Using repos for a different release introduces a risk of breaking something due to changes between releases.

Thank you
Pierre

---

### Post by kio_http on 2011-12-02
> **WDYSUN said:**
> Thank you
Pierre

What is keeping you from updating, if this is an old PC, don't be fooled and thing new versions will not work etc. Try ubuntu 11.10, if it doesn't work Kubuntu will work fine (if you have more than 512Mb Ram), If that fails than Lubuntu will definitely be fine.

---

### Post by TopDollar2006 on 2011-12-24
Pardon the stupid question, but how exactly do you repoint your sources.list file?

---

### Post by pconroy on 2012-01-10
Did you get an answer to this?
I've been late to upgrade and my Karmic based system doesn't even offer up a DIST upgrade anymore... :)

It just fails all the repositories.

In any event - here's how I got things back.   I edited sources.list and changed the URLs to look like:



deb [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) karmic main universe restricted multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) karmic universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/dists/](http://security.ubuntu.com/ubuntu/dists/) karmic-security universe main multiverse restricted

etc.

note that 'archive' went to old-releases and I added the /dists/ at the end of the URL.

running update-manager now at least tells me I need to upgrade to 10.4LTS which I'll do!  :)

---

