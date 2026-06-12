---
title: "Noob doesn't &quot;get&quot; mount points"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by Mr_Smoke on 2007-07-20
Hi, my name is Rob and I used M$ Windows everyday for the last 10 years.  ( chorus of "Hi Rob" )  It makes me question my self worth how much abuse I have put myself through trying to use such a dangerous product for so long, knowing how bad it is for me.  ( chorus of " You are among friends now,  Take it 'One day at a time' " )  Well I have hit rock bottom and must give up Windows but can't do it cold turkey so I now need a multi boot system.  

The current problem seems to be mount points.  I do not understand the concept after google(ing) for the last several minutes.  Any general tips are welcome as well as specifics to my individual installation will be greatly appreciated.  

HDD #1  80 G   winME    boots fine not a problem.  It does have lost clusters that report errors when installing Ubuntu ( I ignore ) Cant convert the lost clusters cause fdisk, and dfrag haven't worked in Win ME for years now.  Can't re-install ME cause my KEY from M$ doesn't work.  XP is new this month here too.  

HDD #2 300G (i read some multi boot tips here which lead me to this partitions setup) (I assumed mount points, and got it wrong)

name - format -- size ----- device ---  mount point
Win XP - NTFS ---  60G -- dev/sda1 -- /media/sda1
Shared - Fat32 - 190G -- dev/sda1 -- /media/sda2
?????? - Ext3 --- 10G ---- dev/sda6 -- /home      --------  how does this one work for sys setings?
ubuntu  Ext3 --- 55G ---- dev/sda8 -- /
swap --- swap -- 3G ----- dev/sda7 -- swap

Is it obvious where I went wrong?  Can I name the mount points anything I want? 

 I need your help to kick the M$ habit.

Thanks, Mr Smoke

---

### Post by xlinuks on 2007-07-20
Just install Ubuntu which will take care of itself, it won't touch your windows partition unless you explicitly choose that option (to use the whole HDD).
The partitioning is not worth the lots of attention you seem to pay to it.
After installing Ubuntu it will automatically take care for you to be able to choose at system startup what OS you want to boot into: Ubuntu or Windows.
Life is great :)

---

### Post by Mr_Smoke on 2007-07-20
I understand that Ubuntu is smater than I am, but can someone help to educate me on this more versitile installation and formatting?

---

### Post by davidjmayo on 2007-07-20
HI Rob

Cam you just clarify for me. You have set up the partitions but not installed ubuntu yet. Right?

If so how did you set up these partitions (what software did you use)?

---

### Post by wpshooter on 2007-07-20
Rob:

Let the Live CD show you where (what drive) you want to install to, then choose manual partitioning and then partition in this vain:

/ = root partition - file system type ext3
/home = home partition - file system type ext3
/swap = swap partition - file system type swap

I would highly recommend that you always make a separate /home partition.

Good luck.

---

### Post by Cappy on 2007-07-20
I see one thing:
You need a 50MB partition in front of Windows XP to allow GRUB to install. You mount it as /boot as the mount point when installing ubuntu. This may be outdated. Confirm or Deny?

If you have a choice, I would use the 55GB for /home and the 10GB for / since you are going to be downloading most stuff onto your /home partition.

---

### Post by stchman on 2007-07-20
> **Mr_Smoke said:**
> Hi, my name is Rob and I used M$ Windows everyday for the last 10 years.  ( chorus of "Hi Rob" )  It makes me question my self worth how much abuse I have put myself through trying to use such a dangerous product for so long, knowing how bad it is for me.  ( chorus of " You are among friends now,  Take it 'One day at a time' " )  Well I have hit rock bottom and must give up Windows but can't do it cold turkey so I now need a multi boot system.  

The current problem seems to be mount points.  I do not understand the concept after google(ing) for the last several minutes.  Any general tips are welcome as well as specifics to my individual installation will be greatly appreciated.  

