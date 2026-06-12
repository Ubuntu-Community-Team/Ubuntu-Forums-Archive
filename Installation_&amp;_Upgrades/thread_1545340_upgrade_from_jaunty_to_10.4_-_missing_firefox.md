---
title: "upgrade from jaunty to 10.4 - missing firefox"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Elvis99 on 2010-08-03
hi all,

I've just upgraded to the newest distro (and was amazed how smooth it went) via the update manager, but it seems that I've lost firefox (and my bookmarks :/ ) in the process.
Is there any chance that I get my bookmarks back? 

Any help would be greatly appreciated!

---

### Post by lovinglinux on 2010-08-03
To reinstall firefox, open a terminal (Applications >> Acessories >> Terminal) and run the following command:

```
sudo apt-get install --reinstall firefox
```

If that doesn't help, try this:

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

You won't lose your bookmarks. They are stored in your use profile, which is located at ~/.mozilla/firefox/<profilename>/places.sqlite and are not affected if you remove or re-install Firefox. Unless of course the upgrade went really bad and that folder got deleted somehow.

---

### Post by Elvis99 on 2010-08-03
> **lovinglinux said:**
> To reinstall firefox, open a terminal (Applications >> Acessories >> Terminal) and run the following command:

```
sudo apt-get install --reinstall firefox
```If that doesn't help, try this:

```
sudo apt-get purge firefox
sudo apt-get install firefox
```You won't lose your bookmarks. They are stored in your use profile, which is located at ~/.mozilla/firefox/<profilename>/places.sqlite and are not affected if you remove or re-install Firefox. Unless of course the upgrade went really bad and that folder got deleted somehow.

Hey and thanks for your quick response!

I meanwhile backuped the .mozilla folder, just to be on the safe side.
I did reinstall firefox with synaptic once, but the firefox icon never showed up anywhere in the menus. Now I tried it via the purge & install, but still - no firefox icon anywhere.
Synaptic says it's installed. Help?!

edit: But I have an entry called "shiretoko web browser", and when I hover with my mouse on it it says "firefox 3.5". Now, when I try to "sudo apt-get purge shiretoko" it says "couldn't finde package shiretoko"

---

### Post by lovinglinux on 2010-08-03
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installation, so I don't need to guess what might be happening to your system:

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Elvis99 on 2010-08-04
> **lovinglinux said:**
> 
**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be locates at the bottom of the info dialog:

[IMG]http://a.imageshack.us/img265/9273/firefoxversion.png[/IMG]

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.04 (jaunty) Shiretoko/3.5.7


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

```

Ubuntu Architecture

Linux blackbook 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.5					install
firefox-3.5-branding				install

Firefox binaries

/usr/bin/firefox: ERROR: cannot open `/usr/bin/firefox' (No such file or directory)
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

opera.list
opera.list.distUpgrade
opera.list.save


```

---

### Post by lovinglinux on 2010-08-04
> **Elvis99 said:**
> Hey and thanks for your quick response!

I meanwhile backuped the .mozilla folder, just to be on the safe side.
I did reinstall firefox with synaptic once, but the firefox icon never showed up anywhere in the menus. Now I tried it via the purge & install, but still - no firefox icon anywhere.
Synaptic says it's installed. Help?!

edit: But I have an entry called "shiretoko web browser", and when I hover with my mouse on it it says "firefox 3.5". Now, when I try to "sudo apt-get purge shiretoko" it says "couldn't finde package shiretoko"

First some explanaitions. Shiretoko is just a codename for the development versions of Firfefox 3.5. So you can't remove it with *apt-get purge shiretoko*, because that package doesn't exist. The real package is *firefox-3.5*. 

Your bookmarks are missing because you have installed firefox-3.5 (aka Shiretoko), which is probably using a different profile folder. So your bookmarks are still there, you just can't see them. Run the following commands to fix this:

```
mv ~/.mozilla/firefox ~/.mozilla/firefox.old 
mv ~/.mozilla/firefox-3.5 ~/.mozilla/firefox
```

Looking at your report I see that you are missing some firefox files. Let's try to fix this. Run the following commands to completely purge firefox and install it again:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get purge firefox-3.5
sudo rm -f /var/cache/apt/firefox*
sudo apt-get update
sudo apt-get install firefox
```

You should be able to see the icon in the menu after that. Start Firefox and check the version.

---

