---
title: "upgrade notification with never check for updates turned off"
date: 2018-04-19
forum: Installation &amp; Upgrades
---

### Post by missmoondog on 2018-04-19
probably a silly question but i always have check for updates set to never as i check manually every day.

my question is this. is it possible to still get notified of upgrade when 18.04lts comes out with that setting like that or will i just see a ton of things that say upgradeable in synaptic? i always use synaptic to get updates also and  not software updater.

thank you

---

### Post by cruzer001 on 2018-04-19
You can do it manually without update-manager.

[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

---

### Post by deadflowr on 2018-04-19
As long as you run an apt update, then you'll get some kind of notification of pending upgrades, albeit, you need to open the update manager (software updater) to see it.
(or run the do-release-upgrade command)
The check for updates setting should not affect the notify me of new releases setting.

When you might get the notification depends on what release type you set in the notify me and what the current release is.
If on 16.04 and have it set to any new release, it'll show 17.10 (currently)
if on 16.04 and set to lts releases, then that won't appear until July/August at the first point release.
If on 17.10, then both the any new release and the lts releases should show an upgrade option when the next (18.04) comes out.

What will be interesting is that when a release goes dead the archives move up to point to the next available release.
Why this interests me is that since 17.10 goes dead in July, having the setting set to any new release if using 16.04 might bring in the new release before the expected point release. 
It'll be interesting to see if that's what happens.

(I see on my 14.04 install that I get the do-release-upgrade option to get 16.04 and that is set to normal (any new release)
But I have no idea when that was set, I'm guessing after 15.10 went lights out, but when, but when.)

Random thoughts

---

### Post by missmoondog on 2018-04-20
thank you :)

---

