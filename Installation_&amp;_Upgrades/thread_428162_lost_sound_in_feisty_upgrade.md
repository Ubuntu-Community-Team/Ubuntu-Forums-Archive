---
title: "lost sound in feisty upgrade"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by brandt on 2007-04-30
Hey,
I just recently upgraded my thinkpad z60t from edgy to feisty.  Now my sound doesn't work.  Everything worked fine under edgy.  Does anyone know what I need to do to get sound up and running again?

---

### Post by Rospo Zoppo on 2007-04-30
Have you seen this [http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device]("http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device")

---

### Post by brandt on 2007-04-30
No luck ](*,).  Thanks for the link, in either case.

---

### Post by Rospo Zoppo on 2007-04-30
Can you post an alsamixer screen?

---

### Post by rrwo on 2007-04-30
I've had the same problems with my ThinkPad Z60m.

Have you checked to see if the sound works when you start from a cold boot? Shut your computer down (as in off completely).  Then start it up and see if the sound works.

Usually the sound works from a cold boot for me, but rarely from a restart or resume form hibernation.

---

### Post by brandt on 2007-04-30
Interesting... cold start worked.  Is there a bug report out on this or should I look into filing one?

---

### Post by rrwo on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/57141](https://bugs.launchpad.net/bugs/57141) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a bug report,

---

### Post by tweston on 2007-05-17
same problem here on upgrading from edgy to feisty on asus w5f laptop
the suggestion listed below involving asoundconf didn't help
going to do fresh install of feisty  - still not working

found problem - feisty not doing intel hda (high def audio) right
for fix see
[http://baheyeldin.com/technology/linux/ubuntu-edgy-6-10-to-feisty-7-04-upgrade-sound-and-video-issues.html](http://baheyeldin.com/technology/linux/ubuntu-edgy-6-10-to-feisty-7-04-upgrade-sound-and-video-issues.html)

---

