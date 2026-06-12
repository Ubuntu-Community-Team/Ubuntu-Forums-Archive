---
title: "Trouble Upgrading!"
date: 2015-09-28
forum: Installation &amp; Upgrades
---

### Post by john464 on 2015-09-28
Hello!

I am currently using an Asus Vivobook S550CA with Ubuntu 14.04 and I have been trying to upgrade to 15.04. I have been using Ubuntu since 10.04, so I know my way around the OS, at least on a general level. I've done everything I could think of, ranging from attempting to use command line to upgrade, using the upgrade manager core, all the way to trying to find any broken packages that may be preventing the upgrade and removing them, to changing my upgrade search from ltsd to normal. I get the notification that there is an upgrade available, and I follow the steps, but it always ends up with this error message:

[IMG]http://i.imgur.com/SVNE6rp.png[/IMG]

I've tried everything that related searches have to offer. What do you professionals have to offer?

---

### Post by sudodus on 2015-09-28
Welcome to the Ubuntu Forums :-)

We are not professionals. We are users with more or less experience, that help each other. Even the moderators and administrators are volunteers.

Please describe the GUI tools you have tried and the command lines that you have used.

Did you start by updating/upgrading your 14.04 LTS system before trying to upgrade to the next version?

Maybe the problem is that you should upgrade step-wise, 14.04 --> 14.10 --> 15.04, but 14.10 has passed end of life and is no longer supported. It might be possible to upgrade via it, but it is probably rather difficult. Instead I suggest that you

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

and then make a fresh installation the new version if you like it. Beware, the lifetime of 15.04 is short, end of life is January 2016, while 14.04 LTS has long time support until April 2019.

---

### Post by dino99 on 2015-09-28
Really does not understand why you took that 'tar' image way; very unusual. As utopic is gone, i suppose the classic way to upgrade from Trusty to Vivid will be a mess.
First if some untrusted packages have been installed, then deactivate this (these) source(s) and update the archive.
So edit /etc/apt/sources.list to change each 'trusty' by 'vivid' and update again.
Then do a manual upgrade: the tools first (dpkg, apt, ...) then the languages (gcc, python, ....) and then everything else

---

### Post by john464 on 2015-09-28
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

We are not professionals. We are users with more or less experience, that help each other. Even the moderators and administrators are volunteers.

Please describe the GUI tools you have tried and the command lines that you have used.

Did you start by updating/upgrading your 14.04 LTS system before trying to upgrade to the next version?

Maybe the problem is that you should upgrade step-wise, 14.04 --> 14.10 --> 15.04, but 14.10 has passed end of life and is no longer supported. It might be possible to upgrade via it, but it is probably rather difficult. Instead I suggest that you

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

and then make a fresh installation the new version if you like it. Beware, the lifetime of 15.04 is short, end of life is January 2016, while 14.04 LTS has long time support until April 2019.

The professionals was a compliment and a joke referring to how all Ubuntu users, developers, and supporters are volunteers and aren't actually Ubuntu Professionals, especially since it is an open sourced OS. So yeah, I got that.

I may just end up going ahead and clean installing it, since so far this is an unheard of issue :(.

---

### Post by grahammechanical on 2015-09-28
We can go from Ubuntu 14.04 to 16.04 when it is released. But the only way to go from 14.04 to 15.04 is to first upgrade to 14.10 but 14.10 has reached end of life. When a version of Ubuntu reaches end of life its repositories are closed and at some point the repositories are archived and moved to a new location. That may have already happened to 14.10 and this could be the reason the Upgrader is seeing 15.04 as the next release of Ubuntu and its rules will not allow it to upgrade 14.04 to 15.04 . 

You may need to use the old-releases technique. Once you get to 14.10 you should be able to get to 15.04. But a fresh install may be best.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

When I make a post I keep in mind that it is not a private conversation. I try to give a bit of education to those who may be viewing the thread. I am sure that I write things that the OP already knows but it also helps me to keep my understanding of how things work fresh in my mind. 

Regards.

---

### Post by ian-weisser on 2015-09-28
> **john464 said:**
> I may just end up going ahead and clean installing it, since so far this is an unheard of issue :(.

It's well heard-of, with many threads in this forum, and some complaints.

The (rare) use case of someone skipping from an LTS to a future non-LTS was discussed when the LTS concept was developed. Developers responded by adding an option to the normal installer to detect and keep your /home directory. And that's the method they test regularly.

The updater is open-source. If sufficient community members want to patch it and do the upgrade-path testing, then release-skipping upgrades will be supported. But that's up to us, not the current developers.

---

