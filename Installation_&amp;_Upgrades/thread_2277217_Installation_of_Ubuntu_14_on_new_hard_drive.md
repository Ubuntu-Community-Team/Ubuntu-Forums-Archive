---
title: "Installation of Ubuntu 14 on new hard drive"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by undershepherd1 on 2015-05-07
I just purchased an HP Pavillion F111NR laptop with Windows 8.1 on a 1 TB drive. My intention is to purchase a new solid-state drive, remove the Windows installed drive, install the new SSD and install Ubuntu on it.
I have read these articles numerous times: 

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

among others as well. I have read on this forum about how some have had access to the firmware boot manager made inaccessible and tried to restore it by short-circuiting the firmware.

My questions:
1) Do I need to disable fastboot, fast start, SecureBoot or anything else BEFORE removing the Windows HD?
2) I will be using a USB with the latest version of Ubuntu 14LTS on it to install Ubuntu. I assume I will need to change the boot order to do that. What happens if I cannot access the boot manager to change the boot order back after installing Ubuntu?
3) Is this even worth the risk? I have read numerous posts about how users have lost access to the firmware and it frankly frightens me a bit. I am certainly no expert with computers, though I have been using Linux for about 10 years now. I currently have a five year old Acer laptop that came with Windows Vista. I installed Ubuntu 12 via DVD, at first dual-booting, then replacing Windows completely. I don't have access to the BIOS, but the computer will boot from the DVD is I have one in there, as I used it to do a fresh install of Ubuntu 14. 

Any help is appreciated.

---

### Post by pmi2 on 2015-05-07
What do you mean above when you say "I don't have access to the BIOS"?

Does this mean that your older laptop computer will not boot without the DVD?  In other words, your Acer laptop does not boot directly from its hard drive?

---

### Post by oldfred on 2015-05-07
Does your UEFI/BIOS have a fast boot setting. That is different than Windows fast startup.
Fast boot in UEFI is where it skips the normal checks on what hardware is in your system. Since you rarely change hardware it speeds up boot. But it then boots so quick you often cannot get back into UEFI.
My motherboard (not HP) had fast boot setting with separate setting for warm or reboot and full power off cold reboot. And I could even set a delay, so I used 3 sec so I could always get into UEFI if needed, although it now slows reboot by 3 sec (and I did another 3 sec for grub) and with SSD reboot is very quick.

Grub menu does have a setting that is supposed to get you into UEFI. But if you only have one system installed you will not normally get grub menu.

HP have issues with booting "ubuntu" entry in UEFI. They have modified UEFI to only directly boot an entry with "Windows". That is not per UEFI standard.
But UEFI still boots a hard drive entry so with HP and others we copy grub into /EFI/Boot and rename it to bootx64.efi. Then it is like booting an external drive or flash drive as that is how external drives are booted, from bootx64.efi.

Details are in link in my signature if you need to know now.

---

### Post by undershepherd1 on 2015-05-07
[I]What do you mean above when you say "I don't have access to the BIOS"?

Does this mean that your older laptop computer will not boot without the DVD? In other words, your Acer laptop does not boot directly from its hard drive? [/I]

On the older laptop, it boots from the HD which has Ubuntu on it. But after pressing the power button, the screen says "Press F2 to access system settings" but pressing it repeatedly or continually only brings up the Ubuntu menu.

---

### Post by undershepherd1 on 2015-05-07
oldfred:
Thanks for your  reply. I will read the link you attached in your signature. I do not have the HP as yet, just purchased it online two days ago.  
For a non-expert like me, some of the instructions are rather vague. Such as: 

*"Backup entire efi partition before making changes."* Backup the Windows HD efi partition? Back it up to a flash drive?

*"From live installer mount the efi partition on hard drive,"*  How do I get to the terminal from the live installer?  Do I do this before partitioning the new SSD? Is gpt included in Ubuntu installer?
I'm sorry for the dumb questions. I know how to use the terminal in Ubuntu and some basic commands. This is way over my head. 
Thanks again for all your help.

---

