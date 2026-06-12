---
title: "How to share directories across two distros"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by gorellana09 on 2013-07-14
Hello again folks,

I have Linux Mint and Xubuntu installed on my system. I use them both regularly depending on what I am doing and on my mood. Currently sharing files between the two means mounting the other partition and navigating to the folder I want (downloads, pictures, documents, etc.). Is there a way to do this automatically? I know there is a way to share /home directories but I would like to avoid this and simply share the Downloads, Pictures, Music, Desktop, etc. folders so that no matter what distro I am using thse folders will always contain the same files. Any help will be greatly appreciated.

---

### Post by fantab on 2013-07-14
I triple boot with two flavors of Ubuntu and Arch. Here's what I do regarding sharing my files/directories:

I don't use a separate '/home' partition. I install my distros on a 20-30GB '/' partition. When we don't have a separate /home then Home folder is created in '/' partition. 
For my Data I use a simple Linux partition (Data partition) formated with Ext4, without any mountpoint. I manually mount this partition from Nautilus/Thunar by just clicking on it whenever I need to. We can also automount this partition at the system start by adding it to the [/etc/fstab]("https://help.ubuntu.com/community/Fstab"), [More info]("http://ubuntuforums.org/showthread.php?t=283131").
I have created on this partition myPictures, myDownloads and so on. Then I [create symbolic links]("http://www.howtogeek.com/howto/16226/complete-guide-to-symbolic-links-symlinks-on-windows-or-linux/") (In the link refer to 'Symlinks in Ubuntu) of these folders and place them in my 'Home' on '/' partition. Simple, is it not?
I have also changed the default save/path in the applications to save files/folders in the Data Partition in the appropriate folder. Except for UbuntuOne, everything works. 

This way I don't have separate /home for my distros and also formatting and re-installing distros in '/' partitions is carefree.

My two cents.

---

### Post by gorellana09 on 2013-07-14
fantab, you are a hero. I have done exactly as you said even modified /etc/fstab to automount on boot and now I have all my folders in a separate partition called Data. This is exactly what I wanted to do. Thanks so much I appreciate it. I am so excited now I can go and install Xubuntu on my other partition.

---

### Post by gorellana09 on 2013-07-14
I also want to add that following the same procedure as above I did the same for my .Skpe .thunderbird .mozilla and google-chrome folders creating symlinks and now I nicely share my email and web browsing and skype with both distros. I just have to make sure I always run the same version of them because apparently it may have some problems if they are not. But this is great, thanks again fantab.

---

