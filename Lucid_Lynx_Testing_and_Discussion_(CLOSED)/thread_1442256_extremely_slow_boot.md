---
title: "extremely slow boot"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by benderbeerman on 2010-03-29
I upgraded to 10.04 beta from 9.10 as soon as i could using "update-manager -d". the install went fine, rebooted remarkably fast, and ran beautifully. I restarted my system after applying updates, loaded into plymouth, at which point the boot hung with all the little lights on under the plymouth emblem red and not cycling. my hdd access light was on, so i figured i'd restart once the light went out. 20 mins later, the system actually loaded. I didn't like the 20 boot time, and figured it may have been an error in the update, so i downloaded the live cd. again, loaded beautifully, installed fine, restarted quickly, installed updates, rebooted again and again the system hung at plymouth. the drive seems to make a *CLICK,click* sound. I was not having any luck finding anybody else on the forums with these same or similar symptoms, so i assumed maybe it was the cd, so i downloaded the alt install cd with the same exact effect. I have tried loading grub2 without the "quiet" and "splash" options, with the same basic results (hang after boot, but no splash). Funny thing is, no matter how long the boot actually takes, the bootchart shows 180sec. anybody hane any ideas?

---

### Post by Owen.C93 on 2010-03-29
> **benderbeerman said:**
> I upgraded to 10.04 beta from 9.10 as soon as i could using "update-manager -d". the install went fine, rebooted remarkably fast, and ran beautifully. I restarted my system after applying updates, loaded into plymouth, at which point the boot hung with all the little lights on under the plymouth emblem red and not cycling. my hdd access light was on, so i figured i'd restart once the light went out. 20 mins later, the system actually loaded. I didn't like the 20 boot time, and figured it may have been an error in the update, so i downloaded the live cd. again, loaded beautifully, installed fine, restarted quickly, installed updates, rebooted again and again the system hung at plymouth. the drive seems to make a *CLICK,click* sound. I was not having any luck finding anybody else on the forums with these same or similar symptoms, so i assumed maybe it was the cd, so i downloaded the alt install cd with the same exact effect. I have tried loading grub2 without the "quiet" and "splash" options, with the same basic results (hang after boot, but no splash). Funny thing is, no matter how long the boot actually takes, the bootchart shows 180sec. anybody hane any ideas?
It does this everytime you boot? Because the first one ureadahead needs to reprofile and other stuff. Apparently there may be an issue with the -18 kernel. Try the -16 one if you can.

---

### Post by dinamic1 on 2010-03-29
-18 is sooo slooooow

---

