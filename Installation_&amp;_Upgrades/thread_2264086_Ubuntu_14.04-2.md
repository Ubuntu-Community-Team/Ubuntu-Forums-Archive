---
title: "Ubuntu 14.04-2"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by The-Valk on 2015-02-05
I read that Trusty 14.04-2 was due to be released today (5-2-15).
Will 14.04-1 installations automatically update?
I really need this new release to fix a driver problem I am living with.

---

### Post by nerdtron on 2015-02-05
Unless you have chosen to install automatic updates, your system won't update by itself.A
Also, if it's a driver problem, you probably need the new kernel update. Be sure that when you update, the kernel is also updated.

To check your current kernel, run:
```
uname -r
```

After the update and reboot, run the command again to see if you have the updated kernel.

---

### Post by The-Valk on 2015-02-05
> **nerdtron said:**
> Unless you have chosen to install automatic updates, your system won't update by itself.A
Also, if it's a driver problem, you probably need the new kernel update. Be sure that when you update, the kernel is also updated.
After the update and reboot, run the command again to see if you have the updated kernel.

Yes, I do get the usual updates offered to me daily which I install.  I am currently on kernel 3.13.0-45.
Will the new kernel 3.14 be offered in the same manner as the updates already received and installed for 3.13 or do I need to specifically ask for the new kernel?

---

### Post by craig10x on 2015-02-05
Just to clarify for you, the updated kernel for 14.04.2 would be the one that is in Utopic (14.10) which is the 3.16 kernel...
Someone else will need to answer your question about getting the kernel update...

---

### Post by deadflowr on 2015-02-05
> **The-Valk said:**
> I read that Trusty 14.04-2 was due to be released today (5-2-15).
**Will 14.04-1 installations automatically update?**
I really need this new release to fix a driver problem I am living with.

If you mean, will the 14.04.1 installs automatically update to the new 14.04.2 kernel and hardware stack, then no.
To get the new stacks you need to either manually add the packages, or simply do a fresh install of a fresh copy of Ubuntu.
General guidelines here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Generally though, I pay attention to the [fridge discussions]("http://ubuntuforums.org/forumdisplay.php?f=122") or [Announcements]("http://ubuntuforums.org/forumdisplay.php?f=13") about any news on when the release is made officially public.
(Keeps me from jumping around anxiously)

---

### Post by Elfy on 2015-02-05
just fyi - it's unlikely that you'll be seeing this point release today

---

### Post by Min_Jia on 2015-02-05
> **Elfy said:**
> just fyi - it's unlikely that you'll be seeing this point release today

could you please let us know why?

I read from the link below, 14.04.2 is due to release today:

[https://wiki.ubuntu.com/DraftReleaseSchedule](https://wiki.ubuntu.com/DraftReleaseSchedule)

---

### Post by Elfy on 2015-02-05
There have been some issues with it. I know that I've marked all the Xubuntu tests as critical fails, Lubuntu have issues as well. As far as I know the ubuntu release team are looking to delay till next week. 

That though is subject to change.

---

### Post by Min_Jia on 2015-02-05
Thanks for the info Elfy. I was planning on installing the new 14.04.2 today but it appears I'll have to wait. Thanks for your insight info.

---

### Post by Elfy on 2015-02-05
> **Min_Jia said:**
> Thanks for the info Elfy. I was planning on installing the new 14.04.2 today but it appears I'll have to wait. Thanks for your insight info.

It's a point release. 

Unless you've got reason to not want the accumulated updates, bandwidth maybe, just install 14.04.1

---

### Post by Min_Jia on 2015-02-05
> **Elfy said:**
> It's a point release. 

Unless you've got reason to not want the accumulated updates, bandwidth maybe, just install 14.04.1


I thought the new kernel might provide better performance hence the plan to go for 14.04.2. I currently have 14.04.1 installed it it's actually working fine. So maybe I'll just stick with the current version.
I upgraded to 14.10 back in October last year, however there were many glitches with many software, even ones in depository, so I went back to 14.04.1 which has been solid.

---

### Post by craig10x on 2015-02-05
You know what you could do, just install the 14.04.2 hardware enablement stack which should be available after 14.04.2 officially releases (to get the 3.16 kernel)...that would be the only difference between your 14.04.1 and 14.04.2 because everything else that the new point release has, you would have gotten automatically in the updates...it's just one simple command in the terminal...then you re-boot and you would have it...

---

### Post by Elfy on 2015-02-06
fyi 

> we've opted to delay the release until Feb 19,

[https://lists.ubuntu.com/archives/ubuntu-release/2015-February/003208.html](https://lists.ubuntu.com/archives/ubuntu-release/2015-February/003208.html)

---

### Post by OrangeCrate on 2015-02-06
^, Thanks Elfy.

---

### Post by The-Valk on 2015-02-06
> **craig10x said:**
> You know what you could do, just install the 14.04.2 hardware enablement stack which should be available after 14.04.2 officially releases (to get the 3.16 kernel)...that would be the only difference between your 14.04.1 and 14.04.2 because everything else that the new point release has, you would have gotten automatically in the updates...it's just one simple command in the terminal...then you re-boot and you would have it...

Thanks to all for the information.   I am quite happy with 14.04.1 in all regards but one.  My network connection is via a Qualcomm Atheros QCA8172 chip and the driver in kernel 3.13 apparently doesn't support reporting network traffic.
I miss this facility but not enough to reinstall the OS and spend hours getting it just the way I like it which is why I always go with Ubuntu LTS.
I may just buy a plug in network card with a different but fully supported chipset.

(Just edited it to say that I'm totally flumoxed by the term 'hardware enablement stack' so maybe I shouldn't go there?).

---

### Post by newuser7 on 2015-02-06
Can we install the latest daily build of 14.04.1 (03/02) which comes with kernel 3.16.0-30 ?

[http://cdimage.ubuntu.com/trusty/daily-live/20150203.2/](http://cdimage.ubuntu.com/trusty/daily-live/20150203.2/)

---

### Post by Elfy on 2015-02-06
Closing this. It's not a catch all thread.

If people need help with 14.04 I suggest they start their own threads.

Thanks.

---

