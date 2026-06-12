---
title: "GRUB2 Rescue"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Apolyonn on 2012-11-25
Per a friend's suggestion, I've been checking out #! on my netbook.  Since I'm concerned more about stability and battery-life on my netbook, I didn't have a reason to keep it, so I deleted the partition.  Joke's on me, GRUB2 went with it.

Now I'm at this "grub rescue" business, and I have no idea what I'm doing.

My question is: is there a way to boot into my Linux partition and repair grub via Lubuntu, rather than creating and booting up a livedisk?  IF the livedisk option is the *ONLY* solution, then so be it, but I'd rather have the know-how to fix this without doing so.

Thanks.

---

### Post by 2F4U on 2012-11-25
These articles explain how to rescue grub:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jualin on 2012-11-25
> **Apolyonn said:**
> Per a friend's suggestion, I've been checking out #! on my netbook.  Since I'm concerned more about stability and battery-life on my netbook, I didn't have a reason to keep it, so I deleted the partition.  Joke's on me, GRUB2 went with it.

Now I'm at this "grub rescue" business, and I have no idea what I'm doing.

My question is: is there a way to boot into my Linux partition and repair grub via Lubuntu, rather than creating and booting up a livedisk?  IF the livedisk option is the *ONLY* solution, then so be it, but I'd rather have the know-how to fix this without doing so.

Thanks.

You can try using [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") within Lubuntu. It works pretty nicely in a normal Ubuntu install so it should work on Lubuntu. Good luck :)

You would then need to open the Terminal, add the "yannubuntu" repository, install boot-repair and run it:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

---

### Post by Apolyonn on 2012-11-25
2F4U: thanks for the response; unfortunately, neither links contain an answer to my question.

jualin:  as of now, I have no idea how to boot into Lubuntu from "grub rescue>", so I can't install any programs as of yet.

In other news, reading the first post on [this]("http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub+rescue+lubuntu") thread, it seems that the only issue I've ran into is finding the linux.mod file.  since both the "insmod linux" and "insmod /boot/grub/linux.mod" commands give me "file not found."  Anyone have any ideas?

---

### Post by jualin on 2012-11-25
> **Apolyonn said:**
> 2F4U: thanks for the response; unfortunately, neither links contain an answer to my question.

jualin:  as of now, I have no idea how to boot into Lubuntu from "grub rescue>", so I can't install any programs as of yet.

In other news, reading the first post on [this]("http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub+rescue+lubuntu") thread, it seems that the only issue I've ran into is finding the linux.mod file.  since both the "insmod linux" and "insmod /boot/grub/linux.mod" commands give me "file not found."  Anyone have any ideas?

OK, I misread your answer and thought that you had access to Lubuntu. Since you are not finding linux.mod then that means that you didn't set the prefix correctly. Basically, you are probably pointing Grub to the wrong partition in your hardrive. 
If you only have one hardrive then that would be #0 and you would need to find the partition where Ubuntu was installed. Repeat Step 2 of the [first post]("http://ubuntuforums.org/showpost.php?p=9957262&postcount=1") until you find your partion (You should be able to do a "ls (hd0,n)/boot/grub ", where "n" is your partition number where Ubuntu is installed.

---

### Post by wildmanne39 on 2012-11-25
*Thread moved to **Installation & Upgrades**.*

---

### Post by Apolyonn on 2012-11-25
> **jualin said:**
> OK, I misread your answer and thought that you had access to Lubuntu. Since you are not finding linux.mod then that means that you didn't set the prefix correctly. Basically, you are probably pointing Grub to the wrong partition in your hardrive. 
If you only have one hardrive then that would be #0 and you would need to find the partition where Ubuntu was installed. Repeat Step 2 of the [first post]("http://ubuntuforums.org/showpost.php?p=9957262&postcount=1") until you find your partion (You should be able to do a "ls (hd0,n)/boot/grub ", where "n" is your partition number where Ubuntu is installed.

No worries.  (hd0,msdos6) is definitely my Lubuntu partition.  

However, in step 3 "set prefix=(hdX,Y)/boot/grub", I appended "/i386-pc/" because that's where my .mod files are located (in /boot/grub, I only see a couple of folders and grub.cfg).  I don't know if any of this would make a difference, but linux.mod isn't in /boot/grub or /i386-pc.

---

### Post by jualin on 2012-11-26
> **Apolyonn said:**
> No worries.  (hd0,msdos6) is definitely my Lubuntu partition.  

However, in step 3 "set prefix=(hdX,Y)/boot/grub", I appended "/i386-pc/" because that's where my .mod files are located (in /boot/grub, I only see a couple of folders and grub.cfg).  I don't know if any of this would make a difference, but linux.mod isn't in /boot/grub or /i386-pc.

Interesting, what is the output of "ls /boot/grub/i386-pc", "ls /usr/lib/grub/i386-pc" and "ls /boot/grub" in grub-rescue?

---

### Post by jualin on 2012-11-26
Maybe someone can correct me if I am wrong but I think that if you cannot find your modules then GRUB will not be able to boot. 
It might be easier and faster to just boot with a LiveCD, install boot-repair in the live session and run it. Boot-repair will take care of installing GRUB on your partition and finding the Lubuntu installation. :)

---

