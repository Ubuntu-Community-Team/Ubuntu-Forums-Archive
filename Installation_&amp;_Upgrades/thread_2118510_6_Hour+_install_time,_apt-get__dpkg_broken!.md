---
title: "6 Hour+ install time, apt-get / dpkg broken!?"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by Noki0100 on 2013-02-21
[COLOR=black][FONT=Tahoma]Hi All,[/FONT][/COLOR]
 
**[COLOR=black][FONT=Tahoma]Problem:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]I wanted to try Steam for Linux on my Gaming PC, tried installing Ubuntu 12.10 (and Mint 14) and the install is amazingly slow, at the 'Copying Files...' stage for example this takes about an hour. I killed the install (after going to the pub and back) and rebooted and was amazed to find myself on the Desktop. However running apt-get took an age and always failed and I think DPKG is what was being slow. I discovered that apt-get and dpkg were completely broken and could not be fixed (likely because I cancelled the install).[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]Ubuntu itself ran fine incidentally; very smooth and speedy with the exceptions I've listed.[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]By contrast Debian 6 (which I've used for years on my Server) installs in about 25 minutes and runs fine, all be it too old to get Steam running (without hassle anyway). Someone suggested to me that this may be because it is older and is using less modern drivers (or something) and Ubuntu is trying to do it the 'correct' or 'modern' way and is somehow failing, causing the huge speed problem.[/FONT][/COLOR]
 
