---
title: "How to create the perfect install"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by 33Nicolas on 2015-10-30
I'm opening this thread here because I convoluted my Ubuntu Studio to the point where it makes less and less sense to fix. I'm a newbie and just downloaded the MinimalCD.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The goal here is to install a lean system on an old machine, circa 2008 I believe, and to install only what I need.

Looking forward to the learning curve and leave the Infernal Trio behind.

---

### Post by Bashing-om on 2015-10-30
33Nicolas; Hey !

I am looking to find the 14.04.1 minimal release .iso ..
I "think" you will be better served with the .1 release as 64 bit . However, I have been known to make errors in judgement. You are encouraged to correct my thinking.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-30
33Nicolas; eeekkk ;

My google-foo is failing me . I am unable to find a 14.04.[color=red]1[/color] minimal .iso !
We may have to work with 14.04.3 (??) . That might put a small kink in the plan .

[INDENT][INDENT]best laid plans of mice and men
[/INDENT][/INDENT]

---

### Post by sudodus on 2015-10-30
[Look here](http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730) for mini.iso versions (they do not completely match the versions of the desktop iso files).

---

### Post by 33Nicolas on 2015-10-30
Sorry for the delay, been busy.

Ah, thanks all, I was having difficulties finding the right one. Thanks Sudodus for the links and Bashing-Om for keeping up with me. Maybe this thread can help others also.

I'm trying to figure out what my hardware is. I typed sudo lshw and got the following.

```
 Dell Precision WorkStation 390
64-bit system
CPU Intel 2 CPU 6300 @ 1.86GHz (no AMD Bashing-Om, what did I do with this install!)
2GB RAM
Nvidea NV44 [Quadro NVS 285]
onboard audio... Gasp.
```

OK, now I know which one to download. I can't find 14.04.x. Can you help? Thanks.

---

### Post by Bashing-om on 2015-10-30
33Nicolas33; Hey !

Thanks to sudodus for the link .
[http://cdimages.ubuntu.com/netboot/trusty/](http://cdimages.ubuntu.com/netboot/trusty/)  -> "Select an architecture to install 14.04 with trusty's 3.13 kernel (supported until April 2019)"
The 1st choice : amd64 - For 64-bit Intel/AMD (x86_64)

As this version will have the X we want to use.
Remember to check that the download is valid; and the burn is good.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Then boot it and
[INDENT][INDENT]let our adventure begin
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-30
Thanks Bashing-Om and Sudodus, the patience is much appreciated.

Bashing-Om, I downloaded the first link and will check it to burn a CD. I'll boot into it tomorrow. Wow, 39MB! Exciting to be on this journey.

---

### Post by sudodus on 2015-10-31
Good luck!

Come back if you have questions, and also to share the solution :-)

---

### Post by 33Nicolas on 2015-10-31
Thanks all,

Sudodus, beware what you ask for :) I will be back and asking tons of silly questions as I browse through the links you and Bashing-Om offered.

Step 1: Downloaded the MinimalCD

Step2 : Backed up another time important files on the seperate drives and partitions.

Step 3: I will boot into the MinimalCD in a few hours.

---

### Post by Bashing-om on 2015-10-31
33Nicolas; Uh Huh ...

Make a plan, Prior Prudent Planning prevents P*** Poor Performance.
Speaking of which .. while I have no objection to the standard default for a new user; there are benefits to setting up partitions yourself if you know how your use case will be . I like to have a separate /home and /var partitions - for my use case ! - ,
as this is to be a long term install .. might give separate partition setup a few thoughts; in light of how you will eventually use your system. Separation of system files from "use" files can be a good thing .. goes a long way in preventing work files and log files eating up all the disk space in a partition unexpectedly . Among other things such a set up promotes a comprehension of the file system, and the management there of.
( - Now if ya get real radical there is raid and (L)ogical (V)olume (M)anagement ) 

Keep to the plan
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-31
Thanks Bashing-Om,

I've always kept OS and personal data seperated on different drives when it was possible, partitionewd seperatoly when I had no choice. MS taught me that early on. 

In this U-Studio case, one drive has the installation, programs and everything relevant. The other HD has my documents, multimedia files, as in pictures, videos, etc., as in my own created, personal multimedia files. I write a lot and film videos. Sometimes I partition my personal secondary drive. I think that's what you were talking about? So /home is on the second SCSI in my case. I've not only backed it up with BackInTime, and also dumped a copy on a seperate USB drive, now disconnected. 

As to /var, I'm still a little confused about what it does. I understand it to be a folder where the system constantly writes to under normal operations, but that's the limit of my understanding at this stage. I think it has to do with multi-users and shared data? Do you put yours on another drive or partition? What is the benefit if you don't mind explaining.

