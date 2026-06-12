---
title: "Thunderbird rollback to 68.12.0"
date: 2021-03-09
forum: Installation &amp; Upgrades
---

### Post by bl75 on 2021-03-09
I am using Ubuntu 20.04 LTS.

Of course, as usual, after a Thunderbird update calendar add-ons stop working and I really do not have time to deal with this.

Therefore, I'd like to go back to version 68.12.1 and stop Thunderbird from further updates, but did not find out how to do that.

Please do not try to convince me of staying with the newer versions. I am just tired of these problems and spent an hour or so with fruitless efforts to go back. If I can't manage to roll back, I will have to switch to MS Outlook. No attractive perspective... but hopefully not inevitable.


I found the release notes of thunderbird here: [https://www.thunderbird.net/en-US/thunderbird/releases/](https://www.thunderbird.net/en-US/thunderbird/releases/)

But there is no chance to download.

What I also found is this source: [https://ftp.mozilla.org/pub/thunderbird/releases/](https://ftp.mozilla.org/pub/thunderbird/releases/)

Finally, I will probably have to exclude Thunderbird updates from the repository, but did not manage to find out how. Can I select it somehow from "Canonical partners"?

Thanks in advance for your support!

---

### Post by Hagar Delest on 2021-03-09
You can deinstall TB and then download the version you want from the [https://ftp.mozilla.org/pub/thunderbird/releases/](https://ftp.mozilla.org/pub/thunderbird/releases/) link (go to /pub/thunderbird/releases/68.12.1/ and then your architecture and the language).
Then extract it in /opt for example and create a custom launcher with a thunderbird.desktop to be placed in ~/.local/share/applications that points to the thunderbird file in /opt/thunderbird.
Et voilà.

That's what I used to do in the past to update TB/FF quicker than the distro or with beta releases.

---

### Post by ajgreeny on 2021-03-09
However, be aware that you may find there is a problem using your TB profile and configuration contained in the hidden .thunderbird folder in your home which has now been used in TB 78 to work again in TB 68.

---

### Post by Hagar Delest on 2021-03-09
Indeed, better make a backup of the profile in case there is an issue and you end up keeping the most recent version.
Nonetheless, if your accounts use IMAP, at least the content is easily restored. More a hassle for the address book.

---

### Post by TheFu on 2021-03-09
When v78 was pushed out, I didn't have any issues still connecting to my network calendars in Zimbra. They all "just worked". I was using Lightning before. The built-in Calendaring handled the migration and a few other long time bugs were fixed.  Though I've seen a few minor new bugs in the new thunderbird, they were display update only in seldom used 3-level deep dialogs. I doubt many people use the "Manage Identities" stuff.

To install a specific package you'll need to know the exact name, with the version - use **apt-search** for that.  
As for marking a package to prevent updates, use **apt-mark** for that.

BTW, MS-Exchange is currently under attacks around the world, so if your email server is MS-Exchange, since last Friday the IT support guys have probably been doing all they can to fix problems with it.  Last count I saw was that over 100K Exchange servers had been cracked. The professional IT websites have been writing about this issue for 3 days straight.

---

