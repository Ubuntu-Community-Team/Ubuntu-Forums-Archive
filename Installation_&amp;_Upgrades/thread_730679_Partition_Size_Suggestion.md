---
title: "Partition Size Suggestion"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by em4r1z on 2008-03-21
I'll install Ubuntu on an 80 Gb HD that has WinXP SP2 installated (about 3.5 Gb) and I'd like to hear some suggestions about a partition scheme (with sizes).

Facts:
- WinXP SP2 is there only because I needed to test my hardware (for this is a brand new machine) and will be gone by the end of the month.
- The *swap* partition will be 1 Gb in size as the machine has 2 Gb of RAM and it will be used for web browsing, office projects, music reproduction and basic graphic edition in GIMP and Inkscape.
- Regarding */var, /tmp* and */usr* partitions: Only daily used applications will be kept and I do belive in the 'one application per task' idea.

Should I add a */boot* partition if there's only going to be one Linux system?

I'm open to suggestions. Thanks in advance.

---

### Post by forestpixie on 2008-03-21
I wouldn't bother with /var, /tmp and /usr or /boot - I would though have a seperate /home partition 

/ 6.5Gb
/home 69Gb
swap 1Gb

when you get rid of XP add thespace to /

I'd use gparted - make an extended partition in which to put /home and swap, would leave / as a primary partition

---

### Post by Herman on 2008-03-21
I wouldn't even bother with /home, just make an integral install in a single /root partition.
You are going to be the only user aren't you? Who is it you are trying to restrict to a certian amount of disc useage? Your self?
Those old fashioned partitioning schemes were for old Unix mainframe servers, where a lot of people were each allowed a small amount of hard disc space on the server.
For a personal desktop machine you don't want restrictions, you want flexibility. Use directories not partitions, directories never need resizing, they are always exactly the size they need to be.

WinXp 3.5 GB
Ubuntu / (root) 75.5 GB
swap 1.0 GB

Regards, Herman :)

---

### Post by forestpixie on 2008-03-21
We've had this conversation before :D

---

### Post by sandysandy on 2008-03-21
>  WinXp 3.5 GB
Ubuntu / (root) 75.5 GB
[COLOR="Red"]swap 1.0 GB [/COLOR] 

since the RAM is 2 GB would 4 GB SWAP (twice the RAM size) be preferred or since 2GB is large enough u have recommended 1GB SWAP.

regards

---

### Post by forestpixie on 2008-03-21
Assumed op is running 32bit - 2Gb RAM and 4Gb swap would be a waste of space as it wouldn't normally be recognised. 

I have 1Gb each and have used a max of 40Mb of my swap - except when I was being ridiculous and seeing how high I could get it before I got bored.

With that much RAM you'd only need big swap if you were doing memory intensive things, or if you were going to hibernate then swap should equal RAM

---

### Post by em4r1z on 2008-03-21
Thanks on your quick replies.

I didn't mention a different partition for /home because I took it for granted and as it cotains my personal stuff you wouldn't be able to help me that much with its size.
I'm thinking on sepparate partitions because I've read this enhances system performance. As I understand, the access to /var is way higher than the access to say root and /usr, thus it might be a good idead to have it on a different partition. Do you think a desktop machine used for office tasks like this will notice the improvement from this?

I'm still unsure about the behaviour of /tmp.

Also, I'll be trying other distros on a virtual machine. Where does it store its files: /home, /usr, /var, all of them? I need to know this because it'll dramatically affect the space reserved for that section.

---

### Post by forestpixie on 2008-03-21
AFAIK virtual machines store everything inside the file it creates - including all those

---

### Post by em4r1z on 2008-03-22
Well, I think I'll have to solve this by trial and error. I'll install a couple of distros within some virtual machines using VirtualBox on my WinXP SP2 system and take notes of the sizes of the partitions right after the installation and again a couple of days later, once I have the applications I really use.