I think we're on the same wave length. Thanks for explaining these things. This thread could become a great how to for dummies like me :)

---

### Post by Bashing-om on 2015-10-31
33Nicolas; Hey, yeah !

Preaching to the choir I be ..
I bet you can teach me a thing or 3 ...

As to /var ... I do some weird things sometimes and then again I break it ( I fix it ) .. in the event of my logs going hog wild I do not want a out-of-disk space condition crashing the box. 

Then again I think I have a better handle on maintaining the system using separate/dedicated partitions . a quick ' df -h ' tells me all I generally need to know on a regular basis .

This ole dog can learn new tricks
[INDENT][INDENT][INDENT]I expect to learn a thing or 2 before this is a done deal .
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-11-01
Minimal installs are straightforward, but take some planning if you are not intending to install a machine profile using tasksel during the mini install.

I avoid that route and don't mark anything there, just continue. Once the install is done, you will restart and log in to a CLI, no log in manager or anything else, and you will have a machine running just the Ubuntu kernel. You install everything else and this is where the plan you've made comes into effect. 

* A mini install must be done with a reliable ethernet connection (cable), not wireless. 

You need to choose a desktop environment and list the apps you want to use and then simply 'sudo apt-get install' them. For instance, on first boot after log in, this would give a very simple set up:

```
sudo apt-get xfce4 lightdm synaptic firefox lxterminal pcmanfm xfwm4
```
That gets you, in order, a desktop environment, a desktop manager, a package manager, a browser, a terminal, a file manager and a window manager. Reboot and you will login and get to a basic desktop. Take it from there. Install other things via the terminal or Synaptic Package Manager and you're on your way. Ask here when/if you hit a brickwall with your research.

Good luck. It is the only way I go, lightweight, fast, flexible, a satisfying pursuit and you get to create your own hybrid monster! 

PS: If you are intending a mini install only to then install *buntu-desktop, don't bother with the mini. Installing ubuntu-desktop, for instance, is more or less equivalent to installing Ubuntu, so just install Ubuntu. :)

PPS: As for the UStudio stuff, which bits do you want? You don't need it all, probably. For instance, if you are only interested in the audio stuff, then 'ubuntustudio-audio' will drag just that stuff in (you will probably want 'ubuntustudio-audio-plugins' also). 

Or you can install apps from UStudio individually (and they may be already on your original plan). If you have a look in a working install in Software Centre or Synaptics, and search for 'ubuntustudio' you will see all the available bits you can drag into your monster. :)

---

### Post by 33Nicolas on 2015-11-01
Wow, you folks are amazing. I'm really excited, or maybe a better word would be feeling liberated.

Thanks Bashing-Om for clarifyiing the way you use and place the /var folder. I'm doing some more reading on it.

Thanks Bucky Ball for the planning info and how to install the basics without overloading this old computer. That gets me going in the right direction.

My aim is to build a Linux computer that plays well with MIDI and audio in general. I want to plug in my synth, drum set and that annoying as hell JamLab USB guitar connector. That last one doesn't have a Linux driver I believe, but some people were able to make it work. I use Clementine for my heavy audio collection. I'm open to anyting else, VLC? Next step will be to get a good audio card.After that, there is that iMac I've been itching to switch over. 

If any audiophines and musicians have technical recommendations, I welcome them.

Again, deep thanks! And I'll report the state of this install hopefully today, if not tomorrow.

---

### Post by Bashing-om on 2015-11-01
33Nicolas; Doing well ..

We have failed, however, to remind you that the very 1st thing to do once installed is to update/upgrade
```

sudo apt update
sudo apt full-upgrade

``` before installing anything.

[INDENT][INDENT]it's them little things
[INDENT][INDENT][INDENT]get ya every time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-11-01
Continuing on from Bashing-om:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... will do it. This will not upgrade the release you've installed to a newer one. 

If you're going the way I mentioned, starting minimal with no machine profile, do the update commands on the first boot after install when you log into the CLI text screen BEFORE installing all the other things. :)

Yep, Doh! Forgot to mention it ... :| No big deal if you're already rolling, though. Just run those commands when you read our posts.

---

### Post by 33Nicolas on 2015-11-01
Ah, yes, perfect.

So to recap from the previous steps, once installed and rebooted:

```
sudo apt update
sudo apt full-upgrade
```

then

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then I will proceed to:

```
sudo apt-get xfce4 lightdm synaptic firefox lxterminal pcmanfm xfwm4
```

Since I plan on using these. I switched over to PaleMoon, a lighter version of Firefox, which I might substitute in the prompt. It's been working pretty well.

The  update again, if I understand the series well.

