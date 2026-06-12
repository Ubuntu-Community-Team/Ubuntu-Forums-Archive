---
title: "ubuntu 8.04 flash and gcc problem"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by indianhits on 2011-05-31
hello guys i recently installed ubuntu 8.04 from Desktop CD (from shipit service) and when i tried to install the flash from adobe site it doesn't work i downloaded the tar(i couldn't find .deb file) file and extracted it to desktop then i followed the instruction in README but still it doesn't work  FOR GCC: as i dont have internet i deselected all the internet downloadable files and enablied only the cd-rom in the software sources and tried this command &quot;sudo apt-get install bulid-essential&quot; and &quot;sudo aptitude install bulid-essential&quot; but it shows that it cannot find the packages.what could be the reason ??? i needed to install necessary files for gcc as when i compile the .C file it shows me that stdio.h is not there.

---

### Post by mörgæs on 2011-05-31
8.04 is unsupported. I recommend a fresh install of one of the supported releases:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by sanderd17 on 2011-05-31
8.04 has reached the end of life, three years support (for an LTS) means that it ended in april this year.

Reaching end of life means that the repositories are taken offline, so you can't install anything new and you don't get security updates anymore. I suggest you to install 10.04. That is supported until april 2013.

---

### Post by indianhits on 2011-05-31
i dont have a very good internet speed but still i tried to download ubuntu 11 but the ISO got corrupted   BTW i have the 8.04 & my friend has 8.10 CD how can i install bulid-essential using the CD it gives me error saying it cannot find package

---

### Post by mörgæs on 2011-05-31
Best is to download Ubuntu using a torrent or Wget. Using these it is very unlikely that you get a failed download.

---

### Post by sanderd17 on 2011-05-31
8.10 has reached the end of life a long time since it's not an LTS. So you will get the same problem.

If you need to get a CD with a bad internet connection, you might want to buy one from cannonical: [http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)

I don't know if you're a unity fan or not, but if you're not, I would suggest you to buy the 10.10. There are a lot of people complaining about 11.04 (including my family, so I gave them 10.10 back).

I don't know where you live, but maybe if you ask this forum for someone that lives close to you, or one of the loco teams ( [http://loco.ubuntu.com/teams/](http://loco.ubuntu.com/teams/) ), that person might lend you a CD.

---

