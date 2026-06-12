---
title: "GRUB: Error 11: Unrecognized device string"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by TXBDan on 2007-06-26
Hey guys,

I'm also trying to get my Windows XP to boot. If you have some time, please take a look.

Here is my situation:

I have windows XP installed on my only SATA HD.

I also have an IDE HD that used to be an old windows install. I reinstalled my new windows install as above onto the SATA drive. This IDE drive has since been just storage, but it did hold on to its "C:" name if that matters. So my primary windows drive is actually called F: in windows. This IDE drive has the boot priority in the bios.

I just installed ubuntu onto the old IDE HD that i was using for storage. ubuntu boots up and loads fine.

Somehow i missed something in setup and ubuntu never tried to configure my system as a dual boot. It was setup as a ubuntu only boot. So i'm trying to add the windows part to GRUB.

My device.map looks like:
(hd0) /dev/hda
(hd1) /dev/sda
(hd2) /dev/sdb

I don't know what /dev/sdb is. i only have one SATA HD.

My 'fdisk -l':

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS


I added this to my menu.lst:

title Windows XP
rootnoverify (hd1,0) (i tried root and rootnoverify)
map (hd0)(hd1) (i tried flipping the order of this line and below)
map (hd1)(hd0)
makeactive
chainloader +1


The problem is when i select Windows XP in the boot menu, i get the Error 11: Device string not found or something like that.

I'd much appreciate any input. Thanks!

---

### Post by logos34 on 2007-06-26
edit: sorry I see you added the fdisk.

---

### Post by logos34 on 2007-06-26
maybe sdb is usb stick

---

### Post by logos34 on 2007-06-26
have you tried to boot directly to windows on the sata since ubuntu install?  at least that'll show the windows bootloader is still ok.

---

### Post by logos34 on 2007-06-26
I think I see what the problem is:

> map **(hd0)(hd1)** (i tried flipping the order of this line and below)
map (hd1)(hd0)

If you copied and pasted the above without alteration, you need a** space** between the devices like this:
> 
map (hd0) (hd1)
map (hd1) (hd0)

try that

---

### Post by TXBDan on 2007-06-26
ah ha! good eyes!

that was indeed the problem. And now onto the next. hah :)

So now i'm getting the good old "NTLDR is missing".

Now.. does this come from the boot.ini? or is that message generated from GRUB?

In other words, can i conclude that GRUB is now looking at the correct drive/part for windows?

I just tried to set the SATA drive to first priority in the bios and i get the same message. This is bypassing GRUB (since GRUB is on my IDE drive) so i guess its not a GRUB message. However, my original windows MBR is on the IDE drive so i wouldnt expect the SATA drive to boot anyway. But then why is it looking for NTLDR?

Now that i think about it.. did i install GRUB over the windows MBR stuff on the IDE drive? over NTLDR? Is that ok..?

Maybe i can set the SATA to priority and reinstall GRUB there?

Can you guys correct my thought process so i can begin to work on this problem?

Thanks again

---

### Post by logos34 on 2007-06-26
> Now that i think about it.. did i install GRUB over the windows MBR stuff on the IDE drive? over NTLDR? Is that ok..?
yup.  normally it's fine.

> now i'm getting the good old "NTLDR is missing".

Now.. does this come from the boot.ini? or is that message generated from GRUB?

In other words, can i conclude that GRUB is now looking at the correct drive/part for windows?


If I had a dollar for every 'ntldr is missing' error I've read about recently I'd be rich as Croessus...I don't think grub is the problem here...it's a windows error.  This is not a grub problem, it's handing off the boot process correctly I think.  Like you say it's something to do with boot.ini file, maybe NTDetect or something else.  I'd try reinstalling windows bootloader to the windows sata disk--maybe that'll clear up the problem.  You can also post the boot.ini file if you want.  maybe an error creeped in.  But don;t put grub on the sata just yet.

---