---

### Post by sudodus on 2015-11-01
May I suggest that you ***backup*** your system, so that you don't have to do all the work twice.

It is a good idea to run a backup program or script regularly and keep the backup copy in a safe place. The more work you put into your system and files, the more important it is with regular backups.

---

### Post by 33Nicolas on 2015-11-01
Thanks Sudodus,

I backed up with BackInTime and made an extra copy on an external drive.

Always back up. Most people learn the hardway. So did I a long time ago.

Hi Bashing-Om and Sudodus, 2 questions:

Is this command worthwhile doing on my system with 2GB or RAM?

```
File /etc/default/linux-restricted-modules-common
```

Not sure how to remove 

```
 language-pack-en and language-pack-en-base 
``` 

```
 rm language-pack-en language-pack-en-base 
``` ?

Thanks

---

### Post by sudodus on 2015-11-02
the command ***file*** determines the file type. Maybe you want to do something else?

Do you want to install the **restricted extras**? If you use xfce as recommended by Bucky Ball, maybe you'd run

```
sudo apt-get install xubuntu-restricted-extras
```

which contains support for MP3 playback and decoding, Microsoft fonts, Flash plugin, DVD playback, and LAME (to create compressed audio files).

---

### Post by Bashing-om on 2015-11-02
33Nicolas; Ouch ...

" linux-restricted-modules-common' is non-standard, and not in the 14.04 repo ... What have you been doing ? - Like you have the base core system all installed now ? This from a PPA ???

Removing languages:
see:
[http://askubuntu.com/questions/515330/how-do-i-go-about-removing-all-the-language-packs-i-dont-need](http://askubuntu.com/questions/515330/how-do-i-go-about-removing-all-the-language-packs-i-dont-need)

in the context of things
[INDENT][INDENT][INDENT]where are we ?
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-02
Ah, thanks, yes I do.

I want to remove the extra language packs. And yes, I do want to install these audio extras. 

Spot on Sudodus.

Bashing-Om, 

No, I haven't gone that far yet. This was a pre-emptive question, as in should I do it?

Tx

---

### Post by Bashing-om on 2015-11-02
33Nicolas;

unetbootn ? ,, never used that app .. so I assume the choice is from there ? I do not know as what we want for the initial install is 14.04.1 .
14.04.1 has the 13 series kernels that will remain when we upgrade 14.04.1 to what is now current ( 14.04.3 )
as in my install:
```

sysop@1404mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
sysop@1404mini:~$

sysop@1404mini:~$ uname -r
3.13.0-66-generic
sysop@1404mini:~$

```
Where my initial install was 14.04.0 .

Installing grub ... YES
Install grub to the same hard drive as you are installing 'buntu onto ... GRUB == Grand Unified Bootloader; got to have a loader to load an operating system.

[INDENT][INDENT]cover all  the bases
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-02
Ah, thanks Bashing-Om.

I tried installing it on the first HD, I believe sda, but it give me a fatal error message. So I'm back at Install the GRUB boot loader on a hard disk. When I press enter, it brings me back to the previous message where it lists the 14.04.3 and 14.04.2 LTS installed OS. Weird, because I formated the HD. I guess I need to install GRUB on the master boot record. I missed that part.

I'm not sure I know what unetbootn is :/

Victory, 14.04.3 LTS is installed and I booted into it.

I'm worried 14.04.2 LTS was still listed at boot up time.

I am proceeding with the updates and later basic installs.

---

### Post by sudodus on 2015-11-03
Congratulations :KS

-o-

> **33Nicolas said:**
> Ah, thanks Bashing-Om.

I tried installing it on the first HD, I believe sda, but it give me a fatal error message. So I'm back at Install the GRUB boot loader on a hard disk. When I press enter, it brings me back to the previous message where it lists the 14.04.3 and 14.04.2 LTS installed OS. Weird, because I formated the HD. I guess I need to install GRUB on the master boot record. I missed that part.

I'm not sure I know what unetbootn is :/

Unetbootin is a tool to create a USB boot drive from an ISO file. See this link

[Installation From USB Stick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

If your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by 33Nicolas on 2015-11-03
Thanks Sudodus,

I installed 

```
 sudo apt-get xfce4 lightdm synaptic palemoon lxterminal pcmanfm xfwm4 
```

and find myself not knowing what to do next. I rebooted, but I'm still at the command prompt. I wonder if I need to start X at the prompt?

Am I missing something? Thanks

---

### Post by Bucky Ball on 2015-11-03
* If that is what you've put into the CLI, you forgot install!

```
 sudo apt-get **install** xfce4 lightdm synaptic palemoon lxterminal pcmanfm xfwm4
```

If you still have an issue, start at the CLI with an ethernet cable and a full update/upgrade:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Then use this in the command prompt, but you should be getting to a log in screen on boot now. We'll get to the bottom of it, but first, let's get to a desktop. Not startx, but:

```
sudo service lightdm start
```

Desktop?

At the CLI, you can also try:
```

sudo dpkg-reconfigre lightdm
sudo reboot -h now
```

* Do those update/upgrade commands ASAP so you know you're machine is up to date before you start installing anything else. :)

Good luck.

---

### Post by 33Nicolas on 2015-11-03
Thanks Bucky Ball, this is what I was missing.

I'm also seeing an older Ubuntu 14.04.2 LTS. I'm wondering if I didn't properly format the first drive I was installing this lightweight system on. I'm considering redoing it from scratch tomorrow and see what happens.

By the way, I documented everything and would be happy to give it to the community for editing if it helps. It's actually much easier than I assumed.

---

### Post by Bucky Ball on 2015-11-03
Did everything install and reboot to a desktop once you added 'install' to that install line?

If so, that's it. :) You can install Gparted (or a Live session from the install media) to have a look around at the partitions and rearrange what you need to. I'd sniff around a bit more before going for a reinstall. Still, if you want to reinstall anyway, just for the heck of it and experience, up to you.

It is easy once you've done it once or twice. The fun starts when you get to a desktop and start adding missing things. It can sometimes take a week or two to get things 'settled'. Once there, though, you have a racehorse with few moving parts. :)

---

### Post by 33Nicolas on 2015-11-03
I'm laughing, cuz I sure can't show you how much I'm blushing!

---

### Post by Bucky Ball on 2015-11-03
:D So you have a desktop? We all start somewhere, incidentally. I have a raft of previous 'blushing' situations from the last seven years of Ubuntu!

---

### Post by 33Nicolas on 2015-11-03
It's good to see that I'm not the only one. In my case, it's getting older, vanity for not wearing glasses and dyslexia!

Well, yes, and more weirdies. I see my desktop and there is a dialog box with my username, but it says "failed to start session" in it in red when I put in my password. I've never seen this dialog box.

Fun stuff, all in all.

I'm crossed eyed now. I'll take this up tomorrow again. Thanks!

---

### Post by Bucky Ball on 2015-11-03
See you then. When you get back, try:

```
sudo dpkg-reconfigure -a
```

We will get there! You're at the desktop so just a matter of working out what's missing now and squashing any issues. :)

---

### Post by Bashing-om on 2015-11-04
Et al :

:)

[INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT]there is a way
[INDENT][INDENT][INDENT][INDENT]that is the 'buntu way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-04
Thanks all, just got back and eager to get that computer going.

Not sure how to get to a terminal, since the desktop is only leaving a few options, close, reboot, and networking.

It's fun being a newbie with the right people around :)

---

### Post by Bashing-om on 2015-11-04
33Nicolas; ???

You installed xfce4 ? then in the task bar is "applications menu" activate the terminal you prefer .
On my xfce4, a right click on the desktop gives me 10 options, among them is also "open terminal here" .


[INDENT][INDENT]sometimes we wonder
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-04
[HTML]sometimes we wonder[/HTML]
Ditto!

I installed xfce4 and there is that weird dialog box that has my user name and asks for the password, which I input, but it says can't start session. Nothing happens when I right click.

The more I think about it, the more I feel I should reinstall from scratch again. There might be gremlins in this computer!

Starting to get the hang of writing in this forum, at last.

---

### Post by Bashing-om on 2015-11-04
33Nicolas; Well ..

Remember what I said about a display/login manager - here lightdm - // not required on a single user system and in my opinion useless overhead. If you do not mind booting to terminal, and from terminal - if a GUI is now wanted ... start the GUI from terminal . No problem, no hassle .

I have none, but I am willing to learn lightdm of ya want it.

[INDENT][INDENT]you can have it your way
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-11-04
To get to a terminal from the login screen hit control+alt+F1. That will get you to a CLI (a big terminal). Plug in an ethernet cable if you need to and update/upgrade, then reboot and see if things change. If not, let us know what is now happening.

I'm just trying to think if we've missed installing something essential in that first install line. If that is the case, a fresh install won't help much, so perhaps we should perservere with this for awhile longer. There are other options, like perhaps changing the dm. 

But, again, up to you, of course. Something else may have gone amiss during install.

---

### Post by sudodus on 2015-11-05
What dialog box is weird?

Do you know what the xfce dialog box should look like? Maybe you can describe it. Did you try left-clicking (not only right-clicking)?

-o-

But if you think you have destroyed something in your system, it might be easier to re-install than to repair.

