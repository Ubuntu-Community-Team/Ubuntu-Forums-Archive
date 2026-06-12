---
title: "Instalation Issue"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by SkyLord77 on 2008-11-11
Ok... So some people may have seen my last post about the same topic and I thought I had it licked after I did a lot of research, but alas it remains.

I had issues installing Ubuntu from the Live CD that I created. Major issues with one of my two monitors going blank (The DVI) and the other looking like something out of the Matrix (The VGA).

I was able to get around that by booting into "Safe Video Mode?". So anywho I got a bit into it. Set it up for dual boot by creating a partition for Swap, and setting up the rest of my drive. I had it chuggin' along until it tells me that either the CD, or my HD is bad.

Ok... So I burn another CD in slower mode. Same darn thing.

I get out a Ubuntu 7.10 CD that I had mailed to me many moons ago and run that... Same issue.

So now I use wubi and do a install that way. It goes through peachy keen. I figure I can transfer it over as a full install to the partition I already created.

Here's my main problem. When I select Ubuntu in the prompt for my dual boot it takes me back to my ORIGINAL problem of having a black screen (Again the DVI) and the Matrix looking screen ( My VGA) monitor.

I've tried plugging my VGA monitor into my onboard and it's just black.

I did a bit more research and found that if I select Ubuntu from boot up, let it chug for a few minutes and once the mess returns I can hit CTRL + ALT + F2 and get into a screen I can actually read.

I logged in.... I entered "sudo -s" as I read that this command would magically fix everything. It doesn't. To be honest I don't know what the heck sudo -s stands for.

So anyway.... How do I get Ubuntu to boot into the "Safe Graphics" mode that I could from the live CD? I assume once I'm in that way I can update my drivers and be all jolly and happy?

Thank you in advance.

---

### Post by crazyness003 on 2008-11-11
OKay, "sudo -s" means that you are permanently logging into the root account (not a very good idea). Suso stands for Sper User DO (like telling the computer "I'm the super user rand I command you to do this:...bla bla bla").

Your second question, how to get to safe graphics mode: when you reach the grub menu, go the the entry that might look like this

[FONT=Fixedsys]Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)[/FONT]

and it should boot up, load the kernel and give you a a selection of 4 choices (in a not so pretty looking blue box). I cant exactly remember what they are, but one of them lets you use xterm (i think). Thats the old school 'DOS lookin'' thing when you can type commands and stuff. 

Experiment with these. If all goes wrong, i suggest using a newer version of Ubuntu (assuming you're still trying to run 7.10 or 8.04). 
FYI: 8.10 solved my display issues.

---

### Post by SkyLord77 on 2008-11-11
Thank you for the reply! :)

I did install Ubuntu 8.10 off of Wubi so I'm at the latest version. lol 

I will try what you mentioned in about 5 minutes and then post what happened here.

After beating my head against a wall for a full day I think I might finally see the light at the end of the tunnel.

Well... Maybe the light is the cops flashing lights in my rear view, but a light is a light and I hope it's promising. :)

---

### Post by crazyness003 on 2008-11-11
Thats the way to look at life: "If everything doesn't go as planned, go out in style: lights and all!"

---

### Post by SkyLord77 on 2008-11-11
Ok. This is what I did.

I booted Ubuntu. 

Hit ESC to enter that cool lookin' blue screen.

My options were...
1.) Resume
2.) Clean     Try to make free space
3.) dpkg      Repair broken packages
4.) fsck      File System Check
5.) xfix      Try to fix X Server

I tried all of them except Clean.

Once I got to the prompt and had a choice as what to type I tried

"apt-get" to see what would happen. It gave me a bunch of -commands to append.

I tried the one that is supposed to download updates, and no fix.

I'm really stumped. I can't believe there is no option to boot into a safe video mode like is on the Live CD.

