---
title: "How many users have dual boot unavailable after upgrading to Lucid?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by adm1968 on 2010-05-02
[FONT="Georgia"]I am seeing threads on this issue all over the place: different users, with different versions of Windows on different setups, all sharing the same problem:

Dual boot was OK with earlier versions of Ubuntu
Dual boot is unavailable after upgrading to Lucid

Is it just chance?
Are we all doing something wrong without noticing?[/FONT]

---

### Post by adm1968 on 2010-05-02
[FONT="Georgia"][SIZE="2"]I have kept reading (and trying out) different methods here and there, still no success ...[/SIZE][/FONT]

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/newreply.php

Tried this?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Dmitri on 2010-05-02
Did you try this?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

edit: beaten by nitstorm to it

---

### Post by adm1968 on 2010-05-02
[FONT="Georgia"][SIZE="2"]Yes, I have, thanks :P

Didn't work, though

In any case, **why should the SAME Windows configuration work under 7.04 through 9.10 Ubuntu releases, and then stop working under Lucid?**

That is indeed my question  [/SIZE][/FONT]

---

### Post by mtdave on 2010-05-02
I have this problem, my dual boot worked great under 9.10 with XP dual boot. Now I can't boot XP. No solution yet. I think we need a sticky thread on this so we can get some solutions.

---

### Post by jbarntt on 2010-05-02
I dual booted Ubuntu 9.10 & Windows XP. I upgraded to Ubuntu 10.4, and now can't boot into Ubuntu, but I can boot into XP

---

### Post by necromonger on 2010-05-02
can't see vista at all now!

---

### Post by kamikazepsi on 2010-05-02
my dual boot still works w/ vista but the menu titles are wrong.  

booting into vista leads to the recovery mode, and booting into the recovery mode leads to the normal vista.

weird

---

### Post by NILP on 2010-05-02
I was running xp and 9.04, I'm new to linux, got both working ok in January, read that in order to upgrade to 10 I should first run all the updates for 9, did that, upgraded, 10 worked great, but selecting XP (in the Grub mgr)- only gives a blinking cursor in the upper left. downloaded testdisk but didn't see where I could run it (maybe it runs from a text screen somehow), ran my XP cd, did not give me an option "R" where I could get to fixmbr, only the install - which it did, now it boots with 2 selections of XP, thank God one of them is my old XP with all files and software intact, the other is a new install. But now there is no Ubuntu option. What next to get back to dual boot so I can learn Ubuntu? Can I edit the boot ini in Windows to point to the other partition with Ubuntu on it? And what do I enter, does Ubuntu/grub need special text in there?

---

### Post by paynek716 on 2010-05-02
> **adm1968 said:**
> [FONT="Georgia"][SIZE="2"]In any case, **why should the SAME Windows configuration work under 7.04 through 9.10 Ubuntu releases, and then stop working under Lucid?**

That is indeed my question  [/SIZE][/FONT]

How did you install Lucid? Was it an update or fresh install? I currently dual boot Karmic and Vista. Don't want to update to Lucid if dual boot is a problem.

---

### Post by kansasnoob on 2010-05-02
In answer to your question, lots and lots of folks:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765)

They pushed out the final release while I was still testing :(

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765/comments/96](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765/comments/96)

I saw no need to continue testing once the final was released. IMHO somewhat sloppy last minute work so they could get on to doing what's needed for UDS.

---

### Post by poo_22 on 2010-05-02
one plus. i had 9.10 with windows 7 on the same hdd installed. life was good. then came theupgrade and windows7 doesn't boot. doesn't even get to the booting screen, just the cursor in the corner blinks a bit then it goes back to grub2... my windows partition was intact, and i tried using the windows dvd and doing > fix my computer > startup which said there's nothing wrong.

appart from dualbooting i now don't have any hardware acceleration for opengl so compiz and anything anything else using GLX is broken :x

this is the most brutal upgrade we've had i think. also if you solve the issue at hand post it in this thread, or link to the solution!

---

### Post by adm1968 on 2010-05-03
> **paynek716 said:**
> How did you install Lucid? Was it an update or fresh install? I currently dual boot Karmic and Vista. Don't want to update to Lucid if dual boot is a problem.

[FONT="Georgia"][SIZE="2"]I installed Lucid using the Live CD, leaving the "/home" partition untouched from Karmic
I have been doing that since Dapper all the way up to Jaunty, without a glitch, with dual booting ALWAYS available.

