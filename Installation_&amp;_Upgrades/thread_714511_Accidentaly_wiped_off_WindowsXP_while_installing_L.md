---
title: "Accidentaly wiped off WindowsXP while installing Linux Ubuntu?"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by TheNinja on 2008-03-03
is there any way to recover my windows now? i have a dell dimension e310 and there suppose to be norton ghost in the bios but cant find it :confused::confused::confused::confused:  :(:(:(is my Windows XP gone forever?

---

### Post by BobSongs on 2008-03-03
[FONT=Verdana]Did you run Norton Ghost before installing Ubuntu? If so you should be able to recover your Windows XP data by the procedure described in the manuals provided by Dell.

What hard drive option did you select when installing 
when installing Ubuntu? If you're running Linux now and you don't see Windows, it may just be that your Windows partition is not mounted.

However, if you chose to install Ubuntu over the whole hard drive, you have likely lost your entire Windows setup. My hope is that you've backed up your personal documents or that they reside on a different partition (i.e., D: drive for example).
[/FONT]

---

### Post by brent113 on 2008-03-03
Welcome to a new world of file recovery.  My suggestion is to acquire some excellent drive recovery software, I personally use Easy Recovery Professional.

That can recover partitions and other data as long as it is on the disk and has not been written over.  Since it's likely the entire partition is not in tact, I suggest using it to scan for files you want recovered.

Most of the data probably will be gone.  Don't feel too bad though, I'm right with you.  Yesterday I accidentally deleted every piece of software I've ever written.  Pretty upset over that one.

---

### Post by Jay Jay on 2008-03-03
Not necessarily - you might be in luck, maybe some of the others might have Linux solutions but this is what I know from my DOS/Windows days. 

1) [Access the recovery console option from your Win XP CD]("http://support.microsoft.com/kb/307654")

2) From the recovery console you can try using the [Unformat]("http://www.easydos.com/unformat.html") command on the relevant partition to rescue your XP installation.

Hope this helps!

---

### Post by TheNinja on 2008-03-03
the first time i installed it i think i messed up the partitions by choosing something like "new partition table" or somethin like that then i tried installing windows xp sp1 it didnt connect to the internet and graphics were wrong so i just installed linux again overwriting everything  
any chance of recovering now? 
btw im using linux right now

---

### Post by BobSongs on 2008-03-03
[FONT=Verdana]Well, from your description it would appear that you've overwritten the data on your hard drive several times now.

If your Windows XP partition was erased, written over with Ubuntu using ext2, returned to ntfs/fat32 and then back again to ext2... there may be some recoverable files but the possibility of recovering those files decreases dramatically each time this happens.

At this point Jay Jay's advice may not work at all because your NTFS filesystem is gone entirely. And brent113's suggestion sounds like it may work, however it will mean installing XP on your system *again*.

Now it is very possible a recovery program will work. But it will mean re-installing XP and getting hold of this software. And you said>  i tried installing windows xp sp1 it didnt connect to the internetSo it means searching for and downloading software for XP while in Linux. You'd need to burn this to a CD then re-install XP and install that recovery software.

Personally: I hold out little hope of recovery. But these packages can be quite surprising in what they're able to do.

How to proceed depends on how important those files were. I leave that in your hands. It may also depend on how much you're willing to spend on recovery software.

Keep us apprised on how things go.
[/FONT]

---

### Post by TheNinja on 2008-03-04
since i have to reinstall windows again maybe it isnt worth the trouble of recovering the files since there wasnt anything of real importance though i hate the idea of reorganizing all my pics that i backed up on CDs

---

### Post by BobSongs on 2008-03-05
> **TheNinja said:**
> since i have to reinstall windows again maybe it isnt worth the trouble of recovering the files since there wasnt anything of real importance though i hate the idea of reorganizing all my pics that i backed up on CDs:popcorn: Yay! All your photos are backed up. Excellent. So we're talking about a minor inconvenience instead of a serious loss of information. Good. I'm glad you did a wise thing: you backed up your info first. :guitar:

Still, I'm sorry to hear of the loss. PCs were meant to maintain our data, not lose it for us. Sort of defeats the purpose.

If you wish to dual boot your PC from XP to Ubuntu, I'd suggest you start again with a full wipe, cutting a small partition for XP, installing Ubuntu second, downloading Service Pack 2 (or 3) and saving it to your XP partition, upgrading XP and then using both systems.

If you're what I call a "light" user (just such applications as e-mail, instant messaging, photo management, the occasional office document, surfing the web) then stick with Ubuntu for about 2 months and see if you really need to go back. If not, your system is set up and ready for daily use.

If you're a "heavy" user (you've purchased all kinds of proprietary software that your dependent on like QuarkExpress, PhotoShop, CorelDRAW, Macromedia software, sound-recording software, millions of games, etc.) then a dual boot is more along what you'll need to remain happy.

Thanks for the update.

Bob

---

