---
title: "New Computer"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2012-11-06
Time for a new Internet only laptop.The one I'm using now has Ubuntu 10.04 on it.Once I get back to were I was I want to upgrade to the latest LTS. I haven't loaded any extra software at all on it(the old computer) as Ubuntu comes with Firefox.I have configured GNOME PPP for my dialup USB modem.So the question is this:
Once I install Ubuntu on the new computer can I just copy the Home Folder from the old to the new? I think I can and everything will be as it was on the old.
Thanks

---

### Post by drmrgd on 2012-11-06
It will be more or less.  You'll get things back like your .bashrc  and .vimrc (if you use those kinds of things).  You'll also get things like your Mozilla profile (if you use Firefox and / or Thunderbird), and some other custom settings.  This, of course, all in addition to any data files you have in /Home.  

However, there could be a number of packages that will be new and the old settings will not be useful or will not propagate well. A good example of that might be custom window settings and session details.

What I did the last time I set up a new computer was to save all those files and just patch in the ones I needed / wanted.  I didn't care about reconfiguring new packages.  However, I did want to retain my bookmarks, email, and such.  

So, definitely save /home and migrate it in.  Just be aware that you still *could* need to tweak things a little and it won't be quite like you left it.

---

### Post by Silvertones on 2012-11-06
> **drmrgd said:**
> It will be more or less.  You'll get things back like your .bashrc  and .vimrc (if you use those kinds of things).  You'll also get things like your Mozilla profile (if you use Firefox and / or Thunderbird), and some other custom settings.  This, of course, all in addition to any data files you have in /Home.  

However, there could be a number of packages that will be new and the old settings will not be useful or will not propagate well. A good example of that might be custom window settings and session details.

What I did the last time I set up a new computer was to save all those files and just patch in the ones I needed / wanted.  I didn't care about reconfiguring new packages.  However, I did want to retain my bookmarks, email, and such.  

So, definitely save /home and migrate it in.  Just be aware that you still *could* need to tweak things a little and it won't be quite like you left it.
Thanks.
I keep the old computer right up to date. This is my plan.
1. Install 10.04 on the new computer
2. Get all the updates
2a. Install TB
3. Migrate the Home folder
It should go OK as I use Ubuntu without any tweaks. Just use Firefox and Thunderbird
4. Upgrade to the latest LTS

---

### Post by drmrgd on 2012-11-06
Why install 10.04 only to upgrade right away?  Why not just start off fresh with 12.04?  I think this will take much less time and go much more smoothly than going through an upgrade process right away.

---

### Post by darkod on 2012-11-06
> **drmrgd said:**
> Why install 10.04 only to upgrade right away?  Why not just start off fresh with 12.04?  I think this will take much less time and go much more smoothly than going through an upgrade process right away.

+1. You are only asking for trouble by installing the OS only to upgrade it immediately. While it might offer greater chance of accepting the settings you copy over with your Home folder, the possibility things to go wrong or corrupted during the upgrade I think outweight those benefits.

---

### Post by Silvertones on 2012-11-06
> **drmrgd said:**
> Why install 10.04 only to upgrade right away?  Why not just start off fresh with 12.04?  I think this will take much less time and go much more smoothly than going through an upgrade process right away.
Yea you're probably right. I guess upgrades do not always go as planned and most folks do fresh installs.

---

