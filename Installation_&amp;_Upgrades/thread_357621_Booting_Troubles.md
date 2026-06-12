---
title: "Booting Troubles"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Smoko on 2007-02-09
I've recently installed Ubuntu Edgy Eft. I've tried several times, and haven't been able to access it after the initaial install.

The first time, I used GRUB. After rebooting I got and error, I cant remember which one it was exactly but a google search showed that it didn't like the file system it was on, or trying to load.

So, I reinstalled and started fresh only installing Lilo this time. After resetting too load Ubuntu for the first time, Lilo just loaded with L 01 (It kept addind 01s to the end). I've had that problem with Slackware, and installing the GAG bootloader seemed to have fixed it. But it didn't this time.

I'm still using the Lilo install currently it's along side Windows XP. I've set XP up with WinGRUB, and get Error 19(Google shows it as error 18 though). The error means this:
```
Error 18: Selected cylinder exceeds max supported by BIOS
```

I've seen suggestions about moving my Linux partition closer to the start of my hard drive, but I don't think it should be all that important (and don't have enough free space for doing it either). Also, Slackware worked on the exact same partition as Ubuntu is now. The only difference being the OS that was installed.

So, my question is this. Does anyone have an idea on how I can fix this, or can I use the Alternate install CD to load the installed Ubuntu like you can with Slackware?

---

### Post by Herman on 2007-02-09
Smoko? Hey that's a good username! :) Beertime would be even better! He-he, :)

Okay then, what kind of BIOS do you have and what size is your hard disk and is a new one that you have had added to the computer later?

Grub error 18 is a grub error message that can mean a few different things, so it's impossible to give someone any exact instructions about what to do.
I have read of some people checking in their CMOS (BIOS settings), and finding that they had LBA turned off. That's something you can check, some people have solved their error 18 problem by enabling LBA.

Some other people have solved it by shrinking their Ubuntu partition so that it fits within the 137 GB limit.

Others have updated their BIOS with a BIOS flash from their motherboard manufacturer's website. If you look carefully and be ready to hit your pause key as your computer is booting you might see some exit on your monitor telling you your BIOS version or date. If not, you should be able to find out by looking around in CMOS, (BIOS settings). Then you can google your motherboard manufacturer and check to see if there is a free BIOS upgrade there you can download to update your BIOS with. (BIOS flash).

I get grub error 18 myself now and again in one of my computers since I added a second hard disk to it. It works okay most of the time, and my BIOS is reasonably modern and should be able to handle hard disks twice or four times the size of the ones I have, so error 18 can be misleading too.

It's odd that Slackware can work on it but Ubuntu can't. Maybe none of those ideas will help, but I don't know what else to suggest really.
I hope you can solve it and use Ubuntu.
Regards, Herman. :)

---

### Post by Smoko on 2007-02-10
Thanks for your reply Herman. I got bored and tired of trying to fix it, and decided to try giving reinstalling another go. Only this time I deleted my linux partitions and let Ubuntu decided how it wanted them to be. GRUB installed into the MBR with no troubles, and booted perfectly. Except now after logging in, everything loads and then it kicks me out again.

I tried using the fail safe session, and it said it found another version running and then exited. So, I think it's loading multiple instances of the GDM for some reason. Anyone can feel free too reply here with a fix if I haven't posted that I've fixed it yet.

My computer specs are as follows:
Intel Pentium 3, 733mhz.
224Meg of RAM
160Gig hard drive(58.8Gig WinXP install(NTFS), 70.6Gig Data Storage(NTFS), 30.5Gig Ubuntu Install(ext3) and 635Meg of swap space)
Voodoo Banshee video card, with 16meg of on board RAM.
D-Link DWL-G510 wireless NIC
And I'm not sure of my sound card or motherboard.

I'm still not sure why letting Ubuntu select how its partition and the swap one were set up worked, but I'm still happy it did either way.

---

### Post by Smoko on 2007-02-10
I gpt a little bit further into the system last night. If I booted in recovery mode, it wouldn't kick my out, but I couldn't use my keyboard or mouse(after starting X11 of course). But I could boot into the failsafe terminal on a normal boot.

From there I could create a user, log out of the terminal and then login with a failsafe GNOME session with the new user. The only catch was I couldn't do much while in there, it only worked once per new user and closing the 'Unable to load GNOME Settings daemon' error box would randomly log me out again or leave me alone. I tried reinstalling, but that ruind the copy of GNOME I had in my MBR even though I told the installer to not touch it. I did have an idea on how I could possibly avoid the login loop, and that was by having ubuntu boot into run level three(That's the terminal only?) and start X11 manually like is needed with booting in recovery mode. I haven't got an accesible Ubuntu install at the moment to try it though, but it might be a valid suggestion for anyone else with this problem to try, at least untill the is a fix for it anyway.

I've also seen lots of other people having the login loop troubles after using the 6.10 installer or ubgrading too it. So I'm downloading Kubuntu 6.06, because no one seems to have this sort of trouble with 6.06 and I would of converted to KDE anyway.

---

