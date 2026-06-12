---
title: "Gparted resize freezes"
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by pxie on 2016-02-29
Hello. I have dual-boot ubuntu / windows , today i formated partition where ubuntu was installed so that partision is now unallocated 35 gb and i wanted resize the main parittion where windows is installled by 35 gb formated partition but when i resize the main parittion and click apply settings there's a small window Applying pending operations but it always freezes after like 5 seconds at "check file system on /dev/sda5 for errors and ( if possible ) fix them", so i have to brute-force close it otherwise it will never stop. I did not have such a poblem before when i wanted to do the same thing i always used disk managment in windows and did it there but this time partition managment in windows shows that there's not any unallocated partition basically it shows 195gb but gparted shows 160gb + 35 gb unallocated and it freezes while resizing. I had installed ubuntu but during update it restarted and had some problem while booting so i decided to reinstal and this is happening. Really dont know what to do , will be thankful for every single help.

---

### Post by yancek on 2016-02-29
You forgot to post which windows version you are using.  Since they've been selling operating system for over 30 years, it does make a difference.
Do you have windows hibernated?  Why are you using GParted?  If you are re-sizing a windows partition you would be better off using Disk Management although GParted can be used.

You might post an image of what you are referring to from GParted or Disk Management.

---

### Post by QLee on 2016-03-01
Pxie,
It appears that you have a misconception. You formatted a partition but that does not make it "unallocated" space, that makes it "formatted" unused space, if you delete the partition it becomes "unallocated".

You should always avoid "brute-force close" of the system if you can.

As yancek advised, it is always a good idea to tell as much as you can about which version of Windows, which version of Ubuntu, since there might be differences that matter in what way to correct a problem and it's also good to state what computer you are using and what specifications it has. This time what computer you are using probably doesn't matter but yancek asks for some information that might give hints of what is happening.

[Edit] Pxie if all you want to do is reinstall Ubuntu, you could do that on that partition without any resizing of your Windows partition (you don't have to put the partition's space back into the Windows partition first).

---

