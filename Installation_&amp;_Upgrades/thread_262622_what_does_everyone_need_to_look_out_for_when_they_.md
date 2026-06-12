---
title: "what does everyone need to look out for when they update their kernel?"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by pixelmoon on 2006-09-21
Well, I'm still a linux newcomer and have been using Ubuntu on and off.  Using Ubuntu at first was both frustrating and interesting (like my relationship with programming) and after days of fiddling I finally got everything to work.  From installing/uninstalling programs and fiddling with different howtos which usually end up breaking something, I'll usually find out how to fix it.  XGL and compiz are nice but I ended up tossing it out for  easier reliability.  Updating to a new kernel is different.

I think the reason I stopped using Ubuntu was because I didn't know how to deal with things breaking from updating to a new kernel.  There are a ton of ways to solve specific problem but **I'd like to know what common things people would need to check on once they update to a new kernel.**

From my experience, updating from 2.6.15-26 to 2.6.15-27 affected my cpu usage, shared folders on my network, and it might have had an effect on my wireless.

*my 100% cpu problem:*
I had to recompile the kernel module in method 2 in the following link.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

*my wireless seems to be disconnecting every now and then:*
not sure if this problem is specific to the 2.6.15-27 kernel but I don't remember this happening before I upgraded.

*my nautilus doesn't see my shared folders on my network:*
i tested going back to using 2.6.15-26 and it saw the folders fine
went back to 2.6.15-27 and it didn't find any computers or folders on the network

would i have to recompile my networkmanager applet?
is it just a matter of recompiling specific programs to get the functionality back?

---

### Post by wieman01 on 2006-09-22
I cannot answer your question concerning the recompiling, however, I ask you a question in return: Why do you upgrade at all? Why don't you disable the upgrade function and stick to the current version of you kernel?

The reason why I am asking is simple: Most of the upgrades (security updates being the exception) are nice-to-haves but go unnoticed by the majority of the users. I personally "pinned" my kernel version and disabled all other upgrades except for security updates. Hence I have been spared the trouble.

---

### Post by pixelmoon on 2006-09-22
The only reason why I update to the latest kernel in the repositories is basically because I see synaptic telling me that there's an update.  I know that most of the time, the updates won't affect my os setup with my hardware.

The reason why I'm looking at finding solutions to my kernel problems is because I'd like to see if there are common problems that occur during a kernel update.  I like fishing for solutions and finally fixing things myself but the reason why I posted this was basically because I was a little lazy and wanted answers faster.

If I find that the answers are random and don't necessarily break the same programs after each update then I probably will settle with a specific kernel.  I never really thought about doing that but I guess it'd save me from those late night headaches.

---

### Post by wieman01 on 2006-09-22
Should you decide to settle with the current kernel and are happy with your setup as it is, you could try this:

[http://www.ubuntuforums.org/showthread.php?t=259280]("http://www.ubuntuforums.org/showthread.php?t=259280")

Personally I don't see a need to upgrade because I don't gain anything out of it but occasional trouble & bug-fixing.

---

### Post by paperdiesel on 2006-12-16
Thanks for the link!

---

