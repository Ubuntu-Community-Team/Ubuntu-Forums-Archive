---
title: "Ubuntu 11.10 - Everything is Unstable and Crashing after last Update"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by seventhsamurai on 2012-04-03
Hi guys

I am running Ubuntu 11.10 32-bit on an Acer Aspire 5375-6285 with 3 GB RAM, Intel Core II Duo 2.0 GHz Processor.

Just yesterday I ran the latest update and I guess there was a Linux firmware update as well in there. Since running the updates, my system has become very unstable. Until before the update, it was running perfectly fine. Now, everything crashes. Chromium crashes the moment I attempt to open a website, sometimes the program doesnt even start up. When I copy a large file from 1 drive to another, the whole system crashes. Firefox is a little more stable than Chromium but it too is crashing often. Same with VLC media player when I attempt to play a 2 GB file. Plays fine for about 2-3 minutes and then quits abruptly.

I just wanted to check if anyone else was having the same issue? Is there a way for me to rule out that this is happening because of the update, by reverting to the previous configuration? I'd appreciate any help.

Thanks.

---

### Post by scottjonesy on 2012-04-04
Hi,

I have exactly the same thing. Firefox appears somewhat stable (hence how I registered and am posting this) but everything else is borked. I'm a newbie to Ubuntu so am not even sure how to roll back changes. But, yep, after the normal basic updates that came thru yesterday everything is messed up..chrome and chromium actually wont even start. Firefox is very 50/50 sometimes crashes after 10 seconds...sometimes is ok for 10/20 minutes. Any help appreciated too! 

Cheers, Scott

---

### Post by DukeOfTrentham on 2012-04-04
I'm having exactly this problem and have no idea how to solve it.

For me, I'm running Chrome Beta and it rarely even starts up. An unfinished window loads for, hangs for about 30 seconds and then usually just disappears. Nautilus sometimes starts up and sometimes doesn't.

I've installed the offline Gmail webapp in Chrome which is supposed to run as a separate process on startup and that doesn't happen either.

Gnome Shell seems to run fine, as does Terminal and AWN.

Here are the packages that were updated for me yesterday, 3 April 2012, taken from the Software Center history:

New
linux-headers-3.0.0-18 (3.0.0-18.31)
linux-headers-3.0.0-18-generic (3.0.0-18.31)
linux-image-3.0.0-18-generic (3.0.0-18.31)
 
Updated
linux-generic (3.0.0.17.20, 3.0.0.18.22)
linux-headers-generic (3.0.0.17.20, 3.0.0.18.22)
linux-image-generic (3.0.0.17.20, 3.0.0.18.22)
linux-libc-dev (3.0.0-17.30, 3.0.0-18.31)
python-aptdaemon (0.43+bzr697-0ubuntu1.1, 0.43+bzr697-Oubuntu1.2)
python-aptdaemon-gtk (0.43+bzr697-0ubuntu1.1, 0.43+bzr697-Oubuntu1.2)
python-aptdaemon.gtk3widgets (0.43+bzr697-0ubuntu1.1, 0.43+bzr697-Oubuntu1.2)
python-aptdaemon.gtkwidgets (0.43+bzr697-0ubuntu1.1, 0.43+bzr697-Oubuntu1.2)
aptdaemon (0.43+bzr697-0ubuntu1.1, 0.43+bzr697-Oubuntu1.2)
aptdaemon-data (0.43+bzr697-0ubuntu1.1, 0.43+bzr697-Oubuntu1.2)

I had proposed and backport updates switched on, but now have them switched off.

I'm a pretty big cloud computing geek, so I mainly use Chrome on my computer. It's pretty important that it work!! I'm writing this in Firefox at the moment, which seems to be stable but is slow.

I'm having this trouble on a 32-bit HP dx6500 laptop, Core 2 Duo 1Ghz, with oneiric installed.

Any help greatly appreciated!

---

### Post by seventhsamurai on 2012-04-04
By the way, this problem does not seem to be happening with the 64-bit version. I am running 11.10 64-bit on 3 other machines which are perfectly stable after the most recent round of updates.

The 32-bit however is a royal mess.

---

### Post by cottfcfan on 2012-04-04
For your Chromium problem, I had the same thing with Chromium 18 on 12.04 beta.
When I came to file a bug report, it had already been done, so the devs appear to know about the problem.
An update will probably come through shortly and sort it.

---

### Post by ravado on 2012-04-04
Hi there,

After running updates yesterday, I have the same problem with my Lubuntu 11.10. Ghrrr...

RV

---

### Post by seventhsamurai on 2012-04-04
Bump

---

