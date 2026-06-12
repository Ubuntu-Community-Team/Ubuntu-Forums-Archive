---
title: "Suggestions welcome for possible hard-drives setups"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Corvo78 on 2007-02-21
I'm ready to take the leap of faith - after test-driving Ubuntu on my Laptop, I'm convinced my desktop is ready for a change of OS.
More often then not, a Desktop's setup is more complex than a laptop's setup...

I wouldn't mind getting some suggestions on how others think I should setup my hard-drives (for use in Edgy).
First of all, these are the drives I have:[list=1][*]A 300GB or 200GB SATA *(Either the 300GB or the 200GB drive will be used to dual-boot into Windows... for gaming.)*
[*]Two 250GB SATA drives which I intend to FakeRAID with my NVidia NForce4
[*]A 500GB SATA[/list]
Basically what I had in mind was this:[list=1][*]Use the 300GB as **/**
[*]Use the 250 GB mirror as **/home/**
[*]Use the 500 GB as **/home/videos/**[/list]Which, for an ex-Windows user, seem like a plausible Linux setup :) 



Although a few questions would remain:[list=a]
[*]Which drive would be suited best to have the Swap-partition?
[*]Isn't 300GB for root (excl. everything from /home) a bit too much? Something tells me 200GB will do just-as-well and (the resource hungry) Windows probably likes 300GB better...[/list]

So, obviously my biggest question is: How would you setup my drives?
And even more impotant: What's the easiest way, for an Ubuntu-newbie like me, to do this?


I thank everyone in advance for any knowledge/experience they would like to share!

---

### Post by louis_nichols on 2007-02-21
I suggest using LVM. It will have a learning curve, but the advantages later are great. Especially if you use reiserfs filesystem.

Basically, what this means is that you can configure logical volumes and resize them online later. For example, you can just start with 2GB for / and 10GB for /home. When these get almost full, you just need to type 2 commands in terminal to enlarge any of them, without even logging out. I've been using this for 1 year and am very happy with it.

LVM info is found [here]("http://tldp.org/HOWTO/LVM-HOWTO/").

---

### Post by Corvo78 on 2007-02-21
Interesting... I will read up on LVM. Which sounds too good to be true :)

What's the main difference between Ext3 and ReiserFS?

---

### Post by Kateikyoushi on 2007-02-21
Despaite that you seem to have plenty of space to play with using a bigger / than 10GB is a waste if you have another /home. Add that to your home, in 10GB you can still fit in every Desktop environment you want to try. Putting swap on a different drive might make things bit faster if it doesn't cause problem for you during install try it.

---

### Post by Corvo78 on 2007-02-21
Thanks.
I was reading up here and there... and was already drawing the conclusion that a 200GB **/** was overkill.
I guess I should give it a meaningful place within /home or 'give it' to Windows.



*Edit:*
At the moment I'm thinking about this setup...[list]
[*]200GB[list][*]20GB as **/** (root)[*]180GB as **/home/corvo/videos/movies**[/list]
[*]250GB FakeRaid mirror[list][*]250GB as **/home**[/list]
[*]500GB[list][*]2GB as **swap**[*]498GB as **/home/corvo/videos/series**[/list][/list]

Not sure if LVM is handy when using a FakeRaid1 mirror together with regular (non-raid) drives :confused:

---

### Post by louis_nichols on 2007-02-21
> **Corvo78 said:**
> 
Not sure if LVM is handy when using a FakeRaid1 mirror together with regular (non-raid) drives :confused:

Sorry, but I wouldn't know what to tell you about that. I only have one ATA HDD. But you can just make an experiment to see if it works. You would only need 2 gigs for that and an installation for the Ubuntu desktop can take only about 15minutes or so. Then you find out. Just an idea.

Otherwise, it is true that you can make a smaller /home and make a separate partition for storing, mounted elsewhere.

Of course, there are other ways. In fact, I strongly recommend you run a search on the forums for ideas. I've seen discussions on this topic many times.

---

### Post by Corvo78 on 2007-02-21
Searched around a bit more and I think I know what to do...
I guess I'll just have to bite the bullet and will try to install Edgy onto a FakeRaid mirror.


So, I guess this should do the trick:[list]
[*]250GB FakeRaid mirror[list][*]20GB as **/** (root) [*ReiserFS??*][*]230GB as **/home** [*Ext3*][/list]
[*]500GB[list][*]2GB as **swap** [*Linux-Swap*][*]498GB as **/home/corvo/videos** [*Ext3*][/list][/list]
This should protect the entire OS and my personal data from 1 disk failure and seperate my videos onto the big 500GB drive.
Would it be a good idea to use ReiserFS as the FileSystem for Root? :confused:
*(since it should be able to handle a lot of small files better then Ext3)*


After all is said and done, I can install Windows unto my 300GB drive with an (for now) additional 200GB drive.
More then enough of a challenge, I'm sure.

---

### Post by louis_nichols on 2007-02-21
I recommend reiserfs. Read [here ]("http://ubuntuforums.org/showthread.php?t=157647")why.

---

### Post by Corvo78 on 2007-02-21
Wow, thanks for all the helpfull replies.
One last question before I embark on this adventure, can **/boot** also be ReiserFS?
...while (re)searching ReiserFS I thought I read something about **/boot** not working if it's ReiserFS.

Anyways, thank you for the replies. I'll post back with results of my installataion! :popcorn:

---

### Post by louis_nichols on 2007-02-21
No. /boot needs to be ext2 or ext3. And can not lie in an LVM.

Myself, I have a separate 100MB partition for /boot

---

### Post by Corvo78 on 2007-02-22
I took the installation for a spin last night...
I detached all drives except the two 250GB drives and created a RAID array in the BIOS.
After that I made a lot of installation attempts, mostly loosely or strictly based upon:[list][*]_[FakeRaidHowto wiki](https://help.ubuntu.com/community/FakeRaidHowto)_
[*]_[FakeRaidEdgy wiki](https://wiki.ubuntu.com/FakeRaidEdgy)_[/list]
But... to no avail. So, I'll try again tonight.
](*,) 
Setting up FakeRaid certainly isn't for the faint of heart.

Any pointers are always welcome.

---

### Post by Corvo78 on 2007-02-22
I decided that FakeRAID just isn't worth the hassle...
...so, I've placed an order for a "3Ware Escalade 8006-2LP" SATAII controller.

From what I've gathered is a RAID controller with it's own dedicated CPU and such, so should be true hardware RAID.
3Ware also has good Linux support and the RAID controllers are supported in most (all?) Linux kernels.

As soon as I fit that controller and restart my installation, I'll post back!

---

