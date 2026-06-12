---
title: "Reboot after Install Hangs on GRUB"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by Soarer on 2006-04-11
Hi All,
After a blinding success yesterday, installing Ubuntu for the first time, I thought I'd try it again today on a different PC.
This is a Compaq Evo epc with 512MB, a 40 GB IDE disk, P4 2.4 GHz (I think) and an ethernet card and not much else.
Install went the same as the first machine (similar spec, bigger disk & different manufacturer) but after the reboot, it says:
GRUB Loading Stage1.5
GRUB Loading please wait

and hangs. I have tried the Super Grub Disk (Ubuntu is great - really easy to create an iso disk on my first install) and it hangs too at 'Stage 2'.

So I thought it might have an old BIOS (its about 4 years old) and partitioned the disk so the boot partition was only 5 GB (using Herman's instructions) but after another install its still the same.

Does anyone have any useful pointers for me please? I used to be a SysAdmin (on System III mind) so I'm not scared of terminal sessions so don't hold back just becuase I'm a Ubuntu/Linux noobie :)

Thanks.

---

### Post by Monster_user on 2006-04-11
Can you boot to a terminal session?

cd to '/etc', and 'vi', or 'view' your '**/etc/grub.conf**'. Press type ':quit' to exit. If have changed anything, you will have to press "Esc", and use ':quit!' instead. Oh, you press "Insert" to begin editing, and ':write' to save.

Make sure that all entries are pointing towards your latest kernel. cd to '/boot', and do an 'ls' to check for the kernel version.

I do not remember how to update the menu after a change. You can check the manual via 'man grub', or 'man grub.conf'.

I suspect that somehow your boot order was incorrectly detected, and now seems to have "changed" since the install. As a result the root drive is set wrong. It should probably be '/dev/hda1', with the image being '/vmlinuz', and initrd being something like '/boot/ubuntu-kernel-image-i386-2.6.xx-17' I am not sure what it is exactly. I run Dapper (Ubuntu 6), but I am on XP right now.

---

### Post by Soarer on 2006-04-12
Hi Monster_user,
Thanks for the reply. I looked for the files (grub.conf etc.) but I don't have them in /etc on the working or the non-working installation. I do have menu.lst in /boot/grub & edited the first line (after all the comments) to point to my boot partition (/dev/discs/disc0/part1) but get the same hang.

I then tried installing Dapper but get the same again.

I then downloaded the live CD (of Dapper) which will boot OK & bring up the normal desktop, but it won't recognise my mouse so I can't use it to search around the file system. This PC has no PS2 ports - keyboard & mouse have to be USB (or on a PS2-USB adaptor). The Live CD session will see the keyboard but not the mouse!
So what I think I need  to know is if the boot partition above is likely to be the correct one (its the one that is listed first during the Live CD boot for example) and which files I need to edit to ensure GRUB gets its kernel from there.
A pointer to anywhere this is documented would be fine, too.
Thanks.

---

### Post by Monster_user on 2006-04-12
I use Lilo, not Grub. So I had to look up the info. 

I found a GREAT post on the subject.
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

Use the instructions in the second thread. I recommend those, as your less likely to erase your data.

1. Pop in the Live CD, boot from it until you reach the desktop. *(You can use this method from the install CD, but no instructions are listed.*
2. Open a terminal window or switch to a tty *(Ctrl-Alt-F5, Ctrl-Alt-F7 to switch back to the desktop)*.
3. Type "grub"
3a. Type 'find /boot/grub/stage1'
3b. Type 'find /sbin/init'

4. Type "root (hd0,1)", or whatever your harddisk + boot partition numbers are ([i]My /boot is at /dev/hda5, which translates to hd0,5 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by Soarer on 2006-04-12
Thanks Monster_user - that is a great thread. I didn't get that far back with my 'grub' search - thanks for pointing it out.

That looks like it should work. I'll give it a try in the morning & report back (not quite back into the 'burning the midnight Unix oil' yet - it'll come :)).

---

### Post by Soarer on 2006-04-13
Hi again,
I have followed the instructions, started a shell and typed 'grub' - got to the grub prompt.

'find /boot/grub/stage1' gives Error 15 - File not Found.

It doesn't seem to see my disk at all.

[Edit] If it helps, I am now running Dapper Live CD and Dapper is installed, but not working, on my sysyem. I have no other OS on there, or anything I need to save.

---

### Post by Soarer on 2006-04-13
Hmmm.
Now followed the instructions on the Wiki: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28after%29%7C%28recover%29%7C%28windows%29%7C%28install%29](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28after%29%7C%28recover%29%7C%28windows%29%7C%28install%29)

