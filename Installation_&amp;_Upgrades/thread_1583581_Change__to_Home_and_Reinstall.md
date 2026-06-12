---
title: "Change / to /Home and Reinstall"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by Laysan_A on 2010-09-28
Hi,

I am currently set-up with everything on one partition. I've created both a swap and root partition, but I haven't taken the plunge and changed anything yet.

I want to reinstall lucid while saving the contents of my home dir. (Before you ask, no, I don't have an external drive for back-up)

It seems a simple matter to specify my root partition as / in gparted during the install - there's nothing on it yet. But I'm not sure how to handle the change of my large partition from / to /home without losing anything. 

Do I need to rename my current home and associate my new home with the partition before I reinstall?

And what about the new root partition: If I don't change the association for it before running the installation disk, will the installation program insist on reformatting everything? (By 'everything' I mean /Home, too?) And then there's the issue of what happens if I change / to /Home. Nothing will work after that, will it?

There's a lot about moving /Home, and I've found what appears to be a good guide: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)
But it's not exactly the same, since I'm not moving /home to a different partition.

As you can see, I'm not really comfortable with this, and I have a lot of uncertainty about how to proceed. Help?

---

### Post by mörgæs on 2010-09-28
No matter if you are upgrading or just a daily user of the system, a back-up is indispensable. I wouldn't advice you to go further without.

---

### Post by nothingspecial on 2010-09-28
> **mörgæs said:**
> No matter if you are upgrading or just a daily user of the system, a back-up is indispensable. I wouldn't advice you to go further without.

That is a must.

However, when you do the install and get to the partitioning bit, choose manual.

Choose to use the root partition as an ext4 journaling file system, choose a mountpoint of / and put a tick in the format box.

Choose to use the home partition as an ext4 journaling file system, choose a mountpoint of /home but [SIZE=4][COLOR=Red]do not[/COLOR][/SIZE] put a tick in the format box.

I would definitely backup first though. Things can go wrong.

---

### Post by Laysan_A on 2010-09-28
Hi Thanks for the replies. My primary partition is already formatted as ext3, as is the intended root partition. When I did the formatting there were still some problems with ext4. 

I can't just label a partition ext4 when it's been formatted as ext3, can I? And is it advisable to use a different file system for home and root?

As for the back-up, well, I'm just going to have to take my chances...

---

### Post by nothingspecial on 2010-09-28
Yeah use it ext3 instead.

No problems with different file systems, well ext3 and ext4 anyway.

---

### Post by Laysan_A on 2010-09-28
Thanks for the help, nothingspecial. I think I will format the root partition to ext4. 

Anyone got any advice about the best way to go about keeping /Home in the same partition where root is now (without loosing anything)?

At least some words of encouragement to allay my fears?

---

### Post by nothingspecial on 2010-09-29
You've not done this the way I would have done.

I would have created a /home partition, moved my /home to it, then reinstalled ubuntu over my existing install.

However, theoretically you should just be able to remove everything else once you installed. I am not 100% sure on this.

Also bear in mind You will have to remove the /home directory without removing eveything in it, otherwise once you have installed, all your configs will be in /home/home/laysan instead of /home/laysan/ if you see what I mean and nothing will work.

---

### Post by Laysan_A on 2010-09-29
Right. I'd pretty much resigned myself to the idea that I'll still have to actually copy/move everything to the new /Home folder, even though they're in the same basic place (unless someone knows some fancy linux-fu to avoid it). The link on moving /Home I included in my first post has what appears to be a good command for moving everything without changing it.

Hmm...I've been thinking about this, and I'm not sure I have to move anything. Home already sits in root. Basically all I have to do, I think, is reassign the partition to /home from a root terminal in the installation disk. That should do it, right? Then I just come back after the installation and delete all the other files? 

On third thought, Im not sure this'll work...I don't know what linux will do when the partition is reassigned. Will it ignore the already existing /home and create another, with everything, the old root included, inside it, and if not, how will it deal with an entire directory structure that will essentially cease to exist? Maybe it will simply refuse to accept the change?

Help?

---

### Post by Laysan_A on 2010-09-30
Bump?

---

### Post by woodmaster on 2010-09-30
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Laysan_A on 2010-09-30
Hi woodmaster,

Thanks for replying. Yeah, that psychocats link was developed from the post I linked to in my first post. It's a good step by step for moving your /home to a new partition, but that is not precisely what I'm doing, and I have some doubts/questions about how it is different.

---

### Post by woodmaster on 2010-09-30
Not sure I'm understanding you?  What you want to do is preserve your home folders for the purpose of upgrading(by reinstalling,) right?  In that case this will indeed do that and when you reinstall, just don't format the /home partition you created by choosing an advanced partition scheme as posted above.  Other than that, I can't seem to see what you are trying to accomplish, unless I am reading wrong...

---

### Post by Laysan_A on 2010-10-01
Hi woodmaster, thanks for sticking with me.

I also posted on the kubuntu forum and I think I got the answers I need. 

It's been a long time since I've installed via disk. Since 8.04 I've always used the auto-upgrade, because during my first attempts to install hardy (and another distro before that) I couldn't get the partitioner to do what I wanted. Also, everything I've read about installation suggested the only way to save /home was to have it on a separate partition.

Hence the first part of my question...Come to find out, if I choose to install manually I can not only choose to install ONLY to my new root partition, but I can also designate my current large partition as /home, and grub and fstab will automatically be updated. 

This leaves me with only the second part of my question: What about all my files and my old root directory structure? I have been assured that my old directory structure will appear in my new /home folder, so all I have to do is delete everything I don't want, then copy what I do want into the new /home/username folder. 

Pretty cool, huh?

It's actually very simple. It's no wonder everyone has been having trouble understanding what I'm trying to do. Everyone was probably wondering why I was asking so many questions about something that seemed so straightforward to them! They must've been saying to themselves, "He can't be doing what I think he's doing...It MUST be something else, something I'm just not understanding..."

Well, my heartfelt thanks to everyone who offered their aid.

---

