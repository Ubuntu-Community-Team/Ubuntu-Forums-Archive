---
title: "upgraded but now can't  boot windows vista from grub"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by newbie1969 on 2010-05-21
Hi There,

I also upgraded to 10.4 from 9.10 and now can't use guub to load windows vista

What have I done wrong? in simple terms please

I have no idea how to post a script as my brother was the one that installed 9.10 in the first place and partitioned the hard drive for me.

I did have windows vista in /dev/sad2

Thanks

---

### Post by newbie1969 on 2010-05-21
What application do I use to launch the boot info script

Thanks

---

### Post by darkod on 2010-05-21
If you are sure vista is on /dev/sda2 just use the instructions here to repair partition #2 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The instructions should be clear enough. We can't explain it in more details.

---

### Post by newbie1969 on 2010-05-21
Sorry but I do not understand at all. I see i am using Grub 1.98

Have tried to use the terminal but have no idea how to find path to  launch application

I am not a very good with these things

Thanks for your help

---

### Post by wilee-nilee on 2010-05-21
So if the testdisc option is confusing, then the bootscript is accessed from a live ubuntu cd. Save the http address on a piece of paper, then boot the live cd download the script, it will probably go to downloads or your home directory. Drag it on to the live cd's desktop the run this command, from the terminal.
```
bash ~/Desktop/boot_info_script*.sh
``` 

This will put the readout of running the script onto the live cd desktop. Then come back to your thread using the live cd and paste the read out into a reply; highlight the text and click on the # in the reply panel window.

You can also down load the script onto your running Ubuntu setup and then just open the partition with the live cd and drag it onto the desktop of the live cd then unmount the Ubuntu partition then run the code and post as suggested. You don't want to run the script from your live running Ubuntu, it wont hurt anything, but the general use of it is from a live cd.

And darkod is very good with this stuff so his instructions will be relevant.

Here is the boot script link again so you can just access it from the live cd from your thread for running the instructions.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by newbie1969 on 2010-05-21
I did the upgrade from updates so have no cd to run live

I am so confused. I tried the testdisk and saw P Windows RE (Store). I am not seeing the word boot unless I am in the wrong part

Cheers

---

### Post by newbie1969 on 2010-05-21
I do not see backupbs just rebuildbs

I think I have stuffed up somewhere

My brother has the 9.10 live disk so I am not able to use it

---

### Post by wilee-nilee on 2010-05-21
I can't really help with the testdisk options, I am just not familiar with it, but the instructions on the page are there.

You need to have a Live CD or thumb loaded anyway for situations like this so I would get the live CD of your release.

You can run from the terminal 
sudo fdisk -l and post the results.  So l=small case L but you can just copy and paste the command into the terminal.

You are going to want to get familiar with doing some of these other tasks for easy travel in the future though. ;)

---

### Post by newbie1969 on 2010-05-21
I am downloading unbutu 10.04 to a cd at moment so am not able to do much more for now.

Might have to wait till I am back from work tonight

Cheers and thanks for all your wonderful help so far

---

### Post by wilee-nilee on 2010-05-21
> **newbie1969 said:**
> I am downloading unbutu 10.04 to a cd at moment so am not able to do much more for now.

Might have to wait till I am back from work tonight

Cheers and thanks for all your wonderful help so far

Smart idea. ;)

---

### Post by newbie1969 on 2010-05-21
> **wilee-nilee said:**
> I can't really help with the testdisk options, I am just not familiar with it, but the instructions on the page are there.

You need to have a Live CD or thumb loaded anyway for situations like this so I would get the live CD of your release.

You can run from the terminal 
sudo fdisk -l and post the results.  So l=small case L but you can just copy and paste the command into the terminal.

You are going to want to get familiar with doing some of these other tasks for easy travel in the future though. ;)

Thanks for all your help. Looks like I have a lot to learn

Cheers

---

### Post by bcbc on 2010-05-21
You can still boot ubuntu right? So you don't really need the live CD. Just boot ubuntu and follow the instructions on [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) to run the script and post back

---

### Post by wilee-nilee on 2010-05-21
> **bcbc said:**
> You can still boot ubuntu right? So you don't really need the live CD. Just boot ubuntu and follow the instructions on [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) to run the script and post back

That is fine but the OP will need the live disc to fix the MBR if it is a grub problem basically.

---

### Post by darkod on 2010-05-22
> **wilee-nilee said:**
> That is fine but the OP will need the live disc to fix the MBR if it is a grub problem basically.

Not really. The OP needs to remove grub2 from the vista partition (probably, we don't have all the info) and this can also be done with testdisk from within the hdd ubuntu install.

However, if the testdisk procedure link already posted confuses him so much, I don't know whether he should be pushed to do it. He can really mess things up with testdisk. That's why I backed off.

---

### Post by newbie1969 on 2010-05-23
Just to let you guys know I am a lady.

Yes I can still use ubuntu at the moment.

I had a bit of trouble downloading Ubuntu to a cd so have ordered the latest version and will have to wait 4 to 6 weeks for it.

Will see if my brother can help when he gets time.

Cheers

---

