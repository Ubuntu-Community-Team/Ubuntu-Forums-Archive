---
title: "Can I create a separate /home partition when loading Lucid?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Scunnered on 2010-03-31
I have been looking to create a separate /home partition and my thoughts were do so when adopting Lucid. What I would like to know is how I can achieve this. 

I propose to download 10.04 and having created the boot disk install it completely on my hard drive.  I don't want any other OS on the system. I know the principals of creating a partition but am unsure how I physically create the separate /home. 

When I had a look at my present set up by using Gparted from the Live CD I found that there were 3 partitions listed being ext4, unallocated and Linux swap.  Checking the file system support I found a complete shopping list with the exception of a separate /home partition.  It is at this point that my ignorance surfaces yet again and I seek your indulgence and guidance.

Ideally I would like to try a dummy run using Karmic so when I adopt the LTS that I will get things right first time.

---

### Post by oldfred on 2010-03-31
I think all the automatic installs just set up root & swap as that is all that a new user needs. I ran that way for 3 years.
If you understand partitions then you use the manual install where you select the partitions (root, swap, & others) and format them (or not for existing /home). I believe you can create partitions at that time but I have always created them in advance.

---

### Post by Mark Phelps on 2010-03-31
Lucid is still in beta testing.  Please post your beta-related questions to the correct forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.  Look there for any future responses.

---

### Post by plucky on 2010-03-31
> **Mark Phelps said:**
> Lucid is still in beta testing.  Please post your beta-related questions to the correct forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.  Look there for any future responses.

Why??

Partitioning is relevant for all versions of Ubuntu.

@Scunnered

