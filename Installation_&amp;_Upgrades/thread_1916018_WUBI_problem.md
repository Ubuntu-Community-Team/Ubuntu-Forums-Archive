---
title: "WUBI problem"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by holytree on 2012-01-27
Hello all~! I had a wubi install of 10.10 and then upgraded to 11.04 and it went without a hitch.

Then When I upgraded to 11.10 it worked good for a while then it stopped working.

Since then ive tried 20-30 times (no exaggeration) to install but all that happens is after the installation and reboot option 
the _ line blinks for 3 seconds then the computer restarts please help!!!!!!

Sincerely
Holytree

---

### Post by Paddy Landau on 2012-01-27
Hello Holytree

Sorry for your problems.

Unfortunately, WUBI is unstable, especially when it comes to upgrades. It is also extremely difficult to resurrect once it has gone wrong.

I hope you have backups, because I don't think we will be able to get your WUBI working again.

I suggest you uninstall WUBI and reboot to ensure that Windows is still OK. If you can't do that, post back here.

Finally, it would be a better idea, if you wish to use Ubuntu long-term, to install it natively. (It will be a bit like WUBI, where you get to choose between Windows and Ubuntu, but it will be more stable and much easier to fix should it go wrong.)

---

### Post by holytree on 2012-01-28
You see my parents wouldnt allow the partition process as my windows xp is very important..windows is fine..do you think i may be able to install 11.04 then upgrade it??

---

### Post by Paddy Landau on 2012-01-28
Ah, if you are not permitted to change the partitions, then you have a three options.

[LIST=1]
[*]Use WUBI.
[*]Use a flash drive (at least 8Gb, formatted to FAT32), and install Ubuntu on it (with *persistence*; the instructions should be on [the download page]("http://www.ubuntu.com/download/ubuntu/download")). It won't be as fast as a hard-drive installation, obviously, but it still works.
[*]Use an external USB hard drive and install Ubuntu on it. It is nearly as fast as an internal hard drive.
[/LIST]
Whichever you choose, bear in mind that a clean installation is usually far less error-prone than an upgrade. So, install 11.10 (that's the latest). When 12.04 comes out, ensure that you have backups of your work, then install 12.04 rather than upgrading.

If you choose option 2: You may want to install [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") instead of Ubuntu, because Lubuntu will load faster. It's not as pretty, but it's fast.

If you choose option 2 or option 3: When the installer asks you where to place the bootloader, be sure *not* to choose the internal drive but to choose the USB drive instead.

The advantages of options 2 and 3 are:

[LIST]
[*]You change nothing on your parents' hard drive.
[*]Your solution is portable, so you can take your USB disk with you and boot on a different computer.
[/LIST]
Option 3 has yet another advantage. You can use the functions of a hard drive, including a dedicated swap space, and separating your root (/) and home (/home) folders.

I would recommend option 3 if you can afford the hard drive, otherwise option 1 or 2 depending on your personal preferences.

If you choose option 2 or 3 and have difficulty, post a new thread (and post a link to the thread here so that we can find it).

---

### Post by bcbc on 2012-01-28
What computer brand/model is it? It's pretty strange to have it just reboot. So if you install 11.04 it works, but 11.10 - it reboots? Or haven't you tried 11.04 since.

How are you installing - just running wubi.exe standalone? 
If so, you could try downloading the desktop CD ISO (from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) ) and saving it in the same directory as wubi.exe before running. It works slightly differently (only on 11.10). See if that makes a difference.

---

### Post by ottosykora on 2012-01-29
>What computer brand/model is it?<

very important question in this particular case.

I had exactly this on one install some time ago. Old hardware, was able to run only with acpi=off and  noapic as far as I remember.
In one case, on old compaq desktop, I never found a solution, it simply crashed and rebooted when system tried to config drivers or so.

---

### Post by holytree on 2012-01-29
Hello All My problem got solved i installed 11.04 then upgraded to 11.10 fine for now..

Thanks For all your help 
and @bcbc- if i use wubi from the live cd then would it require internet like the wubi.exe file does?

---

### Post by holytree on 2012-01-29
> **Paddy Landau said:**
> Ah, if you are not permitted to change the partitions, then you have a three options.

[LIST=1]
[*]Use WUBI.
[*]Use a flash drive (at least 8Gb, formatted to FAT32), and install Ubuntu on it (with *persistence*; the instructions should be on [the download page]("http://www.ubuntu.com/download/ubuntu/download")). It won't be as fast as a hard-drive installation, obviously, but it still works.
[*]Use an external USB hard drive and install Ubuntu on it. It is nearly as fast as an internal hard drive.
[/LIST]
Whichever you choose, bear in mind that a clean installation is usually far less error-prone than an upgrade. So, install 11.10 (that's the latest). When 12.04 comes out, ensure that you have backups of your work, then install 12.04 rather than upgrading.

If you choose option 2: You may want to install [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") instead of Ubuntu, because Lubuntu will load faster. It's not as pretty, but it's fast.

If you choose option 2 or option 3: When the installer asks you where to place the bootloader, be sure *not* to choose the internal drive but to choose the USB drive instead.

The advantages of options 2 and 3 are:

[LIST]
[*]You change nothing on your parents' hard drive.
[*]Your solution is portable, so you can take your USB disk with you and boot on a different computer.
[/LIST]
Option 3 has yet another advantage. You can use the functions of a hard drive, including a dedicated swap space, and separating your root (/) and home (/home) folders.

I would recommend option 3 if you can afford the hard drive, otherwise option 1 or 2 depending on your personal preferences.

If you choose option 2 or 3 and have difficulty, post a new thread (and post a link to the thread here so that we can find it).

I have a 1 tb hard drive and suppose i used 250 gb of it how can i increase the size??

---

### Post by Paddy Landau on 2012-01-29
> **holytree said:**
> My problem got solved i installed 11.04 then upgraded to 11.10 fine for now..
Excellent! Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

> **holytree said:**
> I have a 1 tb hard drive and suppose i used 250 gb of it how can i increase the size??
I don't know how to increase the size when using WUBI.

However, if you do a native installation, it is easy to change the size. Boot from a Live CD (or USB), and use [GParted]("http://gparted.sourceforge.net/") (it's on the Live CD) to modify the partitions.

250Gb is huge. Ubuntu takes about 5Gb, so unless you are storing massive amounts of data, you won't need to increase its size. If you are storing such massive amounts of data, think about how you will back it up (what happens if you drop your hard drive?).

Another thing to note is that Ubuntu will easily see Windows partitions (NTFS), but Windows cannot see Ubuntu partitions (ext4). If you need to store data that both Windows and Linux can see, create a separate partition, format it as NTFS, and save the shared data there. (Your hard drive is probably already formatted as NTFS.)

---

### Post by bcbc on 2012-01-29
> **holytree said:**
> Hello All My problem got solved i installed 11.04 then upgraded to 11.10 fine for now..

Thanks For all your help 
and @bcbc- if i use wubi from the live cd then would it require internet like the wubi.exe file does?

Great. That's a bit of work (upgrading) but glad things are working. In answer to your question, you don't need the internet when installing wubi from the live CD but it's better to be connected - because wubi.exe will download the md5sum and check the ISO before installing.

PS if you installed on a 250GB partition you could resize it, but there's no real need to make your partition that big. It'd be better to have a separate partition for /home (or just for large multimedia files) if you think you'll have that much data. If you'll be accessing the data in both Windows and Ubuntu, then you'd probably do better with a shared NTFS partition just for data.

---

