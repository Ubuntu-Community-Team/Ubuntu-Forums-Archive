---
title: "Upgrading from Dapper"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by wwhyte on 2008-04-03
Hi,

This is my first post so apologies for any errors or omissions.

I've got Ubuntu Dapper, version 6.06. I'm interested in upgrading to 7.10 or potentially even 8.04. My understanding is that the only safe upgrade from Dapper, 6.06, is to Edgy, 6.10, so I went looking for how to do this.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) said to run gksu "update-manager -c". Doing this just gave the message "Your system is up-to-date"; no upgrade offered.

A bit more searching suggested I should run gksu "update-manager -c -d". However, when I did this it offered me an upgrade to 8.04 but not to 6.10.

Is there a way to upgrade to 6.10? If not, is it safe to upgrade directly to 8.04?

I'm running on a Thinkpad T60, FWIW.

---

### Post by Jussi Kukkonen on 2008-04-03
upgrades from LTS release to LTS release are supported, so generally speaking 6.06 -> 8.04 is definitely the best path for you. However, 8.04 is not yet released, so you may want to wait a bit if this is not time critical  -- the release should happen this month.

Btw, I guess the update manager did not offer 6.10 as it's practically out-of-support already (18 months for normal releases)

---

### Post by OrangeCrate on 2008-04-03
> **Jussi Kukkonen said:**
> upgrades from LTS release to LTS release are supported, so generally speaking 6.06 -> 8.04 is definitely the best path for you. However, 8.04 is not yet released, so you may want to wait a bit if this is not time critical  -- the release should happen this month.

+1

The official release date is 4/24.

@OP, if you can wait until then, the update should be flawless, and you'll have the latest and greatest.

---

### Post by argraff on 2008-04-10
I have a question with this too - my old Dell won't run any other OS other than Dapper (7.04 and 7.10 were absolutely no-go). What are the chances of 8.04 working fine? The main issue on the inbetweens were mostly graphics related (well, I couldn't get the screen to work, so I can't tell if there were other problems!).

(Tell me if I should start a new thread too, if that's more appropriate - I just thought these were related.)

---

