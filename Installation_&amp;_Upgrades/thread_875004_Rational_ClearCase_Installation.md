---
title: "Rational ClearCase Installation"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by blustarz on 2008-07-30
Hi,

Does anyone have installation instructions for Rational's ClearCase tool on "hardy"?

---

### Post by kwits on 2008-10-13
Good Day,

  I can help you with the installation instructions but do you know that IBM does not presently support ClearCase under the Ubuntu OS distribution? Have you discovered a workaround this non-support statement? My scenario is for testing and prototyping, not for production.  

Regards,
Keith

---

### Post by SixedUp on 2008-12-15
Kwits, I'd be interested in hearing how to get Rational ClearCase running under Ubuntu - even if its not a supported configuration. Pointer to a how-to, or posting one here would be really appreciated. Thanks

---

### Post by DarkoBeatsDeath on 2008-12-21
I would like that as well.

Thanks.

---

### Post by SixedUp on 2008-12-22
Turns out that it seems to "just work", though undoubtedly it won't be supported by IBM (they only ever seem to support RHEL and SUSE).  

I simply ran the ClearCase Remote Client for Linux installer (provided by our clearcase admin guys). It doesn't create any menu items, but seems to install just fine. You can then easily create a launcher for "/opt/IBM/Rational/ClearCase701/clearcaserc", and then it's simply a matter of starting it up, letting it install any updates (which works just fine) and entering your clearcase configuration info into the resulting GUI panels.

I'm on Ubuntu 8.10, and installed ClearCase 7.0.1, for what it's worth. Hope that helps.

---

### Post by DarkoBeatsDeath on 2008-12-25
well, Clearcase remote client (CCRC) is not exactly clearcase.
been there, done that ;-)
i'm more interested in a traditional clearcase installation
with dynamic+snapshot views, mvfs and cli.

if anyone managed to do it, i'll be more then happy to know how.

10x.

---

### Post by SixedUp on 2008-12-26
Ahhh, I see what you mean. Since I'm a fairly low-needs user CCRC provides me with all that I need, and seems to run just fine under Ubuntu.  But I think if I were going to go much beyond this (say as a professional user) then I'd want the confidence of official support; and that has to mean running under a supported client - so RHEL or SUSE, or in practice, Windows.

---

### Post by sirius42 on 2010-05-02
> **SixedUp said:**
> Ahhh, I see what you mean. Since I'm a fairly low-needs user CCRC provides me with all that I need, and seems to run just fine under Ubuntu.  But I think if I were going to go much beyond this (say as a professional user) then I'd want the confidence of official support; and that has to mean running under a supported client - so RHEL or SUSE, or in practice, Windows.

For Ubuntu you have to MVFS module for working with native ClearCase client. I have found information about porting ClearCase 7.1 MVFS to Ubuntu server 9.04

I have tried and have good result - I have native ClearCase client for working with dynamic views on Ubunutu.

---

### Post by nocnokneo on 2011-03-01
> **sirius42 said:**
> For Ubuntu you have to MVFS module for working with native ClearCase client. I have found information about porting ClearCase 7.1 MVFS to Ubuntu server 9.04

I have tried and have good result - I have native ClearCase client for working with dynamic views on Ubunutu.

Can I ask how you did this? I have been able to get rid of several compilations errors that I'm getting on Ubuntu 10.10 with kernel version 2.6.35-27-generic, but this one seems to be a show-stopper:

```
/usr/src/mvfs-7.1/mvfs_src/mvfs_linux_mvops.c:1478: error: implicit declaration of function ‘get_empty_filp'
```

Due to this kernel change:

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.33.y.git;a=commitdiff;h=e81e3f4dca6c54116a24aec217d2c15c6f58ada5](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.33.y.git;a=commitdiff;h=e81e3f4dca6c54116a24aec217d2c15c6f58ada5)

Any help would be appreciated. Thanks!

---

### Post by whiteo on 2011-03-07
I struggled to get the MVFS module to compile under Ubuntu 10.10, and eventually gave up and re-installed Ubuntu 10.04 LTS.  This works fine!  The LTS version is more likely to get official support anyway (we live in hope), although IBM currently officially support only 8.04 LTS.  Make sure you have updated ClearCase to 7.1.2.01 to get the latest MVFS code.

The kernel change that caused the major issue you identified was introduced in 2.6.33, and looks like it will need more than a little hacking of the MVFS code to fix up.

Under Ubuntu 10.04 all you have to do is install the pre-requisites as per [https://www-304.ibm.com/support/docview.wss?uid=swg21443159](https://www-304.ibm.com/support/docview.wss?uid=swg21443159) (note you will have to find a version of libstdc++5 as it is missing from Ubuntu 10.04) and manually create your mvfs_param.mk.config

One thing to be aware of is the xclearcase tool will crash with a Segmentation Fault when viewing a graphical version tree unless the LANG environment variable is set to C

---

### Post by nocnokneo on 2011-03-07
Thanks for the reply. I guess I'll just stick with snapshot views for now and hope for an updated ClearCase client with support for Kernels newer than 2.6.33 in the not-to-distant future.

---

### Post by lone.ranger on 2011-08-19
When i run this from the install directory:
$ ./install_client.sh

It gives me the error:
ERROR:   Unsupported OS Distribution.
Aborting install

Trying to install Clearcase client 7.0.1.7 on Ubuntu 10.04 to be able to see dynamic views and snapshots.

I know this version is not supported on this platform but some people seems to have done it.

Any links or howtos or advice?

---

