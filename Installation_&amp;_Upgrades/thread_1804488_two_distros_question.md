---
title: "two distros question"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by nmxdaven on 2011-07-14
Hey guys!

Have a question. May seem a bit elemental but I've never done it before so I want to make sure I get it right.

On my laptop I currently have Ubuntu 11.04 installed. Its partitioned as follows.

1. /boot 500mb primary
2. swap 3gb primary 
3. / 70gb primary 
4. /home a lot logical
5. The rest is unformatted free space.
Boot loader is installed in the default location

Now I want to install a different distro, namely backtrack 5. How do I make sure my Ubuntu install isn't fubard? I want to use the same swap space but thats it, the rest is to go on the unformatted partition. Any tips for making sure I don't screw up my install?

Thanks guys!
nmxdaven

---

### Post by Quackers on 2011-07-14
I'm not 100% sure but Backtrack has caused problems for some people. I believe it uses grub legacy as opposed to grub2 and this can cause a conflict of sorts. Try not installing Backtrack's bootloader at all, or install it to it's own root partition and use 11.04's grub to boot it.

---

### Post by nmxdaven on 2011-07-15
> **Quackers said:**
> I'm not 100% sure but Backtrack has caused problems for some people. I believe it uses grub legacy as opposed to grub2 and this can cause a conflict of sorts. Try not installing Backtrack's bootloader at all, or install it to it's own root partition and use 11.04's grub to boot it.

 So if I dont install its own bootloader I would just have to configure grub2 to reflect this?  thanks for the help!

---

