---
title: "How often should I install updates?"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2014-08-16
Looking for advice on how often I should install updates.  

Recently did a fresh install of 14.04 LTS plus a few apps (VMWare Reader, VLC, Chrome).  It seems like every 2-3 days the Software Updater appears wanting to install 100MB of updates (seems like a lot).  Having recently migrated from Windows where the conventional wisdom is to always install all updates, I'm wondering whether the same true in Ubuntu?

P.S. the last two times I installed updates, VMWare had to re-compile and link some modules with the kernel before launching.  Don't know if this is normal behavior or not.

---

### Post by JetStorm on 2014-08-16
As often as they appear. The cool thing about Linux is you don't need to reboot your machine after an update, unless a new kernel is available.
Of course sometimes things get broken after updates but that's the price of always having the latest software. 
If you're searching for something with less updates take a look at Debian (it's what Ubuntu is based on). Most of your apps will be a few versions behind the latest one but at least the system is a bit more stable.

---

### Post by ian-weisser on 2014-08-16
> **ken18 said:**
> the conventional wisdom is to always install all updates, I'm wondering whether the same true in Ubuntu?

Yes, if you installed the software from the normal Ubuntu repositories. 
The frequent updates are security patches and important bugfixes.
Sometimes a single patch or fix requires updating several packages. That's why some days seem to have a theme.

> **ken18 said:**
> the last two times I installed updates, VMWare had to re-compile and link some modules with the kernel before launching.  Don't know if this is normal behavior or not.

Yes, it is normal behavior for kernel updates.

---

### Post by Bashing-om on 2014-08-16
ken18; Hi !

My slightly different take on updating . I do not run any GUI package management applications and I do value a fully updated ( you may read that also as patched !) system, I have the habit of each and every time I start up my system, the very 1st thing I do is check for updates (terminally). Be advised I have been running 'buntu for several years and have never encountered a problem accepting the updates, paying attention to what is offered, and aware of what might break - because of non-standard software installed -.
A high degree of faith and trust in the package management system. These people are not known as "Masters Of The Universe" for nothing ! All their work is for a purpose.

[INDENT][INDENT]I do the updates
[INDENT][INDENT][INDENT][INDENT]and keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2014-08-16
Not sure what the problem is, the more the merrier. :) I like my system fully up to date.

If you are worrying about space run these once in a while

```
sudo apt-get autoclean
sudo apt-get autoremove
```

Or you can use bleachbit to do it (don't check the experimental features and deep scan) Removing the unused localizations alone would free up a lot space.

Edited: The only thing is don't accept 'partial upgrade' from the update-manager. That may break your system. It  doesn't happen often but it may happen if you use ppas and not all required packages are uploaded to the server. Personally i do update manually.

---

### Post by grahammechanical on 2014-08-16
In Ubuntu we can set the Update Manager to check for updates daily, every two days, weekly or every fortnight. There is even a setting for never. The longer we put off updating the larger the download will be.

Regards.

---

