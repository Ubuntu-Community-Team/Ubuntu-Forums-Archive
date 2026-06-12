---
title: "echoing to grub2 boot menu"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by dijxtra on 2011-01-29
I'd like have some text written on my grub2 boot menu. In legacy grub you could just add:
title Foobar
and you'd get "Foobar" displayed. I tried:
menuitem "Foobar" {}
grub2, but it doesn't work. Any ideas how do you do something like that?

(Yes, I know writing grub.cfg by hand is not very smart. But I have a special situation: I wrote my own grub.cfg on a dedicated boot partition from where I chainload to other grub on other partitions. Those secondary grubs generate their grub.cfgs on the fly, so everything is OK :-) )

---

### Post by sikander3786 on 2011-01-29
I think these links might help you.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by oldfred on 2011-01-30
sikander3786 gave you good links on grub2. 

I have used these to add a space line, chainboot, & reboot. Some have not had halt work, seems to depend on system. Note that depending on what drive you boot the hd number may not match  the sda number as hd0 is always the boot drive.

menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

---

### Post by dijxtra on 2011-01-30
> **oldfred said:**
> sikander3786 gave you good links on grub2. 
Yeah. Excellent links, but I couldn't find the answer to my question... which is:
> **oldfred said:**
> 
menuentry " " {
set root= 
}

this.

Thanks man, you helped a lot.

---

