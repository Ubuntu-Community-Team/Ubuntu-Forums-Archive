---
title: "Ubuntu Precise Pangolin - support ending...?"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by zuto2 on 2016-01-24
Hello,

I have been using Ubuntu Precise Pangolin for a long time. How insecure will it be after support has ended? I've always found Precise to be lighter and not as laggy as later Ubuntu Distros versions. I tried 14 once 2 years ago, but the archive manager just didn't really work well and it was a bit laggy. Although, I never tried cinnamon environment on later versions....could it possible function better?

I don't really have a reason to upgrade besides security reasons and not wanting to install all my programs again. I have many back ups of my entire OS with everything on it. Even if all the repos die.....I can instantly restore everything within 30 minutes. I have done this many times.

What version would you recommend me switching to?

Sincerely,

Zuto

---

### Post by ajgreeny on 2016-01-24
What hardware do you have which finds 14.04 laggy?

If your hardware is of low spec you may find another DE (such as the cinnamon you suggested) is quicker, though I am not sure what spec cinnamon needs; I prefer XFCE found in Xubuntu.

---

### Post by grahammechanical on 2016-01-24
What kind of support do you think is ending?

If you are running 12.04 or 12.04.1 or 12.04.5 then Canonical will continue to provide security updates to the Linux kernel until the end of April 2017.

[URL="https://wiki.ubuntu.com/Releases"]https://wiki.ubuntu.com/Releases

[/URL]If you are running 12.04.2 or 12.04.3 or 12.04.4, then you should  consider upgrading to the 12.04.5 hardware enablement stack in order to  get continued support for security fixes. Or upgrade to Ubuntu 14.04.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

What output does this command give?

```
lsb_release -a
```

It will tell you what version of Ubuntu you are running as seen by the output on my machine.

> graham@sdb7-Dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial

If you are referring to a recent announcement by Google, then it is not Ubuntu 12.04 that is not longer receiving support but all 32 bit Linux versions of Google Chrome and, as I understand it, 64 bit versions of Google Chrome running on Ubuntu 12.04.

Support for the Ubuntu Linux distribution is provided by Canonical & not Google. The announcement by Google only affects Ubuntu users if they are running a 32 bit version of Ubuntu & have installed Chrome or are running a 64 bit version of Ubuntu 12.04 & have installed Chrome.

[http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

Regards.

---

### Post by zuto2 on 2016-01-24
I guess I have until 2017.

> No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04.5 LTS
Release: 12.04
Codename: precise


I'll switch to the next LTS Ubuntu once security support ends, but will always keep my Ubuntu Precise back ups.

Thanks everyone! :D

---

