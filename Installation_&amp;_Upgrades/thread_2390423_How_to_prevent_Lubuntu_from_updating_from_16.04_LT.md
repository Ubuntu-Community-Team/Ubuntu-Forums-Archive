---
title: "How to prevent Lubuntu from updating from 16.04 LTS"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by shellhrs2 on 2018-04-28
I needed a laptop for browsing the web only. No word processing, spreadsheet, image processing, or gaming needed. So last week I took out the old Acer Aspire One netbook (1GB RAM), installed Lubuntu 16.04 LTS, deleted some of pre-installed apps, leaving only Firefox. It ran just fine.

Yesterday Lubuntu 18.04 came out, but the minimum requirement has increased from 512MB to 1GB (2GB for Youtube etc.). Adding RAM is out of the question, so now I have to make sure that the netbook doesn't get updated to higher Lubuntu versions. How to make sure that these commands will not update the Lubuntu version? ```
sudo apt-get update
``` or ```
sudo apt-get upgrade
``` or ```
sudo apt-get dist-upgrade
``` 

Another question: in case I can get the additional RAM needed, how to make sure that ```
sudo release-upgrade
``` only update to another LTS version?

---

### Post by Bashing-om on 2018-04-28
shellhrs2; Hello; Welcome to the forum .

dist-upgrade:
> 
A dist-upgrade will install new dependencies for packages already installed and may remove 
               packages if they are no longer needed. This will not bring you to a new release of Ubuntu.

The terminal command to do the release upgrade is very specific to that purpose. 

If you set in software-center for updates - Long Term Support - then when the release path is set by the development team only then will you see notifications that the release-upgrade is available. And only 18.04 will be accepted if enabled. 

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by shellhrs2 on 2018-04-29
Thank you Bashing-om. The setting in software center for updates is already set to LTS only, so I changed it to Never.

I hope this old netbook can be useful for many more years.

---

### Post by Impavidus on 2018-04-29
Lubuntu LTS releases, like the other light flavours, only have 3 years of support. Lubuntu 16.04 has only one year left, although many components, including Firefox, are shared with standard Ubuntu and have 3 years of support left.

I'm not sure how hard this minimum memory limit is. The memory you need to run the base OS with a bunch of applications just slowly increases and then people put some sumber on it, which is occasionally updated. If you have enough hard drive space available, you could dual boot 16.04 and 18.04 to test.

---

### Post by mörgæs on 2018-04-29
> **Impavidus said:**
> If you have enough hard drive space available, you could dual boot 16.04 and 18.04 to test.

Yes, better to see for yourself how your computer behaves with 18.04. People have different expectations to speed so hardware recommendations can't be exact.

---

