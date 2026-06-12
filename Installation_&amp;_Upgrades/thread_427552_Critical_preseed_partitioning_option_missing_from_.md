---
title: "Critical preseed partitioning option missing from documentation, re: expert_recipe"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by andrew davidoff on 2007-04-29
I am not sure where to report this, so I'm trying here.

I couldn't get expert_recipe preseeding working in 6.10 or 7.04.  No matter what I tried, even using the example preseed file from the ISO, I would get dropped to the partitioning menu and/or an error that I had no root partition definied.

After a lot of trial and error and scrounging Debian documentation (as well we Ubuntu), I discovered the following preseed option which is required for expert_recipe preseeding to work.

partman-auto    partman-auto/method string  {regular|lvm|crypto}

In my case I needed to use "regular".

If I add this to my preseed file, partitioning with an expert_recipe works fine.  If I remove it, it fails.  I can reproduce this over and over.  References to this option can be found in Debian's example preseed for etch:

[http://www.debian.org/releases/etch/example-preseed.txt](http://www.debian.org/releases/etch/example-preseed.txt)

"
# In addition, you'll need to specify the method to use.
# The presently available methods are: "regular", "lvm" and "crypto"
d-i partman-auto/method string lvm
"

Please add this to the documentation and and example preseed file with 7.04.

Thanks.
Andrew Davidoff

---

### Post by andrew davidoff on 2007-04-30
Bump.

Andrew Davidoff

---

### Post by andrew davidoff on 2007-05-01
One last bump before I try a different audience.

Andrew Davidoff

---

### Post by raq on 2007-05-03
Thank you so much. I had the same problem, but now I have some questions:

1) I would like to select first disk to partition, but putting

    d-i partman-auto/disk string /dev/discs/disc0/disc

    is NOT WORKING

   I must put

    d-i partman-auto/disk string /dev/hda

2) I try to use 'd-i partman-auto/expert_recipe_file string <file>', but I does NOT seems to work
    Actually, I do not know how to specify <file>

   I must use    d-i partman-auto/expert_recipe string

and finally,

3) I would like to create 4 primary partitions, but NO WAY. I can only create 2, been the others of   logical type.

Regards, and thanks again

---

### Post by andrew davidoff on 2007-05-03
I should start by saying that I'm by no means an expert on any of this, so you shouldn't take my responses as the end all be all on these topics.

> **raq said:**
> Thank you so much. I had the same problem, but now I have some questions:

1) I would like to select first disk to partition, but putting

    d-i partman-auto/disk string /dev/discs/disc0/disc

    is NOT WORKING

   I must put

    d-i partman-auto/disk string /dev/hda

Sorry, not sure on this one.  I would think that /dev/hda will always pick the first disk, though maybe you're trying to do something special that I don't understand.  I certainly don't understand why using /dev/hda, if that is working for you, is a problem, even if there's another alias by which the disk can be referred to once the OS is loaded.

> **raq said:**
> 2) I try to use 'd-i partman-auto/expert_recipe_file string <file>', but I does NOT seems to work
    Actually, I do not know how to specify <file>

   I must use    d-i partman-auto/expert_recipe string

I haven't tried this yet, but from the documentation I read this only works if the file is already in the intallation environment.  This would mean (I think) you'd have to create it during install before the installer tries to read it (not sure at what point this would be, or if it'd be possible), or you'd have to put it into the initrd image.

> **raq said:**
> and finally,

3) I would like to create 4 primary partitions, but NO WAY. I can only create 2, been the others of   logical type.

Regards, and thanks again

Sorry, not sure on that one either.  If you are specifying $primary{} for all 4 but 2 are still showing as logical I'm not sure.  I don't know the guts of partman or the installer.

Again, I'm no expert here, but this what I think I can responsibly suggest based on what I feel I understand.  Good luck.

Andrew Davidoff

---

### Post by raq on 2007-05-03
Sorry, not sure on this one.  I would think that /dev/hda will always pick the first disk, though maybe you're trying to do something special that I don't understand.  I certainly don't understand why using /dev/hda, if that is working for you, is a problem, even if there's another alias by which the disk can be referred to once the OS is loaded.

Well, the problem is that I have a cluster of 150 calculation nodes where some of them have the first disk as /dev/hda and some have /dev/sda. I should do the installation one by one. Not a disaster, but it could be better.

I haven't tried this yet, but from the documentation I read this only works if the file is already in the intallation environment.  This would mean (I think) you'd have to create it during install before the installer tries to read it (not sure at what point this would be, or if it'd be possible), or you'd have to put it into the initrd image.

Sorry, not sure on that one either.  If you are specifying $primary{} for all 4 but 2 are still showing as logical I'm not sure.  I don't know the guts of partman or the installer.

If you put 'primary{}' at more than 2 the partitioner stops with an error

Anyway, your discovering  has been of great help. Thanks again

---

### Post by andrew davidoff on 2007-05-03
> **raq said:**
> Well, the problem is that I have a cluster of 150 calculation nodes where some of them have the first disk as /dev/hda and some have /dev/sda. I should do the installation one by one. Not a disaster, but it could be better.

That's something I am working around right now, too, by having different preseed configs based on the hardware I'm installing onto (essentially different options from my PXE boot menu).  I'd like to use in-install utilities and debconf-set and friends to dynamically figure this out and set it during the installation, but (1) it seems that there are no obvious utilities available from which I can gleam this information at the points of the installation where I could try (early_command, late_command, run), and even if there are, I am having issues getting debconf-set and friends to work in the installation environment.  Perhaps the topic of another post if I ever figure it out. 

Andrew Davidoff

---

### Post by paljas on 2007-05-04
Hi,

Which documentation are you gays talking about? I can't find any docs on 7.04.
My 6.10 preseed file isn't working for 7.04. That is: it keeps asking about which partitioning method I want to use.

I guessed:

d-i partman-auto/disk string /dev/sda \
    select  Guided - use entire disk

but that doesn't help.

---

### Post by andrew davidoff on 2007-05-04
> **paljas said:**
> Hi,

Which documentation are you gays talking about? I can't find any docs on 7.04.
My 6.10 preseed file isn't working for 7.04. That is: it keeps asking about which partitioning method I want to use.

I'm using the 6.10 documentation supplemented by the example preseed file on the 7.04 install media.

> **paljas said:**
> I guessed:

d-i partman-auto/disk string /dev/sda \
    select  Guided - use entire disk

but that doesn't help.

I think you're using that option incorrectly.  The partman-auto/disk option only takes one string argument specifying the disk you want to install on as I understand it.  So, the "use entire disk" information doesn't go here.  You're probably looking for this (or something like it):

d-i partman-auto/choose_recipe \
       select All files in one partition (recommended for new users)

Just a shot in the dark.  I have never used the interactive installer so if "Guided - use entire disk" is an option there, perhaps you can pass that as an argument to d-i partman-auto/choose_recipe if what I suggested doesn't do what you want.

Andrew Davidoff

---

