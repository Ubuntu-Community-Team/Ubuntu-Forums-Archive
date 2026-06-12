---
title: "Windows installed on the last partition"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2016-04-11
Hi guys.  I don't know if this is the right forum to post this.  I just want to show anyone who might be interested that Windows CAN be installed on the last (right-most) partition in a dual-boot system.

I've done this setup on three desktop computers already.

This is what it looks like in Gparted:

[  |  data (ntfs)  |  Lubuntu   |  swap  |  ]  [ Freedos ]  [ Windows 7 ]

data, lubuntu, and swap is inside an extended partition, while freedos and windows 7 are installed in two separate primary partitions.

Good day.

By the way, can I post my own contribution to this community? I want to post something like a list of all the things that I do to make a fresh Lubuntu installation "complete", from installing pulseaudio volume control to uninstalling or replacing several built-in applications.  Or has someone done that already?

---

### Post by ajgreeny on 2016-04-11
You could add a thread to the tutorials section of the forum [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100) but I suspect if you look in that section and do a search you will find that someone has already done what you speak of in your final paragraph.

See [https://www.google.com/url?q=http://ubuntuforums.org/showthread.php%3Ft%3D1880394&sa=U&ved=0ahUKEwjbh9ia6obMAhVFLg8KHUGZBnAQFggHMAE&client=internal-uds-cse&usg=AFQjCNHT14_iBS81LJXPPpq0GbGGcjM-hQ](https://www.google.com/url?q=http://ubuntuforums.org/showthread.php%3Ft%3D1880394&sa=U&ved=0ahUKEwjbh9ia6obMAhVFLg8KHUGZBnAQFggHMAE&client=internal-uds-cse&usg=AFQjCNHT14_iBS81LJXPPpq0GbGGcjM-hQ)
and
[https://www.google.com/url?q=https://help.ubuntu.com/community/Lubuntu/Documentation&sa=U&ved=0ahUKEwjbh9ia6obMAhVFLg8KHUGZBnAQFggFMAA&client=internal-uds-cse&usg=AFQjCNGFmHF6gWBJeM6HvOc9qCNB6_0YfQ](https://www.google.com/url?q=https://help.ubuntu.com/community/Lubuntu/Documentation&sa=U&ved=0ahUKEwjbh9ia6obMAhVFLg8KHUGZBnAQFggFMAA&client=internal-uds-cse&usg=AFQjCNGFmHF6gWBJeM6HvOc9qCNB6_0YfQ)

I suspect it is easy to find a lot more already written about the subject.

---

