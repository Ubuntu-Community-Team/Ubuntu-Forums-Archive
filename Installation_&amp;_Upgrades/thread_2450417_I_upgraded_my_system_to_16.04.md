---
title: "I upgraded my system to 16.04"
date: 2020-09-13
forum: Installation &amp; Upgrades
---

### Post by hebdave on 2020-09-13
Hi, With Ubuntu 16.04 it said you can clear all obsolete files on  upgrading my install. I selected "no" as it said it would take a period over night to do it. However can you tell me how to do that now. And will Bleachbit do the same job if I do that at root perhaps? Also I keep get a box flashing up saying there is a problem or an error with my system or a failure to do something internally. I can't remember exactly what it said sorry. But I suspect it is common and is meant to be ignored and stopped somehow. This was happening on my prior install of Ubuntu LTS 14.04 and has just carried over onto 16.04 with the same problem. Also one final thing is it said there was a further upgrade than 16.04 midway into the upgrade- it asked me if I wanted that- so I selected "yes" and saw some things flash up on the terminal saying 18.04 I think it was. However it then proceeded with 16.04 terminal things after. I suspect it thinks its a possible upgrading facility to 18.04 and not actually the new upgrade to this? However it did say upgrade too...so I don't know why I did not get 18.04. Thanks for creating new versions guys if your on here- its most appreciated. I hope there is relevance in all the queries to upgrading as that’s the posted area I have aimed for. I am a beginner to Ubuntu in the sense I don't try and learn anything much other than what I click. I forgot how to use the terminal and think I had to enter my unique "something" before I enter a command. I appreciate your help. Thanks very much.

---

### Post by Impavidus on 2020-09-13
I have to dig into my memory for 16.04. That was 4 years ago, I'm on 20.04 now. BTW, 14.04 reached end of life over a year ago, unless you paid for extended support. Best to upgrade before a release reaches end of life.

The upgrade from 14.04 leads to 16.04. Only when that upgrade is complete, an upgrade to 18.04 should be offered. The upgrade from 18.04 to 20.04 should have been available by now, but it seems to be delayed. But long chains of upgrades aren't recommended anyway. Better to fresh install.

It's normal that problems aren't solved by release upgrades (other than problems caused by poor drivers). So if you had some error on 14.04, it's not surprising you still have it on 16.04.

I never tried bleachbit. I always use synaptic for package management and keep things clean manually. It should be able to show you any leftover packages from an old release. Look for the status "Installed (obsolete or manually installed)".

---

### Post by SeijiSensei on 2020-09-13
I'd create a clean installation of 20.04 myself. 16.04 will be obsolete within the year.  Rather than worry about stale files, just install from scratch. Make sure you back up your personal files first.

---

### Post by hebdave on 2020-09-14
I always tend to worry about grubs and multi-boot with having windows. I think I used a windows 3rd party partition tool to get that right as well at one stage. I assume you can overwrite Ubuntu and re-partition on a new install. And hopefully if your clever enough add a grub there and then too. So you don't have to use a live Cd or a memory key afterwards to get ubuntu back with a multi booting grub then. If it is simpler these days it would be good to do. I don't mind upgrading to 18 only if there is a clever way to make sure that can retain things correctly. For example I could of used there clear obsolete files during the upgrade they offered. This in itself should mean there is an obsolete file removal command for the terminal after if required? In which case that might solve the error messages to if I am very lucky. Although probably not as its a system error. I assume it automatically updates on the fresh install. It might need an update to fix anything possibly? A few questions here but I really am a beginner I promise. Just trying to sound like I am not at the moment- Bare with me :smile:

---

### Post by TheFu on 2020-09-14
there is no obsolete files removal command. the installer just overwrites existing files, but only if the new files and old filenames are the same. If you want to delete cache files or temporary files, then you can manually do it or use tools.  In the end, they will just run an '*unlink*' command - unlink is the programming function that "rm" uses.

You should backup any data you want to keep, then install a fresh 20.04.  Upgrading may have made sense in 2016, but not anymore.  Too much has changed underneath since 14.04.  Conflicts will happen. Don't wait so long next time is my advice.  Perhaps 4 yrs ago, someone would remember all the little issues in going from 14.04 --> 16.04, but not any more.  Today, people remember little issues going from 18.04 --> 20.04. 

