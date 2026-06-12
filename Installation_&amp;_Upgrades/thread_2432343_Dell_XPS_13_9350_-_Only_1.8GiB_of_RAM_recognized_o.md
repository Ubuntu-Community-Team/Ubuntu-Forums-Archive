---
title: "Dell XPS 13 9350 - Only 1.8GiB of RAM recognized out of 8GiB after install"
date: 2019-11-30
forum: Installation &amp; Upgrades
---

### Post by mattfromseattle2 on 2019-11-30
Sort of a weird situation, but I figured someone might have some ideas. I have a Dell XPS 13 9350 that I'd been running Ubuntu on just fine for the past month or so. The system has 8GiB of RAM on it and this previously was recognized just fine. The other day, I decided to tinker and install Manjaro onto the system. After that install, I had issues with the system freezing and Firefox crashing any time I tried to open something. After a day or so of trying to work around this, I decided to reinstall Ubuntu because it was stable and I knew it worked on my system. As I began to install Ubuntu, I started running into an issue where the installer would freeze up randomly and I'd have to exit out and restart. Eventually, I got it to install but when I logged in, I noticed the system was super slow and it was freezing up and crashing apps just like Manjaro previously had. Curious, I looked at my system settings and noticed that Ubuntu was only recognizing 1.8GiB of memory where previously it had recognized 8GiB. So with that, I figured maybe trying to install version 19.10, which had previously worked fine, might be the issue, so I attempted to install 18.04. Same issue came up.

Next, I tried PureOS, as the installation is quick and was less likely to freeze up on me. After install, same issue, only 1.8GiB of memory recognized. So I tried Manjaro again, but this time went with gnome instead of xfce which I'd previously installed. Same issue. So I ran the Diagnostics from the boot screen and it recognized 8GiB of RAM and passed all tests. Thoroughly confused, I decided to reinstall Windows on the laptop as that would let me see if it was a hardware issue that the tests wasn't detecting. After install Windows, I looked at the system information and it had 8GiB of memory there and ran perfectly fine. So here I am, trying to figure out why Ubuntu (and all other distros) aren't recognizing the RAM on the device suddenly.

If I run 'free' I see the following:
  [TABLE]
 [TR]
 [TH][/TH]
 [TH]total[/TH]
 [TH]used[/TH]
 [TH]free[/TH]
 [TH]shared[/TH]
 [TH]buff/cache[/TH]
 [TH]available[/TH]
 [/TR]
  [TR]
 [TD]Mem:[/TD]
 [TD]1909166[/TD]
 [TD]660552[/TD]
 [TD]114892[/TD]
 [TD]582524[/TD]
 [TD]1133672[/TD]
 [TD]438040[/TD]
 [/TR]
 [TR]
 [TD]Swap:[/TD]
 [TD]0[/TD]
 [TD]0[/TD]
 [TD]0[/TD]
 [TD][/TD]
 [TD][/TD]
 [TD][/TD]
 [/TR]
 [/TABLE]
  
If I run 'free -m' I see:

  [TABLE]
 [TR]
 [TH][/TH]
 [TH]total[/TH]
 [TH]used[/TH]
 [TH]free[/TH]
 [TH]shared[/TH]
 [TH]buff/cache[/TH]
 [TH]available[/TH]
 [/TR]
  [TR]
 [TD]Mem:[/TD]
 [TD]1864[/TD]
 [TD]684[/TD]
 [TD]144[/TD]
 [TD]518[/TD]
 [TD]1035[/TD]
 [TD]437
[/TD]
 [/TR]
 [TR]
 [TD]Swap:[/TD]
 [TD]0[/TD]
 [TD]0[/TD]
 [TD]0[/TD]
 [TD][/TD]
 [TD][/TD]
 [TD][/TD]
[/TR]
[/TABLE]

If I run 'sudo lshw -class memory' I see:

  *-memory
     description: System Memory
     physical id: 39
     slot: System board or motherboard
     size: 8GiB


So - Anyone have any ideas?

---

### Post by mörgæs on 2019-12-01
HI, welcome to the fora.

```
free -h
``` is usually easier to read.

Let's see the complete hardware by running ```
sudo lshw -sanitize > lshw.txt
``` Please post lshw.txt in CODE tags.

---

