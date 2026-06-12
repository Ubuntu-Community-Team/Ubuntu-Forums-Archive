---
title: "Could I lost something updating from 13.04 to 13.10 (noob question)"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by roroland on 2013-11-06
Hi, sorry to ask this, I know this could be silly, but I always do clean installations of ubuntu, but this time I can't afford to do that, so I was thinking to update my current ubuntu version from 13.04 to 13.10 from the update manager.

I use this to run xampp and rails servers as a web designer, also I have some desktop tweak like, themes and so on....so my biggest fear is to lost something, can you tell me if the upgrade should be smooth (I know there is no warranties) like installing a normal package update ?

Thanks in advance

---

### Post by TheFu on 2013-11-06
I have not done this update myself.

However, all major updates like this are filled with risk.

RoR is extremely picky ... that is why developers use RVM or rbenv - to protect their development environment from pesky OS dependency issues. rvm and rbenv ARE best practice methods.  Setting up rvm is the first thing that my Ruby group teaches. We follow *Ruby on Rails Tutorial: Learn Rails by Example* by Michael Hartl for beginner training. The entire book is free online [http://ruby.railstutorial.org/ruby-on-rails-tutorial-book](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book)

It is best to do a complete - positive-you-can-recover - backup, prior to starting.
Also, if your /home is on a separate partition, then your risks are much reduced.

OTOH, every upgrade *should be smooth*, but hope is NOT a plan. I think you'd really want a plan, but only you can answer that.

---

