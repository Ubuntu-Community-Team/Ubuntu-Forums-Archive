---
title: "Stuck on Ubuntu Installation &amp; Trial - Started Dispatch Password Requests"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by mjw3 on 2016-05-15
I am trying to install Ubuntu on a decent laptop. I am installing through a USB and had no errors come up during the disk check.
  Initially it would just hang on the loading screen, so I then removed splash and quiet from the start-up command.
  The very last line before hanging/freezing is:

  [OK] Started Dispatch Password Request to Console Directory Watch.

  Any help?

---

### Post by Bucky Ball on 2016-05-15
Welcome. Where you removed 'splash quiet', replace that with 'nomodeset'. Try again. Any different?

What happens when you 'Try Ubuntu'? I presume you are getting to the options to 'Try Ubuntu' 'Install Ubuntu', etc.? Can you get to a stable desktop?

Best if you can include some specific details like the version and flavour of Ubuntu you are using and the relevant specs of the machine. In this case, graphics card and RAM would be a start. Thanks. ;)

(PS: Sounds like you're get far enough to show that the USB is working fine, but out of curiousity, how did you create the install USB?)

---

### Post by mjw3 on 2016-05-15
> **Bucky Ball said:**
> Welcome. Where you removed 'splash quiet', replace that with 'nomodeset'. Try again. Any different?

What happens when you 'Try Ubuntu'? I presume you are getting to the options to 'Try Ubuntu' 'Install Ubuntu', etc.? Can you get to a stable desktop?

Best if you can include some specific details like the version and flavour of Ubuntu you are using and the relevant specs of the machine. In this case, graphics card and RAM would be a start. Thanks. ;)

(PS: Sounds like you're get far enough to show that the USB is working fine, but out of curiousity, how did you create the install USB?)

I just tried with nomodeset and it did the same thing.
It's the same thing for either Try and Install. I can get to my windows desktop fine but for Ubuntu I haven't been able to get past this. 

I am using 'ubuntu-16.04-desktop-amd64' created using 'rufus-2.8p'. 

As soon as it reaches the Dispatch Password Requests my USB light also turns off.

My specs: 
4GB DDR3 RAM @ 1600MHz
Celeron N2830 2.16GHz
Intel HD Graphics 3000 Mobile

---

### Post by Bucky Ball on 2016-05-15
Even though the USB checks out, have you tried booting it on another machine? Do you get the exact same error or another when you try 'Try Ubuntu' on another machine?

This may not have anything to do with it, but is Windows in hibernation/faststart mode and is it installed in UEFI mode? Check both. Boot to Win and switch off hibernation/faststart. Check the BIOS. If Win is installed in UEFI, you must boot the USB in UEFI also. ;)

---

### Post by mjw3 on 2016-05-15
> **Bucky Ball said:**
> Even though the USB checks out, have you tried booting it on another machine? Do you get the exact same error or another when you try 'Try Ubuntu' on another machine?

This may not have anything to do with it, but is Windows in hibernation/faststart mode and is it installed in UEFI mode? Check both. Boot to Win and switch off hibernation/faststart. Check the BIOS. If Win is installed in UEFI, you must boot the USB in UEFI also. ;)

Update!!! (not sure good or bad)

I disabled faststart and the USB was always running in UEFI Mode.

I now get an error following the dispatch password requests:

NMI watchdog: BUG: soft lockup - CPU#1 stuck for 22s [modprobe: 1075]

I'll be trying it on another machine now

---

### Post by Bucky Ball on 2016-05-15
Please provide the make and model of this machine. 

You are not running on battery by any chance? Never a good idea to upgrade/install using battery power. Plug in the machine and try again.

