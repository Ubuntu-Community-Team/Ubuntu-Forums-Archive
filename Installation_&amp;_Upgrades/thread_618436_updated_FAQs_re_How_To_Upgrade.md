---
title: "updated FAQs re How To Upgrade ?"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-11-20
The current FAQ/stickies are out-of-date or mislabeled.  For instance, the sticky re "Dapper" seems more general than just that old version.  And the sticky for "Edgy" doesn't seem to apply at all now.  Also, I'd like to see a sticky that directly included the info rather than linking to other posts (most of which is, inevitably, unimportant discussion).

I'd like to propose a new sticky entitled, "HOW AND WHEN TO UPGRADE", and with contents such as the following:
________________

**HOW AND WHEN TO UPGRADE**

'Straight' talk about upgrading Ubuntu, presented in 7 parts.

**1) What's the purpose of this FAQ?**

- I am assuming that you have already installed Ubuntu at least once before, and so this FAQ does not have any discussion of actual procedures.
- Not focusing on specific versions allows this FAQ to stay applicable across all versions.
- My impression is that 'a lot' of people regret upgrading their Ubuntu systems.  This mostly seems to happen because people assume that upgrades work 100% of the time, and that all their existing programs and customizations will continue to work.

**2) Why should I upgrade?**

- Each new release of Ubuntu includes new and improved versions of the various software programs.  Some of these new versions are also available for previous Ubuntu releases, but if there's something important to you which is not 'back ported', e.g. newer OpenOffice, then it's probably time to upgrade your entire Ubuntu setup.
- The automated upgrade process (described below) is only tested for the version of Ubuntu immediately prior, i.e., you can't wait for more than 1 new version to come out and then try to upgrade through 2 or more updates.
- Every version of Ubuntu will eventually stop receiving security updates -- from initial release, 36 months for Long Term Support/LTS versions, 18 for interim versions

**3) Why wouldn't I upgrade?**

- If you're happy with your current setup, just let it ride.  You'll continue to receive updates for at least a little while (see comment above re security updates)
- If you've heavily customized your setup, then an upgrade is probably going to cause more problems then improvements.  Besides, you're probably an advanced user who doesn't need this FAQ anyway!
- Unfortunately, there's no such thing as a perfect 100% guaranteed upgrade.  There are just too many variables.  The less you've customized your current install, however, the more likely it is to succeed. 

**4) What's the easiest way to upgrade?**

- The easiest way to upgrade is simply to load the Update Manager, select "Install new version" and hope for the best.  The vast majority of the time, this will work just fine.  And if you've done nothing to customize your setup, it's almost guaranteed to work.  But hopefully you'll have the time and energy to do a little CYA first (see below).
- In the following sections I suggest two alternate ways to upgrade -- the Ideal, and the Reasonable, plans

**5) What's the ideal way to upgrade?**

- Ideally you would never upgrade -- you'd do a clean install instead. But this takes a lot longer and is more complicated to do.
- You would also, ideally, want to use a new hard-drive each time.  This has several benefits: 
[LIST]you can easily switch back to your original setup since the original drive would be untouched
[*]you can mount the old drive as a secondary/data drive and copy your old data and/or settings as needed
[*]you can take your original drive and store it, i.e., if you're a typical computer-owner and never make backups
[*]hard drives are by far the _least_ reliable part of your computer, so it's good to proactively replace them![/LIST]
- By doing a clean install, you'll lose all your custom settings.  But afterwards you can selectively restore your original home directory files, i.e., the hidden configuration folders, and watch to see if the new versions of each program 'accept' the old configuration files (and hopefully upgrade them)
- Finally, ideally you've been making notes of everything you've customized; I know **I do** but then I've worked in IT for 20 years and have learned the hard way to be ultra-organized.  After a clean install you could then manually re-apply the customizations you still want.

**6) What's a reasonable way to upgrade, a way without too much extra work?**

[LIST=1]Make sure you have access to another computer with Internet access, so that you can reach these support forums for research and help.
[*]Make a backup of your personal files beforehand.  By default, this would be the entire /home/<you> folder but if you've been storing files in other folders then you should know where they are, too!
[*]Undo any custom configuration, e.g. proprietary video drivers.
[*]Try booting with the new LiveCD for the new version.  Make sure that the network card is detected.  Look for any other hardware detection problems?
[*]Use the Update Manager to do an online update.  But don't do it right after a new version comes out!  If you wait a week or two, you'll avoid the initial rush which can cause the online servers to overload or stall (and mess up your upgrade?).  Also, the longer you wait, the more additional bug fixes will be included (updates which the CDs wouldn't have).
[*]Keep a list of the recovery tips (below) handy.[/LIST]

**7) How do I recover from a botched upgrade???**

- If your computer restarts but goes to a command-line rather than the GUI, login and re-run the video setup,
```
 > sudo dpkg-reconfigure xserver-xorg
```
- If your computer refuses to load Ubuntu, boot the LiveCD and see if you can access your files.  (You _do_ have a LiveCD from my previous suggestion re testing the network driver beforehand, right?)  This will tell you if there's been a hard drive failure.  It will also allow you to correct the configuration file(s) causing the problem.

---

### Post by bsmith1051 on 2007-11-20
or, maybe we just need to copy (and tweak as needed) some of all the Install FAQs in the Absolute Beginner sub-forum!  Geez, I've using these forums for over a year and never even looked in that sub-forum...

Feel free to post suggested changes and I'll update the original post with them.  But I reserve the right to filter and/or edit the suggestions, as I'm hoping to keep this FAQ from getting too cluttered, i.e., no more than 7 items per section.  (Notice how I only have 7 sections, too?)

---

