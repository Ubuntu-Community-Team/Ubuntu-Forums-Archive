---
title: "Ibex upgrade from Heron boots to command line"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Cobbs on 2008-10-30
I spent all day updating my system from Hardy to Heron, I get to the end of the installation and I am prompted to reboot to finish the update.  Upon booting, my pc goes directly to a command line login... I can ls my files and see everything through the command line, but I don't seem to have a gui at all.

Any ideas on how to get this fixed?  I'm really at a loss as to what do at this point.  If you need any outputs or what not, let me know,

Cheers,

Cobbs

---

### Post by celticbhoy on 2008-10-30
when you login try 

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by celticbhoy on 2008-10-30
Forgot to say then reboot

---

### Post by Cobbs on 2008-10-30
Hmm... no such luck Celtic,  I'm still getting the same readout and then command prompt login.

If this helps, this is what I see when I boot up:

Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/5da0dd9f-21bd-4488-897c-712f2a7f22c) = dev(8,37)
kinit: trying to resume from /dev/disk/by-uuid/5da0dd9f-21bd-4488-897c-712f2a7f22c
kinit: No resume image, doing normal boot...

Ubuntu 8.10 HMSDevastator

HMSDevastator login:

---

### Post by caro on 2008-10-30
After I upgraded to the release candidate, I had a similar problem, but I had also made a change to xorg.conf so either one could have been the problem.

This worked for me.  Reboot, and enter grub.  Select the option at the bottom ("repair X server" or something like that) and let it run.  Reboot again if necessary and see if you boot to the desktop.  If not, you will need someone smarter than me to help.  :)

Good luck.

---

### Post by Paideuma on 2008-10-30
Exact same thing happened to me.

I installed via the Update Manager, letting my computer run all day.  Came home and told it that removing old packages was fine with me... (I didn't volunteer this, of course.  It asked.  hehe)  It chugged away a bit longer then prompted for restart.  I gave it my blessing and ended up with: 

```
<userName>@<computerName>:~$
```

I'll try the grub business if someone would be so kind as to point me to a thread explaining how to get there (to "grub") from here (command prompt).

---

### Post by caro on 2008-10-30
Reboot your computer.  The first thing you will see are three lines and one will tell you to hit "ESC" to enter grub menu.  You have about three seconds to do this.  If you see the Ubuntu splash screen, you missed it.

---

### Post by Cobbs on 2008-10-30
Ok, well i am rebooting my computer to get into the grub menu. &#12288;You should see a option that says something like "press escape to enter the grub menu"

However, I think the problem might be that once I get into this menu I see 4 options:

Ubuntu 8.10 kernel 2.6.27-7-generic 

Ubuntu 8.10 kernel 2.6.27-7-generic (recovery mode)

Ubuntu 8.10 kernel 2.6.24-21-generic 

Ubuntu 8.10 kernel 2.6.24-21-generic (recovery mode)

Could it be that there is a conflict between these two kernels that would result in the console login?

I put the kernel 2.6.27-7 into recovery mode and let the xfix run and then rebooted..

Still got the console login, so I tried "startx". The output was:

Fatal server error:
No screens found
giving up
xinit: connection refused (errno 111): unable to connect to x server
xinit: no such process (errno 3): server error

---

### Post by Cobbs on 2008-10-30
Hmmm, ok from reading other posts I think I may have the SERVER edition installed... I'm at a loss how that happened, because I updated through packet manager.

I don't know how to check if that is the case though....

@Paideuma:  Check out this thread [http://ubuntuforums.org/showthread.php?p=6069471#post6069471]("http://ubuntuforums.org/showthread.php?p=6069471#post6069471")

They seem to be talking about the problem we encountered.

---

### Post by Paideuma on 2008-10-30
Thanks celticbhoy!

Using your advice in getting into grub plus a little experimentation on my own, I was able to get the problem fixed.  Here's what I did:

1) Pressed Escape to enter Grub.
2) Loaded the recovery mode version of the most recent highest kernel on the list.
3) Ran the "fix packages" option.  This caused it to download and install (with my guidance) 6 packages--apparently saving me a total of about 4K in HD space.  It prompted me for normal things like deleting old packages, etc.  I said yes.
4) Run the repair X server thingamajig.
5) Reboot.

