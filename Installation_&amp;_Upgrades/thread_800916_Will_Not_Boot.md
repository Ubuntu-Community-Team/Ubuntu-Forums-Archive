---
title: "Will Not Boot"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by robertlinthicum on 2008-05-20
I successfully installed and updated 8.04 on my old Thinkpad.  Was running great for days, until I tried to install Thunderbird.  Either I or Thunderbird must have corrupted something or interfered with system files somehow, because now the machine won't boot, even in recovery mode.  The Ubuntu install disc won't boot it, either.  How can I format the disc to start over, so that I may reinstall Ubuntu from scratch?

I ran a disc maintenance utility on the disc, so system health is fine, and there are no known hardware problems.

---

### Post by tamoneya on 2008-05-20
can you give any errors.  How far can you get.  Did you load grub yet? If so you should be getting some sort of error that we can work with?

---

### Post by robertlinthicum on 2008-05-20
I get:

****************************************

GRUB Loading stage1.5.

GRUB loading, please wait...

Press 'ESC' to enter the menu . . .

Starting up . . .  

****************************************

(cut to crickets chirping)

If I press ESC to enter the menu, none of the three options get me anywhere.  When I try to boot off of the Ubuntu install disk, I get to the menus successfully, but none of the options can bring it back up.

---

### Post by kami_iwinaru on 2008-05-20
you might just have to wait
or
try reinstalling it

---

### Post by masonfoley on 2008-05-20
I can't imagine ho an install of Thunderbird would do this but I know where you're coming from in that Thunderbird was the last thing you remember working with before your system went on the fritz.

It appears GRUB can't get past stage 1.5.  From that, it appears it found the menu.lst file however, for some reason, it can't proceed to boot of the partition it's being told to boot off of.

You say the LiveCD won't boot either?  It "seems" unlikely but have you checked the connections on your drive(s) inside your box (both power and data cable)?  Perhaps they have become loose.  Perhaps you have multiple drives but one of them is no longer correctly connected?   Either that or it's possible that one of your drives might be failing, especially considering that the liveCD isn't able to load.

Some things to consider.  Let us know what you are able to find.

---

### Post by masonfoley on 2008-05-20
> **kami_iwinaru said:**
> you might just have to wait
or
try reinstalling it

Indeed...reboot and let it sit for a while.  Not that it should take any time at all but if your system eventually loads, that might point to a different problem.

---

### Post by robertlinthicum on 2008-05-20
I let it sit overnight, so I do not believe that this is related to any hardware issue.  I believe that this is a software issue.  The proximate cause was trying to manually load Thunderbird.  A hardware solution is not likely to be helpful, but thank you.

I may end up replacing the hard drive so that I will have at least a useable Thinkpad.  Not the straight line to my destination, but I do not see an alternative at this time.  And disks are cheaper than hours of software troubleshooting.

Feh.

---

### Post by robertlinthicum on 2008-05-20
Anybody know some shareware or freeware that would force a format? Please no Windows recommendations.

---

### Post by PmDematagoda on 2008-05-20
The [Gparted Live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") aught to help you format the hard drive.

---

### Post by robertlinthicum on 2008-05-20
> **PmDematagoda said:**
> The [Gparted Live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") aught to help you format the hard drive.
Downloading now, thanks very much.  Fingers crossed.

---

### Post by robertlinthicum on 2008-05-20
Soon I will post a pic of the screen I got when I tried to use GParted Live.  The menu properly appeared, but then I saw a few screens of commands scroll by, terminating on something about IRQ 11.  IRQ sharing is in effect, so I don't know if or why there would be a conflict, especially since I have made no BIOS changes.

(Posting pics when Imageshack gets its act together . . .)

---

### Post by robertlinthicum on 2008-05-20
This is the last screen that I'm seeing when attempting to use GParted Live:

[http://img387.imageshack.us/img387/6529/dsc0032rz7.jpg](http://img387.imageshack.us/img387/6529/dsc0032rz7.jpg)

---

### Post by robertlinthicum on 2008-05-20
This is the last screen I see when attempting to boot from Ubuntu's "recovery" mode:

[http://img293.imageshack.us/img293/9750/dsc0034ll8.jpg](http://img293.imageshack.us/img293/9750/dsc0034ll8.jpg)

[http://img387.imageshack.us/img387/6529/dsc0032rz7.jpg](http://img387.imageshack.us/img387/6529/dsc0032rz7.jpg)

---

### Post by jtrindle on 2008-05-20
Not seeing any screen shots here...[EDIT: probably the fault of my company's proxy].

Just to clarify... can you boot into the Live CD?  I couldn't tell if you were saying you couldn't boot the "first hard drive" option from the Live CD or couldn't boot the Live CD at all.

If you can boot from the Live CD and mount the hard drive, there's a good chance you can reinstall grub and recover:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by robertlinthicum on 2008-05-20
Hi, I can see the Live CD menu, but can't boot the machine with it (it fails).  I am beginning to think that the root of this is some sort of IRQ issue, but I can't see how anything I did could have caused it.

I wish you could see the pics through your firewall.

---

### Post by tamoneya on 2008-05-20
looking at the gparted liveCD screenshot the line that bothers me the most is: Clock source tsc unstable.  Have you been messing with any overclocking on your motherboard.  Also is it possible that your power supply is giving out.  If you arent getting enough power to your processor and other crucial system components it will become unstable.

---

### Post by PmDematagoda on 2008-05-21
robertlinthicum:- Please don't put such big pictures in posts since they are not allowed. I have removed the IMG tags and just left the links intact which should be enough.

---

### Post by robertlinthicum on 2008-05-24
I have tried everything and the machine will not boot.

Since I can't figure out how to format the drive and start an Ubuntu reinstall from scratch, I am considering popping the drive out of the Thinkpad and into a drive enclosure, and formatting it that way.

There are 120gb notebook drives available for about $65, so I might go that route; that way I would get more capacity in the process.

Question:  Who here thinks successfully formatting (or replacing) the HDD will give me a machine that will accept a new installation of Ubuntu?

P.S.  Manual installations of Thunderbird are risky, I'm a case study for that . . .

---

### Post by animefan82 on 2008-05-24
have you tried using grub?
That is, booting from liveCD, choosing shell then

find /boot/grub/stage1

I take it you know how grub works. If not:
1. sudo grub
2. find /boot/grub/stage1
   -returns (hdx,y)
3. root (hdx,y)
4. setup (hdz) , z is where you want grub to be loaded
5. quit

When it comes to grub, I generally try "resetting" it by the abovementioned commands...

---

### Post by robertlinthicum on 2008-05-24
> **animefan82 said:**
> have you tried using grub?
That is, booting from liveCD, choosing shell then

find /boot/grub/stage1

I take it you know how grub works. If not:
1. sudo grub
2. find /boot/grub/stage1
   -returns (hdx,y)
3. root (hdx,y)
4. setup (hdz) , z is where you want grub to be loaded
5. quit

When it comes to grub, I generally try "resetting" it by the abovementioned commands...
That was actually my first course of action.  Thinkpad will not from LiveCD (see aforeposted links, above).

---

