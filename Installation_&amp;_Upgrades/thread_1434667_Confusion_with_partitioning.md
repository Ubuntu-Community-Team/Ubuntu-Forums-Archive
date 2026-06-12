---
title: "Confusion with partitioning"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by schoft on 2010-03-20
Hey there,  I am in the process of installing BT4. At the partitioning stage of the install, i noticed that it could not detect my windows 7 like in the example screenshot they provided with the guide: [click here]("http://www.backtrack-linux.org/images/bt4inst-05.png")   However, This is how the partition stage looks like on my system:
  [IMG]http://img406.imageshack.us/img406/2877/snapshot1ab.png[/IMG] 


 Why can't i see Windows here? I remember from the partition editor in windows, that my primary C:\ disk had 3 partitions. A system reserve,  some small unallocated space and 157 gb wich belongs to windows.  My question is, why does it fail to detect the windows. I'm guessing the ubuntu installer only sees the 6gb of unallocated space as the only possible option to install on. So Ubuntu can only be installed on unallocated space ? Ill have to narrow down the partition that C:\ is on, make the unallocated partition bigger and put Ubuntu on it.   Did i answer my question there? I am being paranoid because in no case can i loose files :_)  Some clarification will be more than welcome 

Here's a screenshot of my gParted
[IMG]http://img221.imageshack.us/img221/3195/snapshot2d.png[/IMG]

---

### Post by wilee-nilee on 2010-03-20
Gparted shows a NTFS partitions. Go to the disk manager in W7 to do any shrinking or resizing of the MS portion, defrag with a optimizer defrag first like auslogics,
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/).
Then make sure after you have resized the W7 partitions that it boots then try the BT4 install.

I would make sure you realize that grub will be your boot manager and what version it is, legacy or grub2, just in case of any need of loading the MBR.

If your trying BT4 because of it's claims of being a hackers distro, you might consider making sure you have everything backed up no matter what, and know how to reinstall or recover W7 and any other install.

---

### Post by schoft on 2010-03-20
I'm trying BT4 because i love to learn how computers work. I have basic knowledge of unix. I am aware of the possibilities but ill asure you that im not an evil person. And im aware that you'll have second thoughts on helping someone with newbie questions that is trying a advanced OS. Having that said;

What's so bad about having Grub? I'm sure 7 can be dual booted fine from there.

The real question is; What is the 6.1gb partition on my disk ? I can't shrink nor make it larger. I'm guessing ill have to split my current partition that holds windows into 2. Not?

Thanks for the help

---

### Post by 2hot6ft2 on 2010-03-20
> **schoft said:**
> I'm trying BT4 because i love to learn how computers work. I have basic knowledge of unix. I am aware of the possibilities but ill asure you that im not an evil person. And im aware that you'll have second thoughts on helping someone with newbie questions that is trying a advanced OS. Having that said;

What's so bad about having Grub? I'm sure 7 can be dual booted fine from there.

The real question is; What is the 6.1gb partition on my disk ? I can't shrink nor make it larger. I'm guessing ill have to split my current partition that holds windows into 2. Not?

Thanks for the help
The 6 GB partition is just as it says it's the linux swap partition BT4 will use it. Click on Manual in the partitioner to see what partitions are really there. What you're seeing is normal.

And like has already been mentioned you should shrink the windows partition using the windows disk management utility, along with windows disk cleanup and defrag before proceeding with the installer.

Also with how much stuff you have in windows there is no room for another operating system. You'll have to remove some of the stuff on windows. Yes you would have to split some of the space used by windows off for BT4 otherwise there is no way you're going to be installing BT4 or any operating system for that matter.

I surprised windows isn't screaming at you that there is less than 2% free disk space.

---

### Post by wilee-nilee on 2010-03-20
> **schoft said:**
> I'm trying BT4 because i love to learn how computers work. I have basic knowledge of unix. I am aware of the possibilities but ill asure you that im not an evil person. And im aware that you'll have second thoughts on helping someone with newbie questions that is trying a advanced OS. Having that said;

What's so bad about having Grub? I'm sure 7 can be dual booted fine from there.

The real question is; What is the 6.1gb partition on my disk ? I can't shrink nor make it larger. I'm guessing ill have to split my current partition that holds windows into 2. Not?

Thanks for the help

I'm only concerned that you don't lose anything. Grub is great, I again just was sort of Phishing for your knowledge level, and making sure I don't lead you astray.

