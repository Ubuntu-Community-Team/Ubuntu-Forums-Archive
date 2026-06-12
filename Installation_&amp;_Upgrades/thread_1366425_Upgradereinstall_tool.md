---
title: "Upgrade/reinstall tool"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by grizdog on 2009-12-28
I'm only beginning to use *buntu, so  please excuse any Fedora-centric sounding questions.  Also, this is from the perspective of my personal machines, not network full of users.

When I upgrade to a new major release, I typically do a fresh install.  This means saving my personal stuff to someplace else, doing the install, and then cleaning out the new directory that was made for me in the install, filling it with all my old stuff, and then hoping I haven't introduced any incompatibilities.  Ostensibly, the release notes should help me out with that, but I still worry.  I've never had a real problem with this, but it always concerns me.

After  that the real fun begins, with the customiizations I use.  For example I use secure versions of dovecot and postfix.  I have to go in and rebuild these each time, with the fixes for ssl and tsl.  I have my personal and root certificates that go with those, and iptables set up the way I like it, and other things.

Of course, I keep a list of these things aand go through it each time, but it sort of seems like something the computer ought to do.  I was wondering if there was anything like the configure perl script we all use for installations, that I could run right before I upgrade.  It could do a chkocnfig, for example, and see dovecot and postfix turned on, and sendmail turned off.  And then it could go and gather all their configuration files in /etc or whereever and bundle them up for me, gather everything into a tarball with a more or less annotated list of things to do - in the "more" case, it would make an effort to see if my configuration files would still work with the latest version.

So my question is, is there a tool that does this or something like this, or something else that I am missing that will make these upgrades all quick and easy?

---

### Post by slakkie on 2009-12-28
Yes, it is called, apt/aptitude/update-manager. A reinstall is not an upgrade. You may have upped the version, but you still need to so all the icky bits of setting up your machine. Upgrading means that you get the new version without having to do all of the icky bits.

Here is the doc that should help you doing an upgrade: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

It will not touch /etc so you don't have to make any changes. Actually, it is a bit of a lie, but apt will warn you that it wants to override a particular config file and will ask you what to do. Keep your version, override your version, etc.

---

### Post by grizdog on 2009-12-28
Maybe I'm just too old.  I have used yum extensively (and of course, rpm with it), and apt less so, but I think I know how they work.

I thought that if you kept upgrading and never did a fresh install, you would eventually have trouble, something wouldn't line up properly.  I know I had trouble with that sort of thing in the old days, before Linux.

Are you saying that it's fine to just upgrade your way from Ubuntu 1 to Ubuntu 10, never doing a fresh install, and everything will work as well as if you did a fresh install?

Thanks.

---

### Post by slakkie on 2009-12-28
> **grizdog said:**
> Maybe I'm just too old.  I have used yum extensively (and of course, rpm with it), and apt less so, but I think I know how they work.


I dunno how old you are ;)

> 
Are you saying that it's fine to just upgrade your way from Ubuntu 1 to Ubuntu 10, never doing a fresh install, and everything will work as well as if you did a fresh install?


Yes. I've upgraded from 5.x to 6.x, upgraded all unsupported versions of Ubuntu to a supported versions (4.10 to 6.06/8.04, 7.04 to 8.04) and many more (8.04-10.04).

---

