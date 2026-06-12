---
title: "Anomalies after replacing 11.04 with 10.04"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by Futurian on 2012-08-03
I just reinstalled Ubuntu 10.04: "Places" no longer works correctly, and theme updating now has some failures it used to not have.

Places > Home Folder results in the following error message at the top of a new window: 

"/home/paul is a directory.
Please check that you typed the location correctly and try again" (without the quotes)
I get similar results for Places > Desktop through Places > Ubuntu One.

But Places > Computer works. Double-clicking File System from there leads correctly to /home which leads correctly to /home/paul, and so on from there.

Just before this started happening: I replaced my Ubuntu 11.04 installation with an Ubuntu 10.04 installation. My system (a System76 Pangolin Performance panp5) has separate root and home partitions. /etc/fstab has as its last line:

/dev/sda6 /home ext3 nodev,nosuid 0 2

I did the replacement by creating an Ubuntu 10.04 startup usb flash drive, booting from it, deleting the hard drive partition (/dev/sda1), and then installing 10.04 into the disk space freed up by the deletion.

Another anomaly that began at the same time is that when I go to Appearance Preferences > Themes > Get More Themes Online > Window -Borders > Download (for Clearlooks2-Squared-Berries) and select "Theme Installer (default)", I get:

"Installation for theme 'Clearlooks2-Squared-Berries' failed.
Can't move directory over directory."
Yet I was able switch to Clearlooks theme without issues.

I have made similar replacements (e.g. 11.04 or 11.10 with 10.04) recently, and without a glitch. Those installations, however, do not have separate home partitions.

I'm mystified. Any help would be appreciated.

---

### Post by darkod on 2012-08-03
Did you tell it to use the existing /home partition during the installation or you tried to switch to it later?

In my fstab the /home partition is mounted with only the 'defaults' option, not with 'nodev,nosuid'.

---

### Post by Futurian on 2012-08-03
Darkod,

I tried to switch to it later.

Don't know how to do it during installation.

Thanks for looking at this.

---

### Post by Futurian on 2012-08-03
Following darkod's suggestion, I changed the last line of my fstab to

/dev/sda6 /home ext3 defaults 0 2

, rebooted, but still have the same problem.

---

### Post by darkod on 2012-08-03
You need to use the manual install option when you have an existing /home partition.

You can switch to separate /home later but people usually switch to empty partition copying first all the data the install put in /home/username. Only after that you add it to fstab.

Obviously, if you want to keep the data in the /home partition you can't wipe it clean and copy the content of /home/paul.

I would say the behavior  you are seeing is because you didn't reuse the /home partition during install but I don't know what's best to do now. Not unless you are willing to wipe sda6 and copy the install made /home/paul to it.

Try changing the option of sda6 to 'defaults' but I doubt only that will sort anything out.

---

### Post by Futurian on 2012-08-03
Thanks, darkod, I'll give the manual install a try.

---

### Post by Futurian on 2012-08-03
I tried doing a manual reinstall, keeping the existing home partition. It didn't work; I have exactly the same symptoms (Places > Home, etc. doesn't work). 
Maybe I'll try copying all my home data to a backup, create a separate empty home partition, and then copy my home data back in.
But if I have to do that, what is the advantage of a separate home partition? I don't see any saving.

---

### Post by darkod on 2012-08-04
> **Futurian said:**
> I tried doing a manual reinstall, keeping the existing home partition. It didn't work; I have exactly the same symptoms (Places > Home, etc. doesn't work). 
Maybe I'll try copying all my home data to a backup, create a separate empty home partition, and then copy my home data back in.
But if I have to do that, what is the advantage of a separate home partition? I don't see any saving.

If everything is OK with your /home partition, it does work. But I have no idea in what state the partition is in, depending what you did earlier.
I am using separate /home partition and never had any problems, but I always tell the installer to use it during the install, not later.

Since it seems your /home partition has some corruption, I would suggest:
Copy only your personal data like documents, music, videos, etc, but not program settings which are also in the partition. Because you don't know where the problem is, don't copy all of it. Just your personal, important data.

