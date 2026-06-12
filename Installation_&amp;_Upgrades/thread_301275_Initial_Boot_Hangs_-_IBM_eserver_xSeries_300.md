---
title: "Initial Boot Hangs - IBM eserver xSeries 300"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by suggsjc on 2006-11-16
I'm trying to install 6.06 server on an IBM eserver xSeries 300.  The initial install goes fine.  However, when it tries to boot the first time it hangs when it gets to * Loading hardware drivers.

The last message that it displays before hanging is:
```
[42949387.730000] agpgart: Detected VIA Apollo Pro 133 chipset
```

I've tried passing agp=off but that doesn't help either.  Any suggestions?

FYI, I was able to install and boot a minimal install of Debain 3.1 and Fedora Core 5 was installed when I received it.

---

### Post by ikus060 on 2006-12-12
Hi suggsjc,

Actually your not the only one that got this problem. I google it and any one have an workarround to solve this problem.

Also, I'm in the same state, I have two xSeries 300 with Ubuntu 6.06. Tomorrow I update the BIOS from 1.16 to 1.20 to activate de ACPI function, but it's seems that Ubuntu don't really like the 1.20 BIOS version. Since I update, I got the same problem has you.

Well contact me if you found a solution !

Also, I contact IBM Tomorrow and they don't reply my message.

---

### Post by stansaraczewski on 2006-12-12
For the record, I am experiencing the same hang after hardware driver load - however I have a clone that is relatively new... and definitely NOT an IBM product.

The problem didn't arise till recently. 

A second boot completes just fine.

I'd love to know what is going on.

---

### Post by packhamster on 2006-12-13
All, the latest BIOS is required to get it to work. Here are detailed instructions on how and what to change. Sorry if it may appear simple to to the smart folks out there but I tried to describe the process from a "newbie" approach.

To install Ubuntu on the server we are using the server ISO image available on their website. Burn the image to a CD, insert it into the CDROM drive, and turn on the system. It should recognize the CD as bootable drive and boot into the Ubuntu installer. Select to install the LAMP server. Follow the menu and answer the question where required Please note that these parameters are from the old IBM eSeries server I used and will differ from your system (shown in this context in <> brackets – meaning either they will be different or you enter your own, e.g. username – so adjust accordinly…) Also, in my case the computer was attached to a network and could request an IP address via DHCP.

Choose a language:			English
Choose your location:			United States
Detect keyboard layout:		No
The origin of the keyboard		U.S. English
Keyboard layout:			U.S. English

Primary network interface:		eth0: <Intel Corporation…>
Hostname:				<ubuntu>

Partitioning method:			Erase entire disk: IDE1 master (hdq) - …
Write changes to disk:			Yes

Select your time zone:			<Central>
Is the system clock set to UTC:	Yes

Full name for the new user:		<John Doe>
User name for your account:		<jd>
Choose a password for the new user:	<password>
Re-enter password to verify:		<password>

Choose server to install:		LAMP

That should complete the installation, pop out the CD and prompt you to reboot the computer.

The hardware discovery in Ubuntu works very well with new system and the computer should boot up without any glitches. Unfortunately in the case of an eSeries server from IBM it is not the case. The system hangs during the startup and ends up with a message like

Starting up…
[42949377.950000] ACPI: Getting cpuindex for acpiid 0x1

And then nothing. It may also show a message asking for a BIOS upgrade. While that message may or may not be a “real” message (meaning it assumes it to be the problem) it should be the first line of defense: Make sure the BIOS is updated to the latest version (even if it dates back to 2003 as in my case) as in can indeed be part of the problem. In the case of the IBM it is not. What conflict here is the attempt to identify and load the AGP driver – a device that is not present in the IBM server used. Let’s go about fixing the issue.

Since the server doesn’t boot we have to boot one more time from the CD. Pop it back in and restart the server. This time select “Rescue a broken system”. Again we are stepping through a few question:

Choose a language:			English
Choose your location:			United States
Detect keyboard layout:		No
The origin of the keyboard		U.S. English
Keyboard layout:			U.S. English

Primary network interface:		eth0: …
Hostname:				<ubuntu>

Device to use as root file system:	/dev/hda1

When it comes to select the rescue operations we want to launch a shell as we need to modify some configuration files. Therefore select “Execute a shell in /dev/hda1” and select Continue on the next screen.

We are presented with a simple command line shell with the cursor next to the # prompt on the bottom of the screen. The changes we have to make include disabling certain drivers by blacklisting them. To do so open the configuration file in the vi editor. Since this tool is not very intuitive I will walk through every keystroke necessary (probably very boring for most of the folks, but I remember my struggles in the beginning…)

