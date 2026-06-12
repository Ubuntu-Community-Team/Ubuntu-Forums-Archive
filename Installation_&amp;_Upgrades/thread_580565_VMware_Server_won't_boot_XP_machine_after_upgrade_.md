---
title: "VMware Server won't boot XP machine after upgrade to Gutsy 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2007-10-18
I just upgraded to Gutsy a couple days ago, using the -d option on update manager, and I'm just now trying to start VMware.  VMware Server loads just fine, but when I go to select a virtual machine, I get a popup box that says the following:

Unable to change virtual machine power state: The process exited with an error:
End of error message.

I've noticed there is a new version of VMware server out, but nothing about it has come down from update manager about it, just a popup box within VMware.  I've not yet visited their site to download the manual installer.  I've had a lot of problems trying to do a manual install in the past...


On the side, I am having a small problem with compiz missing it's control panel, giving me errors when I try to install it.  You can read about that here, incase this problem might be associated.
[http://ubuntuforums.org/showthread.php?t=578937](http://ubuntuforums.org/showthread.php?t=578937)

---

### Post by rokclimb15 on 2007-10-18
You should completely remove vmware-server and reinstall it.  It depends on your kernel headers to work properly, and those were upgraded during the Gutsy install.

---

### Post by davidshere on 2007-10-19
I upgraded this morning to 7.10 and it appears to have whacked VMWare Player on my machine.  I'm glad I did this at work first because my computer at home has some virtual machines on it with data I don't want to lose.

I saw when it did the "cleanup" at the end that it was removing vmware-player, but I figured that it had installed an update.  I hope there aren't other things on my machine that were whacked but not replaced.

I can reinstall vmware player; it's not really a problem; it just seems weird that an update did this.

Hmm... I just tried to reinstall and it says "VMware Player cannot be installed on your computer type (i386) Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by tact on 2007-10-19
> **rokclimb15 said:**
> You should completely remove vmware-server and reinstall it.  It depends on your kernel headers to work properly, and those were upgraded during the Gutsy install.

Presuming vmware-server was installed from source originally (no other way really) then you do not have to remove it and reinstall it.

just go to a terminal prompt and type 

```
/usr/bin/vmware-config.pl
```

This will reconfigure/compile vmware server with the new kernel headers.

(and ANY time you have a kernel change you will have to do this again).

If there are errors in the compile and modules like vmmon and vmnet refuse to compile - its likely because the vmware-server source you have doesnt know about the newer linux headers that come with your latest new kernel.  So google for the "vmware-any-any" patch.  Download the latest one you can find, and follow the readme to apply the patch to your vmware-server source.   After this patch is applied vmware-server will compile with "any-any" version of linux headers.

---

### Post by davidshere on 2007-10-19
Okay I'm sorry I guess this is a thread about VMWare Server and I'm complaining about VMWare Player.  I'll start another thread.

---

### Post by diablo75 on 2007-10-19
> **tact said:**
> Presuming vmware-server was installed from source originally (no other way really) then you do not have to remove it and reinstall it.

just go to a terminal prompt and type 

```
/usr/bin/vmware-config.pl
```

This will reconfigure/compile vmware server with the new kernel headers.

(and ANY time you have a kernel change you will have to do this again).

If there are errors in the compile and modules like vmmon and vmnet refuse to compile - its likely because the vmware-server source you have doesnt know about the newer linux headers that come with your latest new kernel.  So google for the "vmware-any-any" patch.  Download the latest one you can find, and follow the readme to apply the patch to your vmware-server source.   After this patch is applied vmware-server will compile with "any-any" version of linux headers.

That file doesn't appear to be in my usr/bin/ folder.  What's the best way to go about uninstalling and reinstalling?  Synaptic?

---

### Post by Lucio74 on 2007-10-20
Hi all,
I have got exactly the same problem as Diablo75. Upgraded from 7.04 to 7.10 on a Dell Latitude D620 a couple of days ago. Same error when launching the virtual machine inside vmware-server. Couldn't find /usr/bin/vmware-config.pl file either to reconfigure.
vmware-any-any-update114 patch did not solve the problem.

vmware-server is not the the repo in 7.10 should unistall the old version, download the source from vmware web site and install it ex-novo?

Please help!

Lucio

---

### Post by peshooo on 2007-10-20
I had similar problem after the upgrade to 7.10.
I found one way to use VMware - run Ubuntu with the previous kernel version (from the Grub). Reconfiguring with the new kernel threw errors.
I hope they fix it soon.

---

### Post by satx on 2007-10-20
Same here. Upgraded to 7.10. Get the power-state message. Do not have file config-pl in /usr/bin.

---

### Post by diablo75 on 2007-10-20
So is the best method simply to uninstall and reinstall with the latest version of VMware Server?  Or can/will this be fixed soon via some other simpler means?

---

### Post by Roostey on 2007-10-21
I'm running 64 bit gutsy, trying to start a 32 bit WinXP install in vmware player 2.  I go the same issue and the following fixed it (courtesy of galileux who found the solution)

```
sudo apt-get install ia32-libs
```

A 32 bit vm needs 32 bit libraries to be able to run on 64 bit linux

---

### Post by SquishyMarbles on 2007-10-21
You have to run the vmware-config.pl script every time you update the Linux kernel (which the upgrade definitely did).  This script rebuilds all the kernel modules for your running kernel.  You have to do this as root, as well, so probably "sudo vmware-config.pl."  If it's not in /usr/bin, then try "locate vmware-config.pl," then run whatever it finds.

Edit, that said, uninstalling and reinstalling it shouldn't be a problem, either, although it'll take more time.  If you have VMWare Server installed, and you can't find vmware-config.pl, then please let me know how you installed it in the first place, but also, reinstalling is the only option without this script.

---

### Post by remmosf on 2007-10-21
Hey

I can confirm that it is possible to install a new version of vmware server. 

I have several performance issues after installing though. Keyboard and mouse events are delayed and overall performance is degraded so I might have done something wrong.

Using Synaptic Package Manager I found the packages with vmware in them and uninstalled them.

Then I followed this link

[http://www.williambrownstreet.net/wordpress/?p=94](http://www.williambrownstreet.net/wordpress/?p=94)


And was able to run vmware server. But I have to say again: performance is very bad. Hopefully someone has a clue.

Cheers

---

### Post by Gimli on 2007-10-21
I would like to report that I have had the same problem, did a reinstall as per the post of remmosf and it worked like a dream. I don't have any performance issues on the vmware server.

---

### Post by Raedwald on 2007-10-21
> **SquishyMarbles said:**
> You have to run the vmware-config.pl script every time you update the Linux kernel (which the upgrade definitely did).  This script rebuilds all the kernel modules for your running kernel.  You have to do this as root, as well, so probably "sudo vmware-config.pl."  If it's not in /usr/bin, then try "locate vmware-config.pl," then run whatever it finds.

Edit, that said, uninstalling and reinstalling it shouldn't be a problem, either, although it'll take more time.  If you have VMWare Server installed, and you can't find vmware-config.pl, then please let me know how you installed it in the first place, but also, reinstalling is the only option without this script.

Installed VMWare from Package Manager under 7.04.

There is no vmware-config.pl on the box at all (other than a -network.pl). 

Seems that whilst VMWare is there - it isn't, sort of thing!

So it looks like a reinstallation is called for then to get round this one.

---

### Post by potion on 2007-10-21
I'm dealing with the same situation. VMware always worked like a charm, but after the upgrade to 7.10, I get the error quoted in the first post. And there's no vmware-config.pl anywhere. I had installed from the repos. Anyway, the good news is that following peshooo's suggestion I was able to start up using the previous kernel version and then I could run VMware. Backed up everything I need, and now I'm gonna see about reinstalling. Or rather, installing 1.0.4, since I had 1.0.3 before.

---

### Post by diablo75 on 2007-10-21
Anybody else here wish VMware would publish their stuff as a deb file for once?  I hate downloading the binaries.  I mean, normally this is a piece of cake, but the last time I tried to install VMware from a binary tar, it would do stuff like complain about VMware already being on the system, and I'd have to go through and find certain folders to delete off my system before I could get it to work.  Still, this isn't that big of a deal, but I complain mostly because I wouldn't want to find myself facing a slew of clients calling me on their phone with this kind of issue and me having to go in and take care of uninstalling/reinstalling VMware for them.

---

### Post by nelson.bolanos on 2007-10-23
I had installed on 7.04 with automatix, had the same problems as above, after reinstalling from source, my VM's are up and running, thanks for your help, now I have the vmware-config.pl in /usr/bin.
:)
Guess that I'll know what to do in 6 months :D :D
:popcorn:

---

### Post by treblesix on 2007-10-23
I have had the same problem with VMWare Server console.and I don't have the config file stated in previousd post, only a network one.

It works fine for remote virtuals though.

---

### Post by fridaythe14th on 2007-10-23
**Here's the bug report**: [https://bugs.launchpad.net/ubuntu/+bug/155362](https://bugs.launchpad.net/ubuntu/+bug/155362) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

---

### Post by treblesix on 2007-10-24
I have got this working now,  you need to go the following.

Remove VMWare.

Then follow the steps found here...........

**[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)**

If you get this error when trying to do the tutorial..............

A previous installation of a VMware product has been detected
If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.
If it was installed through Ubuntu, you must purge (completely remove) the old package.

run this ........
**sudo rm -Rf /etc/vmware/**

then try the tutorial again. It worked for me :)

-==edit==--

Amended URL

---

### Post by Chuckels550 on 2007-10-24
Re: VMware Server won't boot XP machine after upgrade to Gutsy 7.10 

--------------------------------------------------------------------------------



> I have got this working now, you need to go the following.

Remove VMWare.

Then follow the steps found here...........

[http://ubuntu-tutorials.com/2007/09/...on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/...on-ubuntu-710/)

If you get this error when trying to do the tutorial..............

A previous installation of a VMware product has been detected
If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.
If it was installed through Ubuntu, you must purge (completely remove) the old package.

run this ........
sudo rm -Rf /etc/vmware/

then try the tutorial again. It worked for me 

Link provdies a 404 error

---

### Post by treblesix on 2007-10-24
The page must have moved, i have fixed the link

---

### Post by diablo75 on 2007-10-24
This is what happened when I got to step 7 in the tutorial:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [no] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

```

How do I fix this?

---

### Post by treblesix on 2007-10-25
Did u compile with the patch, not with the orginal installer?  Looks like your includes are missing. Did u install the build-essential sources ?

I am uincluding the page here ,as the link keeps screwing up.

[B]

Installing VMWare Server on Ubuntu 7.10

   1. Download VMware Server source from the [VMware website.]("http://vmware.com/download/server/") 
   2. Download this [installer patch.]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz")
   3. Extract all the archives to some location on your system (tar -zxvf VMware-server* ; tar -zxvf vmware*)
   4. Ensure that you have build-essential installed in order to compile these sources (sudo aptitude install build-essential)
   5. Run sudo ./vmware-install.pl located within the vmware-server-* unpacked archive.
   6. Select all the default options *EXCEPT* do not compile the modules at this point. (Do you want this program to try to build the vmmon module for your system? NO)
   7. Run sudo ./runme.pl located within the vmware-any* archive. This will launch step 8.
   8. Select the default options and this time answer YES to compile the proper modules.
   9. Install the xinetd server (sudo aptitude install xinetd)
  10. Run vmware-server using the command vmware or via your Applications Menu.

Basically, at this point, VMware Server needs to be installed manually from source until the canonical commercial repository catches up and Ubuntu 7.10 is final. Until then this should work for manually installing.

note: if you update your kernel you will need to re-run the scripts to regenerate and recompile VMware Server for your updated kernel. I&#8217;m guessing this close to beta and final releases that we wont have any more kernel updates.. but I&#8217;m sure that will soon prove me wrong. Just be aware.

[/B]

---

### Post by diablo75 on 2007-10-25
The build-essential package is installed.

I followed that step by step to the letter at least 3 times in a row now, and I am still getting the same message (What is the location of the directory of C header files that match your running kernel?).

How do I "go back to square one" with this mess now?  Can I clean out all the VMware related files that this stuff was copied into and start the install from scratch with a clean slate, so to speak?  Or would that be just as good as what I've done; run sudo ./vmware-install.pl, telling it no (to the question about compiling a module) which goes to the command line, then I go to the updater folder and invoke a sudo ./runme.pl, and follow the defaults, telling it to compile this time around, and I get that message up there ^

I really need to get my machines running.  Please help!

---

### Post by Somatik on 2007-10-25
diablo75, see this thread for a fix to your problem: [http://ubuntuforums.org/showthread.php?t=591374](http://ubuntuforums.org/showthread.php?t=591374)

---

### Post by veloce on 2007-10-25
> **diablo75 said:**
> The build-essential package is installed.

I followed that step by step to the letter at least 3 times in a row now, and I am still getting the same message (What is the location of the directory of C header files that match your running kernel?).

How do I "go back to square one" with this mess now?  Can I clean out all the VMware related files that this stuff was copied into and start the install from scratch with a clean slate, so to speak?  Or would that be just as good as what I've done; run sudo ./vmware-install.pl, telling it no (to the question about compiling a module) which goes to the command line, then I go to the updater folder and invoke a sudo ./runme.pl, and follow the defaults, telling it to compile this time around, and I get that message up there ^

I really need to get my machines running.  Please help!

You are missing the linux headers:

sudo aptitude install  linux-headers-'uname -r' 

You probably don't need the any to any patch with v1.04 - I didn't.

---

### Post by diablo75 on 2007-10-26
Tried to install the headers using this line:

sudo aptitude install linux-headers-'uname -r' 

Still get the same error about my linux headers missing.

Question about the above command.  What's with the 'uname -r'

Is that supposed to be in quotes.  Does the word uname mean Username, and am I supposed to swap my username in there in place of it?

```
sudo aptitude install linux-headers-'uname -r' 
```

```
zeke@zeke-desktop:~/Desktop/vmware-server-distrib$ sudo aptitude install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**Couldn't find any package whose name or description matched "linux-headers-uname -r"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
zeke@zeke-desktop:~/Desktop/vmware-server-distrib$ 

```

---

### Post by AndyCat on 2007-10-26
Hello there. I had the same problem when my 7.04 updated to 7.10. I had to install VMware server again and took the oportunity to upgrade the version to 1.0.4.
Try this if you still have the same problem.
[http://ubuntuforums.org/showthread.php?t=592636](http://ubuntuforums.org/showthread.php?t=592636)

---

### Post by Somatik on 2007-10-26
> **diablo75 said:**
> Tried to install the headers using this line:

sudo aptitude install linux-headers-'uname -r' 

Still get the same error about my linux headers missing.

Question about the above command.  What's with the 'uname -r'

Is that supposed to be in quotes.  Does the word uname mean Username, and am I supposed to swap my username in there in place of it?

```
sudo aptitude install linux-headers-'uname -r' 
```

```
zeke@zeke-desktop:~/Desktop/vmware-server-distrib$ sudo aptitude install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**Couldn't find any package whose name or description matched "linux-headers-uname -r"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
zeke@zeke-desktop:~/Desktop/vmware-server-distrib$ 

```

just run the command and copy paste the result
example
fdb@mrblack:~$ uname -r
2.6.22-14-386
fdb@mrblack:~$ sudo aptitude install linux-headers-2.6.22-14-386

---

### Post by diablo75 on 2007-10-26
> **Somatik said:**
> just run the command and copy paste the result
example
fdb@mrblack:~$ uname -r
2.6.22-14-386
fdb@mrblack:~$ sudo aptitude install linux-headers-2.6.22-14-386

Thank you!  This worked.  Now, if I could get my networking on my VM's to work again, life would be uber peachy.  Alas, [another thread]("http://ubuntuforums.org/showthread.php?t=593203").... :(

---

### Post by xph1010 on 2007-10-27
thanks everyone, i followed the steps and everything finally works now. cheers.

---

### Post by mrhirsh on 2007-10-31
I have one data file that I created in VMWare, but do not have a recent backup.

Before I "follow the steps" I assume I will lose the XPPro Virtual Machine and all data contained on it, correct?

Can someone direct me to "finding" that file from my Gutsy Desktop, so I can back it up, then do the reinstall . . . unless someone has a better suggestion.

Thanks,

---

### Post by diablo75 on 2007-10-31
> **mrhirsh said:**
> I have one data file that I created in VMWare, but do not have a recent backup.

Before I "follow the steps" I assume I will lose the XPPro Virtual Machine and all data contained on it, correct?

Can someone direct me to "finding" that file from my Gutsy Desktop, so I can back it up, then do the reinstall . . . unless someone has a better suggestion.

Thanks,

Your virtual machine's data is stored in var/lib/vmware-server/Virtual Machines.  You can use your file manager to browse to the folders.

Simply copy (or cut) the files inside the "Virtual Machines" folder to a separate directory.  After the upgrade, you can copy the files back in, and then you'll have to "Open a virtual machine" to add your machine back to VMware-server inventory.  If you get a popup box when you start the machine up again for the first time, hit "Keep" or "Always Keep".

Though backing up your data isn't necessary, as the install program will not delete any files or folders that it didn't create itself, it's not a bad idea, and it's good exercise to see where your data is located.

---

### Post by mrhirsh on 2007-11-01
Thanks for the info but . . . .

I followed the trail you gave, but the only program I installed in my VMware (besides the XP Pro OS) is Quickbooks (not a suitable replacement in linux).  I have a data file in there that I want to back up before I do the upgrade.

Only thing I see is the XP Pro folders, which I can't open, but no Quickbooks.  Any other thoughts?

thanks for your help.

---

### Post by diablo75 on 2007-11-01
The only way you can access the files in your virtual machine is to actually start your virtual machine up.  All the data that in the C: of the virtual machine is stored within the data files contained in the path I gave you in the last post.  The entire fake hard drive is just 1 or few files, and NOT an actual directory or folder that you can just open with Ubuntu.

If there is a utility out there that allows you to access this data separate from VMware, I don't know about it.  If I were you, I would simply back up the entire virtual machines directory, install the latest version of VMware per the steps detailed in this thread, and then copy your VMfiles back to their original location.  And technically, moving this data back and forth isn't necessary, but good practice.

---

### Post by veloce on 2007-11-03
> **diablo75 said:**
> 
If I were you, I would simply back up the entire virtual machines directory, install the latest version of VMware per the steps detailed in this thread, and then copy your VMfiles back to their original location.  And technically, moving this data back and forth isn't necessary, but good practice.

I have never lost any vms from upgrading, uninstalling, or re-installing.

---

### Post by akba0012 on 2007-11-14
I have royally screwed up VMWare on my computer after upgrading to 7.10

This is what i'm getting....


```
fahim@Central:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmnet
vmmon

Execution aborted.

```

any help? I'm not sure how to remove these. and they seem important to networking. I have searched everywhere and no one else seems to have ever have had the problem. I have tried removing VMWare in from the Synaptic Package Manager and also the "rm" command. but... i'm still stuck on this.

---

### Post by veloce on 2007-11-15
> **akba0012 said:**
> I have royally screwed up VMWare on my computer after upgrading to 7.10

This is what i'm getting....


```
fahim@Central:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmnet
vmmon

Execution aborted.

```

any help? I'm not sure how to remove these. and they seem important to networking. I have searched everywhere and no one else seems to have ever have had the problem. I have tried removing VMWare in from the Synaptic Package Manager and also the "rm" command. but... i'm still stuck on this.

Just to be sure I understand your problem:
[LIST]
[*]before the upgrade you had vmware server installed from the repositories
[*]after upgrade, you uninstalled from the repositories
[*]you then installed from the 1.04 package downloaded from vmware
[/LIST]

During installation you got that error.  Is this all correct?

Sounds to me like the uninstall didn't work properly. Now that you have bits of two versions, uninstall will be even harder.  I suggest you run the uninstall script then judiciously use rm to get rid of anything left.

use "locate vmware" to find stuff that has been left behind.  

For your specific problem, use "locate vmnet" and locate "vmmon" to get all of the old versions out.

then you can run the install script for the latest version again.

good luck.

---

### Post by akba0012 on 2007-11-15
> **veloce said:**
> Just to be sure I understand your problem:
[LIST]
[*]before the upgrade you had vmware server installed from the repositories
[*]after upgrade, you uninstalled from the repositories
[*]you then installed from the 1.04 package downloaded from vmware
[/LIST]

During installation you got that error.  Is this all correct?

Sounds to me like the uninstall didn't work properly. Now that you have bits of two versions, uninstall will be even harder.  I suggest you run the uninstall script then judiciously use rm to get rid of anything left.

use "locate vmware" to find stuff that has been left behind.  

For your specific problem, use "locate vmnet" and locate "vmmon" to get all of the old versions out.

then you can run the install script for the latest version again.

good luck.

Yes I believe I had VMServer or Workstation installed ( I was able to run windows as a VM) before the upgrade. And then I tried to install the new VMServer 2.0 on top of my existing build of VMWare. Then I realized that I had to uninstall everything since VMWare was not booting up. So then I tried to run the uninstall script to no avail, and then removed the packages from Synaptic Package Manage. And now I left with with this. 

locate vmnet vmmon came up with nothing. i think cause its because they are virutally mounted and I need to somehow unmount them without VMware. The Uninstall script is not working either... I think i'm going to need a clean install of Ubuntu to fix this :(

---

### Post by veloce on 2007-11-15
> **akba0012 said:**
> Yes I believe I had VMServer or Workstation installed ( I was able to run windows as a VM) before the upgrade. And then I tried to install the new VMServer 2.0 on top of my existing build of VMWare. Then I realized that I had to uninstall everything since VMWare was not booting up. So then I tried to run the uninstall script to no avail, and then removed the packages from Synaptic Package Manage. And now I left with with this. 

locate vmnet vmmon came up with nothing. i think cause its because they are virutally mounted and I need to somehow unmount them without VMware. The Uninstall script is not working either... I think i'm going to need a clean install of Ubuntu to fix this :(

Vmware server **2.0**? ***Beta software!!!!!***, that's why no one else has your problem!  You should talk directly with vmware - they should be interested in this as part of their beta testing program.

Those items are not virtually mounted - they are bits added to your ubuntu system by vmware to help run vms (vmnet for the virtual networks and vmmon to monitor the vms).  I can "locate" them on my running system.

But yes, you may need a clean install of Ubuntu to fix this.  In fact, I'm not so sure that the upgrade to gutsy is a good idea for anyone - I eventually did a fresh install after numerous problems.  I now have all non-system bits on a separate partition so when the next upgrade comes along I can re-install more easily.

---

### Post by akba0012 on 2007-11-15
> **veloce said:**
> Vmware server **2.0**? ***Beta software!!!!!***, that's why no one else has your problem!  You should talk directly with vmware - they should be interested in this as part of their beta testing program.

Those items are not virtually mounted - they are bits added to your ubuntu system by vmware to help run vms (vmnet for the virtual networks and vmmon to monitor the vms).  I can "locate" them on my running system.

But yes, you may need a clean install of Ubuntu to fix this.  In fact, I'm not so sure that the upgrade to gutsy is a good idea for anyone - I eventually did a fresh install after numerous problems.  I now have all non-system bits on a separate partition so when the next upgrade comes along I can re-install more easily.

Alright I reinstalled Ubuntu and installed a fresh copy of VMWare Server 2.0 Beta.... everything installed and configured just fine... now how do I go about starting this sucker up? My last version of VM was I believe the Workstation which had a nice console for everything. 

How do I start up the console for the Server??
```

fahim@Central:~$ vmware
Try 'man vmware' for more information.
fahim@Central:~$ 

```

ahhh

---

### Post by veloce on 2007-11-15
> **akba0012 said:**
> Alright I reinstalled Ubuntu and installed a fresh copy of VMWare Server 2.0 Beta.... everything installed and configured just fine... now how do I go about starting this sucker up? My last version of VM was I believe the Workstation which had a nice console for everything. 

How do I start up the console for the Server??
```

fahim@Central:~$ vmware
Try 'man vmware' for more information.
fahim@Central:~$ 

```

ahhh

As I understand it, v2 does away with the old console and uses a browser interface.  So you would connect by browsing to [http://localhost:XXX](http://localhost:XXX) where XXX is the port number that vmware uses - not sure what this is. (It might be https too, not sure about that.)

Would you mind starting a new thread along the lines of "Vmware Server 2.0 beta experiences" to let us know how you get on with it? EDIT: just noticed there's already a thread about this - perhaps you could just add to that.

---

