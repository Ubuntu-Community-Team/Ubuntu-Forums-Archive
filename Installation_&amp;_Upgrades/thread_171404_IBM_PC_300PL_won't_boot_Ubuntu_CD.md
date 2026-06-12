---
title: "IBM PC 300PL won't boot Ubuntu CD"
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by Sgt.Boobi on 2006-05-06
Hi!

This is my first ubuntu thread! :) I'm quite new i Linux/Ubuntu so if you decide to answer please keep it quite simple ;)

Well my problem is that i got an IBM "Personal Computer 300PL" with the "model number" 6862 from my brother and it simply [SIZE="4"]**WON'T boot the Ubuntu CD**[/SIZE] (or any other bootable CD, example WinXP etc.). 

I've updated the computers BIOS to a version released somtime in mid 2001 (it's an old computer running a PIII 500MHz) and there's no place to change some kind of boot order wich is really strange. I'm not new to BIOS settings and this computer really confuses me. When I installed WinXP wich it's running on now, i used a bootdisk. But i can't possible find a Ubuntu bootdisk though i've searched both the site and the forum for it.

Does anyone have a solution for this problem?

Thanks in advance!

// Sgt.Boobi :confused:

---

### Post by RavenOfOdin on 2006-05-06
Oh boy. I wouldn't be surprised if this has anything to do with it. . .