I think it would be appropriate for you NOT to update/install Lucid until a solution is published that fixes this problem for _everybody_[/SIZE][/FONT]

---

### Post by NILP on 2010-05-03
Since I have XP booting again as the first option (Ubuntu 10 doesn't boot at all since the update from 9) I would like to dual boot again, only continue using Windows boot manager and Ubuntu 10 as a second choice. Can anyone tell me how to do that?

---

### Post by adm1968 on 2010-05-04
[FONT="Georgia"]up[/FONT]

---

### Post by timosha on 2010-05-04
I don't have dual boot available after upgrading, but triple boot :

1) Windows 7
2) Ubuntu 10.04
3) Debian 6.0

---

### Post by dnguyen1963 on 2010-05-04
I used Gpart to clear out 8.10 then installed 10.04 to the largest available space on the hardisk.  Dual-boot is successful for 10.04 and XP.  I did not try this approach with my other computer that has Vista and 8.10.

---

### Post by necromonger on 2010-05-04
can not boot xp.

---

### Post by Maddin2010 on 2010-05-04
I have the same Problem.
Bootlaoder starts I can see Ubuntu, recovery Ubuntu, mem test, Windows Vista recovery
and thats it. Vista is gone
in Ubuntu, the Windows Vista partition is mounted automatically and I can browse through the files.
any Idea what I can do ?

Edit:
Tried to boot the recovery and vista was booting :)
Well this problem is done for me now... Would be great if I can change the name from the boot entry and if I had another boot entry for a windows vista recovery...

---

### Post by MurphysServant on 2010-05-04
> **NILP said:**
> I was running xp and 9.04, I'm new to linux, got both working ok in January, read that in order to upgrade to 10 I should first run all the updates for 9, did that, upgraded, 10 worked great, but selecting XP (in the Grub mgr)- only gives a blinking cursor in the upper left. downloaded testdisk but didn't see where I could run it (maybe it runs from a text screen somehow), ran my XP cd, did not give me an option "R" where I could get to fixmbr, only the install - which it did, now it boots with 2 selections of XP, thank God one of them is my old XP with all files and software intact, the other is a new install. But now there is no Ubuntu option. What next to get back to dual boot so I can learn Ubuntu? Can I edit the boot ini in Windows to point to the other partition with Ubuntu on it? And what do I enter, does Ubuntu/grub need special text in there?

Hi NILP,

your story sounds soooo familiar:
[http://ubuntuforums.org/showthread.php?t=1472140&highlight=vancouver+kansas&page=1](http://ubuntuforums.org/showthread.php?t=1472140&highlight=vancouver+kansas&page=1)

---

### Post by adm1968 on 2010-05-05
[FONT="Georgia"][SIZE="2"]Well, AT LAST!
I kwpt searching and found these instructions:
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

This is EXACTLY what I did:

1 Start laptop with Win 7 DVD
2 Press a key to start from DVD
3 Select language and keyboard; press "Next"
4 Select "Repair your computer" option (bottom left)
5 Select the "Use recovery tools that can help fix starting problems Windows" option in the "System Recovery Options" screen
6 Press "Next"
7 Select "Startup Repair" (option 1)
8 Click on "View diagnostic and repair details" (option 1)
9 Check that all tests ran successfully
10 Click on "Close"
11 Click on "View advanced options for system recovery and start"
12 Select "Command Prompt" (last option)
13 At the command line interface, type:
whatever> **bootsect /nt60 C:**
14 Close command line interface
15 Restart

Voilà! ):P

Enjoy
[/SIZE][/FONT]

---

### Post by todd1049 on 2010-05-06
Of the folks who have had problems moving to 10.04 and having their dual-boots messed up -- how many did clean installs, and how many just upgraded their ubuntu systems without wiping out the partition?  I am still using 8.04 and could do either.

---

### Post by peterpan7191 on 2010-05-06
grub messed up badly...
my dual boot is lacking windows completely though i find an entry in /boot/grub/grub.cfg/ ???


