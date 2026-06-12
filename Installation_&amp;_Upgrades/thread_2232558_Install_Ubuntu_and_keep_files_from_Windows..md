---
title: "Install Ubuntu and keep files from Windows."
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by lolsi11 on 2014-07-02
Hey guys,

first really sorry for my "wonderful" English, but I will do my best that you can understand me.

I'm really sick of Windows ( 8.1 yh ), it doesn't work way it should, but I'm not really surprised about that. So I decided I don't want to be frustrated all summer long and my plan is to install new Ubuntu, but I have a problem, I have to keep files, too many off them like 100gb :(. And I don't own any external device bigger than 16gb so my question is can I make partition, put files on then install ubuntu over Windows and keep files on other partition.

Sorry for English again...

Good day

---

### Post by grahammechanical on 2014-07-02
My advice would be to dual boot with windows 8 and once Ubuntu is installed then to migrate the files over to the Ubuntu partition. I am saying this becasue you may need to use the Windows program that created the files to export the data into a file format that the Ubuntu programs can import.

A couple of things to watch out for. When Windows 8 shuts down down it actually hibernates. and the partition cannot be accessed by the Ubuntu File Manager. So, you will need to find the method of shutting Windows 8 down completely.

And to install Ubuntu in dual boot with Ubuntu you need to look at this advice:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You could also use a Windows utility to create space for another partition (data partition) and then create the partition and format it to NTFS. Then Windows 8 will be able to migrate the files into the new partition and you can test to see if those files can be read by Ubuntu applications by using the live session. Do this before you install over Windows.

Regards.

---

### Post by Mark Phelps on 2014-07-02
To disable the "new" hibernation scheme that Win8 uses, turn off FastStartup in Windows 8.  That way, when you shut it down, it won't go into hibernation any more.

---

### Post by yancek on 2014-07-03
If the files you want to save are not program files, another option is to create a partition from your current windows and copy all these files from your current windows partition to the new 'data' partition before installing Ubuntu.  You should familiarize your self with Linux naming conventions for hard drives and partitions because they are not the same as windows/  You could review the tutorial below on installing Ubuntu as it also has other useful information:

  [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by lolsi11 on 2014-07-03
Thanks, it wordked with partiton.

---