---

### Post by 33Nicolas on 2015-11-05
Bashing-Om, thanks for that. I didn't due diligence with Lightdm and yes, it's a one user computer.

Let's see if I can get to the terminal. I'm using an Apple USB keyboard and command keys are always a pain in the ****.

Bucky Ball, I will try later this morning. It shouldn't be that difficult. I see Control Alt and F1. I will let you know later on. Thanks!

Thanks Sudodus, I should have explained it better. Weird meant I hadn't seen it bfore and this desktop manager is new to me. It's purple with white evenly spaced dots. There isa nothing left-clicking will do on it. On the right side of the screen, roughly off center, there is a rounded square dialog box with my user name and a space for my password. When I enter my correct password, it says it can't start the session. I will try to take a picture from my cell phone and upload it here later this morning.

Thanks for all your communial help!

Sorry folks, morning turned into an afternoon until the evening snuck up on me. Getting on it this afternoon.

OK, so Control Alt F1 are not working and I suspect it's that idiotic  Apple USB keyboard. The problem is I don't have another handy. I tried  to click on what looks like a Universal Display icon and check the  onscreen keyboard, but nothing is happening. Righ-clicking has no effect.

Why did I throw away that keyboard!

Bucky Ball,

I got a regular keyboard and found my way to the terminal, thanks to Sudodus's help. I typed:

```
sudo dkpg-reconfigure -a
```

It showed me a ton of Mozilla certificate of authenticity, which I agreed to. I also used UTF-8 to encode to use the console (it was the default setting). Then I used the combined characters to support Latin: Slavic Cyrillic: Hebrew: basic Arabic. Not that I can read or write any of these languages. My latin goes back to 1976! I don't see any other choice that would make sense. I used Fixed appearance for the console and 16, and using dash for the default shell. Not that I know what that last one is, nor a lot of other stuff I'm agreeing to... gulp. 

The package interface I left it at dialog for debconf and left the default question it will ask me as high. It then loaded a few things. 

A linux command line was extracted from /etc/defatul/grub/ pr the 'kopt' parameter in GRUB legacy's menu list. I left the linux command line empty.

It told me the grub-pc package was being upgraded. I left it on my first drive, which I believe to be sda. It showed two other options, sda5 and sdb. 

Bashing-Om, I noticed sd6 has Unbuntu 14.04.02.

It said done after a while, but returned:

```
/usr/sbin/dpkg-reconfigured: initramsf-tool is broken or not fully installed
```

I did breifly see something was not updaded previously when I sudo apt-get upgrade, but couldn't make what it was.

After that, I updated, upgraded and dist-upgraded again. Nothing was upgraded, whether with sudo apt-get upgrade or sudo apt-get dist-upgrade.

By the way, what is the correct shutdoiwn and reboot command at the prompt?

I rebooted and it still says failed to start session. Here's a shot I took form my phone.[ATTACH=CONFIG]265443[/ATTACH]

---

### Post by Bashing-om on 2015-11-08
33Nicolas; It is an adventure,

Now ain't it ?

Got more than one install ?
> 
Bashing-Om, I noticed sd6 has Unbuntu 14.04.02.

Look at the hard drive partitioning and UUIDs:
```

sudo fdisk -lu
sudo blkid

```

and:
> 
By the way, what is the correct shutdoiwn and reboot command at the prompt?

```

sudo shutdown -h now ##will bring the system down and power off
sudo shutdown -r now ## the 'r' says "reboot"

```
see : " man shutdown" .

May the hunt for the script
[INDENT][INDENT][INDENT]begin again
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-08
Thanks Bashing-Om,

I will do this tomorrow, and thanks for the shutdown/reboot refresher.

[HTML] It is an adventure, Now ain't it ? [/HTML]

I'm laughing at it all. It almost mimicks my life to a T.

As far as the other install, as soon as I get to it tomorrow monring I will check it out.

Thanks!

Thanks Bashing-Om,

As I'm getting everything from the terminal, is there anyway to save the returns, or pipe it somewhere? If not, I can type everything I see. Not sure I'm using the right words either.

Bashing-Om,

Here's what ```
sudo fdisk -lu
``` returned.

```
/dev/sdb: 160GB

Device Boot  ID   System
/dev/sdb1    83   Linux
/dev/sdb2    83   Linux
/dev/sdb3      5   Extended
/dev/sdb5    82   Linux Swap / Solaris
/dev/sdb6    83   Linux

Partition table entries are not in disk order

Disk /dev/sda 160GB

Device Boot  ID   System
/dev/sda1    83   Linux
/dev/sda2      5   Extended
/dev/sda5    83   Linux
/dev/sda6    82   Linux Swap / Solaris

