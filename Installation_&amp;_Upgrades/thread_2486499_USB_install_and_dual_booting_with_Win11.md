---
title: "USB install and dual booting with Win11"
date: 2023-05-02
forum: Installation &amp; Upgrades
---

### Post by ajohnl on 2023-05-02
I've shrunk the windows partition with Macrorit Free. It isn't too crippled to do this easily. The windows one needs numbers adding and I have no idea if they are binary based of decimal. It seems Gparted can also do it so wonder why installs can't but some ;) including me would prefer a nicer interface. eg Size and maybe move recovery next to it.

Once there is free space windows partitioner changes. Can't do anything other than use up the space that has been created.

Anyway Macrorit shows the disk layout with no partition numbers. It shows the recovery right at the end of storage. Can I check this while running Ubuntu from the stick rather than installing? Win10 stuck it in the middle of storage when it installed. I wasn't too sure that I could move it during a Linux install so simply overwrote it. This didn't upset win10 but obviously not ideal. I want to be totally sure Ubuntu goes to the correct place.

As win11 is installed according to Macrorit it takes 360MB for system  and 16MB for GPT. Then the win partition. Recovery is 1GB - that may be the same on all installs, I think it's used space was much the same prior to updates. They refer to it as recovery tools.

---

### Post by oldfred on 2023-05-02
Because Windows has some internal files that are difficult to move, gparted may not always work, but usually does. 
So we always suggest using Windows tools to shrink NTFS partitons & reboot immediately as it needs chkdsk after a resize.
Then any issues are Windows issues & users will not blame Linux tools for a Windows issue.

Once you have made unallocated space you should be able to install.
Make sure Windows fast start up & bitlocker are off, otherwise installer may not see the Windows install.
I typically partition in advance and then in installer use Something Else install option to change partition to  / (root).  But you can do that during install also. 

Best to post brand/model system & what video card/chip.
Some brands need extra settings or parameters. If nVidia you need to Safe boot & install restricted drivers.

---

### Post by ajohnl on 2023-05-02
Back again. USB stick on new machine
Screen shot but not sure if this can be used from the USB desktop



Of interest to me as shows the empty space,
Not sure about using this forum. I think I have put the shot is in an attachment

---

### Post by yancek on 2023-05-03
If your question is can you install Ubuntu, I would suggest you use the manual install option.  On Ubuntu, it is called Something Else.  Make sure you boot the USB in UEFI mode to install EFI.  You can then create a partition or partitions you want in the unallocated space.  It should create a separate directory in the EFI partition for the Ubuntu boot files and should also create an entry for windows to boot it from the Ubuntu Grub menu.   Installation of bootloader should be left at the default if you boot UEFI mode.

---

### Post by ajohnl on 2023-05-03
Brand HP machine, Video nvdia T600. nvidia board, It's a mini workstation.

When I booted the new machine from the USB stick I noticed a change. I had to go into the bios and directly select boot that. No option to change the boot order. Makes sense as the bios can be password protected. The install that trashed the machine added an entry to the start up menu to select the boot. Similar view to the bios but different colours used. I didn't see the sense really as it duplicates a function and just avoids an esc key press after a restart. Do I have anything to worry about in this area? ;) I'm always inclined to think if not broken don't fix it so duplicating a function that is always there doesn't make much sense especially if it's done in a different way - which it may not be but who knows.

---

### Post by ajohnl on 2023-05-03
Seemed to have found a very long post on video drivers and etc 100+ pages. However another page
[Linux x64 (AMD64/EM64T) Display Driver | 525.116.03 | Linux 64-bit | NVIDIA]("https://www.nvidia.co.uk/download/driverResults.aspx/204650/en-uk")

How best to install that - possibly from the console - not sure 100+ pages is rather a lot. The driver could be downloaded before a fresh install. It may need the install to use certain available features etc. This brand of cards is rather popular. I have used their and opensource drivers with them - for rather a lot of years.

The linux install on the machine that trashed windows didn't have any problems with the card at all. OS drivers.

---

### Post by oldfred on 2023-05-03
Only install nVidia driver from Ubuntu repository.
You may need safe boot & best to choose the restricted drivers so installed as part of install, or you have to manually boot recovery mode after install to install nVidia driver.

HP seems to be only vendor that does not support efibootmgr to change boot order. It will keep Windows as first in boot order.
You have to go into UEFI settings (not UEFI boot menu) to change boot order if you want Ubuntu first in boot order. Or you have to manually choose to boot it each time.

---

### Post by ajohnl on 2023-05-03
That sounds ok providing install produces a working desktop. For historic reasons concerning other systems I have little interest below that and if needed google finds what I want. I use it and then forget it - other than say moving around and compiling and that sort of thing. I have no interest in picking up yet another system. ;) Not sure I can but have an aversion about some aspects anyway.

I have installed nvidia drivers in the past live with the OS ones in place also just used the OS ones. They have always gone in cleanly. Is there any known reasons why that has changed? It does take work for Nvidia to remain in step.

I haven't use Ubuntu install so don't know what to expect. Previously for me there was a catalogue of software to choose from during install. All OS. I assume Ubuntu may be the same? Or some factors can be chosen?

HP - it's a workstation. Those are generally connected to a local network so for security their approach makes sense. Bios settings may alter this area. I wont mind having to select linux at boot but it may allow me to change it. Their bios's are attractive as several things can be done from them. It was the bios that recovered the machine in the end. There support didn't seem to know that I just needed to wipe the drive via the bios so I wasted time trying to use their USB and DVD's. Those may have been out of date in relation to the machine as windows couldn't find storage drivers. Now I have re installed MS is telling me their is a problem with my account. Probably best ignored as no human to tell why the machine has had 2 installs.