### Post by Herman on 2007-06-26
>  I have windows XP installed on my only SATA HD.
I also have an IDE HD that used to be an old windows install. I reinstalled my new windows install as above onto the SATA drive. This IDE drive has since been just storage, but it did hold on to its "C:" name if that matters. So my primary windows drive is actually called F: in windows. This IDE drive has the boot priority in the bios.
I just installed ubuntu onto the old IDE HD that i was using for storage. ubuntu boots up and loads fine. I agree with logos34, it's a Windows problem and it has nothing to do with GRUB at all. Your GRUB has already found and chainloaded Windows okay but your Windows is confused about where it stands because you have been plugging and unplugging hard disks and this means boot.ini needs to be edited in Windows to agree with your BIOS.
Try some things in this link and you should be able to figure it out, [ NTLDR is missing, press any key to restart]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to").

See also this thread here, [Grub booting Win XP "NTLDR" is missing]("http://ubuntuforums.org/showthread.php?t=450329")             ([IMG]http://ubuntuforums.org/images/uf/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=450329") [2]("http://ubuntuforums.org/showthread.php?t=450329&page=2") [3]("http://ubuntuforums.org/showthread.php?t=450329&page=3") ... [Last Page]("http://ubuntuforums.org/showthread.php?t=450329&page=4")), which is not exactly the same as your situation but is similar enough.

If you still have trouble after reading those two links don't hesitate to ask for more help here, someone will help you.
Regards, Herman :)

---

### Post by TXBDan on 2007-06-26
wups.. i'm running the ubuntu CD right now..

i went and booted the windows XP cd, recovery console, and tried to fixmbr. i still got a missing ntldr. so then i came back to the ubuntu CD and noticed that there really wasnt a ntldr or ntdetect. so then i booted the windows cd and copied these files to C:/. rebooted, still no luck.

so then i did 'fixboot's on F: (windows). rebooted, no luck. i rebooted w/ both the SATA and the IDE drive.. no luck. missing ntldr.  so then i tried to fixboot drive c:, wth. booted both HD priorities, no luck. 

So as it sits now i think i have a window's fixboot MBR on both hard drivers and neither will boot. both show 'ntldr missing'.  So i guess i need to edit my boot.ini files, but i can't edit w/ the windows recovery CD or the windows drive mounted here in linux!

So i'm at a point where i can re-determine which HD i want the bios to prioritize.. any suggestions?  I then need to reinstall GRUB here i guess to at least be able to boot to ubuntu.

I REALLY don't want to loose my windows install.. any more ideas on how i could get that to boot? I think i only need a proper boot.ini and i'm in business. i need to research the format of that file and what multidisk/rdisk/etc is.

Thanks again

---

### Post by logos34 on 2007-06-26
> **TXBDan said:**
> So i'm at a point where i can re-determine which HD i want the bios to prioritize.. any suggestions?  I then need to reinstall GRUB here i guess to at least be able to boot to ubuntu.

Here;s the standard proceedure to reinstall grub using the live cd:

sudo grub 
> find /boot/grub/stage1
(enter output--'hd0,0' i think--in next command)
>root (hd0,0)
>setup (hd0)   
quit

boot back to grub on hda drive

---

### Post by TXBDan on 2007-06-26
great thanks.

hd0,0 is arbitrarily whatever HD i choose to be priority=1 in the bios right?

would it be best to keep the IDE as the priority? I just want ot make sure thats straight before i go doing this. thanks

---

### Post by logos34 on 2007-06-26
> **TXBDan said:**
> great thanks.

hd0,0 is arbitrarily whatever HD i choose to be priority=1 in the bios right?

would it be best to keep the IDE as the priority? I just want ot make sure thats straight before i go doing this. thanks

(hd0,0) is hda1 in grub-talk.  yes hd0 = the first hard disk in bios

---

### Post by TXBDan on 2007-06-26
well now im in windows!

haha. when the GRUB menu popped up, i figured wth, and tried Windows XP. It didnt work. complained about a corrupt FS.