Install the latest 12.04 LTS using the manual method, and use separate /home partition (you can use the same but format it to delete all old data). After the install is done, copy your personal data back into the new installation.

From there on, you can do clean installs and use that partition as /home with the same filesystem, only DO NOT format it in future installs because you want to keep the data.

I don't know why are you trying 10.04 LTS, is there any reason for this? Did you give the latest 12.04 LTS a go?

EDIT PS: Also when we are talking about reusing the /home partition I hope we understand each other. It's not enough simply to use the manual install and set up the root and swap partitions. You have to tell the installer that you want sda6 to be used as /home partition, otherwise it is not used by default. Linux doesn't make guesses about your system, you have to tell it what is what.

---

### Post by Futurian on 2012-08-05
darkod, thanks for your valuable help. This problem is now SOLVED.

Before I read your most recent post, I tried again, using my existing home partition, and telling the installer to use that partition as my home partition. Result: same problems as before, Places > Home didn't work, etc. I think this confirms your statement regarding my home directory being corrupted.

(The only thing I know of that was done to that home directory after it worked and before it failed was my attempt to reuse it without informing the installer. But there may be another possibility. My "old" home directory was set up for 11.04; it may be that some setting didn't work for 10.04. More about this below.)

Also before I read your last post,I backed up my home directory, reformatted the disk and reinstalled 10.04 . Then I copied all of my old home directory into my new home directory. I did tell the installer to use my new home partition as my home partition.
Again, Places > Home didn't work, confirming the  corrupted home directory hypothesis.

So I tried again (before reading your post), with no separate home partition, and again copying my home backup into my new home directory. Again, Places > Home didn't work.

Then I read your post, reinstalled 10.04 again (no separate home partition), but this time avoided copying application setting files and directories into my new home directory. Now Places > Home works, and I can control window layouts. Thanks!

Why use 10.04 instead of 12.04? I apologize in advance if this turns into a rant.

Reviewing my work for the last year or two, it seems to me that I have spent a lot of time trying out various Linux variations, and coping with the consequences of "issues", such as incompatibilities and desktop changes. I've spent this time partially because it is fun and interesting, and partly because when I made changes I wound up having to resolve issues so that I could use the system to do my work. In 20/20 hindsight, I would have been better off to have taken most of that time, and applied it to my teaching, advising, administration, and research (I'm an academic).

So I decided to move most of my Ubuntu installations (I collect them) to 10.04, which does everything I need, runs reasonably quickly on all of my machines, and is supported until April 2013. I hope to redirect the time I used to spend on "playing with" my systems to doing the work these systems are intended to support.

I do run 12.04 on one machine in a virtual environment (VBox), with the Cinnamon desktop. It has its good points for sure. But:
1. It seems a little slower than older releases, and all my machines are old and slow already.
2. It won't run Amaya, which is useful to me. (I hope a new Amaya release for 12.04 comes out.) 
3. With the Netbeans 7.1.2 IDE, the menu bar is black on black, except when I click on an (invisible) menu item, in which case that item becomes visible. [EDIT: Fixed by installing Ambiance-cruchy grey [http://users.skynet.be/linux-rixensart/1_suite.html#crunchy](http://users.skynet.be/linux-rixensart/1_suite.html#crunchy) .]
4.  12.04 won't run acceptably on my most ancient machine, which I still need.
5.  12.04 won't run Nvidia's CUDA [http://www.nvidia.com/content/cuda/cuda-downloads.html](http://www.nvidia.com/content/cuda/cuda-downloads.html) , which I need for research work.

In this "play" over the last two years or so, for a while I ran 11.04 and 11.10 (from separate partitions, of course), each sharing the same home directory (in its own partition). I had been following this pattern (most recent Ubuntu version, previous Ubuntu version, sharing the same separate home partition) for a while, so that I could try out new Ubuntu versions on my real work. When I reached 11.04 and 11.10, at least one application balked. The problem was not as bad as the one covered in this thread, but that experience makes me wonder if this thread's problem came from taking 11.04 settings and attempting to use them in 10.04.

Again, thanks for your help, darkod! You are a prince or princess, as the case may be!

---

