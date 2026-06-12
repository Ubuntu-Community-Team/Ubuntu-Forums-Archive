---
title: "No notification for 16.04.01 LTS"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by Papiur on 2016-07-22
Hi,

I currently run Ubuntu desktop version 14.04 LTS, I've run Software Updater and I'm still not getting notification about 16.04 LTS being enabled. I've got setting to notify my about lts release but when I check available versions I'm getting nothing.

desktop:~$ grep Prompt /etc/update-manager/release-upgrades
Prompt=lts

desktop:~$ sudo do-release-upgrade -c 
Checking for a new Ubuntu release
No new release found

I'm based in Ireland, perhaps new version isn't available here yet? 

Regards

---

### Post by Nailhac on 2016-07-22
I too am having similar problems, I am in England and have assumed that the upgrade is not yet available in our location. Would be grateful if somebody could advise if this is the case.

---

### Post by PaulW2U on 2016-07-22
Take a look at the release notes - [https://lists.ubuntu.com/archives/ubuntu-announce/2016-July/000209.html](https://lists.ubuntu.com/archives/ubuntu-announce/2016-July/000209.html)
> Users of Ubuntu 14.04 will **soon** be offered an automatic upgrade to
16.04.1 via Update Manager.

I think that the word "soon", which I have made bold in the quote above, indicates that the upgrade notification has **not yet been enabled** by the Ubuntu developers.

**Edit:** I've just seen a comment on IRC that suggests the upgrade notification won't be enabled "till early next week".

---

### Post by Papiur on 2016-07-22
Thanks PaulW2U for explanation and update.
Waiting till next week then.

---

### Post by liam.gutierrez on 2016-07-23
Thank you for the heads up!

---

### Post by Nailhac on 2016-07-24
Thanks for info.

---

### Post by ks6124789 on 2016-07-25
i had to upgrade to 15.10 then checked for the updates from there and got it

---

### Post by alan-pd-watson on 2016-07-26
I still have no notification of the new point LTS. Am I the only one (i.e. I have a local issue) or is the lack of notification still the case?

Thanks!

---

### Post by grahammechanical on 2016-07-26
If we are already using 16.04 we will not get any notification of the first point release. The upgrade happens when we update as normal. This is because the kernels in 16.04.0 & 16.04.1 are supported for the full length of the 16.04 support period.

The kernels in the following point releases have a shorter support period and that is when users of 16.04 get notification of a new hardware enablement stack that they might wish to upgrade to.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

> graham@Ub1604:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


Regards

---

### Post by alan-pd-watson on 2016-07-26
Thanks grahammechanical for your reply - perhaps I shoudl have added that I am using 14.04 LTS.

---

### Post by Drew_Vogel on 2016-07-27
I'm still not seeing the upgrade offered when I do the following from my 14.04.4 LTS system...

[COLOR=#000000]desktop:~$ grep Prompt /etc/update-manager/release-upgrades[/COLOR]
[COLOR=#000000]Prompt=lts[/COLOR]

[COLOR=#000000]desktop:~$ sudo do-release-upgrade -c [/COLOR]
[COLOR=#000000]Checking for a new Ubuntu release[/COLOR]
[COLOR=#000000]No new release found[/COLOR]

---

### Post by howefield on 2016-07-27
Be patient, it will come through.

Note : it isn't your installation that isn't behaving properly, it is that the upgrade notifications have not been made live yet. Nothing you can do bar wait.

---

### Post by alan-pd-watson on 2016-07-27
so I guess I'm not the only one who is still waiting ........

---

### Post by PaulW2U on 2016-07-27
Definitely not. And the Release Team are more than aware that the upgrade notification needs to be enabled. :)

---

### Post by Fambank on 2016-07-28
No, you are not the only one. Same here mate ;)

July 29th : The wait is over. xD Upgrading as we speak.

---

