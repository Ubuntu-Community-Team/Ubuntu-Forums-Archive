---
title: "dpkg and everything else broke -- AGAIN"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by ruberad on 2013-12-01
My nemesis is a desktop with 12.04 64bit, installed a few months ago on a new (refurb) crucial 64gb v4 SSD, with a 120GB spinning disk for data. SSD has OS on 16gb ext4 partition, 8gb swap partition (for 4gb ram), 40gb ext4 mounted at /home, big disk mounted at /data. This is a family computer that basically sees 95% of its use in Firefox or Chromium, the remaining 5% is LibreOffice, Shotwell and Brasero.

About the SSD: I originally bought a new Crucial v4, and twice now I have had to return under warrantee, both times I got a refurb back. The refurbs both had a stamp saying they had the latest firmware. All three times, the very first thing I did after 12.04 install was to enable TRIM on both ext4 partitions on the SSD (/, /home).

About a month ago, I noticed that update manager had the red circle/white bar icon. Then when I tried to invoke software center, nothing (icon flashed, no window); I tried to install stuff with apt-get, there were errors, something to do with dpkg. Time went by, I tried software-center from command line, there were errors. Last night I finally took some time to try to research and fix; software-center from command-line was reporting python import problems with first line of /usr/bin/software-center (from gi.repository import Gtk, GObject). (Note, I've never dealt with Python, I'm a perl guy, but this seems pretty fundamentally broken, like in Perl if you couldn't "use File::Copy;" or something). Trying to install packages (gnome-hearts fer da kids) resulted in dpkg-related errors (I think maybe also python import problems)

I searched ubuntuforums, couldn't find this exact problem, but in everything similar people were asking for output from "sudo apt-get update; sudo apt-get upgrade", so I did that. update seemed to work ok, it mentioned 51 somethings, upgrade took probably an hour, apparently downloading the 51 somethings, and then installing. When it was done there were some errors, I don't remember what they were. I did update and upgrade again, still errors. I REBOOTED -- or tried to; and now I'm dead in the water.

Booting up I see the Ubuntu+white-->red dots, I see a page or so of text flashing by, and eventually get to an infinite loop where I see flashing on the top of the screen the two lines:

Could not write bytes - broken pipe                        [OK]
*checking battery state

This infinite loop is EXACTLY the death point I got to a few months ago (I still have it written down on the pad next to the computer) which required me to warantee the SSD (the second time), so I am super pissed (and afraid the only advice I'll get is "replace the disk and reinstall again").

I'm running off of Live CD now; disk utility says the SSD is healthy and "Check Filesystem" instantly returns "File system is clean" for both ext4 partitions. Is there any way I can diagnose/repair from this state? Or is my only recourse to reinstall 12.04 yet again (only to find out in a few weeks that the disk is toast anyways)?

Am I doing something wrong? Should I just give up on warrantee replacements and go back to spinning disks?

---

### Post by Bashing-om on 2013-12-01
ruberad; Hello ,

A bad state of affairs to be sure, and no end to the consternation.

Let's see if we can isolate the problem to primarily a package management problem,
or to a file system problem.
Can you boot to the grub menu (Hold shift key when ubuntu's splash screen appears)  ?
What results when you attempt to boot an older kernel from the grub menu ?
What results when you attempt to boot from "recovery mode" - an option with in grub's boot menus.

Enough for now, next might try and boot into the operating system in "text" mode (??).

Where oh where
[INDENT][INDENT]is the process failing
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-01
Thx so much for quick reply; I am off to church and will try to this as soon as I get back...

---

### Post by ruberad on 2013-12-01
OK I tried like 20 times, and only once got into the grub menu. What are the parameters for when the shift key can be pressed? Because the splash screen goes so fast I can't even see it being white just Ubuntu and bam it's already red.

ANyways, the one time I got into the grub menu, I went into previous versions, and I saw six options there, kernels 3.8.0.29 - .31, each also there with a recover mode. I chose 3.8.0.30 (not recovery) and got into the same infinite loop.

I was going to try a recovery mode next, but never got back in.

In all those times, what I saw in the infinite loop varied some; sometimes the "Could not write bytes - broken pipe" was not there, sometimes another message was there "stopping system V runlevel compatibility".

I think I can mount the drive, and hopefully also make it not read-only, is there a file I can write somewhere that will get me into grub?

---

### Post by QIII on 2013-12-01
Try holding the shift key down just as the BIOS/EFI splash is about to close.

---

### Post by ruberad on 2013-12-01
OK, that did seem to be the right place to hold shift and get into grub.

For the benefit of future googlers, my system starts up with (1) text in upper left (identifying drives), (2) BIOS splash saying I can press F2 (3) black with a few two-letter codes flashing by in the lower-right, (4) all dark purple (5) all black (6) same dark purple Ubuntu splash screen with white-->red dots (7) infinite loop as described above. The right time to hold shift for grub is between 3 and 4.

So, I got into grub, and chose 3.8.0.32 recovery, I thought it wasn't going to work because there was a message about "invalid block" something, I was grabbing pen and paper to copy it down and it went away and I was in the grub menu. I tried dpkg, it asked for read/write and I said OK, it didn't work because it couldn't reach internet repositories. Then I tried fsck but it said too late I was already read/write. Then I enabled network (so that's why dpkg didn't work), then did dpkg again, it took a while, I went for a bike ride, when I got back the screen was back, mouse didn't wake it up, but hitting enter both woke it up and made whatever it said go away. So I did dpkg a few more times, tried to read what was going by.

THere were still the same old python import failure messages. This time the last one I saw was in /usr/bin/pycompile line 28, import optparse.

One time dpkg said it was going to upgrade three things: checkbox checkbox-qt duplicity; another time it said 4 things: those three plus python-lazr.restfulclient.

So now that it seems that I can get into grub ok, what's next?

Seems to me all signs point to broken python, if it can't import basic modules like optparse...(maybe failed python-related update?)

---

### Post by Bashing-om on 2013-12-01
ruberad; Well, at least not all bad .

The system still retains some functionality.
Let's do this:
Boot to the Grub menu;
With a normal kernel entry highlighted, hit the "e" key for edit mode -> boot parameters screen; arrow down and across to the term "quiet splash" insert the term "text" - with out the quotes - before "quiet splash" and then delete the term quiet splash, leaving a space before and after "text";
key combo ctl + x to continue the boot process to a tty terminal.
Login - username and password - there is no response to the screen when pass word entered -

OK, Logged into the system ?

do terminal command:
```

sudo apt-get update
sudo apt-get upgrade

```
to get us an idea of the state of the package manager, so we can see what we might be able to do.

[INDENT][INDENT]we can try
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-01
ok, I.m here on the netbook now, faster than booting to live CD all the time.

I did that, update seemed ok, upgrade was a massive failure. tons and tons of python errors, what's left on the screen at the end is /usr/bin/pyclean, line 26 import optparse;  etc etc , lots of python files failing to import lo0ts of thiungs. (sorry, I cant type proper on this miniscule netbook keyboard)

btw the four things it wanted to upgrade was the same 4 as before. Also, now the grub menu said kernel 3.8.0.33, last time I was in grub playing around with dpkg, I had written d0own that it was only 32. I guess my playing around upgraded the kernel!

---

### Post by ruberad on 2013-12-01
I did upgrade agaiun like this: sudo apt-get -y upgrade > upgrade.txt so I can mail/post full results, and I saw 5 times printed to STDERR:
No apport report writen because MaxReports is reached already

Is there maybe some python system log somewhere that I need to clean out?

Is there cmdline way to upload/email my upgrade.txt somewhere, so I dont't have to reboot to live CD again?

---

### Post by ruberad on 2013-12-01
while I'm sitting, I'll type the end of upgrade.txt:


Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycompile"
    import optparse
EOFError: EOF read where object expected
dpkg: error while cleaning up
 subproce3ss installed postinstallation script returned error exit stqaus 1
Errors were encountered while processing:
/var/cache/apt/archives/checkbox0.13.10.amd64.deb
/var/cache/aopt/archives/checkbox-qt0.13.10amd64.deb
/var/cache/apt/archives/diplicity0.6.18-0ubuntu3.3amd64.deb
/var/cache/apt/archives/python-lazr.restfulclient0.12.0-1ubuntu1.1_all.deb



hopefully you can understand through all the typos!

---

### Post by Bashing-om on 2013-12-01
ruberad; Maybe not as bad as you think !

OK we can clear most of those errors; do:
Terminal commands:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update

```
(apt-get update will rebuild the removed indexes)

and now let's do look and see what the status of python is:
```

dpkg -l python

```
My output for reference:
> 
sysop@1304mini:~$ dpkg -l python
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python         2.7.4-0ubunt amd64        interactive high-level object-ori
sysop@1304mini:~$ 

off interest is "ii  python         2.7.4-0ubunt amd64 " the "ii" here shows that python is fully installed and the package manager is in a happy state with python. What is the code in that first column in your output ? Do you have more than one instance of python installed ? Like it shows more than one version ?

And regarding your:
> 
Is there cmdline way to upload/email my upgrade.txt somewhere, so I dont't have to reboot to live CD again?
 nope, not till we get your system to where you can install the software.
(and then we will not need it, huh )

Try this and see what results.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-01
all the same first lines, final line is

ii      python      2.7.3-0ubuntu2.2     interactive high-level object-oriented language (default version)

---

### Post by Bashing-om on 2013-12-02
ruberad; Making progress !

Per packages.ubuntu.com, this is the proper version of python that should be installed:
> 
Package python

precise-updates (python): interactive high-level object-oriented language (default version) 
2.7.3-0ubuntu2.2: amd64 i386

Yours:
"ii python 2.7.4-0ubunt amd64"

What we need to do now is roll that version back to the correct version.

What have you got on your system at this time that we might be able to (re-)install ?
```

ls -la /var/cache/apt/archives | grep "python*"

```
Else we are looking at "wget" that file and "dpkg -i" to install !

But, hey, we can do this.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-02
I think you misread (I've seen you around these forums before -- you must be helping dozens of people at once!), it is your example that printed out "2.7.4-0ubunt amd64", mine says "2.7.3-0ubuntu2.2" -- however my output did not say amd64 -- or I missed that when I typed last night, I'm at work now and won't be able to check until tonight.

---

### Post by Bashing-om on 2013-12-02
ruberad; Hey ! You are correct !

My wires got crossed some how>
Yours :
> 
ii python 2.7.3-0ubuntu2.2 interactive

Which is a match to what should be installed !
> 
precise-updates (python): interactive high-level object-oriented language (default version) 
2.7.3-0ubuntu2.2: amd64 i386


Looking better alla the time !

So now lets see what the package manager sees for a possible problem.
```

dpkg -C

``` That is an upper case "c"

When ya get in from work, and I get my chores done here we will continue this.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-02
OK, will do tonight. Thx for your patience with me!

---

### Post by ruberad on 2013-12-02
Very illuminating: I summarize (let me know if you need more details)

In a mess:
duplicity
checkbox
python-lazr.restfulclient
checkbox-qt

Unpacked but not yet configured (some is stuff I tried to install since The Problem began...)
libbonoboui2-0
gnome-hearts
libgnomeui-0
libgnomevfs2-common
flashplugin-installer
libgnome2-bin
libgnome2-0
mpack

Onlly half configured:
software-center
gconf2
update-notifier-common

---

### Post by Bashing-om on 2013-12-02
ruberad; Hey ,

Let's see what magic the package manager can work:
```

apt-get -f install
dpkg --configure -a

```

Think'n then we may think about (re-)installing the desk top. May do some looking 1st at file ownership in your home.

[INDENT][INDENT]possibilities yet abound
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-02
both of those commands didn't seem to do much, hobbled by python import errors like before.

dpkg -C looks the same.

trying to anticipate, I peeked at permissions in home dir. A variety of chmods, from -rw------- to drxwrxwr-x, two items (dirs) are owned by root, not me: .cpan/ and .gnupg/ They are both dated Sept 27, which is likely the day I installed 12.04

---

### Post by Bashing-om on 2013-12-02
My output for installed packages:
> 
sysop@1304mini:~$ dpkg -l python-lazr.restfulclient
dpkg-query: no packages found matching python-lazr.restfulclient
sysop@1304mini:~$ dpkg -l checkbox-qt
dpkg-query: no packages found matching checkbox-qt
sysop@1304mini:~$ dpkg -l checkbox
dpkg-query: no packages found matching checkbox
sysop@1304mini:~$ 


Lemme re-boot into my 12.04 install . Will see what it looks like there !

Meet ya soonest.

---

### Post by ruberad on 2013-12-02
I did dpkg -l for those and they all have code iFR; I have no idea what packages are bringing those in, I didn't try to bring any of those in explicitly myself.

In the previous list, the pkgs I tried to apt-get are gnome-hearts and mpack. mpack was yesterday because I was trying to see if I could somehow email text files, and gnome-hearts was from a few weeks ago, after software-center was dead, and before I broke booting. Prolly all the gnome stuff is hearts dependencies.

---

### Post by Bashing-om on 2013-12-02
ruberad; Well.

My 12.04.3 standard install:
> 
sysop1@1204-a:~$ dpkg -l python-lazr.restfulclient
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  python-lazr.re 0.12.0-1ubuntu client for lazr.restful-based web services


sysop1@1204-a:~$ dpkg -l checkbox-qt
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  checkbox-qt    0.13.10        QT4 interface for checkbox


sysop1@1204-a:~$ dpkg -l checkbox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  checkbox       0.13.10        System testing application
sysop1@1204-a:~$


Do you get an "ii" for each of these (below) ?
```

dpkg -l ubuntu-dev-tools
dpkg -l python-launchpadlib
##and checking one dependency
dpkg -l python-pkg-resources

```
Maybe we can wade through (re-)configuring/(re-)installing packages (??)
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-02
The python ones are ii, but ubuntu-dev-resources  is code un

Does that mean Unpacked/no-err?

At what point does a complete reinstall (perhaps of 13.04) become the easier option?

---

### Post by Bashing-om on 2013-12-02
ruberad; Sheessh ;

Everything we look at says python is good .. in respect to the "un"  To decypher the code look above the output, the code is a max of four letters relating to the 4 lines above u = Unknown, n= Not (installed) - on that one I may be barking up the wrong tree, not real sure.

When to give up and (RE-)install the operating system.. When you get frustrated chasing down dependencies and why some are not installed or configured.
Be aware I have a code sequence that will attempt to totally rebuild the system, I have tested it and it does work. However, I do not know what control files it utilizes or what the result would be in a badly crippled system. It is a means of least resort prior to (RE-)installing.
(RE-)install is the nuclear solution, and we learn nothing from taking that approach.

Tell me again (re affirm) that these all give "iFR"
> 
4mini:~$ dpkg -l python-lazr.restfulclient
dpkg-query: no packages found matching python-lazr.restfulclient
sysop@1304mini:~$ dpkg -l checkbox-qt
dpkg-query: no packages found matching checkbox-qt
sysop@1304mini:~$ dpkg -l checkbox
dpkg-query: no packages found matching checkbox
sysop@1304mini:~$


And we will, as per the advise (R), re-install them.
Then see where we stand.
[INDENT][INDENT]that is my thoughts
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-02
yup, tried again and all three of those are iFR

---

### Post by Bashing-om on 2013-12-02
ruberad; OK !

Here is a start on this - be aware it is a serious handicap that I do not see that entire output, thus I can not know what the dependency issues are.
Here goes nothing !
```

sudo apt-get install --reinstall python-lazr.restfulclient
sudo apt-get install --reinstall checkbox-qt
sudo apt-get install --reinstall checkbox

```

If at first you do not succeed ->
[INDENT][INDENT]try try again (sky diving excepted)
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-03
all the same piles and piles of pytho nimport errors,and in the end dpkg -l says iFR for all three still

I don't think python can really be ok; scripts in /usr/bin/py* like pyclean pycompile pyhtmlizer pyversions all spit out tons of errors (when invoked with no arguments), complaining that they can't import optparse

See "Original exception was:" transcript above.

Maybe at this point it would be worth it for me to capture some of these (pages and pages) of errors from some of these commands into text files, boot across to liveCD, mount the drive and upload the files so you can see?

---

### Post by ruberad on 2013-12-03
yah, I think python is definitely broke. on the problem desktop, if I do 
$ python
>>>import optparse

I get the same errors

If I do that on this netbook here (ubuntu, I don't know what version but older than 12.04) that works fine

interwebs seems to say there should be a Lib/optparse.py file somewhere, where would that be?

---

### Post by ruberad on 2013-12-03
I found /usr/lib/python2.7/optparse.py (and .pyc) on both machines. Both files a little larger on the problem machine, but probably because it's more updated. .py file seems uncorrupted as far as I can tell.

I will boot over to liveCD and I have many files full of errors from various apt-get and dpkg commands I can upload; if I dont't hear from you I will just pick one.

---

### Post by Bashing-om on 2013-12-03
ruberad;

Well, yeah, If I could see the actual errors I would have a better understanding of what is not going on. We can sure try !
My quick method to mount the operating system from a liveDVD:
```

sudo mkdir /mnt/work
sudo mount dev/sda1 /mnt/work

```

You now have access to the install system IF that install is on the 1st hard drive AND root (/) is installed on that 1st partition.
access as : <some command> /mnt/work/<path_to_some_file or _directory
say -> ls -la /mnt/work/home/ruberad
or cp /mnt/work/home/ruberad/text-file to_where_ever//

One may also mount the install from the file manager nautilus - if you are more comfortable:
```

gksudo nautilus

```
and then browse the install file system.

ReMemBer to (UN)mount when all done:
```

sudo umount /mnt/work

```
or if from nautilus, "unmount" 
!!
//

I am about played out for this session, I may bail on ya at any time.
I will pick this up in my AM .. prior to getting back on my chores -- winter is coming on here and I am still splitting and storing my firewood ..Winter is going to hit hard this week end! (built me a wood shed a couple of weeks ago !)

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-03
ruberad;
To find a file: use the find command:
```

sudo find / -name optparse.py

```
which will search the file system for a match -- takes a bit of time to search through thousands of files .. patience !

[INDENT][INDENT]my bit to help
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-03
dammit, now I'm back over on liveCD and I can't find the .txt files I made; I guess I"ll have to pop over to grub/text login and recreate them in a few different places.

Here however is I think a klew

I did a diff between /usr/lib/python2.7/optparse.py on the problem drive vs. the liveCD (ramdisk?), and they are the same. But then diff says binary files .../optparse.pyc differ.

I wonder if I just go delete (or rather rename) /usr/lib/python2.7/*.pyc if all of python might run correctly (albeit slower) from scripts instead of precompiled versions?

I so appreciate all your help -- don't stay up for me, I can survive on liveCD and the netbook indefinitely, since pretty much all the family ever does is use browsers for gmail etc.

---

### Post by Bashing-om on 2013-12-03
ruberad;
As you think "python" is broke... do this:
```

apt-cache depends python

```
you will get a list of dependencies -> do:
```

dpkg -l <dependency>
##for example:
dpkg -l  python2.7

``` for each and every one of the dependencies.. the status should be "ii" for each, else there is a problem that will have to be dealt with.

what can I say,
[INDENT][INDENT]it is a pain
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-03
ruberad;
I am bailing out on ya for this session. get my beauty rest for my work tomorrow !

catch up with the situation in my AM.

Later

---

### Post by ruberad on 2013-12-03
All right, nighty night. As ever, thanks for all your help!

And for when you next check in, good morning!

So I grubbed back into text login, renamed all the /usr/lib/python2.7/*.pyc to *.pyc.bak (I have a perl script for mass renaming -- perl has never betrayed me like this damnable python!) and now everything seems better! Well almost...

I did aptget update/upgrade, and alls eemed well. Then dpkg -C gave no output; I guess that's good. dpkg -l on those three suspect packages, they all came back ii.

So I shut it all down and gave a try to rebooting, now instead of a screen that flashes between "checking battery state..." and all black, now I have a screen which is frozen on "checking battery state...". I can't tell if maybe it is actually booting, but very very slow because all the precompiled python libs are gone and it's running all-script all the time

I'll let it sit here overnight if necessary, maybe I'll see a login screen in the morning. Maybe I should go in and reinstall python, now that python seems to be somewhat working.

And wondering about the root cause; my guess is early-stage drive failure, in the area of the drive that happens to hold /usr/lib/python2.7/*.pyc

---

### Post by ruberad on 2013-12-03
7 hours and still frozen on "*Checking battery state...          [OK]"

(the OK was there all along, I just didn't type it before). Off to work.

---

### Post by Bashing-om on 2013-12-03
ruberad; OK !

Let's do remove the uncertainty of a corrupted file system:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required:
```

sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

``` lower level as the file system check (fsck) calls "e2fsck" anyway .

I can see no harm in trying to (re-)install "python" may get some additional info as to where the problems may lie:
```

sudo apt-get install --reinstall python

```

Booting: During my work day I will think about updating the "raminitfs" - ram initial file system - Which is what gets wrote from the image in ram to the hard disk. How to verify that the image in ram is in good shape (??) 

Then I have in mind to see what graphics driver is loaded and see if we can start the GUI desk top (???). For now let's keep the irons in the fire to a minimum, The above will keep us busy for a while.

[INDENT][INDENT]it's all a process of learning
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-03
Cool, I never heard of e2fsck or raminitfs before; the raminitfs is that for the real OS or just the live CD?

Before in liveCD i was mounting the drives using the disk utility gui (so they got mounted to /media/*), I will go to liveCD and not mount and try the e2fsck command as you suggest, and also try a python reinstall.

Googling python compile a little bit, it seems that py can be compiled into pyc not only from external commands, but also from within scripts; is it maybe the case that python will automagically compile .py modules as they are used? Would that take 7+ hours (as various python capabilities are involvedin bootup?)

Graphics driver; I know I have no separate video card, just what was on teh motherboard. I was recently disappointed that when I installed GoogleEarth (shortly before The Troubles), it could not render anything, it popped up a message about insufficient gpu for 3D or something.

---

### Post by Bashing-om on 2013-12-03
ruberad; Welp;

I do not think any re compiling is done at boot time: 
The way it works:
Here's an abbreviated version of what happens when you turn the power on after the machine has been shut down for a while:

First, code in the BIOS chip on the motherboard gets loaded into memory automatically and begins running. Next, the Power-On Self Test (POST) code checks all of the hardware to make certain it's working. In the process it clears all of the RAM space except the very small part it's using to run the POST.

When the POST completes, the BIOS code then begins loading the operating system code into memory. This becomes a "chicken-or-egg" situation, since loading the code requires code to already be there and the BIOS chip isn't large enough to hold all of the necessary code. The solution, in most Linux distributions, is to create a pseudo-disk in RAM, and load it with an abbreviated copy of the system that has all the things needed to load the full system, but nothing else (such as a normal user interface or keyboard drivers). That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe. Once it's loaded, control goes over to it, and it begins loading the actual full system from the "vmlinuz" file. While all this is going on, you see only the splash screen (but you can edit GRUB's actions to see play-by-play reports of it all, if you want to).

When the full system is all loaded, control goes to the "init" process, which sets up the console and virtual terminals, loads the window manager and display code, and lets you log in. The init process continues to run in the background until you shut down the machine, allowing the system to do its work more or less invisibly.

You can view the log of all this by firing up a text editor and looking at /var/log/syslog. This file records each significant event -- and gets huge in a hurry.

Another way of looking at the boot process:

Here is a typical sequence of phases your system goes through as it boots:

    bios screen
    Black with blinking cursor (short). Disk activity LEDs blink and flicker.
    Purple without cursor (long)
    Boot splash graphic (via plymouth)
    Black screen (short). Backlight may go off at this point.
    Maybe more plymouth
    Login screen. Sound (e.g. drums) plays 

Here's what's going on under the hood during each of these steps:

    BIOS detects hard drive with a bootloader (grub) present and starts it
    grub selects a kernel and loads it
    If the kernel supports Mode Setting (KMS), it puts the video card into its preferred resolution using a frame buffer (vesafb). The framebuffer is initialized with a purple background.
    plymouth displays a bootsplash image.
    gdm is started, which instantiates a new X session for the login screen to replace the framebuffer's graphics
    X attempts to put the card into one of its higher resolutions, such as the preferred resolution
    The login screen is drawn on the screen 
---------------
This may be more than you wanted to know, but the point is, at boot re-compiles are not done. It is all in the "image" loaded into ram, and what is then written out to hard disk.

At present it appears the package manager is all happy, so we are looking at the boot process, see what is failing where. Now-a-days with no logging of the booting (some in syslog and dmesg) kinda tough to isolate where the process is failing.
What can be done is to boot in text mode, get real quick on the keyboard and pause the booting process to read the messages output to the screen in an attempt to see what is going on .. May have to (re-)boot several times to get a comprehension of where/why !

[INDENT][INDENT]but;
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-03
Great, thanks! Tonight I will e2fsck both ssd partitions from liveCD, and try to inspect /var/log/syslog to see if there are any clues from the currently-hung boot; then grub back into text login and try to reinstall python. I'll let you know how it shakes out.

---

### Post by Bashing-om on 2013-12-03
ruberad; Roger that !

I will keep an eye out for ya.

[INDENT][INDENT]I so enjoy a good puzzle
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-03
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/**sda1**
Inodes that were part of a corrupted orphan linked list found.                            

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? yes

Inode 136204 was part of the orphaned inode list.  FIXED.
Deleted inode 137566 has zero dtime.  Fix? yes

Inode 138044 was part of the orphaned inode list.  FIXED.
Inode 141182 was part of the orphaned inode list.  FIXED.
Inode 783339 was part of the orphaned inode list.  FIXED.
Inode 785958 was part of the orphaned inode list.  FIXED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -557147 -558711 -3299338
Fix? yes

Free blocks count wrong for group #17 (3218, counted=3220).
Fix? yes

Free blocks count wrong for group #100 (20423, counted=20424).
Fix? yes

Free blocks count wrong (2481391, counted=2481394).
Fix? yes

Inode bitmap differences:  -136204 -137566 -138044 -141182 -783339 -785958
Fix? yes

Free inodes count wrong for group #16 (0, counted=3).
Fix? yes

Free inodes count wrong for group #17 (2, counted=3).
Fix? yes

Free inodes count wrong for group #96 (6, counted=8).
Fix? yes

Free inodes count wrong (672537, counted=672543).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  304737 inodes used (31.18%)
      88 non-contiguous files (0.0%)
     271 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 256560/37
 1424654 blocks used (36.47%)
       0 bad blocks
       1 large file

  205568 regular files
   36424 directories
      57 character device files
      25 block device files
       0 fifos
       9 links
   62650 symbolic links (48046 fast symbolic links)
       4 sockets
--------
  304737 files

---

### Post by ruberad on 2013-12-03
similar for /dev/sda6 (mounted on /home, not so critical), ending with

Pass 5: Checking group summary information

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda6: ********** **WARNING: Filesystem still has errors** **********


   45347 inodes used (1.85%)
    1704 non-contiguous files (3.8%)
       9 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 45280/45
  794417 blocks used (8.13%)
       0 bad blocks
       1 large file

   39090 regular files
    6234 directories
       0 character device files
       0 block device files
       0 fifos
4294967273 links
      16 symbolic links (16 fast symbolic links)
       2 sockets
--------
   45244 files

---

### Post by Bashing-om on 2013-12-03
ruberadl Well !

That do answer a bunch of questions, Huh .

What are we looking at for partitioning ?
```

sudo fdisk -l

```

I have more faith in the system than I do in my own abilities to know how to correct a file system problem .. thus is:
```

sudo e2fsck -f -y -v /dev/sda6

```

I would run that from the liveDVD a couple of times, see if it gets cleaned up. Providing that sda6 is formatted for file system type ext,

[INDENT][INDENT]not great but
[INDENT][INDENT][INDENT]making progress 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-03
I mounted the SSD / partition and copied syslog. I opened it in LibreOffice and saved it as docx to make it a type that I could upload as a 'media' object on my blog. Here is the link:

[http://ruberad.files.wordpress.com/2013/12/syslog.docx](http://ruberad.files.wordpress.com/2013/12/syslog.docx)


Now back to grub/text to try reinstalling python.

---

### Post by ruberad on 2013-12-03
python reinstall seemed to go smoothly. There are /usr/lib/python2.7/*.pyc again (but not as many as I have .pyc.bak saved off -- but of the ones that are there, a bunch of them are different than the corresponding .pyc.bak). I forgot to check whether any .pyc had gotten there automagically before I reinstalled.

HOWEVER, I am now back to "*checking battery      [OK]", flashing again.

I gotta go out for an hour or two. If there are any instructions here for me to follow when I get back, I will follow them!

thx as always...

---

### Post by Bashing-om on 2013-12-03
ruberad;

Is the package manager still happy?
```

sudo apt-get install -f

```
I have nothing installed on my work station to read a docx file . I do not recall right off hand what conversion program I last used to make O office able to read the conversion.

Any idea how far in the boot process you are getting before getting hung at the "checking battery" ?
On my system I can pause the boot process and read the boot messages by selectively pressing ctl+s to pause
and ctl+o to continue.

Tell ya what; try this just as a wild guess.
At grub's boot parameter in addition to text also add nomodeset.
The nomodeset option disables kernel mode setting, and may get us somewhere.

[INDENT]sometimes I do wonder
[/INDENT]

---

### Post by ruberad on 2013-12-04
U got no LibreOffice? ANyways, how about a 427-page landscape PDF? [http://ruberad.files.wordpress.com/2013/12/syslog.pdf](http://ruberad.files.wordpress.com/2013/12/syslog.pdf)

I'll give a try to nomodeset and ctrl-s, but it's not like I see a lot of text flying by at any point. Maybe it's just because the boot process is super fast with SSD?

---

### Post by ruberad on 2013-12-04
> **Bashing-om said:**
> 
sudo apt-get install -f
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded

---

### Post by ruberad on 2013-12-04
I tried kernel *.33 recovery  mode, ran fsck, saw weird errors (udisk-id-? bus error?), resumbed boot, and am stuck in tons and tons of errors like this repeating all the time.

ata3.00: status: { DRDY ERR }
error { UNC }
end_request: I/O error, dev sda sector NNNNNNN
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
irq_stat 0x400000001
failed command: READ DMA
cmd c8/blahblah/e0 tag 0 dma 4096
res 51/blahblah/e0 Emask 0x9 (media error)

That's a toasty disk, right?

&#&$%&@%* refurbs

---

### Post by ruberad on 2013-12-04
I'm not sure how to use nomodeset -- I put that in with text and get rid of queit splash, then I log in and then... ?

---

### Post by Bashing-om on 2013-12-04
ruberad; Just to be honest, Yeah.

That is indicative of a toasted hard disk.
I know this is hard to consider, but, with all those errors I would:
Now, this is just what I would do:
First reseat the cables for the drives (maybe even change those cables out, make sure there are no kinks, twist, or hard bends);
still with problems:
edit: Check that disk with the "disk utility -> SMART report;
Zero out that disk with the "dd" - disk destroyer - command;
and (RE-)install the operating system.

Then, still with disk situations,;
It is time to swap that hard disk out.

Harsh ->
[INDENT][INDENT]but that is the way it is.
[/INDENT][/INDENT]

---

### Post by ubfan1 on 2013-12-04
With the caveats that I know little about SSDs or how effective TRIM might be, after your reinstall, maybe you should think about what you can do to minimize SSD writes, like you would on a USB flash media.  At one extreme are the distributions like Puppy which run totally in ram, to having selected users' home directories in ram, to moving heavily written locations (/tmp, /var/log, /var/run, and browser cache) into ram.  You may find more details on most of these, which apply to Ubuntu, at [www.systemateka.com/usbboot.html](www.systemateka.com/usbboot.html)   Hope something works for you.  SSDs do have a lifespan, and starting with a refurb, you really don't know how much is left.

---

### Post by ruberad on 2013-12-04
Yes, thx, I have reached the end of the line with Crucial since this is now the THIRD 64gb v4 SSD that has failed on me (first new, then two warranty replacements they gave me refurbs). I will give them the chance to warrantee me up to a better-than v4 SSD, looks like the smallest/cheapest option they currently offer would be M500 120GB. If not, then I guess I'm back to resting my Ubuntu on spinning plates.

---

### Post by ruberad on 2013-12-04
And of course I want to thank you mucho once again, your time and advice were invaluable to me.

---

### Post by Bashing-om on 2013-12-04
ruberad; I feel for you !

If the SSD is still under warranty, yeah, best see what the merchants will do for you.
Ya got 'buntu installed on a "spare" spinning drive ? To hold you over in the meantime ?

Sad state of affairs, but there is a solution.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-05
Yes, still under warranty, and as it happens I do have an old 'buntu installed on a spinning drive.

So I got that goin for me...

So now I'm wondering for the upcoming reinstall, 12.04 or 13.10? I chose LTS for the reliability, but you can see how that's worked out for me (not that I'm blaming 12.04!)

I didn't have any problems with 12.04 (when it was working), so I can't imagine what benefit 13.10 would give me. I guess I'll stick to what I know.

---

### Post by Bashing-om on 2013-12-05
ruberad; Well .. well ...


My My, smart guy ain't ya ! No moss growing on your rock.

Version 13.10 is supposed to be lighter and a lot faster. But it is not a LTS version. Here is a thought - what I am going to do - install 13.10 and in April there-a-bouts install the next LTS version 14.04 ... And then take advantage of all the advancements the hard working developers have accomplished !


However, my installs will be minimalistic; I prefer fast, efficient, no frills, and to observe the KISS principal. But, too, I will make a standard desktop install of 14.04 for relating purposes.
I do keep good backups - I do break my system - and have had to (RE-)install ! Point being I can (RE-)install in about 20 minutes, and back up in great shape !  _ Thanks to the powers that be _ I have a fast wired internet connection !

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-05
Yah, I can wait for 14.04 LTS.

My reinstalls are not too bad, since I maintain separate partitions for /home and /data. I actually don't fully backup, I just use dropbox.net for select directories with important files, and I pay for flickr pro to back up all family digiphotos.

---

### Post by Bashing-om on 2013-12-05
ruberad; Impeccable !

Come on home new SSD !
[INDENT][INDENT]all fired up and;
[INDENT][INDENT][INDENT]no place to go
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ruberad on 2013-12-05
However...

I made a 13.10 bootable usb stick to try out, and WOW this really is a lot snappier than 12.04 live CD -- is that more because of try out from usb vs cdrom? Or is 13.10 really that much faster?

---

### Post by Bashing-om on 2013-12-05
ruberad; By hearsay;

13.10 is faster, a lot faster,. Maybe by next week  I will be in a position to install 13.10 and see for myself. Some of your perception is the comparrison of cd/usb .. yeah usb is faster; install onto hard disk and you can imagine how much faster that will be !
However, I do not perceive Lubuntu 13.10 as faster, running it on old hardware. I have lubuntu 13.10 installed on this box also, but I have not messed with it since I did the upgrades .. maybe I should (??),

accolades is all I have heard of for 13.10 .. and very few disgruntlements.
Version 14.04 release is just around the corner ..can only be better !

[INDENT][INDENT]all things can happen to the good
[/INDENT][/INDENT]

---

