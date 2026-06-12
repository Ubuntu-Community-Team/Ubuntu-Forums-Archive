---
title: "LTS --&gt; LTS Easy Upgrade?"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by PeregrinGo on 2010-02-25
Does anyone know if users of LTS 8.04 (aka Ubuntu Hardy) will be able to upgrade directly to LTS 10.4 when it is Launched?

Also, out of curiosity, can you think of any convincing arguments for Hardy users like myself to upgrade each time a short-term variant of Ubuntu is released? Do you find that breaks are commonplace?

My thinking is, once you get the system customized and working just like you want it, is there any real reason or advantage to upgrading before the next LTS comes along? What do you think?

---

### Post by wub on 2010-02-25
I'm trying to figure out who LTS is meant for.  

I had hoped to find a simple upgrade path, too, but looking in the documentation makes it clear that only upgrades to the very next version are supported, and one of the examples given is 8.04LTS to 8.10.  Since no one else has answered you in the last 16 hours (42 page views, though) I feel convinced this must be so.

My guess is LTS is for people who don't want to actively manage their system, and are comfortable as the newer versions pass them by.  I did not realize this when I chose 8.04LTS as my desktop.  Now, I have Firefox 3.0.x, and OpenOffice 2.0.x while my kids running 9.04 have 3.5 and 3.1 respectively.  That isn't causing me any problems, but it does leave me wondering what I'm missing.

I know I cannot upgrade, because I have installed software from scratch when I couldn't get it from the repositories, or when the repository version was not what I needed (sometimes I need older versions, sometimes newer).  So, the apt/synaptic database in my system does NOT know what's really installed, and there will be dependency problems, without a doubt.  Fortunately, I have saved all the tarballs for software I added, so although it will take some time, I will be able to bring my new install to my required state.

I'm going to put in a new hard drive to do this, and use the existing one as a guide to ensure I get everything installed and configured correctly.

What I'd really like to find out, is how to use the apt database I have in my system now as a starting point for customizing my new install using the list of packages that I DID pull from the repositories.  Wouldn't it be nice to say "Load my new system with the current version of all the packages I was using in my old system"?  I will get there eventually, by scanning the package list, clicking and repeating until I get it all.  Not a problem, but it does seem pretty inefficient.

And I guess I'll be doing this every six months now, since I no longer feel that LTS makes sense for me.

---

### Post by snowpine on 2010-02-25
> **PeregrinGo said:**
> Does anyone know if users of LTS 8.04 (aka Ubuntu Hardy) will be able to upgrade directly to LTS 10.4 when it is Launched?

Also, out of curiosity, can you think of any convincing arguments for Hardy users like myself to upgrade each time a short-term variant of Ubuntu is released? Do you find that breaks are commonplace?

My thinking is, once you get the system customized and working just like you want it, is there any real reason or advantage to upgrading before the next LTS comes along? What do you think?

Yes, of course you will be able to easily upgrade directly from 8.04 to 10.04 when it is released in April. :) 

Whether or not to stick with the LTS releases really depends on whether or not you like using new versions of applications. Upgrading every 6 months will give you the latest applications. If you are comfortable using slightly outdated (but well tested and stable) applications, or if you're running a server or business, then LTS may be perfect for you.

---

### Post by texaswriter on 2010-02-25
LTS = long term support. 
I second that you will be able to upgrade directly to 10.04.. From what I understand, this has always been the case and is definitely INTENDED. 

If you are like me, cautious, I will be delving into 10.04 a bit more cautiously... wait for some of the major bugs to surface... :p

---

### Post by speedygeo on 2010-02-26
There is a problem when use a LTS. Many key applications can be so outdated you risk for your security. I think about firefox. The 3.0 is no more supported by mozilla for security updates. Do you know if Canonical or Ubuntu Foundation fix it even until the next LTS?

---

### Post by pbpersson on 2010-02-26
I used to be running 8.04.  Everyone else was talking about the new 8.10 version but mine never told me.....because in every LTS machine in the upgrade manager you can select "only tell me about LTS upgrades".

