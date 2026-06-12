---
title: "Firefox Update"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by tommyss4l on 2010-07-31
I ran the update manager a few weeks ago and for whatever reason, it downgraded me from Firefox 3.6 to Namoroka (Firefox 3.6 beta release from what I understand). Having had Namoroka before, and knowing how unstable it was, I immediately removed it and reinstalled Firefox 3.5 from Linuxappfinder.com. Upon this last update, Ubuntu again downgraded me from Firefox 3.5 to Namoroka. I am worried about updating my other computer because of this problem. 

Is there any one else out there who is having this problem or knows how to fix it?

---

### Post by lovinglinux on 2010-07-31
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installation, so I don't need to guess what might be happening to your system:

**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://a.imageshack.us/img265/9273/firefoxversion.png[/IMG]


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

### Post by tommyss4l on 2010-08-02
So under Help>About Mozilla Firefox it says Namoroka, but here is the information:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.9pre) Gecko/20100728 Ubuntu/10.04 (lucid) Namoroka/3.6.9pre

Here is the system info:

Ubuntu Architecture  Linux zareason-terra 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=10.04 DISTRIB_CODENAME=lucid DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"  Firefox Packages  firefox						install firefox-branding				install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9pre/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  gdm2setup-gdm2setup-lucid.list gdm2setup-gdm2setup-lucid.list.save lucid-partner.list lucid-partner.list.save medibuntu.list medibuntu.list.distUpgrade medibuntu.list.save ubuntu-mozilla-daily-ppa-karmic.list ubuntu-mozilla-daily-ppa-karmic.list.distUpgrade ubuntu-mozilla-daily-ppa-karmic.list.save ubuntu-tweak-stable.list ubuntu-tweak-stable.list.save

Thanks for the help

---

### Post by lovinglinux on 2010-08-02
It didn't downgrade your Firefox, but upgraded to 3.6.9pre because you have the ubuntu-mozilla-daily repository enabled.

You need to disable that repository through "System >> Administration >> Software Sources", then re-install Firefox 3.5. Keep in mind if you install from the repositories, it will install 3.6.8 instead of 3.5.

---

### Post by tommyss4l on 2010-08-02
Ok, it says it's Firefox now, so I'll give it a few days and see if there are any more issues, thanks for all the help.

---

### Post by tommyss4l on 2010-08-02
I am still having tons of issues with youtube videos, and firefox window turning gray like it's going to crash, but it doesn't and comes back, but the video is still choppy and impossible to watch. Do you have any ideas on that?

---

### Post by lovinglinux on 2010-08-02
> **tommyss4l said:**
> I am still having tons of issues with youtube videos, and firefox window turning gray like it's going to crash, but it doesn't and comes back, but the video is still choppy and impossible to watch. Do you have any ideas on that?

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Also make sure you have the latest video driver installed. Go to "System >> Administration >> Hardware drivers".

Also see [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by tommyss4l on 2010-08-02
OK, I checked my Hardware Drivers, it said that I had no proprietary drivers installed and my only options are help and close. 

Installed flash aid and ran it, it seems to have helped a little, but nothing extravagant, still having huge issues.

I went through the flash optimization page, and did pretty much everything but the xorg stuff, still no improvement.

Everything works just fine on my other laptop that I haven't run the update manager on since installing 10.04. I am getting rather confused about the whole situation.

---

### Post by lovinglinux on 2010-08-02
> **tommyss4l said:**
> OK, I checked my Hardware Drivers, it said that I had no proprietary drivers installed and my only options are help and close. 

Installed flash aid and ran it, it seems to have helped a little, but nothing extravagant, still having huge issues.

I went through the flash optimization page, and did pretty much everything but the xorg stuff, still no improvement.

Everything works just fine on my other laptop that I haven't run the update manager on since installing 10.04. I am getting rather confused about the whole situation.

Looks like your problem is the lack of proprietary drivers for you card. Search the forum for card model and manufacturer to find other users with the same card.

You could also try to right-click on a flash video, then deselect the hardware acceleration option. I'm not sure it will help, but worth a try.

---

### Post by tommyss4l on 2010-08-03
Looks like I am having the most problems with embedded videos. I have an embedded video card, where do I find it's information?

---

### Post by lovinglinux on 2010-08-03
> **tommyss4l said:**
> Looks like I am having the most problems with embedded videos. I have an embedded video card, where do I find it's information?

```
lshw -C display
```

---

