---
title: "Upgrading Gutsy-&gt;Heron Failed"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Kazol on 2008-05-02
As expected, the upgrade to Heron (using update-manager) failed-when the system reboots (there were no errors during the upgrade process), I am left with an empty brown screen. I tried editing /boot/grub/menu.lst (disabling "quiet" and "splash" options for verbosity), but there were no errors.

Any ideas?

---

### Post by gnozu on 2008-05-02
Yes I have exactly the same problem. And no, sadly I don't have a solution. Other than format your hard drive and use Windows instead.
I've had so many problems with linux installations over the years I really wouldn't like to try to count them.
The people behind Ubuntu just don't get it. eg live chat support? Well just use an IRC channel. Huh? What's that? Oh well, all you have to do is blah blah blah... and at this point 99.9% of normal humans just switch off.
Ubuntu is ugly, badly designed, and totally unusable to anyone who isn't a complete geek. And even a lot of geeks now use osx.

It's sad because it's a lovely idea gone miserably wrong.

---

### Post by analoog on 2008-05-02
check /var/log/ entry's.
If you can't get into your system check via a live cd.

I guess it's gnome that is giving this brown screen? you can try to reinstall/reconfigure gnome.

I don't think Ubuntu is unusable, you just have to spend some time in it if you want certain stuff or it doesn't work on your pc for x reason.
Same problem can also happen when you do a service pack upgrade in xp.
And IRC is a really nice way to get some support, and what about these forums? Better then Microsoft/Apple imho.

---

### Post by Sef on 2008-05-02
> As expected, the upgrade to Heron (using update-manager) failed-when the system reboots (there were no errors during the upgrade process), I am left with an empty brown screen. I tried editing /boot/grub/menu.lst (disabling "quiet" and "splash" options for verbosity), but there were no errors.

Any ideas? 

Best thing to do a clean install.  Upgrades are more problematic than a clean install.  


> Yes I have exactly the same problem. And no, sadly I don't have a solution. Other than format your hard drive and use Windows instead.
I've had so many problems with linux installations over the years I really wouldn't like to try to count them.
The people behind Ubuntu just don't get it. eg live chat support? Well just use an IRC channel. Huh? What's that? Oh well, all you have to do is blah blah blah... and at this point 99.9% of normal humans just switch off.
Ubuntu is ugly, badly designed, and totally unusable to anyone who isn't a complete geek. And even a lot of geeks now use osx.

It's sad because it's a lovely idea gone miserably wrong. 

Just because you don't have the right hardware, doesn't mean that Ubuntu or any GNU/Linux is bad.  On my system, it works great.  If you prefer Windows, then use it.  GNU/Linux is about choice, not locking you in.

---

### Post by Kazol on 2008-05-02
If upgrades in Ubuntu are not clean, the VERY least that the developers could do is at least mention this somewhere (besides actually rectifying this issue).

> Just because you don't have the right hardware, doesn't mean that Ubuntu or any GNU/Linux is bad. On my system, it works great. If you prefer Windows, then use it. GNU/Linux is about choice, not locking you in.

The exact same thing has happened on a completely different system. And no, I completely despise Windows; all other computers, routers, and my pda runs Linux. Instead, I will consider other distros.

---

### Post by analoog on 2008-05-02
No, you should mention the problem to the developers! AFAIK this bug is not known/reported so how can the developers do something about it if they don't know about the bug?

By reporting this bug @ [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) people can help you finding a solution and/or write a patch for you.

I think already someone reported a similar bug (but his system boots eventually):
[https://bugs.launchpad.net/ubuntu/+bug/223843](https://bugs.launchpad.net/ubuntu/+bug/223843)

---

