---
title: "upgrade to 9.10 boot problems"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by xsilvergs on 2009-11-23
I've just tried to upgrade to 9.10 and now I can't get into Ubuntu. I can see "Starting up" followed by login: all white text on a black background but the screen flashes and the HDD cycles. I can't type my password because of the flashing not every key stroke is recognised.

Any ideas please.

---

### Post by Land Rover Series 3 on 2009-11-23
Sadly, you're not the only one. Have a look around the forum and you'll see loads of other people have had exactly the same problem - so far without much of a meaningful response.

---

### Post by phillw on 2009-11-23
> **Land Rover Series 3 said:**
> Sadly, you're not the only one. Have a look around the forum and you'll see loads of other people have had exactly the same problem - so far without much of a meaningful response.


news to me..   okies... lets' herd everyone together & get it sorted.

1) can you boot from the LiveCD ?

From there, everything is possible & do-able.

Phill.

---

### Post by Land Rover Series 3 on 2009-11-23
Don't need to boot from a live CD ... I can still boot up into the previous system. One of my other posts includes the following...

Fortunately, when I boot up Grub gives me the following 2 main options...

Ubuntu, Linux 2.6.31-15-generic
     (this is the default, and the one that doesn't work)
Ubuntu, Linux 2.6.31-14-generic
     (this still works like a treat, like it always has)

Would really like to be able to (a) preferably, restore the system back to how it was before the upgrade made such a mess of it all, or (b) delete the first option from Grub and tell it to automatically boot up into the old system. Any way of doing either of these, preferably the first?

---

### Post by xsilvergs on 2009-11-23
@ phillw
Thanks for getting back.

From the live CD I can run the Try Ubuntu.
If I try to boot normally and ESC for grub I see Ubuntu 9.10 for three Kernels.
The 2.16.31-14-generic if selected will cause the screen to flash as mentioned above.
The 2.16.28-16-generic if selected will go as far as showing the desktop but the graphics then go funny. I have long enough to select Update and it tell me about Partial Upgrade before the graphics mess up.

Any ideas?

---

### Post by xsilvergs on 2009-11-23
Update.
Using the oldest Kernel and Recovery I was able ask it to repair broken packages and then it did the upgrade.
On rebooting into the new 2.6.31-15-generic the screen went back to flashing as reported in my first post but eventually that stopped and the desktop appeared.
Another reboot and this time a normal start.

The remaining problem seems to be the HDD cycles / continually accessed.

I will have another look tonight but does anybody have an idea what could cause this HDD symptom?.

---

### Post by molecule_splitter on 2009-11-24
hmm

i cant chose any kernels or modes...
it just says 

windows vista
ubuntu

in the boot screen.

how can i pick the .14 ?

thx anyway
molecule_splitter

---

### Post by phillw on 2009-11-24
I'm just asking for help on this one ... brb :p

Phill.

---

### Post by phillw on 2009-11-24
> Ok, well, if it's Grub 2, have him highlight Ubuntu, then "e". That should open an edit window with the commands visible. On the linux and initrd lines the kernel should be visible. In both lines, they can edit the line and replace -15 (or whatever) with -14, then boot.He's a very nice man. The above should allow you to boot into 14.

Regards,

Phill.
(Thanks dave :p)

/edit  Choosing the image to boot is covered here [COLOR=#CC0000]** **[/COLOR][https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

---

### Post by outdoorsman14 on 2009-11-24
Thanks Phill for sending me over here, I noticed in my issue that I have not updated the kernel yet. I am able to get into recovery mode and running an apt-get install update command gives me a list of 59 packages and 3 new installs which is the new kernel. I will give you an update this evening after doing the upgrade and seeing if that could fix my issues. Do you know if I can revert my display driver from the command line? It seems to me that running Envy seems to not have cause the issue, but if reverting is possible, that would at least eliminate that as an issue.

---

### Post by phillw on 2009-11-24
I recall a thread on video issue with the update - if you have problems, I'll go and have a dig round for it.

Regards,

Phill.

---

### Post by ak331 on 2009-11-24
Problem started when update manager installed kernel image of 15 instead of 14 and I lost windows, got stuck on grub and when reinstalled it lost windows xp completely. I think new kernel image is the problem and there are no broken packages on my system.

---

### Post by phillw on 2009-11-24
> **ak331 said:**
> Problem started when update manager installed kernel image of 15 instead of 14 and I lost windows, got stuck on grub and when reinstalled it lost windows xp completely. I think new kernel image is the problem and there are no broken packages on my system.

Getting your Grub back is covered here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Whilst the changes from 14 to 15 shouldn't cause any problems, people are experiencing problems. If you have issued the ```
sudo apt-get update
``` Then, you *should* be able to boot into 15.

If you still have problems, then you'll need to try the 'rebuild packages' from the recovery mode, that worked for at least one person. I'm not sure if it is a menu option, or you just get dumped to shell, if it's not a menu option, then [http://ubuntuforums.org/showthread.php?t=169013](http://ubuntuforums.org/showthread.php?t=169013)  has the instructions.

It worked for one person - as I don't have any problems with 15, it's a bit hard to work out what your problem is. :-\

Phill.

---

### Post by xsilvergs on 2009-11-24
Hi all,

Just to say I've sorted my problem. I have two hdd's both with two partitions, sda1 has Ubuntu and sda4 partition for file storage. The second hdd has an old Windows XP install on sdb2 ntfs and another ntfs partition for file storage labeled sdb5.

Strangley after the upgrade it could not mount sdb2. Although I can't mount sdb2 (and I don't really want to) a little bit of surfing came up with a fix and now the hd0 is quiet.

Hope this helps somebody.

Tony

---

### Post by phillw on 2009-11-24
Thanks for posting back - glad you're sorted :-)

Phill.
(Google *is* good, you gotta love it. Using a + before a word reduces the amount of stuff returned by telling it you want results only with that word in it.  +ubuntu  and +9.10  are cool things to put in search)

---

### Post by tmfries on 2009-11-24
xsilver, did you figure out how to get .15 out of grub and get .14 to boot automatically? Or better yet roll back the updates? I managed to boot using the .14 so I'm not dead in the water. Guess I'll try repairing the packages before I do anything.


UPDATE:  Went into .15 recovery mode. Selected "Repair broken packages". It does some stuff and then dropped me to a command line. I logged in and "sudo reboot now". When it came back up it was still flashing, so I gave it another reboot to no avail. Still flashing again. The second time I even gave it a couple minutes but nothing happened. Right now I'm operating out of .14 kernel so if anyone has a fix, I'd love to be the guinea pig.

---

### Post by phillw on 2009-11-24
> **tmfries said:**
> xsilver, did you figure out how to get .15 out of grub and get .14 to boot automatically? Or better yet roll back the updates? I managed to boot using the .14 so I'm not dead in the water. Guess I'll try repairing the packages before I do anything.


UPDATE:  Went into .15 recovery mode. Selected "Repair broken packages". It does some stuff and then dropped me to a command line. I logged in and "sudo reboot now". When it came back up it was still flashing, so I gave it another reboot to no avail. Still flashing again. The second time I even gave it a couple minutes but nothing happened. Right now I'm operating out of .14 kernel so if anyone has a fix, I'd love to be the guinea pig.


One of the toher threads reported that it took 2 re-boots to settle the system down. So, I guess there's no harm in trying that - give the system a little time to try and settle down tho'.

```
ps -ef | grep -v '00:00:00' > /tmp/f1; sleep 10; ps -ef | grep -v '00:00:00'> /tmp/f2 ; diff /tmp/f1 /tmp/f2

```

Will do a diff on what processes are active over a 10 second interval - you'll be able to see what processes are using processor time. I use it when my hard drive is having a busy time, for no apparent reason - It'll let you know what the process(es) is/are that are busy - from that you can get an idea of what is occuring.

Regards,

Phill.

---

### Post by outdoorsman14 on 2009-11-25
Performed the apt-get update through the recovery mode, but unfortunately it did not fix my issue. I still get the flickering login line and it it just continues you to that over and over again, almost like it is taunting me. Anyways, any other suggestions?

---

### Post by outdoorsman14 on 2009-11-25
UPDATE: In the EnvyNG program, I installed the ATI driver, which didn't work, but then I removed it with the same program and when I went to reboot, I get past the blinking login issue, but now none of the lines on the display line up properly. The picture is all distorted, but I know at what displays I am at so I can actually login into Ubuntu and my Ubuntu Netbook Remix table of contents and desktop appears, but again all distorted. I am also able to use the dropdown menu to shut down the computer, so it is just a display issue at this time, is there a driver I can download or revert the display that I screwed up with the other program, any suggestions?

---

### Post by phillw on 2009-11-25
> **outdoorsman14 said:**
> UPDATE: In the EnvyNG program, I installed the ATI driver, which didn't work, but then I removed it with the same program and when I went to reboot, I get past the blinking login issue, but now none of the lines on the display line up properly. The picture is all distorted, but I know at what displays I am at so I can actually login into Ubuntu and my Ubuntu Netbook Remix table of contents and desktop appears, but again all distorted. I am also able to use the dropdown menu to shut down the computer, so it is just a display issue at this time, is there a driver I can download or revert the display that I screwed up with the other program, any suggestions?

blimey ... some people have really been thru the wars on a minor bug-fix update to the kernel (Honest, they haven't done anything major) There's a sticky thread on video drivers etc lurking over here --->  [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)   It's, well, 'a busy thread' .. You should find the solution to your problem there.

I've still no idea why 15 has gone around breaking peoples computers - None of the people I know from the forums have had a problem with 15, It runs sweet & the only difference is that it says 15 at the end, instead of 14.

I'm really sorry for you guyz & galz for whom it is a nightmare - And myself and others on here wish we had a quick "HowTo" to get it sorted. :-(

Keep smiling, it WILL work.... may take a bit of time ... But, 6 months down the line you'll look back at this episode and go "Well, wasn't that *fun* (not)" 

Now, as a footnote - As I've missed it before - If you're running Wubi then I'm afraid the outlook does not look good. We can pull your data (emails / bookmarks / documents etc.) from the Wubi area, but we don't have a working solution to repairing one. If anyone is so affected, send me a private message and I'll talk you through it.

Regards,

Phill.

---

### Post by outdoorsman14 on 2009-11-25
Thank you for the help, I don't think my problem is related to the kernel upgrade, it happened before then, it was the Envy program that screwed it up. I'll try out that thread and see what I can find.

---

### Post by swalker23 on 2009-11-25
I would like to say I to have been experiencing the same issues.  Ubuntu logo pops up then goes to a flickering command prompt and after that few error type messages and the flickers stop.  I've tried the advice here and other posts but to no prevail.  Only thing that works is going back to 14.

---

### Post by phillw on 2009-11-25
Hi,

Ahh... that's what envy does. For things video why not pop over to the sticky thread at the top of this forum ? [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)  If it's vid related, chances are you'll meet people who either have a solution or are working on one.

(Has bog standard Motherboard Graphics)

Regards,

Phill.

---

### Post by outdoorsman14 on 2009-11-25
Well, I got the boot issues fixed. I have an intel video driver and EnvyNG changed the xorg.conf file to looking for the vesa driver. I changed it to an intel driver and voila, everything works again... except for one thing. My xserver now throws an error when trying to load the netbook-launcher. I can't remember what it said exactly, but I already tried to reinstall xserver and that didn't fix it, any other suggestions? All I have is my background, none of the menu's show up.

---

### Post by phillw on 2009-11-26
An update for Wubi users

Win7 and Wubi seem not to get too well together. However, for people with cursing flashers at the grub prompt, Drs has gone and had a 'play' and has proposed solution.

>  				 				**Re: sh:grub > desperation** 			
 			 			 		   		 		 		[SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

 	Quote:
 	 	 		 			 				# Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 			 		 	 	 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
 		                   		  		  		 		 			 				__________________
				[GRUB2]("https://help.ubuntu.com/community/Grub2") : [G2-Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") [G2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[G2-Tasks]("http://ubuntuforums.org/showthread.php?t=1302743") [DiskSpace]("http://help.ubuntu.com/community/RecoverLostDiskSpace")  
[Expand /]("http://ubuntuforums.org/showthread.php?t=1219270") [SUM]("http://ubuntuforums.org/showthread.php?t=818177") 			
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 1 Hour Ago at 06:24 PM.*

We do need someone to try this out & report back if it works.
One of the things holding us back, is that people are not posting back what they have done to fix their problem - It's really important that you take a couple of minutes to do so. It then helps everyone else.

Regards,

Phill.

---

### Post by k()()zmi4 on 2009-11-27
Hi to ALL!!!):P

I'm only a few weeks familiar with linux, and english isn't my native language, so pls 'cuse me for terminology/grammar mistakes...

Anyway, I've come across this problem as well yesterday. While playing with some compiz, xbmc settings (actually I'm trying to make a stable linux-based HTPC with a little candy)) , I noticed an update reminder and went for it (without even running' through its contents :oops:)
As it finished I ended up with similar problems, listed here and some other threads. I did have a functional grub though, with both kernel (recovery/regular) entries. At 1st misfortunate boot I went back to .14 and finished my updated xbmc setup :lol:. Then my curiousity started killing me and went to infinite reboots, forum searches etc. I did notice after managing to boot to console via .15 recovery and requesting gdm (or x server:confused:) to start there were several messages saying something 'bout the dispay init error (no displays found) and nvidia settings problem (by the way I'm running 8400GS, mentioned in several other posts with this problem).
Another thing I remembered is 1st/2nd (64/32bit) install issue I had with video. During installation from LiveCD I could only finish it using the safe graphics mode, otherwise ended up with a black screen (I'm not exactly using a monitor, but a plasma via av reciever, so guess 'could have been unrecognized resolutions or hdcp issues maybe?)
So I decided to go the simplest way and reinstall the 190.42 driver I already had in my downloads folder, since I came across that black screen again after runnin' "X -configure" set of commands.

Reinstallation of video driver did the trick for me! Oh I guess I should've posted a log of some kind, but not quite sure where to find it((

P.S.: sorry for offtop, and my noob nature, but could someone plz help me with starting 'nvidia-settings' hidden (in background, not sure 'bout the right term). I desperately need this since the settings for overscan compensation are applied when I launch it and them are vital 4 me with my hd-ready tv. I added it to autostart, but I don't wanna see the nvidia-settings window poppin' up on every system restart/logout. I guess there's an easier way, but no luck so far... Thanx in advance!

---

