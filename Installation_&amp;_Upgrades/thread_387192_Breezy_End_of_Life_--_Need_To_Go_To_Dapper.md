---
title: "Breezy End of Life -- Need To Go To Dapper"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by SuperMike on 2007-03-18
I heard that Breezy has reached or is reaching the end of its life. I heard that it's recommended to go to Dapper for long term support. I like to stay conservative in my Linux OS, so I probably won't go with Edgy and might consider moving to Feisty or a later release when it comes out. (I thought I also read another article that said that every odd release of Ubuntu is unstable, and every even release is stable. Is that true?)

Anyway, I'm currently on Dapper at my office and Breezy at home. I purchased the Dapper CD, but unfortunately I didn't realize it came on a DVD and I don't have a DVD player right now for this home system.

So, my question: can someone tell me the proper procedure to download the ISO from Ubuntu, mount it as a local file, and upgrade my PC?

P.S. I also strongly feel compelled to donate a small amount to Canonical because I'm consuming valuable time on their servers to download bytes for the upgrade and for all my patching.

---

### Post by Sef on 2007-03-18
> (I thought I also read another article that said that every odd release of Ubuntu is unstable, and every even release is stable. Is that true?)

The stable versions come out every 3 years for the desktop.  If you are conservative, go with Dapper Drake.  Both Edgy and Fiesty are considered unstable.

> So, my question: can someone tell me the proper procedure to download the ISO from Ubuntu, mount it as a local file, and upgrade my PC?

[Dapper Upgrades]("https://help.ubuntu.com/community/DapperUpgrades") from Breezy.

---

### Post by SuperMike on 2007-03-18
Thanks a bunch. I'll give it a swing.

---

### Post by 23meg on 2007-03-18
[QUOTE=Sef]The stable versions come out every 3 years for the desktop. If you are conservative, go with Dapper Drake. Both Edgy and Fiesty are considered unstable.
[/QUOTE]

Every Ubuntu release (made every six months) is referred to as a stable version. Aside from the normal releases, there will be occasional long term support releases like Dapper, but there's no set schedule for them. Edgy, being a released version, is considered stable, but since it's been put together in less time than a usual release (about four and a half months) to allow for longer bug fixing for Dapper, it's *considered to be* a less stable release than the normal stable releases, but isn't necessarily so in every use case.

Feisty is considered unstable in all meanings, due to the fact that it's still in development.

---

### Post by zaazu48 on 2007-03-19
Hello,

 why is it that when ever I launch sudo I get this error on dapper 

*sudo: timestamp too far in the future: Mar 19 12:10:46 2007*

Please any help will be appericiated

---

### Post by SuperMike on 2007-03-19
Weird sudo error. Hmm. Well, did you somehow apply a Daylight Savings Patch to your system manually? Dapper didn't need it because I found it downloaded properly from Ubuntu and the time changed properly on its own.

If that's not it, I was thinking to uninstall sudo and reinstall (apt-get --purge remove sudo; apt-get install sudo), but that could have drastic effects I suspect, so I don't recommend that at all.

Now might be a good time for you to know your root password in this kind of unstable situation with your sudo:

$ sudo passwd root
(type in your local password)
(type in a new root user password)
(type in a new root user password)

---

### Post by linear on 2007-03-19
> **zaazu48 said:**
> why is it that when ever I launch sudo I get this error on dapper 

*sudo: timestamp too far in the future: Mar 19 12:10:46 2007*

See [this post]("http://www.ubuntuforums.org/showpost.php?p=1145634&postcount=10") for a solution. (The entire thread discussing the problem is [here]("http://www.ubuntuforums.org/showthread.php?t=173505").)

---

