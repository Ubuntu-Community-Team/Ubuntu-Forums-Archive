---
title: "Help a Beginner?"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by scottmw90 on 2012-04-25
Hello everyone,

I have an Intel Atom notebook with Windows 7 Starter pre-installed. I've decided, however, to install Ubuntu instead, and have therefore installed 11.04 (I think...) on a separate partition and can choose between either Ubuntu or Windows 7 on startup. 

I now want to uninstall Windows 7, but the Microsoft site hinted that this would be a stupid thing to do since Windows 7 was there first. 

So, can I do it, and how?? Is it just a case of copying over any files I want to keep onto the Ubuntu partition, then deleting the Windows 7 partition?

Thanks.

Also, another question. I originally tried to download Lubuntu, but ended up with Ubuntu. Is this a problem for an Intel Atom 1GB RAM 1.1 GhZ notebook?

---

### Post by darkod on 2012-04-25
You shouldn't have any problems deleting windows. Forget what MS says about it.

Copy all files that you need, and delete the partition. Or format it again as ntfs or ext4 and you can use it like that too.

Ubuntu should work fine on a netbook. I have it on my Samsung NC10 which comes with Atom N270 and it runs fine. The only difference is that I installed a 2GB memory module immediately after I bought it instead of the 1GB it came with.

---

### Post by Buddhika Udaya Sri on 2012-04-25
Hi scottmw90,

Yes ,I agree with darkod, forget What MS says. But remember to copy all  your documents & files which are in the desktop & my documents to another partition. 

I think you can access all your  windows partitions through Ubuntu. If so then you are free to go with Ubuntu.

---

### Post by codemaniac on 2012-04-25
Here is a community documentation that will spoon feed you .
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

### Post by codemaniac on 2012-04-25
> **darkod said:**
> You shouldn't have any problems deleting windows. Forget what MS says about it.

Copy all files that you need, and delete the partition. Or format it again as ntfs or ext4 and you can use it like that too.

Ubuntu should work fine on a netbook. I have it on my Samsung NC10 which comes with Atom N270 and it runs fine. The only difference is that I installed a 2GB memory module immediately after I bought it instead of the 1GB it came with.

Darkod , I am kind of scared how it would turn out when you delete a partition randomly from a running system .I mean would not it better to format the partition than delete and recreate it ?

In a multiboot scenario if you delete a partition randomly , are not we messing up our partition table sequence?

---

### Post by mastablasta on 2012-04-25
> **codemaniac said:**
> Darkod , I am kind of scared how it would turn out when you delete a partition randomly from a running system .I mean would not it better to format the partition than delete and recreate it ?
 
In a multiboot scenario if you delete a partition randomly , are not we messing up our partition table sequence?
 
not really. i once had D drive dissapered (was deleted) after computer froze during filezilla update. 
now C drive with system was there and i managed to repair it all in the end. but moving, deleting and changing partition (on unfragmented disk) shouldnt+ pose much danger. however there is always that small % chance for which it is better to have data backed up.

---

### Post by darkod on 2012-04-25
> **codemaniac said:**
> Darkod , I am kind of scared how it would turn out when you delete a partition randomly from a running system .I mean would not it better to format the partition than delete and recreate it ?

In a multiboot scenario if you delete a partition randomly , are not we messing up our partition table sequence?

If you boot ubuntu you can delete the windows partition. Or, as I said, another option is just formatting it and using it as data partition.

From windows of course you wouldn't be able to delete it since it is running from it. But from ubuntu you can delete it.

You are not messing up anything in the partition table.

---

### Post by km3952 on 2012-04-25
> **scottmw90 said:**
> Hello everyone,

I have an Intel Atom notebook with Windows 7 Starter pre-installed. I've decided, however, to install Ubuntu instead, and have therefore installed 11.04 (I think...) on a separate partition and can choose between either Ubuntu or Windows 7 on startup. 

I now want to uninstall Windows 7, but the Microsoft site hinted that this would be a stupid thing to do since Windows 7 was there first. 

Microsoft just wants to dominate the desktop market..

> So, can I do it, and how?? Is it just a case of copying over any files I want to keep onto the Ubuntu partition, then deleting the Windows 7 partition?

Personally, if you don't want to re install using the whole disk, I would just copy what I want into my /home & then delete everything on the Windows partition, then just use it as is (ntfs) or put a linux filesystem on it.

> Thanks.

Also, another question. I originally tried to download Lubuntu, but ended up with Ubuntu. Is this a problem for an Intel Atom 1GB RAM 1.1 GhZ notebook?

If the Ubuntu version suits you keep it, if not try Lubuntu, both are about to be 12.04 versions.

Personally, I like a simple fast desktop, & use Lubuntu.  :)

---

### Post by scottmw90 on 2012-04-25
Thanks for the replies!

In the meantime it has been strongly recommended that I uninstall Ubuntu and install Linux Mint instead, since it's apparently a much easier Ubuntu-based version of Ubuntu.

