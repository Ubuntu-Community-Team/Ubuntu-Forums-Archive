---
title: "outwitting apt-get"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by akashiraffee on 2009-12-10
I have a few distros on my hard drive and need to use the same mailer with all of them so that I can maintain one common mountable partition with the mail and all my settings (filter rules, etc) on it. Because I don't necessarily use the same DE all the time, and I'd rather avoid DE specific clients like evolution. So I use sylpheed, which IMO is better than most anyway.

But the ubuntu 9.10 sylpheed was built without spell checking, which is a pain. So I tried to build it from source, and when I ran into a weird problem, the sylpheed devs told me it was because of a bug in the Turkish spell checker from enchant 1.5, that either I should downgrade to 1.4.2 or build from source with the Turkish checker configured out.

I did the later and low and behold, they were right. No problem -- except to do that I had to force remove of the enchant package. A bunch of things depend on that, so it turns apt-get into a cankerous whiner who refuses to co-operate.

The only way I could find to solve this was to reinstall enchant, then delete all the files it left. I could have overwritten it by installing the source build into /usr, but I prefer to keep source built stuff in /usr/local, separate from packages, so nothing gets mixed up, inadvertently overwritten, etc. And deleting all installed files seems a surer way to make sure that the (buggy) package libs never get used.

But that is still very hackish -- is there really no way to spoof a dependency for apt-get, or simply supply it with one, eg:

apt-get --add-to-db enchant-1.5

I have not had a look at the dpkg database itself, has anyone ever inserted an entry into it for this purpose? More generally, what do other people do in this situation?

---

