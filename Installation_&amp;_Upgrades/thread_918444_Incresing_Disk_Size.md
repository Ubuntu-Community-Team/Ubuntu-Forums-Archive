---
title: "Incresing Disk Size"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by kemadruma on 2008-09-12
Hello,

I have installed ubuntu on my windows drive using wubi( ubuntu 8.04 desktop edition) with 5 GB disk size, Now i want to increase the disk size to 10 GB so that i can installed more software, Is there any way to do it??

Also,
When i login to forums from ubuntu ( using firefox 3 beta 5), it logs me in successfully and shows a "click here if ur browser doesnt redirect you" also, but after that the next page open doesnt shows me logged in. even if i try to make a post it asks for login and when i click login it redirects to same login page again and again, but thru windows i m successfully able to get login, what could be the problem????

---

### Post by Herman on 2008-09-13
Unfortunately, it has never been easy or quick to resize any Linux partition to the left.
Most people install Linux after Windows, so they leave Windows on the left of Linux, so Linux can only be resized to the left.

One way is to install Ubuntu again (new) and use the partition editor to resize Windows 5 GB smaller and install in the free space. 
When you boot it, mount your old Ubuntu installation and copy your files over to the new one. 
Then delete your original Ubuntu partition and resize the new one to the end of the disc or to your swap area.
That will take around 45 minutes if you're fast.

The other way is to resize Windows with a partition editor in a live CD such as Gnome Partition Editor in the Ubuntu Live CD or GParted LiveCD or Parted Magic.
Then 'move' Ubuntu to the right and then resize it to the left to fill the free space. 
That will take ages, it's a very slow process, best to let it run overnight.

Another idea would be to make a Partimage backup of your partition and store it in some other disk or media. 
Delete your old Ubuntu partition and resize Windows 5 GB smaller and restore the Partimage backup to the now larger partition.
You may need to resize the file system afterwards if Partimage doesn't do that for you.
(The partition size will be 10 GB, but the file system will still be 5 GB). You can use the resize2fs command for that, [What to do if your file system doesn't fit your partition]("http://users.bigpond.net.au/hermanzone/p10.htm#What_to_do_if_your_file_system_doesnt").

> I have installed ubuntu on my windows drive Why do you call it your 'Windows Drive'? :) (Just curious)

---

### Post by kemadruma on 2008-09-13
I have installed ubuntu desktop edition hence in "windows drive" of 20 gb , 5gb is allocated to ubuntu, now i want to change it to 10gb. i have installed ubuntu thru windows.

---

### Post by Herman on 2008-09-13
Do you mean you have installed Ubuntu inside your Windows partition? (A lot of Windows people use the words 'partition' and 'drive' interchangeably). For example, you may have made a Wubi install. I don;t know anything about those.
If that's the case, disregard my earlier post.

If you mean you installed Ubuntu in a hard disk which previously contained only a Windows installation, (by partitioning the hard disk), then my previous post should apply.

I'm still not clear about what it is you're trying to say. :)

---

### Post by kemadruma on 2008-09-13
yes i hav installed thru  wubi installer.

---

### Post by Herman on 2008-09-13
:oops: Oh, okay, sorry, please ignore me then, I don't know anything about wubi installations.
Hopefully someone else will come along and help.

Have you looked in the [Wubi]("http://ubuntuforums.org/forumdisplay.php?f=234") section of the forums?

EDIT: Here is a link that might help you: [How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

---

### Post by kemadruma on 2008-09-13
Thanks, i think i might get the answer there, as their are lots of posts like that

---