Voila!  Yay to Ubuntu forums!  Long live celticbhoy!

---

### Post by Imashinu on 2008-10-30
> **Paideuma said:**
> Thanks celticbhoy!

Using your advice in getting into grub plus a little experimentation on my own, I was able to get the problem fixed.  Here's what I did:

1) Pressed Escape to enter Grub.
2) Loaded the recovery mode version of the most recent highest kernel on the list.
3) Ran the "fix packages" option.  This caused it to download and install (with my guidance) 6 packages--apparently saving me a total of about 4K in HD space.  It prompted me for normal things like deleting old packages, etc.  I said yes.
4) Run the repair X server thingamajig.
5) Reboot.

Voila!  Yay to Ubuntu forums!  Long live celticbhoy!

How did you run the "Fix Packages" option? When I try and run my recovery mode It also boots in the terminal. This has to be the most annoying problem I have ever encountered.

---

### Post by Jerdsy on 2008-10-30
> **caro said:**
> After I upgraded to the release candidate, I had a similar problem, but I had also made a change to xorg.conf so either one could have been the problem.

This worked for me.  Reboot, and enter grub.  Select the option at the bottom ("repair X server" or something like that) and let it run.  Reboot again if necessary and see if you boot to the desktop.  If not, you will need someone smarter than me to help.  :)

Good luck.

I just had the same thing happen to me after upgrading from Hardy.

I tried your recommendation and it worked great, thanks!

To sum up:

1. On boot, hit escape to enter the grub menu
2. Select Recovery Mode (choose the newest, highest version in the list)
3.  Wait for a selection screen, select Repair (or is it rebuild) X Server 

Works fine now, Thanks!

---

### Post by Cobbs on 2008-10-30
Tried to do the same thing you did mate, but my 6 packages failed to install...  got errors trying to connect to the security.ubuntu.com stuff  

Any ideas?

---

### Post by Paideuma on 2008-10-30
> **Imashinu said:**
> How did you run the "Fix Packages" option? When I try and run my recovery mode It also boots in the terminal. This has to be the most annoying problem I have ever encountered.

Hmmmm.  Here's a step by step.

First, I hit "escape" during startup to load GRUB.

I then saw the following:
> Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-14-generic
Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-16-generic
Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
Ubuntu 8.10, memtest86+

I chose the second option: Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode).

After a bunch of loading text scrolled by (including the "unable to find an image" message), a red-grey-black-blue menu popped up.

[QUOTE]Recovery Menu

resume     Resume normal boot
clean      Try to make free space
dpkg       Repair broken packages
fsck       File system check
root       Drop to root shell prompt
xfix       Try to fix X server

    <Ok>         <Cancel>[\QUOTE]

I first chose dpkg and ran through that, then I chose xfix and ran through that.  Then I restarted...

---

### Post by Paideuma on 2008-10-30
> **Cobbs said:**
> Tried to do the same thing you did mate, but my 6 packages failed to install...  got errors trying to connect to the security.ubuntu.com stuff  

Any ideas?

Mine gave me some "not able to connect/find" errors w/r/t the servers, but I guess it tried another domain and found it that way.  My best guess is that the domains are perhaps flooded and you should try again?

Sorry, I'm totally green w/ Ubuntu.  I like it though!

---

### Post by Imashinu on 2008-10-30
> **Paideuma said:**
> Hmmmm.  Here's a step by step.

First, I hit "escape" during startup to load GRUB.

I then saw the following:
```
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-14-generic
Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-16-generic
Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
Ubuntu 8.10, memtest86+
```

I chose the second option: Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode).

After a bunch of loading text scrolled by (including the "unable to find an image" message), a red-grey-black-blue menu popped up.

[code]Recovery Menu

resume     Resume normal boot
clean      Try to make free space
dpkg       Repair broken packages
fsck       File system check
root       Drop to root shell prompt
xfix       Try to fix X server

    <Ok>         <Cancel>[\code]

I first chose dpkg and ran through that, then I chose xfix and ran through that.  Then I restarted...

See my problem is that the red-grey-black-blue menu does not show up, just  root@(user):~#.

So I have no idea how am I going to fix this.

---

