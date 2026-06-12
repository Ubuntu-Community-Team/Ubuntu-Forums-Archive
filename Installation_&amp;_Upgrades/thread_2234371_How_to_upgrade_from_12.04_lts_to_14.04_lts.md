---
title: "How to upgrade from 12.04 lts to 14.04 lts"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by Richard_Lorentz on 2014-07-14
I thought I read somewhere that I should be able to do this in July, but still no luck when I type do-release-upgrade. (Side comment: I'm hoping this will also fix my java woes with Google Chrome.) Any thoughts/suggestions?

Thanks!

---

### Post by slickymaster on 2014-07-14
Can you please give us a bit more information? Are you getting any errors? Can you post them?

The process itself is fairly simple, First things first, make sure that you are fully up-to-date. Double check by opening the Update Manager application from the dash and installing all updates listed.

When that&#8217;s done, open the dash again and launch a terminal window and run```
sudo update-manager -d
```Hit the return/enter key and, if prompted, enter your user password.

The Update Manager application will open after a few seconds with a prompt to upgrade. Click this button to begin the process.

---

### Post by Richard_Lorentz on 2014-07-14
When I type:
sudo do-release-upgrade

I get:  Checking for a new Ubuntu release
No new release found

And when I type: sudo update-manager -d

Ohhh... I get an upgrade button! Strange.

I'll click it and report back. Thanks!

P.S. It says New Ubuntu release '14.04' is available. No mention of LTS. Am I safe upgrading from 12.04 LTS?

---

### Post by slickymaster on 2014-07-14
All LTS desktop users need to wait until the Ubuntu LTS v14.04.1 is released by Canonical. That's why you're passing the **-d** option to the update-manager command so you can upgrade Ubuntu 12.04 LTS to Ubuntu 14.04 LTS before that

---

### Post by Richard_Lorentz on 2014-07-14
Your use of the phrase "need to wait" seems to suggest I should wait until that version is released -- around the end of next week according to reports. What would be the danger in doing it now (when I happen to have the time)?

---

### Post by slickymaster on 2014-07-14
Upgrades between LTS releases are not enabled by default until the first point release, which for this version is 14.04.1, mainly because most users that use LTS are conservative, even more so on the server side, so prompting for updates isn't enabled until the point release.

Basically what you'll get in a week is that a few bugfixes have been published between between the release and the point release thus making 14.04.1 a culmination of all those bugfixes.

If you're itching to move to 14.04 right away though, you can follow the instructions to move to 14.04 immediately.

---

### Post by Richard_Lorentz on 2014-07-14
Had a few more than the usual problems, but I'm basically up and running now.

Thanks!

---

### Post by slickymaster on 2014-07-15
You're welcome. Happy *buntuing.

---

