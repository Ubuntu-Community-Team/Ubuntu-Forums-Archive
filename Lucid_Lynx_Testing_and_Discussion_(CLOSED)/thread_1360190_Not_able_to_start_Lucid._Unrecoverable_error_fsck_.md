---
title: "Not able to start Lucid. Unrecoverable error fsck /home"
date: 2009-12-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-12-20
Hi All,

I am not able to get to login screen. I am getting the following error.

Unrecoverable error fsck /home.

Any Help!
SK.

---

### Post by ranch hand on 2009-12-20
How is your box set up?  Just the one OS?  More?  How about some info on the specs of the box itself.

---

### Post by donniezazen on 2009-12-20
Sorry to not to give any info. I have dual boot with windows XP. I have a Dell 6400/E1505.

Thanks.

---

### Post by ranch hand on 2009-12-20
If you have room I would put another ext4 version of Ubuntu on your box and see if you can recover data.

I would then reinstall after reformating your /home partition.

If you do not have room for another OS you could try retrieving the data with your LiveCD and burning it to CD/DVD.  RW is your friend.

Do not mark anything to format in your installer.  I have no idea what this will do to your / partiton but would love to hear if it leaves you with your extras or just over-writes /.

Unfortunately unrecoverable means unrecoverable as far as I know.

If you look at my sig you will see info on my box.  You might consider something like that.  I am not at all familiar with all makes and models and have no desire to look it up.

---

### Post by donniezazen on 2009-12-20
> **ranch hand said:**
> If you have room I would put another ext4 version of Ubuntu on your box and see if you can recover data.

I would then reinstall after reformating your /home partition.

If you do not have room for another OS you could try retrieving the data with your LiveCD and burning it to CD/DVD.  RW is your friend.

Do not mark anything to format in your installer.  I have no idea what this will do to your / partiton but would love to hear if it leaves you with your extras or just over-writes /.

Unfortunately unrecoverable means unrecoverable as far as I know.

If you look at my sig you will see info on my box.  You might consider something like that.  I am not at all familiar with all makes and models and have no desire to look it up.

