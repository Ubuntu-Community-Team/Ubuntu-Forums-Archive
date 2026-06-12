---
title: "No X after upgrading Feisty to Gutsy"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by murphyml on 2007-10-06
OK, I decided to upgrade my (Kubuntu) Feisty system to Gutsy last night (probably not a wise idea, but the upgrade procedure looked easy enough, and I wanted to see the new features).

Everything went OK, but when I rebooted my computer, I get a text login screen.  When I login, and try to startx, it fails.

I guess I should mention that I have a Radeon 9000.

After doing some reading, it seems that the Radeon 9000 (and indeed, most ATI cards) are having problems with Gutsy?

Can anyone confirm or deny this?  Because I'll wait until the official release comes out, and upgrade to that, if this will be fixed in the release (due this month sometime).

Or, did I just do something wrong?  I've tried numerous ATI fixes, patches, procedures, driver installs, etc, that I've looked for on the web, but nothing seems to work.  At best, I get an ATI driver installer to run, but it dies trying to build the kernel module, saying the files show a version of "" rather than "2.6.22-13_generic" (yeah, I've probably messed that kernel version up, but you get the idea).

I admit stupidity in this - I didn't make a backup, I didn't do my homework before I tried this, so I really expect no sympathy from anyone on this, because I should know better.

That being said, I'm hoping that someone who reads this will have any suggestions for me, other than the obvious "wait for the official release, and never install beta software on your live machine again without backing up and doing your homework."

Thanks.

---

### Post by taurus on 2007-10-06
After log in from a console, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Use **vesa** as the driver for your graphic card for now and once you get X up and running again, then install ATI driver for it.

Then, see if X works again with

```
startx
```

---