```

```
sudo blkid

/dev/sdb1 Multimedia ext4
/dev/sdb2 Documents  ext4
/dev/sdb5 swap
/dev/sdb6 ext4
/dev/sda1 ext4
/dev/sda5 ext4
/dev/sda6 ext4

```

I formatted the secondary hard drive to hold my documents and multimedia files, and I assume it's the sdb partitions.
Not sure how a swap landed on that secondary drive.

sda is what I reserved fdor the system and that was completely formated, to my knowledge.

More weird things again? ;)

---

### Post by Bashing-om on 2015-11-09
33Nicolas; Hummm ...

You can not start the GUI and in the GUI activate a terminal ( XTerm on my system is the default ) ? There you have copy paste .

Just how many installs do you have ?? 5 ! ???

If we can not get complete outputs of commands .. well we again install pastebinit, and pass the outputs to the site.

Need to look at :
```

sudo fdisk -lu
sudo parted -l
sudo blkid
df -h

```
Let's figure out what you have where, and get them labeled ..
Be aware in multiple installs, there can be only one operating system controlling the boot process at any given instance on each hard drive . There can be only ONE . You must control which one is ONE .
For your reference only ... My system with 5 installs:
```

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie1504" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
/dev/sdc3       204806144   266246143    30720000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux
sysop@1404mini

```

[INDENT][INDENT]we got to point the
[INDENT][INDENT]flying fickle finger of fate
[INDENT][INDENT][INDENT][INDENT]in the right direction
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-09
Bashing-Om;

Just to clarify:

```
You can not start the GUI and in the GUI activate a terminal ( XTerm on my system is the default ) ? There you have copy paste .
```

When I start the computer I get to the desktop, but when I try to log onto my username with the correct password on the dialog box below in the picture, it says it cannot start session. There is no terminal session I can start from here, no clicking or right clicking either. It has four basic functions top right, time, keyboard layout, network, sound and shutdown, reboot, etc. Those are the only thing I can access with a mouse.

When I do Control Alt F1, I get to the command prompt, but not a terminal session. It closes this purple desktop and I'm back at the command prompt that takes up the entire screen, much as it was before installing xfce4. I hope that makes sense. Here's a picture of what I see.

[ATTACH=CONFIG]265458[/ATTACH] that's the dialog box on the left hand side I see. Nothing happens besides that.

As to the installations, I had a few installs before Ubuntu Studeio  and the toughest one was AVLinux, which had a few quirks. Maybe it installed on sdb. I certainly never chose my secondary drive for an OS install. That one is off limit, or so I thought. As far as I'm concerned the only boot is on sda 1. I only want to save Documents and Multimedia if possible, but I have a few backups in case, the rest is nothing I use. AVLinux could explain why I have those weird extra sadb partitions. I certainly never created on them consciously on this machine.

```
If we can not get complete outputs of commands .. well we again install pastebinit, and pass the outputs to the site.
```

I'm OK doing that. In fact, I'm OK formating everything but those Documents and Multimedia partitions if that makes it easier. What do you think? Thx again.

---

### Post by sudodus on 2015-11-09
Are there any non-standard characters in your password, that might be interpreted differently in a text screen and the login window? That might cause your problems to log in. If that is the case, you could log back in to the text screen and change password with

```
sudo passwd
```

See ```
man passwd
``` if you need instructions. You can select a very simple password, for example **changeme** just to be sure that the characters work in graphics mode, and after checking you can select another and better password.

---

### Post by Bashing-om on 2015-11-09
33Nicolas; Welp;;

We have options. Bear in mind we are here to assist you in any manner you dictate.
I have no heartburn at all with cleaning everything up ( wiping the disk ) and starting all over . but the learning experience to fix this present install may be good for all of us.

@ sudodus; A good day to you, sir ! Sure glad you are in here with us.

@Nick. how about we try and start the GUI from terminal (TTY1) ?

Boot to grub, 'e' key for edit mode -> boot parameters screen :
The line starting with linux and containing " quiet splash " replace quiet splash with the term "text" with out the quotes, and remove all after.
key combo ctl+x to continue the boot process to TTY1.
Login here with user name and password.
now what results with terminal command:
```

startxfce4

