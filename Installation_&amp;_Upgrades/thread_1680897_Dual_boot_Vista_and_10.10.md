---
title: "Dual boot Vista and 10.10"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by Zebra_ on 2011-02-03
I am trying to make my machine dual boot with windows Vista and Ubuntu 10.10. I have two hard drives in the machine, one with Windows Vista already installed, but I want to install Ubuntu 10.10 on the other hard drive (it's blank right now) and then be able to select which operating system I want to boot into. Should I just boot from the Ubuntu 10.10 cd and then install it on the blank drive, reboot, and then it will work? Or, is there something that I have to do to the Vista or Ubuntu or both boot files? Something that I need to do in CMOS? Please assist if you are able, thanks :)

This is the solution that worked for me:

> **YesWeCan said:**
> Having Ubuntu and Vista on separate HDs is a very good idea.
The way I would approach this is:
1. Disconnect the Vista HD
2. Install Ubuntu on the other
3. Shut down and reconnect the Vista HD
4. Tell the bios to boot the Ubuntu HD first
5. Reboot into ubuntu and from a terminal run 'sudo update-grub'. This tells Grub to scan your HDs and add Vista to the boot menu.
6. Reboot and select Vista from the Grub menu

---

### Post by kansasnoob on 2011-02-03
Thank you for preparing in advance, a little planning certainly saves a lot of problems later on. I'd first quickly browse the Release Notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

Specifically:

> In dual boot installs, side-by-side partitioning can be overridden by the user, resulting in data loss. After selecting the "Install alongside other operating systems" option, clicking on either the "Use entire partition" of "Use entire disc" buttons will override the side-by-side partitioning and result in a loss of data.  

I made sort of an overview of the new installer here in post #1 and post #15:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

After browsing that a bit I'd next recommend giving the Live CD a spin choosing to Try Ubuntu rather than installing just to see how it works with your hardware. It will run considerably slower than the installed OS but it's worth the time.

While running the Live CD I'd next familiarize myself with Ubuntu device designations. The Live CD has Gparted pre-installed, it's found in System > Administration. This guide gives a decent overview of using Gparted:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

In your case you want to be certain to understand how Ubuntu recognizes your drives and partitions. I should also point this out to you:

[http://ubuntuforums.org/showthread.php?t=1659542](http://ubuntuforums.org/showthread.php?t=1659542)

It's not a big deal, and I've never seen it on my own machines, but you should always be mindful of any possible fluke in behavior to prevent installation errors. 

You should also consider possible partitioning schemes. By default the installer generally creates a layout like this, with only root "/" and SWAP partitions:

[ATTACH]182625[/ATTACH]

Many people like to create a separate /home partition similar to this:

[ATTACH]182626[/ATTACH]

The advantage to having a separate /home is that you can reinstall, still selecting and setting the mount point on the existing /home but NOT formatting it, therefore leaving your existing data in tact.

Regarding booting with two drives I'd assume you know that hard disc boot priority can usually be changed in the system BIOS, eh? Ubuntu's bootloader is Grub, since Karmic we've used a version most often referred to as grub 2.

By default the Ubuntu installer will install grub to the MBR of drive #1, aka: /dev/sda. And in the new installer the ability to change the grub installation location is only available if using the "Specify partitions manually (advanced)" option. So, if you want to leave the Windows drive's MBR untouched you'll want to install grub to the MBR of the Ubuntu drive.

Have I confused you yet? If you need more specific instructions please post the output of the following commands using the Ubuntu Live CD:

```
sudo parted -l
```

```
free -m
```

BTW that's a lower case L at the end of the first command.

---

### Post by Zebra_ on 2011-02-03
> **kansasnoob said:**
> Regarding booting with two drives I'd assume you know that hard disc boot priority can usually be changed in the system BIOS, eh? Ubuntu's bootloader is Grub, since Karmic we've used a version most often referred to as grub 2.



Yes... I know this -_-, but what I want to be able to do is to have something come up after POST that will allow me to use arrow keys to select which Operating System that I want to boot into. I am wondering if this is possible, or does it depend on the BIOS that you have?

---

### Post by kansasnoob on 2011-02-03
> **Zebra_ said:**
> Yes... I know this -_-, but what I want to be able to do is to have something come up after POST that will allow me to use arrow keys to select which Operating System that I want to boot into. I am wondering if this is possible, or does it depend on the BIOS that you have?

Grub does just exactly that. Right after the system/BIOS screen passes the grub menu will appear and you'll have the choice of booting either Ubuntu or Windows. Now, the new grub 2 menu may display more options than you like but there's a new tool for editing the menu:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

There are other options, in particular EasyBCD, but I hate it! I've found the newest versions of grub 2 to be quite superior to any other bootloader in all but a very few corner situations (less than 1%).

Actually, if you're comfortable fiddling with hardware (static safeguards and all), you could just disconnect the Windows drive, install Ubuntu to it's drive using the "Entire disc" option then, after a reboot to be sure Ubuntu boots, choosing to shutdown. Then reconnect the Windows drive, set the Ubuntu drive to boot first in BIOS and once Ubuntu boots just run the command:

```
sudo update-grub
```

NOTE: When I say, "if you're comfortable fiddling with hardware (static safeguards and all)", I mean what I say! The word "comfortable" means you know how to adjust jumpers if these are both IDE drives sharing one cable, how NOT to damage connectors, how not to kill components with static charge, etc!

---

### Post by Zebra_ on 2011-02-03
I'm not that much of a noob bro... I've just never done this type of dual boot before. I tried to install Ubuntu first but then I had Ubuntu on IDE0 and Vista on IDE1 and Ubuntu wouldn't see Vista at all soooo not really sure what went wrong there...

---

### Post by Cavsfan on 2011-02-03
You should go for the custom option in the middle of the screen when installing and pick your partitions. 
All I have is 2GB - 2048MB for swap (2nd physical partition) and the rest as ext4 on "/" for everything else (on a 3rd partition with windows 7 on partiton 1).
As you probably know you can have 4 physical partitions per HD and then as many logicals as you desire.
You might be interested in the tutorial in my sig. It creates a nice bootup screen (GRUB) that is good for dual booting.

---

### Post by Cavsfan on 2011-02-03
And you have to install windows first and Ubuntu 2nd. Windows likes it that way.

---

### Post by YesWeCan on 2011-02-03
> **Zebra_ said:**
> I am trying to make my machine dual boot with windows Vista and Ubuntu 10.10. I have two hard drives in the machine, one with Windows Vista already installed, but I want to install Ubuntu 10.10 on the other hard drive (it's blank right now) and then be able to select which operating system I want to boot into. Should I just boot from the Ubuntu 10.10 cd and then install it on the blank drive, reboot, and then it will work? Or, is there something that I have to do to the Vista or Ubuntu or both boot files? Something that I need to do in CMOS? Please assist if you are able, thanks :)

Having Ubuntu and Vista on separate HDs is a very good idea.
The way I would approach this is:
1. Disconnect the Vista HD
2. Install Ubuntu on the other
3. Shut down and reconnect the Vista HD
4. Tell the bios to boot the Ubuntu HD first
5. Reboot into ubuntu and from a terminal run 'sudo update-grub'. This tells Grub to scan your HDs and add Vista to the boot menu.
6. Reboot and select Vista from the Grub menu

The only caveat is that I am not entirely sure whether Vista will throw its toys out of its pram if it is not on the 1st boot drive. Windows 7 has a more mature attitude and works fine.

If Vista refuses to boot then it gets messy because you have to install Grub into the MBR of the Vista disk. The mess occurs if you ever upgrade Vista as it will throw its toys out of its pram if the MBR is not the MS one.

---

### Post by Zebra_ on 2011-02-03
Right, thank you YesWeCan, this is exactly what I want to do. However, as of right now (I have just finished step 5 in your instructions), I am not seeing the GRUB menu for any selection when I boot into Ubuntu (for instace, the option to run memtest, etc). Will this change now that I have done this?:

```
student@dualboot:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
```

---

### Post by YesWeCan on 2011-02-03
Looks good. Vista should appear in the menu on the next boot. Fingers crossed.

Grub is a little too clever. It hides its boot menu if there is only 1 OS to choose from. Even though there is a always a memtest to choose. This behaviour can be changed in the /etc/default/grub file (see the Ubuntu Grub web page: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)). Once you have both Ubuntu and Vista in the list the menu should appear.

---

### Post by kansasnoob on 2011-02-03
> **Zebra_ said:**
> **[COLOR="Red"]I'm not that much of a noob bro...[/COLOR]** I've just never done this type of dual boot before. I tried to install Ubuntu first but then I had Ubuntu on IDE0 and Vista on IDE1 and Ubuntu wouldn't see Vista at all soooo not really sure what went wrong there...

But I must always be careful :D

Quite often what seems very simple to me results in breakage for others. Like don't rebuild your computer on a shag carpet :lolflag:

---

### Post by Cavsfan on 2011-02-03
> **YesWeCan said:**
> 5. Reboot into ubuntu and from a terminal run 'sudo update-grub'. This tells Grub to scan your HDs and add Vista to the boot menu.

That command does not scan HDs or add anything to the boot menu.

It just makes any changes you have made "stick".

---

### Post by kansasnoob on 2011-02-03
> **Zebra_ said:**
> I'm not that much of a noob bro... **[COLOR="Red"]I've just never done this type of dual boot before. I tried to install Ubuntu first but then I had Ubuntu on IDE0 and Vista on IDE1 and Ubuntu wouldn't see Vista at all soooo not really sure what went wrong there...[/COLOR]**

I'm also not that much of a noob anymore but that was not a situation requiring reinstallation!

Noobs or not we all make mistakes :p

---

### Post by YesWeCan on 2011-02-03
> **Cavsfan said:**
> That command does not scan HDs or add anything to the boot menu.

It just makes any changes you have made "stick".
Yes it does. Read the manual.

---

### Post by kansasnoob on 2011-02-03
> **Cavsfan said:**
> That command does not scan HDs or add anything to the boot menu.

It just makes any changes you have made "stick".

That statement is just DEAD WRONG!

If os-prober is installed grub-pc (aka grub2) does search and find most OS's when 'update-grub' is run!

There are a few corner issues like XFS filesystems, etc. Most of those are easily dealt with!

Don't slam something you don't understand!

---

### Post by Cavsfan on 2011-02-03
> **YesWeCan said:**
> Yes it does. Read the manual.

If you make a change to one of the files in **/etc/grub.d/**, **sudo update-grub** will update grub making the changes permanent.
It does not do anything else...

---

### Post by kansasnoob on 2011-02-03
> **Cavsfan said:**
> If you make a change to one of the files in **/etc/grub.d/**, **sudo update-grub** will update grub making the changes permanent.
It does not do anything else...

You're dead wrong!

---

### Post by Cavsfan on 2011-02-03
> **kansasnoob said:**
> That statement is just DEAD WRONG!

If os-prober is installed grub-pc (aka grub2) does search and find most OS's when 'update-grub' is run!

There are a few corner issues like XFS filesystems, etc. Most of those are easily dealt with!

Don't slam something you don't understand!

Maybe you need to rethink this... 
If **/etc/grub.d/30_os-prober** or **/etc/grub.d/10_linux** is made executable and you do not execute **sudo update-grub**, the entries will **not** show up. If you do execute **sudo update-grub**, they **will**.

If you make those files unexecutable and do not execute **sudo update-grub**, the entries **will** still show up, but if you do execute **sudo update-grub**, they will **not**.

It just updates grub and makes any changes "stick" or "take" or makes them permanent.

Ask **oldfred**, **drs305** or **ranchhand** and see what they have to say...

---

### Post by Cavsfan on 2011-02-03
Post any questions you have about how GRUB2 works right here in **drs305**'s **GRUB 2 Guide** and see what he has to say.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

I am not arguing about what **sudo update-grub** does any more...

---

### Post by drs305 on 2011-02-03
"update-grub" is a stub for "grub-mkconfig -o /boot/grub/grub.cfg"; "grub-mkconfig", with the above option, is the command actually run. 

"grub-mkconfig" generates the Grub2 menu by running commands in accordance with the instructions in */etc/default/grub* and executable scripts in */etc/grub.d*, as is stated in *grub.cfg*. If every file in */etc/grub.d* is made unexecutable, the result of "update-grub" is a *grub.cfg* file with only this content:
> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
(The top title and header information in the Grub2 menu is hard-coded and cannot currently be changed by the user.)

When "update-grub" is invoked, the entire *grub.cfg* file is rewritten. It starts with the above cited section and is built in sections by the */etc/grub.d* scripts (following any */etc/default/grub* instructions). You can see the script responsible for each section of *grub.cfg* by inspecting the comments. 

[LIST]
[*]No changes to *grub.cfg* will be made until "update-grub" is run as root.
[*]Any script in */etc/grub.d* which is executable is included and the entries it generates will be included in the new *grub.cfg*. 
[*]Any script in */etc/grub.d* which is not executable will not be included. Any previously-generated entry from that section will disappear.
[*]If a command invoked by a script is not found, only portions of that script may appear. For instance, if *os-prober* is not installed, the *30_os-prober* script will run, it's section will be included in *grub.cfg*, but it will not find other operating systems.
[*]If */etc/grub.d/30_os-prober* is executable, the *os-prober* command is found, and there is no entry in */etc/default/grub* disabling it, the entire system will be searched for other operating systems which, if found and understood by Grub2, will be included in the menu.
[/LIST]

Added: If I've misstated or made confusing entries in any of my guides I am always receptive to making corrections or improvements.

---

### Post by kansasnoob on 2011-02-03
One last thing, even if Cavsfan doesn't read or doesn't care, there are a number of executables in "/etc/grub.d". You can see what is, or is not, executable adding "-l" to the "ls" command like this:

```
lance@lance-desktop:~$ ls -l /etc/grub.d
total 36
-rwxr-xr-x 1 root root 4444 2011-01-20 11:28 00_header
-rwxr-xr-x 1 root root 1416 2011-01-20 11:05 05_debian_theme
-rwxr-xr-x 1 root root 4843 2011-01-20 11:28 10_linux
-rwxr-xr-x 1 root root 6605 2011-01-20 11:28 30_os-prober
-rwxr-xr-x 1 root root  214 2011-01-20 11:28 40_custom
-rw-r--r-- 1 root root  483 2011-01-20 11:28 README

```

In that case "os-prober" is executable so "update-grub" will add anything "os-prober" finds"!

Really, no kidding ;)

---

### Post by Zebra_ on 2011-02-04
OK everyone, I didn't get a chance to reply yesterday, but YesWeCan's suggestion worked. After sudo update-grub the boot menu came up on startup allowing me to select Ubuntu, Recovery mode, memtest, and Vista. This is what I wanted to do, so thank you to everyone. Also loling at this nerd war on my thread :D

---

### Post by Cavsfan on 2011-02-04
> **drs305 said:**
> "update-grub" is a stub for "grub-mkconfig -o  /boot/grub/grub.cfg"; "grub-mkconfig", with the above option, is the  command actually run. 

"grub-mkconfig" generates the Grub2 menu by running commands in accordance with the instructions in */etc/default/grub* and executable scripts in */etc/grub.d*, as is stated in *grub.cfg*. If every file in */etc/grub.d* is made unexecutable, the result of "update-grub" is a *grub.cfg* file with only this content:

(The top title and header information in the Grub2 menu is hard-coded and cannot currently be changed by the user.)

When "update-grub" is invoked, the entire *grub.cfg* file is rewritten. It starts with the above cited section and is built in sections by the */etc/grub.d* scripts (following any */etc/default/grub* instructions). You can see the script responsible for each section of *grub.cfg* by inspecting the comments. 

[LIST]
[*]No changes to *grub.cfg* will be made until "update-grub" is run as root.
[*]Any script in */etc/grub.d* which is executable is included and the entries it generates will be included in the new *grub.cfg*.
[*]Any script in */etc/grub.d* which is not executable will not be included. Any previously-generated entry from that section will disappear.
[*]If a command invoked by a script is not found, only portions of that script may appear. For instance, if *os-prober* is not installed, the *30_os-prober* script will run, it's section will be included in *grub.cfg*, but it will not find other operating systems.
[*]If */etc/grub.d/30_os-prober* is executable, the *os-prober* command is found, and there is no entry in */etc/default/grub*  disabling it, the entire system will be searched for other operating  systems which, if found and understood by Grub2, will be included in the  menu.
[/LIST]

Added: If I've misstated or made confusing entries in any of my guides I  am always receptive to making corrections or improvements.

Drs305, thanks for the clarification of what the command does and doesn't do. :)


> **Zebra_ said:**
> OK everyone, I didn't get a chance to reply yesterday, but YesWeCan's suggestion worked. After sudo update-grub the boot menu came up on startup allowing me to select Ubuntu, Recovery mode, memtest, and Vista. This is what I wanted to do, so thank you to everyone. Also loling at this nerd war on my thread :D

I am glad you got it worked out. :smile: 
If you ever need to know anything about GRUB2 look for drs305's many guides and tutorials on the subject.
He knows more than anyone else I know of.

---

