---
title: "How do I check if my system is compatible/ready for up gradation to 14.04?"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2014-10-02
I have been reading and hearing that people have faced numerous problems while upgrading and after when they have upgraded to 14.04.

To prevent any sort of problem, what steps/checks do I need to perform so that it gives me clear information whether I 
should upgrade to 14.04 or not and remain stick to 12.04.

Thanks.

---

### Post by Vladlenin5000 on 2014-10-02
12.04 is supported until 2017. Upgrading or not is entirely your decision. 
Always backup before attempting such upgrades. Often you should do a clean install instead of an online upgrade. The presence of proprietary drivers and/or third-party software installed via PPAs strongly recommends a clean install.

---

### Post by satyamM on 2014-10-02
[SIZE=2][COLOR=#000000]@Vladlenin5000

Thanks for your reply. Really appreciate it. :)

I wanted to know if there is specific way to know if my system is ready/compatible to get upgraded to 14.04.

Do you know any such way, such checks, such commands, through which it gives me some information which further helps in 
deciding whether I should go with the upgrade or not.

I have heard people have faced problems regarding drivers when they upgraded to 14.04.
[/COLOR][/SIZE]

---

### Post by Vladlenin5000 on 2014-10-02
If your looking for a tool that checks your system hardware and tells you whether or not upgrading is advisable like in Windows, you'll be disappointed.
As a general rule, if it works fine with 12.04 it should work with 14.04. Certainly there are exceptions and the rare cases of some drivers not behaving as good as before and other issues.
It all depends on specificity of your hardware and what proprietary driver are required (or recommended). Certain manufacturers did indeed drop support for some legacy chips in this 2 years interval. ATI/AMD comes to mind immediately. Other than that you should have no problems.
You can test a live session of 14.04.
And, of course, you can also post here the detailed specs. We'll see if something already known as problematic in 14.04 pops up from your list.

---

### Post by varunendra on 2014-10-02
Well.. I think the Live DVD/USB is not only for installation, it is the best and safest way to test hardware compatibility as well as getting an overall idea of how the OS will behave.

The live session requires a bit more memory than the installed session, but if memory is going to be a bottleneck for a live session, it is most certainly going to be a bottleneck for the installed version as well (when you actually start using heavy or multiple applications).

General recommendation for Ubuntu with Unity is : 2 GB or more for 14.04, 1 GB or more for 12.04.

So if you have less than 2 GB, go for Xubuntu or some other light weight variant. If you have 2GB or more, you should be able to test a live session without glitches. If it works in a live session, it'll work after installation too. Obviously, performance will be faster once the OS is installed and run from hard disk.

---

### Post by satyamM on 2014-10-02
Thanks for your replies. :)

As of now, I do not have a live cd of 14.04. I can download Ubuntu 14.04 from the site and then test using live usb.

I am attaching a picture of memory specs. Please have a look.


[ATTACH=CONFIG]256902[/ATTACH]

Thanks.

---

### Post by varunendra on 2014-10-02
Memory looks okay to me. Okay for Ubuntu 14.04, pretty good for Xubuntu 14.04.

Graphics is perhaps onboard one (embedded Intel 2000HD), should work out-of-box. The only thing 'Not Okay' is the available disk space, but I'm sure you are already aware of that and will be able to take care of it.

---