HDD #1  80 G   winME    boots fine not a problem.  It does have lost clusters that report errors when installing Ubuntu ( I ignore ) Cant convert the lost clusters cause fdisk, and dfrag haven't worked in Win ME for years now.  Can't re-install ME cause my KEY from M$ doesn't work.  XP is new this month here too.  

HDD #2 300G (i read some multi boot tips here which lead me to this partitions setup) (I assumed mount points, and got it wrong)

name - format -- size ----- device ---  mount point
Win XP - NTFS ---  60G -- dev/sda1 -- /media/sda1
Shared - Fat32 - 190G -- dev/sda1 -- /media/sda2
?????? - Ext3 --- 10G ---- dev/sda6 -- /home      --------  how does this one work for sys setings?
ubuntu  Ext3 --- 55G ---- dev/sda8 -- /
swap --- swap -- 3G ----- dev/sda7 -- swap

Is it obvious where I went wrong?  Can I name the mount points anything I want? 

 I need your help to kick the M$ habit.

Thanks, Mr Smoke

Welcome to the club.  Once you get the hang of Linux all will be good.  Refer to my site about getting your install setup.  i also have a section on partition access and such.

---

### Post by Rui Pais on 2007-07-20
> **Cappy said:**
> I see one thing:
You need a 50MB partition in front of Windows XP to allow GRUB to install. You mount it as /boot as the mount point when installing ubuntu. This may be outdated. Confirm or Deny?
No, not necessary. grub files will go to /boot/ folder either on / (root) or a separated partition anywhere on HD. Grub loader usually is installed on MBR. The only precaution is installing Windows 1st, to avoid it overwritten MBR.
> If you have a choice, I would use the 55GB for /home and the 10GB for / since you are going to be downloading most stuff onto your /home partition.
I agree with you on more space to home is a good choice... but downloading stuff related with the system, upgrades, will go to root, some times big packages like upgrades of OO2.


@OP
> Is it obvious where I went wrong? Can I name the mount points anything I want? 
Yes you can make mount points anywhere and name it what you want. The only delicate thing (and installer will do that for you) is ensure that system has correct mount points for system specific folders. They are set on file /etc/fstab. 

Under Linux all folders tree is relative to this abstract scheme of mount points. There is no C:, D:... If you have 4 Linux on the same machine they all be mounted as / and the homes at /home, no matter which partitions they are installed. 
Same is valid for all folders inside /. They can be on separated partitions, The only thing need to make it valid and got a working system is they are correctly assigned on fstab. 
But again installer will do that for you.

Still on you question and maybe clarifying a bit. 
You will need to have a /home folder with that name. You cannot change that. But you can change the other non-system mount points. As an example, instead of /media/sda1 and /media/sda2 you can make a /media/Windows and a /media/Documents and mount sda1 and sda2 on that folders :) Is up to you.

An extra tip. If you make a mount point on /media/ it will appear on your desktop (using Ubuntu/Gnome) as special folders, but if you don't want them there you can make it, for instance, on traditional linux path /mnt/

hope that don't make it even more confuse...

---

### Post by Mr_Smoke on 2007-07-20
Thanks for all the good tips.

I'll try to install Ubuntu once again now.  I hope the partitions work this time. If not, you'll see a fresh question by Mr Smoke in a few hours.

Peace

Thread closed

---

### Post by HermanAB on 2007-07-20
I keep giving people this important tip:  Once you have your system up and running *don't* experiment on it - Install the free VMware Server and install another pair of Ubuntu and Windoze machines inside that.  Then you can experiment to your heart's content in virtual machines without fsck'ing up your host system.

At home, I use Windows XP once a year to do my taxes using VMware Server.  

At work, I have VMware all over the place - it saves an enormous amount of time and effort when deploying systems, since I keep pre-installed copies of Windows 98 SE, Windows XP Pro, Windows 2003, RedHat 5, Ubuntu and others.  If I need something special, I make a copy of one of those and off I go within a couple of minutes instead of wasting hours to re-install a machine from scratch.

'Hope this helps!

Herman

---