Thanks for the reply. I suspected the same. I have reinstalled Ubuntu using USB drive. I have a separate home partition so i have all my data safe. :( the pain is all installing updates, settings and softwares.

---

### Post by phillw on 2009-12-20
one last gasp attempt ...

assunming /home is /dev/sda4  (Change it your own)

Try

```
 sudo e2fsck -y /dev/sda4 
```

That's gotten me out of the mire once before.

Phill.

---

### Post by barnaclebill18 on 2009-12-20
I also am interested, I reinstalled Karmic without formatting, and it left all my settings intact and also most programs, but I only had a couple.

---

### Post by ranch hand on 2009-12-20
> **phillw said:**
> one last gasp attempt ...

assunming /home is /dev/sda4  (Change it your own)

Try

```
 sudo e2fsck -y /dev/sda4 
```That's gotten me out of the mire once before.

Phill.
How is this different than fsck?  Just and ignernt noob longing for knowledge.

---

### Post by phillw on 2009-12-20
Hi,

I posed this question  --> [http://ubuntuforums.org/showthread.php?t=1351477](http://ubuntuforums.org/showthread.php?t=1351477)

What I now have is LL on it's own partition
Complete with it's own internal ~home
/home (from 9.10) on it's own partition
I used rsync to drop 9.10's /home onto LL's home area.

Last time I borked my LL, I did a fresh install & rsync'd my home back over.

I take backups of LL in the same way I do my production area.

A bit late for you - I know, but will hopefully prevent such a thing happening again.

Whenever I want to move stuff from LL to my 9.10 area I just mount /home and pop the files onto my ~Desktop folder - and they are there when I boot into 9.10.

If I've been doing a lot of work on 10.04 & want history etc, copying over - I just rsync the LL /home with my 9.10 /home
I do, however have a backup of my 9.10 /home 
Yeah, so I'm paranoid about backups !!!!

Phill.

Phill.

---

### Post by donniezazen on 2009-12-20
> **phillw said:**
> one last gasp attempt ...

assunming /home is /dev/sda4  (Change it your own)

Try

```
 sudo e2fsck -y /dev/sda4 
```

That's gotten me out of the mire once before.

Phill.

Sorry can't test it already reinstalled.

Thanks.

---

### Post by ranch hand on 2009-12-20
Did or did not you loose your / when you reinstalled not formating that partition?

---

### Post by donniezazen on 2009-12-20
> **ranch hand said:**
> Did or did not you loose your / when you reinstalled not formating that partition?

O! i formatted the root partition before partition. Never tried reinstalling without formatting. Can you actually save your installed softwares and setting by just installing without formatting?

---

### Post by ranch hand on 2009-12-20
Beats me.  I was hoping you would find out.

I know that not formatting your /home usually works (back up still a great idea).  I have never lost anything that route.

I may have to have another install here just so I can get it all set up and then try that,

Might be FUN.

---

### Post by donniezazen on 2009-12-20
> **ranch hand said:**
> Beats me.  I was hoping you would find out.

I know that not formatting your /home usually works (back up still a great idea).  I have never lost anything that route.

I may have to have another install here just so I can get it all set up and then try that,

Might be FUN.

No worries! Nvidia is giving me enough opportunity to reinstall my system twice a week.lol

---

### Post by ranch hand on 2009-12-20
Well if your /home is what is screwed try not formating the / and see what happens.  If it worked it would surely beat downloading all the stuff you add to /.

I rarely format my /home and that saves having to rebuild my files (so far), I do back up if there is anything important.

---

### Post by k3lt01 on 2009-12-20
> **ranch hand said:**
> I rarely format my /home and that saves having to rebuild my files (so far), I do back up if there is anything important.I format the entire system, but for /home I copy it to an external hdd and then copy it back.

Doing it that way I still have my settings etc, but I also have improvements that have been developed since the last release in things like file systems (ext3 > ext4) and also incidentals like changes in the Places menu that wouldn't otherwise be written into the system. It also helps with the little bit of fragmenting that occurs over time.

---

### Post by donniezazen on 2009-12-20
> **ranch hand said:**
> Well if your /home is what is screwed try not formating the / and see what happens.  If it worked it would surely beat downloading all the stuff you add to /.

I rarely format my /home and that saves having to rebuild my files (so far), I do back up if there is anything important.

If you don't format your /home you get a new installation with old settings and do you which you don't see the new default improvements. So i just copy all my files to a folder and delete all hidden files with settings in home folder. This way i have all my data and new settings. Just like a new system. And it is always advised to have backup.

---

### Post by ranch hand on 2009-12-20
I don't know, I never tried it.

Just because you do not format does not mean that it is not installing on there.  I have seen that (I watch the out put on apt and have synaptic set for terminal out put too).  It over writes some stuff when needed, thus the backup being smart.

---

### Post by VMC on 2009-12-21
> **soham_1207 said:**
> O! i formatted the root partition before partition. Never tried reinstalling without formatting. Can you actually save your installed softwares and setting by just installing without formatting?

Yes you can. I tried that on a couple of messed up installs. I used the same partition without re-formatting and my /home was left intact.

---

### Post by ranch hand on 2009-12-21
What about the other way - format /home and leave /?

I think I really need to try that.

---

### Post by VMC on 2009-12-21
> **ranch hand said:**
> What about the other way - format /home and leave /?

I think I really need to try that.

I forgot to say, I only use one partition "/" (to rule them all). I do make regular clone of that partition. I'm not sure the outcome of multiple partitions. I've done it this way for years. I got tired of all those multiple partitions when I use to work for AT&T and there Unix systems.

---

### Post by donniezazen on 2009-12-21
> **VMC said:**
> Yes you can. I tried that on a couple of messed up installs. I used the same partition without re-formatting and my /home was left intact.

I am little confused here. What i do is format / and don't format /home which leaves most of the settings (like wallpaper, theme, icons, browser settings etc) but no software or updates are left.

What did you do? Reinstall without formatting / or /home (so you don't format anything) . And you were able to save your softwares and repo's etc:confused:

---

### Post by ranch hand on 2009-12-21
No, the OP had an "unrecoverable fault in his /home fs.  Reinstalled.

I just wonder what would have happened if he tried to just reinstall the /home and leave the / untouched.

I still wonder and am considering what flavor OS to use as a victim.  I have the 10.04 disk handy, I think I will use it.

---

### Post by Framli on 2009-12-21
Had the same problem yesterday and as I don't have a separate /home, it was on the whole / partition. :P

I tried to boot many times, with different kernels who all gave me the same error.

Today, I was ready to chroot and play, but when I turned on my testing laptop the problem was "magically" solved and everything was booting and running fine... :)

---

