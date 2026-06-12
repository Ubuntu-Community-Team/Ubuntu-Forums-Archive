---
title: "Is there any difference between the 3.13 Kernel and the 3.16 Kernel?"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2015-07-14
I did not install the HWE when Lubuntu upgraded to 14.04.2, mainly because if I did it would have erased half of the programs I have already installed and it appeared to me a number of important files were also going to be deleted. I also thought I might get a black screen, since there were reports of black screens after installing the HWE and given the number of programs and other important files that were going to be deleted if I did the upgrade.

So with 14.04.3 arriving in early August, is it OK to stick with the default Kernel? Is there a major difference between the 3.13 Kernel and the one included with the HWE? I have an old P4. Everything runs fine with the 3.13 Kernel. Am I missing any major improvements if I don't upgrade to the newer Kernel or install the HWE, including the new X-Org Server? In order to upgrade to the HWE Kernel and new X-Org Server, I am going to have to do a complete reinstall.

Thank you for any advice!

---

### Post by sudodus on 2015-07-14
There are security updates of the kernel series 3.13 (the trusty kernel). And there are updates for the application programs. The 3.13 kernel has LTS, while the 3.16 and 3.19 kernels have shorter support periods.

Stay with a kernel that works well for you :-)

---

### Post by ajgreeny on 2015-07-14
I have been using Xubuntu 14.04, installed as the first point version, not even 14.04.1 and as it runs like silk I have not updated the hardware stack either.  The 3.13 series will be supported until 2017, the point releases for a shorter period.

As sudodus says, if it ain't broke don't fix it; the only time that you might want or need to update the hardware stack is if you have newer hardware that is not supported by the 3.13 kernel series, in particular wireless or graphics performance.

---

### Post by grahammechanical on 2015-07-14
We can, of course, download Lubuntu 14.04.3 and install that over Lubuntu 14.04. But upgrading the hardware enablement stack does not require a fresh install. But there is something to keep in mind.

With a new hardware enablement stack (HWE) we get not only a newer Linux kernel and a newer X stack but also newer proprietary video drivers which may not have support for our video adapter. Support for older video cards is often dropped from newer proprietary video drivers. So, if you do upgrade the HWE swtich to using the open source video driver before hand and then install an appropriate proprietary video driver afterwards.

Regards.

---

### Post by v3.xx on 2015-07-14
Yes, the 3.13 kernel will give you 5 years of support (the life of your install) and the others will not.

This is something I do not fully understand since it was not intended to have long term support upstream (kernek.org).

---

### Post by deadflowr on 2015-07-14
> **v3.xx said:**
> Yes, the 3.13 kernel will give you 5 years of support (the life of your install) and the others will not.

This is something I do not fully understand since it was not intended to have long term support upstream (kernek.org).

That was determined by the Ubuntu kernel team.
There simply wasn't enough time to thoroughly test 3.14
Which would be an LTS kernel.

So short story long.
The onus to support and patch is completely upon the Ubuntu kernel team.

That being said, every new kernel gains some amount of improvement over the last.
Bugs do get quashed, even those that have existed for quite sometime.
So even though your hardware may be older than the new stuff currently being given kernel support, there is still a chance that some small fix may help your hardware perform better.

But that's a crapshoot.
And you would have to decide if the performance you currently get is worth upgrading to, as already pointed out to you, a kernel version which has a much shorter life span.

And of course, there is also a dark flipside where in a newer kernel may cause a serious, non-deliberate/unintentional, regression. 
That's rare, but seemingly possible.
Weirder things have happened.

---

### Post by roler2 on 2015-07-16
Thank you so much for all of the advice. I think I will stick with the default kernel. There still seems to be major Programs and files that will be removed if I do a manual install of the HWE. It looks as though I would have to reinstall the entire OS if I want to include the HWE. Everything is running fine with the default kernel. I may experience an increase in speed and other enhancements, however it just doesn't seem to be worth the effort to do a complete reinstall. I will do a complete reinstall to 16.04 next April anyway.

Thank you again!

---

### Post by sudodus on 2015-07-16
If you are happy with the replies, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

