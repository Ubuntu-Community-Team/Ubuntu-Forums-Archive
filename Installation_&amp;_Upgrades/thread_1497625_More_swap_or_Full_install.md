---
title: "More swap or Full install?"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by blagosphere on 2010-05-30
Back about a year ago i installed jaunty through wubi. it failed to upgrade to karmic so i did a fresh wubi install. I am running a laptop and the hibernation feature would be greatly appreciated. to do this i need a larger swap partition. Because it is installed through wubi i do not know how to make it larger or if its even possible. If it is not I would like instrucitons on how to save my settings on this ubuntu and then install a full lucid without touching my windows xp tablet edition. if it is too much troubble then i guess i wont do it... are there any particular advantages to a full install?

---

### Post by bcbc on 2010-06-02
> **blagosphere said:**
> Back about a year ago i installed jaunty through wubi. it failed to upgrade to karmic so i did a fresh wubi install. I am running a laptop and the hibernation feature would be greatly appreciated. to do this i need a larger swap partition. Because it is installed through wubi i do not know how to make it larger or if its even possible. If it is not I would like instrucitons on how to save my settings on this ubuntu and then install a full lucid without touching my windows xp tablet edition. if it is too much troubble then i guess i wont do it... are there any particular advantages to a full install?

You can't hibernate on wubi. Also, hibernation is a lot slower and flakier with ubuntu. 

