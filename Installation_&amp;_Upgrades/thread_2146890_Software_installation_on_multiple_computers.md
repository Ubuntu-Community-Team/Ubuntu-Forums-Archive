---
title: "Software installation on multiple computers"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by xom1kadze on 2013-05-20
Hello,
I've computer lab with 30 computers, all of it running Ubuntu. And also Ubuntu server computer. 
When it is need to install new software, or update Ubuntu for a new version(For  ex: to 13th) all of work is doing manually on each computer. That way is very time and bandwidth consuming.
 So, the task is to manage way of simultaneous (and 'silent') software and updates installation on that 30 computers from server. Principle of work is next: server computer gives command to install package on computers (all, group or just one) and this package gets installed for users on that computer without any actions performed on that computer, only on server.
P.S.: Early on forum was _[thread]("http://When installing same packages, or updating Ubuntu on multiple computers, if I have to download and install same packages by running Synaptic Package Manager on each computer, or running update manager on each computer to update Ubuntu, it will waste a lot of bandwidth and time.So, is there anyway for just using ONE of the computers to download and install the packages (including the dependencies, with or without Synaptic Package Manager) / Ubuntu updates, then install the same packages / Ubuntu updates on other computers without re-download on each computer?")_ with quite simular question, but there is only answer how to do caching on server for updates and packages. But clients, in such way, must request manually for installation.

---

### Post by 2F4U on 2013-05-20
It is possible to configure clients as well as servers to automatically install updates:

[URL="https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo"]https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo

[/URL]If you want the server to initiate the update you would need to some sort of software distribution management system, maybe something like this:

[http://m23.sourceforge.net/PostNuke-0.750/html/index.php](http://m23.sourceforge.net/PostNuke-0.750/html/index.php)

I am not aware of any method to automatically upgrade a system, e. g. from 12.10 to 13.04. In order to save bandwidth, you could setup a local/offline repository:

[http://askubuntu.com/questions/147654/how-to-setup-local-repository-for-ubuntu-12-04](http://askubuntu.com/questions/147654/how-to-setup-local-repository-for-ubuntu-12-04)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)

---

