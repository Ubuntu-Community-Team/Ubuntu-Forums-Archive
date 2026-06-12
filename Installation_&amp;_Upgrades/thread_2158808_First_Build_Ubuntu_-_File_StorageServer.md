---
title: "First Build Ubuntu - File Storage/Server"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by incurablegeek on 2013-06-30
I'll just list up my needs so as not to waste anyone's time:

1) I am not building a NAS.
2) I am not a Gamer; I use my computers for work.
3) I just want on-line networked storage of my work (Develop educational materials and curricula for gifted students)
4) My work computers are Windows 7 64 bit Ultimate - no plans for any MS upgrades (I read a lot and therefore consider MS to have lost its way [http://blog.zorinaq.com/?e=74](http://blog.zorinaq.com/?e=74) (succinct article)
 
Hardware:
1) Gigabit network - D-Link DGL-4100 Router, two Netgear unmanaged switches
2) Server: Corsair HAF case; Corsair 650/80 PSU, ASUS M5A97 EVO Motherboard; AMD 6-Core CPU; 16 GB Corsair RAM; Syba 6 GB/s 4-port SATA card; 128 GB Samsung SSD (OS); 5 X 3 TB Western Digital Caviar Green hdd's. (storage)
    Note: I prefer WD Greens cause they power down when not in use - again not a traditional NAS that would require WD Reds.

Can anyone be kind enough to give me some links, etc. to get started?
Note: I have been building, repairing and using computers for business for 25 years - but only DOS and Windows; Certifiably ignorant when it comes to Ubuntu.

Thank you. I know you guys to be especially kind to fresh-faced Newbies. :D

---

### Post by Old_Grey_Wolf on 2013-06-30
I think you may be looking for a Samba File Server. Here are some links:
[http://www.samba.org/samba/what_is_samba.html](http://www.samba.org/samba/what_is_samba.html)

[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)
[http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/](http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/)

---

### Post by incurablegeek on 2013-06-30
Hugely appreciated. I'll get started there.

Thank you for responding, and for being so kind in doing so. :)

Technology is just changing so fast; and quite honestly I can't keep up.

_________

So I'm guessing that because my server will be _networked to_ both _Linux and Win 7_ workstations, Ubuntu Server 12.04.2 LTS** alone will not suffice**?  It needs Samba as well?

---

### Post by Old_Grey_Wolf on 2013-06-30
I would wait for other responses. I am an old retired guy. There may be something newer and better. :)

I don't think Samba is installed by default. I think you have to install it. Either way, you still have to configure it.

---

### Post by Cheesemill on 2013-06-30
If you're looking for a quick and easy solution for file sharing then I wouldn't use Ubuntu. Instead take a look at [FreeNAS]("http://www.freenas.org/").

You say you're not looking to build a NAS but that's ***exactly*** what a file sharing server is.

> **incurablegeek said:**
> 1) I am not building a NAS.
3) I just want on-line networked storage of my work


Sounds like **N**etwork **A**ttached **S**torage to me :)

---

### Post by incurablegeek on 2013-06-30
No sir, I am definitely _**not**_ looking for NAS.

At the risk of sounding presumptuous or going into lots of irrelevant detail, I know quite a bit about NAS. More importantly, I understand why the architecture of NAS is wrong for my needs.

No sir, after much extensive study I can tell you two things I will never use: NAS and RAID.

@Old_Grey_Wolf
Please don't depreciate yourself so. You are not old; you are experienced.  :popcorn:

> I don't think Samba is installed by default. I think you have to install it. Either way, you still have to configure it. OK, I can respect your opinion that I need some form of "overlay" on Ubuntu Server but I don't understand why. I would assume that the Ubuntu server would see my files as "raw data" and not care if they are stored as FAT, NTFS, or ever ReFS. Is that the reason, OGF?

Since FAT, NTFS and ReFS are simply hard drive formats, I am guessing they are irrelevant to Ubuntu server. What apparently Samba is, just guessing mind you, is an interpreter or translator of Windows File Extensions. So what happens if some of my work is done on Ubuntu (which I will migrate to) and some of the legacy work is on Windows, can both be stored on hard drives managed by Ubuntu Server?

Trust me. I shall be reading much more on this so as not to be a drain on you guys.

...............

Note to all: My question is _how to set up an Ubuntu File Server for on-site storage_. Technically all my computers presently do that via the network. However, I want centralized storage as well, so I can keep better track of my work.

What I do not need is to get derailed by being told I need something else, don't know what I really need, etc. Please. I know you folks mean well but I do know what I need.

[B]Please disregard my question. I'm just going to do things the easy way.
[/B]
Thanks for your efforts. You guys are wonderful. :D

---

### Post by CharlesA on 2013-06-30
> **incurablegeek said:**
> [B]Please disregard my question. I'm just going to do things the easy way.
[/B]
Thanks for your efforts. You guys are wonderful. :D

What is the easy way?

If you are really looking for some sort of centralized file storage, and you aren't interested in RAID, what else would you be using?

