---
title: "Upgrade from 10.04 LTS to 12.04 LTS on Atom Server"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by Beeeerock on 2013-01-02
I have been running 10.04 LTS in what was originally a Netbook Remix configuration.  Reason being, the box is a web and email server and is running an Atom processor.  Quiet, low power consumption and has enough performance for my needs.  Thus the desire for the simple and lightweight approach of NBR!

I'm seeing the notification that I should upgrade to 'precise', using 'do-release-upgrade'.  I understand 'precise' is the latest LTS release and my old LTS will soon lose support... so I need to act eventually.

Question is... should the automated upgrade work smoothly on my Atom box, given the way it was originally installed?  I've read about the desktop environment evolution through the releases converging to a unified desktop across the platforms, but I don't typically log into the GUI very often... so I'm most concerned with email and web services Just Working after the upgrade.  As far as I can recall, I've installed almost everything with apt-get...

Should this upgrade go smoothly, or are there any obvious things I should be concerned with?  I don't want to spend a pile of time fixing a whole list of things!

---

### Post by Beeeerock on 2013-01-03
About an hour after I submitted the original posting, this thread was started: [http://ubuntuforums.org/showthread.php?t=2093100](http://ubuntuforums.org/showthread.php?t=2093100)

It's relevant (back up of course...) but doesn't really address my specific issue.

Can anyone comment on whether the automatic upgrade offered at login is going to cause troubles with my configuration?  That is, having installed the Netbook version originally, will the upgrade recognize this given I'm now running it as a web/mail server?

I don't really want to rebuild Wordpress sites and a whack of email from my backup...

---

### Post by tgalati4 on 2013-01-03
Leave your setup as is for another year.  Is there really a reason that you need to upgrade?  Upgrading is usually needed when you need a framework (like Drupal or Wordpress) and you can only get the new features by upgrading.  You can almost guarantee that you will spend a lot of time fixing things and getting services back up and running with a new distro--auto-installed or fresh installed.  So you have to weigh the "agony-units".  How much time do you want to spend fixing things?  What new features do you need that necessitates the upgrade?

Security can be an issue in an enterprise/production environment, but for home use, you can probably go a year running your current setup without problems.

---

### Post by Beeeerock on 2013-01-03
My understanding is the desktop version is scheduled for end of life in April.  Server will be supported until April 2015.  Since I would think that the basic install I did would be considered 'desktop', I'm assuming security updates will stop in April.  And since this server is on the web and not a private intranet, not keeping it patched would be a Bad Thing.

I've been watching the log-in notice for a while now, not looking forward to the upgrade.  But it will have to be done before April if my logic is correct.  If it's going to be a tough upgrade, better that I do it on my own timeline than as an emergency when a future exploit messes it up even worse.

I'm really just looking for thoughts on whether the automatic upgrade should be painless... or not!

Thanks!

---

### Post by tgalati4 on 2013-01-03
The server support means that apache and the kernel will continue to get security patches.  Other packages will continue to get updates through the "backports" repository.  Usually these are popular packages that a lot of folks want patched.

I guarantee that the automated upgrade will be easy to do and it will ball up your system tighter than a rubber band ball.  It will be up to you unwrap it.  Try it and let us know what breaks.  You do get to keep both pieces.

---