The 6.1 gig is a extended partition with the swap inside which is some what normal but the extended part would normally be larger and have the Linux OS in a logical  with the swap in it's own partition. So delete the 6.1 resize the W7 partition with the W7 disk manager leaving a open space for the install and install you should be fine.

Just make sure when you get to the install that you watch that the ntfs partitions be recognized and a free space for you to install in. 

So the 6.1 partition must have been created by you I am curious as to how it got there.

I just noticed the post above, they are correct you have no way of shrinking the W7 partition it is almost full, it must running a little ruff being that loaded up.

---

### Post by 2hot6ft2 on 2010-03-20
I just noticed that the guided resize which is selected in the first pic it's showing that BT4 would take the place of the linux swap partition and I can tell you right now that wont work for 2 reasons.

1. I have BT4 installed and it is using 6.18 GB of the partition it's on. That's more than the 6.1 GB of the swap partition.
2. The installer will complain that there is no swap partition and the installer WILL fail if you try with the limitations you have there.

---

### Post by schoft on 2010-03-20
> **2hot6ft2 said:**
> The 6 GB partition is just as it says it's the linux swap partition BT4 will use it. Click on Manual in the partitioner to see what partitions are really there. What you're seeing is normal.

I surprised windows isn't screaming at you that there is less than 2% free disk space.

Windows never whines unless i go under 700mb or something. I guess it's because my swap ( or cache, idk ) file is on another disk that i had to disable in the bios else BT4 wouldn't boot ( IDE compatible mode ). 

I figured the partition was the swap file used by BT4 but when i got into W7 the partition was still there. That's why i wondered what it was.

As for the space on my disk, that's not a problem as i was planning to remove certain stuff for this task but haven't done it yet.

> **wilee-nilee said:**
> 
Just make sure when you get to the install that you watch that the ntfs partitions be recognized and a free space for you to install in. 
Just wondering, How ( in bt4 ) would i identify the disk after i split it in w7 ? And wouldn't the bootrecord be all messed up after i split it? Or will windows disk management take care of that?

Will do the things you guys are suggesting

Thanks loads

---

### Post by 2hot6ft2 on 2010-03-20
> **schoft said:**
> Windows never whines unless i go under 700mb or something. I guess it's because my swap file is on another disk that i had to disable trough the bios else BT4 wouldn't boot. 

I figured the partition was the swap file used by BT4 but when i got into W7 the partition was still there. That's why i wondered what it was.

As for the space on my disk, that's not a problem as i was planning to remove certain stuff for this task but haven't done it yet.

Ill do the things you guys are suggesting

Thanks loads
Sounds good. I would suggest at least 10 GB for the BT4 operating system PROVIDED you don't use it to collect things like it looks like you did with W7. If you think you'll collect things on it then give it more, mine is bare bones and uses 6.2 GB basically.

You wont be able to run videos and stuff like that on BT4 since you will always be running as root which is very dangerous in linux but since most apps in BT require that they be run as root you run as root all the time.

Starting with BT as your first linux experience is one major learning curve. Be sure to spend some time learning in their forums here:
[http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)

and the old forum here:
[http://forums.remote-exploit.org/](http://forums.remote-exploit.org/)

---

### Post by wilee-nilee on 2010-03-20
The boot record is in the sda1 100mb partition. resizing the W7 partition with the disc manager will advise you on how small you can make sda2 and none of this should mess with the boot record.

---

### Post by 2hot6ft2 on 2010-03-20
> **schoft said:**
> 
Just wondering, How ( in bt4 ) would i identify the disk after i split it in w7 ? And wouldn't the bootrecord be all messed up after i split it? Or will windows disk management take care of that?

Use the Manual partitioning option in the installer and it will see it and you can specifically choose where it will go.

There are some risks when installing grub with W7 and you should read up on possible problems and solutions before doing the install. You can start by searching the forum for windows 7 and grub.
Also BT4 uses ubuntu 8.10 as it's base OS and legacy grub so you'll have to keep in mind that things you find for grub2 will not apply.

I had no problem when I installed it but then I'm a bit more familiar with things and have been using computers and tweaking them since the 1980's.

---

### Post by schoft on 2010-03-20
> **2hot6ft2 said:**
> using computers and tweaking them since the 1980's.

That's impressive :D Thanks for the help. Haven't done it yet but I guess this is solved.

---

### Post by 2hot6ft2 on 2010-03-20
> **schoft said:**
> That's impressive :D Thanks for the help. Haven't done it yet but I guess this is solved.
Then you should use the Thread Tools at the top of the thread to mark it as solved.
I don't know about impressive but it sure makes me feel old..;)
And you're welcome

---