I've read various articles about it and this was particulary helpful:
[http://aplawrence.com/Linux/linux_partitioning.html](http://aplawrence.com/Linux/linux_partitioning.html)

I'll have at least four partitions: root, /var, /home and swap, keeping in mind that: **/usr** can be within root because even though it's rather large it doesn't change that often nor does it need backup; and that **/tmp** might need its own partition for it can be large and very active depending on my taks (I might put it in the same partition as /var.)
I'll post my results in case someone wants to do the same.

I was going to use XFS on all my partitions (bar the swap one, of course), do you think this is ok?

**forestpixie**, you're right and I didn't express clearly: I wanted to know where that file was stored. Now I know it's stored, by default, in your /home directory (or its equivalent in Windows).

---

### Post by Kiri on 2008-03-22
> **em4r1z said:**
> Thanks on your quick replies.

I'm thinking on sepparate partitions because I've read this enhances system performance. As I understand, the access to /var is way higher than the access to say root and /usr, thus it might be a good idead to have it on a different partition. Do you think a desktop machine used for office tasks like this will notice the improvement from this?



I think it will only improve performance if they are on partitions on different physical disks. If they are just partitions on the same disk, then it wont make any difference since the HD heads can only be in one place at a time. It may even decrease performance because they have to move between partitions. 

That is my understanding anyway. Someone please correct me if I'm wrong :)


Anyway, I would just keep the partitions:
xp
/
/home
/swap

---

### Post by forestpixie on 2008-03-22
I'd agree completely - it's all well and good having seperate partitions but the size for each is then fixed, from my understanding the seperate partition scenario is fine for a server.

It'd be better to have them in one / then they can use the space as they see fit - I can understand having a seperate /home but not the rest.

How exactly are you going to work out how much room to give /tmp for instance and how do you intend to deal with the problem if it's not enough. 

But all that said - this is linux and you can set it up howver you see fit and ther'll probably be someone here to help if you need it.

Good luck :D

---

### Post by em4r1z on 2008-03-22
> **Kiri said:**
> I think it will only improve performance if they are on partitions on different physical disks. If they are just partitions on the same disk, then it wont make any difference since the HD heads can only be in one place at a time. It may even decrease performance because they have to move between partitions.I got the same anwser by other users, thus you may be right. I based my ideas on different articles I read on the net, and various were based on servers. If you're right I'll go back to basics: root, swap and /home, there's no reason to 'complicate' things if the improvements aren't noticeable.

---

### Post by Kiri on 2008-03-22
But why does it matter if they are static or dynamic?

Honestly I dont think it will make much difference either way you do it in terms of performance. You can always try it if you want though :)
But since you wont have a point of reference, you will never know which one, if any, was better. And if you dont know, then does it matter? ;)

My point is, I dont think there will be any significant performance different, so I dont think you should worry too much about it. 
Personally I would go with the simplist possible partitioning scheme, since the more partitions, the more complex it becomes to manage and deal with disk space. (you will waste a lot more this way too)

---

### Post by em4r1z on 2008-03-22
**Kiri**, you replied to me right after I edited my post. I see your point and I'll most likely use three partitions (root, /home and swap.)
As I understand, and even if I don't need it, sepparating constantly accessed folders, like /var, from the rest improves system performance by managing disk usage.

---

### Post by Kiri on 2008-03-22
Well Im not an expert, so it may be that doing it like that might give you some improvement. I just cant see how. Different physical disks, yes. But just partitioning the one disk, I think the only advantage is when you want to be able to re-install and keep the other partitions intact. 
As for performance... I remain skeptical ;)

In windows there might be some possibility, because dividing it up would possibly stop the main OS partition getting fragmented so much, but apparently linux does not have much fragmentation...

If you have some information that suggests that it does help though, let us know, because I would be interested to check it out :)

---

### Post by forestpixie on 2008-03-22
As I see it disk usage will be less efficient, although I could be wrong. If you had say 100Gb of hdd space and decided to give various folders a fixed space you have to give it enough room to grow, therfore each folder will have wasted space until it's used.

By just having / and /home - all the /usr, /var etc. get the space they need as and when they need it.

I think you are right to return to the simple partition scenario.

---