# cd /etc/modprobe.d [Enter]
# vi blacklist [Enter]

Wait until the file is displayed (It begins with something like “# This file lists those modules…”

To move around in vi use the key h (left), j (down), k (up), and l (right) unless of course you are in insert mode in which case you can type those letters. Since this typing mechanism is kind of non-intiutive I will list the process as sequence of key strokes. Ignore the spaces inbetween the letters, function keys like enter, spacebar or esc I will list as [Enter], [Space], and [Esc]. So here we go:

j j j j i # [Space] Added [Space] for [Space] IBM [Space] issues [Enter] blacklist [Space] agpart [Enter] blacklist [Space] via-agp [Enter] blacklist [Space] intel-agp [Enter][Enter][Esc] : w : q

Let’s look at the above sequence a bit more in detail. Once we lauchned vi and open the file the repeated j move the cursor down 4 lines. The “i” puts the editor in insert mode. Subsently anything typed will be added to the file. After completing the entry (two [Enter] adding an empty line we switch the editor back into command mode by pressing [Esc], then save the file (:w) and quit the editor (:q). You can easily check your success but loading the file once more with “vi blacklist”. There you should see your entry. Then use “:q” to exit the editor. And just in case you get completely lost during the editing: Just hit [Esc] to make sure that you are no longer in edit mode, then force the editor to quit without writing the file buy typing “:q!” (without the quotes of course).

I found another problem with the IBM in that it showed issue with Ipv6 support. To avoid any conflicts there I disabled is by creating a new file called bad_list. So again here is the sequence of key strokes:

At the command prompt type “vi bad_list” and hit [Enter]

i # To [Space] avoid [Space] conflicts [Space] with [Space] the [Space] IPv6 [Space] protocol [Enter][Enter] alias [Space] net-pf-10 [Space] off [Enter][Esc] :w [Enter] :q [Enter]

That should be it! Type “exit” at the prompt which brings you back to the selector. Choose the last option and reboot the system. Don’t forget to take the CD out of the drive during the reboot.

Good luck!

   -packhamster-

---

### Post by stansaraczewski on 2006-12-13
A lot of detail there - nice job. 

It doesn't pertain to me though. My search for the solution continues.

I may just end up living with it because lots of times the first boot works, and sometimes a second attempt is required.

---

### Post by ikus060 on 2006-12-13
I will walk trought this and see If it's work. I will come back with feedback in few hours.

Thank for your help.

---

### Post by ikus060 on 2006-12-13
Hi to every one !

I'm so happy, it's work on one of my system and at this time, I try to the other one.

In brief, the key of this problem is to blacklist the apgart, via-agp, intel-agp modules.

Thank you for your reply and I will document it for next time.

---

### Post by ikus060 on 2006-12-13
It's to beautiful to be true.

On the other system, I got this when I try to install a LAMP server: 
> hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
hda 39179952 sectors (20060MB) w/2048kiB Cache, CHS
...

But, when I wait about 2 min, the installation begin and during the installation, I'm stuck at :
"Detecting hardware to find CD-ROM drives"
"0%"
"Detecting hardware, please wait..."

If I starting the installation with the "acpi=off" argument, the installation begin immediately and the detection of hardware work too.

I have to interrupt my test at this time. I will continue next morning.

---

### Post by ikus060 on 2006-12-17
Finally, I found the problem with the other server. There is a VIA CPU in this server. I change it for an Intel CPU and every thing work fine with the trick given by packhamster.

Thank for your good support.

---

### Post by packhamster on 2006-12-19
Glad I could help! Happy holidays!

---

### Post by LivingSouL on 2007-11-04
so, does this mean that we can't install desktop ubuntus on IBM eservers?

I had a hard time installing 6.06 and 7.04 on my IBM eServer xseries 200.. both wont work, reboots on step 5 (Migration of files). and i guessed the problem is on the hardware...

:(

---

### Post by ikus060 on 2007-11-04
I succeed to install Ubuntu dapper on my IBM eServer X300.
Describe your problem with more detail and some one or me will help you.

---

### Post by LivingSouL on 2007-11-05
Here's my problem:

I tried 7.04 (Live CD) on my IBM eServer xSeries 200 everything seems to work fine, tried to access all my drives on live cd, and yes i can access my files. But when I install it, it can identify all my drives and I tried BOTH manual and guided.

On the manual, steps 1 to 4 are great, but when it goes to step 5 (which is migration of files, which i guess accessing of files on the other drives) after like 3 seconds on the step 5, it mounts some drive name /blahblah/ (can't read it 'coz its too fast) then the system reboots... so frustrating.. :(

same thing goes on the guided, on the migration of files, it reboots.. :(

---

