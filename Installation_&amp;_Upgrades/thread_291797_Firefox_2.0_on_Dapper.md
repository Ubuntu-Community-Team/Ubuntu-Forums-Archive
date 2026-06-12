---
title: "Firefox 2.0 on Dapper?"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-11-02
Is it possible to install Firefox 2.0 on Dapper (6.0.6 LTS)?

If so, where do I find the package in the repositories?

I looked everywhere using Synaptic but all I could find was Firefox 1.5.0.7.

Thanks,
Alex

---

### Post by taurus on 2006-11-03
OKay, here's a link for you...

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by mcbane on 2006-11-03
I don't know of any Debian/ubuntu packages for Dapper yet. You may need to wait until they get in the backports.

In the meantime, you should try Swiftfox, optimized build of Firefox for specific processors. Installation is incredibly easy, and you'll notice a notable increase in speed compared to regular Firefox. Go to

[http://www.getswiftfox.com/installer.htm](http://www.getswiftfox.com/installer.htm)

The only downside that I can see is that it won't be updated automatically, so you'll have to watch for bugfixes and update it manually each time. But it's worth the trouble.

---

### Post by jgcamp99 on 2006-11-03
> **xp_newbie said:**
> Is it possible to install Firefox 2.0 on Dapper (6.0.6 LTS)?

If so, where do I find the package in the repositories?

I looked everywhere using Synaptic but all I could find was Firefox 1.5.0.7.

Thanks,
Alex

I just download the one @ mozilla.com, then replace the Ubuntu version with it. It would be nice if the Ubuntu repository version would allow for manual and automatic updates and link over to the mozilla homepage instead of the Ubuntu repository ? But the strange thing, even with the mozilla version, it wouldn't update from 1.5.0.7 to 2.0 anyway when I was in Dapper, now that I'm using Edgy, I reenabled root to login and do it that way for the replacement, then under the Ubuntu created default user, I create an app launcher for the gksudo version, so that when logged in as that Ubuntu default user I can update it like I would as sudo. As for Dapper though, updates to the 1.5.0.* version(s) would work, but not 1.5 to 2.0. I guess Ubuntu wants to stay on top of those applications and control how it interfaces with Ubuntu ? Good that it's secure, bad that you have to wait the extra time to get Ubuntu's updated version.

---

### Post by geodude on 2006-11-03
Why is upgrading to FF2 in Ubuntu such a difficult process, requiring us to 'step out' of the Ubuntu environment? It seems to go against the whole Ubuntu ease of use thing. :-/

Even Slackware, which is not known for ease of use, had an updated package out over a week ago. All I had to do was download it and run 'upgradepkg'. Surely creating an official Ubuntu upgrade isn't that tough is it?

---

### Post by ermannobonifazi on 2006-11-05
yes, this is what I mean. I know I can manually install FF2.0 and I know how to do it, but it involve putting lib and bin in different places since FF on Ubuntu is not placed in usual directory. I'd like avoid mess my Ubuntu running machine, so I wonder why is taking so much to put FF 2.0 on the official repository for the upgrade

---

### Post by xp_newbie on 2006-11-05
> **ermannobonifazi said:**
> yes, this is what I mean. I know I can manually install FF2.0 and I know how to do it, but it involve putting lib and bin in different places since FF on Ubuntu is not placed in usual directory. I'd like avoid mess my Ubuntu running machine, so I wonder why is taking so much to put FF 2.0 on the official repository for the upgrade

Not only that, but installing from the .tgz file bypasses all the benefits of using the package manager (apt or Synaptic) - especially the dependncies check.

Thanks to everyone who replied.

Alex

---

### Post by jis on 2006-11-08
You may want to check [this]("http://www.ubuntuforums.org/showthread.php?p=1725281#post1725281") out.

---

