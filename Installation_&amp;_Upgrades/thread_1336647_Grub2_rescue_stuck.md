---
title: "Grub2 rescue stuck"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by HellHornet on 2009-11-24
Hi all,

I have some issues :) After getting frustrated with Vista I decided to try out Ubuntu 9.10 which went smoothly and I was enjoying it for a couple of days before I noticed the update feature. I clicked the button and updated the OS, upon restart I was met with the Grub2 Bootloader crap. 

I did a bit of research and found the grub2 documents and went through the steps for reistalling grub, but now I am stuck on a new screen stating, "GRUB rescue" I really need to gain access to my files, there is 500gb of data which is now effectively locked.

Note: My harddrive as 2 partitions, 1 with Vista & Ubuntu installed and the other with personal data.

thanks in advance

---

### Post by phillw on 2009-11-24
Hi,

Recovering windoze and ubuntu areas is covered here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That'll get you sorted :p

Should things be REALLY messed up, then head over to --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Regards,

Phill.

---

### Post by HellHornet on 2009-11-24
thanks for those links, going through them now. so much effort and i havent event got started on linux tut tut/

---

### Post by HellHornet on 2009-11-24
OK now I have reinstalled the bootloaders for both ubuntu and vista and can boot windows. But now I am back to my original problem of not being able to access Ubuntu due to GNU GRUB version 1.97 error. Any further suggestions please.

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> thanks for those links, going through them now. so much effort and i havent event got started on linux tut tut/

