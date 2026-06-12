---
title: "Wifi problems after kernel update"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by joeymorin on 2023-10-27
Longtime listener, first-time caller.

Note to moderators:  If I've posted in the wrong forum, please forgive me.

System details:

[LIST]
[*]Lenovo T410i
[*]Ubuntu MATE 18.04 LTS with esm-apps, esm-infra, and livepatch.
[/LIST]
Partial output of lspci -vv:[INDENT][FONT=courier new]03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak][/FONT][/INDENT]
[INDENT][FONT=courier new]        Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN[/FONT][/INDENT]
[INDENT][FONT=courier new]        Kernel driver in use: iwlwifi[/FONT][/INDENT]

I use WiFi on this machine but not as my main connection, so I didn't notice this right away, but recently I found that I could not unblock it, either soft unblocking or hard unblocking.  Looking in /var/log (kern.log and syslog) I find:[INDENT][FONT=courier new]        iwlwifi 0000:03:00.0: Error, can not clear persistence bit[/FONT][/INDENT]

Only a reboot will restore functionality.  The issue appears to be triggered semi-randomly, seemingly only after at least one suspend cycle.

Brief digging suggested this kind of thing to be an issue with a kernel update (although I'm not certain).

The kernel version I was running when I noticed the issue was 4.15.0-219.  I rolled back to 4.15.0-218 but the issue remained.  I had already used [FONT=courier new]apt autoremove[/FONT] to toss 4.15.0-216 at that point, but I installed it manually via [FONT=courier new]apt install linux-headers-4.15.0-216 linux-headers-4.15.0-216-generic linux-image-4.15.0-216-generic linux-modules-4.15.0-216-generic linux-modules-extra-4.15.0-216-generic[/FONT], and selecting it at boot time solves this particular problem.

Is this issue familiar to anyone?  Can anyone point me in some direction that will help me learn what has changed to cause this problem?  Change logs appear to be largely unavailable for esm- updates, so I'm not even sure what I'm missing out on, but I expect -218 and -219 carried important security updates.

Is there some other place I should be reporting this?  It's unclear to me if this is a build/configuration issue, or a regression.

Many thanks.

---

### Post by MAFoElffen on 2023-10-28
I am using that wifi module on my Lenovo on 22.04.3 and am having no problems. 18.04 LTS has been out of support for end of life was May 23rd, 2023... But you have it on ESM, which extended Security Updates through 2028, but... This Forum's Policy is to support only releases under active support.

Just a question... What is preventing you from upgrading to a release that is actively being supported?

Having said that... What do you mean by that you "could not unblock it, either soft unblocking or hard unblocking."?

Did you mean by using rfkill or nmcli? Or by restarting the NetworkManager.service? (by turning on/off the radio by using utilities that use it's API to interact with it...)

And how does the relate to you suspecting that you have a module issue?

I mean I can give you commands to check those issues, but I am unclear of the why,and what you are looking for.

The underlying unknown here is looking at this:
```

journalctl -b -l --system -o short-full -g 'iwlwifi'

```
Please post the output within CODE Tags. If you are unsure how to do that, look at the link in my signature line.

---

