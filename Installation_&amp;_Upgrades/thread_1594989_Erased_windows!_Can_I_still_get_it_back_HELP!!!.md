---
title: "Erased windows! Can I still get it back? HELP!!!"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by ildo on 2010-10-12
I know I made a mistake!
I have installed Ubuntu 10.04, 10.10CR on different machines for many times.
This time I tried to install 10.10 on my friend's Toshiba laptop.
I didn't backup anything, thought I will do it easily again.
When I was asked where to install the ubuntu, I choose the only partition (NTFS for windows) and then I clicked "Change"
I thought that will create a new partition so I can install Ubuntu. (just like I did before)
But once partition is done, the NTFS partition is gone!. and there are one new ext2 partition for ubuntu and a new free space.

Is there anyone can help me to tell me how to recover the windows partition?
My friends has many important files need to get. I need to at least save those files for him.
Any one can help? Please.
I will DIE if I cant...

Please

Thanks a lot.

Jun

---

### Post by otherethe on 2010-10-12
> **ildo said:**
> I know I made a mistake!
I have installed Ubuntu 10.04, 10.10CR on different machines for many times.
This time I tried to install 10.10 on my friend's Toshiba laptop.
I didn't backup anything, thought I will do it easily again.
When I was asked where to install the ubuntu, I choose the only partition (NTFS for windows) and then I clicked "Change"
I thought that will create a new partition so I can install Ubuntu. (just like I did before)
But once partition is done, the NTFS partition is gone!. and there are one new ext2 partition for ubuntu and a new free space.

Is there anyone can help me to tell me how to recover the windows partition?
My friends has many important files need to get. I need to at least save those files for him.
Any one can help? Please.
I will DIE if I cant...

Please

Thanks a lot.

Jun

If you installed after doing this then no you can not get the files back there gone, but if your still at this screen just click the back button and it'll fix your problem but if you went on with the install and Ubuntu installed then sorry to be the one to tell ya but thoes files are gone for ever

---

### Post by kansasnoob on 2010-10-12
You might be able to use testdisk and photorec to recover some of the files:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I've used it but I always just have to read the documentation and muddle my way through.

---

### Post by VMC on 2010-10-12
> **ildo said:**
> ...
But once partition is done, the NTFS partition is gone!. and there are one new ext2 partition for ubuntu and a new free space.

...
Are you sure its gone? I'll assume you did an "fdisk -l" to make sure it is in fact over written.

---

### Post by Rasa1111 on 2010-10-12
Looks like you will never be touching their computer again!

 If Ubuntu is already installed, and the NTFS partition already gone,
you are , (more so your friend) is S.O.L.

 Dang, Glad Im not in your shoes.

---

### Post by VMC on 2010-10-12
> **ildo said:**
> ...
Is there anyone can help me to tell me how to recover the windows partition?
My friends has many important files need to get. I need to at least save those files for him.
Any one can help? Please.
I will DIE if I cant...


Ask your "Friend" if his PC came with recovery disks. Usually, now days, they do. 

If not, most manufactures have recovery disks you can either download or purchase as a reasonable price.

---

### Post by Rasa1111 on 2010-10-12
> **VMC said:**
> Ask your "Friend" if his PC came with recovery disks. Usually, now days, they do. 

If not, most manufactures have recovery disks you can either download or purchase as a reasonable price.

How would a recovery disc help recover lost files if the entire OS is gone?

---

### Post by PRC09 on 2010-10-12
If you have access to a windows machine I have had pretty good success with this software.If you havent done this kind of recovery before you may have to do quite a bit of research to figure out how to...If you are going to attempt this, shut down the  problem machine immediately and remove the drive place it in a windows machine as a slave drive(non-boot) and run the disk recovery software there.There is a full working version for trial on the site so if you cant recover anything it doesnt cost you anything...except an awfull lot of time......Good Luck.....