### Post by pmi2 on 2015-05-07
I remember that some Acer laptops have an issue with timing when you press F2 (so do some other laptops, Acer is not unique in that)  Depending on your model, there are various ways posted on the Internet, you can use to overcome that.  Here are some quotes from those kinds of posts:

> ...with some laptops you have to press the key at just the right time. To  fast and the keyboard has not been initialized yet to slow and you  missed it and it is booting Windows...
and:
> One finger on F2 key

With ANOTHER finger press start button

IMMEDIATELY start pressing f2 every SECOND

You can even start pressing F2 ...BEFORE you press start/power button (it will do no harm)

SO like this....

PRESS F2, PRESS POWER BUTTON, WAIT 1 SECOND PRESS F2,WAIT 1 SECOND PRESS F2,WAIT 1 SECOND PRESS F2,WAIT 1 SECOND PRESS F2,...

Basically, this is telling you that you have to press F2 during a very short time window, to be recognized.  Usually while the Logo screen is up.

On some laptops you have to remove the hard drive (temporarily), which slows the boot process enough to give you a chance to get into the bios.

edit:

Perhaps you can practice with a Live CD/DVD", or usb stick, using your old laptop.  Things like running Linux from the live media, opening a terminal, using the GParted partition editor, and so on.  The same thing would apply to doing backup/restore.  Try it on the old laptop.

(nothing is worse than having TWO machines that don't work the way you want them to)

---

### Post by oldfred on 2015-05-07
Further in the instructions are several suggestions for backups.

I just purchased a Dell SFF and it took a lot to do all the backups we suggest. My last Windows install was on my desktop with XP back in 2006, so I did all the backups. 
I did a Windows backup which took a 8GB flash drive, I did a Dell recovery backup which took 3 DVDs, and a full backup with Macrium. The Macrium backup took over 20GB or another 32GB flash drive and two DVDs one Linux recovery and one Windows PE recovery (you probably do not need both, but I did everything). Macrium also backed up efi partition, but not sure if any of the others did. I like to have efi partition separately backed up, as you can just copy it back if necessary. No special install software required. Backups should be to other devices. 

Because I had to go to store to get more media, it took 3 days. I also had to learn how to change the Windows fast start up, shrink Windows NTFS partition and change some UEFI settings. Every vendor is different on UEFI.
But Ubuntu install took about 10 minutes.

On Ubuntu run the live installer in live mode first just to make sure system works. You click on icon in upper left (Dash) to select applications, and type in terminal. If I keep Unity, I lock terminal to left icons so I can make it easily accessible. Or Ctrl + Alt + T anytime.
But to copy efi partition, I just use Nautilus. With 15.04 I have had issues mounting it and editing it after install as the settings in fstab are now very restricted.


[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by undershepherd1 on 2015-05-07
Thanks again to everyone who has offered suggestions. I guess I'll have to wait until I receive the laptop to try all this. A few people have said that all they did was change the boot order and Ubuntu installed correctly on HP computers, even alongside Windows 8. 
Will it be easier to install Ubuntu on the same drive as Windows (following the instructions here: [http://www.rodsbooks.com/linux-uefi/;](http://www.rodsbooks.com/linux-uefi/;) or will it be easier to take it out, install a new drive, and dedicate that whole drive to Ubuntu? 
I know how to run Linux in live mode, how to use the terminal, how to make backups in Linux. Not so much restore. I have used a partition manager before, in previous versions of OpenSuse and Red Hat. I'm not concerned with the older laptop's BIOS accessibility. 
I am concerned about the install of Ubuntu on the new laptop and if it will mess things up and then the Windows HD will not work as well.
 
So, I guess the order of steps may be as follows:
1) See if the laptop will boot the USB (with Ubuntu on it) and allow me to try the live version with the original Windows HD in place.
2) If it does, shut down the laptop, remove the Windows HD, install the new drive and try step 1 again. 
3) If it doesn't boot to the USB this time, I can try to access the boot settings, change the boot order, and re-try step 1. 
4) Here is where I get confused. If step 2 and 3 don't work, what next? If the live version works with the new drive installed, should I go ahead and try to install Ubuntu on the new drive? Will I need to do the partitioning manually (via the "Something else" option), or allow Ubuntu to partition the new drive for me? The discussion about installing in EFI mode or legacy mode or whatever is beyond me. What kind of problems will I encounter if I try to install Ubuntu on the new drive without first changing boot order, secureboot, fast boot, etc.?

