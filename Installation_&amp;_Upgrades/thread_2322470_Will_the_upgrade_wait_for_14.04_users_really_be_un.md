---
title: "Will the upgrade wait for 14.04 users really be until July?"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by 98cwitr on 2016-04-28
"[COLOR=#333333]Users of 14.04 LTS will be offered the automatic upgrade when 16.04.1 LTS is released, which is scheduled for July 21st."

[/COLOR]http://fridge.ubuntu.com/2016/04/21/ubuntu-16-04-lts-xenial-xerus-released/

So check to see if the update was available because nothing has come down automatically yet

```
do-release-upgrade -c
```

Which yielded no results. I can install using the -d switch, but figured there must be a reason for the wait. In doing some research I found the above link and was very surprised that they could hold off on the automatic upgrade all the way until July. I assume there's no real difference between the package available for upgrade and the distro that's available for install right now. With Chrome no longer updating and my wireless drivers not working with the 3.13 kernel for the past two years, I'm kind of itching to see if they will work with 4.4.

Why is it has Canonical is holding off the upgrade users so long?

---

### Post by grahammechanical on 2016-04-28
The -d switch will not upgrade 14.04 or 15.10 to 16.04. It will upgrade to Yakkety Yak the development version of 16.10 which when it is released in October will only have 9 months support.

There are reasons why the LTS to LTS upgrade has been postponed until July. I can only guess at the reasons.

One of which could be the non existence of AMD proprietary video drivers in 16.04. AMD is not supporting its proprietary video drivers on 16.04 because 16.04 uses a version of the X server that AMD drivers do not work well with. AMD is putting a lot of work into its open source video drivers (radeon & amdgu). That work may have some good results by the summer.

Keep in mind that 14.04 still has 3 years support left. So, there is no real reason to rush to upgrade. In my opinion that only people who really need to install the very latest version of Ubuntu are those who have purchased the very latest hardware or have some hardware issue that they hope the latest version will resolve.

My advice to you is to download the latest 16.04 image and put in a dual install of 14.04 & 16.04 and see if the hardware issues are really resolved.

As for Chrome not updating that should be solvable. Is the problem related to Google no longer supporting 32 bit version of Chrome on Linux? We can edit a configuration file to fix that issue.

[URL="http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html"]http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html

[/URL][http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu)

Regards

---

### Post by Impavidus on 2016-04-28
For 18 months in which you used 14.04, a newer version was available. You did not upgrade to 14.10, 15.04 and 15.10. So, it is assumed that you, and all the others like you, want stability more than the latest software. It was therefore assumed that you would be happy to wait for another 3 months before upgrading, so that bug removal and driver support have improved.

Note that it is possible to install a newer kernel on 14.04. It's called a [hardware enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). Maybe a little late now, as you could as well move on to 16.04.

---

### Post by ajgreeny on 2016-04-28
A lot of users of the LTS versions are business users who can not allow an LTS to LTS upgrade to go ahead until they can be sure all the bugs in the new version are ironed out; certainly all the bugs that could cause a business user to lose the OS on which they depend.

For that reason the upgrades wait until the point version 1 appears by which time hopefully only minor bugs will remain.

If you read these forums much you must have seen that there have been quite a few problems where users have already upgraded using the command line; it's those problems which Canonical is hoping to avoid by waiting for the 3 months, which is not that long when you consider there will be a support period of 5 years.

---

### Post by 98cwitr on 2016-04-28
> **grahammechanical said:**
> The -d switch will not upgrade 14.04 or 15.10 to 16.04. It will upgrade to Yakkety Yak the development version of 16.10 which when it is released in October will only have 9 months support.


Actually that's not the case at all. From LTS to LTS (that is, setting the update-manager to LTS upgrades to Long term releases only) -d results in upgrade to 16.04 LTS. I am running it right now...tired of waiting :D

---

### Post by 98cwitr on 2016-04-29
Sadly, my wifi still doesn't work :( Pinging the gateway simply results in destination unreachable.

---