**[COLOR=black][FONT=Tahoma]What I've tried:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]I only had Ubuntu "Installed" for an evening, since the install didn’t really finish I can't blame Ubuntu for not working at this point. So I ran through a selection of fixes for apt-get and so on but nothing worked, /var/lib/dpkg/**[FONT=Tahoma]status[/FONT]** (and status-old) were both 0k and similar forum posts I found all suggested this was a critical problem and a complete re-install was the suggested fix.[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]I tried upgrading the Kernel to one which supports TRIM and enable the features for this from varying sources, I tried many combinations, no change in performance.[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]Links on TRIM (though I can’t see this as being the culprit): [link]("https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu"), [link]("http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm")[/FONT][/COLOR]
 
**[COLOR=black][FONT=Tahoma]What I'm doing now:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]Reading through the Kernel help files so that (when I'm ready to) I can build my own Kernel for what I need. This is quite long (and much of it makes little sense to me) so any links to useful resources there would be appreciated, such as do I really need to read all of it since most of it just says 'if unsure leave as 'no''? My money is on this being some sort of driver / kernel / hardware incompatibility which *should* have a workaround / fix somewhere.[/FONT][/COLOR]
 
**[COLOR=black][FONT=Tahoma]Specs:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]Intel i7 3770k 3.5Ghz (Ivybridge)[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Asus P8Z77 Pro ([related info]("http://ubuntuforums.org/showthread.php?p=12295887"))[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]32GB of DDR3 RAM (Corsair Vengeance 1600Mhz in 4*8GB modules)[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Crucial M4 128GB SSD (OS Drive, Windows 7 runs great, has latest firmware 040H)[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]3*Intel X25-M SSDs (Windows is using them as my Stuff partition so can be ignored for this)[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]On the Crucial M4, this [link]("http://linuxlookup.com/review/crucial_m4_ssd_review") shows someone using this drive under Ubuntu 11.04 without issue (and on the older version of my motherboard, well fairly similar).[/FONT][/COLOR]
 
**[COLOR=black][FONT=Tahoma]Any Ideas:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]So what I need to know is what's is actually going wrong, why is the Ubuntu installer so slow, what is wrong with apt-get/DPKG, are there easy fixes for any of these things, am I likely to need to build my own custom Ubuntu installer to get this to work on my machine? A few 'Linux Guys' at work have blamed my SSD, but if that's the case and it can't be fixed right now I'll give up as I don't want to buy a normal HDD just so I don't have to use Windows anymore.[/FONT][/COLOR]
 
*[COLOR=black][FONT=Tahoma]Also BTW, I am one of those people who think Linux is held back by the lack of game support! There don't seem to be many of us around anymore.[/FONT][/COLOR]*
 
*[COLOR=black][FONT=Tahoma]ALSO NOTE: Debian is currently installed as I needed to get back to Windows and it seemed the quickest way to fix the boot loader while still playing with Linux. I may run the installer all day while I'm at work and *hope* it works well enough when I get home to do something.[/FONT][/COLOR]*

---

### Post by Noki0100 on 2013-02-22
So...
 
I've now tried it on a brand new 256GB Crucial M4 using the entire disk as a partition (in case my problem was block size). This had no affect on the installer being so slow.
 
Today I have started the installer and come to work, when I get home tonight *hopefully* I will have a fresh install of Ubuntu ready to go, this time I cleared out the Intel X25M SSDs and I'm installing it there, these are much older drives and in theory more likely to be supported, a guess tbh.
 
I guess what I'm asking is does anyone have a suggestion as to my next steps?
 
Is there a way to get the installer to dump debug logs onto a usb stick for me to TRY and figure this out?
 
Can I run the installer in a different way?
 
Is using a whole SSD as a partition and just putting the entire / (root directory) there a good idea?
 
Is there anything wrong with installing it on another computer, imaging the drive and copying it back?
 
I am willing to try ANYTHING at this point!!!
 
ANY help would be appreciated,
 
Thanks,
Noki

---

### Post by dino99 on 2013-02-22
maybe glance at post #10 of:
[http://ubuntuforums.org/showthread.php?t=2033027](http://ubuntuforums.org/showthread.php?t=2033027)

---

### Post by zhaozhou on 2013-02-22
> **Noki0100 said:**
> [COLOR=black][FONT=Tahoma]Hi All,[/FONT][/COLOR]

Hello.
 
> **Noki0100 said:**
> [COLOR=black][FONT=Tahoma]By contrast Debian 6 (which I've used for years on my Server) installs in about 25 minutes and runs fine, all be it too old to get Steam running (without hassle anyway). Someone suggested to me that this may be because it is older and is using less modern drivers (or something) and Ubuntu is trying to do it the 'correct' or 'modern' way and is somehow failing, causing the huge speed problem.[/FONT][/COLOR]

It's all kernel and drivers. Ubuntu may, or may not, have the latest of them. I can't imagine the installer is having any effect.
 
> **Noki0100 said:**
> [COLOR=black][FONT=Tahoma]I tried upgrading the Kernel to one which supports TRIM and enable the features for this from varying sources, I tried many combinations, no change in performance.[/FONT][/COLOR]

TRIM has been in the kernel for some time now, and even if you were to run Ubuntu on a kernel without trim, you wouldn't suffer these kind of consequences, as you point out.
 

> **Noki0100 said:**
> **[COLOR=black][FONT=Tahoma]What I'm doing now:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]Reading through the Kernel help files so that (when I'm ready to) I can build my own Kernel for what I need. This is quite long (and much of it makes little sense to me) so any links to useful resources there would be appreciated, such as do I really need to read all of it since most of it just says 'if unsure leave as 'no''? My money is on this being some sort of driver / kernel / hardware incompatibility which *should* have a workaround / fix somewhere.[/FONT][/COLOR]

You shouldn't have to go down this road. Building a kernel is basically 'know your hardware'. Ubuntu does a good job of automatically loading and configuring most devices.
 
> **Noki0100 said:**
> **[COLOR=black][FONT=Tahoma]Any Ideas:[/FONT][/COLOR]**
[COLOR=black][FONT=Tahoma]So what I need to know is what's is actually going wrong, why is the Ubuntu installer so slow, what is wrong with apt-get/DPKG, are there easy fixes for any of these things, am I likely to need to build my own custom Ubuntu installer to get this to work on my machine? A few 'Linux Guys' at work have blamed my SSD, but if that's the case and it can't be fixed right now I'll give up as I don't want to buy a normal HDD just so I don't have to use Windows anymore.[/FONT][/COLOR]

I have no experience with SSD drives. It might be an issue, someone else might chip in with information on this, but at least we can test it.
 
> **Noki0100 said:**
> *[COLOR=black][FONT=Tahoma]Also BTW, I am one of those people who think Linux is held back by the lack of game support! There don't seem to be many of us around anymore.[/FONT][/COLOR]*

You are not alone, not by far. Did you see the comment section of the first "Steam is coming to Linux"-announcement from Valve?

Anyway, if you can boot up the Ubuntu live cd - not installing, you can check dmesg for information, perhaps pastebin it for us. You can also mount your HDD and try to write some data onto it, and check pastebin again, and time (1) it to check throughput of the operation (something like time dd if=/dev/zero of=file_on_ssd bs=1M count=1024).
If you are able to boot something systemrescuecd you've got additional benchmarking and testing utilities to use.

---

### Post by zhaozhou on 2013-02-22
> **dino99 said:**
> maybe glance at post #10 of:
[http://ubuntuforums.org/showthread.php?t=2033027](http://ubuntuforums.org/showthread.php?t=2033027)

GPT, although cool, will probably not fix the issues Noki has - I can't imagine MBR being the cause of this.

---

### Post by Noki0100 on 2013-02-22
[COLOR=black][FONT=Tahoma]Thanks, that's a great idea about testing the SSD from a Live CD, never occurred to me![/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]I've been looking through some posts today and most of what I've found seems to be minor improvements, nothing solid that looks like it's my problem, but I've been through so many they all look the same now. I've picked a few (from above) that look good to play with at the weekend. So thanks for the links.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]As for the Kernel, good to know that Ubuntu support things like TRIM out of the box but this is something I have wanted to learn about for a while, but since I might start skim reading a little more so I get onto more interest (and understandable things).[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
*[COLOR=black][FONT=Tahoma]As for my comment about upgrading the Kernel, I am sure that when Ubuntu was installed the Kernel was even older than Debian was running; I'll confirm that later on. My thinking at the time was perhaps it install initially with an older Kernel and the upgrades itself towards the end of the install.[/FONT][/COLOR]*[COLOR=black][FONT=Tahoma][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]I think I will be rebuilding the machine soon, possibly the weekend including Windows so I may look into the GTP UEFI / MBR thing, for the sake of learning more than anything. This machine is kind of disposable, it's for browsing, watching and playing, my Debian server has all my stuff on it.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Thanks again, I'll repost over the weekend with my findings, and with a little luck the word SOLVED![/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Thanks,[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Noki[/FONT][/COLOR]

---

### Post by grahammechanical on 2013-02-22
I have known installations to complete in about 40 minutes not including the time it takes me to enter my details. If we choose to download updates during the installation and the download of third party software, then it will take longer as more work has to be done. Oh, the installation of third party software requires user input. If the user does not give that input the installer just waits and waits and then finally gets going again. May be. I have not tested this.

Debian does not give the user a choice of installing third party software. This is my understanding. So, I guess a Debian install would be a lot quicker.

You could try

```
sudo dpkg --configure -a
```

and

```
sudo apt-get -f install
```

[https://lists.ubuntu.com/archives/ubuntu-accessibility/2009-February/003301.html]("https://lists.ubuntu.com/archives/ubuntu-accessibility/2009-February/003301.html")

Should note any messages. They will be useful for diagnosing problems.

then run

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

to see if the OS can be updated. Again note any messages.

Regards.

---

### Post by Noki0100 on 2013-02-22
Hi Thanks for the input, can these options be run during the installation?
 
I guess if my installtion is finished when I get home then that is a moot point.
 
As a side note, I elected *not* to install updates or third-party software as I know this maybe causing delays, so this is a Vanilla install where the only option I chose is 'Something Else...' and I chose where to put my Root Directory, Swap was created during an old Debian install I did and I just left it there. As I said before the whole files system is going to a single partition.
 
Thanks Again!
 
Noki

---

### Post by Noki0100 on 2013-02-25
Hi All,
 
So, I've had Ubuntu installed all day yesterday while I did things, and generally speaking the PC is behaving itself. I got Steam installed (my end goal) which seems to work ok and managed to get 8 gig installed (I think the Steam servers were being slow yesterday and not my machine), I killed off Unity in favour of Gnome (gnome 3.6.1 sucks BTW, planning on reverting back if I can to an older, more standard Gnome) I pulled down 3000 emails from hotmail into Thuderbird, ran Ubuntu updates, ran the built in benchmark/performance test thing, used Chrome/Firefox to browse the web, imported my music installed XBMC and scrapped my movies folder.
 
All sounds great, and many of these things I was doing all at the same time, no real slow down or problems. Not as fast as Windows, but almost there, which is what I would expect.
 
Incidentally my tests on the SSDs under Ubuntu came back with over 100MB write, and well over 200MB read speeds, so the disks are not the problem.
 
=======================
[] Yet my issues STILL persists! []
=======================
 
running 'apt-get update' hangs EVERYTIME for **20 minutes at 'Reading Package Lists...'.**
 
*Unsure how significant this is: from 0% - 56% (there about) it goes SLOWELY, then from 57%ish to 90% it shoots through in about 10 seconds) then slows down again for the final 10%. This is consistently reproducable behaviour.*
 
I've searched around and can find various posts about this around but ALL of those are complaining about this step taking as long as 3 minutes, not 20 like I'm putting up with.
 
I've applied all of the fixes mentioned, but these feel like configuration improvements and tweaks, not fixes like I feel I need. I have also done the following:
 
-Mounted TMP Files into the RAM
-Booting the disks with flags to enable TRIM where appropriate (not sure if I got this correct but it didn't do any harm)
-Mounted /home onto another disk (not really an improvement just a difference)
 
Again, workaround, nothing which attempts to fix my issues. I will close this post in the next couple of days (wince it's no longer an installation issue) and raise one specifically for apt-get. But I will of course link the 2 together and post solutions to both if I find one.
 
Again though, thanks for everyone's input, PLEASE PLEASE PLEASE post if you can think of a way for me to debug this problem of Reading Package List taking forever, at this point I am stuck for ideas and need help!
 
Thanks,

---

### Post by Bucky Ball on 2013-02-25
Have you tried changing the server/mirror you are attempting to update from? You may have mentioned this, sounds simple but just a thought. The 'Find closest server' option does not always find the fastest.

---

### Post by Noki0100 on 2013-02-25
I have to be honest, no I haven't.
 
I assumed that once it had gotten to 'Reading Package Lists...' it was done pulling information down from sources and was figuring out what was needed for my currently system/config.
 
I can try this tonight when I get home.
 
Also I assume Mint uses different Servers, and this also happened during my Mint install last week, again why this never occured to me.
 
Thanks,

---

### Post by Noki0100 on 2013-02-26
Hi, I moved my sources list in the Systems Settings from UK to Main, and if anything it became a little slower. At the least the 'get' and 'ign' sections did, but 'Reading Package List...' took around the same 20 minutes.
 
Also Steam decided to update when I got home, I assume to do that it needs to run something similar to apt-get (though presumably something seperate) and this took some time too, about 3-4 minutes. By comparison when I booted into windows a couple of hours later Steam also need to update here with a file around the same size which took maybe 15 seconds.
 
I think there is more wrong then just apt-get, or there is something small not working correctly which apt-get needs to use over and over when running update.
 
Still stuck, any and all help appreciated.

---

### Post by Noki0100 on 2013-02-26
I just found like guide: [http://www.dedoimedo.com/computers/linux-system-debugging-super.html](http://www.dedoimedo.com/computers/linux-system-debugging-super.html)
 
I'm going to run through it tonight see if I can narrow down my problems, though if this looks like a waste of time for my problem, please shout!

---

### Post by Noki0100 on 2013-02-26
Hi All,

I've now run strace and ltrace on apt-get update and got the output, I am able to compare this to my debian 6 server, but it's not a true comparative test as even the hardware is different.

I'm searching through the web now looking for possible causes but so far I haven't found anything. If anyone can make sense of this please post.

strace:
[HTML]
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 93.25    0.005222         373        14           waitpid
  4.54    0.000254           0      2662           read
  1.61    0.000090           0       875       286 stat64
  0.61    0.000034           1        30           munmap
  0.00    0.000000           0       590           write
  0.00    0.000000           0       240         6 open
  0.00    0.000000           0       309           close
  0.00    0.000000           0        10         9 unlink
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         4           chdir
  0.00    0.000000           0        17           chmod
  0.00    0.000000           0         1           getpid
  0.00    0.000000           0        12        11 access
  0.00    0.000000           0        10           kill
  0.00    0.000000           0        35           rename
  0.00    0.000000           0        21           dup
  0.00    0.000000           0        23           pipe
  0.00    0.000000           0        11           brk
  0.00    0.000000           0         2           ioctl
  0.00    0.000000           0       232           gettimeofday
  0.00    0.000000           0         2           fchmod
  0.00    0.000000           0         2           fsync
  0.00    0.000000           0        14           clone
  0.00    0.000000           0        14           mprotect
  0.00    0.000000           0        27         3 _llseek
  0.00    0.000000           0       452           select
  0.00    0.000000           0         4           msync
  0.00    0.000000           0         4           rt_sigaction
  0.00    0.000000           0       254           rt_sigprocmask
  0.00    0.000000           0         2           getcwd
  0.00    0.000000           0        62           mmap2
  0.00    0.000000           0         1           ftruncate64
  0.00    0.000000           0         2         2 lstat64
  0.00    0.000000           0       262           fstat64
  0.00    0.000000           0         1           getuid32
  0.00    0.000000           0        16           getdents64
  0.00    0.000000           0       305           fcntl64
  0.00    0.000000           0         1           set_thread_area
  0.00    0.000000           0         8           openat
------ ----------- ----------- --------- --------- ----------------
100.00    0.005600                  6532       317 total
[/HTML]

ltrace
[HTML]
% time     seconds  usecs/call     calls      function
------ ----------- ----------- --------- --------------------
 49.93  991.580396   991580396         1 _ZN11CommandLine11DispatchArgEPNS_8DispatchEb
 44.92  892.111896   892111896         1 _ZN12pkgCacheFile11BuildCachesEP10OpProgressb
  5.01   99.452689    99452689         1 _Z10ListUpdateR16pkgAcquireStatusR13pkgSourceListi
  0.10    2.011690        4460       451 sigaddset
  0.01    0.174376          28      6147 strlen
  0.00    0.095587          26      3542 _ZN10pkgAcquire10WorkerStepEPNS_6WorkerE
  0.00    0.062476          31      1980 _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i
  0.00    0.058722         130       451 _ZN16pkgAcquireStatus5PulseEP10pkgAcquire
  0.00    0.051496          28      1797 __snprintf_chk
  0.00    0.041437          45       902 sigprocmask
  0.00    0.035268          63       559 _ZNSo5flushEv
  0.00    0.027825          26      1041 _ZNSs4_Rep10_M_destroyERKSaIcE
  0.00    0.027084          31       858 _Z9SizeToStrd
  0.00    0.025476          40       631 memset
  0.00    0.025083          39       631 __sprintf_chk
  0.00    0.013495          28       481 snprintf
  0.00    0.012177       12177         1 _ZN12pkgCacheFile12RemoveCachesEv
  0.00    0.011808          26       451 sigemptyset
  0.00    0.008400          78       107 _ZNSo3putEc
  0.00    0.008065          50       159 gettext
  0.00    0.006206          34       181 _Z9TimeToStrm
  0.00    0.005443          70        77 _ZN16pkgAcquireStatus7FetchedEyy
  0.00    0.004580          25       180 memcpy
  0.00    0.004548          25       180 __udivdi3
  0.00    0.002492        1246         2 _ZN12pkgCacheFile15BuildSourceListEP10OpProgress
  0.00    0.002120        2120         1 _Z13pkgInitConfigR13Configuration
  0.00    0.001686          29        57 _ZNSt8ios_base4InitD1Ev
  0.00    0.001618          26        60 _ZNSo9_M_insertImEERSoT_
  0.00    0.000255         255         1 _ZN16pkgAcquireStatus4StopEv
  0.00    0.000219         219         1 _ZN12pkgCacheFileD2Ev
  0.00    0.000163         163         1 _Z13pkgInitSystemR13ConfigurationRP9pkgSystem
  0.00    0.000132          66         2 signal
  0.00    0.000131          26         5 _ZNK13Configuration5FindBEPKcRKb
  0.00    0.000122          40         3 _Z12_GetErrorObjv
  0.00    0.000109          27         4 _ZNK13Configuration5FindIEPKcRKi
  0.00    0.000106         106         1 setlocale
  0.00    0.000094          94         1 _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
  0.00    0.000092          30         3 _ZNSoD1Ev
  0.00    0.000089          14         6 __cxa_atexit
  0.00    0.000088          29         3 _ZNSt9basic_iosIcSt11char_traitsIcEE5rdbufEPSt15basic_streambufIcS1_E
  0.00    0.000087          87         1 _Z8ioprintfRSoPKcz
  0.00    0.000068          34         2 _ZNK11CommandLine8FileSizeEv
  0.00    0.000065          65         1 _ZN14OpTextProgress4DoneEv
  0.00    0.000062          62         1 getuid
  0.00    0.000060          60         1 isatty
  0.00    0.000058          58         1 ioctl
  0.00    0.000049          49         1 _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
  0.00    0.000048          16         3 _ZNSoC1EPSt15basic_streambufIcSt11char_traitsIcEE
  0.00    0.000041          41         1 _ZN12pkgCacheFileC2Ev
  0.00    0.000040          40         1 _ZN16pkgAcquireStatusC2Ev
  0.00    0.000038          38         1 _ZN14OpTextProgressC1ER13Configuration
  0.00    0.000036          36         1 _ZN16pkgAcquireStatus5StartEv
  0.00    0.000032          32         1 _ZN11CommandLineD1Ev
  0.00    0.000032          32         1 _ZN11GlobalError10DumpErrorsERSoRKNS_7MsgTypeERKb
  0.00    0.000029          14         2 _ZNSt8ios_base4InitC1Ev
  0.00    0.000019          19         1 _ZN11CommandLine5ParseEiPPKc
  0.00    0.000016          16         1 textdomain
  0.00    0.000016          16         1 _ZN11CommandLineC1EPNS_4ArgsEP13Configuration
------ ----------- ----------- --------- --------------------
100.00 1985.866535                 20983 total
[/HTML]

Any help appreciated,

Noki

---

### Post by Noki0100 on 2013-02-27
My searches came up empty last night, I will begin a new thread on this I think with more specific information. If anyone can suggest any next steps though before I'm able to do that then please do!
 
Thanks,
Noki

---

### Post by framlin2 on 2013-09-29
Servus,

did you have found a solution for this behaviour?

I have exactly the same problem. Tehe *download* is NOT the problem, its the prcessing, that comes after, that takes nealry half an hour.

I have this problem since I updated fom 12.04 to 13.0 some days ago. I have tried to change the server, I have checked the sources.list. but all of that seems to be ok and not part of the problem, becaus fetching the sources is as fast (or slow ) as expected. But something slows down the "package-processing" dramatically.

Thanks 
    Wolfgang

---

### Post by Bucky Ball on 2013-09-29
@framlin2: Welcome. Please start a new thread rather than resurrecting and hijacking this old one. ;)

Your problem is not the same and the thread title does not match your problem so you would will have more chance of help with a new thread describing your issue rather than burying yourself here. Thanks.

---

### Post by Bucky Ball on 2013-09-29
@framlin2: Welcome. Please start a new thread rather than resurrecting and hijacking this old one. ;)

Your problem is not the same and the thread title does not match your problem so you would will have more chance of help with a new thread describing your issue rather than burying yourself here. Thanks.

---

