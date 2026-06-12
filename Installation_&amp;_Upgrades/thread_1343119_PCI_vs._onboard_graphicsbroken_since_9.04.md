---
title: "PCI vs. onboard graphics/broken since 9.04"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by Jules Delespy on 2009-12-01
This issue has shown up in various forms since 8.10. Is there a durable solution out there?

In this case: I am finally ready to switch to Ubuntu from Windows. The machine is a Pentium 4 entry-level Dell (Dimension 2350) / 1Gb of memory,  with onboard Intel graphics, and a PCI geforce card added. Using *only* the onboard graphics, all versions up to current boot without problem, and work as expected. With PCI geforce (6200) card, only versions up to 8.04 can boot. All versions after 8.04 get thrown into a kernel panic early in the boot process. The machine will be dual-boot, and the Windows+geforce card are needed for the games 4 kids play on it. 8.10, 9.04, 9.10, and the latest 10.04 are affected.

Similar issues have been brought up with other computers and card combinations, but it seems that the constant is onboard graphics works  vs. PCI graphics card does not work.

I only find three possible solutions:
[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)
and
[http://ubuntuforums.org/showthread.php?t=1144043](http://ubuntuforums.org/showthread.php?t=1144043)
and
[http://ubuntuforums.org/showthread.php?t=1078576](http://ubuntuforums.org/showthread.php?t=1078576)

I was hoping the problem was limited to 8.10, 9.04 and 9.10, and was planning to wait out 10.04 before migrating, but the problem is apparently still there in 10.04.

Just one more piece of information on this particular system: the BIOS options for graphics are: 'onboard' or 'auto'. No 'PCI only' option. Ubuntu up to 10.04 boot when either the card is removed, or BIOS is set to 'onboard'. 

Any suggestions?

Thanks

---

### Post by Jules Delespy on 2009-12-02
More solutions:
[http://ubuntuforums.org/showthread.php?t=496999](http://ubuntuforums.org/showthread.php?t=496999)

As it turns out, problems with PCI cards when onboard graphics are also available also affect versions 6 and 7 of Ubuntu. I tried booting 6.10 and 7.10 from CD, and both get into kernel panic early into booting. 
So: it seems only 8.04 is ***not*** affected. 
Can any experienced user suggest what 8.04 alone does with respaect to PCI vs. onboard, or how to find out??

---

### Post by Jules Delespy on 2009-12-03
After more research, I have found that all versions of Ubuntu are affected, with the possible exception of 8.04. Here is a collection of related links.
The issue is installation on machines where 1) graphics processing is integrated into the motherboard and 2) a graphics card has been added as an upgrade. The cards are often Nvidia, but not necessarily. Often, the integrated graphics cannot be fully disabled in BIOS, or things go wrong even when the integrated graphics are disabled in BIOS.
This configuration can lead to a variety of problems, with the most severe being kernel panic at boot time, which results in the inability to either try out the liveCD, or install Ubuntu at all.
Since issues related to the combination of integrated graphics+graphics card show up in many forum categories, I collected a list of references where a solution was proposed. The first of those references comes from Alberto Milone (tseliot in Ubuntu forums), the author of EnvyNG, among other qualifications. It seems reasonable to think that it is the best current solution.
The problem has existed in all versions of Ubuntu since at least version 5.10, and all the way to 27 November 2009 daily releases of 10.4. Strangely, it is possible that 8.04 was not affected. I have checked that the live CD of 8.04 indeed boots properly on affected machines, while none of the other versions do. As illustrated by the following links, other distros are affected as well. As a practical matter, this is very likely to stop many users from installing Linux on entry-level namebrand computers, which seems a shame.

here are the links:
[URL="http://www.albertomilone.com/nvidia_...integrated.txt"]
[/URL][http://www.albertomilone.com/nvidia_int ... grated.txt]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1256691](http://ubuntuforums.org/showthread.php?t=1256691)
[http://ubuntuforums.org/showthread.php?t=1144043](http://ubuntuforums.org/showthread.php?t=1144043)
[http://ubuntuforums.org/showthread.php?t=675497](http://ubuntuforums.org/showthread.php?t=675497)
[http://ubuntuforums.org/showthread.php?t=1308919](http://ubuntuforums.org/showthread.php?t=1308919)
[https://bugs.launchpad.net/ubuntu/+sour ... +bug/55104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55104")
[http://www.bikechatforums.com/viewtopic.php?p=2356664](http://www.bikechatforums.com/viewtopic.php?p=2356664)
[http://www.nvnews.net/vbulletin/showthread.php?t=128934](http://www.nvnews.net/vbulletin/showthread.php?t=128934)
[http://ubuntuforums.org/showthread.php?t=196693](http://ubuntuforums.org/showthread.php?t=196693)
[http://ubuntuforums.org/showthread.php?t=635943](http://ubuntuforums.org/showthread.php?t=635943)
[http://ubuntuforums.org/showthread.php?t=192677](http://ubuntuforums.org/showthread.php?t=192677)
[http://ubuntuforums.org/showthread.php?t=496999](http://ubuntuforums.org/showthread.php?t=496999)
[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)
[http://ubuntuforums.org/showthread.php?t=1078576](http://ubuntuforums.org/showthread.php?t=1078576)
[http://ubuntuforums.org/showthread.php?t=295133](http://ubuntuforums.org/showthread.php?t=295133)
[http://javadocs.wordpress.com/2008/09/2 ... -gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")
[http://ubuntuforums.org/showthread.php?t=207303](http://ubuntuforums.org/showthread.php?t=207303)
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)
[http://mepislovers.org/forums/showthread.php?t=6487](http://mepislovers.org/forums/showthread.php?t=6487)
[http://www.opensubscriber.com/message/s ... 46049.html]("http://www.opensubscriber.com/message/slug@slug.org.au/6446049.html")
[http://ubuntuforums.org/showthread.php?t=126492](http://ubuntuforums.org/showthread.php?t=126492)

---

