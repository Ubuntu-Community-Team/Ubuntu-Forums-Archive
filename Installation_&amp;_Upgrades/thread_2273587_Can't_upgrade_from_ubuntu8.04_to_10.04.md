---
title: "Can't upgrade from ubuntu8.04 to 10.04"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by alex492 on 2015-04-14
Hi, I have been following a tutorial on help.Ubuntu.com on how to upgrade from 8.04 to 10.04. I have followed the first bit where it says to press check on the update manager but when I do that it gives me this error:

Could not download all repository indexes. The repository may no longer be available or could not be contacted due to network problems. If available an older version of the failed index will be used. Otherwise he repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release](http://dl.google.com/linux/earth/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

Please could someone tell me how I can get around this because it is stopping me from updating my system
 software!

Alex

---

### Post by dino99 on 2015-04-14
we are now in year 2015, and 10.04 stands for 2010 April; its time to drop old things dont you ?

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by coffeecat on 2015-04-14
Oh my. You're trying to upgrade from an Ubuntu release that went end-of-life four years ago to a release where the desktop version went end-of-life nearly 2 years ago, and the server edition is about to go end-of-life. End of life means obsolete, with no further support and no updates. This is why you are getting failed to fetch messages – the repositories are closed. Had you not noticed that your Ubuntu 8.04 has not been able to get any updates for years?

You can update to 10.04 and thence to a version that will be supported after the end of this month – say 12.04 – by using the old-releases repositories, but I recommend you don't do it. Or if you do, be prepared that it might go wrong. So back up your data. Here is a link for updating obsolete releases:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I suggest you make a fresh install instead with one of the current long term support releases, namely 12.04 or 14.04. 14.04 would be a better choice as it has a longer support life remaining. Be aware though that things have changed since 8.04/10.04 days which both had the old gnome 2 desktop. Ubuntu now comes with the Unity desktop which has divided opinion, it is fair to say.

What do you want to do? Do you need any more information about where to get Ubuntu ISOs, information about Unity, or alternative desktops if Unity is not what you want?

---

### Post by alex492 on 2015-04-14
Sorry! Hi, I didn't realize 10.04 had become obsolete because the computer I am talking about has been in storage for about 3 years. I would appreciate it if someone could send me a link to a set of instructions on how to upgrade to 14.04. Really I don't care about data loss because it is not a computer I will use regularly at all. Thanks!

---

### Post by michi1983 on 2015-04-14
There you go :)
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by alex492 on 2015-04-14
Hi, I have a few questions:

Will this delete all my data?
Will this change the current partitions?
How can I put Ubuntu 14.04.2 LTS onto a USB so I can install it?

Thanks, Alex

---

### Post by dino99 on 2015-04-14
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

you may want to control the installation yourself, so choose the 'smothing else' option when the installer will ask. Its easier to know the actual partitions to continue, so run gparted first; you then decide to continue with /home without formatting that partition, or prefer to format the whole disk. Well we can decide for you.

---

