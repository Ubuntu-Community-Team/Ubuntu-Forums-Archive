---
title: "Dual Boot - Ubuntu 12.04 LTS &amp; Puppy Linux"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by rodmiles on 2013-02-05
Hi All,

I'm currently running Ubuntu 12.04 LTS on my HDD as the main OS. I have a USB drive with Puppy Linux on it which we can boot to by intervening in the boot up process (F12), however, I want to copy everything on this flash drive to the main HDD and retain everything that is already set up for this installation of Puppy Linux.

The BIOS setup for this particular PC won't let us set the boot option to USB first and it will just be easier to have it boot up, display either Ubuntu 12.04 LTS or Puppy Linux so we can choose either at the start of the day and be done with it.

*A bit of background - The Puppy Linux USB drive is set up to boot into a secure kiosk mode and has all of the settings that we need for it to perform the function for which it is intended.*

Is it at all possible to just copy the file system contents of the USB drive to a partition on the main HDD and set it up to boot from there some how?

Thank you in advance for your help ;)

---

### Post by varunendra on 2013-02-06
Report by rodmiles -
> Please delete this thread for me, I figured it out and don't want to dilute the community efforts.

Hi rodmiles,

We would appreciate if you can post how you got it done so other too can get benefitted by your experience.

After posting a short description and possibly steps on how to do it, you should consider marking the thread as **[Solved]** so others looking for a similar solution may know this one contains a solution.

There's no need to close it as it is relevant and unique. :)

Thank you.

---

### Post by rodmiles on 2013-02-06
Oh ok, I like the community atmosphere of helping people out! I'm still new to this and it's been a pleasant experience thus far :)

My solution was almost embarrassingly simple really...

I was able to update the Lenovo M58p machine BIOS to the latest version by going here  [http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-70892](http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-70892) which took care of the booting to USB on startup issue. This means that I do not need to worry about doing a frugal install of Puppy on my main HDD (which isn't recommended anyway).

Although I found the startup scripts pertaining to the setup of Opera into a bulletproof kiosk mode and I could have copied these to the Ubuntu OS with some changes to the locations/directories I decided not to go down that path since the USB Puppy filesystem is fully operational...Apart from the dang Intel Gigabit Network Card still not working in Puppy (still working on trying to load that module manually which is hurting my brain).

In starting to investigate the copying of the startup scripts over from Puppy to Ubuntu I found this article to start me off on the right path [http://stackoverflow.com/questions/12973777/how-to-run-a-shell-script-at-startup](http://stackoverflow.com/questions/12973777/how-to-run-a-shell-script-at-startup)

Anyway, I hope this does help someone somewhere someday :)

---

### Post by varunendra on 2013-02-06
That's pretty comprehensive, Thank you again!

Feel free to ask your questions in existing threads or start new threads of your own as long as they are not duplicates. If the threads/posts happened to be in wrong place, use the "Report abuse" button to make a request, and someone would happily do the job for you.

Although that button says "report _abuse_", it can be used for anything that needs mods/admins' attention.

Hope you'd have a good time here .:)

---

