---
title: "[UNSolved] Windows Vista won't start on dual-boot HP G60"
date: 2015-05-15
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2015-05-15
I installed 14.04 on my Windows laptop (HP G60). It set up the boot list properly, giving my Windows Vista bottom billing (of course), but Windows won't start now.

The green 'marching ants' move about three times through and then the machine reboots. I have an endless cycle of Grub list, choose Windows, attempts to start, then reboot.

Ubuntu 14.04 starts up just fine and runs great. Using it, I can 'look' at my Windows partition (both systems on one disk) and see that everything seems okay - it just won't boot.

I issued the command ro rebuild grub (sudo update-grub) but that didn't change a thing.

Any ideas out there on how I can kick my Windows into starting?

Bill

---

### Post by WB0HYQ on 2015-05-15
More info:

When I installed 14.04, I may have screwed things up badly. The installer offered the 'normal' window that show xxxxGB allocated to Windows and xxxxGB allocated to the new Ubuntu install. I used the slider to add roughly 30Gb to the Ubuntu space. This, I think messed up my Windows NTFS partition.

I am now afraid that I'll have to just copy all my stuff on Vista over to an external drive and simply install Ubuntu on the laptop. I hate to do that, as I have a couple of programs I use when traveling that don't have an equivalent in Linux. But, if I have to, I will. I can 'see' into the Windows partition just fine and all my data is still there, it just won't boot.

So, if anyone can can confirm I probably messed up Windows, I'd be very happy.

Bill

---

### Post by Vladlenin5000 on 2015-05-15
Yes, it's kinda screwed and you're right about the messed up NTFS partition. Always shrink the partition in Windows - Windows own disk management tool can do it - and reboot to let it run the error correction tool. Some recommend repeating the procedure, ie, reboot twice. At that point you can install Ubuntu. Ubuntu's installer will take care of most of the options with minimal user input and use the now unallocated space. 

Right now, what you need to use is a Windows installation media or Windows recovery media, something able to provide access to a recovery console where you'll be doing *chkdsk *or something like that. The point being: Windows tools.
After checking and correcting the Windows partition it may mess up Grub and make it boot Windows straight away. If that happens you'll then need a Ubuntu media to boot from in a live session, reinstall and update Grub.

All in all, there's hope. It may not be so screwed as you think.

Nex

---

### Post by WB0HYQ on 2015-05-16
Thanks, Nex. This confirms what I originally thought. The fix you outlined makes a great deal of sense, but I think my best course of action is to scoop all the data/files/pictures I want off the old "C" partition onto a USB drive and just wipe Windows off the laptop and reinstall 14.04 over the whole disk. My G60 is a pretty old laptop (hence the Vista on it) and the battery is giving me trouble also so it may end up being chained to my desk for the rest of its useful life on permanent A/C power.

On the other hand, I may just leave the Windows partition alone for a while and tinker with it from time to time just to see if I can get it to boot once more. Having gotten all of the important stuff of it, I can afford to mess it up even further. I have a Windows 7 installation disk that should have the recovery console tools necessary to do at least a CHKDSK (thorough) and see if that will recover the section of the partition I moved the slider over on top of.

My suspicion was that if I'd taken the offered division originally given to me by the Ubuntu installer, I would have avoided treading on Window's toes. That kind of warning might be a good thing to add to the installation screen above the divided window with the slider.

Thanks again,

Bill

---

### Post by WB0HYQ on 2015-05-16
Ha! Got it! My Windows 7 install disk managed to repair the partition, and I have both Windows and Ubuntu running nicely. Under Windows, the internal wi-fi takes ten minutes to initialize, and when it does it takes another five minutes to actually let me use it. I can iron that out even if I have to use an external USB wi-fi module. Under Ubuntu, the internal wi-fi initialized almost as fast as the rest of the system and I can use it immediately. The "flashing blue light" reported by a lot of users doesn't happen in my case. The blue light comes on and stays on permanently.

Thanks for the heads up. Nex. I'll mark this 'Solved".

Bill

---

### Post by Vladlenin5000 on 2015-05-17
Glad to know you mange to have your system as you like it. You can now mark this one as solved using the thread tool in your original post, so future users will benefit.

Off-Topic: Perhaps it's a good idea to update the drivers for your WiFi in Windows.

---

### Post by WB0HYQ on 2015-05-17
I already added the Solved following my post yesterday.