---

### Post by oldfred on 2015-05-07
Best to change UEFI settings first.

If you unplug Windows drive, it may not automatically work when you replug it in. UEFI saves boot entries in its NVRAM, but if drive is missing then others have posted that it loses those entries & you have to readd them to the UEFI boot menu. You can do that from your Windows repair console or Linux with efibootmgr.

System should boot in CSM/BIOS mode without issue if you turn off secure boot. BIOS mode is a totally separate way to boot and secure UEFI must be off. UEFI has two modes secure and not-secure.

How you boot install media is then how it installs. Or you must boot flash drive in UEFI mode to install in UEFI mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mattharris4 on 2015-05-07
> **oldfred said:**
> Does your UEFI/BIOS have a fast boot setting. That is different than Windows fast startup.
Fast boot in UEFI is where it skips the normal checks on what hardware is in your system. Since you rarely change hardware it speeds up boot. But it then boots so quick you often cannot get back into UEFI.
My motherboard (not HP) had fast boot setting with separate setting for warm or reboot and full power off cold reboot. And I could even set a delay, so I used 3 sec so I could always get into UEFI if needed, although it now slows reboot by 3 sec (and I did another 3 sec for grub) and with SSD reboot is very quick.

Grub menu does have a setting that is supposed to get you into UEFI. But if you only have one system installed you will not normally get grub menu.

HP have issues with booting "ubuntu" entry in UEFI. They have modified UEFI to only directly boot an entry with "Windows". That is not per UEFI standard.
But UEFI still boots a hard drive entry so with HP and others we copy grub into /EFI/Boot and rename it to bootx64.efi. Then it is like booting an external drive or flash drive as that is how external drives are booted, from bootx64.efi.

Details are in link in my signature if you need to know now.


In other words I would return this computer to the store and buy one from a maker that does not attempt to force people to only use Windows.  Oldfred's process works well if you can understand the instructions.  Unfortunately most of us are not programmers (myself included) and from what I can understand this requires changing code in the actual kernel manually (as opposed to an apt-get script) -- not something to be taken lightly.  One screw-up and it will likely take either a wipe and reinstall or Linus Torvalds himself to fix it (if you call Linus be prepared for a snarky comment along the lines of his comment to a programmer that he didn't know how the guy survived infancy as he was too dumb to find a breast to suckle on -- unfortunately he is known to be crude and rude to people, actually he is my kind of guy there as my natural unfiltered personality is similar but he is a very talented programmer and actually created the Linux kernel in the early 90's).  

Dell computers don't have this issue, most Lenovos do not either (none have this specific issue but we did see one on here where there were other problems, I could not tell if it was an individual sample issue or a Lenovo model line issue).  My 2014 model Toshiba did not either (other than disabling Fast Boot and possibly Secure Boot the install was as easy as a BIOS computer install) although I have seen a couple of comments that some newer ones do, (EDIT:  I found more on this issue -- including one comment from a well-respected moderator here with instructions on how to deal with a Toshiba with this version of UEFI so I have voluntarily edited my original comment here, the comment I originally read on this issue did not meet my standards of completeness and I had not run into others until tonight) if you purchase a Toshiba laptop is to make Windows backups before wiping or changing the HD and installing a Linux OS.  If the computer has the "HP issue", wipe, reinstall Windows and return the computer to the store for exchange or refund.  We do know that Toshiba CS is useless with these issues (even though they sell computers minus an OS in some countries -- what is someone going to install on one of these, Fortran?  C++? -- no, they are purchased for installation of some flavor of Linux) and will instruct you to reinstall Windows and use that instead.  Dell sells a couple of their computer models with Linux pre-installed but unfortunately they picked their top of the line Intel i7 CPU equipped computers and they cost about $1300 -- you can get an i3 CPU equipped computer for less than $500, install Ubuntu on it yourself and a Windows license to boot, get 90% of the performance of the i7 (unless you are working for an adult film producer and editing movies on your laptop -- in which case you would not likely be using a Linux OS anyway -- an i3 is more than enough CPU for you) and save $700 in the process.  There are also a couple of sellers that do the wipe and install of Ubuntu for you, Linucity ([www.linucity.com]("http://www.linucity.com")) sells an i3 equipped Toshiba laptop for $415, a similar desktop for less than $400.  System 76 ([www.system76.com]("http://www.system76.com")) is another but their computers are more expensive -- their full size desktops (i5 CPU) start at $659, their laptops (i3 CPU) start at $599.