### Post by MadFranky on 2012-04-04
Same here! Ubuntu 11.10 32bit.

I rebooted my Ubuntu using the previous kernel (3.0.0.17) and everything works fine again. :p

---

### Post by dadexix86 on 2012-04-04
Same here! Booting with 3.0.0.17 solved.

To autoboot with it waiting for the next update remove the files related to 3.0.0.18 in the directory /boot and update-grub.
This will remove the 3.0.0.18 line on grub and default to the last (which is 3.0.0.17).

---

### Post by MadFranky on 2012-04-04
To boot automatically into Kernel 3.0.017:

- launch "StartUp-Manager"
- choose "Ubuntu with Linux 3.0.0-17" as default operating system
- reboot the machine

Enjoy the "old", good working kernel. :p

---

### Post by gimi on 2012-04-04
Same here.. with the previous kernel works fine..

---

### Post by Midemeanor on 2012-04-04
Thanks to MadFranky 
version 18 caused all sorts of problems and I have now reset to version 17 using start-up manager

---

### Post by blackboot on 2012-04-04
Just posting to confirm experiencing the same bug reverting to 3.0.0-17-generic

---

### Post by rfaull on 2012-04-04
Bug reported at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972821)

---

### Post by scarter on 2012-04-04
Same problem here.  Thank goodness for these forums.

---

### Post by tazz4vr on 2012-04-05
Nice to know I am not alone with the problems, thought it was just me being a newbie and all...

---

### Post by tazz4vr on 2012-04-05
> **MadFranky said:**
> To boot automatically into Kernel 3.0.017:

- launch "StartUp-Manager"
- choose "Ubuntu with Linux 3.0.0-17" as default operating system
- reboot the machine

Enjoy the "old", good working kernel. :p

Help!  Newbie here and I need to ask if this solution will work on a Wubi puter as I still have Windows installed.  If so, where can I find 'StartUp Manager'?  I can only find 'StartUp Applications'.

---

### Post by JerseyNick on 2012-04-05
> **tazz4vr said:**
> Help!  Newbie here and I need to ask if this solution will work on a Wubi puter as I still have Windows installed.  If so, where can I find 'StartUp Manager'?  I can only find 'StartUp Applications'.

Apparently “Startup Manager” is not installed by default.

To install Startup Manager you will need to run the below command in a Terminal:

sudo apt-get install startupmanager


And why do you still have windows installed?????



Thanks guys, I was having the same problem with 32, this solved it.

---

### Post by gulokhar on 2012-04-05
The problems seems indeed to be related with the 3.0.0.18 kernel. Downgrading to the 3.0.0.17 will solve problem.

---

### Post by tazz4vr on 2012-04-05
> **JerseyNick said:**
> Apparently “Startup Manager” is not installed by default.

To install Startup Manager you will need to run the below command in a Terminal:

sudo apt-get install startupmanager


And why do you still have windows installed?????



Thanks guys, I was having the same problem with 32, this solved it.

Thank you for the info on installing the Startup Manager... as for the Windows question.. glutton for punishment would be my only defense at this time!  Unfortunately there are a few programs that I use in a work related sense and have not been able to find a suitable work around with Linux.  As a newbie, in Linux I do try suggested programs as alternatives, but still no luck as of yet.

---

### Post by MadFranky on 2012-04-06
A new kernel (3.0.0-19) is available. 
Run "update manager", upgrade Ubuntu and reboot your machine. 
Everything should work just fine! :p

Good work, dear Ubuntu team! Thanks!

---

### Post by tazz4vr on 2012-04-06
Need Help, again....
After going into Update Manager, did not see anything listed as kernel (3.0.0-19), however did run the updates that were showing, but still having issues.  Attempted to open the Software Center but it just hangs there.

Also, previously was able to find the Startup Applications, initially was looking for Startup Manager, but unable to find either now.  Was thinking about going to previous version that worked.

---

### Post by seventhsamurai on 2012-04-07
Ran the latest kernel updates this morning. We're back on track, back to a stable OS.

All is well!

---

### Post by MadFranky on 2012-04-07
@tazz4vr

Open the Terminal and type the following commands:

sudo apt-get update

[enter your password]

sudo apt-get upgrade

sudo dist-upgrade

---

### Post by tazz4vr on 2012-04-07
> **MadFranky said:**
> @tazz4vr

Open the Terminal and type the following commands:

sudo apt-get update

[enter your password]

sudo apt-get upgrade

sudo dist-upgrade

