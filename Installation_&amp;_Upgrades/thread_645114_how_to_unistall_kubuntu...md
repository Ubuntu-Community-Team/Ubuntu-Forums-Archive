---
title: "how to unistall kubuntu.."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by BrOSs on 2007-12-19
first to all.. i have a real mess.. check this out:

[15:31] <BrOSs> i want to unistall kubuntu.. and reinstall it from liveCD, how can I unistall it?
[15:33] <BrOSs> well.. I don't know in which partition is exactly installed
[15:33] <BrOSs> =/
[15:33] <BrOSs> besides.. kubuntu is not the only os installed
[15:33] <BrOSs> i also have Vista, XP.. and old versions of kubuntu
[15:34] <BrOSs> haha is a real mess
[15:34] <BrOSs> i just want to keep Vista..
[15:34] <BrOSs> in order to reintall kubuntu 7.10

thks

---

### Post by stalker145 on 2007-12-19
> **BrOSs said:**
> first to all.. i have a real mess.. 

<snip>

thks

To begin with, I would open a terminal and type ```
cat /etc/fstab
``` while in Kubuntu to figure out which partition is root. It'll be the one with a slash (like this / ) - make note of which device it is (in my case it's /dev/sda1)

Once you figure that out, it's as simple as popping in the install CD and installing on that drive.

Now, if you just wanted to uninstall Kubuntu for a different DE/WM then I would say to check out the [Psychocats]("http://www.psychocats.net/ubuntu/") web site under "Playing Around"

Check back if this doesn't work out for you.

---

### Post by BrOSs on 2007-12-23
> **stalker145 said:**
> To begin with, I would open a terminal and type ```
cat /etc/fstab
``` while in Kubuntu to figure out which partition is root. It'll be the one with a slash (like this / ) - make note of which device it is (in my case it's /dev/sda1)

Once you figure that out, it's as simple as popping in the install CD and installing on that drive.

Now, if you just wanted to uninstall Kubuntu for a different DE/WM then I would say to check out the [Psychocats]("http://www.psychocats.net/ubuntu/") web site under "Playing Around"

Check back if this doesn't work out for you.

-----

the windows vista partition is broke.. doeesn't start, so i can just log to kubuntu partition in order to boot my system. is there a form to unistall kubuntu inside of kubuntu. I mean, boot from kubuntu 'cause is the only OS that runs.

sorry about my english.. hope u understand x)

---

### Post by jrusso2 on 2007-12-23
you could just boot off the kubuntu cd and reinstall it.  Reformat the partitions first and then reinstall.

You should probably fix you windows first though before you reinstall kubuntu.

If you reinstall windows after you will have to fix grub again.

---

### Post by BrOSs on 2007-12-23
> **jrusso2 said:**
> you could just boot off the kubuntu cd and reinstall it.  Reformat the partitions first and then reinstall.

You should probably fix you windows first though before you reinstall kubuntu.

If you reinstall windows after you will have to fix grub again.

I did that.. thks for helping me, now is working

---

