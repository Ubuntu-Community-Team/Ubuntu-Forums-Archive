---
title: "boot failure after shutdown during upgrade"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by RememberWhenItRained on 2012-01-11
So, I finally decided to bite the bullet and upgrade to 11.10 from 10.04. I loaded 10.10 on a USB drive and after annoying prompts to enter a disc i didn't have, unchecked that option from software sources.

I was in the middle of an update to 10.10 on my laptop (without my power cord) and my computer shut down in the middle of the update. Now, when trying to access the linux OS, it freezes at the purple loading screen (after all the dots are colored.) When trying to access both recovery mode and previous kernels, they all freeze in a blank/black screen.

Fortunately, I am dual booting (well, triple, but that's beside the point) so I am using my Win7 partition right now.

How to i resolve this issue while keeping my settings/files/etc. Is there a way I can patch/repair the update?

Thanks.

---

### Post by carl4926 on 2012-01-11
Do you have /home on a separate partition? Because my guess is you will need to do a new install. You can use a Live CD to recover all your personal files, even if they are not separate, but if they were you could just keep /home. So less to worry about.

You realize that to perform a distro upgrade with no power is asking for trouble?!

---

### Post by RememberWhenItRained on 2012-01-11
> **carl4926 said:**
> Do you have /home on a separate partition? Because my guess is you will need to do a new install. You can use a Live CD to recover all your personal files, even if they are not separate, but if they were you could just keep /home. So less to worry about.

You realize that to perform a distro upgrade with no power is asking for trouble?!

I'm not sure. /home on a separate partition to what? See attached screenshot, that might give you your answer.

So a live USB will work the same as the CD i presume. There a specific utility i should use?

And yeah, it was stupid, i didn't realize i was low on battery and was going to plug it in soon. Too late, obviously.

---

### Post by carl4926 on 2012-01-11
So you are working with a Live USB?
Yes it's the same as a CD

There is a process where you can chroot to the installed system. But it's kind of complicated. And before I did any more I'd backup files I really needed. Can you do that? You need something to write the files to, that could be an external HD or an internal Partition (Eg; if you have a windows install there) you could create a folder on there and write all your data to it, assuming there is room. The file manager should let you do all this.

Once you have stuff backed up. You can look at the repair or re-install.

If you want to try a chroot to the installed system and try to continue the upgrade, we could have a go. But in any case I'd still recommend a new install, especially after this fiasco

---

### Post by prshah on 2012-01-11
> **RememberWhenItRained said:**
> I was in the middle of an update to 10.10 on my laptop (without my power cord) and my computer shut down in the middle of the update. 

Can you access a recovery terminal? Look for recovery options in the GRUB menu (may have to tap shift or esc during bootup).

If you can reach a recovery terminal, please see this thread [Hardy is wonderful]("http://ubuntuforums.org/showthread.php?t=780531") for advice on how to recover from an interrupted upgrade. The advice is dated but still applicable. Summary (but please read the linked thread):```
dpkg --configure -a
```

Please post back here if you have problems with this advice.

---

### Post by carl4926 on 2012-01-11
> **RememberWhenItRained said:**
> I'm not sure. /home on a separate partition to what? See attached screenshot, that might give you your answer.

So a live USB will work the same as the CD i presume. There a specific utility i should use?

And yeah, it was stupid, i didn't realize i was low on battery and was going to plug it in soon. Too late, obviously.

Well it looks like you probably have /home separate
But you need to examine the file system contents on those partitions to be sure which is which.
Parted Magic or even the Ubuntu live cd will give you a better idea.

---

### Post by RememberWhenItRained on 2012-01-11
> **prshah said:**
> Can you access a recovery terminal? Look for recovery options in the GRUB menu (may have to tap shift or esc during bootup).

If you can reach a recovery terminal, please see this thread [Hardy is wonderful]("http://ubuntuforums.org/showthread.php?t=780531") for advice on how to recover from an interrupted upgrade. The advice is dated but still applicable. Summary (but please read the linked thread):```
dpkg --configure -a
```

Please post back here if you have problems with this advice.

unfortunately not. As I mentioned earlier, trying to access the recovery option in GRUB only leaves me staring at a black screen. I'll try again though, just in case.

---

### Post by RememberWhenItRained on 2012-01-11
> **carl4926 said:**
> So you are working with a Live USB?
Yes it's the same as a CD

There is a process where you can chroot to the installed system. But it's kind of complicated. And before I did any more I'd backup files I really needed. Can you do that? You need something to write the files to, that could be an external HD or an internal Partition (Eg; if you have a windows install there) you could create a folder on there and write all your data to it, assuming there is room. The file manager should let you do all this.

Once you have stuff backed up. You can look at the repair or re-install.

If you want to try a chroot to the installed system and try to continue the upgrade, we could have a go. But in any case I'd still recommend a new install, especially after this fiasco

since I'm booted in Windows right now, I suppose I should try and put my /home folder on this partition. I need to copy just the home folder, or every file i'll want to save? I assume with a fresh install of 10.10 all my settings (such as the POP settings in Thunderbird) will be lost? A fresh install would be the safer bet, no? That seemed to be what you were saying.

I'll see if i can work on this tonight after your response. Much thanks!

---

### Post by prshah on 2012-01-11
> **RememberWhenItRained said:**
> trying to access the recovery option in GRUB only leaves me staring at a black screen.

Try to drop to single user mode; at the grub prompt, add the word " single " (note the spaces) before the "--" (or after "quiet" if no "--").

If it still doesn't boot, then probably chroot is the best way to attempt recovery of your system. Boot off a live CD, then open the terminal (Applications-Accessories-Terminal) and give the commands```
sudo mount /dev/sdX0 /mnt # replace sdX0 with the partition that contains your root directory
sudo chroot /mnt

```
At this point (maybe a few seconds later) you should be in your "broken" installation. Try to run the dpkg commands (as mentioned before) in an attempt to repair your broken install.

I would strongly suggest you attempt to get your install back up, rather than a reinstall; however, if nothing else works, then that is all that is left to you.

---

### Post by carl4926 on 2012-01-11
> **RememberWhenItRained said:**
> since I'm booted in Windows right now, I suppose I should try and put my /home folder on this partition. I need to copy just the home folder, or every file i'll want to save? I assume with a fresh install of 10.10 all my settings (such as the POP settings in Thunderbird) will be lost? A fresh install would be the safer bet, no? That seemed to be what you were saying.

I'll see if i can work on this tonight after your response. Much thanks!

You need to work from Linux, something like the Ubuntu CD in Live mode, mount your /home and windows partitions in Nautilus. Create a folder on windows C called something like: **linux-bak**.  Split the view and press Ctrl+H on /home to see hidden files too. Because you might want to copy .mozilla and .thunderbird as well as your documents etc or other hidden folders that have settings etc...
Trying to copy the whole of /home could be too big
It's better to copy just what you need.

A fresh install is always cleaner and better IMO

But notice others here have made some suggestions you might want to consider, in line with some comments I made earlier about using chroot

---

### Post by RememberWhenItRained on 2012-01-12
okay, status update: Left the recovery kernel (if that's the right term) up on the blank screen for about an hour to see if anything would happen. No such luck. Also tried summoning the terminal (Ctrl+Alt+F2 right?) on both the normal and recovery kernels. Also, no such luck.

What's the next step to proceed? If i were to chroot, i would need access to a terminal *in that particular kernel* which i don't seem to have, right? I wondered if i could chroot my linux kernel from my BackTrack 5 i have installed, but that didn't seem to make much sense to me...

So find out where my /home is in and copy that and any other file i want to my OS: (windows partition)? Also booted up in BT5 today and was glad to see that my files were still there..though some of them i did not have permission to access in BT apparently.

So, i seem to have gotten two different responses: try to fix, or chroot, the broken install, or do a fresh install of 10.10. The latter makes me a bit leary, as i don't wish to lose my files and settings (might have to though.) Can i just use my DiskInternals Linux Reader to copy /home and other files (and can i compress the folder in windows to save space?) to win7, and write over the existing partition i had used for 10.04? Since i have 3 OSs, that might be hard to tell which is which.

Also, if i were to chroot, where would i find the terminal to do it? on the liveUSB? Also, i don't have my wireless card driver installed on the liveUSB, so no internet, unfortunately.

Also, can the liveUSB be used to upgrade your existing version, rather than solely a fresh install?

Appreciate your responses. Thanks so much (and thanks for being such a wonderful community.)

---

### Post by carl4926 on 2012-01-13
If /home is separate then when you install, just choose not to format it.
You have to proceed to manage the partitioning manually though.
All your settings and files are preserved. But you will need to re-install all the applications you use.

To chroot, and then try managing the packages from there, would require internet.
Getting internet might just require you dropping the firmware in to /lib/firmware, but that's another subject and we'd need to know what wireless device you have.
Basically you load the live CD and establish which partition is root.
Let's say it's sda1

 Now we need to mount the filesystem to /mnt
  $ sudo mount /dev/sda1 /mnt
      * Now mount the rest of your devices
  $ sudo mount --bind /dev /mnt/dev
      * Now chroot into your system
  $ sudo chroot /mnt

Now from here you can run apt-get as you require (assuming you have internet)

---

### Post by RememberWhenItRained on 2012-01-13
> **carl4926 said:**
> If /home is separate then when you install, just choose not to format it.
You have to proceed to manage the partitioning manually though.
All your settings and files are preserved. But you will need to re-install all the applications you use.

To chroot, and then try managing the packages from there, would require internet.
Getting Internet might just require you dropping the firmware in to /lib/firmware, but that's another subject and we'd need to know what wireless device you have.
Basically you load the live CD and establish which partition is root.
Let's say it's sda1

 Now we need to mount the filesystem to /mnt
  $ sudo mount /dev/sda1 /mnt
      * Now mount the rest of your devices
  $ sudo mount --bind /dev /mnt/dev
      * Now chroot into your system
  $ sudo chroot /mnt

Now from here you can run apt-get as you require (assuming you have internet)
guess who's running 11.10 now?!
 
that's right, this guy!

anyway, that helped a lot. I had to figure most that out with the help of a CS major, linux guru friend since i didn't bother to read the forums late at night.
I think i was making it harder than it had to be - i simply had to mount the partitions to /mnt (which took me a few tries) and use that and GParted to browses and look at sizes to see what was what?

/sda6 was my Linux (which showed up as 10.10 but still didn't boot up), /sda7 was my seperate /home, so that was seperate like we thought, and /sda8 was my backtrack (with showed up as 10.04.2 LTS)

then i just installed 10.10 over /sda6, did not format /sda7

hours and two upgrades later, viola!

i think it's going to take some getting used to but i like it a lot more than i thought i would.


quick question... did they do away with aptitude? i used to use that all the time, now I'm stuck using apt-get.

also, when i try to do su instead of typing sudo after all admin. commands, it gives me authentication failure message, even though it's the same (correct) password I used on sudo commands.

hmm.

thanks guys!

---

### Post by carl4926 on 2012-01-13
I'm not at a Ubuntu machine ATM so can't check but:

su - (is more correct than su )

Good to know you had some success, well done!

---

