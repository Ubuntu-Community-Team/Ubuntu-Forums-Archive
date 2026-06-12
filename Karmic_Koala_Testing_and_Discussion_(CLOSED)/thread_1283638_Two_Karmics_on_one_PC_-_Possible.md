---
title: "Two Karmics on one PC - Possible?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-05
I want to have 2 Karmic installs. 
 I know I will have to have 2 seperate volumes on the HDU, but can I just install it twice, on each?  Will GRUB2 find them?  I want to have the Beta and the Daily available and do some comparisons (and if I can do 2, I may want a third  for "possibly destructive tests").
Thanks!

---

### Post by slakkie on 2009-10-05
Yes it is possible. Why one would do that is beyond me though.

---

### Post by emarkay on 2009-10-05
> **slakkie said:**
> Yes it is possible. Why one would do that is beyond me though.

Like I said above - 2 versions for concurrent testing...  Jeez!

So, can you answer if GRUB 2 will "find" them?
Anything I need to know before I do this?

---

### Post by VMC on 2009-10-05
If you think about it, the answer will reveal itself. Many people, me included, have multiple distro's installed. What's the difference having two karmic's installed. None. The installer doesn't know one karmic from another.

---

### Post by Seventh Reign on 2009-10-05
> **slakkie said:**
> Yes it is possible. Why one would do that is beyond me though.

For the same reason we install and test the Alphas, Betas, and RC's.  Testing isnt done once the final release comes out.  

Personally I like to have 3 systems at all times. 

1, My stable system (aka my Jaunty system)
2, My Alpha/Beta testing system (aka my Karmic system right now)
and 3, my Stable + Proposed/Backports+ other special repo's system

---

### Post by emarkay on 2009-10-05
So to confirj - just have 2 partitions available and just install as normal, on the appropriate partitions and GRUB2 will find them?

It's just that simple?  :)

---

### Post by SigmaSanti on 2009-10-05
That should work, but grub will show them both as the same name (i think) which may result in confusion.

---

### Post by emarkay on 2009-10-05
> **SigmaSanti said:**
> That should work, but grub will show them both as the same name (i think) which may result in confusion.

I can rename them manually by editing GRUB - I figured I'd know which one was which by looking at the disc assignment data in the string.

---

### Post by SigmaSanti on 2009-10-05
Then you will have no trouble (hopefully) with your testing/experimenting/distromania :)

---

### Post by VMC on 2009-10-05
> **SigmaSanti said:**
> That should work, but grub will show them both as the same name (i think) which may result in confusion.

Only for the user, not grub. They will have different UUID's.

---

### Post by ranch hand on 2009-10-05
This is a bit of my 09_custom file (this type of entry works without updating it - ever);
```

#!/bin/sh
# This file is an example on how to add custom entries

echo "Adding KinkyA1 on sda16" >&2
cat << EOF
menuentry "KinkyA1 on sda16" {
        set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding DailyGrub on sda22" >&2
cat << EOF
menuentry "Adding DailyGrub on sda22" {
        set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding KinkyA4 on sda20" >&2
cat << EOF
menuentry "KinkyA4 on sda20" {
        set root=(hd0,20)
        linux /vmlinuz root=/dev/sda20 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Kinky Stoner1.0 on sda10" >&2
cat << EOF
menuentry "Kinky Stoner1.0 on sda10" {
        set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding KinkyStoner1.0 on sda6" >&2
cat << EOF
menuentry "KinkyStoner1.0 on sda6" {
        set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 so quiet splash
        initrd /initrd.img
}
EOF

```
These are all 9.10 variations, some clean installs, some upgrades.  One boots the internal drive they are on and my external (which boots by itself too).

I like have several because then I can concentrate on one method of breaking the buggers per install.

It is also interesting to note that just because you have two that are pretty much the same, say a couple weeks between 2 clean installs, they are not at all the same with daily updates.  There is usually a little difference in the number of updates per day, which packages are held back.  In a couple of weeks like we have had here recently, the buggers get pretty well buggered by someone trying to keep them going and it shows.

The difference between a clean install and an upgrade is quite interesting too.

---

### Post by VMC on 2009-10-05
> **emarkay said:**
> I want to have 2 Karmic installs. 
 I know I will have to have 2 seperate volumes on the HDU, but can I just install it twice, on each?  Will GRUB2 find them?  I want to have the Beta and the Daily available and do some comparisons (and if I can do 2, I may want a third  for "possibly destructive tests").
