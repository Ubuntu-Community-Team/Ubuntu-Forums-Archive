---
title: "Problem with a remote repository"
date: 2022-03-01
forum: Installation &amp; Upgrades
---

### Post by sbloom67 on 2022-03-01
Hello All,  I built a local Ubuntu 20.04.03 repository using apt-mirror on a server that is in our DMZ network.   That server gets updated every day by running apt-mirror in the cron.  I also built a Ubuntu server in our Production network.  That server has apache2 running and we rsync the contents of /var/www/html/ from the DMZ server to the Production server every day.  I have also updates the sources.list file to have the changes for the server in productions.  The issues is when I do an apt update , I get some errors, but not all and there are no updates to be had.  I know that there are definitely updates available.  Anyone have any ideas on what I am doing wrong ???

Thx Steve

---

### Post by guiverc on 2022-03-01
You're mixing details.  Details do matter.

Ubuntu Core 20 is a different server product to that far more common *year.month* format products, ie. 20 represents a *snap* only server product where as 20.04 represents the 2020-April release of the *deb* based Ubuntu product for Servers and Desktops.

You mention 20 implying it's a snap only system, but then mention sources, apt & commands for a 20.04 system.

20 != 20.04

Question also asked at [https://askubuntu.com/questions/1395490/i-need-help-with-ubuntu-20-remote-repo](https://askubuntu.com/questions/1395490/i-need-help-with-ubuntu-20-remote-repo)

---

### Post by sbloom67 on 2022-03-01
yes its ubuntu 20.04.  and I asked the question on another forum as well.  Do you know how to configure repositories ???

---