Therefore, when the new LTS comes out, all the people still on Hardy Heron who have that setting enabled will see the red carpet rolled out for them so they can upgrade to the new LTS version.

I once thought of being an LTS person but as it is turning out I tend to hop on each new version three months after it is released - after trying it on a couple of test machines first.  ;)

---

### Post by snowpine on 2010-02-26
> **speedygeo said:**
> There is a problem when use a LTS. Many key applications can be so outdated you risk for your security. I think about firefox. The 3.0 is no more supported by mozilla for security updates. Do you know if Canonical or Ubuntu Foundation fix it even until the next LTS?

If there is a security flaw in Firefox 3.0, Canonical will "backport" the security patch. They are fully committed to keeping 8.04 secure for the duration. I personally use FF3.0 every day with zero problems.

---

### Post by PeregrinGo on 2010-02-26
> **speedygeo said:**
> There is a problem when use a LTS. Many key applications can be so outdated you risk for your security. I think about firefox. The 3.0 is no more supported by mozilla for security updates. Do you know if Canonical or Ubuntu Foundation fix it even until the next LTS?

I'm confused by these recurring statements that running an LTS means your software is outdated. My software gets updated QUITE FREQUENTLY, and I am currently running Firefox 3.5.3. My other programs are, for the most part, also as current as they are with my seldom-used Windows partition and my Windoze XP machine at work.

---

### Post by kostkon on 2010-02-26
> **speedygeo said:**
> There is a problem when use a LTS. Many key applications can be so outdated you risk for your security. I think about firefox. The 3.0 is no more supported by mozilla for security updates. Do you know if Canonical or Ubuntu Foundation fix it even until the next LTS?
LTS versions are supported with security updates (Firefox included. I'm still getting security updates for Firefox from Canonical) and with the use of PPAs, nowadays you can keep your system fairly up-to-date relatively easily and safely.

---

### Post by Devlin67 on 2010-02-27
I've maintain 8.04LTS on a company laptop since it's launch and have added a few PPA for firefox, openoffice and AWN without any problem whatsoever.
Very stable.

---

### Post by mick222 on 2010-02-27
I was actually thinking the same thing myself a few days ago. Probably the easiest way to upgrade is to back up your home folder maybe include the tarballs or links to the downloads reinstall lucid or whatever with a seperate home directory then add the backed up files. Better to do a new install for things like ext4 file system and grub2.

---

### Post by speedygeo on 2010-02-27
I'm looking for a LTS-like distro that have all  the fixes and upgrades needed for the common users to recommend it.
I'm waiting for Lucid that I have downloaded today.
If you say I can have all the needed fixes for the older firefox even if Mozilla doesn't support it anymore, than it's a good news for me. :p

---

### Post by raymondh on 2010-02-27
> **mick222 said:**
> ... back up your home folder maybe include the tarballs or links to the downloads reinstall lucid or whatever with a seperate home directory then add the backed up files......

Sorry to go off-topic, and for those considering ....

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Getting back on thread .... I am looking forward to Lucid, but as a habit, always do a fresh install :)

Raymond

---

### Post by PeregrinGo on 2010-02-27
> **raymondh said:**
> Sorry to go off-topic, and for those considering ....

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Getting back on thread .... I am looking forward to Lucid, but as a habit, always do a fresh install :)

Raymond


This is GREAT to know. Thanks!

On an unrelated note, let me say how interesting it was to see the quote in your signature attributed to Benjamin Franklin: Just two days ago I received an announcement from a book publisher trying to promote its latest textbook, and they had used the same words, but they were attributed to -- ready? -- Confucius. Funny how that happens.

---

### Post by raymondh on 2010-02-27
> **PeregrinGo said:**
> ...... Just two days ago I received an announcement from a book publisher trying to promote its latest textbook, and they had used the same words, but they were attributed to -- ready? -- Confucius. Funny how that happens.

That is indeed funny.

Raymond

---

