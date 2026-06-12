---
title: "Typing freezes the screen temporarily"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Zorrothustra on 2010-05-05
Just reinstalled 10.4 on one of the partitions of my HD. RE-installed cause I kind of messed up the previous installation. Formatted the partition as ext4. Except one major problem everything seems to works fine now. The problem didn't appear in the previous installation (ext3). 

When I type the screen freezes for a few seconds every few seconds (only when typing). Rythmbox keeps on playing. Just a crack when the screens becomes active again. Tried closing programs to check if it was program-related. My machine managed to hang even with only Gedit opened. It really seems keyboard related. I have to wait while typing cause it doesn't remember more than a few characters. Extremely unworkable. 

I use a Dell Studio 1558. Looked around the forum, didn't seem like anyone else has this problem. 

An idea someone ? Except another reinstall that I am about to do shortly without some community help....


Thanks

---

### Post by Zorrothustra on 2010-05-06
Did that reinstall in ext3-format. Everything seemed to work fine. Until I installed the proprietary driver for the wireless and the ATI graphics card and rebooted. Same problem again. 

Uninstalled the Broadcom b43 driver since the wireless didn't work anyway. Same problem until the rebooted again: typing as it should be. 

The problem seems to be in the driver somewhere... No-one else bumped into this ? 

Anyway, as long as there is a wire, I can work. Thats what it's all about. Typing is more of the essentials I need for now. But wireless would be nice...

---

### Post by Tommy_CZ on 2010-05-30
Hi, I have same problem, it appears after 1 year of using, I have Kubuntu 10.04 and wondering if someone know why it does?
I also filled a [bug report in launchpad]("https://bugs.launchpad.net/ubuntu/+bug/587160")
Please comment here you can confirm it so they can realise it IS a problem.

---

### Post by aneganov on 2010-07-14
I have similar problem.
Yesterday I upgraded to 10.04 lucid, and now I see I made mistake - so many problems, that I can't think about anything positive in my this decision now.

I experience freezing typing too on my Acer Aspire 5930G. This happens not right after the system boot though. `top` is showing nothing interesting too, so I believe this is not an application problem. Bu the only proprietary driver installed is nvidia vga, so this is either hardware error (hope is not) or a kernel bug. 

Any workarounds/fixes?

---

### Post by aneganov on 2010-07-25
Still having this problem. After some time after boot, my keyboard start freezing. Syslog are overfilled with messages about ACPI errors. Any ideas?

---

### Post by aneganov on 2010-07-28
Please someone help! I have to reboot every 30-40 minute, since keyboard hangs and its impossible to continue working. I'm pissed off with this, I have to work but can't due to this!

When I type letters, and keyboard freezes, which happens every 2 seconds or so, sometimes typed keys are missed. This makes it even impossible to type blindly, guessing letters will appear after freeze. 

I don't know is this related to freezes or not, but every time when this happens, logs are filled with this messages:


```
Jul 28 14:17:47 fantomas-laptop kernel: [ 7063.989144] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:48 fantomas-laptop kernel: [ 7064.984045] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:48 fantomas-laptop kernel: [ 7064.984060] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:48 fantomas-laptop kernel: [ 7064.984089] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f7017120), AE_TIME
Jul 28 14:17:48 fantomas-laptop kernel: [ 7064.984184] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.484071] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.484088] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.484121] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f7017120), AE_TIME
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.484223] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.985101] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.985115] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:49 fantomas-laptop kernel: [ 7065.985147] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.484111] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.484127] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.484161] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f7017120), AE_TIME
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.484268] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.985240] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.985257] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:50 fantomas-laptop kernel: [ 7066.985291] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.484382] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.484398] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.484428] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f7017120), AE_TIME
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.484524] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.984050] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.984065] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.984094] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f7017120), AE_TIME
Jul 28 14:17:51 fantomas-laptop kernel: [ 7067.984188] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 28 14:17:52 fantomas-laptop kernel: [ 7068.489070] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:52 fantomas-laptop kernel: [ 7068.489085] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:52 fantomas-laptop kernel: [ 7068.489113] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:52 fantomas-laptop kernel: [ 7068.989233] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:52 fantomas-laptop kernel: [ 7068.989249] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:52 fantomas-laptop kernel: [ 7068.989279] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:54 fantomas-laptop kernel: [ 7070.489079] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:54 fantomas-laptop kernel: [ 7070.489096] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:54 fantomas-laptop kernel: [ 7070.489125] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:54 fantomas-laptop kernel: [ 7070.989074] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:54 fantomas-laptop kernel: [ 7070.989088] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:54 fantomas-laptop kernel: [ 7070.989116] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:56 fantomas-laptop kernel: [ 7072.489259] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:56 fantomas-laptop kernel: [ 7072.489274] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:56 fantomas-laptop kernel: [ 7072.489304] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:56 fantomas-laptop kernel: [ 7072.989135] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:56 fantomas-laptop kernel: [ 7072.989151] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:56 fantomas-laptop kernel: [ 7072.989180] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:58 fantomas-laptop kernel: [ 7074.489039] ACPI: EC: input buffer is not empty, aborting transaction
Jul 28 14:17:58 fantomas-laptop kernel: [ 7074.489055] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 28 14:17:58 fantomas-laptop kernel: [ 7074.489084] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Jul 28 14:17:58 fantomas-laptop kernel: [ 7074.989038] ACPI: EC: input buffer is not empty, aborting transaction

```

---

### Post by aneganov on 2010-07-30
Bump

---

### Post by aneganov on 2010-07-31
Help

---

### Post by afauno on 2011-05-10
I have the same issue after upgrading to natty... :(

It seems the same as this ubuntu bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578506)

More importantly, a patch is proposed by the kernel guys at [https://bugzilla.kernel.org/show_bug.cgi?id=14733](https://bugzilla.kernel.org/show_bug.cgi?id=14733)

---

