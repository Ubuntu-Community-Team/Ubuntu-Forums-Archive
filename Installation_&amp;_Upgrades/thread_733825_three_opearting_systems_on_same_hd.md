---
title: "three opearting systems on same hd"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by iamdennisthomas on 2008-03-24
hey friends. i am having xp and fedora already installed in my pc. how can i install gutsy keeping both my previous os?

---

### Post by toa on 2008-03-24
> **iamdennisthomas said:**
> hey friends. i am having xp and fedora already installed in my pc. how can i install gutsy keeping both my previous os?

I have XP + Vista + Gutsy all in one machine and OSX is coming soon :)

In your case, you might need to consider installing on a different partition with seperate home folder from previuos, focus on the partition part... this guide might help

[http://howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by housam on 2008-03-24
Just install it as usual. you'll have a grub nenu with the three distros. do not forget to create two partitions for installing ubuntu - root (/) and swap

---

### Post by iamdennisthomas on 2008-03-24
Thanx for ur response.. but my main concern is the partition. When i tried doing it i found i could only have 4 primary partition in one hd. space is not the problem. but just can't figure out how to go about the partition. Can i give the same partition i gave to fedora to gutsy? Is their anything i can have common in gutsy's installation

---

### Post by housam on 2008-03-25
You can delete one of your primary partitions ( transfer the data from non-system partition to any other partition ) and reformat it to an extended partition which can be devided to many logical partitions. by this way you can create the required partitions for installing ubuntu ( insde the extended partition ).

---

### Post by iamdennisthomas on 2008-03-28
din get u. ubuntu dont make installations on logical drives is what i know.Mr. Housam i will tell u how my partition is right now. i have one primary partition for windows. One for fedora and one in which i can keep all my data so even if i have to format i would have some sort of back up. If i try to give last bit of unallocated space to ubuntu it wont accept it. somehow it even did but then it would only make a swap and then would show it cannot use the last part.

---

### Post by iamdennisthomas on 2008-03-28
can both fedora and ubuntu use the same swap space?

---

### Post by forestpixie on 2008-03-28
yes same swap will be fine - and you can install it in a logical partition, but to do that make an extended - then create a logical inside and install to that

---