It is possible to convert your wubi to a regular partition (I've done it), but all of the shell scripts that I've found to do this refer to an older version of grub than the one you're using so you need to figure out all that. Or you could do it manually as well... again a bit of work to figure out.

Finally, lucid has a few issues - one of which is a much reduced battery time (on intel processors). I'd do some research on that before making the leap. The upgrade also has a few potential risks.
See here: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by goinglinux on 2010-06-02
> **blagosphere said:**
> Because it is installed through wubi i do not know how to make it larger or if its even possible. If it is not I would like instrucitons on how to save my settings on this ubuntu and then install a full lucid without touching my windows xp tablet edition.

**Wubi**
A Wubi install is not intended for long-term use. That is why features such as upgrades and suspend are not supported. My suggestion would be to do a full install of Ubuntu Lucid from a LiveCD. It will not interfere with your Windows installation. In fact, your boot experience will be very similar with the exception that instead of seeing the Windows boot loader screen with a choice to boot into Windows or Linux, you will see a GRUB boot loader screen with the same choices. 

**New Installation**
You will want to boot your computer from the LiveCD. Once you have Lucid booted, you will see an icon that lets you install the OS. Answer a few questions and when you get to the point where it asks you about where to put it on the disk (partitioning) select the option that installs Linux along side of your Windows XP, using the empty space on your hard drive. This should be the default option. Of course, you might want to uninstall Wubi first, so that you have more free space to use for the fresh install. 

**Backup and Restore Apps and Settings**
Before you uninstall Lucid, here are a few links that will help you in retaining your data, your settings, and your installed applications. 

Use dpkg to migrate installed apps to new installation.
Forum posts:
&#65279;[http://ubuntuforums.org/showthread.php?t=169062]("http://ubuntuforums.org/showthread.php?t=169062")
[http://ubuntuforums.org/showthread.php?t=908979]("http://ubuntuforums.org/showthread.php?t=908979")

If you backup your entire home folder, then copy everything (including the hidden files and folders) from the backup into the home folder on your new installation, all of the settings and preferences for all of your installed applications will also be retained.

Here are some links with information about backups.
Podcast episodes and links:
[http://goinglinux.com/2008shownotes.html#glp029]("http://goinglinux.com/2008shownotes.html#glp029")
[http://goinglinux.com/2008shownotes.html#glp031]("http://goinglinux.com/2008shownotes.html#glp031")

---

### Post by blagosphere on 2010-06-02
Wubi has brought me much joy and i have updated into lucid just fine. Since i have all summer i believe i will start the full install process. Some of my friends who have used wubi then uninstalled it still have the windows "select os" screen even while there is no longer that os.... how do i uninstall wubi ubuntu completely? I have made a live cd before and checked the hash so i am not worried about that, but how much time should i have to devote to the install process once i have the cd made?

---

### Post by bcbc on 2010-06-02
> **blagosphere said:**
> Wubi has brought me much joy and i have updated into lucid just fine. Since i have all summer i believe i will start the full install process. Some of my friends who have used wubi then uninstalled it still have the windows "select os" screen even while there is no longer that os.... how do i uninstall wubi ubuntu completely? I have made a live cd before and checked the hash so i am not worried about that, but how much time should i have to devote to the install process once i have the cd made?

Yes, wubi gets a bad rap on these forums. It does have limitations, but all in all it does what it's designed to do.

Here is a [link]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") that tells you how to manually remove the 'menu option' if it's still there after uninstalling.

Installing Ubuntu is fairly quick , but you should check out how to migrate you /home directory from wubi. That will take a bit of time to figure everything out and make sure it's all working. 

At the least keep a backup of your wubi install (c:\ubuntu\disks\root.disk) and you can access it later if you missed something. But better is, if you have the space, keep wubi running until you've migrated and tested it fully.

---

### Post by tommcd on 2010-06-02
> **blagosphere said:**
> Wubi has brought me much joy and i have updated into lucid just fine. Since i have all summer i believe i will start the full install process.
Wubi is ok for trying Ubuntu, but as others have said, if you plan to stick with Ubuntu, you should do a  real install to a dedicated partition on your hard drive. 
Wubi's developer Agostino Russo even said that:
> Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
See this interview with the Wubi developer Agostino Russo for more info:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Ubuntu will perform much better with a real install to a partition with an ext4 file system anyway.
Here are 2 great sites to get you get started:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

### Post by blagosphere on 2010-06-02
One more Question.... Wubi uses 64bit and i have no problems... should i make my live cd for 64 or 32 bit?

---

### Post by goinglinux on 2010-06-02
blagosphere:

I have used both the 32-bit and the 64-bit version. Either is fine. If you find that there are some 64-bit features you want to use, like the ability to edit and render lots of large videos or other processor-intensive tasks, or use more than 4GB of RAM, then by all means use the 64-bit version. 

On the other hand, I am running 32-bit Ubuntu 10.04 on my 64-bit computer because, I don't do a lot of video editing, I don't have only 3GB of RAM and I have found that more things require fiddling to get them working on 64-bit. (Like Adobe Flash.) On the other hand, that is just my experience in the way that *I* use my computer. 

I think the bottom line is, if you have had no issues with 64-bit Ubuntu under Wubi, then I see no reason *not* to install the 64-bit version. I hope everything goes extremely well for you.

Oh, by the way, to address the "how much time" question, it depends a lot on the speed of your computer, but it sounds rather modern. Assuming you will use the LiveCD, it won't take long to complete the installation. From insertion of the CD, through booting, clicking the icon to install, and getting to the dialog box that asks whether you want to continue testing or reboot, you will spend maybe an hour (plus or minus). 

Once you reboot, you will have a fully-functional system, ready to fill your "home" folder with the stuff you need from your backed-up information. (Remember the hidden folders.) You can then install any applications you had installed on your Wubi installation, then you are ready to go. How much time this last bit will take might be estimated as the same amount of time it took to make the backups.

---

### Post by blagosphere on 2010-06-04
the hardest part was finding a good defrager to defrag the mess of a partition that windows occupies. after that i used gparted to shrink my windows partition and now have my full install. I went with the 64bit. Before i got rid of my wubi install i saved the home folder, including the hidden items to a networked hdd. i included the hidden files (well all but one that was linking to something that was far too large to be any part of my ubuntu install.) the only problem is that on a windows machine i see all those files, but in ubuntu i dont... even with "show hidden files" selected.

secondly in windows it is possible to run 32bit apps in a 64bit system.. just not the other way around.. can i force ubuntu to use the 32bit architecture in my system?

---

### Post by bcbc on 2010-06-05
> **blagosphere said:**
> Before i got rid of my wubi install i saved the home folder, including the hidden items to a networked hdd. i included the hidden files (well all but one that was linking to something that was far too large to be any part of my ubuntu install.) the only problem is that on a windows machine i see all those files, but in ubuntu i dont... even with "show hidden files" selected.

Did you back up the c:\ubuntu\disks\root.disk file before uninstalling wubi? If so, you can loop mount it and retrieve your /home directory.

---

### Post by vince2678 on 2010-06-17
wubi-move-to-partition seems to work fine though I have never tried LPVM . LPVM is just too outdated.:mad:

---

