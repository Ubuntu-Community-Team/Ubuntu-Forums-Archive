---
title: "Help Partitioning Post-Install"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by Yayzik on 2006-08-26
I just started using Ubuntu on a machine I inherited that was previously running Windows XP. When I installed Ubuntu from the liveCD, I had it automatically partition it for me. However, I realized not too long later that the way it was partitioned was not suitable for how I wanted to use my machine.

I tried using QTParted, but on advice from an Ubuntu-using friend of mine, I decided to just reinstall Ubuntu, wipe the current Ubuntu partition and manually set up new sizes in the Wizard. I used GParted within the Wizard to set my partitions up like this:

Windows: 17.6 Gig
Ubuntu: 8.7 Gig
SWAP: 1.6 Gig

When I submitted that, and it took me to select where to mount the drives, the Windows reset to the setting I had before (about 20.5 gig), Ubuntu was smaller (5.2 gig or something), and SWAP was the same, 1.6 gig. Frustrated with trying repeatedly to fix this, I went ahead and partitioned them as it had suggested, with Windows huge, and Ubuntu small (allegorical, anyone?)

I threw GParted on my Ubuntu, and I booted from the liveCD, thinking I could just resize them from there, since the liveCD is being used, and not the actual partition. Here's my problem:

I can shrink down Windows to 17.6 gig, thus leaving me about 3 gig unassigned space. But, when I try to increase the size of Ubuntu, it doesn't give me that option. The max I can have is still 5.2 gig.

Any suggestions for remedying this without wiping out both Ubuntu and Windows XP and having to reinstall them both?

---

### Post by Herman on 2006-08-26
Hello, Yayzik, A new version of GParted that can move Linux partitions has been invented, but hasn't been released yet.
In the meantime, Linux partitions can not yet easily be resized from the start (left), only from the right (end), or moved. Will the information in the following link be of any help to you? (Click on the word 'Go').

**Okay, I want to resize my Ubuntu partition, how do I do that?**.................................[GO]("http://users.bigpond.net.au/hermanzone/p6.htm#Okay_I_want_to_resize_my_Ubuntu_partition_how_do_I_do_that")

That shows how to do it two ways, the simple way, you may need help to re-install Grub and edit /etc/fstab afterwards. You should be able to get help here in Ubuntu forums if you do need it.
Otherwise, the second method shown is a little bit more messing around, but you don't have to re-install Grub or edit /etc/fstab. Take a look and choose whichever method you like.
Another link you might like: [How to resize partition,    step by step]("http://gparted.sourceforge.net/larry/resize/resizing.htm")
These links are really about using [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), but the same information should also be useful for using the Ubuntu LiveCD with GParted in it.

Regards, Herman :D

---

### Post by GadgetsGuy on 2006-08-30
if you happen to have a dual boot with windows, Partition Magic will resize and move your /ext3 partition(s) effortlessly, and save alot of farting around with gparted and the sorts

just a heads up

Even though I run windoze in a VMWare server appliance, I have kept my dual boot just for the few little instances such as this where I know a windows tool that will get the job done without any greif.

:cool:

---

