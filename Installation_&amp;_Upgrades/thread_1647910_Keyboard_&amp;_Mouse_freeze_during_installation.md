---
title: "Keyboard &amp; Mouse freeze during installation"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by jimmy8910 on 2010-12-18
Hi,
I'm trying to install ubuntu 10.04 on my system, however my keyboard & mouse freezes while i'm trying to install it. At the max i can go upto Step 4 during installation and after that my mouse and keyboard freezes and i can do nothing but reboot the system manually.
I tried it 4 times already and it doesnt go beyond step 4 (froze at step 3 once),
I tried unplugging and re-plugging the mouse & keyboard, but that didnt help either.
However it installed fine on my Dell Inspiron without any such issues, now i want to install it on my desktop, but i'm unable to do so.


Here are my system specs :-

Motherboard : Intel D102G
Processor : Intel Pentium D CPU 2.66GHz
RAM : 1022MB DDR2
Graphics Card : NVIDIA GeForce 7300GS 512MB
Hard disk : 160GB Segate
Keyboard & Mouse : PS/2

---

### Post by sikander3786 on 2010-12-18
Step 3 is the timezone and step 4 is the keyboard layout page?

The same disc succeeded in installation on another system but it is still worth to check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

And if that doesn't help, on the same page linked above, there are some boot options under F6 menu. Actually 6 of them. I would recommend to try all of them one by one and any of them might work magically.

Keep posting ;-)

---

### Post by jimmy8910 on 2010-12-18
@sikander3786
Thanks for the quick response

Step 3 is time zone, step 4 is partition & keyboard layout is step 2.

I'll try out the other  boot options under the F6 menu and update if that worked out.

---

### Post by sikander3786 on 2010-12-18
If step 4 is partitioning, I am wondering if your HDD might be cause a problem for the installer.

Go to Applications > Accessories > Terminal and post the output of this command.

```
sudo fdisk -l
```

Before we dig deep into partitioning problems, you need to make sure that your Disc is not defected as mentioned in the above post..

---

### Post by jimmy8910 on 2010-12-18
I checked the disc, the result came out just fine.

> Check finished: no errors found

Press any key to reboot your systemThis is what i got, then again i tried to start ubuntu to access terminal to type in the command u gave and it again froze, this time during the loading itself.

---

### Post by jimmy8910 on 2010-12-18
I'm unable to type the command in the terminal, once i enter into the terminal and hit ANY key, my keyboard and mouse freeze and that particular key keeps repeating itself in an infinite loop.

---

### Post by sikander3786 on 2010-12-18
Try with some other keyboard if available. It might just be a hardware issue. Or check your keyboard. Some key might have stuck down and causing improper function. OR debris under the keys....

---

### Post by jimmy8910 on 2010-12-18
I did check at that time to see if the key remained pressed, but that was not the case, i'm sure the keyboard is working fine as i've booted into windows and there is no such problems with the keyboard at all.

I had to reboot manually and when i tried again, the same thing happened, this time it repeated D in an infinite loop instead of S.

---

### Post by sikander3786 on 2010-12-18
My bet would be some broken cabling or some internal problem with the keyboard. My money on hardware problem... Sometimes one OS doesn't seem to care about an issue and the other one recongizes it. That might be the case here with Windows and Ubuntu.

---

### Post by jimmy8910 on 2010-12-18
I dont understand why my mouse freezes, if that were working, i could had closed the terminal, but it just freezes everything.

---

### Post by jimmy8910 on 2010-12-18
I typed the whole command in gedit, there was no problem at all, but as soon as i copied the text and opened the terminal, my keyboard and mouse froze again.
Now i have no other option but to reboot manually.

---

### Post by sikander3786 on 2010-12-18
> **jimmy8910 said:**
> I typed the whole command in gedit, there was no problem at all, but as soon as i copied the text and opened the terminal, my keyboard and mouse froze again.
Now i have no other option but to reboot manually.
Strange. Terminal doesn't like your keyboard while Gedit 'loves' it. I feel stumped just like you.

However, I would still suggest to try with some other keyboard. Probably a USB one and see if that makes any difference.

If you can't do that, go to Applications > Accessories > Terminal and fire up Gparted. Take a screen shot and post it.

---

### Post by jimmy8910 on 2010-12-18
No good, as soon as i open up my terminal, everything freezes, i'll just have to try out with another keyboard.

---

### Post by jimmy8910 on 2010-12-18
Facing the same problem with a USB keyboard too, unable to type anything in terminal.

---

### Post by sikander3786 on 2010-12-18
> **jimmy8910 said:**
> Facing the same problem with a USB keyboard too, unable to type anything in terminal.
So that might not be a hardware issue.

Did you try the F6 boot parameters?

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by jimmy8910 on 2010-12-18
Ya, i'm trying that.
The acpi=off setting resulted in a blank screen with cursor and no respone for like 15mins.

Using noapic i was able to run the command u gave and this is the output i got.
Its not freezing anymore.

