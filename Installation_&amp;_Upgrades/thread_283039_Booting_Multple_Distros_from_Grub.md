---
title: "Booting Multple Distros from Grub"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by jeradzan12 on 2006-10-23
Hi everybody ,

I hope you can help me].  I haven't found the answer I need in the forums so far.  I love Ubuntu and linux in general.  What I want to do is expand and apply what I have learned to other linux distros.  I want to run them all from a single PC and use grub to boot each.  2 questions: Is this possible, and if so, how would I go about setting this up?  I will be using a single 200GB hard drive.  It currently has Vista RC1 and Ubuntu 6.10 beta installed.  I was looking at possibly adding Mac OS x86, Solaris 10, and/or Fedora Core 4.

Thanks!

---

### Post by bulldog on 2006-10-23
GRUB will be overwritten every time you do a new install.

But it should be up to date then so no trouble I guess.

As long as you use distro's with GRUB ofcourse :D

---

### Post by Kateikyoushi on 2006-10-23
Osx won't install grub so you have to add it manually.

Similar to the win entry. [LINK]("http://fredcpp.wordpress.com/2006/04/03/multiple-boot-with-grub-adding-mac-os-x/")

---

### Post by slapout on 2006-10-23
It is possible to do (I've done it before). There was an article in TUX magazine that explained how. I don't have the link handy, I try to find it and post it when I get to work tomorrow.

---

### Post by Irony on 2006-10-24
> GRUB will be overwritten every time you do a new install.

No it won't. When it comes to the installing bootloader stage in each distro then simply choose the option not to install - this leaves the Ubuntu GRUB intact (regardless of whether each distro uses GRUB as a default bootloader).

After installing go to your /boot/grub/menu.lst in Ubuntu and add entries for each distro, for example;

[PHP]# This entry added by me as an example
# installation on /dev/hda9
title		Fedora Core 4, hda9
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.11-1.1369_FC4 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd-2.6.11-1.1369_FC4.img
savedefault[/PHP]

To find the root path for each distro simply mount each distro and navigate your way to each kernel/initrd file in the /boot folder.

Note each Linux distro can use the same swap space, you don't need multiple swaps.

---

### Post by slapout on 2006-10-24
Ok, I found it. It's in Tux Magazine Issue 8. The article is entitled: Give Multiple Distros the Boot--How to boot multiple Linux distributions. (page 31). 

You can get it from here: [http://www.tuxmagazine.com/node/1000163](http://www.tuxmagazine.com/node/1000163)

Although I think you have to do the free signup thing.

---

### Post by jeradzan12 on 2006-10-25
Thanks everybody for all of your responses.  I won't get a chance to try eveerything for a few days since I am now in the middle of moving.  But I should be able to do it sometime this weekend and will post my results and any further questions I may have.


Thanks for the link Slapout.  I am a subscriber to TUX but don't get much time to read.  I guess now I will have to find the time!

---

### Post by jeradzan12 on 2006-11-09
You know, I tried to do the install of the other distros and couldn't do it.  I can only have a maximum of 4 partitions, which I already have - XP, Vista RC1, Ubuntu, and the Swap.  I don't want to risk losing m data so I guess I will have to find another way for now until I can get another hard drive....

---

### Post by ascherjim on 2006-11-26
Slapout:  I came across your reference to the TUX article, which I downloaded today.  It's great and seems to answer all my questions and gives me clear guidelines on how to proceed.  I'd previously pieced together rasndom bits of useful information on this subject from other forums, but the TUX article wraps it all up and then some.  Thanks.

---

