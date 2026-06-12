---
title: "Which Lubuntu x86 version is recommended/LTS?"
date: 2020-01-24
forum: Installation &amp; Upgrades
---

### Post by shade42 on 2020-01-24
On lubuntu.net, looking for the current x86 version:

The link at the top of the main page is for 18.04.

The link at the bottom of the main page is for 18.10 (though it's a dead link at time of writing)

On the Download page, there isn't any guidance as to what x86 version to use, but 18.04 is linked to under 'Previous Alternate Images'.

In the download folders, the latest available is actually 18.04.3.

The Download page appears to recommend anyone looking for an LTS version use 16.04.3, but Wikipedia says support for this ended in April 2019.

Apparently (according to Wikipedia) 18.04 is an LTS version, but the Download page doesn't say so.


I think most people would have given up at this point! The point of Lubuntu as far as I'm concerned it to make best use of very old PCs, but the official site leaves me baffled as to what x86 version to use.

Please advise. Given so many links to x86 18.04, are there problems with 18.04.03 or 18.10? Is Wikipedia correct in saying 18.04 is LTS? Does that mean 18.04.03 is as well?

Thanks

---

### Post by deadflowr on 2020-01-25
18.04 and whatever point release are all the same.
18.04.3 is 18.04.
Lubuntu 18.04 is an LTS, but it's support length is only 3 years.

(All flavors of Ubuntu, except regular Ubuntu, have shorter, 3 year, support cycles for long term releases.)
Which really means Lubuntu 18.04 has a little over one year support left.


Also: for what it's worth, this is the correct and official web page for Lubuntu
[https://lubuntu.me/downloads/]("https://lubuntu.me/downloads/")
lubuntu.net is something else.

---

### Post by guiverc on 2020-01-25
Lubuntu.net is neither a Ubuntu, nor Lubuntu site.  

It's out of the reach of both Ubuntu, or Lubuntu teams - thus we cannot update it.  If you're unsure what web site to use for a flavor, don't ask google (there are multiple unofficial sites for a number of flavors) but ask ubuntu.com (ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)) which will send you to a correct site.

Please use the Lubuntu web site - [https://lubuntu.me/](https://lubuntu.me/)

Some other references  (*from Lubuntu manual*)

[https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)
Chapter 1.1 Retrieving the image - see [https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
Chapter 1.2 Booting the Image - see [https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html)
Chapter 1.3 Installation - see [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

Note: current manual (manual.lubuntu.me) refers to the latest *stable* release which is 19.10.
  Lubuntu 18.04 LTS uses the LXDE desktop so will look different to the images on that page (some functions will also be different, though similar), but LXDE is on *life-support*.

If it's for a x86 box; I'd recommend Lubuntu 18.04 LTS too. 

I have it on a couple of x86 only computers; which whilst they were also used to run 18.10, 19.04 (*and one 19.10*) for testing purposes and ran LXQt really well (*better than XFCE, MATE or anything else I tried; GTK3 is heaver than older GTK2 & was noticeable on pentium M especially*) - 18.04 LTS has 3 years of support so you're covered until 2021-April (ie. 18.04 + 3 years = 21.04 *using year.month format of Ubuntu*)

---

### Post by GhX6GZMB on 2020-01-25
^ +1
Please use lubuntu.me

Other sites could be infested. Start from scratch with your download.

---

### Post by shade42 on 2020-01-25
Thanks for the replies. I had mistakenly concluded that ubuntu.net was the official site. It is quite a mess.

Most of the links on it (that aren't broken) are to cdimage.ubuntu.com, so am not worried about infection.

---

### Post by shade42 on 2020-01-25
Thanks, many useful points there. 

Do I understand correctly that you ran some x86 versions of Lubuntu 19.x? I didn't think x86 versions existed?

---

### Post by GhX6GZMB on 2020-01-25
The latest (and last) x86 version is 18.10.

---

### Post by guiverc on 2020-01-25
ml9104 is correct, Xubuntu & Lubuntu both provided a x86 (i686) image of 18.10, which was the last official release.

Lubuntu & Xubuntu did continue to produce *daily* ISO's into the 19.04 cycle, and as I tested both I got the pleasure of using them in 19.04, but the images stopped being produced in December 2018 (Xubuntu first at beginning of the month, Lubuntu late in the month). Those were alpha images, but once installed were normal and continued receiving all updates normally.

19.04 received all x86 upgrades during it's full life, but install media was never officially released. It however is now EOL. ([http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/))

One (pentium IV) box I bumped to 19.10 again pre-release and got to see the effect of the turned-off infrastructure that used to build x86 images; ie. some packages no longer receive updates (my kernel remains 5.3.0-13-generic kernel).  19.10 x86 never had any dailies; and it was in the last week before release when build infrastructure stopped building some packages (some still update - but I wouldn't trust it)

---