The slow startup of the internal wi-fi was not present the third time I booted into Vista. When I checked, I had the latest drivers available and they'd been installed six months ago. I think the delay was just Windows doing some housekeeping in the background. The biggest CPU drain was the updater. Vista always was a bit creaky for me.

Thanks for the help.

Bill

---

### Post by Vladlenin5000 on 2015-05-17
You're welcome. :p

PS - Vista was "creaky" to almost everybody using it at the time. It was a flop like ME years before and like 8.x now. Windows 10 will be great and probably the Windows as we know it. The steep decline in market share for the traditional PCs and the rise of the mobile devices will change this landscape in ways we probably can't imagine right now.

---

### Post by mattharris4 on 2015-05-18
I would suggest that others installing Ubuntu/Lubuntu/etc. defragment the Windows install before attempting to install Ubuntu.  If you don't, best case scenario you have less space that the Ubuntu installer will allow you to allocate to its install, worst case you will install Ubuntu over some of your Windows data or OS -- possibly causing you to lose data or worse.  This advice actually applies to any Linux install where Windows (probably OS X as well) will also be on the drive at completion.

You may also be able to buy another battery for your computer at Amazon.com.  They sell batteries, for older computers replacement batteries are as cheap as $13 each depending on model and manufacturer.  Of course there is a limit to how old the computer can be and a manufacturer manufacture replacement batteries profitably but Vista came out in 2008 so assuming that is what your laptop came from the factory with this is likely not a consideration here (they have plenty of batteries for my 2010 eMachines laptop).  An extended use battery may also be available for a little bit more cash that will allow you to use the computer on battery power longer than when it was new.  Unless you do not have any need to use the computer on battery power I would suggest replacing the battery ASAP, some older computers even require a functioning battery to transmit mains power to the computer so if the battery fails completely your computer may not function until it is replaced.

---

### Post by WB0HYQ on 2015-05-26
Recently, I added Ubuntu 14.04 to my laptop by splitting my hard drive. I struggled a bit getting the Ubuntu side running and then it was fine. Now, I find that the Windows (Vista) side is failing to boot. After many (sometimes as many as 10) reboot attempts, the Windows Boot Repair facility will load and run. When it does, it may take as long as twenty minutes to "find" what's wrong (it never tells me what it found) and I can boot into Windows.

I can continue to boot into Windows as long as Ubuntu doesn't update itself and re-write the boot loader. When that happens, I go through the failure to boot routine on the Windows side.

What does Ubuntu do to the boot loader that screws up Windows?

Bill

---

### Post by Vladlenin5000 on 2015-05-26
> **WB0HYQ said:**
> What does Ubuntu do to the boot loader that screws up Windows?

Nothing.

On the other hand, what you do in Ubuntu like mounting and writing to the Windows system partition may have undesirable results. Grub itself just points and chains to the Windows bootloader. Whatever else is happening in the Windows "side" is entirely Windows related.

Assuming that Vista is the original OS, then your computer is anything but new so a failing HDD shouldn't be ruled out.

---

### Post by WB0HYQ on 2015-05-26
According to the Linux side, the Windows partition is already mounted when the desktop comes up. Other than that, I do not do anything to it. I haven't even accessed it with a file browser. I assume that the Windows partition is mounted as the machine boots up, so is there a way to stop that from happening - unless I _***want***_ it to happen?

Bill

---

### Post by Vladlenin5000 on 2015-05-26
No, it shouldn't be. Showing up as a "drive" icon in the launcher or as additional unit in the file manager doesn't mean it is mounted. Now, just clicking on one or another will mount it. It can't be automatically mounted unless you explicitly made it so, by editing fstab or with some GUI tool.

Anyway, this was just a reminder. Windows doesn't like it so we shouldn't do it in order to keep Windows happy ;). I was NOT implying you did it nor that's the cause.

What I would do before anything else:
- Boot Windows (yes, keep trying until you succeed)
- Right click "C: drive", select Properties then tool tab.
- Select error correction and, at the emerging dialogue, tick both options. Confirm.

At this point Windows will tell you that it can't perform the checking/correction in a drive which is in use - this should be expected - and offer to run in the next boot. Confirm. Reboot again in Windows. It should then boot to the recovery tool instead of the normal system. Do not press any key at this point and let the tool do its job.