### Post by Cobbs on 2008-10-30
Maybe that is the case, as far as the servers being bogged down.  I have worked through the grub and run the dpkg, however, my outputs look something like this

```
 Err http://security.ubuntu.com intrepid-security/main linux-headers-2.6.27-7-generic 2.6.27.15
    Could not reslove "security.ubuntu.com"

Err http://security.ubunu.com intrepid-security/main linux-libc-dev 2.6.27-7.15
    Could not resolve "security.ubuntu.com" 
```

This output is followed by the failure of the 6 files to download :(

It seems as though I can't connect to the update server...

---

### Post by tmray on 2008-10-30
mine just goes to the command prompt and if I try yo run kdesu it says it can't find xorg and it says the same for dpk-reconfigure

---

### Post by Cobbs on 2008-10-31
Okay, after a few more attempts, the problem is definitely not being able to access those updates contained in the security.ubuntu.com.

When it tries to read from them, it fails the process instantaneously because it cannot resolve "us.archive.ubuntu.com"

Would I be correct to assume that this does not result from the server being busy (I would think that it would at least wait a bit before declaring failure).

So is it possible that the system does not have permission to access this repository? How could I enable it if this is the case?

---

### Post by OlorinIWas on 2008-10-31
^Man, I don't think so...I can't get those same packages either, and they seem pretty major. I may be wrong, but this seems a bit absurd.

---

### Post by bj0 on 2008-10-31
That's strange, I can ping security.ubuntu.com, is your network or network device down?

If so you can try to bring it up manually with:
sudo ifconfig eth0 up
sudo dhclient eth0

---

### Post by OlorinIWas on 2008-10-31
No screens, no xorg, no connection...what am I supposed to do?

...go to bed...it's frakkin 530 am

---

### Post by glis on 2008-10-31
> **Imashinu said:**
> See my problem is that the red-grey-black-blue menu does not show up, just  root@(user):~#.

So I have no idea how am I going to fix this.

Ia have the same problem. No way to fix that :(

---

### Post by bigfootnmd on 2008-10-31
Hi gang,

I have the same problem.  First of all let me be clear that when grub comes up all the choices are Ubuntu 8.04 yada yada yada.
There is no 8.1.  No errors were seen during the upgrade.

Clean up was automatically done before the upgrade finished.

Also I have tired nine ways to Sunday to bring up or get the GRUB menu
I have head the escape key down from the moment my PC powers on and from the moment the BIOS screen splashes. NOTHING happens I still see
the Ubuntu 8.04 Yada yada choices.

Also,  When I do get the terminal login screen I also
see

Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/5da0dd9f-21bd-4488-897c-712f2a7f22c) = dev(8,37)
kinit: trying to resume from /dev/disk/by-uuid/5da0dd9f-21bd-4488-897c-712f2a7f22c
kinit: No resume image, doing normal boot...

Ubuntu 8.10 HMSDevastator

charles  login

I have done the dpkg reconfigure -phigh -force xserver-org and it did not help.  So, I am stuck on a wall.

I like the GNOME DESKTOP.  I do not want xubuntu.

Any ideas will be appreciated. How do I get to that grub menu to fix packages if hitting escape does nothing?

HELP:confused:


AN idea occurred to me.  If I download the ISO install image and put it on a USB thumb drive (yes, I have the uboot whatever) I can boot off the thumb drive and install 8.1
However, I want to preserve my home folder.

Details will follow and please somebody reply

PROBLEM SOLVED!

By checking these forums I learned how to mount my usb drive from the command line of my crippled system.  I then was able to backup my important files to the thumb drive.  I next proceeded to do a FRESH INSTALL.  I WILL NEVER UPGRADE again.

---

### Post by OlorinIWas on 2008-10-31
> **bj0 said:**
> That's strange, I can ping security.ubuntu.com, is your network or network device down?

If so you can try to bring it up manually with:
sudo ifconfig eth0 up
sudo dhclient eth0

Interesting, while that didn't work last night, the supplied commands did allow me to install my 6 absent packages today. BUT that has not resolved the issue with init...kdm is running...network accesses is on but doesn't work...

Check for package breakage, tried to fix xserver...I seem to remember it telling be there were no screens..

Could installing the OS with two monitors hooked up cause this problem?

---