If you do choose to modify the kernel to boot Ubuntu on the HP computer, I wish you the very best of luck.  Please report back how it went and the difficulty of the process for you.  I am very interested.

---

### Post by oldfred on 2015-05-07
I have not seen anyone that had to modify kernel to get it to boot. But a variety of brands do different things with UEFI that do make it more difficult. 

Some extremely new systems do have issues where the very newest kernel, support software & Intel video drivers are needed, but you can install those with a ppa and then it is just like any other apt get update.

---

### Post by undershepherd1 on 2015-05-08
Well, lo and behold, my order from HP was canceled, actually for the second time. I ordered the first time online, but inadvertently inserted an extra letter in my email address. After no contact from HP for five days, I called and they told me it was canceled because of the errant email. So I ordered it again from HP direct on the phone. I again did not hear from them for three days, so I called this morning and was informed it was canceled, again. No reason given. 

I have done a lot of looking online and at Best Buy for laptops. I had looked at System76 computers, but I read four reviews that all said they were made with shoddy parts and the customer support was horrible and the wireless cards on all of them either wouldn't work or wouldn't stay connected. I looked at linuxlaptops, but their prices for anything decent (and better than the one I do have) are above my price range (less than $900). The Dell ones with Linux pre-installed had Celeron processors. I presently have an AMD Athlon2. 

I thank you all very much for your help, advice and support. It is greatly appreciated by us, who, like mattharris4, want to use Linux, but the learning curve can be steep and daunting. It helps to have experts ready to help and so patient with us dummies. 
I guess it's back to the drawing board. I'll check out Dell and linucity. Do any of you have any suggestions of what brands to avoid and what brands are at least not resistant to Linux installation?

---

### Post by oldfred on 2015-05-08
Some of the smaller systems have 32 bit class 3 UEFI. Class 3 means no BIOS/CSM mode and Linux used to not have a 32 bit UEFI installer. But those still are much more difficult to install.

All others seem to be able to install. A few require CSM which then is a bit of a hassle as you must totally reboot and may have to turn on/off UEFI or CSM mode to match install if dual booting. If only booting Ubuntu you then can install in CSM or UEFI. 

But UEFI does have some advantages. But because of many more features, that is more settings/configurations that you may have to adjust.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I think if you stay with the major brands there is a better chance that it works well. 
Other issues that I have not followed a lot are video and wireless. 
With video the higher end systems with dual video are now starting to work with Linux. Before there was bumblebee as a way to make dual video work.
And best to check which wireless chip is used. Some seem to work better than others. But again if installing with wired Ethernet then system usually downloads correct driver. Only then a few require special effort.

---

### Post by mattharris4 on 2015-05-08
> **oldfred said:**
> I have not seen anyone that had to modify kernel to get it to boot. But a variety of brands do different things with UEFI that do make it more difficult. 

Some extremely new systems do have issues where the very newest kernel, support software & Intel video drivers are needed, but you can install those with a ppa and then it is just like any other apt get update.

