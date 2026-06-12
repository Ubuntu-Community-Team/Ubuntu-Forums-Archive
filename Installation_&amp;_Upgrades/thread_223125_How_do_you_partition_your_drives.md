---
title: "How do you partition your drives?"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by ZeusABJ on 2006-07-25
Just got me two sweet SATA 300GB Seagate Perpendicular Drives! Now I'm working on planning my Ubuntu install. I've decided to attempt to get a striped (or spanned) array going using one of these methods:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

That should give me a whopping 600 GB's of disk space. Now I'm in the process of determining a convention for partitioning. Since I'm still a little new to Linux I'm just wondering how I should allocate things. I think I’m going to separate things out like this:

[INDENT]**/swap**: I have 2GB of RAM so 4GB here[/INDENT]
[INDENT]**/[root]**: Not 100% sure here... 40-60 GB maybe? (Plenty of growth room for updates, etc)[/INDENT]
[INDENT]**/home**: Again sure how to go here, another 40-60GB? (Got a lot of personal documents)[/INDENT]
[INDENT]**/files**: I plan to allocate all the rest to this "custom" partion (for sharing/backup purposes) [/INDENT]

If anyone see’s any flaws in my structure or wants to suggest something better I’d sure welcome their opinions. I’d also really appreciate it if some of you more seasoned vets would take a moment and share some of your partitioning conventions, maybe along with a quick explanation as to why you partition the way you do. Finally I have few partitioning questions I was hoping someone could answer for me:
[LIST]
[*]Under Windows I typically move my “Program Files” directory to a separate partition. Is there a similar “all purpose” folder that houses Linux program files that I should separate from the root partition?


[*]Someone on another forum once mentioned that I should put my kernel on its own partition. Anyone know how to do this and why it would be beneficial to me?


[*]Will resizing partitions have any adverse affects my data?
[/LIST]
**To clarify, my main concern is this:**
I'm willing to bet there might be another folder normally stored in /[root] that might be better served on its own partition. I'm just not experienced enough to know exactly what that folder might be!

:-k 

If anyone can help I’d be eternally grateful!

---

### Post by wieman01 on 2006-07-25
Man, that's a hell-of-a-harddisk... 

The partitioning really depends on what you are trying to achieve, but here is what I(!) would do:

/home : 5 GB
/[root] : 10 GB
/swap : twice the size of your RAM
/data partition: all remaining space

I would create an independent data partition that you could backup separately and share with other computers in the network. Just a thought... That's the "neatest" solution IMHO.

---

### Post by ZeusABJ on 2006-07-26
> **wieman01 said:**
> Man, that's a hell-of-a-harddisk...

I know!!! I'm REALLY excided about all the free space! I also left out the fact that I also have an additional FOUR of these 300 GB drives that I plan to drop into a server on my network! Plan to make those into a nice RAID 5 Array (good old parity) and use it for backups. Hope to eventually dedicate the server flavor of Ubuntu to that task.

:) 

> **wieman01 said:**
> 
I would create an independent data partition that you could backup separately and share with other computers in the network. Just a thought... That's the "neatest" solution IMHO.

That was pretty much what I was intending to do. I just call mine "files" as opposed to "data". Although... "data" does have a nicer ring to it... So Wieman01, are you telling me you share your *entire* data partition on your network, or just selected folders? Also why so small on [root]? I was under the impression that you package manager used that partition for installing software, so it stands to reason that it will grow over time. I want to make sure I allocate enough space to it. Any comments?

:confused: 

Hey also, thanks a lot for your input!

:wink:

---

### Post by wieman01 on 2006-07-26
> **ZeusABJ said:**
> That was pretty much what I was intending to do. I just call mine "files" as opposed to "data". Although... "data" does have a nicer ring to it... So Wieman01, are you telling me you share your *entire* data partition on your network, or just selected folders? Also why so small on [root]? I was under the impression that you package manager used that partition for installing software, so it stands to reason that it will grow over time. I want to make sure I allocate enough space to it. Any comments?

Ok, files they are. :-) 

Sharing your entire partition really depends on what your requirements are. But you could restrict users to access only single folders or files... That's entirely up to you. I usually share only folders that I want others to have access to.

The root partition should be sizable enough, because as you have highlighted the proportion of used space grows over time. However, I have experienced that 5 GB are enough... You have plenty of space so 10 GB should definitely do it. You cannot install as much software even if you wanted to. :-) But again, you may decide to create a bigger one. If you want to play safe, give it 20 GB. You can resize the partition later on anyway.

On the whole, I would create 4 partitions as mentioned. A separate file/data partition ensure that you have to share neither the home nor the root partition.

---

### Post by ZeusABJ on 2006-07-26
Excellent advice Wieman01, that’s the route I'll go. Just one more question. Just in case (for whatever reason) want to change some of these allocations later how well does partition resizing work? Anyone have any horror stories or advice to share with regards to resizing after the install?

---

### Post by wieman01 on 2006-07-27
> **ZeusABJ said:**
> Excellent advice Wieman01, that’s the route I'll go. Just one more question. Just in case (for whatever reason) want to change some of these allocations later how well does partition resizing work? Anyone have any horror stories or advice to share with regards to resizing after the install?

I have never done that under Linux, although I know you can do it. If you have a dual boot system (which I doubt you have after reading your post) then there is a nice Windows tool called PartitionMagic that does the trick.

But I am sure others have a better advice as far as corresponding Linux tools is concerned. I'd be interested in this as well!

---

