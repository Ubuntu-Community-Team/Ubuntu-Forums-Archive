---
title: "partial upgrade to 7.10 - what do I have now?"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by wheelwrightmike on 2008-04-05
I tried to upgrade from 7.4 to 7.10 failed with the errors listed below.
This may be the same as [Bug #152296]("https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296") 
[https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296](https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296)

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2 
```

My system is athlon 64 bit running the 64 bit build.  After the errors, 
update manager said I could do a parital upgrade and I let it do so.

Now my repositories settings have all of the Ubuntu software tab options
unselected and on the Third-party Software tab Ubuntu 7.04 is listed and
selected.

What is my system now?  How can I continue the upgrade?  Do I have to 
start over and reload?

Thanks,
-Mike

---

### Post by markiangooley on 2008-04-06
Similar problem here.  I am sorely tempted to install 7.10 from CD burned from ISO image file, but I don't really trust the backup program I used to save my mailbox, data files, etc.

Mark., tried several times
gooley at gator dot net

---

### Post by zvacet on 2008-04-06
In system>admin>software sources change your local server to main.Reload.

```
sudo apt-get update && sudo apt-get upgrade
```

After this go to update manager and try to continue upgrade.

---

### Post by wheelwrightmike on 2008-04-06
zvacet wrote:
[QUOTE=zvacet;4665460]In system>admin>software sources change your local server to main.Reload.

Software sources currently shows 'Download from: Main Server'.  Should I un-select the 'Feisty Fawn' repositories listed in the 'Third-Party Software' tab and select the unselected sources in the 'Ubuntu Software' tab before I do the update and upgrade?

Thanks,
-MIke

---

### Post by zvacet on 2008-04-07
Uncheck all third party sources which are not Ubuntu related (like **medibuntu** ) and yes chceck all boxes under Ubuntu software and under updates Tab.Reload.


```
sudo apt-get update && sudo apt-get upgrade
```

After this go to the update manager and continue with upgrade.

---

### Post by wheelwrightmike on 2008-04-10
That did it.  
Thanks Very Much.

-Mike

---