lol, with freedom comes responsibility. It'll possibly take you a while to get 'into' the ubuntu mind-set.
We were all noobies once.
There's lots of 'hi end' stuff (running a full server setup) that I have had questions for - but the support from these forums is awesome. Just remember, chances are, some one has had the same problem before - and, if enough have - there's a tutorial for it. No question is 'dumb' - not asking is 'dumb' - The support system for Ubuntu is somewhat different to other operating systems :)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)   sums it up.
A more light-hearted approach is here --> [http://linuxgazette.net/issue45/orr.html](http://linuxgazette.net/issue45/orr.html)

When you've used Ubuntu for a while, you'll appreciate our humour :D

Please accept my apology for not saying welcome to ubuntu on my 1st post back to you.

Regards,

Phill.

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> OK now I have reinstalled the bootloaders for both ubuntu and vista and can boot windows. But now I am back to my original problem of not being able to access Ubuntu due to GNU GRUB version 1.97 error. Any further suggestions please.

Does the error have an error number ?

Phill.

---

### Post by phillw on 2009-11-24
As the windows area is back - you should be able to transfer booting rights over to Grub2 as detailed in >  [SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

of [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Phill.

---

### Post by HellHornet on 2009-11-24
thanks for the links on linux humour, seems kinda true when u think about it, reason why i wanted to try linux was because vista stopped doing what i wanted to do and there was no reason for it :).

Anyway back on topic the error simply states GNU GRUB version 1.97~Beta4 (some extra text) and a command prompt. 

Sincerely
John

---

### Post by HellHornet on 2009-11-24
> **phillw said:**
> As the windows area is back - you should be able to transfer booting rights over to Grub2 as detailed in 

of [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Phill.

Umm i did that first and from what I gathered it worked, and has led me back to the current problem.

---

### Post by phillw on 2009-11-24
okies ... this is a bit scary to new comers (it scared the living daylights out of me when i messed up my Grub2 a couple of days ago) But, it does work. Follow the instructions. If you're not too sure on stuff - post the output of ```
sudo fdisk -l
``` And I'll tell you the device parameters that you need.

Section 12 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you see grub rescue prompt , then you need to be a bit lower down at section 14

Section 12 is what I did to recover my messed up system (I have Vista and ubuntu)

I'll keep this thread open - so do let me know how you get on !!

Regards,

Phill.

---

### Post by HellHornet on 2009-11-24
I followed step 12 as directed but the problem is still there, only difference made is that the windows bootloader has been erased/overtaken by the Ubuntu Grub. Here is the code:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e5d980d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12749   102400000    7  HPFS/NTFS
/dev/sda2   *       12749       60802   385984512    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by phillw on 2009-11-24
I've asked drs to have a look - He's more knowelegable than I am on things Grub2 (he wrote the how-to's i've refferred you to)

He'll be along presently.

Regards,

Phill.

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> I followed step 12 as directed but the problem is still there, only difference made is that the windows bootloader has been erased/overtaken by the Ubuntu Grub. Here is the code:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e5d980d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12749   102400000    7  HPFS/NTFS
/dev/sda2   *       12749       60802   385984512    7  HPFS/NTFS
ubuntu@ubuntu:~$


Ahhhhh.... you're running wubi.  Darn me for not checking 1st.  (Kicks self)

Phill.

---

### Post by HellHornet on 2009-11-24
yeah i guess i should have mentioned that first, from the looks of things this is where I have gone wrong (but in all honesty the install went so smoothly I had no reason to suspect that Wubi would be the cause of problems). Thanks for the referal and eagerly awaiting the response

John

---

### Post by parkland on 2009-11-24
This just also happened to me, on my laptop.

I accidentally filled the hard drive completely full (from backing up my other machine, which has a 9.10 ext4 install that is failing)

I ran my disk full many times with 9.04 & ext3, so I blame ext4 for this. I just reinstalled 9.10 & ext4 on my laptop, and will continue the experience, but on my desktop, it is getting ext3 because I dont want to lose everything. :(

---

### Post by HellHornet on 2009-11-24
well that will be my backup plan, if all else fails I will just get a new harddrive and do a fresh install and then save the files that I want from the old one, question is where the heck do you transfer 500gb worth of data.

---

### Post by phillw on 2009-11-24
The pauses are me and drs in IM.  Go back, restore your windows MBR.  Recovery options from Wubi are very limited, but not impossible. And, I should have spotted it from >  Note: My harddrive as 2 partitions, 1 with Vista & Ubuntu installed and the other with personal data.

My mess up on that one. Let's get Windows boot back & get any data you have in the Wubi area saved before you hose it & do a fresh Wubi install.

The other option of dual booting is preferable, but as you've had a scare with ubuntu, you're probably not too keen on that. Wubi runs under windows & does its best, just sometimes that is not quite good enough.

Putting a true 'dual boot' is painless and offers much more stability than Wubi can do.

Regards,

Phill.

---

### Post by phillw on 2009-11-24
> **parkland said:**
> This just also happened to me, on my laptop.

I accidentally filled the hard drive completely full (from backing up my other machine, which has a 9.10 ext4 install that is failing)

I ran my disk full many times with 9.04 & ext3, so I blame ext4 for this. I just reinstalled 9.10 & ext4 on my laptop, and will continue the experience, but on my desktop, it is getting ext3 because I dont want to lose everything. :(

Linux does require you to have your active brain cell as the active partion before you carry out certain commands - lol

But, seriously, taking a backup to a different system is quite easy - you can use clonezilla (I believe it's called) or a simple script from here --> [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Mine looks like this ```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/phillw/Desktop/PhillzMuzic --exclude=/tmp /

```

the last / tells it where to put the backup.

Regards,

Phill.

---

### Post by HellHornet on 2009-11-24
ok i have the windows boot back, at the risk of sounding naive, now what?

Regards,
John

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> well that will be my backup plan, if all else fails I will just get a new harddrive and do a fresh install and then save the files that I want from the old one, question is where the heck do you transfer 500gb worth of data.


If your disk is that full - and you don't have a backup ... then I'd be sweating. Bad things can happen to good hard-drives. The TB disks are reasonably affordable now - it's down to how much value you put on your data.

Ubuntu can look after backups, as my post, above, covers.

Regards,

Phill.

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> ok i have the windows boot back, at the risk of sounding naive, now what?

Regards,
John

what data is in your wubi area that you need to save before we hose it & do a fresh install of Wubi ?

Phill.

---

### Post by HellHornet on 2009-11-24
> **phillw said:**
> If your disk is that full - and you don't have a backup ... then I'd be sweating. Bad things can happen to good hard-drives. The TB disks are reasonably affordable now - it's down to how much value you put on your data.

Ubuntu can look after backups, as my post, above, covers.

Regards,

Phill.

The important stuff is very important stuff is backed up, the fun stuff is not. I just need the weekend to come about so I can do some shopping for a new HD just to be extra safe. 

Regards
John

---

### Post by HellHornet on 2009-11-24
> **phillw said:**
> what data is in your wubi area that you need to save before we hose it & do a fresh install of Wubi ?

Phill.

Nothing, it had only been 2 days before the crash so all i had done upto this point was download some softwares and personalise ubuntu, nothing that cant be replaced i suppose.

---

### Post by phillw on 2009-11-24
That sounds like a plan :-)

If you let me know what sorta important stuff (bookmarks , documents etc) u had in your Wubi area, I can tell you how to pull them clear of that folder. Having had a chat with drs, sadly, it does not look like we can resurrect your Wubi installation, so we're now at data backup stage.

With a backup in place, slicing your disk to give you true dual-boot is painless. Whilst I have sliced / moved / shrunk - grown my hard disk more times than is good (It scares the living daylights of me, still) - I've never had one fail on me. That does not negate the fact you MUST have a full backup - otherwise Murphys Law will kick in.

Phill.

---

### Post by parkland on 2009-11-24
> **phillw said:**
> Linux does require you to have your active brain cell as the active partion before you carry out certain commands - lol

But, seriously, taking a backup to a different system is quite easy - you can use clonezilla (I believe it's called) or a simple script from here --> [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Mine looks like this ```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/phillw/Desktop/PhillzMuzic --exclude=/tmp /

```

the last / tells it where to put the backup.

Regards,

Phill.



The worst part is that these files were already moved to an external drive.
I had 8gb space left, deleted 150gb backup folder, emptied trash, and later realized I had no free space! After emptying the trash, the files were somehow gone, but still taking up space!
I restarted but then I learned that the filesystem was currupt. 1st boot said "can not mount filesystem" 2nd boot said "grub2 rescue".

Like you said, wasnt the smartest thing to do, but like I said, ext3 * 9.04 didnt fart let alone crash.

I think ext4 could be great, but it obviously needs some tuning.

---

### Post by HellHornet on 2009-11-24
Although as I said that the wubi section is completely empty my hd partitions are totally full with about 20gb free. I am slightly hesistant to start messing around at this stage and am leaning towards waiting until I can source a new hd so that I could backup the entire contents of my drive.

Please advice what you would do?
Regards
John

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> Nothing, it had only been 2 days before the crash so all i had done upto this point was download some softwares and personalise ubuntu, nothing that cant be replaced i suppose.


Get your backup done of sda (Your primary disk) C:  in windows speak (unless you have partitions within that) - If so, I'll give you a script to 'photo-copy' your disk to another disk.

Rule #1 - Backup the Data
Rule #2 - Check the Backup is okay
Rule #3 - Go and 'play' :D

Whilst you are waiting for you backup disk, head over to [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Choose the one you'll be using and have a read though. As you'll be putting Ubuntu on AFTER a windows install, you need not worry about the fact some of their How-To's are based on earlier versions of Ubuntu - the methodology is the same.

Also, while you are w8ing, get yourself an AIM account - they're free & I'm always kicking around somewhere near my computer except when I'm asleep - lol

Because of spam attacks etc. we're not allowed to issue email addresses etc in threads, but I can send you my details in a Private Message, if you wish.

Regards,

Phill.

---

### Post by phillw on 2009-11-24
> **parkland said:**
> The worst part is that these files were already moved to an external drive.
I had 8gb space left, deleted 150gb backup folder, emptied trash, and later realized I had no free space! After emptying the trash, the files were somehow gone, but still taking up space!
I restarted but then I learned that the filesystem was currupt. 1st boot said "can not mount filesystem" 2nd boot said "grub2 rescue".

Like you said, wasnt the smartest thing to do, but like I said, ext3 * 9.04 didnt fart let alone crash.

I think ext4 could be great, but it obviously needs some tuning.

The usual one for that is that you were using root. the trash area for root doesn't clear itself. It's one more reason not to use root.  Other ones that can catch people out are  is scripts that backup to an external device that isn't mounted & the files system stuffs itself.

I'm putting an area of ext4 onto my system for Lucid to have a 'play' with. It is my goal to move to Lucid and STAY THERE !!!!  It is an LTS, I came in to the system at 9.04, so well through the release cycle. The secret of having nice things happen is to try them out before you commit. I just wish more people wouldn't go jumping onthe 'latest' just because it is there - I had good reason to move over to 9.10 and also to Grub2 - that being a 6 month lead time for Lucid. As to why other people have updated from perfect;ly working 9.04 systems to 9.10, I can only guess. I'd certainly not have done so.

Phill.

---

### Post by HellHornet on 2009-11-24
phill thanks for the help so far, its getting abit late now and i need my beauty sleep. I will get back to messing with linux tomorrow hopefully. In the meantime good night and thanks again.

Regards,
John

---

### Post by HellHornet on 2009-11-24
> **phillw said:**
> That sounds like a plan :-)

If you let me know what sorta important stuff (bookmarks , documents etc) u had in your Wubi area, I can tell you how to pull them clear of that folder. Having had a chat with drs, sadly, it does not look like we can resurrect your Wubi installation, so we're now at data backup stage.

With a backup in place, slicing your disk to give you true dual-boot is painless. Whilst I have sliced / moved / shrunk - grown my hard disk more times than is good (It scares the living daylights of me, still) - I've never had one fail on me. That does not negate the fact you MUST have a full backup - otherwise Murphys Law will kick in.

Phill.

Actually before I go to sleep, i have noticed that when i installed thunderbird under ubuntu it downloaded all my emails off the POP3 hotmail servers and onto my pc, is there any way I would be able to gain access to thunderbird to correct this problem?

Thanks again.

---

### Post by phillw on 2009-11-24
> **HellHornet said:**
> Actually before I go to sleep, i have noticed that when i installed thunderbird under ubuntu it downloaded all my emails off the POP3 hotmail servers and onto my pc, is there any way I would be able to gain access to thunderbird to correct this problem?

Thanks again.


Yeah, I've seen that on a thread ... I'll go dig it out & post it here and in a PM to you.

Regards,

Phill..

---

### Post by phillw on 2009-11-24
Yeah ... we just need to take a copy of a hidden directory. I'll talk you thru it once we've both had some sleep :D

Phill.

---

