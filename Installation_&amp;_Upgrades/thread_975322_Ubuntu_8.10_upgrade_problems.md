---
title: "Ubuntu 8.10 upgrade problems"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by mjfowler on 2008-11-08
Hi,

I've just upgraded from Ubuntu 8.04 to 8.10 on my Dell Dimension 3000, and I am now experiencing the following problems:

1. There is some significant screen tearing when opening windows in Thunderbird and Firefox

2. Printing via HPLIP to an HP LaserJet 6L produces a string of random symbols at the top of the page

3. Startup is verbose, i.e., I get system messages displayed and no usplash, whereas the menu.lst entry includes 'quiet' and 'splash' options.

Has anybody else experienced these problems? any suggested fixes, please?

Thanks,

Mike

---

### Post by ajhoover on 2008-11-09
I've been getting the gibberish characters at the top line of the first page of print jobs also since upgrading to 8.10. Also an HP LaserJet 6L. I haven't found a solution yet.

---

### Post by ajhoover on 2008-11-09
> **mjfowler said:**
> Hi,

I've just upgraded from Ubuntu 8.04 to 8.10 on my Dell Dimension 3000, and I am now experiencing the following problems:

1. There is some significant screen tearing when opening windows in Thunderbird and Firefox

2. Printing via HPLIP to an HP LaserJet 6L produces a string of random symbols at the top of the page

3. Startup is verbose, i.e., I get system messages displayed and no usplash, whereas the menu.lst entry includes 'quiet' and 'splash' options.

Has anybody else experienced these problems? any suggested fixes, please?

Thanks,

Mike

It seems to be fixed on mine. After finding these posts--http://ubuntuforums.org/archive/index.php/t-865466.html--I deleted and re-installed the printer with the Gutenprint driver, and no longer get the garbage line at the top of the first page.

I was using the driver: 'HP LaserJet 6L Foomatic/ljet4 (recommended)'
I changed it to: HP LaserJet 6L - CUPS+Gutenprint v5.2.0-rc1

---

