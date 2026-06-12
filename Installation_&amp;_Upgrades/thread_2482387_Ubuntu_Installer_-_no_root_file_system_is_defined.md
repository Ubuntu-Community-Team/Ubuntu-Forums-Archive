---
title: "Ubuntu Installer - no root file system is defined"
date: 2022-12-29
forum: Installation &amp; Upgrades
---

### Post by davidmichaellemon on 2022-12-29
I'm trying to install Ubuntu 22 on a hand-me-down laptop that is currently running Windows 11. When I made it to the final part of the installation it errored and said "No root file system is defined". Worst part is when I found a solution for it, it didn't even apply to me because they had partitions appear and I didn't. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291479&d=1672351330[/IMG]
My brother believes that its detecting my flash-drive but not my hard-drive and I have no idea how to fix that. 
If you have any way to help me, please, by all means...

---

### Post by yancek on 2022-12-29
If you used rufus, it will create a live system with an installer which you can use to install Ubuntu.  You need to set and select free space or a Linux partition on which to install Ubuntu.  In your image, you appear to have about 10GB of free space available.  Best to make that larger (20GB) by using windows to shrink the main ntfs partition (sda4) then install Ubuntu.  10GB is pretty small for a full install though it might work.  When you get to that screen, highlight the free space, click the plus sign ( + ) and a new window should open which allows you to select a Mount point.  Click the down arrow and select the symbol /, then Install.

---

