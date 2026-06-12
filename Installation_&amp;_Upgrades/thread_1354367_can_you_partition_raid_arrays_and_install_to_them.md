---
title: "can you partition raid arrays and install to them?"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by rx7man on 2009-12-13
Ok... newb alert here. My eyes are sore from searching for my answers online today, must have been looking for 4-5 hours today... so any help would be really really awesome right now.

I am trying to install ubuntu 9.1 on a new computer I just built. I have 3 1.5tb drives and I wanted to raid 5 them and install. Then I was reading about ubuntu's soft raid capabilities and decided that would be cool since my onboard raid was a no go...

I usually install on single disk systems but since this new machine will be holding all my stuff in one place (FINALLY) I want it to be safe (raid 5). So my single disk instally are usually like partioned for 20gig root, 1 gig swap, rest for home directory.

I tried to use the alt install cd and got an array configured... but then it wouldn't let me partition it... what am I missing? I don't wanna run with one giant partition if I don't have to... what do I do?

---

### Post by rx7man on 2009-12-14
Anyone? I used mdadm to create a raid 5 array using the (try ubuntu w/out installing), but how do I install ubuntu to it now? Can u not do this?

---

### Post by falconindy on 2009-12-14
Look into LVM. It will do what you ask.

---

### Post by rx7man on 2009-12-15
Well I figured it out last night... I feel so stupid... I put the partition layout I wanted on all three drives and made 3 different raid 5 arrays, one for root, swap and home. Is this the most effecient way to do so? I will look into the LVM as I don't know what that is but thank you so much for being the only one to try to help me. Much props dude :)
 
Edit: I did see the w/lvm options but never used them since I didn't know what they were for... gonna read up on the subj now...

---

### Post by darkod on 2009-12-15
If you use only ubuntu (no dual boot), LVM Logical Volume Manager is great, with or without raid. Basically it allows to dedicate your whole physical space to it, and then you create sizes for /, /home, swap etc as small as you think you need. After you begin to have little free space, you can expand /home for example, without any need to reformat or repartition, as long as you still have unused space in the LVM setup.
As for the softraid, yes, I think you got it. You create same size partitions on all drives, as many different as you need, and you just softraid the partitions between them.
If that made any sense. :)

[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

---

### Post by rx7man on 2009-12-17
Awesome, that link really really helped me out. Now if I understood right from all this I now have my system installed like this. Partitioned 3 1.5tb drives w/one large ext3 partition and flagged for raid. Made them one large softraid 5 array. Created one large volume group over the top of that and then within the VG I made three logical volumes(partitions) for root, swap and home.

This is the most efficient way to do so? So since I'm using this LVM stuff I can grow with another 1.5tb drive down the road? I really gotta dumb this stuff down to understand it lol

The only difference I have noticed running this way is that I get a bunch of boot errors from GRUB but it boots anyways.... weird huh?

---