Thanks!

If you haven't already done this, I have a quick way of getting the second karmic installed in about ~5 minutes.

Use gparted from livecd like partedmagic and do a copy from installed karmic and paste to unallocated partition. The UUID's will get copied over also, so you need to use ```
sudo tune2fs -U random /dev/sdax
``` sdax being the copied partition.

They will then be identical. So from there you can keep one updated separately from the other.

That's how I did mine. I no longer keep the second one updated. I was using it as a backup for when updates crashed karmic;and they did. So I will probably use that partition for karmic+1

---

### Post by autocrosser on 2009-10-05
I also have 2 Karmic installs--I kept one updated a week after the other one as a "in case it broke" backup--only had to use it a couple of times this cycle, so I too will upgrade both to Karmic+1 as soon as the toolchain is uploaded----LET THE BREAKAGE BEGIN!!!!!! :P:P:P

---

### Post by VMC on 2009-10-05
> **autocrosser said:**
> I also have 2 Karmic installs--I kept one updated a week after the other one as a "in case it broke" backup--only had to use it a couple of times this cycle, so I too will upgrade both to Karmic+1 as soon as the toolchain is uploaded----LET THE BREAKAGE BEGIN!!!!!! :P:P:P
Are we there yet :) Oh. no. We have to wait for the final product. Then, hopefully I can push jaunty to the backseat and use karmic as my main squeeze while I play around with karmic+1 and find her dark secrets. (bugs). :lolflag:

---

### Post by DougieFresh4U on 2009-10-05
I the moment I have 3 Karmic, 32 bit & 64 bit and one 64 bit waiting for the repo's to open for Lucid.
I can keep track of which is which as in grub I see -  sda6, sda7, and sda8

---

### Post by autocrosser on 2009-10-05
> **VMC said:**
> Are we there yet :) Oh. no. We have to wait for the final product. Then, hopefully I can push jaunty to the backseat and use karmic as my main squeeze while I play around with karmic+1 and find her dark secrets. (bugs). :lolflag:
(Image of alpha-tester in a semi-dark corner)--LET THE BREAKAGE BEGIN!!!!! :lolflag:

I know it's not done til it's done, but I grow bored with how easy this cycle has been---altho' I fear that Lynx will naught more than a "safe ride" (secret wink that it's a rough/n/bumpy one!!!)  And before I hear the wags say that I shoud "try" something else---I have grown very fond of testing 'buntu--AH, I remember Warty & the earty head-bangin' days.....:P:P:P

Breezy--where are you now...........

---

### Post by slakkie on 2009-10-06
I know you said because you wanted two karmics to test. I don't see a real reason to have more then one karmic install on the same box. I can understand why someone wants to run Karmic on several PC's (with different hardware).

---

### Post by ranch hand on 2009-10-06
> **slakkie said:**
> I know you said because you wanted two karmics to test. I don't see a real reason to have more then one karmic install on the same box. I can understand why someone wants to run Karmic on several PC's (with different hardware).
WELL!!!!!!!!! I AM INDIGNANT.

Ok, not really.  As Bob Dylan said "ain't no use talkin' to you, it's just like talkin' to me" about what a dull place the world would be if we were all the same.

I only have, currently, 5 32bit versions and 6 64bit versions (I can run this box either way) and think it is just about the perfect number.

There are a lot of folks, generally and here on the forums, that play computer games.  For the life of me I can not fathom this at all.  I, on the other hand, play games with my computer.

---

### Post by slakkie on 2009-10-06
LOL, you have 11 different installations on the same box? Epic. You run all the Ubuntu supported releases??

I don't like to waste that much space on various releases/distro's. Can only run one at a time. If I want to play with other distro's I'll use a virtual machine.

But he! Don't let me stop you, I just made a comment that I don't understand why people do it. I'm not saying DON'T do it :) Whatever makes you feel happy.

---

### Post by VMC on 2009-10-06
> **slakkie said:**
> LOL, you have 11 different installations on the same box? Epic. You run all the Ubuntu supported releases??

I don't like to waste that much space on various releases/distro's. Can only run one at a time. If I want to play with other distro's I'll use a virtual machine.

But he! Don't let me stop you, I just made a comment that I don't understand why people do it. I'm not saying DON'T do it :) Whatever makes you feel happy.

I think most of Ranch Hands 12 distro's are variations of the same distro. Namely Ubuntu.

The problem with only using VM's is that you can't really test your hardware. Using a VM, I wouldn't have found out that Fedora-11 Intel video works perfectly, unlike Ubuntu. Also PartedMagic is using X Server 1.6.4 AND Intel driver 2.9.0, and it works perfectly for my computer, which has Intel i865 video chip.

---

### Post by slakkie on 2009-10-06
I realize that by using a VM I don't actually test an OS on my hardware, but I have no intention of switching to another distro. So I don't really care if it is or isn't working on my hardware.

But putting the same release of a certain distro on the same hardware isn't really helping either, you are testing the same thing twice. If someone multiboots Fedora Rawhide and a Ubuntu development release it makes sense, to me at least.

But I'm hijacking this thread, so I'll shut up now.

---

### Post by kansasnoob on 2009-10-06
> **ranch hand said:**
> WELL!!!!!!!!! I AM INDIGNANT.

Ok, not really.  As Bob Dylan said "ain't no use talkin' to you, it's just like talkin' to me" about what a dull place the world would be if we were all the same.

I only have, currently, 5 32bit versions and 6 64bit versions (I can run this box either way) and think it is just about the perfect number.

There are a lot of folks, generally and here on the forums, that play computer games.  For the life of me I can not fathom this at all.  I, on the other hand, play games with my computer.

This, "I, on the other hand, play games with my computer.", pretty well sums up my favorite hobby!

If I'm multi-booting any less than 4 distros I get absolutely bored to death. Sometimes I learn something on one distro that I then try to figure out on another. I just love to try and get things working, then once I get everything working I soon become bored and blow everything all to pieces!

My youngest son loves video games but he's constantly frustrated because a new game will be either too simple or too difficult. Now, I get frustrated sometimes and have to remind myself it's time to just go back to what I know works for a day or so, but for the most part I just love learning to do knew things.

Whenever possible I'm now trying to focus on the whole bug report scenario, something that still quite often baffles me!!!!!!!!!!!!

Anyway, sorry for the hijacking, but I always multi-boot:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2104    16900348+   7  HPFS/NTFS
/dev/sda2            2883        9729    54998527+   5  Extended
/dev/sda3            2105        2882     6249285   83  Linux
/dev/sda5            4214        5012     6417967+  83  Linux
/dev/sda6            5013        7434    19454683+  83  Linux
/dev/sda7            7435        8199     6144831   83  Linux
/dev/sda8            8200        9576    11060721   83  Linux
/dev/sda9            9577        9729     1228941   82  Linux swap / Solaris
/dev/sda10           2883        4213    10691194+  83  Linux

Partition table entries are not in disk order

Great fun!

---

### Post by ranch hand on 2009-10-06
Nope, those are the 9.10 veriatations.  I also have Debian (lenny) and PhatDebian(beta) which is lenny with the 2.6.30 kernal (very nice).  I have the 32bit Mandriva2009-0 both Gnome and KDE.  Mandriva 2009-1(spring) in 64bit in Gnome and what I call "both".  It is a cool way to distribute your OS.  Large LiveDVD has the option to install as Gnome, KDE, Lxde or all of them at once (choice at login, of coarse).  I like Lxde and pcmanfm.

While I spend most of my time on one 9.04 OS, my "main" where we do banking and business is Hardy.  I like LTS.  I am excited, because of 9.10, about 10.04.  I think it ought to be REAL NICE.

I have a number of 9.04 clean and respins, 32 and 64bit.  Mainly Stoner Edition1.0 and 1.1 an SuperOS.  In spite of the name, Stoner Edition is a very nice OS with really slick artwork (theme may not be suitable for homes with small children or the office).  SuperOS is alright but it does not upgrade to 9.10 well at all, at least on this box.

I can't get a Lubuntu LiveCD that will install, I want one.  I also want Sid.  Sidux did not impress me.

I don't like the RPM system but I do like Mandriva in spite of it.

I have hopes of testing another Ubuntu respin but do not know if it is for public knowledge right now or not.

I do like Ubuntu and it's offspring and Debian a LOT.  I have learned that Ubuntu is an old african word for "can't configure Debian".  I just don't see Debian as hard to configure but that is what some folks say.  I like a saying that makes me grin.

---

