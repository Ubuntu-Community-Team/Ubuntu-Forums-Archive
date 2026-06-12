---
title: "How to install ubuntu into a smaller partition or one i have provided?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by jeremyleroy96 on 2010-03-02
Okay so here is the situation,
    I want ubuntu and i have windows 7 beta but the beta is ending soon. Ubuntu was my OS before i went to the beta (TERRIBLE SWITCH) and i wiped the HDD clean and went to windows. So now i need to have windows and ubuntu together (dual boot). Windows has invaded all of my HDD space and will only give up 10gb i want ubuntu in that 10gb space i have partitioned in windows. I would use the installations partitioner but the smallest it lets me make it is 80gb and if i gave it that my windows will corrupt leaving me a sad panda. So how can i put ubuntu into a 10gb partition?

Regarding my old thread: This is really a different topic then the
                         one i originally asked. I gave up on WUBI!

---

### Post by darkod on 2010-03-02
Have you already shrinked win7 so it leaves 10GB unallocated space on the hdd? Or that is just unused space in the win7 partition?

PS. If you can post a screenshot of windows Disk Management it would be even better.

---

### Post by sgosnell on 2010-03-02
If you already have a 10-GB partition, tell the installer to use it.  If you don't have the partition, run the liveCD instead of just the install program, start gparted and make the partition.  Slide the Windows partition to the left to leave ~10GB of unallocated space, then have gparted make a new partition there, formatted to whatever you want.  Then run the installer and have it use that partition, and you can use whatever filesystem you want, it will be reformatted during the install.

---

### Post by darkod on 2010-03-02
> **sgosnell said:**
> If you already have a 10-GB partition, tell the installer to use it.  If you don't have the partition, run the liveCD instead of just the install program, start gparted and make the partition.  Slide the Windows partition to the left to leave ~10GB of unallocated space, then have gparted make a new partition there, formatted to whatever you want.  Then run the installer and have it use that partition, and you can use whatever filesystem you want, it will be reformatted during the install.

Actually it's better to delete that 10GB partition (if it exists) regardless what filesystem it is. Only one partition will make ubuntu run without swap. That's why I asked if the space is just unallocated.

You need to get to that point and then just tell the installer in step 4 to Use Largest Available Free space. That will set up the standard root+swap into that space.

---

### Post by jeremyleroy96 on 2010-03-02
well while thinking about it i deleted the partition i made and decided to download the newest version of ubuntu i originally was using 7.04. It has a way better partitioning system. I think i got it to go into unallocated space i hope, its installing now :o
EDIT: Okay ubuntu is up and running but installing updates so can't tell if windows is still good :/ but its still there i saw it on the boot loader. Can i get the windows boot loader back? it makes my dad mad for some reason? He can deal with it though! Thanks for the support guys!

---

### Post by darkod on 2010-03-03
> **jeremyleroy96 said:**
> well while thinking about it i deleted the partition i made and decided to download the newest version of ubuntu i originally was using 7.04. It has a way better partitioning system. I think i got it to go into unallocated space i hope, its installing now :o
EDIT: Okay ubuntu is up and running but installing updates so can't tell if windows is still good :/ but its still there i saw it on the boot loader. Can i get the windows boot loader back? it makes my dad mad for some reason? He can deal with it though! Thanks for the support guys!

Windows bootloader can't boot linux directly, it can't even see it. You can "force" grub2 to install onto the ubuntu root partition, it doesn't usually like that. But using the --force argument, you can.

However, only that won't make it work right away. You still have to do a procedure to add grub2 to the windows bootloader.

IMHO, your dad is looking into more trouble that way.

One option to make thing easier is to make the windows entry default, and you could also change the positioning of the windows entry so that it's first on top.

---

### Post by jeremyleroy96 on 2010-03-03
Thanks for the reply, 
That doesn't sound worth it ;). Can i make it boot into ubuntu automatically? My mother would be clueless.

And yes my family does use my computer a lot :p

---

### Post by sgosnell on 2010-03-04
You can have it boot into Windows or Linux automatically, whichever you want.  Set the default to your desired OS.  It may still go to the grub menu, but you can set the timeout on that fairly low, so it doesn't stay long.  It will eventually boot to the default without doing anything else.  My wife's laptop is set to dualboot, with Windows the default, and she was clueless as to what was going on, but I finally convinced her to just wait, and Windows eventually boots.

---

### Post by jeremyleroy96 on 2010-03-04
how do i shrink the time because i think its 10 seconds now

---

### Post by darkod on 2010-03-04
> **jeremyleroy96 said:**
> how do i shrink the time because i think its 10 seconds now

sudo gedit /etc/default/grub

The line GRUB_TIMEOUT="n"

PS. Of course, you need to run

sudo update-grub

after that for new grub.cfg to be updated. You always need to run that after making changes to grub config files.

---

### Post by jeremyleroy96 on 2010-03-04
Thanks it worked!

---

