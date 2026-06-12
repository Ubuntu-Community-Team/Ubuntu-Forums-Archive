---
title: "Installing Ubuntu on SATA RAID, need help!"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by imkqm6 on 2010-02-04
I have an ASUS P4C800-E motherboard, two Seagate 250 Gb Hard drives, and my Raid ( I can use either raid(0) or (1), really whatever I pick by using the software) is controlled by Fasttrak system, or something like that. I have tried everything the help forums have suggested, but nothing has worked. I am not dual booting right now, and I am not worried about losing data, because it was all destroyed trying what the other forums said. I have the alternate 9.10 CD, is there anyone who can give me a step by step for idiots? I never used linux before. I know RAID is the problem, it seems there is a solution, but I am not smart enough to use it. Thanks!

---

### Post by darkod on 2010-02-04
Depending whether you plan to dual boot with windows or not, you have two options:
1. The so called Fakeraid, or motherboard BIOS raid, which works but is not fully supported by ubuntu.
2. So called Software RAID, where in fact you do not have raid enabled in your BIOS. Instead you create equal partitions on your hdd, and the Ubuntu OS is combining them in raid array. That's why it's called software raid.

People have reported the second option is working better, but for dual boot with windows you have to take the first option. I haven't installed on raid myself, but here are the tutorials:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by phillw on 2010-02-04
+1 darkod

Hi, and welcome to the forums,

Just be aware that 9.10 and RAID are not the 'best of friends' - Using either Grub Legacy on 9.10 or 8.04.4 (the last LTS) or using burg on 9.10 are the pick of the bunch at the moment.
Grub Lecacy on 9.10 should be okay to go to 10.04, which is having the raid issues sorted, 8.04.4 will have to be okay for 10.04 (LTS --> LTS upgrade) and burg has the fixes for raid available in 9.10.

Choices, choices ....

Regards

Phill.

---

### Post by imkqm6 on 2010-02-04
Ok, so now I get I need a new boot loader, Thank you! Now, how do I get burg and Ubuntu 9.10 in one package? I thought 9.10 live CD only came with either LILO or Grub? Is there a way I can download an ISO with burg instead of Grub?

---

### Post by imkqm6 on 2010-02-04
Also thanks for the quick reply, and thanks for the welcome :p

---

### Post by darkod on 2010-02-04
> **imkqm6 said:**
> Ok, so now I get I need a new boot loader, Thank you! Now, how do I get burg and Ubuntu 9.10 in one package? I thought 9.10 live CD only came with either LILO or Grub? Is there a way I can download an ISO with burg instead of Grub?

Don't let Phill scare you off. :) The Fakeraid document shows how to install grub and for Software RAID it uses separate /boot partition so using grub is not an issue at all.
Of course, you can go with something like burg too. As Phill said, you have quite a bit of choices.

---

### Post by phillw on 2010-02-04
The maintainer of burg can be reached by this thread --> [http://ubuntuforums.org/showthread.php?t=1378951](http://ubuntuforums.org/showthread.php?t=1378951)

It's where you have his commitment to 9.10. LIke most, he's concentrating on 10.04 if you post in there, he should pick it up, even tho' it is the dev area.

As to getting an image, you'd have to ask him (bean).  The posts that darkod gave you will work fine, however, if you put on 8.04.4 - 8.04.4 has only recently been released in readiness for 10.04 at the end of April. 10.04 is already on Grub 1.98 sub-version what ever, as opposed to the 1.97 beta that shipped with 9.10

I don't have a raid system ,I've just been keeping a quiet eye on developments as it caused problems when 9.10 first came out. Bottom line seems to be that they're not going to roll out the full raid fixes back to 9.10 - as they're still rolling fuller support to the test system, they cannot risk breaking a fully released version. (Which is fair enough !!).  

If you're just dipping your toe into Ubuntu, you could always put 10.04 on, but it is a test system & could break (it's doing very well, actually). 

If bean doesn't get back to you, IMHO (and I stress it is just my opinion), you may be better going with 8.04.4, where the raid support is there & the how-to's are already written. The details on 8.04.4 are over here --> [http://ubuntuforums.org/showthread.php?p=8740883#post8740883](http://ubuntuforums.org/showthread.php?p=8740883#post8740883)

I'm sorry I cannot give you a straight answer - that is because, at this moment in time, there does not appear to be one - I do ask occasionally what the state of play is, but it is in a state of flux, with additional raid and lvm support being added to grub for 10.04 on almost a weekly basis.

** NOTE** If anyone has more information than I have, please do post !!!

Regards,

Phill.

---

