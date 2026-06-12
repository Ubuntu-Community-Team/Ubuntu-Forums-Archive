---
title: "How to upgrade from 10.04 to 11.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Shellbak3 on 2012-04-30
I thought I had upgraded (this seldom used machine) from 10.04 to 11.10 to be in sync with a couple others.

How do I upgrade from 10.04 LTS to 11.04 LTS? The only instructions I see suggest using the upgrade manager but it wants to upgrade to 10.11 only.

---

### Post by sudodus on 2012-04-30
> **Shellbak3 said:**
> I thought I had upgraded (this seldom used machine) from 10.04 to 11.10 to be in sync with a couple others.

How do I upgrade from 10.04 LTS to 11.04 LTS? The only instructions I see suggest using the upgrade manager but it wants to upgrade to 10.11 only.
I would not recommend upgrading from 10.04 LTS to 11.04. Why? Because 10.04 end of life is April 2013, but 11.04 end of life is October 2012. And it would be a two step procedure, 10.04 --> 10.10 and 10.10 --> 11.04. And each upgrade to a new version is risky, it may imply a little or a lot of manual patching. Instead wait until July this year, when I expect we will be offered a direct upgrade from 10.04 LTS to 12.04 LTS, and it will probably be rather well debugged. At least my experience is good from upgrades between LTS versions.

But it will still be risky, so you should have good and recent backups of all your personal data. A complete backup of the whole hard drive would be the best.

By the way, many people prefer to make fresh installs and then add application programs when needed. The personal data can be copied back from an external drive.

---

### Post by Shellbak3 on 2012-05-02
Thanks, what I ***really*** want is to upgrade from 10.04 to 11.10 and thought that it might be accomplished in two steps: from 10.04 to 11.04 and then to 11.10.

I have three specialty machines using 11.10 and I wanted the old notebook to use the same version so that I could try to code and test some communications routines.  The other machines will run headless to control some specialized cameras on a completely local small intranet and probably will never be upgraded again.

---

### Post by sudodus on 2012-05-03
> **Shellbak3 said:**
> Thanks, what I ***really*** want is to upgrade from 10.04 to 11.10 and thought that it might be accomplished in two steps: from 10.04 to 11.04 and then to 11.10.

I have three specialty machines using 11.10 and I wanted the old notebook to use the same version so that I could try to code and test some communications routines.  The other machines will run headless to control some specialized cameras on a completely local small intranet and probably will never be upgraded again.
In that case I would recommend that you

- backup your personal files from the notebook.
- make a fresh install of 11.10 instead of upgrading in three steps.

That direct way is likely to save you a lot of time and problems compared to upgrading. But it is *possible* to upgrade

10.04-->10.10-->11.04-->11.10

so if you want to try and if you are prepared to do some manual repair job ... and if you have the time ... The advantage with upgrading is that you will learn a lot about your system.

---

### Post by Shellbak3 on 2012-09-15
I just received another of my machines that had 10.04 installed and it was trivial to upgrade to 11.10 (in two steps).

When I attempt to upgrade this one using update manager the upgrade loader runs for a few seconds and then gives the error: "Authentication Failed" and suggests a possible problem with the server or internet.

Does anyone know how to fix this?

Thanks

---

