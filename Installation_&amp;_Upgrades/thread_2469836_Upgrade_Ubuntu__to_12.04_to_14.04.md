---
title: "Upgrade Ubuntu  to 12.04 to 14.04"
date: 2021-12-11
forum: Installation &amp; Upgrades
---

### Post by ramj72 on 2021-12-11
Dear Professionals

I wish to upgrade my Server HP Proliant 350G5 from 12.04 LTS to 14.04 LTS. This server is compatible for this or not. Second thing if I upgrade  this our existing installed software will be available or not or these up-gradation  will make UN-install our software.
kindly let me know as I have to upgrade this as Anydesk and Teamviwer  is not working/  not install-able  on  our existing Ubuntu 12.04.

Thankin you

---

### Post by yancek on 2021-12-11
If this is a business or commercially used server, you need to keep closer watch on support time.  EOL (End Of Life) for 12.04 was over 4 years ago and 14.04 has not been supported for over 2 years.  A possible exception is if you have an extended security maintenance contract.  See the link below for possible options.

[https://itsfoss.com/ubuntu-14-04-end-of-life/](https://itsfoss.com/ubuntu-14-04-end-of-life/)

---

### Post by MAFoElffen on 2021-12-12
What edition of Ubuntu 12.04 are you running? You say your "Server" and that it is an HP Proliant 350 G5, but Teamviewer and Anydesk do not run on Server Edition. They are both remote Desktop Applications and require that you have a Desktop Edition installed. If it was running a Server Edition, you would be using SSH, and not asking about Teamviewer or Anydesk.

So that is why I am wondering if you actually have a Desktop Edition of Ubuntu installed on your HP branded Server Hardware... Is it's "job"... what it is being used for, as a server or as a desktop?

Ubuntu 14.04 came out 7 years ago... and (yes) it is also end-of-life many years long past. As a Desktop or as a Server, I can't see any use to upgrade to something that is still not supported. That is just common sense.

I would migrate to at least 20.04 LTS with plans update to 22.04 LTS when it comes out... The easiest would be to backup any data and configuration files, list any installed applications... Then installed 20.04 LTS as fresh, install the appropriate/same or comparable applications, update the configurations, then restore the data.

---

### Post by grahammechanical on 2021-12-12
An application that runs on 12.04 can only run on 14.04 or 20.04 if the developer of the application has upgraded the application to run on the newer versions of Ubuntu. You do not tell us what applications you are running or where you installed them from. We cannot assure you that the applications will run on newer versions of Ubuntu.

Regards

---

### Post by MAFoElffen on 2021-12-12
> **grahammechanical said:**
> An application that runs on 12.04 can only run on 14.04 or 20.04 if the developer of the application has upgraded the application to run on the newer versions of Ubuntu. You do not tell us what applications you are running or where you installed them from. We cannot assure you that the applications will run on newer versions of Ubuntu.

Regards
Very true. When I was trying to pickup and upgrade my Ama-Gi Project and update it from being based on Ubuntu 12.04 to 20.04, there where the default applications in the suite I had selected for it back then, that are no longer available through APT for 20.04. Some went way in time. Others were longer in the APT Package Management system, and only available through the Snap Store and/or Installed by compiling myself from source.

The good news is that, a lot of time has passed since then, and other applications, newer, with more features, now exist.

The two that you did mention, do exist, in better form and features than for 12.04 and 14.04... for 20.04 LTS.

---

### Post by ActionParsnip on 2021-12-13
Personally I'd setup a new server using 20.04 and run it side by side and set it up, then switch the IP across the new server and test. If all is well then decom the old box and be done

---

