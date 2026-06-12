---
title: "What do the daily apt and aptitude scripts actually do?"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by leblanc_kevin on 2007-03-26
Hello!

I've recently installed Kubuntu 6.10 (after years of using RedHat/Fedora), and I am trying to configure a number of things.  One thing I'd like to set up is automatic downloading of upgradeable packages.

My first instinct was to just add a cron script using apt-get (or aptitude, or dselect, or...).  But I noticed  that in the default installation, there are already two scripts running daily, which deal with package maintenance.  They are "/etc/cron.daily/apt" and "/etc/cron.daily/aptitude".

As far as I can tell, the "/etc/cron.daily/aptitude" script just rotates some log files(?).  The "/etc/cron.daily/apt" script aparently uses apt-get to perform some maintenance tasks regarding the installed packages.  It looks like it can delete old packages based on some age and size parameters, download upgradeable packages, etc.  In other words, it should be able to do what I want to do.  I think the configuration files in "/etc/apt/apt.conf.d/" can be used to set some of the parameters of the maintenance.  In particular, "15adept-periodic-update" seems to have an entry to allow the automatic downloads I'm looking for...

My questions can be grouped as follows:

1. What is the "/etc/cron.daily/aptitude" script supposed to do, and how important is this?  Does this have anything to do with the "aptitude" front-end which can be used to upgrade packages?  Is there some easy way to check if this script is doing what it's supposed to do?

2. Am I correct in assuming that the files in "/etc/apt/apt.conf.d/" are the ones I should use to configure the "/etc/cron.daily/apt" script?  And in particular, why are these settings put in this strange place with such strange names?  In the man page for apt-get this directory is said to be for "APT configuration file fragments", and there is a reference to an "/etc/apt/apt.conf" file which doesn't exist (from what I gather this file existed in some previous releases).  Is it just me, or wouldn't this whole thing be a lot more user-friendly if the seven options used by the "/etc/cron.daily/apt" script were just put (back?) into the "/etc/apt/apt.conf" script, in some standard configuration file format?  At the very least some information about how to configure the "/etc/cron.daily/apt" script should be easier to find.  For example, I'm wondering about the intended use of the files in "/etc/apt/apt.conf.d/".  Can I just add an entry for "APT::Archives::MaxAge" in the "15adept-periodic-update" file, or is this supposed to be set somewhere else?  Basically the whole thing looks quite messy, and there is little help to be found about how to tweak these things.  I think most users would just add a new cron script to download updates automatically, rather than try to figure out what the default scripts are doing - which means that something isn't right.

3. Why are there two scripts, using both apt and aptitude related things?  Couldn't one script be used for all the package maintenance tasks?  I've read that aptitude is better than apt-get, since it tracks dependencies better ([http://www.psychocats.net/ubuntu/aptitude)](http://www.psychocats.net/ubuntu/aptitude)).  Both programs take essentially the same arguments.  If I decide that aptitude is better for me, can I just replace apt-get with aptitude in the apt script?  Does anyone know if the other front-ends (e.g. adept_manager) have the same limitations as apt-get?

4. What does the apt-index-watch process do?  The man page says that it "rebuilds the apt-front indexes", but I don't know what that means.

I know these might seem like small things, but I like to know what's happening on my system!

Thanks for any help you can provide!

---