[http://www.intel.com/pressroom/archive/releases/in011800.htm](http://www.intel.com/pressroom/archive/releases/in011800.htm)

---

### Post by ronnieredd on 2006-09-07
The link to the intel site is dead. I tried a seach on the site for ibm 300pl and just 300pl with 0 results.

I just aquired one of these 300pl desktops and also don't know where to make it boot from the CD. Anyone else have any ideas?

---

### Post by cstudent on 2006-09-07
I had one of these models about a year ago. I had to have it for a class and put Gentoo on it. I ended up finding a bootup linux floppy to get it to install, but when I was telling the instructor about it, he had me put the CD in and start the boot. He then hit a key to make it actually boot from the CD. He said he had come across it before. Unfortunately, I can't remember if it was the esc key or a function key. Anyway, try playing with that idea when it starts to boot. I no longer have the pc to try it out myself. I fried the motherboard. :rolleyes:

---

### Post by Thruston on 2006-10-09
To get the IBM PC300 to see the CD you need to get into the BIOS settings and change the boot up device.

You have to hold down the F1 key during the power on cycle to get at the Configuration and Settings program.   

From the user manual...

[I]To start the Configuration/Setup Utility program:
 1. Turn on your computer. If your computer is already on when you start this procedure, you must shut down the operating system, turn off the computer, wait a few seconds until all in-use lights go off, and restart the computer. (Do not use Ctrl+Alt+Del to restart the computer.)

 2. When the Configuration/Setup Utility program prompt appears in the lower left corner of the screen during startup, press F1. (The Configuration/Setup Utility program prompt appears on the screen for only a few seconds. You must press F1 quickly.)

 3. If you have not set an administrator password, the Configuration/Setup Utility program menu appears on the screen. If you have set an administrator password, the Configuration/Setup Utility program menu will not appear until you type your administrator password at the password prompt and press Enter.

See “Using a power-on password” on page 67 and “Using an administrator     password” on page 71 for more information.

The menu you see on your computer might look slightly different from the menu shown here, but it will operate the same way.
                              Configuration/Setup Utility
                               Select Option:
                               System Summary
                               Product Data
                               Devices and I/O Ports
                               Start Options
                               Date and Time
                               System Security
                               Advanced Setup
                               ISA Legacy Resources
                               Power Management
                               Save Settings
                               Restore Settings
                               Load Default Settings
                               Exit Setup
[/I]
You want to fiddle with the "Start Options" menu.

One of the benefits of getting an IBM system is that they are well documented.  You can get all the old PC300 manuals here:

[http://www-307.ibm.com/pc/support/site.wss/product.do?subcategoryind=0&familyind=50025&brandind=11&doccategoryind=0&modelind=0&doctypeind=8&validate=true&partnumberind=0&sitestyle=lenovo&template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&operatingsystemind=49980&machineind=55478](http://www-307.ibm.com/pc/support/site.wss/product.do?subcategoryind=0&familyind=50025&brandind=11&doccategoryind=0&modelind=0&doctypeind=8&validate=true&partnumberind=0&sitestyle=lenovo&template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&operatingsystemind=49980&machineind=55478)

---

### Post by SanjoEel on 2007-08-15
I am bumping this thread up because I am having the same problem on an old IBM that I am trying to install Linux on. I have changed the boot order in the BIOS but it still won't boot from a CD (except a Win 98 install CD, recognized the CD at boot and installed 98 no problem) I have tried several different distros, and nothing will boot from a CD. :(
Am I stuck having to boot from a floppy or what? I'm confused on this one....
Thanks,
Jason

---

### Post by SanjoEel on 2007-08-17
Anyone have any ideas on this? Thanks!

---

### Post by whackattacker on 2007-12-01
I know that this is an old topic, but I found the answer and wanted to share it.

OK, you're all gonna kick yourselves in the head for this, I found this forum looking for the same answer, and..... it's right in front of you. The trick is, IBM has this little thing hidden in plain sight. When you start your computer, push the F1 button and it offers you the setup menu, which is control-s (or if you wait long enough, it will just go there anyway). In the menu is the **start options**..select that, and hit **enter**. HERE'S WHERE EVERYONE INCLUDING MYSELF GETS LOST.......BUT, BELIEVE ME, IT'S RIGHT THERE! The very first line says "STARTUP SEQUENCE" ----- That's not a title, that's a selection!!!!! All you have to do is hit **enter**, and the screen you're looking for is there. You can choose first, second, third, and fourth boot devices.  
Unlike the rest of the items on the start options menu, this one has no choices behind it, so it looks like a title to the page. Plus they left a blank line under it, separating it from the rest of the options.

Don't forget to hit "save settings" when you get back to the config/setup menu!!!!

---

### Post by SanjoEel on 2008-01-17
Thanks, I'll give that a shot!  Welcome to the forum.

---

### Post by f1r31c3r on 2008-04-01
> **whackattacker said:**
> I know that this is an old topic, but I found the answer and wanted to share it.

OK, you're all gonna kick yourselves in the head for this, I found this forum looking for the same answer, and..... it's right in front of you. The trick is, IBM has this little thing hidden in plain sight. When you start your computer, push the F1 button and it offers you the setup menu, which is control-s (or if you wait long enough, it will just go there anyway). In the menu is the **start options**..select that, and hit **enter**. HERE'S WHERE EVERYONE INCLUDING MYSELF GETS LOST.......BUT, BELIEVE ME, IT'S RIGHT THERE! The very first line says "STARTUP SEQUENCE" ----- That's not a title, that's a selection!!!!! All you have to do is hit **enter**, and the screen you're looking for is there. You can choose first, second, third, and fourth boot devices.  
Unlike the rest of the items on the start options menu, this one has no choices behind it, so it looks like a title to the page. Plus they left a blank line under it, separating it from the rest of the options.

Don't forget to hit "save settings" when you get back to the config/setup menu!!!!

holly sh****t i spent nearly an hour trying to look for this, if it is was there before i decided to look around see if others had the problem. i will be checking this first thing tomorrow morning i am gonna kick myself really hard if this is true lol.

ill post a link back tomorrow on the outcome of this, i kept returning to this menu again and again like a broken record and im thinking now i am sure i seen that and yes it is a title and its not bold like the rest of the options it looks exactly like the menu title ill report back tomorrow on a defo with this but thank you in advance if your right:guitar::lolflag:

---

### Post by nowin4me on 2008-04-01
Try this
Wubi is a program that install's Linux WITHOUT wiping your orginal OS of ypur hard drive and is genraly more easy. Download here
[http://wubi-installer.org/](http://wubi-installer.org/) 

With Wubi you can install the following so far:
[LIST]
[*]Ubuntu
[*]Kubuntu
[*]Kubuntu-KDE4
[*]Xubuntu
[/LIST]

It installs it straight from the net on to your hard drive check out my link for more info
[http://ubuntuforums.org/showthread.php?p=4631268#post4631268](http://ubuntuforums.org/showthread.php?p=4631268#post4631268)

---

### Post by mmccaghrey on 2008-05-13
> **whackattacker said:**
> I know that this is an old topic, but I found the answer and wanted to share it.

OK, you're all gonna kick yourselves in the head for this, I found this forum looking for the same answer, and..... it's right in front of you. The trick is, IBM has this little thing hidden in plain sight. When you start your computer, push the F1 button and it offers you the setup menu, which is control-s (or if you wait long enough, it will just go there anyway). In the menu is the **start options**..select that, and hit **enter**. HERE'S WHERE EVERYONE INCLUDING MYSELF GETS LOST.......BUT, BELIEVE ME, IT'S RIGHT THERE! The very first line says "STARTUP SEQUENCE" ----- That's not a title, that's a selection!!!!! All you have to do is hit **enter**, and the screen you're looking for is there. You can choose first, second, third, and fourth boot devices.  
Unlike the rest of the items on the start options menu, this one has no choices behind it, so it looks like a title to the page. Plus they left a blank line under it, separating it from the rest of the options.

Don't forget to hit "save settings" when you get back to the config/setup menu!!!!

Thank you whackattacker. It is so simple when you get told it. I knew what I was looking for but ignored it because I thought it was a title.

It now boots off the CDROM, but unfortunately the install fails because at the "Detect and Mount CDROM" stage because it can't find it in dev, but that's another story...

---