Alternative CLI method: Use *chkdsk /r* in the command prompt as explained here: [https://technet.microsoft.com/en-us/library/cc730714.aspx](https://technet.microsoft.com/en-us/library/cc730714.aspx)

---

### Post by WB0HYQ on 2015-05-26
I've been through CHKDSK three times - both the error checking and the thorough disk scrub. Neither one of them helped, or hindered, the problem. For some reason, Windows just fails to load and I have to keep trying until it will load once more. Now, each time I manage to get Windows to boot, I keep having to kill CHKDSK after the first one was completed. I figure that somehow the partition 'dirty bit' is never reset, so I get the CHKDSK prompt.

I'm getting to the point where I'm about to wipe Windows off the computer and let Ubuntu have the entire drive. At the moment, Ubuntu is on a 80G partition, and that seems to be quite enough. My laptop only goes out on trips with me so I can stay in touch with various forums, my writing site, and Thunderbird, so losing Windows wouldn't be a big deal - especially Vista, which I hate anyway.

Is Ubuntu capable of reclaiming the rest of the drive WITHOUT having to re-install it? I've been in Windows since the very first version (3.0), but relatively unfamiliar with the partition tools in Linux. I am leaning towards just leaving well-enough alone and use the X-Windows partition for storage or backup.

Bill

---

### Post by oldfred on 2015-05-27
If not using Windows best not to use NTFS. It does require chkdsk periodically just as Ubuntu runs fsck every 40 or 60 reboots. And you can only run chkdsk from Windows.
You do have to let chkdsk finish and with Windows it often has to be run more than once to clear all errors.

But as mentioned I would check Smart tools to see if drive is starting to have issues. You can use it in Disks (icon in upper right for more options) or Disk utility if 12.04.

---

### Post by WB0HYQ on 2015-05-27
I don't understand the first sentence, Fred. Windows has to run on NTFS, so if I use it, NTFS has to be the file system. When I installed Ubuntu, I let it default to whatever it uses for a file system - and it wasn't NTFS.

When CHKDSK runs, it finishes properly and Windows finally boots. The next time I boot into Windows, CHKDSK runs yet again. I've let this happen for four consecutive reboots and yet is still happens.

I have narrowed down possible reasons why Vista won't start and the primary culprit seems to be the built-in wireless adapter. Just about the time the LED should change from orange to green, Windows will either fail, or continue booting (and change the LED). So, just before I shut down Windows, I manually kill the on-board wireless and wait for the LED to turn orange. The next time I boot, Vista seems to boot just fine. Once I get the desktop, THEN I turn on the wireless and let it connect.  I think the wireless drivers (Atheros Wi-Fi) are hosed. The problem is that the latest drivers are around 5 years old and no newer ones are available. I am exploring the use of a new Linksys dongle now and it seems to work okay.

This could be my problem.

Bill

---

### Post by oldfred on 2015-05-27
I did not assume a working Windows in a NTFS data partition. I had XP as a small system partition for years, but kept some data in a separate NTFS data partition. But I had a Windows 7 repair flash drive that I downloaded so I could run chkdsk and make other repairs if needed as I was then not booting XP, but did not want to reconfigure NTFS data partition (since changed).

I thought Windows always worked & it was Linux that always had issues. :)

---

### Post by WB0HYQ on 2015-05-27
No. Windows (Vista) is messed up and Ubuntu works just fine.

I finally got it to start yesterday and I left it running all day. Then, that evening I shut Vista down. This morning, it refused to start yet again. I'm done screwing with it. It will be gone in about half an hour, never to darken my door again.

So, I guess, this is "Solved".

Bill

---

### Post by WB0HYQ on 2015-06-03
Since my last post 2 weeks ago, Vista has been starting up just fine with only 1 instance of failure, but restarted next boot.

Since yesterday, when Ubuntu rebuilt the boot loader (or whatever it is called where it goes out and 'discovers' various operating systems), my problem is back again. Vista refuses to boot over and over again. Choosing Boot Restore will fail also after "Windows is loading files" ends. I have not been able to get into Vista since Ubuntu rebuilt the loader.

Ubuntu HAS to be doing something to the Windows partition that causes Windows to fail. I would really like to know what it is.

Bill

---

### Post by WB0HYQ on 2015-06-09
In the three weeks since my last thread on this subject, I am still frustrated by Ubuntu doing something to the Windows side of my HD.

