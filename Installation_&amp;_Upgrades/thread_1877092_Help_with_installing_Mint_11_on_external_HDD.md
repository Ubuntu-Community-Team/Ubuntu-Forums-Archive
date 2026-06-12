---
title: "Help with installing Mint 11 on external HDD"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by CJ-1990 on 2011-11-07
Heya doods and doodettes :)

I haven't been on here for ages lol, finally installed Ubuntu on my netbook, everything is fine and dandy there :)

My current problem is, I am running Ubuntu Netbook Remix Natty, but I'm also interested in Mint, I am keeping Natty on my internal drive, but I want to install Mint on my external, as an alternative to Ubuntu when I feel like it :)

I am still somewhat of a noob when it comes to Linux, I am learning fast, but I just wanted to ask somebody who knows what they're doing so my internal drive doesn't get affected negatively :)

Can anybody provide me with a step by step guide to installing Mint on my external HDD? I have heard it is quite difficult sometimes.

Thankyou for any help you can give me :)

Cheers (Y)

CJ

---

### Post by oldfred on 2011-11-07
I do not know Mint, but this is a good reference on how to install to a second drive. The important thing is to use manual install so you get the choice to install grub2's boot loader to the MBR of the external.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by ajgreeny on 2011-11-07
It shouldn't be difficult.

You will need to choose the "Something Else" option at the disk preparation stage of installing, then make absolutely sure you choose the correct device and partitions to install to.  On that page (I think) there is also a box where you can choose where to install the bootloader (grub2 in this case) and again you must be absolutely sure you put Mint's grub onto the root of the external disk, not onto a partition such as /dev/sdc1, but to /dev/sdc;  (sdc here is just an example, yours may be different.)

Apart from that there should be little difference installing to an external disk vs an internal one;  just make sure you get the correct device, and that you put grub on the root of the same device and not onto your internal disk.

---

### Post by CJ-1990 on 2011-11-07
Thanks for the help doods :)

A warning message comes up when I go into the "Something else" option and select the appropriate drive...
It says "The root file system is not defined" As I said before, I am a bit of a noob when it comes to linux though I can learn fast :)

What do I have to do to "define" the root file system? 

Thanks again :)

---

### Post by oldfred on 2011-11-07
You have to create partitions with manual install or have partitions already created and choose which to use for / (root). It finds swap automatically if created in advance, otherwise you should create it also.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by CJ-1990 on 2011-11-07
Aha! Thanks a bunch to everyone who helped :) 

I am going to try again tomorrow, and if I succeed I will defs mark this post as solved :) 

I don't use windows anymore lol, apart from fixing my family's and sister's windows computers for them... I'm fully Linux now :D 

I understand what the home and the other directory is for, but what does swap do? Is that basically the Linux equivalent of a paging file in windows?

Thanks a bunch to all who helped :)

I am proud to be a part of such a helpful community :)

Cheers (Y)

CJ

---

### Post by oldfred on 2011-11-07
Swap is for RAM memory overflow, if you load too many programs or data at once. With 4GB or more of RAM it becomes difficult to actually use swap. Video editing or maybe using every program may start to use swap. You really do not want to use swap, as it is very slow, but it is good to have some just for system startup (looks for it until it times out) and just in case something large gets loaded.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by CJ-1990 on 2011-11-08
Heya peeps :) The installation went well, everything is set up on my HDD, but when I go to boot from it, it comes up with a menu which I have to select from ie, mint normal, mint safe mode and such...

I pick the top one, it looks right, exactly what I want to boot, but when I select it, it just goes to a black screen and doesn't do anything...

When I boot up ubuntu with my HDD attached it comes up with the same menu, I pick the top one and boom, it boots properly, I'm typing from unbuntu now...

What went wrong? And how can I fix it? I followed your instructions, specified the partitions properly, made the first 10gb of space the /root, the all of bar 2bg the /home, and the last 2 gb is swap space...

Thanks for any help you can give me :)

CJ

---

### Post by KBD47 on 2011-11-08
I don't know if this will help you, but here is what I did tonight to install Xubuntu 11.10 to a 16 gig usb stick which is similar to installing Mint to an external hard drive:

I used gparted to format the drive, erasing everything off it first, I set two partitions:

swap (set it to twice your computer's ram, i.e. you have 1000 mb ram, set swap for 2000 mb).

ext 4 / (make sure you have it labelled with (/) and set it for the space needed or available space i.e. 10 gig.)

boot up a live cd of Xubuntu (in your case Mint) and click install, follow along until you get to where it asks you to install and choose "something else" and choose that ext4 hard drive. It may ask you to unmount it to edit it, in 11.10 I had to click on edit it and labelled it ext4 again and set (/) after that I could install it. In Mint 11 you may also have to point it to your external hard drive for installing grub. Take your time, be careful, make sure you've got everything backed up, and don't take my word for gospel, look at what others say as well. I wish you good luck.
KBD47

---

### Post by CJ-1990 on 2011-11-08
Thanks for the info dood :)

Here's what I did:

First partition is for the install, 10gb, ext4, and /

Second partition is the /home ext4, all but 2 gb worth