Keep using only LTS releases, unless you want to be forced into a new OS every 6 months. The next 3 releases each have 9 months of support and you'll need to move from 20.10 --> 21.04 --> 21.10 before the next LTS, 22.04, gets released.  Today, if you don't have a really, really, really, good reason to do anything else, 20.04 is the release to be installed.

---

### Post by rsteinmetz70112 on 2020-09-14
> **Impavidus said:**
> 
I never tried bleachbit. I always use synaptic for package management and keep things clean manually. It should be able to show you any leftover packages from an old release. Look for the status "Installed (obsolete or manually installed)".

I tried bleachbit and found it was a pretty blunt instrument. It seems really easy to do a lot of damage. I backed away quickly.

There are several ways to find unsupported packages . The simplest seems to be```
 ubuntu-support-status 
```
but you may need to install the package.

---

### Post by mastablasta on 2020-09-17
> **hebdave said:**
> I always tend to worry about grubs and multi-boot with having windows. I think I used a windows 3rd party partition tool to get that right as well at one stage. I assume you can overwrite Ubuntu and re-partition on a new install. And hopefully if your clever enough add a grub there and then too. So you don't have to use a live Cd or a memory key afterwards to get ubuntu back with a multi booting grub then. If it is simpler these days it would be good to do. I don't mind upgrading to 18 only if there is a clever way to make sure that can retain things correctly. For example I could of used there clear obsolete files during the upgrade they offered. This in itself should mean there is an obsolete file removal command for the terminal after if required? In which case that might solve the error messages to if I am very lucky. Although probably not as its a system error. I assume it automatically updates on the fresh install. It might need an update to fix anything possibly? A few questions here but I really am a beginner I promise. Just trying to sound like I am not at the moment- Bare with me :smile:

you can use the option to overwrite (not format) but that might leave issues as well. that is what happened to me when i tried to push Kubutnu 14.04 to 16.04. it had a major upgrade bug (basically it was imposisble to do it). so i used the install but don't erase option and it didn't work too well. so backup data and format it was. and it was a lot faster too.

since you are upgrading anyway, i would go with 20.04 and then remain on it for the next 5 years.

i was thinking the other day (and i am not sure if i am correct) but what would happen say if you only have /root (MBR parittion) or /root + EFI partition (UEFI) and all you do is:
1. boot into live session
2. delete system files found in /root and only config files in home
3. install using option without formatting the disk

that would keeps all the data files, but not /home files, desktop configuration and and apps, right? it would be like a fresh install with all user data still there? you could maybe even leave some application configuration and data files (e.g. like steam games)

or would something important get overwritten?

because i plan to run upgrade next year and then if things go wrong just do it like that rather than moving the user data to separate disk first, then format and install and then moving the data back.

upgrade overwrites old system files and adds any new files. while the old obsolete files are left there. at least i think it's the way it goes.

i did only 2 linux upgrades that were successful. about 6 got messed up.
on windows i did upgrade about 5 times, but last one i did was from 98 to XP. before that i did 3.11-95 and 95 to 98. so anyway a long time ago.
i see at work they mostly perform fresh install of windows 10 when they "upgraded" windows 7 and 8 PCs.
from experience, applications usually need a reinstall anyway unless they are self contained in a way of portable apps on windows or binary folders on linux. even if you move wine prefixes from old to new OS, they sometimes need additional setup on upgraded OS.

---

### Post by hebdave on 2020-09-30
Hi thanks very much. I have another question but please direct me if I need to use a different part of the Ubuntu forum to ask this question. I have managed to upgrade to 20.04.1 LTS. I had to go from 16 to 18 then to 20 by the upgrade root and it only offered 20 as available a few days ago. This was successful. I should mention I set my partitioning as half my computers storage along with windows. Multi boot is still working with the linux grub too. I have about 250 GB for Linux- however would this make it slow with an i3 processor on start up with not to much storage used? I am finding Hibernate takes about 2 and half minutes to get up and ready, about the same for a complete restart. I was asked if I wanted to delete the obsolete files on upgrading and I did so. I did not loose any needed data. I am not sure if they were overwritten if that's what you meant? oddly 18.04 was good at boot times from restart as well- so why is it not very good from 20.04? This is why I give you my information above just in case it could be useful. Maybe I can stop extra things loading up on restart and this will help hibernate as well- how though? I am windows user only with my knowledge sorry. I have little storage space used on linux as I only use it for surfing and helpful uses. So maybe it is actually restarting and not hibernating at all? The settings interface is set by me to use "hibernate" on power on and off. Is there any command I could use to check this out or set correctly on the terminal ? Any simple things I might utilise here ? Thanks. My Ubuntu knowledge is highly limited and I struggle to remember the word "terminal" and how to access it too. Ctrl alt T seems to get me there. Thanks I really appreciate your help and I hope this is not to much to ask. Thank you!

