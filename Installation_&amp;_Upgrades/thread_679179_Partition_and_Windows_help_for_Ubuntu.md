---
title: "Partition and Windows help for Ubuntu"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by zapoqx on 2008-01-26
Hello all
Its been a while since I posted because I had issues and decided to take a break from ubuntu and come back at another time.
I notice the install is much different and the problem is, all the options seem to want me to destroy my hard drive setup I was trying to make.
I installed Windows and made it 100GB.
I reserved 50GB to be for Ubuntu and left it unpartitioned.
The problem was, when trying to install it, it wanted to format my Windows XP partition on all the options (obvious exception being the manual).
 
So I know I need ext3 and Swap. The sizing on Ubuntu I have no idea on and I'm not sure but I thought I need a /boot or something for the option to go to Windows or Ubuntu.
 
If basic specs are needed for my laptop, it is:
1.8GHZ
2GB Memory (128MB Vid shared)
1 Hard drive (100GB to Windows, 50 for Ubuntu)
 
I've read the partitioning basic so For the basics, this is my understanding...
2GB for Swap
38GB for ext3 /
10GB for ext3 /data
 
Is that it or am I missing anything?

---

### Post by Pumalite on 2008-01-26
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize your XP partition. A good scheme for your new partition:
10 GB for '/'
1 GB for /swap unless you have a laptop, where /swap=RAM
The rest for /home
Then install Ubuntu, go Manual and use partitions already made.
Don't forget to backup everything.

---

### Post by logos34 on 2008-01-26
> **zapoqx said:**
> 
2GB for Swap
38GB for ext3 /
10GB for ext3 /data

You don't need a separate /boot.

But reverse the / and /data -- i.e. 

38GB for ext3 /data
10GB for ext3 / (--> actually, even 10 is probably more that you need with a separate data partition.)

You might look into a [separate /home]("http://psychocats.net/ubuntu/separatehome") instead of /data.  Then you can surely reduce the size of / down a few gigs.

EDIT: looks like pumalite was faster on the draw

---

### Post by zapoqx on 2008-01-26
Resize my XP partition? Wouldn't that possibly corrupt the main partition though?

---

### Post by Pumalite on 2008-01-26
Here you have something to read:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by erfahren on 2008-01-26
I guess Pumalite didn't catch the part where you said you left 50GB unformatted

when using the LiveCD go with the "Manual" partitioning option. Make an extended partition out of the free space, then create logical ones inside it the way Pumalite laid out. (With that partitioner you might not need to create an extended partition first - just create your root ( / ), /home and swap as logical partitions.)

see hermanzone's page on partitioning for more info: [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning) (it talks about the AlternateCD, but the basics are still the same).

---

### Post by zapoqx on 2008-01-26
I got it up.  Sorry I didn't reply sooner.  Just running into a Wireless weirdness.  Thanks for the help.
But while I have this, there is one other weirdness.  I know seeing on a few other people's Ubuntu setup that when choosing the operating system, choosing Ubuntu, it should show the Ubuntu logo as well as what is being loaded up.  After choosing it on my end, it doesn't show anything visually so it makes me think that my system froze or something.  I don't know what is up with that so any help is wonderful.

---

### Post by erfahren on 2008-01-26
> **zapoqx said:**
> I got it up.  Sorry I didn't reply sooner.  Just running into a Wireless weirdness.  Thanks for the help.
But while I have this, there is one other weirdness.  I know seeing on a few other people's Ubuntu setup that when choosing the operating system, choosing Ubuntu, it should show the Ubuntu logo as well as what is being loaded up.  After choosing it on my end, it doesn't show anything visually so it makes me think that my system froze or something.  I don't know what is up with that so any help is wonderful.
It sounds like what you are saying is that after you boot into Ubuntu from the boot menu you just get a black screen (with no "splash screen" and the progress bar)? 

If this is the case and it also seems like it takes too long to boot it could be the problem with usplash.
see: [http://ubuntuforums.org/showthread.php?p=4188775](http://ubuntuforums.org/showthread.php?p=4188775)

---

### Post by zapoqx on 2008-01-27
Yep.  That's it alright.  Thanks, that did the trick!

---

