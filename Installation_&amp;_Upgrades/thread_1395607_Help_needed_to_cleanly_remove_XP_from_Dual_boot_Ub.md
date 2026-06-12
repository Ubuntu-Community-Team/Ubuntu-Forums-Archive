---
title: "Help needed to cleanly remove XP from Dual boot Ubuntu laptop."
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by solorize on 2010-02-01
Hi,

I recently bought a refurbished HP Compaq NC6000 which had a new installation of Win XP put on it but takes about 5
attempts to boot up as it just sat at the load screen and freezes.

So I decided to install Ubuntu 9.10 as a Dual boot with the view to getting rid of XP once I had Ubuntu up and running,
which I have now. So cant understand why XP wouldn't work lol.

Now I would like to fully get rid of XP and just have Ubuntu as the only OS on the laptop.

Currently as it is Dual Boot I have my 80gig Hard drive partitioned with both OS’s on it.

Could someone point me in the right direction of how to get rid of XP cleanly so I just have Ubuntu left on my machine.
I don’t really want to re-install Ubuntu as I have spent the last week getting it set up, so would it be possible
just to get rid of XP?


Also would getting rid of XP mess up the Grub Boot loader menu?


Thanks

Mark

---

### Post by darkod on 2010-02-01
Reinstall on the whole disk would be good because you will have all space allocated to / for example.
On the other hand, you can always create ntfs or ext4 partition in place of the current XP partition and use it however you want.
Nothing easier than getting rid of XP. Boot ubuntu and open Gparted (you might need to install it first). Then just format the XP partition as ntfs if that's what you want, or delete it and create ext4 partition in its place.
Since you did a clean install of 9.10 and you have grub2, all you need to do is run:
sudo update-grub

and that will delete XP from the boot menu because after formatting the XP partition it will not be detected any more.

---

### Post by solorize on 2010-02-01
Darkod,

Thanks for your prompt reply.

I will have a go tonight as have had enough
of Windows.

btw. I could not believe how much faster booting up / running
& shutting down Linux is over Windows. Just proves how much
of a bloated OS Windows is =)

Thanks again,

Mark

---

### Post by solorize on 2010-02-02
Once quick question:

I have now deleted the windows xp partition so now
have unallocated space.

Last night I tried to re-size my existing linux partition
(using Gparted LiveCD), to use the unallocated space,
by dragging the partition to the left to use the
unallocated space.

( I am not at my laptop now so dont know the exact names
of the partitions .i.e /dev/sda1 etc..)


before:
[ unallocated space][..........linux partition..........][]

after:
[..............................linux partition......................][]


All looked good, as the procedure started and it gave me
an estimated time to finish of just over 6hrs, so let it
run overnight.

This morning I had a look and there was a message screen
saying an error had occured, but did not give a discription.
And the linux partition had reverted back to its origional size
and the unallocated space was still there, as displayed below.


[ unallocated space][..........linux partition..........][]


Does anyone know if I am going about this the wrong way?
i.e should I make the unallocated space into "ext4" 1st
and then resize the linux partition?

Any pointers would be greatly appreciated, as still just
finding my feet with linux.

Regards,

Mark

---

### Post by darkod on 2010-02-02
If you want to expand neighboring partition, the space needs to stay as unallocated. But I have no idea why it didn't work.
Because of this I said reinstalling on the whole hdd is preferred option. Something can get corrupted easily during partition resizing.
You could also try Gparted from the ubuntu cd, booted in the live desktop (obviously you can't expand from your hdd ubuntu when it's booted up).

---

### Post by Shark_AtK12 on 2010-02-02
If its not a big hassle i would just reinstall Ubuntu on the whole HDD. Also if you do this, then make your /home on a seperate partition to make it easier when reinstalling/upgrading.

---

### Post by solorize on 2010-02-02
Thanks Darkod & Shark_atK12,

If I  keep this “unallocated space” and just format it to say ext3.

**1.**
what steps do I need to do to put my /home onto it.

**2.**
Does it matter that this new partition is the first partition on the HD?
i.e. before one with Ubuntu on.

**3.**
If I decided to reinstall ubuntu (after deleting partitions/ formatting the whole HD)
so the HD just had one partition on it (i.e. not moving the /home on to a separate partition).
If in the future I “upgraded” my version of Ubuntu would it loose all my files etc.. or
would that only happen if I did a complete “re-install”.

Sorry for all these questions!

Regards,

Mark

---

### Post by Shark_AtK12 on 2010-02-02
From what I understand, (as i am still new to Linux) the /home is where all your media(music,vids, pics, documents,ect) get saved +configuration files. I have my boot setup this way:
 
10-15gigs for Root (/)
4gigs for Swap
rest on /home
 
Mind you this is on a 250gig HD.
 
If it works like i think, then putting the root drive first puts it in the beginning so it will be accessed quicker. And to answer your last question, yes, when doing a clean upgrade/install(which is recommended) you wont lose your personal files and most configurations.
 
Hopefully that all makes sense. Im getting ready to come off a 12 hour night shift.

---

### Post by darkod on 2010-02-02
Upgrade to the next version will keep your home folder intact, but it can also create issues later (or immediately after the upgrade).
Clean install is always preferred but it will delete your home folder unless it's a separate /home partition.
Being first doesn't matter much. You could format it as ext3 or even ext4 and then make it your /home partition, but I haven't done that myself. There should be plenty of guides on google though.

---

### Post by oldfred on 2010-02-02
This is a good guide on moving /home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
and if you get the dmrc error.
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by solorize on 2010-02-03
Thanks again to everyone who has posted comments.

I decided to bite the bullet and got rid of everything
and did a fresh reinstall of ubuntu 9.10

I set up a seperate partition for / and for /home and 
also swap space.


Only thing is now I dont get the Grub load menu
when it boots, it just loads straight into ubuntu.

Does anyone know how to get Grub to display again?

Also, when I created the partitions I did them as "EXT3" and
not EXT4 as I read somewhere that EXT4 is not as stable, is
this true?

Regards

Mark

---

### Post by darkod on 2010-02-03
Any reason you would like the grub menu to hold you up? When ubuntu is the only OS the menu doesn't show because you don't have another OS to select.
In 9.10 you can bring up the menu by pressing Esc during boot but you have to be quick to catch it before it starts actually loading ubuntu.
Also, there are some parameters in /etc/default/grub that can make the menu show, you can read more here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by solorize on 2010-02-03
darkod,

Thanks for letting me know, I thought I had
messed up the install somehow ;-)

As I was re-installing at about 12:00 last night 
and was not 100% alert to what I was doing.

Cheers,

Mark

---