### Post by em4r1z on 2008-03-22
I read various articles on the net (most of them based on servers). This is the last I read and one which resumes more or less what I've read elsewhere:
[http://aplawrence.com/Linux/linux_partitioning.html](http://aplawrence.com/Linux/linux_partitioning.html)

I might have confused 'to sepparate' with 'to part', for the articles I read might be talking about different physical disk and not just different partitions. Again, I'm not sure and I didn't save the articles, they were similar and 'recommended' this division.

---

### Post by forestpixie on 2008-03-22
I'd say that is talking about servers - if you're going to be using this pc at home you really aren't going to need to do it.

---

### Post by Herman on 2008-03-22
> I think it will only improve performance if they are on partitions on different physical disks. If they are just partitions on the same disk, then it wont make any difference since the HD heads can only be in one place at a time. It may even decrease performance because they have to move between partitions. 

That is my understanding anyway. Someone please correct me if I'm wrong :smile: I agree with Kiri.
It's conceivable that you might be able to get some performance improvement if you have your operating system spread out over several different hard disks. because you would be spreading the work out over more sets of read and write heads.

Hard disk read and write time is still a bottleneck in computer performance, lagging well behind advances in technology which has improved transfer speeds.

If you're after performance and you have PATA (IDE) hard drives then , you might also want to consider which how you set up your hard drives with regards to IDE cabling and jumper settings too,and the way you plan your partitions would need to take that into consideration as well, if you want best performance.  [2.9 Two devices on one cable - speed impact]("http://en.wikipedia.org/wiki/AT_Attachment#Two_devices_on_one_cable_-_speed_impact")

If you did go buy a special hard disk for each partition and split your operating up into four or more partitions in three or four hard disks I still don't think you'll be able to notice that much of a speed difference for the expense and effort you're going to be going to though. If you try that, keep us posted, it would be interesting to read about whether it really would make much difference or not.

If you only have a single hard disk and you're going to use it as a standard desktop PC, then I still maintain that you are best of avoiding the creation of rigid boundaries at all. You will only be fencing yourself in and creating un necessary restrictions on yourself.

In the old days it made sense to divide their Linux or Unix installation up into many parts, because of the risk of a file system collapsing or a hard disk failing. They didn't have the same technology in hard disks we have now, and they didn't have journalling file systems like ext3.
You might enjoy reading the pages beginning with this interesting link which will take you through the history of hard disks, [A Brief History of the Hard Disk Drive | StorageReview.com]("http://www.storagereview.com/guide/hist.html").
Warning, you will need a lot of time to read all that information. 
You will realize after that how much hard drive technology has improved since the days when Unix mainframe servers ruled by strict and snobbish system administrators dominated the computer industry. 
Only the computer administrators of old would have fond memories of those days, when they could achieve a sense of importance by imposing their strict rules on their poor subjects, forcing them to confine their use to a miserable disk space usage allowance, and when mail was stored in /var in a mail server. :lolflag:

On the other side, were their advsaries, poor computer users, who did their best to revolt, as described in the entertaining 3.5 MB .pdf you can download from this link, 
**[The UNIX-[B]HATERS Handbook** free pdf]("http://www.google.com.au/url?sa=t&ct=res&cd=9&url=http%3A%2F%2Flibrenix.com%2F%3Finode%3D3046&ei=_6PlR-mYN5-SpwTXmviYBg&usg=AFQjCNFut8GANPu2upMJwzWTeK7rjfE_2Q&sig2=Kjh3wthglkz2UuXSQqOvJA")[/B]

The conflict between these two opposing factions, 'rulers' and their 'subjects', was the main reason why it used to be seen as necessary to divide an operating system into rigid and restrictive little pieces.

As for improvements in the file system, here are three of my favourite links about the ext3 file system, 
[Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html")    [B]
[EXT3, Journaling Filesystem]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")[/B]   
[Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html")

If you read all that, by now you should be able to appreciate the improvements in file systems since the days of Minix and big old mainframe servers.

The modern tendency is for everyone to have their own computer and to move towards larger hard discs and nice, flexible integral operating system installations, at least for home PC users.
There's even a possibility we can eliminate the need for a separate swap area, which I think would be a good thing, [Reasons to choose swap files over swap partitions]("http://ubuntumagnet.com/2007/10/reasons-choose-swap-files-over-swap-partitions").

Regards, Herman :)

---

### Post by em4r1z on 2008-03-23
**Herman**, thanks for the extensive information and the references. While I didn't read evyerything there, I did check all the links provided and read the sections related to my question. I even started a 'file system information tour' after the read (I might try JFS instead of ext3.)

I'll use a different partition for /home because it's easier to reinstall the OS by doing so, and I'll use a different partition for swap because I'm sure it'll be smaller once I've used the OS enough (with 2 Gb of RAM for office tasks and basic graphic edition, the 1 Gb reserved for swap will most likely be redundant), and because I can share it with other distros. If I used a swap file I'd have one for each OS which I don't find efficient.

---