So then i tried the main ubuntu kernal and it started up, but during the ubuntu splash screen w/ the orange progress meter, it hung up and just stopped..

so i rebooted, tried windows again, but this time the 2nd window choice within the windows boot loader. this is left over from when i had the original windows installed. voila! it worked. strangely the one that worked is the one that points to the primary HD.. even tho thats the IDE disk w/ linux on it.. so im not sure whats up w/ that. ill reboot in a sec and double check the priority in the bios.

I'm getting there.. i appreciate your help

---

### Post by logos34 on 2007-06-26
well, I was wondering when this was going to get interesting...;-)

---

### Post by logos34 on 2007-06-26
> so i rebooted, tried windows again, but this time the **2nd window choice within the windows boot loader. this is left over from when i had the original windows installed. voila! it worked**. strangely the one that worked is the one that points to the primary HD..

well, I guess we won't know for sure until you post your boot.ini file, but  maybe it has something to do with 'rdisk(0), partition(1)'  vs. 'rdisk (1), partition (1)...

---

### Post by TXBDan on 2007-06-26
Ok. i rebooted and confirmed that my IDE HD is infact the priority in booting.. so i dont totally understand why windows boots.. but it does. both options in the windows boot loader are 'Windows XP Professional' so i renamed them to Windows 1 and Windows 2. so then i can definitely trace the one i choose to the boot.ini.

On the linux side, is there a way to 'repair' the install?

I booted normally into ubuntu, same crash during the very beginning of the progress bar. i booted again into recovery mode and saw that it hangs up right after the USB stuff. the last thing it displays in the USB mouse stuff.

*shrug*

---

### Post by logos34 on 2007-06-26
maybe Herman or someone else has a suggestion about the ubuntu errors...I do know that dmesg | tail will give some clues.

could you post that boot.ini file?  I'm just curious exactly what the entries are

---

### Post by TXBDan on 2007-06-26
sure,

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Pro 1" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Pro 2" /fastdetect


Option 2 is the one that works. so thatd be pointing to the first part on the first HD eh? weird.. unless the default overrides it? i wouldnt think so. thats the time out default right?


How/where would i use that command? nevermind, i searched and foudn some info. ill get the log and report back

---

### Post by logos34 on 2007-06-26
> multi(0)disk(0)rdisk(**0**)partition(1)\WINDOWS="Micro soft Windows XP Pro 2" /fastdetect