Got down to 'Troubleshooting' :( 

Everything in there *appears* to work. although I had to go through 'Recovering Manually' as '/sbin/grub-install /dev/hda' fails.

Still, 'root (hd0,0)' and 'setup (hd0)' worked OK.

Then I edited /boot/grub/menu.lst as specified to
'root (hd0,0)'  -  which worked above
'kernel /boot/vmlinuz....  /dev/discs/disc0/part1' etc.

(also tried it without the /dev/discs etc.)

In both cases, still no change - hangs on:
'GRUB Loading, please wait' - no error or anything.

Any more threads that might help please?

---

### Post by siew on 2006-04-13
Try to have open your cdrom device before grub shows its menu. Enter to your favorite kernel, and then see that the system now boots ok. (cdrom device open at boot).

The same happened to me, and with this trick the system boots ok. I still don't know why that happens..

---

### Post by Soarer on 2006-04-13
Hi Siew,
Yes - the CDROM drawer is open at boot (or non-boot in this case).

Its all over very quickly:

[B]Searching for Boot Record from CDROM.. Not Found
Searching for Boot Record from IDE-0.. OK
GRUB Loading Stage 1.5.

GRUB loading, please wait[/B]

and that's it. Even if I press [ESC] really quickly I don't get a menu or anything.

Thanks for the tip though - I'm sure it will help someone :)

---

### Post by Soarer on 2006-04-22
OK - its been interesting trying to get this machine to boot :( 
I tried all the GRUB reinstall options I could find - still the same error. Then I tried installing LILO instead - but it wouldn't write to the MBR. This may be the root of the problem with both GRUB and LILO. I hope to investigate more. I considered buying a new HD to see if this one - which is a few years old and has had WIN2003 and XP on it at various times - was broken but that might not have made any difference and felt like it was admitting defeat.
So today I found GAG in this thread [http://www.ubuntuforums.org/showthread.php?t=159298&highlight=gag](http://www.ubuntuforums.org/showthread.php?t=159298&highlight=gag) and checked it out at Herman's page ([http://www.users.bigpond.net.au/hermanzone/p12.htm](http://www.users.bigpond.net.au/hermanzone/p12.htm)) which gives lots of great information and the link to get GAG ([http://gag.sourceforge.net/)](http://gag.sourceforge.net/)).
Downloaded, burnt the ISO (how easy is that in Ubuntu!) and booted from it on the other machine. Instant success!
I've written it to the hard disk but I haven't as yet rebooted. Just enjoying the wonderful Dapper on here.
Thanks to Herman for the post & Sergio Costas Rodriguez for GAG.

---

### Post by Herman on 2006-04-22
Hello, Soarer, you are welcome!
      Thanks for saying thanks! It really does make everyone's day a happier one!  I just maintain my web-site for a hobby because I'm not good enough to know how to do anything better. (And I'm still only learning how to do that).
The whole Ubuntu community really rocks! From forum administrators, moderators, members who dedicate their time to answering posts, people editing the Official Ubuntu Wiki to the actual open source and Ubuntu software developers themselves, everyone puts in a huge effort. No wonder we're growing by a thousand members per day or more some days!
A simple 'thank you' now and again does help make it all worth-while, so I'd like to thank everyone too!
     Thanks big brothers and little brothers and big sisters and little sisters.
From Herman :D

---

### Post by Monster_user on 2006-04-23
Glad you got it working.

---

