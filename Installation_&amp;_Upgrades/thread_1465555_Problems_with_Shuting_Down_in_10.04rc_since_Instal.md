---
title: "Problems with Shuting Down in 10.04rc since Installation this morning"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by RichardSM on 2010-04-29
Hello Ubuntu 10.04rc USERS

I just installed 10.04rc looks real nice had some problems getting connected seems to work for now. Oh well my main concern is my computer won't fully shutdown screen goes to ubuntu logo and it stops at three of the red dots i hear a click and it just sets there. I had this same problem with distro 9.10 found the info in the forum so far no body has posted the problem fix for this distro ?.Now I did try some of the 9.10 fixes no good I even did sudo shutdown -h now it went to the shutdown screen and stopped at the forth red dot any help I would be very thankful for. Again in advance thanks too ALL.......

My system is.

AMD Athlon 1400 Thunderbird
MSI Mother Board
GeForce 6200 256Kb
Ram 512Kb
52x33x52x CD Writer
350W Power Supply
Microsoft Wheel Mouse Optical 1.1A USB
Tower Case****

Hello this was the fix for me give it a try.Just for the record I downloaded the latest copy of Ubuntu 10.04LTS and did all the updates too. Be sure save after change, to update [COLOR="Red"]sudo update-grub[/COLOR]some users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone

---