Just as I suspected...I think what happened (someone correct me if I'm wrong) is that when you installed windows on hda the first time, the IDE drive was set first in the bios hard disk boot priority, so it was seen by windows as '(0)'--like grub NTLDR and /or NTDETECT counts devices starting with zero, although it starts counting partitions at '(1)'...OTOH, when you installed windows to the sata, it was at the time **second** in the bios boot order, which is how windows detected it -- hence 'rdisk (1)'. But in a dual-boot, dual-drive setup when you try to boot windows on a non-first hard disk, you have to add those 'map' lines to trick windows into thinking it's the first disk in the bios boot order, so you lie and say 'you're on hd0'...but I guess this causes a major confusion when ntldr tries to boot windows using the 'rdisk (1)...' entry.  

Herman, wherever you are, isn;t this is what is happening?

One thing you could do is change the 'default' line to 

> default=multi(0)disk(0)rdisk(**0**)partition(1)\WINDOW S

so you won't have to choose it

edit: and yes that's the default timeout.  You can change it all the way down to 0 if you want

---

### Post by TXBDan on 2007-06-26
Here's a dmesg | tail -n 50: 

ubuntu@ubuntu:/mnt/ubuntu$ dmesg | tail -n 50
[  118.647288] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[  118.647299] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[  118.647315] PCI: Setting latency timer of device 0000:01:08.0 to 64
[  118.647320] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[  118.783356] NET: Registered protocol family 17
[  119.704046] fuse init (API version 7.8)
[  121.722440] NET: Registered protocol family 10
[  121.722523] lo: Disabled Privacy Extensions
[  122.067197] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[  129.742155] input: Power Button (FF) as /class/input/input4
[  129.742284] ACPI: Power Button (FF) [PWRF]
[  129.742525] input: Power Button (CM) as /class/input/input5
[  129.742643] ACPI: Power Button (CM) [PWRB]
[  129.771387] No dock devices found.
[  129.786183] Using specific hotkey driver
[  129.888056] ibm_acpi: ec object not found
[  130.094916] pcc_acpi: loading...
[  130.729609] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[  130.729643] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[  130.729645] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[  130.729647] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[  130.729649] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[  130.731189] powernow-k8: ph2 null fid transition 0xe
[  132.668925] eth0: no IPv6 routers present
[  145.067293] lp: driver loaded but no devices found
[  146.302057] ppdev: user-space parallel port driver
[  158.942328] eth0: no IPv6 routers present
[  163.025782] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  163.025787] apm: overridden by ACPI.
[  138.544000] Time: acpi_pm clocksource has been installed.
[  139.048000] Bluetooth: Core ver 2.11
[  139.048000] NET: Registered protocol family 31
[  139.048000] Bluetooth: HCI device and connection manager initialized
[  139.048000] Bluetooth: HCI socket layer initialized
[  140.084000] Bluetooth: L2CAP ver 2.8
[  140.084000] Bluetooth: L2CAP socket layer initialized
[  140.104000] Bluetooth: RFCOMM socket layer initialized
[  140.104000] Bluetooth: RFCOMM TTY layer initialized
[  140.104000] Bluetooth: RFCOMM ver 1.8
[  277.424000] kjournald starting.  Commit interval 5 seconds
[  277.424000] EXT3 FS on hda1, internal journal
[  277.424000] EXT3-fs: mounted filesystem with ordered data mode.


i don't see anything screaming at me..

---

### Post by logos34 on 2007-06-26
yeah, nothing leaps out at me either...no mention of usb...there are a few other files in /var/log you could check for a hint on what's up: debug, messages, and syslog. (syslog0?)  But you'll have to get someone else to translate them.  Thing that gets me is you didn't touch the / partition or anything.  Maybe do **sudo fsck /dev/hda**, but I don't think this has anything to do with a filesysytem error...hmm

---

### Post by TXBDan on 2007-06-26
hrm.

fdsk was clean.

i tried both kernals (20.15 and 20.16), same thing.

looked through all the logs i could find, no blatent errors.


what the heck did i do? hrmmm

does the fact that ubuntu even starts and shows the UBUNTU screen w/ the progress bar rule out anything boot related?

---

### Post by logos34 on 2007-06-26
> **does the fact that ubuntu even starts and shows the UBUNTU screen w/ the progress bar rule out anything boot related?**

well, we're getting to the /boot where the kernel images are (vmlinuz and initrg.img), although I think you still technically in the boot-up process where root is mounted -ro and the kernel decompresses and runs a system check initializing all the hardware and drivers...but you're not yet at the X server stage so it's not a graphics issue (that'll be next!). Maybe it's not finding a module or there's a config error somewhere.  

Thoughts: maybe reinstall ubuntu without overwriting the grub that is there now (and that works!)...you have to use the alternate install cd though because it's the only one that allows you the option of NOT installing grub.

---

### Post by logos34 on 2007-06-26
I really wish this would work for you, seeing how you've come this far and managed to get windows to boot from grub and all...but I have to confess I just don't know enough about this part of the boot process to say what could be causing the problem.  

Anyone else?

---

### Post by TXBDan on 2007-06-26
woot!

i had a hunch and just reinstalled ubuntu w/ the normal CD.

However this time i noticed that it detected my windows 'documents and settings'. hrmm it didnt do that last time.

sure enough after the install i rebooted, and wam, windows was already in the GRUB menu. and it works! and ubuntu works!

who knows what happened during the original install but im pretty sure i did everything the same. there arent many questions. *shrug*

