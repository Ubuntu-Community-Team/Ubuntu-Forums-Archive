---
title: "need help reinstalling ubuntu"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by insanity99 on 2010-06-02
i decided to completely remove ubuntu and make a fresh install. it was a mess anyway, i booted windows and uninstalled ubuntu in add or remove but it hasn't seemed to free up the 230GB(odd) of space that the virtual drive was (i used wubi). is the virtual drive still there? if so where is it and how do i delete it?

---

### Post by darkod on 2010-06-02
Depending which partition you selected when installing wubi, usually there should be 'ubuntu' folder in it. Inside that folder are all the files. There might be few boot files outside of it.

---

### Post by insanity99 on 2010-06-02
yeah there was an ubuntu file in C: but i deleted it, and emptied the recycling bin. the capacity of the drive was 233GB but i only have 136GB free on my HDD currently so obviously, the space hasn't been returned to me.

---

### Post by dino99 on 2010-06-02
use ccleaner with windows

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by insanity99 on 2010-06-02
i have CCleaner but it has never free'd up 200GB lol though i will give it a try.

what should i check for cleaning? all advanced a tent to leave unchecked and only a few with system.

---

### Post by insanity99 on 2010-06-02
ok i used free memory wipe which seemed to have done the job. now for the scary part, partitioning, i have downloaded 'ubuntu-9.10-desktop-amd64.iso' what do i need to do now? how risky is it to partition a used drive? i have over 932GB of data on my drive, its a lot to risk.

i have never done anything like this before so its pretty worrying. 

thanks

---

### Post by darkod on 2010-06-02
> **insanity99 said:**
> ok i used free memory wipe which seemed to have done the job. now for the scary part, partitioning, i have downloaded 'ubuntu-9.10-desktop-amd64.iso' what do i need to do now? how risky is it to partition a used drive? i have over 932GB of data on my drive, its a lot to risk.

i have never done anything like this before so its pretty worrying. 

thanks

Do you plan to do a full install now, on its own partition?
You need to decide how to organize your disks, where to install ubuntu first. It all depends how your disks are split into partitions.

---

### Post by insanity99 on 2010-06-02
well i am thinking of using about 70-100GB of my C drive for my ubuntu install.

my C drive is a 1TB HDD with 221GB free space, as i said i intend to use 70-100GB of that space.

---

### Post by darkod on 2010-06-02
You have a single partition on 1TB? Uhhhh.... Why not a smaller system partition for windows and then other data partitions? Anyway...

In windows vista and 7 you have a tool in Disk Management able to shrink partitions. Usually it's best to use that tool and shrink the partition 100GB. However, because windows has nasty habit of saving files all over the place, it might actually tell you that you can't shrink 100GB if it has unmovable (by windows terms) file in that area.
Usually I think disabling System Restore helps, but note that disabling the function deletes all restore points.

So, the procedure would be something like:
1. Backup the partition. Any resize operation has a degree of risk, you should have a backup just in case. :)
2. Use Disk Management to resize the partition for 100GB. Leave that space as unallocated, don't create a partition from it.
3. If Disk Management says it can't shrink 100GB, look online for solution what to do in that case.
4. Reboot windows few times to do its disk checks.
5. After windows is happy again, boot with the ubuntu cd, start the installer and in step 4 use the option Use Largest Available Free space. That will set it up inside the 100GB unallocated space you left.

Before starting the above you should run the ubuntu cd in live mode, Try Ubuntu option. That will show you any potential hardware issues. If live mode runs OK, most probably the install will be fine.

---

### Post by insanity99 on 2010-06-02
ah thanks for the help. i hear some people make 3 partitions '/' 'root' and 'swap', or something like that, do i not need to do that?

---

### Post by darkod on 2010-06-02
/ is root, it's the same. The third partition most widely used is /home. Linux can work both ways. The users Home folders can be just folders in /, or you can have separate /home partition created during install and the users Home folder are there.
Separate /home is recommended because it allows you to do a clean install over your existing ubuntu, but you can keep your personal files/settings because /home is another partition and you will format only /. Of course, the users created in the new install would usually need to have the same username.

It's similar like in windows when you have other partitions, D:, E:, etc. If windows breaks down, you format C: and install over it, but your data on D: is safe.

The guided methods of the ubuntu installer create only / + swap setup, and the method decides (I guess some algorithm) how much space to give to root and how much to swap from the space you left for ubuntu.

To have complete control how big every partition is created, and/or to create separate /home, you have to use the Manual Partitioning option during the install.

