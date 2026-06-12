---
title: "Restore IMAGE to new hardware"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by Ubu1son on 2016-10-16
I have been using xubuntu 14.04 LTS for a while now.  It is all up to date, so I'm assuming that would be the same as installing the latest 14.04x iso...

I have made an image of the partition ( on a celeron laptop/intel gpu ) and wish to restore that partition image to new hardware ( 2016 pentium n3710 ).

The new hardware has an ssd.  

Will it just boot up and recognise the hardware and run normally, or will there be problems?

Also, will there be anything to configure for the ssd ( as it is not a install but a restore ), or does an up to date 14.04 work with all ssd's?


Thanks.

---

### Post by ajgreeny on 2016-10-16
It is difficult to say with complete certainly but the system may well boot fine from that disk, particularly if still using an integrated Intel GPU, so try it if possible.

If there do turn out to be problems it may be something simple that can be fixed easily.

Linux is a great deal easier to deal with in this situation than Windows which is now inextricably linked to an individual hardware set.

---

### Post by Ubu1son on 2016-12-07
Well, I restored the image onto the new laptop, and it has booted up fine ( going from intel dual to quad core, and from mbr/bios to gpt/uefi).


But a few things, I'm not sure if related to new hardware. 


1) In firefox, there is a small amount of screen tearing on youtube ( html5 ) and more cpu usage than expected, as I thought it would use the intel gpu?
And flash is just choppy....


2) when loading up office, I noticed under java section it has sun microsystems 1.6 and oracle java 1.7.  Are these old, and should be replaced with just one java?


3) on the old laptop, the brightness hotkeys didnt work, and they still dont work. But when I loaded up a live cd with 14.04, they were working!  Not sure how that is?

---