```

Now, if you can not log in to TTY1 .. well then I think we are best served to just back up the 10 yards and punt . We start all over with a clean install, and this time .. keep it real simple, one thing at a time .
We put 'pastebinit' back in our back pocket, see what we need to do.

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-09
Sudodus,

No strange characters. Just regular stuff. No odd characters. I can change that password and make an easier one in the meantime. Wouldn't it give me an error message if characters were throwing off the system? Tx

Bashing-Om, 

I will get to it later this evening, if not tomorrow morning. Sounds like a plan. Will start xfce4 TTY. 

Maybe I'm not sure what the difference is between terminal and TTY. I believe terminal is the command prompt shell you can use in a desktop session and TTY is just the command prompt from the kernel directly, if this makes any sense. Tx

---

### Post by Bucky Ball on 2015-11-09
That was pretty much my understanding, yea.

---

### Post by 33Nicolas on 2015-11-09
Bashing-Om,

Weird problem trying to start xfce4 from TTY. I think  I know the difference now between TTY and the terminal inside a desktop  GUI!

I logged in my username and password on TTY and got a few fatal errors

```
 
(EE)

Fatal server error
(EE) Server is already active for display 0
If this server is no longer running, remove /tmp/.XO-lock
and start again

After that it tells me where to find help wiki.x.org

No protocol specified
xinit: giving up
xinit: unable to connect to x server: Resource temporarily unavailable
xinit: server error

```

I should reinstall it?

Tx

---

### Post by Bucky Ball on 2015-11-09
Nope. It is already installed and as far as the install is concerned, your display is up and running as it should be (even though not as it should look). It is throwing the error because you are trying to start another on the same display by the looks. The plot thickens ... :-k

There is nothing when you hit control+alt+F7? That is where the desktop should live.

---

### Post by 33Nicolas on 2015-11-09
Bucky Ball,

Control Alt F7 brings me back to the purple desktop with the same user name dialog box, as per the picture I uploaded previously.

If it says failed to start session whether I use my username and password or I try a Guest Session. What session does it mean? Sounds like the x server is up and running and xfce4 is properly installed. So what session is it talking about?

I'm starting to crave a simpler plot...

I appreciate all your communal patience while I put sme rest on my weary eyes for this evening.

---

### Post by Bashing-om on 2015-11-10
33Nicolas; Bucky ...

My thought processes are in total disarray .. booting to terminal and display 0 is active ???

I can not imagine how that could be - even though it is - What could possibly start a display at this point ?
All that should be running is the kernel and PID 1 and children, awaiting further instructions .

Maybe we investigate what pies lightdm has it's fingers in ??

Pardon me while
[INDENT][INDENT][INDENT]I re-arrange my thinking
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-10
fdisk is looking mighty tempting at this stage... Muhahahah. But, I'll restrain my quick-to-react fingers.

I'd like to know how to make sdb not boot, remove any partitions, except for Documents and Multimedia,and the rest can be used as an extra partition if needs be. Then, the entire sda can be formated into one partition and reinstall.

Does this make sense? In the meantime, I'm going to watch Star Trek and dream of talking to computers...

---

### Post by Bashing-om on 2015-11-11
33Nicolas; Well ..

How about we look and see if we can determine the file that is getting started ?
what have we :
Looking from the perspective of TTY1 ( terminal login )
```

ls -al

```
As I really am interested to know how the display is started in this instance.
And we start reading scripts !

EDIT: oopps .. no copy/paste in TTY1, so redirect to our paste site
```

sudo apt-get install pastebinit
la -al | pastebinit

```
and pass that URL back here to us.
[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-11
Bashing-Om,

Thanks for the reply. Just to clarify, in order to get to the TTY I have to first start the computer, which gets to that crippled desktop. Once there, I do Control Alt F1 and get to the TTY. Maybe that is one of the problem.

```
sudo apt-get install pastebinit la -al | pastebinit
```

[http://paste.ubuntu.com/13234034/](http://paste.ubuntu.com/13234034/)

Thanks!

---

### Post by Bashing-om on 2015-11-11
33Nicolas; Hey ...

just try'n to understand how your startup differs from my working start.
Without "looking" at pid 1's upstart ,,, what have we:
```

cat .bashrc
ls -al .config
ls -al .config/autostart
cat .profile

``` and then we start tracing lighdm's startup paths .

[INDENT][INDENT]what a web we weave
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-11
Bashing-Om,

Indeed, not sure why, but I suspect some installations went in the wrong places and some installations were not standard?

Do you think I can fdisk a few of those sbd partitions? Would that help?

Also, do you want me to do all this:

```

cat .bashrc
ls -al .config
ls -al .config/autostart
cat .profile