I might be misunderstanding the process you wrote to make HP computers boot changing some line of code to make the UEFI boot Linux or GRUB by tricking it into thinking it is booting Windows.  I was under the impression that the process you wrote was altering the kernel.  That shows how little I understand about actually programming in any computer language (not limited to just Linux).  Other than my verbiage I think I described the scary process pretty well as I understand it.  At this time my recommendation stands even with your correction -- don't buy a new HP computer if you wish to run Linux (not limited to just the Canonical OSes) on it.  It is too bad Toshiba is evidently moving in the same direction altering the UEFI to only boot Windows.  My year old Toshiba's Lubuntu install went almost as smoothly as an older BIOS computer's install -- quite easily.

I agree that installing a packaged ppa is relatively simple as long as a person has adequate instruction on how to do so.  I installed the (non-Canonical) Oibaf AMD driver package, it went relatively smoothly and only took about 20 minutes including installing another ppa that was required to install and run Oibaf.  It would be nice if someone could create a ppa that would run in a live USB session of Ubuntu/Lubuntu/etc. to make HPs boot Linux or dual-boot with Windows.  I hate having to tell people not to purchase any new computer of a certain brand but if I am going to be honest with people here and have a clear conscience about it that is what I have to do in this instance.

---

### Post by oldfred on 2015-05-08
With HP, Sony and several others you have to copy grubx64.efi or shimx64.efi into a /EFI/Boot folder in the efi partition and rename it bootx64.efi. Then the hard drive boot entry works to actually boot grub.

The /EFI/Boot/bootx64.efi is also the way external USB drives boot and UEFI was updated several years ago to add internal drives to allow that. My full install of Ubuntu in a flash drive required me to do that also even though I do not have major issues with my desktop. My desktop did require many UEFI setting changes to get to configured to boot Ubuntu in UEFI mode.

For Sony & HP detailed instructions have been posted here and in the link in my signature.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by MikeMecanic on 2015-05-08
Have an HP computer and installed Ubuntu in the pass 3 years many times (more then 20 times with Ubuntu 15.04 B1, B2 and Final release). 

**Let's make it simple**:  You access the BIOS on almost any HP computer by pressing F10.  **You access the boot up sequence by pressing F9 **and from there everything is solved:  Choose the boot up media where Ubuntu is in.  The rest belong to the Ubuntu Installer...

But among all and because Hp does not support Linux (only Dell and Lenovo do), _t**he first thing you must do under Windows is to update the BIOS**_ and then get rid of that wide spread virus: Windows 8.  Choose the default installation.  For fine tinning purposes you may need a second installation if you get an unstable desktop environment.  You'll do!  Ubuntu runs at best when it's installed from Ubuntu.  

All the best,

---

### Post by undershepherd1 on 2015-05-09
Posted by oldfred: "With HP, Sony and several others you have to copy grubx64.efi or shimx64.efi into a /EFI/Boot folder in the efi partition and rename it bootx64.efi. Then the hard drive boot entry works to actually boot grub."

Reading through the three detailed instructions suggested by oldfred above, one thing remains confusing to me. Copy grub64.efi FROM WHERE? And when? As in, when Ubuntu live is up and running or after Ubuntu has been installed on a HD with Windows in a dual boot situation or what? What may seem to some as easy to follow instructions are to others almost gibberish. Some of us need to be taken by the hand and treated like a 5 year old who has virtually no knowledge of these things. 

This whole thing with UEFI and all the finagling that one seems to have to do to get Ubuntu installed is quite daunting. And frankly, I'm so fearful of rendering a brand new computer completely unusable that I would probably just leave Windows as is and not try at all. Or the other option is to spend an additional $200-$300 and buy a laptop with Ubuntu already installed. Which is the route I am currently researching. 

I know that my ignorance of how to do what to some of you are simple tasks is because Windows has dumbed computer users down. I learned a lot when using MSDOS and earlier versions of Linux, which forced the user to know some code. But I have forgotten some of that and have not kept up with the newer technology, like UEFI. I didn't know it existed until I began to look into buying a new computer. 

Please note that all the help is always greatly appreciated and it needs to be said over and over to those of you who take the time to help, THANK YOU! For those of you who are more knowledgeable about this stuff, it must seem like us newbies are just plain dumb. I admit that may be the case with me. In the end, what we all want, especially us newbies, is to be able to start up the computer, see the Ubuntu logo, have it up and running successfully and without any glitches, and raise our hands in triumph over Windows and scream, "I did it!" 

