---
title: "What is the best way to create a partition for Ubuntu?"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by Richiegs on 2010-10-03
I want to install Ubuntu in a separate partition of my PC. Right now I only have Windows Vista or just one partition in my PC. I would like to know what is the best and safest way to create a partition for Ubuntu.
1. Shrink the existing Windows partition into two partitions using Disk Management in Windows.
2. Shrink the existing Windows partition into two partitions using Gparted in Ubuntu.
3. Using Ubuntu Installation Disk to install ubuntu side by side with Windows Vista as recommended in Ubuntu website.
 
My goal is to be able to adjust the size of each partition easily when I may need to do it in the future. Thank you very much.

---

### Post by oldfred on 2010-10-04
You want to use Vista MMC to shrink the Vista partition. Windows needs 20-30% free space to continue to work well.

You then can do the default install that creates / (root) and swap in the free space or manually create partitions and use manual install. With manual install you can create a separate /home. You may also want a separate NTFS shared partition for any data like firefox profiles or thunderbird profiles to have the same data in both. I do not recommend writing into system partitions unless you are making repairs, so a shared data partition is a preferred method to share data.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by mikewhatever on 2010-10-04
None of the options you mentioned is 'the best' cause there is no best. Besides, there is no way to shrink one partition into two.;)

---

### Post by Mark Phelps on 2010-10-04
Not to nitpick ... but both #2 and #3 are bad options.

As oldfred has already suggested, go with option #1 to do the shrinkage.  It presents the least risk of filesystem damage.

---