---

### Post by tea for one on 2023-05-03
> **ajohnl said:**
>  Now I have re installed MS is telling me their is a problem with my account.
Of course.
Microsoft know that you have registered with Ubuntu Forums in April 2023 and they want you to reconsider your wise decision ;)

---

### Post by ajohnl on 2023-05-03
> **tea for one said:**
> Of course.
Microsoft know that you have registered with Ubuntu Forums in April 2023 and they want you to reconsider your wise decision ;)
LOL No it may be down to trying to recover my new machine with a downloaded ISO on a machine that already had it installed but trashed. This locked my MS accounts even my win 10 one who's password I have forgotten so now can't set another password on that. So when recovering the new machine I just opened a new account using an outlook email address. They have tied it all up or spotted the hardware has changed due to shrinking the win partition.

Anyone who wants to dual boot with 11 might find this video useful. I turned off fast boot in the bios but not in 11, It's long but interesting. Why the shared partition at the end - pass but would be needed if the windows partition was rebitlocked,
[Dual Boot Workstation - Windows 11 & Ubuntu 22.04 - YouTube]("https://www.youtube.com/watch?v=PF58yIOBdqI&t=2830s")
Anyway I now have an idea about 22.04 install. I noticed that earlier editions eased the process and could shrink the win partition using a mouse.
I part checked my hardware with the stick running in demo but not net connections - I currently have 2 one wire the other wifi, Different ISP's. I could switch as and when I liked on the fly. I'm not sure which one will go yet. I didn't check that. I may be able to run an update on the USB also look at drivers ;) so a bit more to check. Also see if the repo's searched can be extended on it. Not sure that both of the 22.04 ones are used,

:) More PC fun tomorrow. Time to watch a film.

---

### Post by ajohnl on 2023-05-04
Back on the stick, It lost the UK keyboard some how. @ now works following keyboard presses ;) once I found what they were. Another method asked me to log out and then couldn't  log back in, LOL.

The HP bios can change the boot order. Separate section to the usual boot one so machine now uses usb 1st if it has anything bootable in it.

I installed some apps and did an update. There had been some mad fan activity with no need around boot time.Settles down in the stick or in windows, But loaded the desktop utility to look at temp's and it wont function. Used the preferences as it suggests but clicks on it's icon didn't produce a display. The install that trashed windows left the machine with odd fan behavior all of the time, Bit worrying.

Software search. May have missed something but just browsing icons rather than a search. Some one posted links to a repo page for me. Is there an app that will search designated repo's there? I saw mention of adding backports in some post but can't find anyway of changing things.

Using the console. Something I will miss with bells on. I tried running sensors. Command not found, Other distro offers to search for it and then install if found. Any utility to do the same? I normally use a root account as well. Saves typing sudo all of the time in the terminal when needed also allows run as root on the desktop. Just password authentication as needed is ok with me but how does Ubuntu handle this area. Some years ago I installed Ubuntu and set up a root account and that didn't work out at all.

I tried installing the tested nvidia driver on the stick just to see if ok etc. Went wrong at the reboot stage. Maybe I did something wrong? Suspect the problem was down to using restart. Not sure.

Net connections. Wire and Wifi shown as active. No wifi password given so can't see how wifi can be connected. I may well need both active at the same time for a while. Any comments? I have done this before by changing the wire ip address from the usual number so can probably muddle through that aspect. Using both though?

---

### Post by ajohnl on 2023-05-05
No comments. Oh well anyway

Found a bug. Missing my usb sound card. It's been around for some time and was worse but can still miss it. Looks like a timing problem to me. Re plugging fixes it now. Previously having pulse volume control active on the desktop when it's loaded fixed it . It needed to be active from  a previous session. If not run it and then re plug,

Things didn't go too well. I tried the install from the repo web page. Dependency problems from the correct repo's. 

How to re organize the start button icons wasn't clear to me. I'm likely to want to group some in the same way as utilities does. Maybe I missed something but pretty sure I tried right click expecting new and then drag and drop where I want them, Maybe some conventional start button type file can be edited?

So catfish is one app I want. It's a file search that uses the kernel's database. Just needs part of a file name, Folders too. Tried google and found that Ubuntu Studio had included it 14hrs ago so am now running that and have installed it. It's KDE and has all of it's exuberant searches active :( no change there. However add on applications can be searched or just browsed, a long list. Typed sensors in the console as a test and command not found but offered to install it and did. Also includes a partitioner which means some one could prepare to install on it running from the usb stick. There may be a problem with the reboot. It would  have to be tried for dual booting.

Problems. USA keyboard just like straight Ubuntu but that one did select UK once. Makes me wonder if some localization is planted some where permanently and altered accidental by me. Pass, just seems odd. I find it's wrong as soon as I try to enter an email address " instead of @. Oddly both use London time with no summer time adjustment. There doesn't seem to be keyboard option for cycling through them and KDE lists a blistering number of layouts.

Also tried a full update and had the black screen of death. Hasn't done the stick any harm. It uses X for graphics. Not sure about keyboard etc. That can be useful if some one owns a tablet not made by waycom but maybe the find that is a bit more flexible now.

I started using Linux with an enterprise version that came boxed with documentation in books. Bought from a large retailer called PC World. ;) It used the kernel's file database for searches. It is useful at times, Going back that far makes me wonder about trying a simpler desktop. Looks have changed but the basic mechanism that does it hasn't really changed. Capabilities have - sometimes unneeded or not flexible enough, Probably put up with it. it all started when IBM demonstrated a pointing device.

---

