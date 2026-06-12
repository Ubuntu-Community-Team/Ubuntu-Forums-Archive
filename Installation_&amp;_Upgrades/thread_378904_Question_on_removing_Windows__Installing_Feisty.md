---
title: "Question on removing Windows / Installing Feisty"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by jcconnor on 2007-03-07
I'm sure this has been asked and answered before but I couldn't find it - was probably using the wrong search terms - anyway, here it is:

I'm currently using Ubuntu 6.10 in a dual boot with XP.  I'm thinking about dropping the XP part and using that partition to install Feisty when it gets released.  My partitions are set up as:

/dev/hda1 - 20gig NTFS (XP boot)
/dev/hda3 - 20gig EXT3 ( / )
/dev/hda4 - 30gig EXT3 (/home)

My questions are this:


1)  Will I just boot a Feisty Live CD and install on the /dev/hda1 partition (the XP partition) like it's a normal install?

2)  Will GRUB recognize the /dev/hda1 and the /dev/hda3 partitions as separate boot partitions so I can boot back to 6.10 Edgy if I run into problems?

3) Will both the Feisty and Edgy partitions use /home for both?

4)  If I install VMWARE player and put the XP VM on /home will both Edgy and Feisty see that and both be able to use it?

5)  Why can't I do a better search and find these answers for myself?

Thanks!!

---

### Post by Kateikyoushi on 2007-03-07
1) You can boot and install feisty like the edgy installer and install it to hda1, you can manually edit the partitions to choose where it goes.
2) Yes but I would rather stick with the edgy grub or you might have to copy boot options from edgy.
3) As you like if you set so yes if you want can leave home in feisty / or make another partition for it.
4) if vmware settings are stored in /home yes but might i never tried it also the feisty and edgy version might be different.
5) I find the ubuntuforums search quite good in fact, recently I used gentooforums again and noticed it actually comes up with something I can use.

---

### Post by jcconnor on 2007-03-08
Thanks,

I was actually joking about the forum search stuff on the last one.  It's really a problem with me more than the forum search - I just wasn't getting the right combination of keywords or was too generic with the ones I used.  

Good information on the other points.  I'll just have to wait and see what happens.

Thanks!!

---

### Post by Kateikyoushi on 2007-03-09
I know what you meant, indeed it takes a few tries to find the right combination of words to get the results we need, I just tried to point out that despite the forums size the search does a good job if compared to other forums, unfortunately all I managed to do was to write a meaningless sentence.

---