This means I'll need to uninstall Ubuntu, which I assume is done simply through Windows, and then install Linux Mint. I've also been strongly urged to leave Windows on the netbook, and instead of uninstalling it to simply greatly limit its partition. 

If I keep it on the netbook, I assume this means that while running any other OS the netbook won't also be trying to maintain Windows through any background processes which would detract from the new OS's performance?

---

### Post by TBABill on 2012-04-25
If you created a separate partition for Ubuntu, then when you restart only one operating system is active. You'll never have background process running from the other OS in that scenario.
 
Have you made a backup of your Win7 install? I mean where you actually create disks in case you ever want to reuse it? You paid for that license, no sense deleting all the info without the ability to restore in the event you actually need it later. Whether you keep Win7 and dual boot with Linux is entirely a personal choice, but I'd recommend a backup since it's a netbook and you don't normally get disks with them (especially since they have no CD/DVD drive).
 
Lastly, when you install a Linux OS of any distro, it will prompt you for which partition you want to use. Just point Mint or Ubuntu at your existing Ubuntu install and it will reformat and write over that same partition. There's no need to pursue an "uninstall" in the Windows sense of the word.

---

### Post by Mark Phelps on 2012-04-25
> **scottmw90 said:**
> In the meantime it has been strongly recommended that I uninstall Ubuntu and install Linux Mint instead, since it's apparently a much easier Ubuntu-based version of Ubuntu.
Mint has its own features that make it different than Ubuntu, although they both use the Linux OS kernel.  If you need detailed info or advice about Mint, you would do best checking their forums.

> This means I'll need to uninstall Ubuntu, which I assume is done simply through Windows, and then install Linux Mint. 
Unless you installed Ubuntu using MS Windows in the first place, you can not remove it using MS Windows.  And if you DID installing using MS Windows, then removing MS Windows removes Ubuntu as well.

> I've also been strongly urged to leave Windows on the netbook, and instead of uninstalling it to simply greatly limit its partition. 
The main drawback of ALL Linux distros tends to be lack of drivers, especially for brand new equipment -- which is the main reason for trying out new distros using the LiveCD or LiveUSB method.  That allows you to see how well the distro detects your hardware and installs the proper driver before you install it.

Also, despite what you may hear, only SOME Windows apps will run in Linux using Wine.  So, if you depend critically on a Windows app that does not run in Wine, you need to keep MS Windows around for running that app.

> If I keep it on the netbook, I assume this means that while running any other OS the netbook won't also be trying to maintain Windows through any background processes which would detract from the new OS's performance?
In a multi-boot situation, only one OS is running at a time.  When you're running the Linux OS, MS Windows will not be running.

Which also means, that you should not HIBERNATE your PC and then run Linux distros.  You should restart, instead.

---

### Post by techsupport on 2012-04-25
Piece of cake. Just install Gparted Parition Manager and delete the windows paritions, and expand the Linux parition to use that extra space created by getting rid of windows.  Gparted is down the list here:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by codemaniac on 2012-04-26
> **darkod said:**
> If you boot ubuntu you can delete the windows partition. Or, as I said, another option is just formatting it and using it as data partition.

From windows of course you wouldn't be able to delete it since it is running from it. But from ubuntu you can delete it.

You are not messing up anything in the partition table.

Yes i understand that we cannot delete an partition that is mounted and running .That is why playing with partitions is suggested via a live cd environment .

Lets say one has 4 logical partitions /dev/sdx5-8 , all root partitions having different linux flavors installed .
and abruptly we delete sdx6 which is root partition of "Linux 6" , in this scenario i believe the partition table would be messed up .
Historically logical partitions must be contiguous. Each logical partition contains a pointer to the next logical partition .
So deletion of an intermediate logical partition which contains pointer to next logical one , confuses the partitioning table .

---

### Post by mastablasta on 2012-04-26
> **scottmw90 said:**
>  
In the meantime it has been strongly recommended that I uninstall Ubuntu and install Linux Mint instead, since it's apparently a much easier Ubuntu-based version of Ubuntu.
 

Linux mint is only a little bit different than Ubuntu (well appart from the GUI). It is a good alternative but like it was said it has it's won features.
 
The one that bothers me most is that you need to do a clean install to upgrade. in ubuntu upgrade to new version is only a click away and should work fine unless you heavilly customized the OS or added plenty PPA.

---

### Post by pratikk on 2012-04-26
Scott, I use a netbook with similar specs but slightly faster CPU, dual booting XP and Ubuntu 10.10. Works just fine. I've kept the XP install because I occasionally use old Win software which does not run reliably on Wine. Besides, I use the XP partition for storage of archived stuff that I don't use every day. 

If you do remove Win:
1. if you need to use Win software at all for legacy reasons, check if it runs OK on Wine at winehq.org. They have extensive test reports.
2. Make a backup CD copy of your OS, as someone has already suggested. 
3. Don't remove the Win recovery partition. The OS is yours to keep, even if you don't use it.

In addition, some netbooks like Eeepc have a tiny partition (4-5 Mb) that GParted reports as 'unknown format'. Since it mystifies me, I've left it alone. 

Pratik

---