Does the fact that I have Windows still installed make a difference in whether or not the above commands will work?  I did as specified but still having issues, ie, Software Center folder opens but hangs, unable to access Startup Manager or Startup Applications.  Fyi, the code below was the end result after entering the commands you specified.  After completing the initial steps suggested, I did reboot my system.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*****:~$ sudo dist-upgrade
sudo: dist-upgrade: command not found
*****:~$ 

```

---

### Post by deodiaus on 2012-04-07
I installed 3 versions of the 64 bit OS (Ubantu 11, 10, 8), but none work.  They install, but none really allow you to get to do anything.  The screen just hangs with the backdrop showing.
Is there an instrumented version which traces things so that I can debug?

PC is HP Pavilion a1632x 


desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 43
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping    : 1
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips    : 2004.23
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 43
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping    : 1
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips    : 2004.23
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by tazz4vr on 2012-04-07
Unfortunately didn't realize how much I was unable to access via Ubuntu 11.10, had to reboot and go into Windows....  Is this a situation that I need to be creating a 'bug' for?  If so, where do I start?

---

### Post by MadFranky on 2012-04-07
@tazz4vr

Whoops... my fault! That's embarrassing! I'm sorry!

The correct command is:

sudo apt-get dist-upgrade

---

### Post by tazz4vr on 2012-04-08
> **MadFranky said:**
> @tazz4vr

Whoops... my fault! That's embarrassing! I'm sorry!

The correct command is:

sudo apt-get dist-upgrade

Okay... giving it another shot, wish me luck!  Oh, thank you kindly MadFranky, I appreciate your patience and assistance.  Stay tuned....

---

### Post by tazz4vr on 2012-04-08
> **tazz4vr said:**
> Okay... giving it another shot, wish me luck!  Oh, thank you kindly MadFranky, I appreciate your patience and assistance.  Stay tuned....

So after redoing the commands suggested, with the corrected one as well, still having issues.  Here is what came up on the terminal following commands....

```
********:~$ sudo apt-get update
[sudo] password for *******: 
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://archive.ubuntu.com oneiric Release.gpg
Hit http://security.ubuntu.com oneiric-security Release
Hit http://archive.ubuntu.com oneiric-updates Release.gpg
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-updates Release
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric/universe i386 Packages
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Reading package lists... Done
*****:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
******:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*****:~$ 