This is so odd. I mean I know what the problem is. My drivers arn't groovin'. I just want the monitor('s) to work correctly. I can deal with just one for now and then tweak the settings so I can get the other one up, but this is blowing my mind.

Anyway thank you for all your help.

I must go lay down for the evening. I've been battling Lyme Disease and Babesia ( a cousin of Malaria ) and I'm really sick.

I can't tell you how much I appreciate you responding and trying to help.

Have a wonderful evening

---

### Post by crazyness003 on 2008-11-12
hmm. It seems like xorg just cannot find the right settings for graphics. I think we may need to probe this more.[COLOR=Red]** PLEASE READ THE ENTIRE POST BEFORE DOING ANYTHING**[/COLOR]
Anyone else wanna help, is more than welcome to.

Okay, since none of that worked, lets get down to business. 
What kind of grfx card are you using? 
[COLOR=Red][B]1
[/B][COLOR=Black]Id try this first:
[/COLOR][/COLOR]```
sudo apt-get install linux-restricted-modules-generic
```
This installs the necessary restricted modules for your particular kernel. It might ask you to install some additional stuff. Allow it. [COLOR=Red]**YES**[/COLOR]
Aterwards, it may ask you to install the particular video drivers, select the most recent ones that apply to you (ati or nvidia) with tthe latest version number.
[COLOR=Red]**2**[/COLOR]
If that still dont work, Then try these:
If nvidia try
```
sudo apt-get install nvidia-glx-177
```
If ATI, try
```
sudo apt-get install xorg-driver-fglrx
```

Im not to sure about the ATI one, i dont have an ATI card to test on, but the nvidia one is the latest driver that supports almost all nvidia cards (i say almost since there is a 0.001% chance that it wont). The 177 driver is the latest for nvidia (i hope you have nvidia, ATI and Linux arent the best of friends).

When you do try the above terminal code, it may prompt you to install a bunch of other packages, just accept them, its the dependencies that are associated with that driver (like .dll's in windows).

Here's a readout of the xorg-driver-fglrx package (in synaptic)
> Video driver for the ATI graphics accelerators
Video driver for the ATI Radeon and FireGL graphics accelerators.

This version of the ATI driver officially supports:
 * RADEON X1300, X1600, X1800, X1900
 * RADEON 8500, 9000, 9100, 9200, 9500, 9550, 9600, 9700, 9800
 * RADEON X800, X700, X600, X550, X300 series (AGP and PCI Express)
 * MOBILITY RADEON 9000, 9200, 9600, 9800, X700
 * MOBILITY RADEON 9000/9100 IGP Series
 * FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2
 * MOBILITY FireGL 9100, T2
 * RADEON XPRESS 200


This package provides 2D display drivers
and hardware accelerated OpenGL.

**[COLOR=Red]SUMMARY[/COLOR]**
The first command should get the ball rolling, but if it doesnt, keep track of what you do. If soneone who is more knowlagable comes in, tell them EXACTLY what you've done so far. It will help wonders.

Sorry to hear about the lyme disease and Babesia. That sounds kinda bad. I hope you get better.
Remember, dont force things, they usually end up getting damaged in the process. 

Take it easy

---

### Post by SkyLord77 on 2008-11-12
Thank you again.

This is what I have done thus far.

I booted Ubuntu, pressed ESC and then selected the generic recovery. I entered that pretty blue screen and selected to drop right into the kernel.

After typing in my log ID and pass I did the following.

sudo apt-get install linux-restricted-modules-generic

It told me that it is already at the newest version. 0 upgrades and 0 installs.

I then typed the following as I do have Nvidia

sudo apt-get install nvidia-glx-177

It told me

> E: Couldn't find package nvidia-glx-177

I said to myself "Self... Maybe I should boot it normally until I see the darkness and then hit CTRL ALT F1 and log in after it boots". My thought was that it might not be able to see my network connection.

So I did that. After I logged in again at the kernel I typed the same thing again.

Same exact results.

I find it so odd that Ubuntu will allow you to boot into safe Graphics mode from their Live disk, but not once it's installed.

I gotta be honest and admit that I'm lost. 

BTW I didn't mention that I do have NVIDIA.

I have NVIDIA MCP61 A3 on North and south bridge on my MB.

I have a Video Card that is NVIDIA GeForce 7300 SE/7200 GS

I'm sorry I didn't post that earlier.

---

### Post by crazyness003 on 2008-11-12
okay. i know why you cant install the nvidia-glx-177 package. you need to enable the restricted repos. But, unfortunately, im not that advanced of a user, so im gonna attempt to enable all of the repos (that ship with ubuntu) using a couple of terminal commands. I got the info from here: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
Please bear with me, this_* might*_ work. i cannot guarantee anything. If your system gets tanked...them im sorry. Reinstalling is good for the soul anyway (if you have the time)

Backup your current source list.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Now issue this command
```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
```
In a nutshell its removing the hash (#) sign from the listed, disabled repos. I dont know the exact details, but according to what i read, this is the big cheese.

This updates your source list into apt.
```
sudo apt-get update
```

There. done. Now try to issue the command
```
sudo apt-get install nvidia-glx-177
```
and see it that works.

Remember, if this broke anything you backed up your original source list. To recover it, just type
```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
``` and let it override.

---

### Post by Jackie999 on 2008-11-12
I have the older nvidia (GeForce FX 5500) that I've been trying to get working in intrepid. I was given this link that seems to have quite a bit of information. Pretty much the same as you're suggesting there crazyness003 - it's another place for SkyLord77 to look if your post doesn't help:

[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

Here is my thead where I was told about it:

[http://ubuntuforums.org/showthread.php?t=965818](http://ubuntuforums.org/showthread.php?t=965818) (see rich257's post)

Hope this helps.

---

### Post by uidb4056 on 2008-11-12
I suggest you to try a normal boot but when the grub menu appears hit 'e' key on the first line and then 'e' again in the line that begins with 'kernel', move to the end of line and delete 'splash' and 'quiet' options (may be you could add 'noacpi' if the first attempt not work) then press 'enter' and 'b' to boot, you will get a verbose screen where you can see what is happening and I think you can get at the end the graphic login screen, if it works you can add permanently this chages editing menu.lst file. I had a similar problem installing 8.10 and that does the trick for me.

---

### Post by Dazed_75 on 2008-11-12
Is there any particular reason not to just reinstall from the Live CD and use its Safe Video Mode?  You would probably want to use the manual partition option and just select the same partitions that were created from your first install, but it does not sound like you have anything within ubuntu to save yet.

---

### Post by SkyLord77 on 2008-11-12
Oops

---

### Post by SkyLord77 on 2008-11-12
Thank you everyone. :)

This is what I did and the results.

I backed up my source list.

I issued this command.

     sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list

No error so I assumed that everything was fine. 

So next I did this.

     sudo apt-get update

And I received this.

Failed to fetch..... About 30 times, then

Could not resolve "x website"

I figured this was a not so good thing; however, I tried the following command anyhow.

     sudo apt-get install nvidia-glx-177

And I got this.

"You may want to run apt-get to update", and

"E: Couldn't find package nvidia-glx-177"

I can only assume what is going on here. It seems to me ( Remember I'm no computer genius ) that for some reason Ubuntu isn't searching the web at all. I can't understand this because when I booted into the safe graphics mode from the Live disk I was able to surf the net just fine.

Crazyness,

I will go on the site that you recommended as soon as I finish typing all of this out. I can't thank you enough for all of your effort in helping me.

Jackie,

I'll be looking into the links that you provided as well. Thank you. :)

uidb4056,

To be frank I don't quite understand what you typed. I'm still REALLY new so I'm kind of in the dark. I do appreciate the time that you took to try to help me out. :) :guitar:

Dazed,

I can't start over from the CD because every attempt I make at installing I get half way through install and then I'm prompted that there is an error with either my CD, or my HD. I know it's not either so that's why I did a wubi install with hopes that I can transfer everything over to my partitioned drive as soon as everything is sorted out.

Thank you all and have a wonderful evening.

---

### Post by crazyness003 on 2008-11-12
Just to clarify: You have no access to a roeking GUI of ubuntu, is that correct?
If you could use a liveCD and edit some files on the installed partition, then this may be easier (since you said that you also had net access).

Since you have a backup of source.list, open the file by doing this:
This will open the filebrowser [COLOR=Red]WITH ROOT PRIVELEGES. EXTREMELY DANGEROUS[/COLOR]. Be careful not to do anything wrong, other than what i say.
```
sudo nautilus
```

Then you have to mount the filesystem (just go to Computer, and open 'Filesystem'. make sure this is the actual installed Ubuntu filesystem. I dont know how to tell the difference exacly, but then you get there, tell us what you cant do)

Then navigate to /etc/apt. there you will see a file named 'sources.list', right-click and open with text editor.
[MAKE SURE YOU HAVE THE BACKUP THERE SOMEWHERE AS WELL, dont touch it, just make sure you have it]

DELETE everything inside that file. and replace it with this:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #OpenOffice.org Launchpad Packages
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
```
The above is my source list.

Now save the file. and go back reboot into the Ubuntu partition. and then try to issue
```
sudo apt-get install nvidia-glx-177
```
I really hope that works because im running out of things to tell you.

If you cannot use a live CD to do the above. all hope is not lost...it just gets a little more intimidating, but not impossible. You'll get to use 'nano', but first try to do it this way. i know its a very long way around, but its more comfortable.

Im gonna hit the sack, so when i have time, i'll check up on you asap. Good luck

---