I hope this is not your case, but [here's someone who seems to have had exactly the same issue]("http://ubuntuforums.org/showthread.php?t=2205211&p=12996968&viewfull=1#post12996968"). 

This is a 64bit machine I presume??? (Disregard. [That processor is 64bit]("http://ark.intel.com/products/81071/Intel-Celeron-Processor-N2830-1M-Cache-up-to-2_41-GHz").)

---

### Post by mjw3 on 2016-05-15
> **Bucky Ball said:**
> Please provide the make and model of this machine. 

You are not running on battery by any chance? Never a good idea to upgrade/install using battery power. Plug in the machine and try again.

I hope this is not your case, but [here's someone who seems to have had exactly the same issue]("http://ubuntuforums.org/showthread.php?t=2205211&p=12996968&viewfull=1#post12996968"). 

This is a 64bit machine I presume??? (Disregard. [That processor is 64bit]("http://ark.intel.com/products/81071/Intel-Celeron-Processor-N2830-1M-Cache-up-to-2_41-GHz").)

I tried the USB on my main computer and it worked fine. 

Ugh I hope it's not a power supply fault. I have had the laptop plugged in this whole time. 
The model is [URL="https://www.asus.com/ca-en/Notebooks/X553MA/specifications/"]https://www.asus.com/ca-en/Notebooks/X553MA/specifications/
[/URL]

---

### Post by Bucky Ball on 2016-05-15
Bingo, perhaps. 

Intel® Bay Trail

These have known problems with 16.04. There are a couple of links around on here if you have a look. Apparently the bug goes back a bit. You might want to do some research on that. 

Read all of [oldfred's post here]("http://ubuntuforums.org/showthread.php?t=2253168&page=3&p=13290160&viewfull=1#post13290160").

My suggestion, and this would confirm if it is the 16.04/Baytrail issue, try with 14.04 and see if you get the same result. That is actually also an LTS (long-term support) release, supported until 2017, so you could install that for now and upgrade via the internet later (which avoid reinstalling). Any bug with Baytrail and 16.04 LTS may be fixed by that time.

---

### Post by oldfred on 2016-05-15
I think Bucky's suggestion of 14.04 is currently the best choice. But you can try the suggested boot parameter.

 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by mjw3 on 2016-05-15
I just tried installing v 14.04 with no success.

It now stops around the same time v16 does(in terms of time). Sometimes I get an extra line or two but it stops around the same spot:

Stopping flush early job output to logs     [OK]
...
Starting bluetooth daemon    [OK]

This does seem to be  CPU-related issue

---

### Post by Bucky Ball on 2016-05-15
Just to confirm: You are not getting to the 'Install third-party' drivers' and 'install updates during install' screen are you? Just a punt. If so, untick them so you receive neither.

Throwin' horsehoes. :-k

---

### Post by mjw3 on 2016-05-15
> **Bucky Ball said:**
> Just to confirm: You are not getting to the 'Install third-party' drivers' and 'install updates during install' screen are you? Just a punt. If so, untick them so you receive neither.

Throwin' horsehoes. :-k

No I'm not getting any of those. The only error message I see at startup is "The NTFS partition is in an unsafe state".

---

### Post by oldfred on 2016-05-15
That almost always is from Windows hibernation or fast start up.
It can be from the resize as NTFS always requires chkdsk after a resize.

So boot back into Windows, if resized be sure to run the chkdsk, it probably is automatic. And turn off fast startup.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by mjw3 on 2016-05-15
> **oldfred said:**
> That almost always is from Windows hibernation or fast start up.
It can be from the resize as NTFS always requires chkdsk after a resize.

So boot back into Windows, if resized be sure to run the chkdsk, it probably is automatic. And turn off fast startup.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Ah I didn't have this turned off. I turned it off and don't get any errors but it hasn't solved my main problem.
I had FastStart in Bios turned off.

---

### Post by oldfred on 2016-05-15
Fast boot in UEFI is different than fast startup in Windows.

Fast boot in UEFI assumes all hardware and system wide configuration is the same, so it does not rescan system for changes & just turns over system to operating system to boot. Since most times system has not changed it speeds boot, but can make it impossible to get into UEFI to tell it you have changed things.

Fast start up in Windows is hibernation. Linux NTFS drivers will not let you write into hibernated systems to prevent damage & default mount is read/write. You may be able to manually mount in read only mode, in an emergency.

---