```

and copy it to here, or use pastebinit?



Thanks!

---

### Post by Bashing-om on 2015-11-12
33Nicolas; Hey !

A pastebin will be fine -- I do not expect to find anything relevant, but I do want to check.
We are looking at how lightdm gets started and what is going on with the login manager and maybe the greeter .

Now this is your system and your think'n ... but, but but ......
For my peace of mind, and for my own thought process and a quick way to get you booting ....
How about we wipe that disk and start all over with an install ? Do this new install in small stages,
get the base system installed
insatll xorg -- NO login manager ! 
install xfce4
install a web browser ...............
Stop ... and now see what the operating system is ..........

Then continue with another application install -- one at a time .. so we do not run into unknown conflicts .

Just my feelings, but I would feel the better about getting you a good reliable system by a (RE-)install and keep it simple and in small stages. 
However, I also welcome this oportunity to learn more about lighdm . If you want and have a desire to use lighdm .. hey we fight till we win .
We can mount the partitions of the target hard drive and see what is where and decide if to wipe the drive and just delete a partition(s) .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-11-12
Hey Bashing-Om,

Both venues sound good to me. I'm learning a heck of a lot and I've relegate the computer to a test bed. 

```
A pastebin will be fine -- I do not expect to find anything relevant, but I do want to check.
We are looking at how lightdm gets started and what is going on with the login manager and maybe the greeter .
```

Okidoky, I will do this tomorrow afternoon.

```
How about we wipe that disk and start all over with an install ? Do this new install in small stages,
get the base system installed
insatll xorg -- NO login manager ! 
install xfce4
install a web browser ...............
Stop ... and now see what the operating system is ..........
```

Makes perfect sense to me. That will be step 2. I will need help on formatting sda. I thought I did it last time, and wonder what happened. I would like to format the sdb partitions that are irrelvant also. I will need help for both :)

```
I would feel the better about getting you a good reliable system by a (RE-)install...
```

Me too :)

```
If  you want and have a desire to use lighdm .. hey we fight till we win . We can mount the partitions of the target hard drive and see what is  where and decide if to wipe the drive and just delete a partition(s) .
```

No comprendo... slight reference to The Tick TV series.

I'm happy you're here to help me out, as with everyone else. I like the learning part.

---

### Post by Bashing-om on 2015-11-12
33Nicolas; Hey .. 

IF and the stress is on IF .. we are to (RE-)install ; best if we know what is on the hard drives and determine for sure which hard drive we will make this new install onto.
To that end .. I do suggest we work from a live environment. Got a desktop install DVD made up ? - besides, we probably want GParted ( partition editor) that is available on this liveDVD .

It then is no big deal from this live environment in "try ubuntu" mode to mount the various partitions, see what is there and save what we want to .
Know then what partition is what, and what each contains . At some point get these partitions labeled .

If you have not guessed it .. I do lean to a fresh new install and a fresh new start . But it still, your call .

I really adhere to
[INDENT][INDENT][INDENT]clean and simple
[/INDENT][/INDENT][/INDENT]

---

### Post by sudodus on 2015-11-13
> **Bashing-om said:**
> ...
How about we wipe that disk and start all over with an install ? Do this new install in small stages,
...


+1

---

### Post by 33Nicolas on 2015-11-13
I feel reassured. Agreed. Tomorrow, I'll wipe out everything and redo a correct install.

---

### Post by Bucky Ball on 2015-11-13
> **33Nicolas said:**
> I feel reassured. Agreed. Tomorrow, I'll wipe out everything and redo a correct install.

+1.

Couple of tips while you're on a break from it as I noticed you were using code tags for quotes: use [quote] tags for quotes. There is an icon in the toolbar. There is also a 'Reply with Quote' option at the bottom right corner of the post you'd like to quote. :)

Let's see how you go this time. Consider that a learning experience. :)

---

### Post by 33Nicolas on 2015-11-13
> **Bucky Ball said:**
> +1.

Couple of tips while you're on a break from it as I noticed you were using code tags for quotes: use [quote] tags for quotes. There is an icon in the toolbar. There is also a 'Reply with Quote' option at the bottom right corner of the post you'd like to quote. :)

Let's see how you go this time. Consider that a learning experience. :)

Gotcha, thanks for the heads up. I should have remembered my basic html. Quote, Code and html. Got it.

Tomorrow I'll wipe out everything and start with a clean plate, one step at a time.

Thanks for your help.

---

### Post by Bucky Ball on 2015-11-13
Good plan. :)

---

### Post by 33Nicolas on 2015-11-14
I will close this thread and start a new one as creating a minimal install. Thanks everyone.

---

### Post by Bucky Ball on 2015-11-14
Good plan, again. I thought you'd started with a minimal install? Anyway, will keep an eye out. Make sure you have a solid plan and I suggest installing just the essentials to start with, like the desktop and synaptics, and building up from there. If something breaks, you'll have a clearer idea of what broke it. Never had many problems with minis myself so not sure what's going wrong. 

A reinstall is overdue on this, but sounds like you learned plenty. So good luck of the second attempt. :)

---

