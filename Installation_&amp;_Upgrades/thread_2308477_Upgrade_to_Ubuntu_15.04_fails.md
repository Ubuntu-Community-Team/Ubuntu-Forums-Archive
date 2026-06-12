---
title: "Upgrade to Ubuntu 15.04 fails"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by einpekkar on 2016-01-03
Been trying for some time to upgrade from 14.04, but keep getting the same result. Attached are the error message I get. After this the system i reset to previous state and I'm back to square one. Any ideas?

[IMG]https://dl.dropboxusercontent.com/u/87830328/Screenshot%20from%202016-01-03%2020%3A30%3A17.png[/IMG]

---

### Post by grahammechanical on 2016-01-03
You cannot upgrade Ubuntu 14.04 to Ubuntu 15.04 without first upgrading to Ubuntu 14.10. But you cannot upgrade to 14.10 because 14.10 has reached end of life. Its repositories are now closed and have been moved to another location. This means that the URLs in the software sources list are inaccurate. And that is the cause of the problem.

There is a way to upgrade to and from and end of life releases but Ubuntu 15.04 is about to reach end of life itself. And so if you do get to 15.04 you will then need to upgrade to 15.10 which only has 9 months support that started the end of October 2015. So, you will have to eventually upgrade to 16.04.

As you are on 14.04, my advice would be to stay on 14.04 then you can upgrade directly to 16.04 when it is released end of April 2016. It will only be one upgrade and not four.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by einpekkar on 2016-01-04
Sounds like a plan ;)

---

### Post by kansasnoob on 2016-01-04
> **grahammechanical said:**
> You cannot upgrade Ubuntu 14.04 to Ubuntu 15.04 without first upgrading to Ubuntu 14.10. But you cannot upgrade to 14.10 because 14.10 has reached end of life. Its repositories are now closed and have been moved to another location. This means that the URLs in the software sources list are inaccurate. And that is the cause of the problem.

There is a way to upgrade to and from and end of life releases but Ubuntu 15.04 is about to reach end of life itself. And so if you do get to 15.04 you will then need to upgrade to 15.10 which only has 9 months support that started the end of October 2015. So, you will have to eventually upgrade to 16.04.

As you are on 14.04, my advice would be to stay on 14.04 then you can upgrade directly to 16.04 when it is released end of April 2016. It will only be one upgrade and not four.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

Regarding this:

> You cannot upgrade Ubuntu 14.04 to Ubuntu 15.04 without first upgrading to Ubuntu 14.10.

That's no longer true:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

But the process is borked:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1497688](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1497688)

Regardless it's really foolish to upgrade from 14.04, which is an LTS version, to 15.04 which will be EOL before the end of the month:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Best to just remain on 14.04 and then upgrade to 16.04 when it's released.

---

### Post by Bucky Ball on 2016-01-04
> **kansasnoob said:**
> Best to just remain on 14.04 and then upgrade to 16.04 when it's released.

+1. Stick with LTS unless you have a good reason not to. Works for me in any case. :)

---