I would humbly ask that when you post a response in order to help someone, that you "dumb it down" and make sure to include every keystroke or describe in detail the particulars of the situation. I know it can be tiring to do so, and I thank you ahead of time for taking the time to do that.

---

### Post by oldfred on 2015-05-09
With UEFI grub creates a new folder in the efi partition as part of the install. And grub is in that folder. The detailed instructions showing the cp command shows both the from & to locations. Some system have the /EFI/Boot and others you have to create that folder in the efi partition.
I have many links for most brands of computers on what users have done. Some have just given up thinking it is just too complex but most have been able to install.

If that concerned buy a larger flash drive or external hard drive and install Ubuntu to that. Still need to install in UEFI boot mode and you need to partition in advance. Even external will auto install grub to internal drive's efi partition, but you can copy grub into external and in all cases must use a bootx64.efi to boot. My flash drive would not directly boot grub/ubuntu full install until I added  bootx64.efi.

My new Dell SFF small form factor desktop type system, just worked. While it took me about 3 days to learn Windows 8 to change settings and did have to go to store for more media for backup as I used 5 DVDs & 2 flash drives, it took 10 minutes to install Ubuntu and it just worked on reboot.

---

### Post by undershepherd1 on 2015-05-09
```
 If that concerned buy a larger flash drive or external hard drive and install Ubuntu to that. 
```

Well, that was the reason I started this discussion. I was planning to 1) buy a laptop by one of the big manufacturers (HP, Dell, Lenovo, etc.), 2) buy a new internal SSD, 3) remove the Windows drive originally shipped with the new laptop, 4) install the new SSD, and 5) install Ubuntu on it. Then, I read about UEFI and SecureBoot and Fast boot and things got real confusing and scary. I was hoping I would be able to re-install the OEM Windows drive if I ever needed to use Windows. But then someone said something about some of the computers wouldn't let me do that, as in the case of HP which seems to be set up to boot only what it recognizes as Windows OS. 

I have found some more tutorials, by dedoimedo, that present a complete walk-through of installing Ubuntu alongside Windows 8. I have read through them and he makes it seem not so daunting or scary. 
 
If I went with an external drive to use for Ubuntu, the only thing I would need to change is the boot order in the UEFI (used to be BIOS) menu, to boot from the USB drive before the HD. Is that correct? Or would I need to disable Fast Boot and possibly SecureBoot as well, before installing Ubuntu?

Thanks ever so much.

---

### Post by oldfred on 2015-05-09
You still need to turn off Windows fast startup and fully shut it down each time.
You need to turn off fast boot in UEFI or else you may have difficulty getting into UEFI. And some vendors make it such that the only way to get into UEFI is from Windows so when Windows breaks you have same issue.
My motherboard had separate fast boot settings for cold boot, warm boot, and I could adjust timing. So I set cold boot as normal, and set warm boot as fast but with a 3 sec delay so I might be able to press a key to get into it.

With UEFI it is difficult to get grub to install to external drive. Again you have to copy grub to bootx64.efi.
You will just select ubuntu from UEFI menu as it will be on internal drive.

---

### Post by mattharris4 on 2015-05-09
I got into UEFI via Windows on my Toshiba.  However, Toshiba (as of early 2014) still includes a recovery partition on the hard drive and allows/has a program to make backup Win 8.1 DVDs or USB sticks with the pertinent drivers on it along with Windows.  If needed a person can still force-boot a DVD or USB stick from the boot screen if the HD fails completely or you replace the HD for some other reason.  If Windows completely fails I would have to reinstall both Win and Lubuntu as the install process for Win completely formats the HD (other than the recovery partition) before reinstalling Win but at least the computer isn't expensive junk if the HD fails or Win gets borked.  I think I ran across another way to get into the UEFI the traditional (BIOS) way right after it starts booting but I don't recall the instructions.

---

