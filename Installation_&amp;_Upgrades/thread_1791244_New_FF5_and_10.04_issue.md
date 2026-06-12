---
title: "New FF5 and 10.04 issue"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2011-06-26
So, I have installed FireFox 5 on my two XP boxes and on 4 other Linux boxes (3 running 10.10 1 running Mint) but it is a no go (?) on my 10.04 LTS main box.

It is in Synaptic as installed, but when I click on the help to check the version, it tells me I am still running 4.x. (even tried a re-install in Synaptic!)

Sure like to get the new version up and working as the FF 4.x has a memory leak issue and an issue with shutdown with FireFox.bin.

Any help there peeps?

Thanks.

---

### Post by lovinglinux on 2011-06-26
Please explain how did you install Firefox 5?

Also see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by oldsoundguy on 2011-06-26
> **lovinglinux said:**
> Please explain how did you install Firefox 5?

Also see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

Used this only had to run the install firefox command also.

[http://www.liberiangeek.net/2011/06/install-firefox-5-in-ubuntu-10-1010-04-via-ppa/](http://www.liberiangeek.net/2011/06/install-firefox-5-in-ubuntu-10-1010-04-via-ppa/)

It worked on the other boxes .. just not the 10.04

---

### Post by lovinglinux on 2011-06-26
> **oldsoundguy said:**
> Used this only had to run the install firefox command also.

[http://www.liberiangeek.net/2011/06/install-firefox-5-in-ubuntu-10-1010-04-via-ppa/](http://www.liberiangeek.net/2011/06/install-firefox-5-in-ubuntu-10-1010-04-via-ppa/)

It worked on the other boxes .. just not the 10.04

Change the repository server. You might be using a mirror that hasn't been updated yet. See [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by oldsoundguy on 2011-06-26
> **lovinglinux said:**
> Change the repository server. You might be using a mirror that hasn't been updated yet. See [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

I used the same repository server for the other computers.  They work.

---

### Post by lovinglinux on 2011-06-26
> **oldsoundguy said:**
> I used the same repository server for the other computers.  They work.

Sorry, my comment was totally stupid, because you are using a ppa ](*,)

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

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

### Post by oldsoundguy on 2011-06-26
> **lovinglinux said:**
> Sorry, my comment was totally stupid, because you are using a ppa ](*,)

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

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

sorry, but I am not a programmer, I am a user.
That is far too much cut and paste.

Now the software update for Firefox came up and is attempting to connect to "the update server" .. been doing so for the past 2 hours.

---

### Post by lovinglinux on 2011-06-27
> **oldsoundguy said:**
> sorry, but I am not a programmer, I am a user.
That is far too much cut and paste.

Now the software update for Firefox came up and is attempting to connect to "the update server" .. been doing so for the past 2 hours.

Just copy the entire thing and paste on a terminal.

---

### Post by oldsoundguy on 2011-06-27
OK, thanks .. here is the printout.  (not sure how to put this in a separate window.)

Ubuntu Architecture

Linux dave-mediaroom 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.0-gnome-support			install
firefox-branding				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-5.0/firefox.sh'

Sources

anonbeat-guayadeque-lucid.list
anonbeat-guayadeque-lucid.list.save
lucid-partner.list
lucid-partner.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mozillateam-firefox-next-lucid.list
mozillateam-firefox-next-lucid.list.save
mozillateam-firefox-stable-lucid.list
mozillateam-firefox-stable-lucid.list.save
tualatrix-ppa-lucid.list
tualatrix-ppa-lucid.list.save
ubuntu-mozilla-security-ppa-lucid.list
ubuntu-mozilla-security-ppa-lucid.list.save
ubuntu-x-swat-x-updates-lucid.list
ubuntu-x-swat-x-updates-lucid.list.save

---

### Post by lovinglinux on 2011-06-27
> **oldsoundguy said:**
> OK, thanks .. here is the printout.  (not sure how to put this in a separate window.)

Ubuntu Architecture

Linux dave-mediaroom 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.0-gnome-support			install
firefox-branding				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-5.0/firefox.sh'

Sources

anonbeat-guayadeque-lucid.list
anonbeat-guayadeque-lucid.list.save
lucid-partner.list
lucid-partner.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mozillateam-firefox-next-lucid.list
mozillateam-firefox-next-lucid.list.save
mozillateam-firefox-stable-lucid.list
mozillateam-firefox-stable-lucid.list.save
tualatrix-ppa-lucid.list
tualatrix-ppa-lucid.list.save
ubuntu-mozilla-security-ppa-lucid.list
ubuntu-mozilla-security-ppa-lucid.list.save
ubuntu-x-swat-x-updates-lucid.list
ubuntu-x-swat-x-updates-lucid.list.save

You have too many ppa repositories and Firefox versions installed.

Run these on a terminal, in order of appearance, to fix it:

```
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-lucid.list
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-lucid.list.save
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-next-lucid.list
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-next-lucid.list.save
sudo rm -fr /opt/firefox && sudo rm -f /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo apt-get remove firefox
sudo apt-get remove firefox-3.0
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by oldsoundguy on 2011-06-27
That got it!!  (but lost a couple of my plug ins as those guys are not all that fast at updating!!)

Thanks and will mark as solved!

Hope FF5 solves the .bin still running shut down problem and the occasional memory leak that were in FF 3 & 4.
It sure is a lot faster, for real!! (even on a Windows box .. it runs circles around IE 7!!)

---

### Post by lovinglinux on 2011-06-27
> **oldsoundguy said:**
> That got it!!  (but lost a couple of my plug ins as those guys are not all that fast at updating!!)

Thanks and will mark as solved!

Hope FF5 solves the .bin still running shut down problem and the occasional memory leak that were in FF 3 & 4.
It sure is a lot faster, for real!! (even on a Windows box .. it runs circles around IE 7!!)

For add-ons, see [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by mons00n on 2011-07-06
thanks this helped me out!

---

