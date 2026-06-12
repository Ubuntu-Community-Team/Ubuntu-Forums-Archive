---
title: "After installing ubuntu 16.04 reboots to shell&gt; prompt"
date: 2017-10-17
forum: Installation &amp; Upgrades
---

### Post by runbad on 2017-10-17
I have been running ubuntu 14.04 for several years.  On a new build, I decided to install ubuntu 16.04 from the install disk that came with the book "Ubuntu Unleashed, 2017 Edition".  The installation seem to go fine.  However, after the required initial reboot, the screen came up in with the shell> prompt only.  I expected the normal ubuntu gui.  How can I get there?

---

### Post by ajgreeny on 2017-10-17
Was that a grub rescue prompt or a command line into which you could login with username and password?

What hardware do you have and particularly the graphic card as that is a possible reason for your current problem?

---

### Post by runbad on 2017-10-17
I agree that my graphics situation could be the problem.  This is a SuperMicro gpu server with one tesla K80 gpu installed. However, I am running on the onboard graphics.  Prior to this install of 16.04, I successfully installed ubuntu 14.04.  With 14.04 the reboot led to the normal GUI and it all worked fine.  However, Nvidia no longer offers a cuda install file for 14.04, so I need to make the switch to 16.04.  Before installing 16.04, I removed the SSD from the server and reformatted it on another machine, so the disk on which 16.04 was installed was fresh.

---

### Post by runbad on 2017-10-17
I should have also responded to your first question. I am not sure what the shell> prompt mode is.  There is not login and it is not the command prompt environment reached by cntl-alt-f1.  For instance, "sudo reboot" is an unknown command.

---

### Post by ajgreeny on 2017-10-17
That sounds more like the grub rescue prompt, but let's see what's what from clicking **Boot-Repair** in my signature below. Follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the **pastebin** link you get which will show us a lot more about your system.

---

### Post by runbad on 2017-10-17
Between your first and last posts I realized that I failed to describe the problem completely.  To get a better description I  re-formatted the hard drive and re-ran the install disk. What happens after I click the reboot button is the screen goes black and the following messages appear:
[ 23:194510] nouveau 0000:84:00.0: unknown chipset (of22d0a1)
[ 23.194768] nouveau 0000:85:00.0: unknown chipset (of22d0a1)
[ **] A start job is running for ubuntu live CD installer (1 min 18s/no limit)

After that the system just hangs. It does not appear to continue in the reboot, nor does respond to the keyboard or mouse.  In the first attempt, after 5 or 10 minutes, I figured it was permanently hung, gave up and cycled the power on the machine to force it to reboot.  That is when it came up in the shell> prompt mode.  In this second attempt I just let it set and did something else for 30 minutes or so.  When I came back to it, it had sorted itself out.  I was able to login and the GUI came up as usual.  However, after the screen saver timed out and I  re-entered my password the message "System program problem detected" appeared.  The associated error report went on for several pages.  It started with:

ExecutablePath
  /usr/bin/appstreamcli:
Package
  appstream 0.94-1
ProblemType
  Crash
Title
  'appstreamcli': assertfailure: ***Error in 'appstreamcli': double free or coruption (fasttop): 0x0000000001df5c40***
ApportVersion
  2.20.1-0ubuntu2
Architectrue
  amd64
  ***Error in   'appstreamcli': assertfailure: ***Error in 'appstreamcli': double free or coruption (fasttop): 0x0000000001df5c40***
 CoreDump
Date 
  Tue Oct 17 18:03:25 2017

... and goes on for several more pages ....

My take is that something about my machine (hardware and/or BIOS) is not compatible with this version of ubuntu. I know ubuntu 14.04 will run on it without error.  Maybe a server version or 17.04 might work.  Any ideas about how I should proceed?

---

### Post by ajgreeny on 2017-10-18
OK, it does sound as if the graphic card is at the root of the problem.

These two lines relate to nouveau the open source nvidia driver;
> [ 23:194510] nouveau 0000:84:00.0: unknown chipset (of22d0a1)
[ 23.194768] nouveau 0000:85:00.0: unknown chipset (of22d0a1)
Let's see if we can at least get you to a desktop by booting with **nomodeset** boot option.

From the grub menu (hold shift at power-on if you do not normally see grub) press E to edit the boot stanza and go to the kernel line that includes "quiet splash" near to the end.

Now delete the two words **quiet splash** and add **nomodeset** in their place then use Ctrl+X to boot, hopefully to a GUI desktop, though it may be at a low resolution, or if not to a command line login screen.

---

### Post by runbad on 2017-10-18
I was thinking the same thing, so I removed the K80 and re-installed installed ubuntu 16.04 on the barebones machine, without a gpu, using onboard graphics, and with a freshly formatted SSD. This time system did not hang during the initial reboot.  The desk top came up and operated fine.  However, it still reported the same system error (the problem is  crash associated with /usr/bin/appstreamcli), but after I rebooted a second time, it seemed to disappear.  That is, on subsequent reboots, the error was not reported.  It appears that without the K80 initially installed, the problem with getting the GUI to run was solved.  There is still this system error report, but it is not clear if that will be a problem for running cuda.  My plan is to re-install the K80, then install cuda, see what happens.  Thanks for your help.

In its current form ubuntua 16.04 will not run without this system error on this Supermicro computer. My plan is to check with Supermicro support to see if there is a version of Linux that will run on their machine. Thanks for your help.

---

### Post by runbad on 2017-10-18
The last sentence in my last response was included by mistake.  I had given up and was planning to try a different Linux when I had the idea of taking out the k80.  Now I think ubuntu is going to work fine.  There must of been a conflict between the k80 and onboard graphics in the initial install that screwed things up. Taking out the K80 solved that. Hopefully cuda will install without re-triggering the conflict.

---

### Post by mörgæs on 2017-10-18
You don't necessarily have to ditch Buntu. You could try 17.10 to see if hardware support has improved compared to the somewhat dated 16.04.

---

### Post by Bashing-om on 2017-10-18
runbad; Hello;

+1 to trying 17.10 when it comes out tomorrow 

I also run a new generation nvidia card that has no support to this time with the open source driver in older releases .
However, the proprietary driver works just fine . One must boot ^^ ' nomodeset' and then install the proprietary driver..

[INDENT][INDENT]My bit to try and help
[/INDENT][/INDENT]

---

