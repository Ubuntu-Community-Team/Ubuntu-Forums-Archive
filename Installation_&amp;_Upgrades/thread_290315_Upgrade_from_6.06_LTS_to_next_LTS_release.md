---
title: "Upgrade from 6.06 LTS to next LTS release?"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by ulyssesmb on 2006-11-01
Hello!
One question (and sorry for my English).
Upgrade from 6.06 LTS to next LTS release?
When Dapper will be out of support, Edgy will be out of its life cycle, too.
We will have to upgrade to Edgy? Or do a clean installation? Or upgrade to next LTS release? Or something else?
There are official announcements by Ubuntu's team or Canonical?
Thanks

ulyssesmb

---

### Post by ciscosurfer on 2006-11-01
If you'd like 5 years of long term support (LTS), then stick with Dapper.  If you want bleading edge (hence, Edgy) then uprade to Edgy.  Edgy was a catch-up release and was intended to fix/enhance many issues that, at the time, Dapper did or could not.  By the time Dapper isn't supported anymore, we'll be many versions ahead and it will probably be a good idea to upgrade at least a few iterations by then.

---

### Post by ulyssesmb on 2006-11-01
Ok. But if we have to upgrade from a release to the next (Dapper to Edgy in this case), how upgrade Dapper, when Edgy will be out of support? This is my question.
thanks

---

### Post by ciscosurfer on 2006-11-01
Support generally refers to security updates.  You will still be able to upgrade.  You can do this anytime you like or if you prefer, wait a little longer.  You won't have any trouble upgrading is my point.

---

### Post by kwaanens on 2006-11-01
> **ciscosurfer said:**
> You won't have any trouble upgrading is my point.

I think you sound a bit too sure. Upgrading *can* be a troublesome process, and alternatives should be considered.

First, upgrading from one version to the next: that usually works out fine, but not always. There was a slashdot article about upgrading problems with dapper > edgy a couple of days ago. A lot of people experience no problems, some have loads of problems.

Second, upgrading across several versions: NOT recommended. I would strongly recommend people to do a clean install, if the old installation is dated. I mean, if you plan to wait till Dapper's out-of-life, and then upgrading to the newest, then you're definately asking for trouble. Linux development is going at a pretty rapid pace, and you might find yourself stuck with really old config-files. And no matter what anyone says, I refuse to believe that developers for each and every package can take care of years of package-dependencies well enough. Not by a longshot. There is always the possibility of going through severeal dist-upgrades, but that would probably (for most people) take more time than a clean install.

I upgrade every time there is a new version, and my philosophy is: clean install every second time. I did a clean install of Edgy, and configuring stuff over took me about a day. That's 1 day every year, and I'm OK with that. It might have taken less if I had planned the install better (ie. copied all relevant config files)

To each her own, but you might get more trouble than you bargained for, if you always upgrade, and wait several years.

My 2 cents...

- Ketil

---

### Post by ciscosurfer on 2006-11-01
> **kwaanens said:**
> [...]Second, upgrading across several versions: NOT recommended. I would strongly recommend people to do a clean install, if the old installation is dated. I mean, if you plan to wait till Dapper's out-of-life, and then upgrading to the newest, then you're definately asking for trouble. Linux development is going at a pretty rapid pace, and you might find yourself stuck with really old config-files. And no matter what anyone says, I refuse to believe that developers for each and every package can take care of years of package-dependencies well enough. Not by a longshot. There is always the possibility of going through severeal dist-upgrades, but that would probably (for most people) take more time than a clean install.[...]

I never suggested otherwise.  At the same time, if he does this incrementally, he/she shouldn't have trouble.  On the other hand, waiting too long will bring trouble unless a fresh install is implemented.

And I agree and follow what you said regarding upgrading.  When it comes time to upgrade, a fresh install is always the best method; less hassles, etc.  Migration is a pain.

Your thoughts, btw, should help out the original poster and that's a good thing!

---

### Post by kwaanens on 2006-11-01
> **ciscosurfer said:**
> I never suggested otherwise.

Not trying to offend you at all, I just felt the need to write something about this. I love Ubuntu, and would like users to know as much about other users expereinces, so they continue to love this wonderful distro.
I didn't think you said anything wrong at all, I just thought that it might be a good idea to say something more.
Nice to see we are in agreement :)

- Ketil (loving Edgy, just like I loved Hoary, Breezy and Dapper)

---

### Post by ulyssesmb on 2006-11-01
> **kwaanens said:**
> 

Second, upgrading across several versions: NOT recommended. I would strongly recommend people to do a clean install, if the old installation is dated. I mean, if you plan to wait till Dapper's out-of-life, and then upgrading to the newest, then you're definately asking for trouble. Linux development is going at a pretty rapid pace, and you might find yourself stuck with really old config-files. And no matter what anyone says, I refuse to believe that developers for each and every package can take care of years of package-dependencies well enough. Not by a longshot. There is always the possibility of going through severeal dist-upgrades, but that would probably (for most people) take more time than a clean install.


- Ketil

Yes. I see. But if LTS releases have an enterprise target, and not only a geeks/desktop target, what is the option? Several dist-upgrades are critical, and a clean install of many machines is a long process.
I'm not asking for trouble, but i'm interested to understand Canonical plans about this.

---

### Post by ciscosurfer on 2006-11-01
Perhaps the Canonical site has the answer you're looking for ;-)

[Canonical.com]("http://www.canonical.com/")

---

### Post by factotum218 on 2006-11-01
> **ulyssesmb said:**
> Yes. I see. But if LTS releases have an enterprise target, and not only a geeks/desktop target, what is the option? Several dist-upgrades are critical, and a clean install of many machines is a long process.
I'm not asking for trouble, but i'm interested to understand Canonical plans about this.

C'mon you can do it... make a rational decision for yourself...;)

---

### Post by magicfab on 2008-02-13
Please see this thread about testing the new Dapper -> Hardy upgrade tool:
[http://ubuntuforums.org/showthread.php?p=4323348](http://ubuntuforums.org/showthread.php?p=4323348)

---

