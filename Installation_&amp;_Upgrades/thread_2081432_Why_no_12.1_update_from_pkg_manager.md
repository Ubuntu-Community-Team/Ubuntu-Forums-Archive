---
title: "Why no 12.1 update from pkg manager?"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by nudnikian on 2012-11-06
Just curious about how I should update 12.04 to 12.10. My 12.04 has been largely successful, but I'd like to get the latest LTS and then stick with it for a while (years?).  I was able to install 12.04 from 11.1 using the software manager.  I don't see the offer to update from 12.04 to 12.10 on either the software manager or the "up-to-date" patch menu? Any reason for this?

---

### Post by David D. on 2012-11-06
12.04 is the latest LTS.  Version 12.10 is not a LTS, so if you want to stick with a LTS you should keep what you have now.

---

### Post by ibjsb4 on 2012-11-06
Your software sources is probably set for LTS upgrades.  12.10 is not an LTS, but if you want the latest and greatest, just change the release setting.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

---

### Post by uclugLee on 2012-11-07
Agreed. 12.04 is the current LTS version.  However, if you want to upgrade to 12.10, open Software Sources, go to the Updates tab, and change the drop down option of "Notify me of a new Ubuntu version" to say "For any new version".  You will then get prompted that there is an upgrade available.

---

### Post by 2F4U on 2012-11-07
> **nudnikian said:**
> Just curious about how I should update 12.04 to 12.10. My 12.04 has been largely successful, but I'd like to get the latest LTS and then stick with it for a while (years?).  I was able to install 12.04 from 11.1 using the software manager.  I don't see the offer to update from 12.04 to 12.10 on either the software manager or the "up-to-date" patch menu? Any reason for this?

12.04 IS the latest LTS release, so if you want to use LTS stay with 12.04. Also, if you read through the forums a bit, upgrading to 12.10 causes quite some problems for a lot of people. If 12.04 is working for you, I would suggest to stick with it as long as possible.

---

### Post by tomdkat on 2012-11-08
> **2F4U said:**
> 12.04 IS the latest LTS release, so if you want to use LTS stay with 12.04. Also, if you read through the forums a bit, upgrading to 12.10 causes quite some problems for a lot of people. If 12.04 is working for you, I would suggest to stick with it as long as possible.You raise an interesting point here.  It's true that the 12.10 release has been problematic for people but couldn't that also be the case for the next LTS release of Ubuntu? I mean that would be a "new release" when it comes out, just like 12.10 is right now. 

I understand the rationale behind sticking with LTS releases but it seems the upgrade issues would or could be the same (or similar) regardless if upgrading to the next LTS release or an interim release.

Thanks for the info posted in this thread as it helped me too.  :)

Peace...

---

### Post by uclugLee on 2012-11-08
Let me touch base on this a little bit.  Mods, please move is this is not the appropriate forum.

I'm on the laptop testing team, and judging by the last email I got, there are only about 12 people on the laptop testing team, not including those who may work for Canonical.  Now, I have three laptops that I test with, but they are all Dell machines and the newest one is 3 years old.  What happens is there are so many different machines out there that not all of them get tested during the alpha and beta phases.

So for those that are having issues, I would love to recommend that you get involved in testing.  I don't want to sound like a commercial or a sales pitch, but the more we have testing and submitting bug reports, the better we all can make Ubuntu.

---

### Post by nudnikian on 2012-11-08
> **2F4U said:**
> 12.04 IS the latest LTS release, so if you want to use LTS stay with 12.04. Also, if you read through the forums a bit, upgrading to 12.10 causes quite some problems for a lot of people. If 12.04 is working for you, I would suggest to stick with it as long as possible.

  Thanks for the clarifying responses.  I'm begining to get the distinction between LTS and regular releases.  Perhaps I should slow down and work with 12.04.

---

### Post by sammiev on 2012-11-08
> **tomdkat said:**
> You raise an interesting point here.  It's true that the 12.10 release has been problematic for people but couldn't that also be the case for the next LTS release of Ubuntu? I mean that would be a "new release" when it comes out, just like 12.10 is right now. 

I understand the rationale behind sticking with LTS releases but it seems the upgrade issues would or could be the same (or similar) regardless if upgrading to the next LTS release or an interim release.

Thanks for the info posted in this thread as it helped me too.  :)

Peace...

What you say is very true but I had more troubles with the LTS version after it was released than 12.10. It depends on your hardware and so on. If you are using the LTS version with no problems then stay with it. If you are having problems with the LTS version, then burn a copy of the later and test it on a live boot to see if it works for you.

---

### Post by grahammechanical on 2012-11-09
Before the release of 12.04 I tested the upgrade path from from both 10.04 and 11.10. I did not have any problems. But then, I have never had a problem installing any version of Ubuntu on my hardware since 7.04.

It is my opinion that people have problems with upgrades when they have heavily modified the desktop. It is similar to what ucluglee is saying about laptops.

The upgrade is tested from default install to default install. It cannot be done any other way because the developers cannot know about the great variety of ways in which the user has modified the operating system. This is why you will find on the forums recommendations to do a fresh install.

It is my policy to have a spare partition of the hard disk that I install the next release of Ubuntu into. I then dual boot between the two releases as I test out the next release to see if I can set it up the way I like and install the applications that I like. Only then do I consider upgrading or fresh installing.

Regards.

---

