---
title: "What I learned about raid + ubuntu"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by sbenz on 2007-01-11
I just spent the last week (literally) wrestling with fakeraid and software raid in a variety of configurations on a couple different machines.

My original goal was to setup 2 different machines - a sata raid5 server for my parents (4x500gig drives) and one for myself (3x320gig drives)

Here are a couple lessons I learned in the process (in hopes this may help someone in the future):

1.  **If you have a choice between fakeraid and software raid, go software.**  One of the mobos i got had an nvidia chipset with raid 0/1/5 on it...  it looked great on paper, but turns out it was a so-called "fakeraid" chip which relies on both the bios and the driver in order to display correctly.  [[COLOR="Blue"]dmraid [/COLOR]]("http://people.redhat.com/~heinzm/sw/dmraid/readme") supports nv_raid (which is the fakeraid used by the nvidia chipsets), but only the most recent ALPHA version supports raid 5 on this chipset (and a few others).
Software raid literally took maybe 10 minutes to partition and format the 4x500 gig drives, and they are still extremely fast.
IMO, the only reason to go fakeraid is if you've already installed windows and CAN NOT afford to lose the data.  If that is the case, i hope you went either raid0 or raid1... [[COLOR="Blue"]this guide[/COLOR]]("https://help.ubuntu.com/community/FakeRaidHowto") will help guide you through the pains

2.  **If you're looking to buy parts to setup a raid system, just buy a controller card, not a raid card.**  Unless you're going to fork down the cash for a [3ware ]("http://www.3ware.com/")card, your money is better spent buying drives and/or a nice controller card.  If you have the ports to support the drives you have, then you don't even need the controller card.  Save yourself some cash and just go software raid.  Chances are the only people that will even need a hardware raid solution are the ones looking to install a serious server setup. (I ended up buying a promise sata300 tx4 for my machine cause it was an older mobo with only 2 sata ports - great card, it just works with no extra configuration - assuming you're going installing Dapper or later)

3. **Don't try to install grub on a raid5.**  This was the final mistake I made.  Grub and LILO have issues with raid5.  It may be possible, I'm not completely sure - but I spent way too much time trying to get it to work.  Make a 250 meg boot partition on the beginning of the drives in a RAID1 configuration.  This is *really* easy with software raids, and will probably save you a headache at the end of the install process.

---

### Post by rustybutt on 2007-01-18
I picked up some el-cheapo EIDE 250GB Western Digital drives last summer.  I hung them off of a Promise IDE controller and used software RAID to set 'em up as a RAID 5 array.  That went easy.  Real easy.  

But then the Promise card locked up with DMA timeout errors.  The whole thing went blooey!   ****...

So I picked up another new Taiwan IDE card, which ended up having no suitable driver.  Next up was a current Adaptec card, which did work, sort of..., except that it decided to take ownership of hda, hdb, hdc an hdd.  I fiddled every which way I could, but then said to hell with it and just used all the drives as regular drives.  I used two drives as data drives and the other two were backup drives that I ran a nightly rsync to.  Ugly but effective.

Since then 3 of the 4 drives have died and the last one is starting to show seek errors.  I grabbed a spare Seagate drive and am living off of that for the moment.

I was surprised to find that Western Digital has no manufacturer's warranty on these things, so it's to electronic recycling they go.

Time to do something different.  I could just get some Seagate IDE drives, but I'd be up for going SATA at this point, hence my reading your post.  

What brand of SATA drive controller are you using, or will any old SATA drive controller work well enough for me to use software RAID?

---

### Post by perimere on 2007-03-03
Personally I set up the following config months ago and have had zero issues so far:
Highpoint RocketRAID 2320 card, with 4 x 500GB SATA II WD500YS drives in a RAID 5 config.

Highpoint provide linux source to patch your kernel with. Recompile the kernel with the new driver (I had no major issues there) and then I was away with 1.5TB of usuable space.

I have a 40GB SATA drive I use for the Ubuntu OS, and everything works sweet. 

Not a cheap solution by any means - I blew just short of 800 quid. Not being funny though, if you want a reliable RAID 5 solutions that doesn't crap out on you after 4 weeks, it's going to take a bit of cash ;)

HTH

---

### Post by gurgle on 2007-03-08
> **sbenz said:**
> 

3. **Don't try to install grub on a raid5.**  This was the final mistake I made.  Grub and LILO have issues with raid5.  It may be possible, I'm not completely sure - but I spent way too much time trying to get it to work.  Make a 250 meg boot partition on the beginning of the drives in a RAID1 configuration.  This is *really* easy with software raids, and will probably save you a headache at the end of the install process.

I am going to have a setup like this:

1 40 gig IDE drive for ubuntu-server
4 SATA HD's, ranging from 250-400 gb

Is this easy to set up? I want to install ubuntu on the 1 drive and then RAID5 the sata drives. Also, is it "easy" to add drives later on if need be?

---

### Post by Justintoxicated on 2007-03-08
Thanks for the advice, I just bookmarked this thread.

I have a few options which would be best?  This is an old computer with only IDE support.

I want a Raid1 Setup.

I have a Highpoint Rocketraid 404 card.

or

Ancient Abit Motherboeard also has onboard Raid HPT370 controller. (not sure if this is fakeraid or not)  it is old...

or

Softraid? - is there a guid to set this up because I have no idea.

Thanks,

---

### Post by gurgle on 2007-03-08
> **Justintoxicated said:**
> Thanks for the advice, I just bookmarked this thread.

I have a few options which would be best?  This is an old computer with only IDE support.

I want a Raid1 Setup.

I have a Highpoint Rocketraid 404 card.

or

Ancient Abit Motherboeard also has onboard Raid HPT370 controller. (not sure if this is fakeraid or not)  it is old...

or

Softraid? - is there a guid to set this up because I have no idea.

Thanks,

check out our discussion here:

[http://ubuntuforums.org/showthread.php?t=319910](http://ubuntuforums.org/showthread.php?t=319910)

---

### Post by Justintoxicated on 2007-03-08
> **gurgle said:**
> check out our discussion here:

[http://ubuntuforums.org/showthread.php?t=319910](http://ubuntuforums.org/showthread.php?t=319910)

I don't follow thats a link to how to get Raid-5 working?  I just want to Mirror...

---

