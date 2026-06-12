---
title: "grub rescue help!"
date: 2017-04-12
forum: Installation &amp; Upgrades
---

### Post by 2bvd on 2017-04-12
[LEFT][COLOR=#222222]Hi everyone![/COLOR]
[COLOR=#222222]So I have a pretty serious problem with my laptop and I hope someone can help![/COLOR]
[COLOR=#222222]It&#8217;s a dual boot system with windows 10 and Ubuntu 14.04 lts, at least I think Ubuntu is still on there. I started the dual boot with installing 12.04 lts which went fine. When I finished the upgrade to 14.04 however, the system needed to restart, which it wouldn&#8217;t do.It also refused to shut down so I shut it off manually. It didn&#8217;t like this because when I started it again it said &#8216;error: file not found, grub rescue:&#8217;. [/COLOR]
[COLOR=#222222]I came across other people with a similar problem however my situation seems to be a bit different because I am not able to boot from a CD or USB. All I have is grub rescue. Adding to that, it seems certain commands just don&#8217;t work. [/COLOR]
[COLOR=#222222]I think I successfully set the prefix and root to the extent that when I enter the command &#8216;set&#8217; it says: [/COLOR]
[FONT=Liberation Serif]prefix=(hd0,msdos5)/boot/grub
[/FONT][FONT=Liberation Serif]root=hd0,msdos5[/FONT]
[COLOR=#222222]However,when I try the next command &#8216;linux&#8217; it says &#8216;unknown command&#8217;.[/COLOR][COLOR=#222222]When I try &#8216;insmod normal&#8217; and &#8216;insmod linux&#8217; it says &#8216;file not found&#8217;[/COLOR]

[COLOR=#222222]I also tried some other commands, with the following results:[/COLOR]
[/LEFT]
&#8216;[FONT=Liberation Serif]ls/&#8217;: ./ ../ lost+found/ etc/ media/ bin/ boot/ dev/ home/ lib/ mnt/opt/ proc/root/ run/ sbin/ vmlinuz srv/ sys/ tmp/ usr/ var/initrd.img cdrom/ initrd.img.old vmlinuz.old[/FONT]


[LEFT][COLOR=#222222]&#8216;[FONT=Liberation Serif]ls&#8217;: (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2)(hd0,msdos1)[/FONT][/COLOR]

[COLOR=#222222]Again,I hope someone can help! I have the feeling that it is &#8216;simply&#8217; a matter of setting the correct path(s), but so far I have been unsuccessful.[/COLOR]
[COLOR=#222222]I tried the commands with the USB stick connected and changed the prefix and root but this was unsuccessful as well.[/COLOR]
[COLOR=#222222]I&#8217;d really like to set the paths and be able to enter both systems again.Does anyone have any suggestions?[/COLOR][/LEFT]

---

### Post by oldfred on 2017-04-12
What brand/model system?
You mention originally 12.04, was that BIOS or UEFI. UEFI was pretty new back then.

Did you have separate /boot partition or any other separate partitions?

       grub rescue:
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg
OR:
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot 

If you cold boot, or full power down and if laptop remove battery, and then hold power switch for 10 sec or so, can you boot Ubuntu installer flash drive.

---

### Post by 2bvd on 2017-04-13
Thanks for your reply! It's a five year old Toshiba Satellite c670-13q, BIOS. I created a partition (root) and used another already in existence for swap. Could this have something to do with the problem (I am not an expert on the matter)?  
 

 Unfortunately, I already tried removing the battery and pressing the power button with no effect. I just can't seem to boot from CD or USB.  
 

 I don't have the laptop with me at the moment but I will try the commands tomorrow, although the command 'linux' does not work; it simply says 'unknown command'.

---

### Post by oldfred on 2017-04-13
If you used Something Else to install, did you install grub2's boot loader to drive like sda, not to a partition like sda5?
If you installed to a partition, you may have old copy of grub in MBR. And if you installed to flash drive, then you may have corrupted it, so it is not bootable.

Just about only way to fix is use f12 to boot flash drive, or perhaps make new bootable flash drive.

---

### Post by 2bvd on 2017-04-14
I used Something Else to install and installed it to a partition (sda5).....I tried (again) removing the battery and using USB but nothing works... it seems the only way in is through grub rescue but the commands don't seem to work or I can't find the right commands...

I'm thinking maybe I can remove the hard disk and hook it up to another computer; fix it that way?

---

### Post by oldfred on 2017-04-14
That can also work.

I find it best to have several flash drives, at least one with a full install and others with various repair tools/versions.

---

### Post by 2bvd on 2017-04-16
Finally I'm in! Taking out the CMOS battery and the laptop's battery _simultaneously_ restored my access to BIOS. So I was able to boot from CD and USB again which allowed me to fix the issue...Thanks again for your help!

---

### Post by Paddy Landau on 2017-04-16
> **2bvd said:**
> Finally I'm in!
Fabulous!

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others who might have the same problem.

---

