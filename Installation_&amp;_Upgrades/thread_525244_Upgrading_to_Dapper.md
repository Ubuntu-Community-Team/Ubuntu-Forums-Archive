---
title: "Upgrading to Dapper"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by wessel_k on 2007-08-14
Hi,

I would like to upgrade to Dapper. But I manually installed some applications on Breezy, and I just don't have a clue what happens to them when I upgrade. 
Do I have to recompile them? Or can I just upgrade and will they work?
I know the applications I configured manually in Breezy are available within the repository for Dapper. In the past I've chosen to install newer versions of the ones available in the repository, so that's the reason they are manually configured. I needed the functionality of the new versions.
I'm not brave enough yet to discard them. :) I need to take some more time to do this. But an upgrade shouldn't take to much time. At least that's my experience with the Feisty machine, which I upgraded from Breezy to Dapper to Feisty.
Hope somebody can help me out with this question.

Regards,

Wessel

---

### Post by jim_p on 2007-08-14
What are the applications you wish to install?
If you compiled them from source while using Breezy, they are most likely to be located in dappe's repositories now.
If non, you can always use [www.getdeb.org](www.getdeb.org) to find what you are missing.

---

### Post by wessel_k on 2007-09-29
Sorry for not answering the reply. I must have been unsubscribed from the thread. 
I know for sure that the installed apps are in the newer ubuntu versions. ;-)

But I'm a little afraid that my settings will be lost. I'm planning on moving to the apps from the repository, but not yet know. I don't have the time at the moment. But I've bought a new printer and the driver is not supported in Breezy.

So I was wondering what happens to the applications that I manually installed. Can I just upgrade and will they still work?

Regards.

Wessel

---

### Post by tgalati4 on 2007-09-29
Provide a list of these applications and folks can weigh in on what needs to be done.

My guess is that Breezy is so old that there must be newer versions of these applications in the repositories.  If not, it's not difficult to recompile them from scratch under Dapper.

---

### Post by wessel_k on 2007-09-29
OK, so I won't loose settings, when recompiling or using the application from the repositories when available?

Because I already know that the versions of the applications I'm using are already available within Dapper or Feisty.

---

### Post by tgalati4 on 2007-09-29
Yes, you may lose some settings.  You can make a backup of /home/you and /etc and that will capture 90% of the settings.  You will have to check each application, because many times the preference files change names and locations and content.  So your backup is simply a guide to how you had your applications set up.  You shouldn't simply copy over your old settings because you will likely break something.

I've been running Dapper on a few machines since June 06 (6.06) and I'm impressed with it's stability.  I used Automatix and Automatix2 to load missing stuff, but now most things are in the repositories (you have to select these repositories manually in Synaptic) or there are decent guides for compiling from scratch.

---

### Post by wessel_k on 2007-09-30
Yeah, I'm also pretty impressed with the whole ubuntu family. :)

I've managed to upgrade using the following steps.:

1. I've upgraded the sources.list to the dapper repositories
2. I've manually upgraded/installed all the applications. I did this to make sure that it didn't do anything I didn't want him to do.
3. I finally did a dist-upgrade to make sure that everything was alright
4. rebooted
5. Everything came up like clockwork.

Only one issue with postfix. I had to replace localhost with 127.0.0.1 to make it work again.

I the process I removed xserver and that saves me around 200 MB in memory usage.

So even if you've compiled applications manually an upgrade won't cause them to go corrupt. Please not that it's possible that some settings won't work anymore since another applications coming from the repositories could be upgraded to a new version causing issues.

Regards,

Wessel

---