Checkout this [link](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Scunnered on 2010-03-31
My thanks to each of you for your assistance.

**oldfred**

My thoughts were that while I think that I will stick with Lucid for the LTS duration it would be handy being able to use /home partition with any update to see how they work.

**Mark Phelps**

I am aware that Lucid in in beta and do not expect that the developers would be able to work miracles by offering a separate /home partition as an install function.  I hand hoped that by seeking advice in advance that I would be fully prepared when I move everything over to the LTS.

**plucky**

The link provided looks to be ideal.  The only thing that I can't get my head round is how I name the mount point to /home?  Can you assist there?

So near - so far!

---

### Post by Vaphell on 2010-03-31
in general in the partitioning step there are 3 options
- use whole hdd (1 partition)
- use empty space (1 partition)
- manual partitioning

manual partitioning lets you create more partitions and assign them to their respective mountpoints. If you want to have separate /home you need
- 1 partition for the root dir of the system (ext4, 20GB should be plenty)
- 1 partition for /home (ext4, rest of the disk space)
- 1 partition for swap if wanted/needed
commit changes and proceed with installation, 15 minutes later it's done - you have a system with a separate /home :-)

in case of reinstall / (root) must be formatted but you leave /home unformatted and thanks to that your customized profile (and profiles of other users) is already in place.

---

### Post by dcstar on 2010-03-31
> **Vaphell said:**
> in general in the partitioning step there are 3 options
- use whole hdd (1 partition)
- use empty space (1 partition)
- manual partitioning

manual partitioning lets you create more partitions and assign them to their respective mountpoints. If you want to have separate /home you need
- 1 partition for the root dir of the system (ext4, 20GB should be plenty)
- 1 partition for /home (ext4, rest of the disk space)
- 1 partition for swap if wanted/needed
commit changes and proceed with installation, 15 minutes later it's done - you have a system with a separate /home :-)

in case of reinstall / (root) must be formatted but you leave /home unformatted and thanks to that your customized profile (and profiles of other users) is already in place.

Exactly, the process of creating a separate /home partition has been in Ubuntu for many years now and remains the same in 10.04 as it has been in many earlier releases.

I would prefer the installer prompt or offer a separate /home as it would certainly make all Ubuntu installs a lot more solid and less likely to lose data, anyone else who also thinks this is a good idea may want to go to this site and see if it has been suggested:

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by tommynz1975 on 2010-03-31
it has been suggested countless times to have an advanced option for a /home on install. So that one may do fresh installs and such like but the sysops seem to think when root /  runs out of space it will cause problems.  Or that it maybe will confuse new users.

---

### Post by Sef on 2010-03-31
Moved.

---

### Post by takisan on 2010-03-31
During the setup, all you need to do is make 3 partitions.

[LIST]
[*]/ [Root]    45% of Drive
[*]/home      45% of Drive
[*]Swap        5%
[/LIST]
That's how I'd do it. Maybe 50% home and 40% root.

---

### Post by cariboo on 2010-03-31
If you're just setting up the desktop version, 10Gb is more than enough for /. I usually set the / partition at 10Gb, swap at 2X ram and /home the rest of the drive.

---

### Post by Scunnered on 2010-04-01
Again my thanks to you all for your replies.

Looking at what you say I have more than enough space to play with so that will not be a problem.  

**Sef & cariboo907**

As you can see from the remarks here there appears to be a number of us who would like the ability to create a separate /home partition when we effect a complete install.

Could you as forum staff perhaps poll the forum for their opinion to see how many find this of benefit.  So often advice is given of the benefits of having this partition so surely making it available at the time of installation would be ideal.

Thanks once again to all for their assistance

---

### Post by john newbuntu on 2010-04-01
I am not sure if you can do this while installing Lucid.  However, if you follow these steps, it does not matter what version you install, you have one less worry:

If you can carve out an ext4 partition from the existing root filesystem to a new one (lets call it /dev/sda7).  Mount it and copy all your home directories there. (Do not perform any changes to /etc/fstab). Then unmount it.

Then, go ahead and install Karmic or Lucid.  Rename the stock /home to something else.  Mount your /dev/sda7 as /home.  Change /etc/fstab to reflect this.  Reboot and you are done.

Edit - Scunnered: I guess the install has to be as generic as possible with preferably just one partition(the swap can be inferred from the total although that is not done so).  There is always a manual option to set up as many partitions as possible including the one for /home.

---

### Post by Scunnered on 2010-04-01
**john newbuntu**

Thanks for your advice. 

My intention is once Lucid is final and the dust has settled I shall load it to both my laptop and desktop systems.  Needless to say I will have everything that I need backed up prior to the change.

I hope that the initial fresh install will let me create a separate /home partition but if that fails I can easily revert to the Live CD and hopefully make things work at that point.  Having mastered this once I will know what to do on the other system.

I don't want to mess about with Karmic as I am perfectly happy with what I have as with luck like mine I would screw things up.  If Lucid was not a LTS  I would have more than likely left things alone.

Am I right in thinking that your instruction is based on usimg gparted from the Live CD having initially installed Lucid?

Again thanks

---

### Post by Arla on 2010-04-01
> **Scunnered said:**
> As you can see from the remarks here there appears to be a number of us who would like the ability to create a separate /home partition when we effect a complete install.


While I think it's highly useful to create a separate /home partition, and definitely in the best interest of any experienced user, I think that if you know enough to be thinking about having a separate home partition, you should be able to do manual partitioning (that the install allows for) easily enough.

---

### Post by john newbuntu on 2010-04-02
@Scunnered,
You can create your /home partition while still on Karmic.  And then when you do a brand new install of Lucid, just swap your home partitions (presuming your userids/groupids/softwares etc are the same).  
The usual caveats apply: backup your installation at all time.

---

### Post by NZjelle on 2010-04-02
> **john newbuntu said:**
> @Scunnered,
You can create your /home partition while still on Karmic.  And then when you do a brand new install of Lucid, just swap your home partitions (presuming your userids/groupids/softwares etc are the same).  
The usual caveats apply: backup your installation at all time.

I have done this. The Lucid installation works fine, and automatically included almost everything I had in Karmic. Big caveat, however, is that I can no longer boot into Karmic. It shows up in the Grub list, but when I try to go back to Karmic it freezes. As far as I can tell this is because it no longer recognizes the keyboard or the mouse. Not sure why, but I think something got messed up because I allowed Lucid to install a new bootloader.

On  the bright side, the Lucid beta is rock solid on my system, so I am now using it all the time. And I am running AMD 64-bit with an ATI graphics card. So far, so good.

---

### Post by Scunnered on 2010-04-02
Again my thanks to all for their assistance.

**Arla**

Thanks for your encouragement. My thoughts were to stick with Lucid as it is a LTS and having a separate /home I can always trial the following updates as and when they arise.

**NZjelle**

As advised to Arla I wish to work with a completely fresh install of Lucid.  From what you say I think that it will be best in the first instance.



======

I am full of hope that I can set up the desktop with Lucid and having established exactly how things worked with that system then duplicate things on the laptop.  When I have both systems to my liking,then unless there is something extra special on the horizon,I intend to work with the LTS version during its lifetime.

I will keep this post open and advice further when I see how things get along mid May.

3rd May 2010.

I am pleased to advise that with assistance from **ajgreeny** and the tutorial from [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) I was able to achieve my aim.  The tutorial was completely clear in its instructions and I was able to effect the changes first time around.

I trust this will assist

---