```

---

### Post by MadFranky on 2012-04-13
@tazz4vr

Perhaps your system is already updated to kernel 3.0.0.19.

In terminal, type 

uname -r

to check what kernel is in use.

---

### Post by tazz4vr on 2012-04-13
> **MadFranky said:**
> @tazz4vr

Perhaps your system is already updated to kernel 3.0.0.19.

In terminal, type 

uname -r

to check what kernel is in use.

My system is showing kernel 3.0.0.17 generic

---

### Post by MadFranky on 2012-04-13
OK, the previous command (uname -r) tells you which kernel is loaded. From what you say, it looks like your system boots the kernel 3.0.0-17.

In terminal, type 

*dpkg --get-selections | grep linux-image*

This command gives a list of all kernel that are available on your system. Do you see 3.0.0-19 in that list?

---

### Post by tazz4vr on 2012-04-13
3.0.0-19 is not in the list.

---

### Post by Curtis6767 on 2012-04-13
As a noob to Ubuntu, I just wonder if upgrading to a 3.2.xx kernel might solve this problem.

Is there even a remote possibility that that might work?

---

### Post by cottfcfan on 2012-04-14
> **tazz4vr said:**
> 3.0.0-19 is not in the list.

You need to enable the proposed updates repo.
In synaptic you need settings/repositories/updates & tick the proposed updates box. Then "reload" and search for the 3 packages you need.
I recommend disabling proposed updates afterwards, then reboot into your new kernel.

---

### Post by tazz4vr on 2012-04-14
> **cottfcfan said:**
> You need to enable the proposed updates repo.
In synaptic you need settings/repositories/updates & tick the proposed updates box. Then "reload" and search for the 3 packages you need.
I recommend disabling proposed updates afterwards, then reboot into your new kernel.

Thank you for the info, how do I get to 'synaptic' to make the necessary changes?

---

### Post by cottfcfan on 2012-04-15
> **tazz4vr said:**
> Thank you for the info, how do I get to 'synaptic' to make the necessary changes?

Install "synaptic package manager" from the Ubuntu software centre.
Then locate it in dash.

---

### Post by tazz4vr on 2012-04-15
> **cottfcfan said:**
> Install "synaptic package manager" from the Ubuntu software centre.
Then locate it in dash.

Unfortunately since the prior updates about 2 weeks ago, I am unable to access anything via Software Center and/or the dash.  Programs that I installed will either open and just hang there or not open up at all.  Any suggestions?

---

### Post by cottfcfan on 2012-04-15
What if you try and install from Terminal?
```
sudo apt-get install synaptic
```
Then access the program from the terminal.

---

### Post by tazz4vr on 2012-04-15
> **cottfcfan said:**
> What if you try and install from Terminal?
```
sudo apt-get install synaptic
```
Then access the program from the terminal.

Did the above code, all seems fine....

How do I access the program from the terminal?

---

### Post by cottfcfan on 2012-04-15
> **tazz4vr said:**
> Did the above code, all seems fine....

How do I access the program from the terminal?

Just type in the program name ie synaptic.
You may want to run:
```
sudo apt-get update && sudo apt-get upgrade
```
to see if that solves your problem first, if not post the errors back here.

---

### Post by tazz4vr on 2012-04-15
> **cottfcfan said:**
> Just type in the program name ie synaptic.
You may want to run:
```
sudo apt-get update && sudo apt-get upgrade
```
to see if that solves your problem first, if not post the errors back here.

After entering 'synaptic' into terminal, I first received the message 'Starting without administrative priviledges'.  Upon going into the settings portion of synaptic, the 'repositories' is not clickable (shadowed).

---

### Post by cottfcfan on 2012-04-15
Try starting it with administrative privileges then,
```
gksudo synaptic
```

---

### Post by tazz4vr on 2012-04-15
> **cottfcfan said:**
> Try starting it with administrative privileges then,
```
gksudo synaptic
```

Woo hoo... that worked.  So now that I have ticked 'proposed' updates, what 3 packages should I be looking for?

---

### Post by cottfcfan on 2012-04-15
linux-headers-3.0.0-19
linux-headers-3.0.0-19-generic
linux-image-3.0.0-19-generic
unless your using the pae kernel.
You can just see what you already have installed in synaptic, and then install the 3.0.0-19 equivalent.

Then reboot into the new kernel.

---

### Post by tazz4vr on 2012-04-15
> **cottfcfan said:**
> linux-headers-3.0.0-19
linux-headers-3.0.0-19-generic
linux-image-3.0.0-19-generic
unless your using the pae kernel.
You can just see what you already have installed in synaptic, and then install the 3.0.0-19 equivalent.

Then reboot into the new kernel.

I am unsure as to what 'pae' kernel is.  The last kernel that I see in the list is 3.0.0-17.

---

### Post by cottfcfan on 2012-04-15
> **tazz4vr said:**
> I am unsure as to what 'pae' kernel is.  
Don't worry about it then.

---

### Post by tazz4vr on 2012-04-16
> **cottfcfan said:**
> Don't worry about it then.

What about the kernel?  How do I go about getting the newest version if it isn't showing in the list?

---

### Post by tazz4vr on 2012-04-16
Unfortunately, I think I am going to just have to uninstall and go back to using windows for a bit.  Unfortunately all the programs I use, some are for work and are not usable anymore.  Perhaps I will attempt my try at Linux another time.

---

### Post by tazz4vr on 2012-04-16
Thank you everyone for all of your assistance with this situation that I was having.  I hope to someday figure out what went wrong.  But for now, it's break time.

---

### Post by cottfcfan on 2012-04-17
tazz4vr..
I really can't understand what your problem is!!
1. Tick the proposed updates box (which I assume you've done)
2. Click the reload button in synaptic (i assume you've done)
3. Install the 3 packages i listed in an earlier post.
4. Reboot into the new kernel.
Simple.

---

### Post by tazz4vr on 2012-04-17
Just to be on the safe side, I re-did everything you listed.  This time after hitting the 'reload' it did show me the 3.0.0.19's.  So I did mark the ones you specified, hit apply and then rebooted my puter.  Unfortunately still having the same issues and a new one has surfaced, the 'Update Manager' shows 1 pending, but does not open.  Whether I use the icon or go through the round thing on the upper right side of screen.

Oh, and there were some older versions still marked in synaptic, they had a full color of green in the box, should I have unchecked these?

---

### Post by cottfcfan on 2012-04-17
The 1 pending is probably not going to change things.
Using Wubi could be your problem, ive never liked it personally.
IMO, you're probably better waiting for the 12.04 LTS to come out. It's only just over a week away, and instead of using Wubi, dual boot, its bound to be less problematic.

---

### Post by tazz4vr on 2012-04-17
Will definitely follow your advice on waiting for the 12.04 LTS to come out.  Timing would work perfectly for me.  Thank you very much for all of your guidance, help, assistance, patience, etc....  If you were just a tad bit closer, I would buy you lunch. :popcorn:

---