I have found this pretty interesting:
[http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04](http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04)

Maybe it will help you, even though you have said you are going to do it the "easy" way without specifying what way that is.

---

### Post by incurablegeek on 2013-07-01
My apologies *[COLOR=#0000ff]Charles A[/COLOR]* for not responding sooner.

The "easy way" is just to install Win 7 64 bit Ultimate, which will contain all the hard drives for centralized record keeping, as opposed to having my files backed up willy-nilly on multiple hard drives throughout the network.

The only thing that made me take Microsoft seriously was the new file system ReFS, which is in MS Server 2012 and can be added on to Windows 8. From what I have read (volumes) ReFS is a real improvement over NTFS which came out in 1993 and has served us well.

However,

1) Doing so would just postpone the move to Linux (Ubuntu) which I have been planning to make for a couple of years now.

2) Learning Server 2012 has absolutely no transfer value for me in e-commerce, because Linux is the Big Dog there.

3) Windows 8 is an embarrassment, so there is also no value in learning it.

4) Using Linux as a server looks like it's just going to further distract me from my actual work - educational materials development.

Now although I need something "quick and dirty", and Windows 7 is actually very nice mind you, using Win 7 in lieu of Linux only postpones the inevitable, i.e. learning Linux by using it, not reading about it.

After weeks of reading, I now fully understand:

1) the weaknesses and vulnerabilities of NAS, so that's out. NAS is more for the AV enthusiast actually.
2) that RAID to know that it is only for people with too much time on their hands for problem solving. Even at it's best RAID offers me nothing.

And, no, I am not interested in debating why the above two are wrong for my needs. I have thrashed that about on other forums and with my tech friends, quite good ones in hardware (not Linux).

What I do have an exceedingly open mind to is how I can **file exchange on my network with** my single (for now) **Ubuntu Linux** desktop. That's the direction my reading will take me for awhile. :(

---

### Post by CharlesA on 2013-07-01
> **incurablegeek said:**
> My apologies *[COLOR=#0000ff]Charles A[/COLOR]* for not responding sooner.

No worries. :)

> The "easy way" is just to install Win 7 64 bit Ultimate, which will contain all the hard drives for centralized record keeping, as opposed to having my files backed up willy-nilly on multiple hard drives throughout the network.

How would you be arranging the drives? Are they going to be grouped together, or set up as single drives?

I was using a Windows XP box to serve files a few years ago and was looking to moving to Win2K3, but found the cost outrageous, which is why I moved over to Linux. So far I haven't looked back. The original XP box was serving files via Windows file sharing (aka Samba) from a USB 2.0 drive, which needless to say was pathetically slow. After that machine died, I build a basic dual core box and loaded it with Ubuntu 9.04, that box lasted around 3 years or so before I retired it and built an i7 box so it could handle more Virtual Machines at the same time.

I use Samba to share files with Windows (and other *nix machines) as well as ssh/sftp if I need it. That was the main reason I wanted to build a home server - to store files in a centralized place and have it set up so I didn't have to worry about doing backups on my own.

> The only thing that made me take Microsoft seriously was the new file system ReFS, which is in MS Server 2012 and can be added on to Windows 8. From what I have read (volumes) ReFS is a real improvement over NTFS which came out in 1993 and has served us well.

I haven't really dealt with Server 2012 that much outside of work, and I have heard of ReFS, but I don't think I have seen it implemented anywhere.

> 1) Doing so would just postpone the move to Linux (Ubuntu) which I have been planning to make for a couple of years now.

True. I wasn't that excited about Linux until I discovered it can do almost everything a Windows server can, but I've also been using it for 4 - 5 years now.

> 4) Using Linux as a server looks like it's just going to further distract me from my actual work - educational materials development.

How so? Once you get it set up, it's pretty much "stick it in a corner and forget about it." You can set it to apply updates automatically and it will pretty much manage itself. I do manual maintenance whenever I do my monthly backups, but that is around once a month and the backups maybe take 30-60-90 minutes to complete, but most of the time the procedure for these backups is just me logging in and running a BASH script manually, then waiting for it to complete, which gives me time to do other things.

> Now although I need something "quick and dirty", and Windows 7 is actually very nice mind you, using Win 7 in lieu of Linux only postpones the inevitable, i.e. learning Linux by using it, not reading about it.

That is true. There is only so much you can learn by reading. Most of my Linux knowledge has come from reading howtos and actually doing them and either succeeding or breaking things. If you aren't totally convinced or want to switch over to Linux full time, I would suggest running a Virtual Machine off one of your Windows machines, so you can play with it and get familiar with it before switching over, so you don't jump in head first and reach epic levels of frustration.

> 1) the weaknesses and vulnerabilities of NAS, so that's out. NAS is more for the AV enthusiast actually.



> 2) that RAID to know that it is only for people with too much time on their hands for problem solving. Even at it's best RAID offers me nothing.

