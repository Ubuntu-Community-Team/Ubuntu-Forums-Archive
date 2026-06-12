---
title: "[Solved] Install ubuntu 12.04 server on IBM xserver 226 8488"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by way3000 on 2013-11-11
Hello, and sorry if I could not find this in the forum.

I have a IBM Xserver 226 - 8488

I am trying to install Ubuntu Server 12.04, but I keep getting a dead end around the partitioning part.
I have made a raid 0 of 3 disks, resulting in 220GB and 3GB Ram on a Xeon 3.0 Ghz CPU.
I can run my install as far as to where I am asked to partition the HD. 

First I tried a normal install, but when I was asked as to where to place Grub it could not install it, and I gave up.
Then I tried this guide:

[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

I got to the "greate MD device" part, and I can then pick the HD's  (see picture)

and I can pick one or two, and the next step takes me directly back to the menu where i can "create" or "delete" a MD device (if I press the delete it dosen't find one) so it dosen't create a MD device.
(I do not know what a MD device is, but according to the guide I need it)

I am stuck here and don't know what to do from now on.

I am thinking of trying a raid 1 setup, but that would put me back to a 70ish HD and that would be kinda bad. (having 3 HD's in the server, I assume I could make 2 of them in a raid 1 and one as an ordinary HD?)

Thanks in advance.


picture:
[IMG]http://theisel.dk/myfiles/pic2.jpg[/IMG]

---

### Post by way3000 on 2013-11-12
Update: right now I will try a Raid level 1 + 1 hot-spare disk, and reply how that goes.

---

### Post by way3000 on 2013-11-12
And same problem... noone have any ideas?

---

### Post by Bashing-om on 2013-11-12
way3000; Hi !

It has been some time since I set up a server, recently I responded to a similar thread, rather than repeat it, this is the link. That reference is to raid 1, but the same procedure should apply for setting up raid level 0.

We are talking "software" raid right ?

[http://ubuntuforums.org/showthread.php?t=2186022&p=12839844#post12839844](http://ubuntuforums.org/showthread.php?t=2186022&p=12839844#post12839844)

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by way3000 on 2013-11-12
Hello Bashing-om
I belive the server uses a SCSI hardware raid, unfortunately, which apparently complicates it (and I have that!)
and I have a difficult time to see if what I am actually doing is setting up a software raid within the hardware raid (which is bound to fail) but I am unsure, unfortunately.

I will read your thread and try whatever it says, then report back the result.

---

### Post by Bashing-om on 2013-11-12
way3000; Hey ..

That reference is strictly for "software" raid.
I would expect hardware raid to be initiated in bios. I do not know how friendly ubuntu is in relation to "hardware" raid. Some time ago, not. Then it was argued that SW raid was as good as and in some respects better managed than hardware raid on ubuntu.

I have no experience with hardware raid - I did try to set it up some years past, gave up and used ubuntu's software raid. I am sure others can offer updated info with better advise.

[INDENT][INDENT]sometimes I wonder, othertimes I just do not know
[/INDENT][/INDENT]

---

### Post by way3000 on 2013-11-12
I am trying to "skip it" by seeing if using the 3 drives as normal drives and then use software raid, but I can't seem to see how to do that, and the serverguide only provides raid options -.- sadly.

So it seems, as of now, I cannot get ubuntu server on a hw raid machine. I actually thought that was standard today.

---

### Post by Bashing-om on 2013-11-12
way3000; I feel for you.

Are you aware that there are 3 types of raid ?
True hardware raid .. incorporating a physical raid controller ... high dollar;
Fake raid so called as it is a setup on the motherboard;
and then there is software raid .//

One must know what they are working with before hand. If I am not to mistaken, if hardware raid or fake raid have been set up before, in order to use "software raid" the old meta data must be removed (??). Pretty sure that is the case.
Not much but,
[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by way3000 on 2013-11-12
It seems I run a Hardware raid (SCSI controller) so, those meta data, sorry, I just don't know what that is :S 

You are a big help and thank you alot for that! just sad that Ubuntu don't support hardware raids as I thought those were ideal for exactly the server install. Thinking of trying out CentOS as it should be compatible with HW raids (both 0 and 1)

OR I can see if I can "rewire" a normal harddrive into the server to use ubuntu on (that dosen't really benefit from the servers setup, but it's one way I think, if it's possible that is)

---

### Post by Bashing-om on 2013-11-12
Hardware raid controllers are supported for the most part:
[http://askubuntu.com/questions/26695/well-supported-hardware-raid-controller](http://askubuntu.com/questions/26695/well-supported-hardware-raid-controller)
[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://augmentedtrader.wordpress.com/2012/05/13/10-things-raid/](http://augmentedtrader.wordpress.com/2012/05/13/10-things-raid/)

Might be a good idea to check the catalog and see if your controller is on the known list.

'till others have better advise

---

### Post by way3000 on 2013-11-12
Ok, first, thanks bashing-om for your help:

Here is what I did to "succeed" in this.

First: My raid controller dosen't seem to be supported here: [http://www.ubuntu.com/certification/catalog/category/RAID/](http://www.ubuntu.com/certification/catalog/category/RAID/)  as I run a integrated IBM ServRAID-7e.

Second: (follow link and read especially my newsflash reply) [http://www.linuxquestions.org/questions/showthread.php?p=5063267#post5063267](http://www.linuxquestions.org/questions/showthread.php?p=5063267#post5063267)

In there I specify what I especially did to make this work, and it does somehow.

I hope this helps others, especially the Ubuntu team to implement whatever CentOS has that "we" don't have, so we can use Ubuntu on the HW raids the "older" servers use :)

Again, thank you for your kind help, I hope it will be possible for me to repay you some day.

---

### Post by Bashing-om on 2013-11-12
way3000; Outstanding !

You too do good work !

Please mark this thread as solved, aids others seeking a solution and in keeping the forum tidy;
1st post -> thread tools.

[INDENT][INDENT]perseverance pays off
[/INDENT][/INDENT]

---