[http://www.diskinternals.com/partition-recovery/](http://www.diskinternals.com/partition-recovery/)

---

### Post by VMC on 2010-10-13
> **Rasa1111 said:**
> How would a recovery disc help recover lost files if the entire OS is gone?

Edit: I thought he was concerned about Windows. Now I see its the lost files. 
In that case, *testdisk* has saved me in the past.

---

### Post by ildo on 2010-10-13
Thank you guys.
I am trying testdisk now. it is scanning the disk and only 52% now.
I also tried use EASEUS partition recovery and data recovery software.
They both scanned lost partitions and files. but i am too afraid to actual perform the recovery.
I dont want to lose those files forever.
I will see what testdisk will give me.

anyone heard and used EASEUS software before?

Thanks again.

---

### Post by nerdy_kid on 2010-10-13
testdisk wont really help him if he wrote a whole os over the ntfs partition.  It is useful only is the data is actually *there*, currently a large amount of it got overwritten.  You (the OP) might be able to pull files from it, but I strongly doubt you will be able to recover the whole partition.  Also the files you pull will all have their names butchered.  I wish you good luck, but I am really glad I am not in your shoes as well...

---

### Post by Mark Phelps on 2010-10-13
IF you really want to recover the former NTFS partition and/or files, the best MS Windows products I've used for this come from Runtime Software.

Go to their website and check out GetDataBack for NTFS and  Recovery My Files.  You should be able to get a trial version of each.

But you'll have to remove your friend's drive, connect it to an MS Windows machine, install the Runtime Software app, and run it -- to see what it finds.  And have patience!  For a large drive, it can take all night to do a low-level scan, looking for directories and files.

You will have to PURCHASE the product to do the actual recovery, but at least this way, you will find out what the app actually finds -- before you buy it.

And, in future, don't mess around with other folks' machines -- since you obviously do NOT know what you're doing.

---

### Post by Rasa1111 on 2010-10-13
good advice mark. <3

---

### Post by Mark Phelps on 2010-10-14
> **moneer said:**
> ...you should meet the [online data recovery]("http://i-data-recovery.com") friend.. I think they are the cheapest in the world... paid only $15 :-)

Has anybody actually USED this service??

Asking because their web page is FULL of typos and bad grammar -- typical indications of scam artists at work.

I'm not saying this is a fraud ... I'm just saying it looks "suspicious"!

---

### Post by nerdy_kid on 2010-10-14
> **Mark Phelps said:**
> Has anybody actually USED this service??

Asking because their web page is FULL of typos and bad grammar -- typical indications of scam artists at work.

I'm not saying this is a fraud ... I'm just saying it looks "suspicious"!

i suppose that one could find out for a spare $15 (I'm not volunteering :P) -- but if data gets overwritten isn't it impossible to get it back no matter what software used?

---

### Post by Mark Phelps on 2010-10-15
> **nerdy_kid said:**
> i suppose that one could find out for a spare $15

I'm NOT concerned about a paltry $15 -- what I AM concerned about, if this is a fraud, is the following:
1) letting them have FULL access to the contents of my drive -- really GOOD opportunity for identity theft and more ...
2) running their software without knowing WHAT it does.  How do we know it won't install some malware that, after my data gets restored, now sends my data to them?

That's why I asked if anyone has used this -- so we know if either of these fears is worth worrying about.

---

### Post by Megaptera on 2010-10-16
Looks like you were right Mark, moneer's post has been removed. I saw too that he posted the same suggestion elsewhere here around the same time.

---

### Post by nerdy_kid on 2010-10-16
> **Mark Phelps said:**
> I'm NOT concerned about a paltry $15 -- what I AM concerned about, if this is a fraud, is the following:
1) letting them have FULL access to the contents of my drive -- really GOOD opportunity for identity theft and more ...
2) running their software without knowing WHAT it does.  How do we know it won't install some malware that, after my data gets restored, now sends my data to them?

That's why I asked if anyone has used this -- so we know if either of these fears is worth worrying about.

oh yeah good point.  For some reason I had not thought about that.

---

### Post by zuerston on 2010-10-16
I bet if **"BIG BROTHER" **wanted those files,they would go right in there and get em,why not email Obama :P

---

### Post by nerdy_kid on 2010-10-16
> **zuerston said:**
> I bet if **"BIG BROTHER" **wanted those files,they would go right in there and get em,why not email Obama :P

rofl

---

### Post by Mark Phelps on 2010-10-17
The real "Big Brother" consists of folks who have ready access (legally or otherwise) to any place in the U.S.  Once they gain entrance and walk off with your PC or hard drive, they can get further access to whatever they want.

I'm not talking about "Big Brother"; I'm talking about a bunch of scam artists that put up a website pretending to offer data recovery services, when what they really want is to either steal someone's private data outright, or to load that person's PC with some malware that will steal the private data later.

OK, so I don't KNOW that these folks are pressing this kind of scheme -- which is why I asked if anyone had actually used this service.

---