I am on an HP G60 (which, admittedly, is a bit old) running Windows Vista. I set up the HD (using Windows partitioning tool) and cleared a space for Ubuntu 14.04, then installed it. The Ubuntu side boots up every time, with no problems at all. The Windows side is a mess. Every time I try to boot, Vista fails in the boot process, usually during the 'marching ants' green dots. No message, it simply reboots over and over again.

Sometimes, I am able to get the Windows Boot Repair facility running (but it also fails to boot at around 50% also). It messes about, banging my HD over and over for around 10 to 15 minutes and then, sometimes, I can get into Vista.

When i finally make it into Windows, it runs just fine. I can shut down and reboot into Windows every time, switching between Windows and Linux easily. Then, _***every time***_ Ubuntu rebuilds itself and goes out looking for OS's (finding Vista on the HD also), it sets up the boot loader again.

From that time onwards, I am frustrated every time trying to get back into Windows. Finally, after going through all the stuff to make it boot Windows, I make it work. I can, once again, run between Windows and Linux easily. And, once again, this continues until Linux rebuilds itself.

I would really like to know what Ubuntu does to the Windows partition to make it refuse to boot. it HAS to be doing something that kills the boot process. If I can find out what it is, I might be able to stop it from happening.

During the period I have both OS's working, I can access the Windows side of the HD just fine, read, write, and move files back and forth easily with no errors. This tells me that RUNNING Ubuntu isn't the problem, it is the rebuilding of the boot loader (and perhaps the "discovery" process) that messes up booting.

Any thoughts on this? Are there any alternatives to the default 'rebuild the boot loader' process?

Bill

---

### Post by howefield on 2015-06-09
Threads merged.

---

### Post by Mark Phelps on 2015-06-09
Linux doesn't routinely "rebuild" itself -- unless you're doing updates that cause changes to the kernel version and/or cause changes to the GRUB configuration file.

What you could try as an experiment is booting Ubuntu from the Windows OS selection screen.  To do this, you need to do the following:
1) Download and install EasyBCD from NeoSmart Technologies
2) Start EasyBCD
3) Click the Add New Entry button
4) In the Operating Systems section, choose Linux/BSD
5) Select Type: GRUB 2, Name: NeoSmart Linux, Drive: <drive containing the Linux OS partition)
6) Click the Add Entry button

Then, when you restart Vista, you should get an OS selection menu with an entry for Linux.

If that works, you can then consider removing GRUB from Ubuntu -- as I suspect what is happening is that updates are clobbering the Vista boot loader files.

---

### Post by WB0HYQ on 2015-06-09
Sorry, Mark. I did mean to say that I let Linux update the kernel and in that process it rebuilds the boot loader (is that 'grub'?).

I'll give your idea a try and report back here as to how it works.

Bill

---

### Post by WB0HYQ on 2015-06-09
I downloaded, installed, and ran EasyBCD. It did as you say and added the Linux to the boot menu. BUT, I had to go through the Ubuntu boot menu to get there. By that, I mean I got the purple screen with Windows Vista at the bottom first and then choosing Windows Vista gave me the familiar Windows boot screen allowing me Windows (at the top) and Linux following that.

I chose Windows and it booted just fine. I imagine there is a way to keep Linux from creating the original purple-screen boot menu then?

Bill

---

### Post by WB0HYQ on 2015-06-09
Well, on the basis of two cycles, I find that I can boot between Windows and Ubuntu without Vista messing up.

My first time in Ubuntu, I used Ubuntu Tweak and cleaned the cruft (which had two old kernels in it). That generated a new GRUB search - which normally would mess up Vista for me. This time, it didn't do that. I still have the purple screen first, but if I choose the Vista entry down the list, I then get the EasyBCD chooser and can go into Windows from there. I can go directly into Ubuntu from the first boot choice screen.

So, I guess that might fix this whole thing up. I'll not mark this one [solved] until I am sure, but I will do so if the clean boots continue for a couple of days.

Thanks for your assistance, mark.

Bill

---

### Post by WB0HYQ on 2015-06-10
I have cycled between Vista and Ubuntu now at least 15 times now. Not one failure. It looks as if adding EasyBCD made the difference. I haven't a clue how, but maybe it "insulated" the Vista boot from tampering by the Ubuntu Grub build.

If I've learned one thing in the 50+ years of IT work - if it works, don't mess with it.

Now, I'll mark this [Solved].

Bill

---

### Post by WB0HYQ on 2015-06-11
Well, here we go again. This morning, I spent over 90 minutes trying to get Vista to boot. It is back to the old tricks it originally had: failing in the 'marching ants' phase of boot.

