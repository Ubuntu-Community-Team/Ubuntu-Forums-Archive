---
title: "Can I move a stable installation of 16.04 without losing anything?"
date: 2017-10-15
forum: Installation &amp; Upgrades
---

### Post by daitheboot on 2017-10-15
I have a good installation of Ubuntu 16.04 running on a HDD. I also have an installation of Win 10 running on a separate SSD. My question....is it possible to migrate the Ubuntu installation complete with all data, settings etc. to run alongside the Windows installation in dual boot format. I do know how to set-up a fresh installation of ubuntu as a dual boot but not sure how to migrate the data, apps and settings.
Any help would be appreciated as I am a relatively newcomer to Ubuntu.

---

### Post by gordintoronto on 2017-10-15
The difficulty arises with the drive ID, which may be included in some settings. Your current Ubuntu installation might be on SDB1, and you will switch to SDA2, perhaps.

A fresh install in dual-boot, followed by installing applications, avoids these issues. Then you could copy your data folders to the SSD. Or perhaps it would be better to set up symlinks to the existing data folders, so you don't fill the SSD. Yes, this is more work than you had hoped for.

When I was faced with the exact same situation, I installed the latest and greatest on the SSD, and left all my data on the spinning drive, without even setting up symlinks. When I use the file manager, I have one extra step: I click on "518 GB drive" then go from there. Note that 17.10 is about to be released, and you will be able to upgrade it to the next LTS when it becomes available.

---

### Post by Bucky Ball on 2017-10-16
> **gordintoronto said:**
> Note that 17.10 is about to be released, and you will be able to upgrade it to the next LTS when it becomes available.

Also note that LTS upgrades to the next LTS, so 16.04 LTS upgrades to 18.04 LTS, unless something's changed for that release. LTS to LTS leapfrogs the interim releases in between, avoiding having to use the interims if you don't want to use them (as I don't). ;)

16.04 LTS is also supported until 2021, but you would need to go 16.04> 18.04> 20.04 LTS to get to the 20.04 LTS I'd imagine (not 16.04 LTS> 20.04 LTS). 

Just thought I'd mention it. :)

---

