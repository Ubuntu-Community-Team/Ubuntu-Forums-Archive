---
title: "Is it possible to install Ubuntu over top of Xubuntu on a Windows 7 dual boot?"
date: 2019-03-02
forum: Installation &amp; Upgrades
---

### Post by jjc55 on 2019-03-02
Here is the deal... I installed xubuntu on a Windows 7 machine and set it up for dual boot. The problem is;  I'm not crazy about the xfce desktop environment or just the distro in general, and I have plenty of machine requirements and resources for the full version of Ubuntu. Since I've been having Internet issues as a result of a battle with xfinity, I currently am without internet so I can't just do an upgrade from the desktop or anything like that. So, I in turn went to my mother's and downloaded Ubuntu and set up a working USB drive with an ISO burned on it. Now,  what I'm wondering is; can I take this ISO and install it over top of xubuntu with the partition that I currently have set up without reallocating more hard drive space?  I haven't yet tried it, but I have a sneaky suspicion that when I start the install, the allocated space on which xubuntu is currently installed on is obviously not going to show up as free space and refuse to allow me to easily take its place with the new OS. I know that I may have to go into Windows and reformat that partition. If there are any other easier/smarter ways to accomplish this task I'd definitely be willing to give it a shot. Any suggestions out there?  I appreciate the help. Thanks

---

### Post by Dennis N on 2019-03-02
Choose the "something else" option at the installation type screen. That gets you the manual partitioning setup. Select the existing Xubuntu partition, then use the 'change' button to tell the installer to use it as the / partition for the new install, and format as ext4. Then you can begin install.

---

### Post by yancek on 2019-03-02
> but I have a sneaky suspicion that when I start the install, the allocated space on which xubuntu is currently installed on is obviously not going to show up as free space

Doesn't need to have unallocated space in your situation.  Take steps recommended above selecting the current Xubuntu partition to use, make sure you select the check box to format that  (root filesystem) partition.

> I know that I may have to go into Windows and reformat that partition.

That wouldn't help as you would need to format with a Linux filesystem and a default windows OS is not capable of doing that.   The Something Else options suggested above should work.

---

### Post by jjc55 on 2019-03-02
Thanks guys. It was actually much easier than I anticipated. Before I even looked at this post I gave it a shot,  and the install process gave me the option to install over xubuntu right away without having to do any tinkering. I should have just tried this in the first place before posting a new thread and wasting peoples time. I apologize for that. I'll mark it solved.

---

### Post by yancek on 2019-03-02
> I should have just tried this in the first place before posting a new thread and wasting peoples time.

No, better off asking any time you are not sure as it will generally save a lot of trouble down the road.  The next question/problem may not work out as well so best to get advice before jumping in.  Glad you got it working.

---