The addition of EasyBCD only managed to put one layer of complexity into the mix - having to select one more menu item before failure.

Linux remains bootable - every time - but Vista fails - every time - now.

While troublshooting the latest development, I realized that during my last set of tests, I never turned the computer off - went to a cold start. Yesterday, i turned the machine off so i could exchange batteries with a new one. Attempting to start up, I was faced with the old non-boot problem again. Even putting the old battry back in didn't help.

So, I am faced with either the supreme frustration of watching the machine cycle through boot/fail over and over again, or dumping Vista altogether and running Linux from now on. Frankly, I wish I'd never started on this dual-boot quest. But, now that I have Ubuntu 14.04 on my laptop, can someone give me help in simply wiping out the Vista half of the hard drive and let me take the whole thing over for Ubuntu's use? I hate to do that, but I've managed to suck all my important stuff from the Vista partition and all that's left is basically a shell of it's former self. The HD is approximately 135Gb and Ubuntu is taking around 90Gb of that. I would like to have the whole HD usable to Linux either as a separate partition, or, hopefully, merged into one HD.

Any help? Or, does this make sense?

Bill

---

### Post by WB0HYQ on 2015-06-13
Still trying to get into the Vista half of my laptop. Fails every time.

Isn't there any Linux guru out there who can tell me how to eliminate the Vista partition and increase my Ubuntu partition to cover the entire HD? I know it involves partition and formatting tools, but I haven't a clue how they operate. Even the Man pages for them are confusing. My only recourse if i can't figure out how to do it this way is to completely trash my current Ubuntu setup and install everything new from DVD.

Bill

---

### Post by WB0HYQ on 2015-06-14
I truly find it hard to believe that out of the 663 people who viewed this thread not a ***single*** one of them can answer my simple (it seems to me) question:

How do I kill the non-functional Windows Vista side of a dual-boot machine in which there is only one hard drive? All I want to do is expand the Ubuntu partition (roughly half) of the HD over into the Windows partition. I. E. use the entire HD for Ubuntu. Is that technically possible? Maybe it cannot be done. Is that the answer? Do I have to start over completely from scratch and destroy all the neat apps I already have in Ubuntu by formatting and installing again?

Failing to find an answer here, is there a more technical forum I can visit and get the answer there?

Bill

---

### Post by v3.xx on 2015-06-14
> I truly find it hard to believe that out of the 663 people who viewed this thread not a single one of them can answer my simple (it seems to me) question:

Thats not how it works.  Most of the hits come from outside the forum.  And those of us who do chime in usually do not want to read 28 post to get up to speed.

I read post 28 and 29.

Use gparted to wipe vista install, then expand your ubuntu partition.  This will probably take hours as it will probably expand the front of the ubuntu partition.  Which has a high probably of breakage and can lead to reinstall.

[http://gparted.org/display-doc.php?name=help-manual#gparted-delete-partition](http://gparted.org/display-doc.php?name=help-manual#gparted-delete-partition)

---

### Post by WB0HYQ on 2015-06-14
@v3.xx: Making someone read through three pages of posts was exactly  what I wanted to avoid before my two threads were helpfully merged.

I  found the URL you cited yesterday, which is why I made the comment  about Man pages. It is still hugely confusing to me. All my expertise is  in the Windows/NTFS side of things, so I am floundering around in  Linux. I am leaning towards just wiping the whole hard drive (which,  incidentally, will get rid of the  "HP Vista re-install like new" 2GB  partition also. My other machines are Win 7/Linux dual-boot, but the  important thing is that they contain TWO hard drives - one for each OS.  Jumping from one to the other has never been a problem. F11 lets me  choose.

But, my laptop is a different animal altogether. It only  has one HD and I guess that Vista got really upset that I tried to  squeeze it down some and install Linux. Using 'gparted' looks to be  pretty complicated, with the high potential of ruining my current Ubuntu  install. So, my best option seems to be just booting my live DVD and  wiping everything out and installing over the entire HD. I really wanted  to avoid that, but I can see dire warnings on the site you cited. My  dzta is already backed up to USB external drive.

Thanks for the input, man. I really appreciate it.

EDIT: tried 3 times to post this, but it isn't making the forum. Oh wonderful! Now I have 3 identical posts. I haven't a clue why that happened.

Bill

---

