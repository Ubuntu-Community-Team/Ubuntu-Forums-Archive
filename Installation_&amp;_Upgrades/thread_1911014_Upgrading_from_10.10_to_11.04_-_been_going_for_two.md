---
title: "Upgrading from 10.10 to 11.04 - been going for two days!"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by ipsi on 2012-01-18
I attempted to upgrade from 10.10 to 11.04 the other day. Most of it went fine until it tried to upgrade grub-pc. Spent over 24 hours waiting for it to work, and all I saw was a little activity on the hard drive. Eventually killed it and the upgrade kept on going. Also took a long, long time to run another grub command (I forget exactly which one). It's now been running for nearly 48 hours - not doing stuff all that time, necessarily, since I've had to sleep and work, but still.

Is this normal? I have two 2TB HDs in my machine (SATA, 7200 RPM), and a 320GB USB drive.

It finished the installation after I nuked a couple of the GRUB tasks and is now trying to re-install grub-pc. Unsurprisingly, it's taking a while. Does anyone have any idea how long I'm going to have to wait for it to finish? And will I have to do this again when I upgrade from 11.04 to 11.10?

I'd just nuke it entirely, but since it's trying to install grub-related stuff, I really, really don't want to leave my system in an unbootable state... Worst-case scenario, I guess I'll just re-format and install the latest version of Ubuntu. Thankfully /home is mounted on the second of the 2TB disks, while Ubuntu is a small partition on the first (Windows, and my games, take up most of the first disk).

---

### Post by raja.genupula on 2012-01-18
your GRUB really behaving strangely . It shouldnt take much time like that . Reinstall the grub gonna be a solution for you i think . try that once .if possible provide us at what areas its stopping . 


Thank you .

---

### Post by ipsi on 2012-01-18
Last night, it took a couple of hours (I think) for it to run grub-mkdevicemap. After it finished that, it started running "grub-probe --device /". Not sure how long that took, as I was asleep. When I got up, it had moved on to running "grub-probe --device /dev/sda1 --target fs". That was started by grub-mkconfig, which has been running for five hours. So gub-mkconfig probably didn't start the original grub-probe, but it's obviously been doing other things too.

---

### Post by raja.genupula on 2012-01-18
I think this problem needs experts eye , please be patient .

Thank you.

---

### Post by ankah on 2012-01-18
my banshee player in ubuntu 11.10 does not play audio files, its always crashing

---

### Post by BlinkinCat on 2012-01-18
> **ankah said:**
> my banshee player in ubuntu 11.10 does not play audio files, its always crashing


Please do not hijack someone else's thread - :(

Start your own!

New thread box is at top of forum page

---

### Post by raja.genupula on 2012-01-18
> **ankah said:**
> my banshee player in ubuntu 11.10 does not play audio files, its always crashing

yes start a new thread and regarding your issue file a BUG .

---