Third partition is the swap space which is a lil over 2gb, my ram is 1gb btw


Everything worked out good, installed properly, didn't get any other error messages...
Though when I go into the BIOS boot menu and select my HDD, it does start booting, but then goes to a black screen.

Now I know that Mint 11 has no splash screen for certain reasons, but the screen stays black for over 10 mins without doing anything, I'm thinking that's a tad too long to boot lol...


As for the grub, I didn't get any message or option about grub when I was installing, could that be why it's not booting? If I need to configure grub to the appropriate area, how would I do that?

Thanks for any help you can give me :)

CJ

---

### Post by KBD47 on 2011-11-08
You can use a live cd or a computer with a system already on it and plug in your hard drive, then open gparted and select your hard drive to see what it looks like. Post a screen shot of it here and you should get help. That first ext4 / partition should have boot at the end of it when you look at it in gparted. My guess is that maybe you didn't point the installer to your hard drive to install grub during installation. Hopefully folks who know more than I do will chime in.
KBD47

---

### Post by CJ-1990 on 2011-11-08
I've attached a screenshot of my external hdd in gparted, it all looks good, which is why I'm confused lol... At the end of the /root ext4 partition it says boot...

If anyone could give me instructions on how to properly direct the grub boot loader onto my external hdd it would be much appreciated.

Cheers :) 

CJ

---

### Post by KBD47 on 2011-11-08
> **CJ-1990 said:**
> I've attached a screenshot of my external hdd in gparted, it all looks good, which is why I'm confused lol... At the end of the /root ext4 partition it says boot...

If anyone could give me instructions on how to properly direct the grub boot loader onto my external hdd it would be much appreciated.

Cheers :) 

CJ

It looks correct to me as well. I hope others will chime in with ideas to help. If your iso was good, and if grub installed correctly, it should boot OK.
KBD47

---

### Post by CJ-1990 on 2011-11-08
Thanks for tryna help anyway dood :) Really appreciate it aye

Everything looks good on my HDD, no idea why it won't boot properly, the boot menu does come up with normal mint and recovery mode mint + other options...

It's not absolutely needed on my external, I'm just doing this to broaden my linux knowledge and learn about how to tweak and get into the nitty gritty of linux :) But it still frustrates me that it should work, but it's not...

Would not having grub installed properly or in the right part stop it from booting properly? 

I used recovery mode and had an option to load another grub, could that maybe help get it to where it needs to be?

---

### Post by CJ-1990 on 2011-11-08
So, apparently, after searching google for my problem... The GRUB does load, when I boot from my HDD the GRUB menu comes up and gives me a fair few options... But when I select the option to boot the first which is Mint 11, it does not do anything, it goes to a black screen, the indicator light on my hDD goes off indication that it is loading, but nothing initialises... I left it for a good 30 mins and still nothing booted...

Could that be a problem with the version of my GRUB? A corrupt GRUB? 

I can get into and boot the recovery mode option which has an "update GRUB' option, would that fix my problem?

As a last resort should I re-install Mint? Would that maybe help?

Cheers for any info you can give me, kinda stuck atmoe lol

Cheers

CJ

---

### Post by ajgreeny on 2011-11-08
I sounds to me as if grub was installed on to the internal hard disk in the machine, not to the external disk.  If you did not set the external as the site for bootloader files, that is where it will be, and it should not be there;  grub must be on the external disk to do what you want.

What happens if you boot up without the external disk attached?  I suspect you will not get a grub menu or anything, just a grub prompt, and then nothing more will happen.  Try it and report back.

---

### Post by CJ-1990 on 2011-11-08
When I boot up without the external attached it just boots up normally, no grub menu :)

I'm gonna try doing a boot repair and see if that works, hopefully I'll be able to put the grub in the right place this time lol...

---

### Post by ajgreeny on 2011-11-08
With the external disk attached you could run ```
sudo update-grub
``` to see if it adds Mint on the external disk to the grub menu.  If you don't see a grub menu still hold shift at boot and it should show.  You can also see if mint has been added to the menu by running command ```
grep menuentry /boot/grub/grub.cfg
```from your ubuntu, which will show all the grub menu entries listed.

---

### Post by CJ-1990 on 2011-11-08
Thanks a bunch to all who helped me, really appreciated :)

I did a fresh install of Mint 11 on my external HDD and configured the partitions properly, and installed the GRUB to the MBR of the external HDD and it worked, I logged into it and ran my wireless net through it before :)

Again, thanks a bunch to ALL who helped and/or tried to help :)

I will now mark this thread as solved

Cheers

CJ :)

---

### Post by KBD47 on 2011-11-08
Excellent! Glad to hear you got it working :-)

---

### Post by CJ-1990 on 2011-11-09
As I reply now, I am using Mint 11 off my external HDD :D 

The install worked perfectly, the only thing wrong with the original install was that I didn't install the grub boot loader into the right partition haha, just a silly mistake :P

Thanks a bunch to ALL who helped or even tried to :)

I am amazed at the speed in which my question was answered, fantastic forum you guys have got going here :)

CJ

---