but thanks a lot for the help!

---

### Post by logos34 on 2007-06-26
> **TXBDan said:**
> woot!

i had a hunch and just reinstalled ubuntu w/ the normal CD.

However this time i noticed that it detected my windows 'documents and settings'. hrmm it didnt do that last time.

sure enough after the install i rebooted, and wam, windows was already in the GRUB menu. and it works! and ubuntu works!

who knows what happened during the original install but im pretty sure i did everything the same. there arent many questions. *shrug*

but thanks a lot for the help!

Hey great!  

I was hesitant to recommend a reinstall that would replace grub, thinking you'd end up right back at square one.  You really lucked out - it even got the windows entry perfect.  super. yeah who knows what happened the first install.  

Enjoy!

---

### Post by Herman on 2007-06-26
:D You fellows have done an excellent job! Good work and congratulations! I just got home for lunch, I was working. I see I missed all the fun! :D
Well I think you two made all the right decisions and things should go really well now. 
It's quite a complicated thread to read all at once and get up to date on what's been happenning during the past few hours, but I think maybe TXBDan's Ubuntu's /etc/fstab might have been the problem when Ubuntu wouldn't boot after switching hard disk priority in the BIOS. I'm not certain, I'd have to re-read the thread again and think about it for a while, but maybe that could have been it. In any case, it's all in the past now, and actually, re-installing Ubuntu would have been probably the best way to deal with it anyway, especially since it was a new install.  Re-installing Ubuntu only takes half an hour or so, and it takes that long to edit all the files, so it probably is better that you have a nice re-install. Now you know for sure everything is set up perfectly.
Again, well done both of you,
Regards, Herman :D

---

### Post by logos34 on 2007-06-27
Hi Herman, 

The fstab!  Never occured to me.  You could very well be right.  But if it was having trouble mounting, how could it write to the logs (assuming those were not left overs from a previous session)?  And how could fstab entries have changed (it was working before)? Stuff happens I guess...

The main reason I was hesitent to suggest a reinstall is because I thought he only had the live cd, which would force him to overwrite grub on the mbr again, which he had just managed to get to chainload windows.  In retropect this probably doesn't make sense because it was really menu.lst (i,e, the map lines typo) that was at issue, and reinstalling would have meant reediting in the event that the debian installer didn't get the windows entry exactly right.  (And then, of course, the problem shifted to boot.ini).  But my 'leave well enough alone' voice was saying the opposite.  Besides, if we tell everyone to just reinstall for every problem, we'll never have any fun getting under the hood, right?  

He really lucked out in getting everything right on reinstall, IMO.  

But it had a happy ending so I'm happy.  Maybe I will recommend a reinstall for new installations a little more often from now on.  

Great work there, Herman, on the SuperGrub page and Grub Page.  Use it all the time.

I'm actually in winxp x64 for a change right now. My 350MB sp2 download is ready for install.  Watch it bork everything.  

see ya.

---

### Post by Herman on 2007-06-27
Hmmm, I'm just re-reading all this again now that I have more time and it looks like I am wrong thinking it would have been the /etc/fstab. In post #9, and #11 it looked like TXBDan was thinking about switching the hard disk priority in the BIOS, but then in #13 just says he's in Windows. I was probably jumping to the conclusion that was what happened. Later in post #16 he confirms that the IDE hard drive is definitely the first in the boot priority. SO I guess I'm wrong.
So if TXBDan used the map commands like you suggested then it makes sense for boot.ini to work with rdsik0 like you explained. That's right. Now I don't know why Ubuntu decided it didn't want to boot then. You did the right thing again by suggesting a fsck. That's what should have fixed it. 
Well, now I just don't know why Ubuntu wouldn't want to boot. Oh well, it's fixed now, that's the main thing. :D

This kind of reminds me of at the end of a game when the sports commentators on TV show the slow motion replays and discuss what happened. :D

He-he, Bye for now,
Regards, Herman :D

---