here's my grub.cfg
### BEGIN /usr/local/etc/grub.d/10_linux ###
menuentry "GNU/Linux, Linux 2.6.32-21-generic" {
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set b0b25a24-f912-4906-8862-be1359d89396
        linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=b0b25a24-f912-4906-8862-be1359d89396 ro  
        initrd  /boot/initrd.img-2.6.32-21-generic
}
menuentry "GNU/Linux, Linux 2.6.32-21-generic (recovery mode)" {
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set b0b25a24-f912-4906-8862-be1359d89396
        linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=b0b25a24-f912-4906-8862-be1359d89396 ro single 
        initrd  /boot/initrd.img-2.6.32-21-generic
}
menuentry "GNU/Linux, Linux 2.6.31-21-generic" {
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set b0b25a24-f912-4906-8862-be1359d89396
        linux   /boot/vmlinuz-2.6.31-21-generic root=UUID=b0b25a24-f912-4906-8862-be1359d89396 ro  
        initrd  /boot/initrd.img-2.6.31-21-generic
}
menuentry "GNU/Linux, Linux 2.6.31-21-generic (recovery mode)" {
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set b0b25a24-f912-4906-8862-be1359d89396
        linux   /boot/vmlinuz-2.6.31-21-generic root=UUID=b0b25a24-f912-4906-8862-be1359d89396 ro single 
        initrd  /boot/initrd.img-2.6.31-21-generic
}
### END /usr/local/etc/grub.d/10_linux ###

### BEGIN /usr/local/etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 0c966e76966e6066
        drivemap -s (hd0) $root
        chainloader +1
}
### END /usr/local/etc/grub.d/30_os-prober ###

pls help .....

---

### Post by unix1adm on 2010-05-06
I must have gotten lucky on this. I did a update from 9.4 to 10 Ubuntu last night 5/5 and my dual boot worked. I was afraid it would not work after reading all these posts about a bad install. My update from ubuntu 8 to 9 was horrible at best. 

But my winxp booted fine and my 10 boots fine (at this time) 

I have other minor issues that I worked out and still have one outstanding one. a topic for another thread. 

But my dual boots are OK.

---

### Post by robertcoulson on 2010-05-06
Ya...When I upgraded to 10.04, I could not boot XP, but a gentleman named BCBC had a fix...It worked perfectly...But still had quirks with 10.04, so I used Gparted to clear a big free space and did a fresh install..Everything works great now.
Robert

---

### Post by mhenriday on 2010-05-07
See [**_Launchpad bug #571893_**]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893"). The [**_Sourceforge testdisk procedure_**]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") mentioned there should quickly resolve the problem for most multi-boot users, but it is rather disappointing that the **Ubuntu** developers have not yet crunched this annoying bug....

Henri

---

### Post by mrsray on 2010-05-08
> **todd1049 said:**
> Of the folks who have had problems moving to 10.04 and having their dual-boots messed up -- how many did clean installs, and how many just upgraded their ubuntu systems without wiping out the partition?  I am still using 8.04 and could do either.

I upgraded without wiping the partition ... tying to fix the dual boot now when I came across this thread

thanks mhenriday ... the Sourceforge testdisk procedure worked perfectly.  Now I'm off to fix all my hdmi issues  :)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

the Sourceforge testdisk Solution

You can repair the boot sector of Windows system partition via "fixboot" from a Windows XP CD, or "bootrect /fixboot" from a Windows Vista/7 CD. But in my experience testdisk works best in this situation. So boot into a Linux OS or Live CD. If your system uses "apt-get" and has "testdisk" in its repositories (in Ubuntu: the universe repository needs to be enabled), you can install and run testdisk via
   sudo apt-get install testdisk
   sudo testdisk
or you can download the tar.bz2 file of the newest version from testdisk to your desktop and install and run it via
  cd ~/Desktop
  tar -xvf testdisk-*linux*.tar.bz2 
  sudo testdisk-*/linux/testdisk_static

In either case:
  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm
 

did work for me.

---

### Post by pemadorje on 2010-05-08
I experienced this problem while doing a fresh install of Lucid. Was dual booting Vista and Linux Mint. Simply did a fresh install over the Mint partition and thought everything would be cool. Vista appears in the grub menu but when selected, the cursor just blinks and nothing happens. Looking forward to trying the testdisk procedure shortly.

---

### Post by kansasnoob on 2010-05-08
I also filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Slightly different flavor:

**Ubuntu grub2 dist-upgrades result in confusion**

> Binary package hint: grub-pc

This is a horrible way to file a bug report and I'm aware of that, but this needs to be considered.

Throughout various upgrade and/or update procedures in Ubuntu and it's variants the user gets a display asking where to install grub(2). There is a suggestion that if in doubt to install to the mbr of all drives.

Unfortunately most new (and some old) users have no idea how drives/partitions are designated in Ubuntu, and they're clueless as to what an mbr is!

So basically you see a screen that says, "if in doubt select all", and you do so. Now, I'm aware those are not the exact words but I've been following (and trying to help folks fix) these problems since Lucid was released.

It's particularly troublesome when someone installs grub2 to an NTFS partition with a Win OS so I'd at least suggest making grub installation to an NTFS (or any FAT) partition very difficult.

Honestly I'm not sure what the solution should be, but I know Colin Watson deals with a lot of these grub2 issues and I've come to trust his judgment. Consider the following options:

#1: Display nothing but drives, that is "sda", "sdb", etc, and NO individual partitions. But create another "advanced" tab/option to allow installation to a partition.

#2: Increase the amount of text explaining the difference between drives and partitions, why it's a bad idea to install to a partition etc. IMHO that's a horrible option. (The more text the less likely a new user is to read it.)

#3: Figure out a way to always have grub(2) install itself where it was to begin with. (maybe a bad idea if the original install was wrong.)

While I think option #1 is great I have no idea how complicated that would be.

Does any of that make sense?

I'd be glad to test any potential "fixes" :^)

I will mention here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893)

