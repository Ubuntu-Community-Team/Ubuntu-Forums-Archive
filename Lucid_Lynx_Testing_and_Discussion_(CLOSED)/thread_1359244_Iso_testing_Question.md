---
title: "Iso testing Question"
date: 2009-12-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yotux on 2009-12-19
I am new to ISO testing.  My question is which option should be used.  Installing on a the physical machine or using a virtual environment?

Which in the preferred method.

Wanting to help out the community and I am not sure how to get.  This seems some what easy and very needed way to help.

Nathan aka Yotux

---

### Post by phillw on 2009-12-19
Hi,

Not sure what everyone has done (and there are some variants !!)

I partitioned off 12GB for 10.04 and installed it onto it's own partition - The installer is savvy enough to see that I already have a swap area, so uses that.

I also have a seperate /home partition - I rsynced that over to the 10.04 area, as was advised that allowing it to 'play' with a copy of my ~home area is safer than allowing it on to the one I use for work.

Regards,

Phill.

---

### Post by PaulInBHC on 2009-12-19
How much space can you make on your HDD and how much knowledge do you have helps you to answer your question.
One of the reasons to test is to make sure the final LiveCD works.
I have WinXP and tried dual boot with 9.04. I liked it and within a few weeks made a new partition for 9.10. I liked that more and removed 9.04 leaving me room to try 10.04. I only do full install. I rarely use XP and haven't used 9.10 since going to 10.04 but keep it around just in case.
It is a learning experience for me. At least in the worst case I can use the LiveCD to get to the internet and try to fix whatever comes up.

---

### Post by andrewsomething on 2009-12-19
> **yotux said:**
> I am new to ISO testing.  My question is which option should be used.  Installing on a the physical machine or using a virtual environment?

Which in the preferred method.

Testing in a virtual environment is a great way to help out, but unfortunately it does not actually test hardware configurations. So if you just want to test ISO image integrity, the installer, and specific programs it's a great way to go. But if you have the extra hardware or room on your hard drive for another partition, we always can use more folks testing on real hardware to shake out issues with video drivers, ect....

---

### Post by yotux on 2009-12-19
Thank you for the quick replies.  I would like to help out with both fronts so it sounds like there is more data with the physical install.  I have a separate home partition and will try the rsync options there were mentioned above to copy data.

Thanks for the quick replies.

---

### Post by phillw on 2009-12-19
> **PaulInBHC said:**
> How much space can you make on your HDD and how much knowledge do you have helps you to answer your question.
One of the reasons to test is to make sure the final LiveCD works.
I have WinXP and tried dual boot with 9.04. I liked it and within a few weeks made a new partition for 9.10. I liked that more and removed 9.04 leaving me room to try 10.04. I only do full install. I rarely use XP and haven't used 9.10 since going to 10.04 but keep it around just in case.
It is a learning experience for me. At least in the worst case I can use the LiveCD to get to the internet and try to fix whatever comes up.

As noted with Virtualisation and testing - most hard drives these days can spare 10 - 15 GB of room. I have Win (Vista) - which i never use but keep to help M$ users, 9.10 for just in case 10.04 borks on me big-time and 10.04.
I gradually upgraded my 9.04 to 9.10, and having learned more about ext4 and grub2 both are now installed as a true 9.10. For any & all testing - you must be prepared to loose everything. So, don't store anything important on your 10.04 area. I backup my 10.04 as per a normal installation before i do any major brain surgery on it. It's a small install and takes a cple of minutes to do.
I'll repeat about not sharing your 'production' /home area - just rsync it over - that'll give you all your bookmarks, logins etc for FireFox, Pidgin etc. - It also kindly took over my complete desktop for me.

I keep my blog, in my Sig updated - but, there's not too much to report - 10.04 is running quite happily, I make a point of booting back to 9.10 just for the updates & ensure none of the updates cause any problems, as 9.10 is still young :-)

/edit  Once you know your partitons for /home and the 10.04 using rsync is easy - Post them back & I'll happily post you the instructions

Regards,

Phill.

---

### Post by yotux on 2009-12-19
My current setup I have some extra space for store of VM's.  When I installed I also used LVM setup.  This means that I have a seperate boot partition.  Can I shrink the LVM and get the 60GB of storage to install?

Is having this other boot partion going to cause me problems when testing?

Any advance is welcome.

My partition lay out:

/Boot 100mb

Lvm

  /root  20GB
  /home  100GB
  /swap  4GB
  /stores 60GB

Was going to take the 60GB partition out.

---

### Post by ranch hand on 2009-12-19
What bootloader are you using?

---

### Post by yotux on 2009-12-19
grub2

---

### Post by ranch hand on 2009-12-19
You shouldn't have a problem.  I would install the grub from 10.04 as it is newer - 1.97 instead of 1.97beta4 - on your partition.  Even if your OS is screwed (it is testing) grub should be fine.

---