### Post by andrewabc on 2010-03-29
install bootchart.
[http://ubuntuforums.org/showthread.php?t=1343305](http://ubuntuforums.org/showthread.php?t=1343305)

Post your bootchart here and in that thread. Upload the image to imageshack. Not the forum.

---

### Post by benderbeerman on 2010-03-29
bootchart: [http://yfrog.com/5jbenderlucid201003291p](http://yfrog.com/5jbenderlucid201003291p)

this boot did not actuall take only 200sec, as stated by the bootchart, but closer to 20 minutes

---

### Post by Ibidem on 2010-03-29
How long does it take on the second boot?

Might it be plymouth?

How quick would a pure text boot be?

---

### Post by benderbeerman on 2010-03-29
> **Ibidem said:**
> How long does it take on the second boot?

Might it be plymouth?

How quick would a pure text boot be?


well, first boot after install screams, less than 20 sec's. each subsequent boot takes significantly longer than that first, about 20 minutes. I don't think it's plymouth because it does the same from the text boot: after all the loading script, it just sits there with a blinking cursor at the top and the drive making a repeating *click* sound

---

### Post by andrewabc on 2010-03-29
What devices you have connected to computer?

Look at bootchart at bottom (6th item from bottom)
jbd2/sda1-8 is using some disk utilization along with some others there.

Maybe something is waiting for something to happen? Unplug some stuff you have connected?

I don't know lots about bootchart I just look for stuff running long time that uses cpu or disk usage.

maybe there is a log somewhere that says what's going on? anyone know? rsyslogd 1/2 way down is running whole time, would that say anything.

one thing to look at is disk througput stops at 18 seconds or so. maybe some process starting around that time is causing problem. no disk throughput but lots of disk utilization is weird. which of course causes high i/o wait

---

### Post by benderbeerman on 2010-03-29
only thing i've got plugged into it (other than my kb/mouse) is my printer

---

### Post by ranch hand on 2010-03-29
Have you tried booting recovery mode?  You get some information that way at least.

You could also try the dpkg option while there.

---

### Post by benderbeerman on 2010-03-29
which dpkg option?

---

### Post by ranch hand on 2010-03-29
There is only one and I can never remember the rest of the name but it looks for broken packages that can be fixed.  It will also run an update but you do have the standard option of not doing that.

If something needs fixed it will do that first then it will try the update/upgrade route.

When finished you should be directed back to the recovery menu.  I go to the normal boot and see what happens.  Amazing how sometimes just booting recovery and doing nothing helps.  Worth a shot in most cases.

---

### Post by benderbeerman on 2010-03-30
here's the bootchart after booting into recovery and running the dpkg repair broken packages option, then rebooting normally. Same deal tho, sat and loaded for 20 minutes and the bootchart only shows 85 sec. 
[http://yfrog.com/9ebenderlucid201003292p](http://yfrog.com/9ebenderlucid201003292p)

i'm gonna try booting into the -16 kernel instead...

---

### Post by ranch hand on 2010-03-30
What happens if you try a terminal login?  Does that go faster?

---

### Post by benderbeerman on 2010-03-30
haven't tried that yet, just tried with kernel -16 for a quick 17 min boot

---

### Post by benderbeerman on 2010-03-30
well, i booted into recovery, then dropped into shell as root and started x and it booted REAL fast as root, no delay at all

---

### Post by k3lt01 on 2010-03-30
[Read this]("http://ubuntuforums.org/showthread.php?t=1434502") and follow keybuk's instructions and post in the bug report. It will probably a mixture of Plymouth, ureadahead, and Bootchart.

---

### Post by jppr on 2010-03-30
yesterday i did fresh daily installation and don´t have any problem with plymouth or ureadahead. system boot and shutdown about 15 sec both 10.04 and win 7. win 7 boot little bit faster than 10.04 maybe 12 sec

---

### Post by benderbeerman on 2010-03-30
submitted bug report on ureadahead, still not all that convinced that's the problem.  :-k

---

### Post by benderbeerman on 2010-03-31
well, i installed the latest updates then rebooted to find that it wouldn't boot at all, so i reloaded into recovery and tried to "boot normally" and it froze with the line "rc-sysinit start/running, process 1122". I rebooted into recovery again and logged in as root just fine tho.

---

### Post by benderbeerman on 2010-04-02
beuller.......................? beuller.....................? frye..........................? beuller.......................?

---

### Post by k3lt01 on 2010-04-02
> **benderbeerman said:**
> beuller.......................? beuller.....................? frye..........................? beuller.......................?What?

This may seem a stupid question but are you trying different things, like removing ureadahead for e.g, and seeing how it boots after you remove something? You really need to do a little detective work.

---

### Post by benderbeerman on 2010-04-03
> **k3lt01 said:**
> What?

This may seem a stupid question but are you trying different things, like removing ureadahead for e.g, and seeing how it boots after you remove something? You really need to do a little detective work.

yes, i've removed ureadahead, and plymouth, installed and removed fglrx, booted into recovery, repaired broken packages, logged in from shell, logged in as root (which works surprisingly well), filed a bug report like stated on the ureadahead sticky posted by keybuck (you wouldn't believe how frustrating it is to have to reboot your computer 3 times in a row at 20+ mins each time), all to no avail... :?:

---

### Post by k3lt01 on 2010-04-03
> **benderbeerman said:**
> (you wouldn't believe how frustrating it is to have to reboot your computer 3 times in a row at 20+ mins each time), all to no avail... :?:Hmmmmm, you obviously haven't used the search function then if you think you need to say that to me. The ureadahead thread by keybuk is because I have had difficulty with it and I have had to wait over an hour more than a few times just to get my laptop to boot to a usable stage. Keybuk is trying to work out the issue and started that thread so that people who used the search function would come across it and let him know what their problem is.

Now we have that out of the way :rolleyes: I'll suggest 3 things.

1. Document what you have done, in order, and the results of each thing. Sorry but what you have just posted doesn't tell me much at all because I don't know what order did it in and what the effects were for each change. Nor do I know if you changed 1 thing at a time or did more than 1 change at a time.
2. If you can't remember what you have done to that degree that you can tell us exactly what effects the different things have you can start doing each thing again and after each one post what happened after a couple of reboots.
3. If your system has changed drastically, enough that your not sure what is supposed to be on it, re-install and start all over again but remember to do each procedure 1 at a time and document what happens.

I am trying to impress upon you the importance of a methodical approach.

---

### Post by benderbeerman on 2010-04-03
late nite, you're right. i'll put up a more detailed list tomorrow.... thanks for the advice

---

### Post by benderbeerman on 2010-04-03
ok k3lt01, here's a detailed synopsis of what i did, the order in which i did them, and their results:

i was running 9.10 until 3-19, no problems. i run an amd phenom 3core on an asus m378-cm with 8gb ram and a radeon hd4800 and a 120gb wd sata. i upgraded my os when beta1 came out using the "update-manager -d" command. install went smoothly thru the initial restart. i updated to the latest packages using "update manager" which required a restart. upon my second reboot i had the problem. it took over 20 mins to boot thru plymouth until i had any type of desktop. i thought maybe the download was unsuccessful because it was an early release or something, so i downloaded the x86_64 live cd from a mirror, wiped the drive for a fresh install, ran thru the entire install smoothly, and restarted with the same exact results. i figured maybe the release i got from the mirror could also have been defective or older so i downloaded the live cd from the ubuntu server and reinstalled with the exact same results. at this point i decided maybe i needed the alt cd, downloaded and installed again with the exact same results. i can usually work out my own problems by browsing thru the forums without much trouble, but not this time... people were having trouble with the video drivers, so i figured i'd try that, i installed fglrx, which didn't exacerbate the problem, but didn't fix it either. it ran ok, but since there was so many other ppl having problems with it, i thought i'd uninstall and remove the video driver from the equation. at this pointi was starting to get frustrated, so i came on the forum and asked for help, which you and ranch hand were happy to provide. i tried the "boot into recovery" method, ran the dpkg repair broken packages command, then rebooted normally with absolutely no change. i booted into recovery again and logged into a shell as root, then started x which booted instantly, no problem. i couldn't believe it. i logged out, to a shell, logged in as user, then started x with the same boot hang of 20 mins again. i figured instead of powering down all the way, i ought to just suspend my system. but when i went to wake it back up and log in, it gave me an active desktop with no pointer. i could use the mouse and highlight objects and click and select, but the actual pointer wasn't there, i had to highlight something before i knew where my mouse was. i thought since i had tried all the other suggestions i had received that i'd follow your suggestion on the ureadahead sticky, so i followed keybuk's instruction to the letter and posted my bootcharts, and haven't heard anything back since then. i have had no other changes. ](*,)

i hope this provides the methodical and insightful type of investigation and reporting that i hadn't been providing earlier. thanks!

---

### Post by ranch hand on 2010-04-03
Wow,  I need to talk to my son.  I talked him into installing 10.04 and he has one of those tri-core boards too.

The alt disk has a "recover a broken system" option doesn't it?  I had to resort to that from the Live DVD for some of my installs that got buggered.  Commands seem to take a bit more "bite" than they do from the terminal in the Live Session on the same disk.

I think that yours is the first tri-core box I have heard mentioned here.  This is great.  Maybe all your troubles (and bug reporting) will help get those boards better supported.  That is, I think quite a bit different hardware than even numbered or single cpus.

---

### Post by benderbeerman on 2010-04-03
[QUOTE=ranch hand;9071893That is, I think quite a bit different hardware than even numbered or single cpus.[/QUOTE]

that is a good point, hadn't even thought of that...

---

### Post by babyhuey on 2010-04-03
I have this same problem though removing "splash" from the kernel boot line is a workaround for me.

---

### Post by k3lt01 on 2010-04-03
This is exactly what I was looking for.

> **benderbeerman said:**
> i booted into recovery again and logged into a shell as root, then started x which booted instantly, no problem. i couldn't believe it. i logged out, to a shell, logged in as user, then started x with the same boot hang of 20 mins again.Ok let's try something new.

Log in as root and when you are in and it is working well create a new test user, e.g. Username "test", login password "test". This will create a totally new set of settings files that will show us if the problem is your current user settings or something else. Now reboot, not as root, and log in to your new test user and see how it goes.

Btw this is assuming that you kept your old Karmic /home and user settings which are kept in /home and are not changed if you didn't format the /home partition. Creating a new user will create new settings that are Lucid compatible. You may need to reboot a few times, ureadahead may reprofile on first boot and be normal on the second boot so give it a couple of goes and see if it gets better. Just remember to only log in to the test user until we have finished this.

P.S. My apology's if I seemed bargy in my previous post.

---

### Post by techunit on 2010-04-04
If you have corrupted media (SD cards) in your machine it will hang indefinately during boot. Learned this the hard way. Try removing everything and then boot again. The most probable problem is with plymouth. Compatibility problems are common with development releases.

---

### Post by ranch hand on 2010-04-04
I just talked to my son and he is using that processor or one with that name anyway.  He is booting, by his watch, not bootchart, in 15 seconds.

Gee, doesn't that make you fell better.

---

### Post by benderbeerman on 2010-04-04
"Gee, doesn't that make you fell better." ya, i'm glad he doesn't have to deal with this too! :)

"Ok let's try something new." thanks k3lt01, i will try that in a few minutes and post the results, thank you for your patience and assistance

---

### Post by benderbeerman on 2010-04-05
ok, that was fun. sorry for the delay, hope everyone had a good easter (if u celebrate that kind of thing)! 

the results are the same with a new "test" user. still a 20 min delay before i can even get to the login screen... then it logs in just fine from there.

---

### Post by ranch hand on 2010-04-06
I sure hope that some one besides us is getting a blow by blow report of this.  Some one in some back room really needs to hear all of this and see if they can duplicate it.

That is the only way this is going to be fixed.  It could be that the root of your problem is responsible for all the erratic behavior of the boot now that it has been so vastly improved over xsplash.

---

### Post by k3lt01 on 2010-04-06
> **benderbeerman said:**
> the results are the same with a new "test" user. still a 20 min delay before i can even get to the login screen... then it logs in just fine from there.So it's not a user profile thing because the issue is before a user profile is selected. I wonder why rebooting as root boots faster though. In other words why is Recovery mode faster than regular bootup?

I agree with Ranch hand, I think this needs to be put on Launchpad as a separate bug report. If you do this make sure you give the step by step account that you did a few posts ago.

It seems to me that there is a conflict somewhere before the gdm. We need to know what files are loaded from the time the PC is started to the time gdm comes on screen. I don't know how to get that information though. I'll do some searching around to see what I can find.

---

### Post by benderbeerman on 2010-04-06
> I agree with Ranch hand, I think this needs to be put on Launchpad as a  separate bug report.
that makes sense, i appreciate the effort you guys are putting into this. if you want any more info please let me know, and i'll get this reported right now!
               
                                                                                           []("https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/556259/+affectsmetoo")[]("https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/556259/+affectsmetoo")
reported as Bug #556259, thanks again! :)

---

### Post by ranch hand on 2010-04-06
Looks like about as good a report as they can expect.  They will send questions if they need more info.

Ought to have some head scratching on that one.

Good job.  You may be in the running for "bug of the release" award.

---

### Post by benderbeerman on 2010-04-06
> **ranch hand said:**
> Good job.  You may be in the running for "bug of the release" award.
 
*hold your applause*
;)

---

### Post by k3lt01 on 2010-04-06
Been thinking about this, yes I know I have to be careful about bushfires from all the internal friction :lolflag:, can you post your bootchart file, and the other files keybuk asked for if they are small enough, as an attachment so we can see what is loading before the GDM?

---

### Post by benderbeerman on 2010-04-06
i'll have to get a boot chart up in the morning, it's half past a monkey's u know what and i ran out of coffee hours ago...

---

### Post by benderbeerman on 2010-04-06
ok, here's the bootchart for this morning: [http://yfrog.com/0lbenderlucid201004061p](http://yfrog.com/0lbenderlucid201004061p)

i was unable to find "ureadahead --dump" file and path don't exist

but it's funny how the bootchart shows the boot only taking 130 secs, when it was actually closer to 1000

---

### Post by Songwind on 2010-04-06
I am having this same issue, benderbeerman.

When attempting to use my system in terminal mode, I got a message about jbc or jdb or something like that.  dmesg had errors in it about journal commits blocking requests.

---

### Post by k3lt01 on 2010-04-06
> **benderbeerman said:**
> ok, here's the bootchart for this morning: [http://yfrog.com/0lbenderlucid201004061p](http://yfrog.com/0lbenderlucid201004061p)

i was unable to find "ureadahead --dump" file and path don't exist

but it's funny how the bootchart shows the boot only taking 130 secs, when it was actually closer to 1000
I eventually got to read your bootchart, I don't know what it was but something in that site just wanted to lock up my little old Acer.

With bootchart, it only shows a certain amount of time even it it isn't finished it will only show the 130 seconds you mention. Anyway that's fine as it is because you seem to have a few processes taking an enormous amount of time to get through their jobs. In order of startup these processes seem to lag.
1. init
2. collector
3. upstart-udev-br
4. udevd
5. rsyslogd
6. dbus-deamon
7. modem-manager
8. wpa_supplicant
9. console-kit-dae

All of these are before the gdm. What I would do now is try to see if there is anything that can be disabled in that list, such as wpa_suplicant, modem-manager, or anything else, and see how it boots after they have been disabled. Make sure if you do this only do one at a time, also note that each time you disable and re-enable ureadahead will probably reprofile and mak the boot process longer than "normal" so you will need to reboot at last twice for each disable and re-enable event.

---

### Post by TrueJournals on 2010-04-07
Just browsed over this thread, and wanted to first note that I also upgraded to Lucid from Karmic, and have had no problems.

Having said that, from what I know about the boot process, etc... It seems to be an issue with some device in your system.  What PCI, USB, FireWire, Memory Card Reader, etc. devices do you have plugged in?  Can you list them specifically with model numbers?  If you get into the system, you can just post the output of lspci -nn and that might provide some clues.

If I had to take a guess, I would say it's either an issue with a wireless card (if you have one), or a disk drive (this could be your harddrive or an SD card plugged into a memory card reader).  How is your harddrive partitioned?  Do you just have ext4 for Lucid and Swap?  Or do you have other partitions on the harddrive also?

[edit] Looking over things again, and reading Songbird's post again, I looked up JBD, and it appears to have to do with journaling on the ext3/ext4 filesystem.  Are you using ext3 or ext4?  When you did the clean install from the CD, did you reformat, or just overwrite files?

---

### Post by ranch hand on 2010-04-07
> **TrueJournals said:**
> Just browsed over this thread, and wanted to first note that I also upgraded to Lucid from Karmic, and have had no problems.

Having said that, from what I know about the boot process, etc... It seems to be an issue with some device in your system.  What PCI, USB, FireWire, Memory Card Reader, etc. devices do you have plugged in?  Can you list them specifically with model numbers?  If you get into the system, you can just post the output of lspci -nn and that might provide some clues.

If I had to take a guess, I would say it's either an issue with a wireless card (if you have one), or a disk drive (this could be your harddrive or an SD card plugged into a memory card reader).  How is your harddrive partitioned?  Do you just have ext4 for Lucid and Swap?  Or do you have other partitions on the harddrive also?

[edit] Looking over things again, and reading Songbird's post again, I looked up JBD, and it appears to have to do with journaling on the ext3/ext4 filesystem.  Are you using ext3 or ext4?  When you did the clean install from the CD, did you reformat, or just overwrite files?
These are good questions.

I doubt that the ext3/ext4 deal has to do with this.  I use ext4 but have upgraded hardy to Lucid which of coarse gives you ext3 and had no noticable difference in speed.

But, this is a bugger of a problem and we should think about all these things.

I have wondered what the result of renaming /etc/init/plymouth.conf to /etc/init/plymouth.conf.OLD would be.  I have a tendency, recently, to assume that boot problems are all caused by plymouth.  Even I realize this can't be true but it sure fells that way.

---

### Post by margazhang on 2010-04-07
I have the same problem trying to help a friend switching from Windows to Ubuntu - it is a Toshiba Harman/Kardon laptop. Well, I should not have installed the Beta 1 in the first place - got to wait for the stable release. Having to go back to Ubuntu 9.10 :-(

---

### Post by benderbeerman on 2010-04-07
Not too sure that it's any pci device or memory card reader as the only thing i have had plugged in was my printer (which i also unplugged), and my dvd drive (sata). other than that, my drive is a 120 gb sata using ext4 with a complete reformat and install on a primary partition (sda1) with swap (ext5). sorry i didn't get back to you last night, karaoke was calling my name :guitar:...

---

### Post by Owen.C93 on 2010-04-07
> **benderbeerman said:**
> Not too sure that it's any pci device or memory card reader as the only thing i have had plugged in was my printer (which i also unplugged), and my dvd drive (sata). other than that, my drive is a 120 gb sata using ext4 with a complete reformat and install on a primary partition (sda1) with swap (ext5). sorry i didn't get back to you last night, karaoke was calling my name :guitar:...
Could you post the contents of your /boot/grub/grub please?

---

### Post by k3lt01 on 2010-04-07
> **Owen.C93 said:**
> Could you post the contents of your /boot/grub/grub please? I think Owen means your /boot/grub/grub.cfg file.

---

### Post by Owen.C93 on 2010-04-07
> **k3lt01 said:**
> I think Owen means your /boot/grub/grub.cfg file.
No, but if you think that's a good idea then yeah that will do :)

---

### Post by k3lt01 on 2010-04-07
> **Owen.C93 said:**
> No, but if you think that's a good idea then yeah that will do :) Owen forgive me for stressing the fact that there is not such thing as /boot/grub/grub so you must have been referring to /boot/grub/grub.cfg

---

### Post by ranch hand on 2010-04-07
> **Owen.C93 said:**
> No, but if you think that's a good idea then yeah that will do :)
So, what kind of system are you no that has a /boot/grub/grub file?

Mine sure doesn't.  I am running Ubuntu 10.04 with grub1.98.

---

### Post by Owen.C93 on 2010-04-07
Well that is odd because I have a grub file and a grub.cfg file. No doubt my fault, sorry I thought everyone had one:oops:

EDIT: the file I was looking for is in /etc/default/grub  for some reason I have it in /boot/grub/ my bad sorry.

---

### Post by ranch hand on 2010-04-07
> **Owen.C93 said:**
> Well that is odd because I have a grub file and a grub.cfg file. No doubt my fault, sorry I thought everyone had one:oops:

EDIT: the file I was looking for is in /etc/default/grub  for some reason I have it in /boot/grub/ my bad sorry.
Does it work from /boot/grub?

It sounds to me like I would be removing grub-pc and grub-common, deleting any remaining files and installing grub-pc and grub-common and only backing up any custom menus.

---

### Post by Owen.C93 on 2010-04-07
> **ranch hand said:**
> Does it work from /boot/grub?

It sounds to me like I would be removing grub-pc and grub-common, deleting any remaining files and installing grub-pc and grub-common and only backing up any custom menus.
I'm not sure, I use burg now instead. I expect I just put it there by accident.

---

### Post by ranch hand on 2010-04-07
As long as burg has its own /etc/default/burg file you should be fine.  I would move the grub file back and change the name if it is interfering so that you have it in place in case you need it.

---

### Post by benderbeerman on 2010-04-07
ok, here's a link to a copy of my /boot/grub/grub(.cfg) file: [http://docs.google.com/Doc?docid=0AeqU_ryw50fpZDNiYmJtNl8wZDNuZnBzZnA&hl=en](http://docs.google.com/Doc?docid=0AeqU_ryw50fpZDNiYmJtNl8wZDNuZnBzZnA&hl=en)
edit: here's a link to a copy of my /etc/default/grub file also: [http://docs.google.com/Doc?docid=0AeqU_ryw50fpZDNiYmJtNl8xY25ndm5uZ2Y&hl=en](http://docs.google.com/Doc?docid=0AeqU_ryw50fpZDNiYmJtNl8xY25ndm5uZ2Y&hl=en)

---

### Post by benderbeerman on 2010-04-08
> **margazhang said:**
> I have the same problem trying to help a friend switching from Windows to Ubuntu - it is a Toshiba Harman/Kardon laptop. Well, I should not have installed the Beta 1 in the first place - got to wait for the stable release. Having to go back to Ubuntu 9.10 :-(

wouldn't worry about it too much, the stable version will be out soon :)

---

### Post by ranch hand on 2010-04-08
I think your configuration looks fine.  You might try going into your 00_header file and commenting out the "record fail" stuff.

I do not think it will help but it shouldn't hurt anything.

When it proves not to change anything after 3 boots I would restore the file to its current form.

---

### Post by benderbeerman on 2010-04-08
> **ranch hand said:**
> I think your configuration looks fine.  You might try going into your 00_header file and commenting out the "record fail" stuff.

I do not think it will help but it shouldn't hurt anything.

When it proves not to change anything after 3 boots I would restore the file to its current form.

i'll give it a shot

---

### Post by ranch hand on 2010-04-08
Grasping at straws.

---

### Post by benderbeerman on 2010-04-08
weird... i just restarted with my quickest reboot yet, less than 10 minutes total! booted thru plymouth in absolutely no time this time, then stalled on a blank desktop (no menus or icons) for several minutes before logging in. the only change was the commenting out the recordfail timeout

edit: here's a link to the bootchart for this last boot, this bootchart actually recorded 440 secs![http://yfrog.com/hqbenderlucid201004071p](http://yfrog.com/hqbenderlucid201004071p)

---

### Post by k3lt01 on 2010-04-08
> **ranch hand said:**
> Grasping at straws.I doubt GRUB has anything to do with it but I don't think we are grasping at straws. My gut feeling is the bootchart shows where the problem is however my knowledge of what to disable without borking the system is extremely limited. The first things I would be looking at disabling would be modem-manager and wpa_supplicant but I'd be doing a search on this forum for the best way to go about it. If they don't work then try the others in the list in post #44 but be careful.

---

### Post by k3lt01 on 2010-04-08
> **benderbeerman said:**
> weird... i just restarted with my quickest reboot yet, less than 10 minutes total! booted thru plymouth in absolutely no time this time, then stalled on a blank desktop (no menus or icons) for several minutes before logging in. the only change was the commenting out the recordfail timeoutReboot again and see if it's the same, always try more than 1 reboot for each change, 3 is a good number as it shows consistency.

---

### Post by benderbeerman on 2010-04-08
> **k3lt01 said:**
> Reboot again and see if it's the same, always try more than 1 reboot for each change, 3 is a good number as it shows consistency.

sounds like a plan  :D

---

### Post by benderbeerman on 2010-04-08
looks like it's down to about 3 minutes :)

here's the new bootchart:
[http://yfrog.com/g0benderlucid201004072p](http://yfrog.com/g0benderlucid201004072p)

---

### Post by k3lt01 on 2010-04-08
Something in that site really makes my machine lag so I will let you tell us what appears to be lagging in that new bootchart.

---

### Post by ranch hand on 2010-04-08
There may be something wrong in grub with the record fail stuff.  It happens.  I would look at your boot logs and see if anything jumps out and bites you.

The chart came up fine for me but I am worthless at reading them.

---

### Post by k3lt01 on 2010-04-08
I had no idea GRUB could be so temperamental until now. I have been working on the "titles" in GRUB and following DRS305 thread got part of it working weeks ago but only found the problem with the rest of it today with DRS305s help. I like GRUB2 but sheez line spacing that works in the original file doesn't necessarily work in a modified script.

Slightly off-topic I know but in this case I thought it was relevant to say that GRUB can be an annoyance if there is something just slightly out.

---

### Post by ranch hand on 2010-04-08
Check in the archives and see the popularity of grub-legacy when it was new.

About like a turd in a punch bowl.

I think the new version is great but it does have rough spots still.  Os-prober is still not up to it.  You should see the entries I get on new installs before disabling that bugger and putting in my custom menu.

---

### Post by benderbeerman on 2010-04-11
here's something interesting, i just updated to the latest kernel today (-20.29) and i no longer have a boot problem. whatever the conflict was it has been resolved, thank you all for your advice and assistance!

---

### Post by ranch hand on 2010-04-11
This is great.  I kind of like the new kernel myself.

---

### Post by benderbeerman on 2010-04-11
happy so far... :popcorn:

---

### Post by ranch hand on 2010-04-11
Might be a good idea to mark this thread solved.

---

### Post by benderbeerman on 2010-04-12
> **ranch hand said:**
> Might be a good idea to mark this thread solved.

thanks for the reminder :oops:

---

### Post by ranch hand on 2010-04-12
I have trouble remembering that.

---

### Post by margazhang on 2010-04-24
I am testing the latest update of Ubuntu (actually it is Edubuntu 10.04) and now I do not have any problem. So I hope when the new version releases on April 29, most problems with beta versions will be gone :-)

---