No really. RAID is quite simple, if you break it down. [This link might help explain the basics.]("http://www.thegeekstuff.com/2010/08/raid-levels-tutorial/") [Here's another one]("https://wiki.archlinux.org/index.php/RAID") that does a good job at explaining the different RAID levels and it has some links to how to configure RAID on a Linux system.

Basically, there are 4 major RAID types, RAID 0 (striped), RAID 1 (mirrored), RAID 5 (striped with parity, able to handle the loss of 1 disk), RAID 6 (striped with parity, about to handle the loss of 2 disks).

I use RAID 5 at the moment with 4 x 2TB drives so I have one large logical drive that can hold around 6TB of data. I am using RAID 5 so I don't have to worry about having the whole thing blow up in my face if one of the drives dies. I will be moving to RAID 6 as soon as my new raid card comes in, so the array can handle 2 disks going out before it breaks. The reason I am using RAID is being I wanted to have a boatload of storage and I wanted to have it be at least somewhat redundant in case one of the drives craps out while I am at work or something. I do daily backups off the array and so far I haven't had a drive die or lose data, but RAID is not a backup solution - it is a method of pooling disks and has the ability to still run if one or more disks go out, depending on the RAID level.

With all that being said, what does RAID not offer you that you can get otherwise? I use it for redundancy, as I stated before and it has worked wonders. If you are just starting out, I would suggest checking out mdadm - [particularly this tutorial]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm").

> And, no, I am not interested in debating why the above two are wrong for my needs. I have thrashed that about on other forums and with my tech friends, quite good ones in hardware (not Linux).

What I do have an exceedingly open mind to is how I can **file exchange on my network with** my single (for now) **Ubuntu Linux** desktop. That's the direction my reading will take me for awhile. :(

Depending on your environment, you can do a whole lot of things. I use Samba being I'm mostly serving to Windows machines, but Network File System works for both Linux and OSX just fine and it is lighter than Samba.

I think the first thing you need to do is figure out how you are going to arrange your drives on your server as that will tell you how you will need to proceed to accomplish your goals.

---

### Post by incurablegeek on 2013-07-01
First of all, it's been difficult for me to express myself as a newcomer on every forum except OCN where they expected me from the get-go (years ago) to be "technical".

1) I understand RAID very, very well. It is not for me.
2) I also understand NAS, and am not interested.
3) I would not expect you to know about ReFS. It's just making its debut, but it will replace NTFS within a couple of years - max. ReFS is just better in every way.  [https://blogs.technet.com/b/askpfeplat/archive/2013/01/02/windows-server-2012-does-refs-replace-ntfs-when-should-i-use-it.aspx?Redirected=true](https://blogs.technet.com/b/askpfeplat/archive/2013/01/02/windows-server-2012-does-refs-replace-ntfs-when-should-i-use-it.aspx?Redirected=true)   (Oh, when I said I wouldn't expect you to know about ReFS, I wasn't trying to be snippy. I hadn't heard about it either until I began to read up on Server 2012.)

In answer to your questions, my file storage will be on an M5A97 EVO board with an AMD 6 core, 16 GB of RAM. 5 X 3 TB Western Digital Green Drives - just set up in JBOD fashion. That way I can specify the size of the partitions/what drives, etc. my files store to. Nothing spectacular, very simple. Only difference between this file storage computer and my others is that I will only be using it for file backup - no programs installed.

Just in 5 minutes of reading, I see that there are ways to exchange files between my computers running Win 7 and my Linux box. My next project, I guess. :)

Again, I've been building, diagnosing, working with computers for many years ago. Actually a tech at Microsoft said I was one of the only people he had actually talked to who installed and made Win NT 3.51 work. A few months later NT 4.0 came out as a free upgrade, and I used it for years. In my opinion, it's the finest OS Microsoft ever came out with.

So with computers, my knowledge is a bit like Swiss Cheese - areas of deep understanding with empty areas of no understanding (right now that would be Linux)

Just to arrive at the above stupidly simple solution (basically, use what I know) required three weeks of intense reading during which I did my best to keep an open mind about Microsoft, but now realize is as I suspected for quite awhile now - not long for the world. You've probably seen some version of the following already  [http://blog.zorinaq.com/?e=74](http://blog.zorinaq.com/?e=74)   (The problem with MS is systemic.)

---

### Post by CharlesA on 2013-07-01
Ok, then.

If you ever want a Linux solution that works well with a JOBD fashion, check out SnapRAID: [http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04](http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04)

---

### Post by incurablegeek on 2013-07-01
Charles A, you've been very kind; and I thank you for your patience and understanding.

I think right now it makes sense for me to start small and grow. I'll start with Ubuntu Desktop and go from there. Network Ubuntu with my Win 7 computers, file share and, when no I'm no longer so lost and confused, get back with you.

Kind of suffering from Brain-Ache if you understand what I mean.

One thing I promise. I will ask questions about Ubuntu Desktop, only after I have read everything on this great site. 

I really don't want to annoy you guys with questions I could answer on my own.

---

### Post by CharlesA on 2013-07-01
Good luck, and don't hesitate to ask if you have any questions.

---

