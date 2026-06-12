---
title: "unusable space in Ubuntu partition tool"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by nathan10 on 2013-10-10
Hello, I am trying to install Linux Mint along side Windows 7 on my sister's computer. I know that it isn't Ubuntu, but I'm still putting it in this category because it's the Ubuntu partition tool, the same one that's in the Ubuntu installer. I created a partition for Linux in Windows 7, and when I get to the point for choosing a place to install it, there is no "Install alongside Windows 7" option, so I chose "something else". In there it shows my partition but it says it's unusable, nothing else. When I click it, the "+ -" "Change" and "New Partition Table" are grayed out. I need help making the partition usable so I can install it on there. I don't want to get rid of Windows so I don't want to do anything that would do that. This is what appears in the partition tool:

/dev/sda
     /dev/sda1 ntfs  208 MB size 69 MB used Windows 7 (loader)
     /dev/sda2 ntfs 318140 MB size 90894 used Windows Recovery Environment (loader)
     unusable (This is where I'm trying to install Mint) 161061 MB
     /dev/sda3 ntfs 16435 MB size 14613 MB used Windows Recovery Environment (loader)
     /dev/sda4 fat32 4260 MB size 3103 MB used

Thank you for your time. Again, I put it here instead of other distro support because it uses the same partition tool as Ubuntu.

---

### Post by heir4c on 2013-10-10
You have 2 partitons with:  "Windows Recovery Environment"  ??

You created a 5th partition and that's impossible because you can have only 4 partition. I mean Primaire Partitions.
You can create more partitions but 1 of the partitions must be a Extended partition. And IN the Extended partitions you can create Logical Partitions.

In the newer Laptops/PC Windows creates always already 4 Primaire partitions. So that make it a problem to partitioning

>  there is no "Install alongside Windows 7" option
That is normal because there are already 4 partitions, so Ubuntu can't give that option.

As I said, you have 2 Recovery partitions. Can you explain that?

It will not be easy, but it will go, but I have no experience with that so somebody else will help you.

---

### Post by nathan10 on 2013-10-10
I didn't toy with the Windows partition at all, I have no idea why it created 2 recovery partitions. Is there a way to get rid of one without killing Windows? Thank you for your reply by the way.

---

### Post by heir4c on 2013-10-10
You're welcome.
Before we remove some things, I think the first recovery sda2 is your systempartition and the second is the recovery. 
What you can do is boot from the Live-dvd/usb and open the partition manager gParted. (find it via the Dash) (UbuntuLogo on the Top in the left)
Make a screenshot from that window (do it with the screenshot maker, you find that via the dash too). (Load it up via a upload site like: [http://imgur.com/](http://imgur.com/) and post the BBCode here in a post.)


Edit: I have to go sleep now, tomorrow go to work.

---

### Post by nathan10 on 2013-10-10
I did what you said but the laptop was having trouble with the wifi. Now I need the wifi drivers! *facepalm* Anyway, I'll try to upload it tomorrow or the next day.

---

### Post by oldfred on 2013-10-10
Often both the Windows boot/repair partition(100MB hidden) is called recovery and the vendor image of your hard drive is called recovery. Or two recovery partitions but different. 

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

