---
title: "Dual Boot XP"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by ITrainDogs on 2005-07-10
I have A dell Laptop with a 60gig HDD. All Space in taken up by windows. I am trying to install Ubuntu. Can Ubuntu resize Windows to allow me to install Ubuntu are do I need to resize first then install Ubuntu. 

Any tips or suggestions also welcome

Jesse

---

### Post by stickman on 2005-07-10
run a partitioner from within winblows..  resize your primary win partition.
then when installing ubuntu, you can specify for ubuntu to use the 
remaining free space on the drive.

stickman

---

### Post by not_yet on 2005-07-10
here's a little guide, see if it helps :) 

[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)

---

### Post by | MM | on 2005-07-11
[QUOTE=not_yet]here's a little guide, see if it helps :) 

[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)[/QUOTE]

I got a question.

When you resize the ntfs partion.  You dont loose data saved within the ntfs partition?  Does it actually move data around, or does it look for empty space on the disk drive for use in creating the partition?


So the result, barring a screw up along the way, Is my existing WindowsXP install, with all the content i have accrued over time(music) working as it should.  But now with the added bonus of an Ubuntu OS happily coexisting in a partition somewhere on the drive?

Cos if thats the case it looks easy.

---

### Post by Shinitenshi on 2005-07-11
[QUOTE=| MM |]I got a question.

When you resize the ntfs partion.  You dont loose data saved within the ntfs partition?  Does it actually move data around, or does it look for empty space on the disk drive for use in creating the partition?


So the result, barring a screw up along the way, Is my existing WindowsXP install, with all the content i have accrued over time(music) working as it should.  But now with the added bonus of an Ubuntu OS happily coexisting in a partition somewhere on the drive?

Cos if thats the case it looks easy.[/QUOTE]

When u said "60 gig is being used by windows" did you mean all 60 gigs are full with informaion or just being used by windows os? Because if there is any empty hard drive space, then you should be fine you wont lose any data :) but if your hd is packed with shi....stuff then u must delete somthing :)

---

### Post by Ozitraveller on 2005-07-11
You might find this useful:

HowTo: install Ubuntu for dual-boot with Windows 
[http://www.ubuntuforums.org/showthread.php?t=16353](http://www.ubuntuforums.org/showthread.php?t=16353)

---

### Post by | MM | on 2005-07-11
Ok im confused by one reply.

My situation:

I have a windows partition, that encompasses the total capacity of my hard drive.

However i have only used ~%50 of my hard drive capacity(the NTFS partiton) for storage.


The impression i have is that i can use the utilities provided on the Ubuntu disk when i boot from it to both, reduce my WindowsXp NTFS partition to 70%, and thus create a Ubuntu partion, or at least space reserved for the eventual installation of Ubuntu.

I also assume, typically speaking, that no data loss occurs on my NTFS/WindowsXp partition?
]



Also, abit OT

But i presume seeing as the 64bit Ubuntu Live disk booted an ran as to be expected, that the 'actual' installation should be sweet.

---

### Post by Aijaz Akhtar on 2005-07-11
Try any Live Linux CD that has QT Parted and do the job. Or use any instalation CD, not Ubuntu, that suports partitioning. the easiest I find is Xandros, and I use that CD to partition/resize. Even if I fail to do so, I install Xandros temporarily asking it to resize windows partition, and later use this Linux partitions for further work.

---

### Post by not_yet on 2005-07-11
> The impression i have is that i can use the utilities provided on the Ubuntu disk when i boot from it to both, reduce my WindowsXp NTFS partition to 70%, and thus create a Ubuntu partion, or at least space reserved for the eventual installation of Ubuntu.


the 70% is just a number used as an example 

during installation you can use the hoary install disk to resize your ntfs partition

see here  [http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)

during the install you are asked to choose a partition size

the % you choose will be the % alocated to the original patition

lets say you have a 100 gig winblows disk

the hoary patitioner asks you for a size,  you enter 80%

that means 80 gigs winblows

and 20 gigs ubuntu

lets say you enter 60%

that means 60 gigs winblows

40 gig ubuntu

afaik you need to have the free space present in order to create the partition

this is all based on ntfs Resize, read more here

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#example](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#example)

---

### Post by ITrainDogs on 2005-07-11
[QUOTE=not_yet]here's a little guide, see if it helps :) 

[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)[/QUOTE]


not_yet

I owe you 1 huge thank you. \\:D/ 

That guide worked like a charm. :grin: 


i am now walking through a Ubuntu wonderland

Thanks Again

Jesse

---

### Post by not_yet on 2005-07-12
welcome to Ubuntu :) 

enjoy the journey

---