### Post by Elvis99 on 2010-08-04
> **lovinglinux said:**
> First some explanaitions. Shiretoko is just a codename for the development versions of Firfefox 3.5. So you can't remove it with *apt-get purge shiretoko*, because that package doesn't exist. The real package is *firefox-3.5*. 

Your bookmarks are missing because you have installed firefox-3.5 (aka Shiretoko), which is probably using a different profile folder. So your bookmarks are still there, you just can't see them. Run the following commands to fix this:

```
mv ~/.mozilla/firefox ~/.mozilla/firefox.old 
mv ~/.mozilla/firefox-3.5 ~/.mozilla/firefox
```

Looking at your report I see that you are missing some firefox files. Let's try to fix this. Run the following commands to completely purge firefox and install it again:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get purge firefox-3.5
sudo rm -f /var/cache/apt/firefox*
sudo apt-get update
sudo apt-get install firefox
```

You should be able to see the icon in the menu after that. Start Firefox and check the version.

I followed your advice, and have now an entry labelled "Firefox Web Browser" in my menu, but the icon is different, it's blue and represents the earth (I think)

I checked the version it says; 

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.3

But the latest firefox for ubuntu from the mozilla.org website is version no 3.6.8.  :confused:

Thanks again for your time :)

---

### Post by lovinglinux on 2010-08-04
> **Elvis99 said:**
> I followed your advice, and have now an entry labelled "Firefox Web Browser" in my menu, but the icon is different, it's blue and represents the earth (I think)

I checked the version it says; 

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.3

But the latest firefox for ubuntu from the mozilla.org website is version no 3.6.8.  :confused:

Thanks again for your time :)

Try:

```
sudo apt-get update
sudo apt-get upgrade
```

Then check the version again.

Also post the output of:

```
which firefox
```

---

### Post by Elvis99 on 2010-08-04
> **lovinglinux said:**
> Try:

```
sudo apt-get update
sudo apt-get upgrade
```

Then check the version again.

Also post the output of:

```
which firefox
```

both the update and upgrade commands did not bring any results:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.3

```
elvis@graceland:~$ which firefox
/usr/bin/firefox
```

---

### Post by lovinglinux on 2010-08-04
At least now you have a /usr/bin/firefox file.

Run the report commands again and post the results.

Can you see your bookmarks again?

---

### Post by Elvis99 on 2010-08-04
> **lovinglinux said:**
> At least now you have a /usr/bin/firefox file.

Run the report commands again and post the results.



Ubuntu Architecture

Linux graceland 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox						install
firefox-3.5					install
firefox-3.5-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `firefox-3.5'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

opera.list
opera.list.distUpgrade
opera.list.save

> **lovinglinux said:**
> 
Can you see your bookmarks again?

Nay, but now that I have a backup of them, it's not an issue anymore - I can fix that, as soon as my firefox installation is working. (eg newest version etc)

---

### Post by lovinglinux on 2010-08-04
I don't know why it is not upgrading Firefox to 3.6.8. But I just realized you still have Karmic 9.10 instead of Lucid 10.04. Go to "System >> Administration >> Update Manager" and check if it offers you to upgrade to 10.04.

---

### Post by Elvis99 on 2010-08-11
> **lovinglinux said:**
> I don't know why it is not upgrading Firefox to 3.6.8. But I just realized you still have Karmic 9.10 instead of Lucid 10.04. Go to "System >> Administration >> Update Manager" and check if it offers you to upgrade to 10.04.

Hi lovinglinux,

I've now updated to Lucid, and Firefox is working as expected EXCEPT that my bookmarks are all gone.
I've tried to import every "bookmarks.html" file from /.mozilla (as there are several folders called firefox (firefox, firefox.old and firefox.sh) and none of them contains my bookmarked items.
Is there any other place I might look for the bookmarks or was that it and I should start blame myself for not making backups? :D

---

### Post by lovinglinux on 2010-08-11
> **Elvis99 said:**
> Hi lovinglinux,

I've now updated to Lucid, and Firefox is working as expected EXCEPT that my bookmarks are all gone.
I've tried to import every "bookmarks.html" file from /.mozilla (as there are several folders called firefox (firefox, firefox.old and firefox.sh) and none of them contains my bookmarked items.
Is there any other place I might look for the bookmarks or was that it and I should start blame myself for not making backups? :D

The bookmarks.html file is an old file from Firefox 2, kept for compatibility. It does not contain the bookmarks anymore. Now they are stored in a database file, called places.sqlite.

---

