---
title: "do-release-upgrade 11.04 &gt; 11.10 failing"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by hillboy2 on 2012-11-22
I need some help upgrading. I'm trying to upgrade my server 11.04 and it's failing with the following message:


root@li220-189:~# do-release-upgrade
Checking for a new ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

Get:1 Upgrade tool signature [198 B]
Get:2 Upgrade tool [1471 kB]
Fetched 1471 kB in 0s (0 B/s)
authenticate 'oneiric.tar.gz' against 'oneiric.tar.gz.gpg'
extracting 'oneiric.tar.gz'
WARNING:root:estimate_kernel_size_in_boot() returned '0'?

**[SIZE="3"]Please report this as a bug[/SIZE]** and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. **The upgrade has aborted**.

---

### Post by darkod on 2012-11-22
Did you try what is suggested in that link?

The 11.04 is end of life, it's not supported any more. There is an option but you will have to change the sources.list I think so that it can find the archived packages.

The versions that are not LTS or only supported 18 months so you need to upgrade before that expires. And for servers people usually run only LTS releases and upgrade from one LTS directly to the next one.

---

### Post by hillboy2 on 2012-11-22
I followed the directions in the link "upgrade information". It suggests that the upgraded from 11.04 to 11.10 should work. The two files that the error message refers to don't exist on my server. 

I realize now that I should have loaded a LTS version and I'm trying to get to 12.04 by way of 11.10. So the remaining suggestion is to report it as a bug but I'm not sure how that would help. I'm looking at having to rebuild the server from a new install and I just don't have the time for that right now.

---

### Post by darkod on 2012-11-22
When you say it should work, do you mean before or after editing the sources.list?

Because regardless how you understood it, upgrading 11.04 with the default sources.list can't work because it was released April 2011 and the 18 months of support expired in October 2012, a month ago. The default repositories are closed.

This is a better link for EOL upgrades since that link in your first post doesn't tell you much:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Note in the /etc/apt/sources.list section how you need to edit them with the word old-releases...

After that you can try the do-release-upgrade again.

---

### Post by hillboy2 on 2012-11-23
> **darkod said:**
> When you say it should work, do you mean before or after editing the sources.list?

Because regardless how you understood it, upgrading 11.04 with the default sources.list can't work because it was released April 2011 and the 18 months of support expired in October 2012, a month ago. The default repositories are closed.

I got it done and now my server is now up to 12.04.1 by way of 11.10. I ran 
*apt-get --purge clean* 
and then the upgrade ran without a hitch. Thanks

---