and vice/versa that they're likely duplicates.

---

### Post by pemadorje on 2010-05-08
Maddin2010. Thank you. Your post solved my problem. It was actually a pretty simple problem and I wish I had caught it earlier. 

It was simply that the grub menu items were mislabeled somehow during the installation. 

Instead of showing:
/dev/sda1 - Windows Vista 
/dev/sda2 - Windows Recovery Environment

It was showing:
/dev/sda1 - Windows Recovery Environment
/dev/sda2 - Windows Vista

Switched the names around (by editing grub.cfg even though I know you're not supposed to edit this)... And all is well now.

---

### Post by peterpan7191 on 2010-05-09
> **mrsray said:**
> 
   sudo testdisk

In either case:
  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  [B]Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"[/B]
  Seventh screen:  type "Y" to confirm
 

did work for me.



can you please help me out at fifth and sixth screens it is showing the message
```

Boot sector
Status: OK

Backup boot sector
Status: OK

_**Sectors are identical.**_

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
```now if i force it to dump at the fifth screen gives me no option but quit dumping


PS - i already see my windows partition in my grub.cfg file but it is not getting shown during boot time in the grub menu.

---

### Post by SiouxerBrewer on 2010-05-10
Has anybody figured out a solution for XP users?

---

### Post by cosaki on 2010-05-11
I am having the same problem on Windows 7.  Grub Legacy actually worked perfectly to dual-boot 10.04 and Windows 7.  After Grub2 was installed, Grub went into some kind of test mode that told me to make sure everything booted properly before finishing the upgrade.  The only problem I had there was that I would need to select my OS twice.  After the first Grub menu (no matter what OS I chose) it would go to a second Grub menu, but this time there was no message that told me how to finish the upgrade.  I thought that was how it was supposed to work, so I upgraded the rest of the way.  Now my boot menu shows Windows 7 (loader), Windows Vista (loader) and the various Ubuntu kernels.  I did an upgrade from Vista to 7 last year, and I haven't seen the Vista option since then.  Now Ubuntu loads (but it takes much longer than it used to), and Windows 7 just takes me to the blinking cursor in the upper left-hand side.  Sometimes that screen will stay there, and other times it will automatically reboot after a few seconds. 

I've tried everything I could find on the various forums, but I am a complete noob in Linux.  I know Windows 7 is still in there, because when I'm in Ubuntu I can see the files and such when I navigate to it.  I can even see everything on my Windows desktop still.  Any help would be greatly appreciated!

---

### Post by oldfred on 2010-05-11
cosaki - This thread says solved so most that look at it will be looking for solutions that worked. If the solutions here have not worked like the testdisk. post this in a new thread:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by kansasnoob on 2010-05-11
Just repeating the obvious:

The devs seldom read the forums!

Without continuing comments at Launchpad this will never get fixed:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Comment, comment, comment! But very politely!

---

### Post by SiouxerBrewer on 2010-05-12
It turns out for me it was an MSI issue because of my hard drive configuration.  Not only did I have to include root=/dev/sdb1 but I also had to add "psi=nomsi" after quite splash.  Now I'm able to dual boot without any problems.  I don't think this is related to this problem though.

---