```

ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x2940293f 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS 
/dev/sda2            5223       19456   114334605    f  W95 Ext'd (LBA) 
/dev/sda5            5223       12339    57167271    7  HPFS/NTFS 
/dev/sda6           12340       19456    57167271    7  HPFS/NTFS 
 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x9dd9fc36 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               2      121601   976752000    f  W95 Ext'd (LBA) 
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS 
/dev/sdb6           60802      121601   488375968+   7  HPFS/NTFS 

```

---

### Post by sikander3786 on 2010-12-18
Partitions look ok.

So with noapic enabled, did you try to start and run the installer? Does it still get stuck at step 3-4?

---

### Post by jimmy8910 on 2010-12-18
Nope, as u said that it might be a problem with the hard disk, i didnt try the installation as it would be of no use if the hard disk is faulty.

Could u please tell me what is this noapic and do i have to turn it off all the time i reboot?

---

### Post by sikander3786 on 2010-12-18
noapic = Disable the "Advanced Programmable Interrupt Controller (APIC)". 

Try to install Ubuntu. If successful, you may need to make that change permanent by edit /etc/default/grub later. We'll surely try to guide you there. But check the installer first.

Regarding your partitions, I just worried if they were partitioned as Dynamic disk in Windows and Linux has a problem regarding Dynamic partition. But you've got basic partitions so nothing to worry there.

Hope your installation would be successful.

Good Luck!

---

### Post by jimmy8910 on 2010-12-18
I've reached till the last step without any problem.
I'll be replacing the 40GB windows partition completely with ubuntu(100mb for boot, 4gb for swap, 20 for / and the rest for /home) so i wouldn be having any other operating system to retrieve data from all other partitions. So i wanted to make sure if its safe to run the system on a long run with noapic.

---

### Post by sikander3786 on 2010-12-18
noapic shouldn't cause a problem in the long run either (it isn't known to cause a problem). But nobody can guarantee you. You can Google it yourself and gather some information.

[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by jimmy8910 on 2010-12-18
Ya i did google a bit on that and saw the wiki article on it too, hopefully it wouldn be a problem in a long run.

The installation completed and asked for a reboot, when i clicked on reboot, after a few lines, the cd ejected and i got a huge list of errors,
this is one of em, only the second digit and the last sector address changed throughout.
```

[ 4192.425429 ] end_request: I/O error, dev sr0, sector 505648

```

Pressed and entered and the system rebooted and got stuck on the load screen.

---

### Post by jimmy8910 on 2010-12-18
Had to reboot manually and now again my keyboard and mouse freezes and i'm unable to enter my password to login into the system.

---

### Post by sikander3786 on 2010-12-18
Press and hold down Shift key from Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to the end of the line that contains "quiet splash". Type "noapic" (without quotes) at the end of that line after the words "quiet splash". Press Ctrl + X to continue boot. Can you see the desktop now?

---

### Post by jimmy8910 on 2010-12-18
I did as u said above and entered the password at login screen,
got an error message "Could not update ICEauthority file /home/jimmy/.ICEauthority"

---

### Post by sikander3786 on 2010-12-18
That shouldn't happen. I haven't seen that error before :confused:

Please reboot and try again.

---

### Post by jimmy8910 on 2010-12-18
I just closed it and it booted in normally.
I'm on the desktop now, should i make any more changes or am i good to go?

---

### Post by sikander3786 on 2010-12-18
Yes one more change :-)

Edit /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

And type noapic in between the quotes in this line.

```
GRUB_CMDLINE_LINUX=""
```

Save and close. Run update-grub (You've to run this everytime you make changes to Grub).

```
sudo update-grub
```

Reboot and see. You should not need to edit the Grub line manually afterwards ;-)

---

### Post by jimmy8910 on 2010-12-18
Done and it didnt freeze, but i still get that error after entering my password.

What if there are grub updates?
Do i have to redo these changes after there is an update for grub?

---

### Post by sikander3786 on 2010-12-18
No you won't need to redo after Grub updates as it would offer you to keep your old /etc/default/grub and you'll say 'Yes' ;-)

Regarding that ICEauthority issue, I wonder if it is a permissions/ownership problem. Post the output of this command.

```
ls -l /home/jimmy/.ICEauthority
```

---

### Post by jimmy8910 on 2010-12-18
Way too many problems, there is no audio either.
If i click on the volume icon, mute all option is grayed out and if i click on sound preferences, it shows "waiting for sound system to respond" and nothing happens even if i leave it for about 10mins.

The output for that command is
```
-rw------- 1 jimmy jimmy 0 2010-12-18 22:55 /home/jimmy/.ICEauthority
```

---

### Post by sikander3786 on 2010-12-18
That seems pretty normal. Did you install the updates during the install? I am wondering if that problem has something to do with a recent update as I've found a very recent similar thread here.

[http://ubuntuforums.org/showthread.php?t=1648148](http://ubuntuforums.org/showthread.php?t=1648148)

Anyhow, if you keep on getting that error, you can start a new thread.

And that sound issue also needs to go to Multimedia sub-forum.

For the moment, if you feel satisfied, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Gotta go now :-)

---

### Post by jimmy8910 on 2010-12-18
Nope, i still have around 297mb of updates pending, however it did download some language packages.

The issue regarding the freeze problem has been solved, so i'd better make a seperate thread for these two issues.

Thanks a lot for all the help and assistance :)

---

