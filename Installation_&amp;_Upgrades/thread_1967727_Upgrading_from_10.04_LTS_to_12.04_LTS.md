---
title: "Upgrading from 10.04 LTS to 12.04 LTS"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by HouTex on 2012-04-28
I had 10.04, but not 10.04.4, so the update manager would not let me update directly to 12.04.  
 
I didn't know about the 10.04.4 version so I've started to update the OS's one by one until I get to 12.04.  I'm in the middle of installing 10.10.
 
Can I revert back to 10.04 and make sure I install 10.04.4 and then upgrade directly to 12.04?  Would that be quicker than updating to 11.04, 11.10, and then 12.04?

---

### Post by darkod on 2012-04-28
Don't upgrade to 10.10. Upgrading 4 times in a row will most certainly create problems.

I don't think you need to upgrade to 10.04.4 first (but I might be wrong). In the Software Sources, in the Update tab, make sure you have Long Term releases only selected. That way it will not prompt you for any normal release, only for LTS releases.

That should offer you option to upgrade to 12.04 directly.

Another option is downloading the ISO, burning a cd and upgrading with the cd instead of over the internet. Most people use the Alternate Install CD for that.

---

### Post by Derspankster on 2012-04-28
It looks like it's not possible to upgrade from 11.04 to 12.04. I have my upgrade settings to LTS versions only and I get no notification to upgrade to 12.04.  

I have a laptop that's running 10.4.4 LTS and it's set for LTS upgrades as well and I get no notification of 12.4 being out there for upgrade either.

Seems to make the point of setting up LTS upgrades only a moot one.

I'm guessing you need to be running 11.10 to be able to 'upgrade' to 12.04 or am I missing something?

---

### Post by darkod on 2012-04-28
> **Derspankster said:**
> It looks like it's not possible to upgrade from 11.04 to 12.04. I have my upgrade settings to LTS versions only and I get no notification to upgrade to 12.04.  

I have a laptop that's running 10.4.4 LTS and it's set for LTS upgrades as well and I get no notification of 12.4 being out there for upgrade either.

Seems to make the point of setting up LTS upgrades only a moot one.

I'm guessing you need to be running 11.10 to be able to 'upgrade' to 12.04 or am I missing something?

From 11.04 it's normal that you don't get the option. You can only upgrade directly from LTS to LTS, and 11.04 is not a LTS. So you would need to go to 11.10 and then 12.04. But in this case a clean install might be a better value. Two upgrades in a row might create lots of issues.

As for the 10.04.4 I am not 100% sure. I have read that maybe you will need for 12.04.4 but that doesn't make much sense to me. You can investigate further.

In general, the LTS only setting does work and it stops you from being offered "normal" upgrades and doing them by accident.

EDIT PS: This thread from the 12.04 testing says that it upgraded from 10.04.4 to 12.04 Beta2. That should mean upgrade to 12.04 is possible without waiting for 12.04.4. Did you all the updates first? Before an upgrade you need to do all the updates of all packages first. There should be no updates pending.

PS2: It seems it will work after 12.04.1 is released. But you can do it before with:
[http://askubuntu.com/questions/125392/no-new-release-found-when-upgrading-a-from-10-04-lts-to-12-04-lts](http://askubuntu.com/questions/125392/no-new-release-found-when-upgrading-a-from-10-04-lts-to-12-04-lts)

---

### Post by grahammechanical on 2012-04-28
It is recommended that the OS be updated before it is upgraded. So, if 10.04 was updated then it would become 10.04.4 would it not?

I tested the upgrade path for both 10.04 and 11.10.

To do this I installed 10.04 specifically to follow these instructions

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade]("http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade")

Note the command to be used.

Note also this comment from the release notes under the heading **Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS**

> It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop")

Regards.

---

### Post by Derspankster on 2012-04-28
> **darkod said:**
> From 11.04 it's normal that you don't get the option. You can only upgrade directly from LTS to LTS, and 11.04 is not a LTS. So you would need to go to 11.10 and then 12.04. But in this case a clean install might be a better value. Two upgrades in a row might create lots of issues.

As for the 10.04.4 I am not 100% sure. I have read that maybe you will need for 12.04.4 but that doesn't make much sense to me. You can investigate further.

In general, the LTS only setting does work and it stops you from being offered "normal" upgrades and doing them by accident.

EDIT PS: This thread from the 12.04 testing says that it upgraded from 10.04.4 to 12.04 Beta2. That should mean upgrade to 12.04 is possible without waiting for 12.04.4. Did you all the updates first? Before an upgrade you need to do all the updates of all packages first. There should be no updates pending.

PS2: It seems it will work after 12.04.1 is released. But you can do it before with:
[http://askubuntu.com/questions/125392/no-new-release-found-when-upgrading-a-from-10-04-lts-to-12-04-lts](http://askubuntu.com/questions/125392/no-new-release-found-when-upgrading-a-from-10-04-lts-to-12-04-lts)

Thanks for your reply. I've decided to do a fresh install on my desktop 11.04 system.  It is the best choice.  The laptop, however, is another matter. Because of it's integrated and weak graphics board I believe I'm better off staying with 10.4.4 LTS and gnome2. If that becomes an issue down the road I'll likely shops for another distro or window manager.

---

### Post by HouTex on 2012-04-28
Well, I updated up to 11.10 and I've stopped there.  It went very smoothly and my system works better than it did in 10.04.  I'll wait a few months to update to 12.04.

But it is strange that you are supposed to upgrade from one LTS to another LTS and the upgrade center never gave me the option to do that.  I didn't know about the 10.04.4 thing.

---

### Post by Derspankster on 2012-04-29
I'm still confused as to why I have no upgrade (to 12.04) option on my laptop running 10.04.4 LTS.

---

### Post by poliltimmy on 2012-04-29
I tried an upgrade last night. And wish I had read this thread before I did. Only two 3rd party apps survived. That was CrossOver and Thunderbird. No permissions  survived. No access to data partition. No access to the software center on Unity desktop. Software Center in LXDE works. So I was able to get gdebi and synaptic back. LXDE has no copy and paste function. So copy and pasting into the terminal is a no go. Typing this,I realize that spellcheck in this version FF 11 does not work.

Where was the warning about apps may need reinstalling? Just before "Installation Complete" dialog.

---

### Post by darkod on 2012-04-29
> **Derspankster said:**
> I'm still confused as to why I have no upgrade (to 12.04) option on my laptop running 10.04.4 LTS.

Did you see the PSs added later to my last post?

Basically it seems an upgrade from 10.04.x to 12.04 will not be offered until 12.04.1 is released in July.

If you want a direct upgrade to 12.04 and not to wait until July, you can do it with:
sudo update-manager -d

---

### Post by Derspankster on 2012-04-29
> **darkod said:**
> Did you see the PSs added later to my last post?

Basically it seems an upgrade from 10.04.x to 12.04 will not be offered until 12.04.1 is released in July.

If you want a direct upgrade to 12.04 and not to wait until July, you can do it with:
sudo update-manager -d

Thanks - I did miss that.  Because of the weak video performance of my old laptop I likely will stay with 10.04.4.

---

