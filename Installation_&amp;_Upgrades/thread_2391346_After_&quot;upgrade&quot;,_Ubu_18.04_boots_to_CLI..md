---
title: "After &quot;upgrade&quot;, Ubu 18.04 boots to CLI. How do I fix?"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2018-05-08
I'm not a happy camper right now.

I had a perfectly good working install of 17.10.1. I ran the Update Utility and it asked me if I wanted to Upgrade to 18.04 LTS. I said yes, but upon reboot, it leaves me with the CLI (previously, I did get some message about a missing "Pass-through cache" (IIRC?)

I tried running "repair" from the Grub menu but it didn't help. How do I fix this? :(

---

### Post by Mugsy323 on 2018-05-09
Follow-up.

I ran (re)install of 18.04 from a boot iso, which detected and "repaired" my installation, but it also created two problems:

1) No new programs will install, reporting "missing dependencies".

2) Repair changed my Boot Loader so turning on my computer now loads Ubuntu at boot instead of Windows by default as previously configured.

The release of 18.04 seems to be quite buggy and should probably be avoided. :(

---

### Post by QIII on 2018-05-09
Hello!

The sample size of your experiment is one.  That makes a conclusion about the performance of the release premature. 

Let's reserve judgement until help arrives and the nature of the failure you encountered has been determined.

---

### Post by tinylagarto on 2018-05-09
Let's hope somebody can help you with the upgrade. It can be very often tricky to upgrade to the next release under certain circumstances. 
You could just back up your files and do a clean install. 

Ubuntu 18.04 is quite stable, especially without older cruft.

---

### Post by Mugsy323 on 2018-05-09
Thanks for the replies, but I've never had difficulty upgrading before.

In fact, I upgraded to 17.10.1 just two weeks ago without a problem.

---

### Post by yancek on 2018-05-09
> I did get some message about a missing "Pass-through cache" 

The details of that message certainly would be useful?  I don't really think anyone is going to be able to help you with the little information you have provided and the best way to get details to post here is to run the boot repair (if you have it) from the Ubuntu iso you seem to indicate you have?  Download and run it from the link below.  Use the 2nd option using the ppa and when you run it select the option to Create BootInfo Summaryu and post a link to the output here.  Do not try to make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