---

### Post by insanity99 on 2010-06-02
is the manual partitioning option easy to use? what do you think i should do? just go with the default settings or do it manually? i know you said it is recommended that you set up separate partitions but is it recommended for someone who has done nothing like this before?

EDIT: ah i also have this unmoveable files issue. it will only allow me to shrink 211MB's.

---

### Post by darkod on 2010-06-02
> **insanity99 said:**
> is the manual partitioning option easy to use? what do you think i should do? just go with the default settings or do it manually? i know you said it is recommended that you set up separate partitions but is it recommended for someone who has done nothing like this before?

EDIT: ah i also have this unmoveable files issue. it will only allow me to shrink 211MB's.

Manual Partitioning is really not a big deal. I know people who have never done it before are nervous, but it's pretty straightforward.
Plus, any partitioning changes you select will NOT be done until the actually install. Until you finish all 7 steps (screens), you can always go Back and change something, or Cancel the whole process.

Depending which version of windows you have, I suggest to google around how to shrink it. There must be good tutorials, I don't know any.

---

### Post by insanity99 on 2010-06-02
ok i will try manual partitioning, after i resolve this unmovable file crap that is. so i want to make '/' '/home' and 'swap'. what about the sizes?

---

### Post by Shazzam6999 on 2010-06-02
> **insanity99 said:**
> ok i will try manual partitioning, so i want to male '/' '/home' and 'swap'. what about the sizes?

I usually make the boot partition +100M, I think the minimum you need is +32M. People tell me the swap should be twice the size amount of RAM you have(and I think that's the Ubuntu default), although realistically unless you're consistently using that much memory it's unnecessary. Your /home partition can be whatever remains. Really, there's quite a bit of room to play around.

Err, make sure to flag your boot partition as boot and to change the type of your SWAP partition to swap.

---

### Post by darkod on 2010-06-02
> **insanity99 said:**
> ok i will try manual partitioning, after i resolve this unmovable file crap that is. so i want to make '/' '/home' and 'swap'. what about the sizes?

if you can spare 100GB to give to ubuntu, I would do:

/ 15GB ext4 filesystem
swap if you plan to hibernate regularly, you need 1.5 x ram memory, if not, even 2GB is enough
/home the rest, also ext4 filesystem

---

### Post by darkod on 2010-06-02
> **Shazzam6999 said:**
> I usually make the boot partition +100M, I think the minimum you need is +32M. People tell me the swap should be twice the size amount of RAM you have(and I think that's the Ubuntu default), although realistically unless you're consistently using that much memory it's unnecessary. Your /home partition can be whatever remains. Really, there's quite a bit of room to play around.

Err, make sure to flag your boot partition as boot and to change the type of your SWAP partition to swap.

Errr, when did the OP said he wanted /boot partition? Please don't throw in confusion. We are not talking about /boot here. And it's not needed anyway.

---

### Post by insanity99 on 2010-06-02
> **darkod said:**
> if you can spare 100GB to give to ubuntu, I would do:

/ 15GB ext4 filesystem
swap if you plan to hibernate regularly, you need 1.5 x ram memory, if not, even 2GB is enough
/home the rest, also ext4 filesystem

ok thanks i will right this down so i dont forget during install lol.

i downloaded PerfectDisk, the 'World leading defragmenter'(trail) hopefully this will take care of windows stupid way of storing data.

EDIT: this to just ignores the MFT file, fearfully, like it was a mob leader. i read that 3rd party partition managers, such as partition wizard will shrink without issues. i guess i must give that a try.

---

### Post by insanity99 on 2010-06-02
good news i have successfully shrunk the HDD 100GB without data lose. thats the dangerous part over right?

---

### Post by insanity99 on 2010-06-02
does this look ok?

EDIT: it worked thanks for the help darkod your an amazing user.

---

### Post by darkod on 2010-06-03
You did great. It wasn't so difficult, was it? :)

Shrinking windows is sometimes such a hassle. Third party tools often work, you can even use Gparted from ubuntu live mode (System-Administration). However, sometimes windows is stubborn when other tools try to resize its partitions.

With the same problem you had, Disk Management allowing to shrink only little space when you have a lot more free space, I have shrunk Vista system partition with Gparted and it still worked out OK.

The first option should be Disk Management, if it allows you to shrink as much as you want.

---

### Post by insanity99 on 2010-06-03
thanks again, it is scary the first time but it is pretty easy your right lol.

---

