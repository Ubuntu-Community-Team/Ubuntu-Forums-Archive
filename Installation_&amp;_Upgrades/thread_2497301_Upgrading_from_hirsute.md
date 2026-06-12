---
title: "Upgrading from hirsute"
date: 2024-04-29
forum: Installation &amp; Upgrades
---

### Post by MarcoPau on 2024-04-29
Hiall, found myself with a backup computer that has Hirsute on it.

Apt is not allowing me to either install new packages or to upgrade.

Is it possible to release upgrade in some way?

What are the steps?

Thanks a bunch!

---

### Post by coffeecat on 2024-04-29
As I see it, you have two choices, as follows:

1 - The first I shall call the **ocean of pain** method.

Essentially, you change your sources.list repos to old-releases.ubuntu.com, and then do a full update of all the packages before attempting a release upgrade. Once that&#8217;s done, you can in theory release upgrade from Hirsute Hippo, 21.04 to 21.10, which is also well past end of life. Then, in theory, you can release upgrade to 22.04, which is both LTS and still supported. I say, &#8221;in theory&#8221;, because this will take hours and hours, you are more than likely to encounter a major breakage at one of the stages, all of which will possibly occasion you a significant emotional event.

And, to be clear, the above is only the outline. The full in all-its-horrific-glory details is described in an Ubuntu wiki somewhere, but I am neither going to look for it nor post a link since - well - I am not a sadist.

I do not recommend this route!

2 - The second is what I shall call the **sensible** route.

Essentially, boot up your old Hirsute system and backup all data that you wish to keep. Then create a fresh install of one of the supported LTS releases, either 22.04 or 24.04.

That should take you no more than an hour, and will be more beneficial for your peace of mind.

---

### Post by Rubi1200 on 2024-04-29
> **coffeecat said:**
> As I see it, you have two choices, as follows:

1 - The first I shall call the **ocean of pain** method.

Essentially, you change your sources.list repos to old-releases.ubuntu.com, and then do a full update of all the packages before attempting a release upgrade. Once that’s done, you can in theory release upgrade from Hirsute Hippo, 21.04 to 21.10, which is also well past end of life. Then, in theory, you can release upgrade to 22.04, which is both LTS and still supported. I say, ”in theory”, because this will take hours and hours, you are more than likely to encounter a major breakage at one of the stages, all of which will possibly occasion you a significant emotional event.

And, to be clear, the above is only the outline. The full in all-its-horrific-glory details is described in an Ubuntu wiki somewhere, but I am neither going to look for it nor post a link since - well - I am not a sadist.

I do not recommend this route!

2 - The second is what I shall call the **sensible** route.

Essentially, boot up your old Hirsute system and backup all data that you wish to keep. Then create a fresh install of one of the supported LTS releases, either 22.04 or 24.04.

That should take you no more than an hour, and will be more beneficial for your peace of mind.
+100 to everything said here!

Just to put things into perspective, I recently installed the full desktop version of Xubuntu in my test partition. It took 20 minutes.

---

### Post by QIII on 2024-04-29
What coffeecat calls the "ocean of pain" method, I call the "significant emotional event" method.

I second, or third, a clean installation -- preserving your /home partition AFTER having backed up everything that is important to you.

---

### Post by guiverc on 2024-04-29
> **MarcoPau said:**
> Hiall, found myself with a backup computer that has Hirsute on it.

Apt is not allowing me to either install new packages or to upgrade.
Is it possible to release upgrade in some way?
What are the steps?
Thanks a bunch!

You're without critical details... esp. product, ie. is this a Server install or Desktop install.

I'm mostly a desktop user, and am involved with in particular one *flavor* of Ubuntu, and keep a system on each supported release. Just prior to 21.04 (*hirsute*) reaching EOL, I would have switched that install to a newer system, but as I would have already had a 21.10 system (*my 20.10 would have become that*) I achieve upgrade by re-install with the next release then in *development* (*it would have become my jammy or what would be my 22.04 system*).   That maybe an option for you, esp. if desktop.

I talk about what I do on this post - [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533) (& elsewhere too).

This maybe an option, but if you're using server apps be aware of how it works & what it will do to your data (*its really a desktop option only*). 

Also note during QA of Ubuntu 24.04 LTS, problems were detected with this approach and thus the `ubuntu-desktop-installer` will FORCE format when re-use of partition is selected, thus this install is not possible (for now) using Ubuntu 24.04 LTS (*or older releases with an updated subiquity done via refresh*). It's still possible with any ISO using `ubiquity` or `calamares` though  ([I]my 23.04 or lunar system became my 24.04 system this way)


[/I]This at least is another option you have.  I use it rather regularly; but I also understand how it works, and can predict what problems I'll have (*where 3rd party packages are involved; we don't QA 3rd party thus I'm careful when I add 3rd party sources to my system on machines where I use this re-install as QA, I have no idea what changes you've made to your Desktop/Server system or what 3rd party was added*).

---

