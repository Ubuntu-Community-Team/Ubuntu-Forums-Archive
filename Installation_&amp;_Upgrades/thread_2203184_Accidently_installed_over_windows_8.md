---
title: "Accidently installed over windows 8"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by phillip5 on 2014-02-02
Hi Guys,

I'm having a bit of a crisis here. I'm a bit of a newbie with installing linux and as I was trying to install ubuntu as a dual boot on my Samsung Ativ Book 8 it seems I have overriden Windows and I have no idea how to get it back.

Basically what happened was during the installation I had a seperate partition set out for ubuntu and it was all installing and I got up to the part about entering the Ubuntu One details but after clicking next the whole thing froze up and wouldn't respond for a while so I just shutdown the computer and tried it again. This time there was an option for deleting ubuntu and reinstalling it. I thought it would be best to click on this to get rid of the failed installation and start afresh. It never gave me the option to choose a partition for ubuntu so I assumed (or rather hoped) it rememberd what I had put last time I tried to install. It all loaded up fine and ubuntu worked so I tried to boot back into Windows and found to my horror that instead of an option for windows and ubuntu I now had two options for ubuntu. I confirmed that ubuntu is now taking up all the disk space and Windows is officially gone :(

I have no idea what to do now and I am at wits end. How can I get Windows 8 back? I don't need to get any data back and a fresh install of windows would be fine but so far this seems impossible. In Ubuntu I've managed to get the product key from the BIOS but it seems that to get the Windows 8 iso from microsoft I need a retail key! 

I don't think Samsung are going to be of any help to me here and I really don't feel like dishing out more cash to get another copy of Windows 8. Any help here would be massively appreciated :)

p.s. please have less ambiguous instructions during the installation. I seriously had no idea that option I chose was going to remove Windows..

---

### Post by tfrue on 2014-02-02
If you made a recovery disk, then maybe. I would like to see your boot-info script just to see what we are dealing with, so if you would go to this site and follow these instructions:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I'm pretty sure that you will not be able to reinstall Win 8 though, sorry friend.

---

### Post by phillip5 on 2014-02-02
[http://paste.ubuntu.com/6860805/](http://paste.ubuntu.com/6860805/)

There is no recovery disk. 

I really really hope there is something that can be done. I've lost all my samsung apps on it too :(

---

### Post by oldfred on 2014-02-02
Please add to this bug. It now says triaged, but I think that just means they are ignoring it.
 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

About all you can do is see if Samsung will let you download your image or purchase for a nominal charge you image to restore your system. Otherwise you have to purchase a new copy of Windows.

While you cannot restore a working system, if you had vital files you did not back up, you may be able to recover some. Linux is a lot smaller than Windows and not everything was overwritten.
First try testdisk and deeper search. This only works if the part of the drive with filenames was not overwritten.
Part of testdisk is photorec. But it takes a very long time as it just scans drive for anything that looks like a file. And you need lots of room on anther drive to copy data to. And it does not restore full filename, just extensions. You can get music & photo names as they have internal data. But other files you have to manually review and see what name it should be. (I have done it and it takes forever or now I do much better backups). 

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

I have never used these, but other have posted they work.

 For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)
Also this one:
Then, I settled on Recuva, which isn't as pretty as the others, but it does the job well and is completely free. 

Part of testdisk in Ubuntu's repository.
      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by Mark Phelps on 2014-02-02
The problem you're going to face trying to get your Samsung apps back is that Windows stores different files and app data in lots of different places, including the registry.  So, it's not a simple matter of recovering a few files.

What you could try is restoring the original partition layout.  The Minitool Partition Wizard Boot CD will sometimes do this.  You have to download the ISO file, burn it to CD, and boot from that.  See if it offers you the option to restore the original partition scheme.

---

### Post by phillip5 on 2014-02-02
Luckily I have no data that I need to recover. That's why I didn't bother with making a recovery disk. I had no idea it would be so difficult just to get a fresh Windows install. By Samsung apps I just meant the apps that come preinstalled by Samsung that would usually need to be purchased (SideSync etc.) 

I am trying my luck with Samsung now to see if I can get the recovery file from them. Even if they charge me it should still be cheaper than buying a brand new copy of Windows 8. Fingers crossed but I can't see why they would refuse? I already have the product key on my machine.

---

### Post by tomasz-ks9 on 2014-02-03
I had similar problem. All you have to do is google for a windows 8 OEM iso (it's very important that its OEM, otherwise it shows that your key is not for the retail version) for an appropiate processor architecture (most probably x64). Then just burn it on a dvd or on your pendrive (there are tutorials how to do it). Then just install windows and it should not even ask you for the product key - it gets it automatically from BIOS. It was a nice discover and I saved ~200z&#322; (~47&#8364;) - the cost of the recovery partition restore.

---

### Post by tfrue on 2014-02-03
Be careful doing that though. Make sure you are downloading the correct image since there are a lot of pirated versions among the internet, and we don't want you doing anything illegal.

---

### Post by Bucky Ball on 2014-02-03
No, we don't, and before this conversation goes any further or any links are posted to torrenting sites, may I take the opportunity to remind one and all, from the forum Code of Conduct:

> Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. 

;)

---

### Post by phillip5 on 2014-02-03
Any idea where I can legally optain the OEM version then?

Samsung sidestepped the question in my email by saying they can't supply the recovery disks "[COLOR=#494949][FONT=Arial]as the recovery software for the unit is preinstalled"..[/FONT][/COLOR]

To fix it they suggest I go to an authorised repair centre but it just seems silly to do that when I could probably easily fix it myself just with the proper .iso

---

### Post by oldfred on 2014-02-03
I just do not know how vendors can do that. Hard drives fail and users do not back up systems. 
But some may want to look at system and then will tell you that you violated warranty or something. But in some countries that is not legal. 
If you have to go to a service center, dd erase the entire drive so it has nothing on it. And say you do not know what happened, maybe it was Samsung or Windows virus but you do not know?

---

### Post by tfrue on 2014-02-04
Haha! What momma doesn't know won't hurt!

---

### Post by phillip5 on 2014-02-06
> **oldfred said:**
> I just do not know how vendors can do that. Hard drives fail and users do not back up systems. 
But some may want to look at system and then will tell you that you violated warranty or something. But in some countries that is not legal. 
If you have to go to a service center, dd erase the entire drive so it has nothing on it. And say you do not know what happened, maybe it was Samsung or Windows virus but you do not know?

Well it seems like I just might do this as their response so far has been the following..

> With regard to your query regarding the installation CD that you are requesting, please be advised that the installation CD for the operating system of your unit is a preinstalled software which we are unable to provide since this is a trial version only.
It was mentioned that you paid for the Windows operating system and you have the product key on your machine. In this regard, please contact Microsoft to assist you further.

I have no idea what they mean by its a trial version?? and naturally I can't download the Windows 8 iso from Microsoft as that requires a Retail Key, not the OEM key.

---

### Post by oldfred on 2014-02-06
I do not think Windows has a trial version and Microsoft always directs users back to computer vendors.

---

