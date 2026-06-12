---
title: "help!"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by roly on 2005-03-13
sorry for the general topic title, but i need a lot of help.  newb to linux, but i don't want to give up!

i previously had windows XP installed on my primary hard drive (seagate 80gb IDE), and a friend intruduced me to Ubuntu.  i tried the live CD first to give it a dry run, and everything worked perfectly.  being a conesaur (sp?) of desktop modification and manipulation, i have always wanted to try a linux environment, so i set up a small partition on my primary HDD to install Ubuntu, warty release.  i had ~4.5gb set aside for the install.

upon installing, i was plesently suprised at the sheer simplicity of the process.  my DHCP was not automaticly configured, but i skipped this step thinking that it would be easily set-up later.  after formatting my small partition under the reiserfs file system, the installation completed, and i went ahead and set up a user name etc.

when i first saw the login screen, i was pretty suprised.  it was.. BEAUTIFUL!  i attempted to log in.. this is where my serious string of problems began.  at first, it was just a brown screen.  nothing loaded, nothing popped up.  i rebotted, logged in again, and got a little further.  the ubuntu loading screen came up, but nothign loaded.  my friend suggested that i try to reinstall, so i did.  still no luck.  no error messages or anyhting, just an unresponsive computer screen.

i have actually gotten into the OS about 3 times, but upon attempting to fix my network connection, the system hangs up, crashes, or acts incredibly slow.. the only error message i can recall is as follows:

"Failed to run network-admin as user root: Child terminated with 1 status"

since then, i have reinstalled, reinstalled, and reinstalled again.  i have even plugged more RAM into my system and added another Maxtor 80gb IDE HDD strictly for linux.

here are some of the problems i have encountered:
1. when partitioning the maxtor 80gb drive under ext3, it takes F-O-R-E-V-E-R.. i actually let it run its course once, and it took over 3 and a half hours to completly format/partition. on RARE occasions it zips through, but the system hangs on 100% complete. i let it sit at 100% for 30 minutes once. this doens't seem right.
2. when partitioning the same drive under reiserfs, the system sometimes hangs on 33%, and other times, it hangs at 33%, but quickly moves on with the process.
3. if i actually get through partitioning, i have had the install hang up when attemting to install the kernel. error message reads: "Unable to install the selected Kernel: Linux 386." (note, i have only gotten this error one time.)
4. if the partition works, and the base system gets installed, the extra packages fail to install.  i have been unable to get past this step every time i try to install now. it says somehting about not enough disk space in ./var/usr or something to that effect.. but i have over 70+ gb free.
5. not that i care, but i am unable to boot windows anymore. when i attempt to load winxp from GRUB, i get a blunch of blah.. the last line of which reads "chinloader +1" or something.. then my system hangs.  i have seen that others have this problem as well.

here are the steps i have taken to verify my media:
1. downloaded two copies of warty release from two different websites.
2. used md5sum to verify the packages before burning.
3. verify the data after burning.

i have used 8 CD-Rs in total.. so i am confident in the integraty of my media.

please note that the live CD works great, and i am quickly falling in love with ubuntu  :)

please excuse my terrible grammar and spelling.

thanks for any help.. i dont' want to give up!

---

### Post by alastair on 2005-03-13
Well, something's badly wrong. I would try and get in and get a copy, after boot, of :

/var/log/syslog

Then have a look through this file and see what happens at boot up - see if there are any errors or warnings.

Alternatively, and this is not great help, I would be tempted to skip Warty and go straight to the Hoart preview install. See if this helps. But ... there does appear something wrong with the system so ... logs might help diagnose.

---

### Post by roly on 2005-03-13
thanks for the reply.. how would i go about getting to this file? would it be sufficient to check it out while using the warty live cd?

---

### Post by Buffalo Soldier on 2005-03-13
roly,

I wish all newbies are calm and organised as you are. It's nice to see you put the effort in describing your problems.

From what you have told us you have used the computer to run Windows XP before, and that usually mean you already have enough processing power and memory. But just to be safe, mind telling what processor are you using and how many memory do you have?

As for getting the */var/log/syslog* file, I think there's no problem booting using Warty LiveCD to get that it.

---

### Post by roly on 2005-03-13
hi buff, thanks for your input

my processor is a p4 1.7, with 1gb of PC133 RAM.

there's a new development too.  now, when i turn my PC on, i get nothing.  it "turns on" (checks memory for errors, detects IDE drives) then nothing.  it won't even attempt to boot.  someone in the #ubuntu irc channel is telling me it's a hardware problem.. 

i'm afraid my mobo is gone.. any ideas??

---

### Post by Buffalo Soldier on 2005-03-13
Your processer and memory are more than enough I think. 

I can only guess and it's a long shot... How old is your motherboard and when was the last time you upgraded the BIOS. Because I think I've read somewhere that old BIOS and Ubuntu don't go too well together.

---

### Post by alastair on 2005-03-13
I think it would be best to try and get the syslog file from the system when it it giving problems. Although the "liveCD" version would be good to see as well.

---

### Post by matthieufecteau on 2005-05-03
The solution to your problem could be a little late ...

I think the solution of your problem is in the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback) 

Try and see ...

---