---

### Post by TheFu on 2020-09-30
> I have about 250 GB for Linux- however would this make it slow with an i3 processor on start up with not to much storage used?
250GB of storage is 10x more than a system needs, assuming it is allocated correctly.  The number isn't really useful to say anything about performance of a system.  Facts would be needed.

> oddly 18.04 was good at boot times from restart as well- so why is it not very good from 20.04?
20.04 is different code than 18.04. Behaviors are completely different. Settings are completely different.  Boot processes changed greatly between 14.04 to 20.04 with lots and lots of things that vastly changed. But it seems you aren't actually booting. You are using hibernation, which is completely different.

> help hibernate
Hibernation shouldn't be used. Windows abuses hibernation where it prevents access to NTFS storage by Linux systems since Win8 by not closing file systems properly when you request "shutdown."  This can lead to all sorts of problems.

If you want a system that is faster, the easiest answer is to replace a spinning HDD for a fast SSD.  NVMe SSD would be 10x faster than a SATA SSD, if the computer can support that.

If you stop using hibernation, there are some things you can do to make booting faster. Mainly it comes down to not starting programs that you don't use.  If you don't use bluetooth, then doesn't start the bluetooth subsystem. Stuff like that.  There are tools to see what is being started, how long each startup takes and how much it impacts overall boot time. Many things started at boot don't actually get in the way of you being able to login and start working, so it doesn't really matter.  You can google for all the reasons not to use hibernation on Linux. From a security standpoint it is a bad idea. There are lots of other reasons as well.

But each of these things are worth having 1 thread about here, since they are specialized questions.  For example, I usually don't try to help with any GUI questions because I don't use the same GUI that everyone else uses.

---

### Post by hebdave on 2020-10-03
Ok thanks I will give it some thought. I suppose I could downgrade again if I am not tech aware. Help hibernate I assume tells me what to do?

---

### Post by TheFu on 2020-10-04
Just saw this about improvements to hibernation. [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.10-Faster-Hibernate](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.10-Faster-Hibernate)  Don't know when this will make it into any Ubuntu. Probably 21.04. Don't know whether it will be back-ported to any other kernels.

I don't use hibernation because I care about security. It causes all sorts of security problems. On a dual boot system, I can see where hibernation by both Linux and Windows could end badly. I don't dual boot or hibernate, so perhaps I'm just being overly cautious.

---

### Post by hebdave on 2020-10-08
OK from another thread i got this info to then get my results for start up issues if there are any. I have elected to go a non hibernate root presently. So with below in mind what do I do? I have remembered how to use the terminal as shown below which is a decent start. Technically with microsoft windows 10 I use basic settings changes to do lots of basic things but I am not so good in understanding under the hood things in Ubuntu or linux. But I do recognise some terms from being here in the past at a basic beginning exploratory level I think.

sudo systemd-analyze blame
[sudo] password for davidpc: 
53.978s plymouth-quit-wait.service                                             >
22.384s dev-sda5.device                                                        >
21.600s networkd-dispatcher.service                                            >
17.300s snapd.service                                                          >
17.079s accounts-daemon.service                                                >
16.351s udisks2.service                                                        >
15.529s dev-loop10.device                                                      >
14.212s dev-loop8.device                                                       >
13.851s dev-loop0.device                                                       >
13.298s dev-loop9.device                                                       >
12.930s dev-loop5.device                                                       >
11.751s dev-loop2.device                                                       >
11.750s dev-loop3.device                                                       >
11.749s dev-loop1.device                                                       >
11.747s dev-loop7.device                                                       >
11.745s dev-loop4.device                                                       >
11.743s dev-loop6.device                                                       >
11.660s systemd-journal-flush.service                                          >
11.341s avahi-daemon.service                                                   >
11.336s NetworkManager.service                                                 >
11.143s polkit.service                                                         >
10.152s NetworkManager-wait-online.service                                     >
 9.990s switcheroo-control.service                                             >
lines 1-23

If indeed I can use a

---

### Post by TheFu on 2020-10-09
First, don't use sudo when there isn't any need, please.

