---
title: "Installation Hangs at &quot;Select and Install Software&quot;"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by rodj on 2006-12-09
I am completely new to Unix/Linux/Ubuntu but very eager to "make the switch". However, I can't get it to install.

I am trying to install 6.1 from the alternate install CD (ubuntu-6.10-alternate-i386.iso). I had previously tried with the standard CD and after various problems discovered the requirement to use the alternate CD when RAM is less than 192MB or so.

So I am now doing a "text mode" installation booting from the alternate CD. The installation starts off seemingly fine - it asks me various questions about the keyboard, partitions the hard drive, etc. It makes it quite far but eventually gets to a point where I have a screen titled "Select and Install Software" and a progress bar that always hangs at 6%. This happens every time I try the install.

Things I have tried:

-- verified the CD - it checked out fine.
-- installing in "OEM" mode. I don't know what that is, but it gives the same problems.
-- installing to a command prompt. That works, I get a command prompt and can do various basic commands like help, pwd, etc., but I don't know how to do anything from there.

Can anyone suggest things I can do to get more information to help diagnose the problem? Are there log files, etc. that I could refer to or post here for someone to look at?

It seems as if some particular part of the software installation is causing problems. Is there a way to do small pieces at a time to isolate the problem? Can I do some sort of manuall install from the command prompt?

Specs on my machine are listed below.

Thanks in advance for any suggestions,
Robert

Machine Specs:
Dell Dimension XPS T450
PhoenixBIOS 4.0 Release 6.0
BIOS Version A07
System Memory 128MB
Pentium III 450Mhz 512KB cache RAM

---

### Post by budgie9 on 2006-12-09
Have you tried the alternative install options? I think they are under F3 or try the F1 help option

---

### Post by rodj on 2006-12-10
Thanks for the suggestions. They got me further along, but still not all the way there. I had not seen the options to install in "expert" mode, which gave me what I wanted: the ability to selectively choose which parts of the install I wanted to do. Using the "expert" mode, I skipped the step for "Select and Install Software". That let me finish installing the system successfully, but unforunately also means that I have no desktop environment. The command line login seems to work fine as best I can tell.

Afer a bit more research, I concluded that what I needed to do was to manually install the desktop environment. So, I tried the following command while logged in as root:

tasksel install ubuntu-desktop

Unfortunately this fails. I see some quick messages about discover1, xresprobe, and xserver-org, then I get a pseudo-graphical screen (blue screen in character mode with gray progress window) and just seem to lock up there. The window title is "Installing packages" and the progress stays at 0%. The CD-ROM drive light blinks for a long time as if it is trying to read something, making me wonder if there is some problem with the CD. But I've done a CD integrity check as part of the initial install, and it comes up fine.

I've tried this process several times, all with the same result.

So, stuck again. I guess since this is a new problem I am going to post a new thread.

---

### Post by wpshooter on 2006-12-10
rodj: 

Am I correct in assuming that you are going to be attempting to install and run **ONLY** Ubuntu on the machine and no other O/Ss ?

If so, try this:

Get the **KILLDISK** program and **WIPE** your hard drive completely clean and then try the install again from the ALTERNATE CD.  I would try it thru just the regular parameters to start with.

[http://www.killdisk.com/](http://www.killdisk.com/)

A hint.  Make sure that when you see each install parameter, that you give your CD drive time to spin down completely between seeing and answering each prompt.

Good luck.

---

### Post by rodj on 2006-12-10
Again, thanks for the suggestion. I was already installing from the alternate CD and had no trouble with the partitioning of the drive. Yes, you are correct, this machine is going to have ONLY Ubuntu on it.

Anyway, I'm posting this follow up to report success with the

tasksel install ubuntu-desktop

command. Apparently I underestimated just how ancient this machine is. Amazingly, after I just happened to leave it on the "Installing packages screen" for about an hour, showing 0% progress the entire time, it suddenly continue on and about 30 minutes later completed the desktop installation. So I just wasn't being patient enough.

Now I am on to a slew of different problems as a Unix newbie, for example configuring my network. So far I am not yet on the internet, but I don't even have a specific question at this point. I've at least got the Gnome desktop running so I am going to read some of the guides and do a little more research before posting my next question.

Thanks for the help!:)

---

### Post by wpshooter on 2006-12-10
Did you setup a swap partition ?

Your partitions should look something like this:

/ for root, i.e. operating system - filesystem type ext3
/home for home folder - file system type ext3
/swap for linux swap - file system type linux swap

---