Ouch.  I don't have a bunch of things you have in my list and the ones that do match up are 10-20x faster here.
**22.384s dev-sda5.device**
I think you have a hardware problem with storage. It could be a failing cable or HDD about to die. Getting really slow is a sign of a disk about to die.  How are your backups?  Check the system logs and SMART data ASAP.

On my 20.04 desktop:
```
$ systemd-analyze blame |grep plymouth
 530ms plymouth-quit-wait.service                           
  36ms plymouth-start.service                               
  18ms plymouth-read-write.service
```

Please post using code-tags. Things line up cleaner that way and are more readable.  You can edit the post above to fix that.  Please.
On my system, 
```
1.646s networkd-dispatcher.service
```
So, you definitely have a network problem too, if the HDD isn't the only problem, check the router port and cable. If the router hasn't been patched in the last 60 days, get new firmware.  If no new firmware exists and hasn't more than 6 months, it is time to get a better router with a vendor who patches their systems.  I see patches for my router every month, for example.  Routers are usually our first line of security from the nasty internet.  Which reminds me, I need to check my router for any available patches. There are about 30 updates available in this single package:
```
pkg	1.12.0_1	1.15.6	upgrade
```
They are mixed from a new kernel to new versions of  php and perl to some new versions of networking tools. I love seeing the details about updates.
There is a separate audit tool available in the router interface. Even after patching, there is 1 security flaw remaining.
*libxml2-2.9.10 is vulnerable*
I'll look for a patch in a week, but at least about 30 other known issues have been closed. Ah ... the power of using a F/LOSS router stack.

---

### Post by hebdave on 2020-10-11
Sorry I am a beginner I don't no how to use the terminal yet hardly. I copied and pasted the first command directly after sudo [COLOR=#000000]systemd-analyze blame I got from a forum elsewhere which seemed to work as I don't know how to do much more. Yours sort of worked I think when I put it in after my first command. But since I did not know what I was doing using a terminal its all based on fluke if I get something correctly entered by its usage. I could not use the 2nd command you recommend for example as a first command without anything else entered in the terminal [/COLOR][COLOR=#000000][FONT=&quot]1.646s networkd-dispatcher.service you wanted in there I presume and after something else perhaps too. Is there an easy beginner way of explaining what I am actually doing to do it ? I was saying I did not know about linux at the start and during this thread. So anything I do with the terminal correctly in entering what you tell me is based on luck in getting the exact command correctly placed within it. I got lucky with my first command [/FONT][/COLOR][COLOR=#000000]systemd-analyze blame in how I entered it in to get a response from the terminal. So I don't honestly know exactly what I am doing. Thanks for all the helpful answers but I need guidance in code placements. Using a Terminal I assume like windows would use command prompt( of which I don't remember how to use actually without guessing). I can only use interfaces and windows as you can tell in terms of computing. Thanks chaps. Let me know how to use your code.[/COLOR]

---

### Post by hebdave on 2020-10-18
Sorry that was to complex a response. I mean to say if I am to shorten the start loading time do I directly enter those in the terminal or slightly differently? I no how to use the terminal in the sense I can copy and paste things into it. The sudo command you don't always appear to use so it must mean a certain thing for certain situations, I am quite ill physically in terms of my length sitting on certain days. So reading through guides and understanding linux commands isn't going to be feasible. So I wondered if you could perhaps guide one bit at a time? Also what am I correcting better and why ?

For example here is my first problem on entering the first command by Thefu above

davidpc@davidpc-K53E:~$ $ systemd-analyze blame |grep plymouth
$: command not found
davidpc@davidpc-K53E:~$  530ms plymouth-quit-wait.service                           
530ms: command not found
davidpc@davidpc-K53E:~$   36ms plymouth-start.service                               
36ms: command not found
davidpc@davidpc-K53E:~$   18ms plymouth-read-write.service

Is it me do something wrong on entering for instance?

---

### Post by Impavidus on 2020-10-19
What TheFu gave you was not a sequence of commands to solve your problem. It was an example with output on a different machine, to show you what would be reasonable output. The first line, starting with the $, is the command (but not the $ itself, which is the prompt, left to indicate that this is the command). The remaining lines were output of this command.

It's possible that your problem is caused by hardware, which would mean that there's no way to fix it in software. Have you checked the health of your hard drive? Have you got backups of all your important files? Run an extended test of your harddrive and view the results. To interpret the result, it's best to monitor the numbers over time and not every hardware problem is easily detected with the smart test.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

