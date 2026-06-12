---
title: "Feisty really slow to start up"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by Valshar on 2007-04-05
Well, after the last apt-get upgrade I did, the next time I started up ubuntu the loading screen took ages to complete, although when I finally logged everything was fine, so I restarted and pressed alt+ F1, and when it says "Configuring network devices", nothing seems to be happenning for a while, I think it there's some kind of error that's corrected or something and suddenly it continues booting normally and gets to the login screen. Not that anything's not working well nor anything, it just takes ages to get to work. Anyone have any idea what the problem is? Sorry if I wasn't very clear, I just dunno how to explain myself any better, haven't been using ubuntu for very long...

---

### Post by liveforfunnow on 2007-04-05
I get this too. Same exact problem. Clean install of Feisty. Recovery or regular boot, takes twice as long before the update, and hangs at "configuring network devices."

Mods, might this belong in the Development section?

---

### Post by Valshar on 2007-04-05
I upgraded from edgy. Sorry if it's the wrong place, I wasn't very sure where to post this

---

### Post by wpshooter on 2007-04-05
> **Valshar said:**
> Well, after the last apt-get upgrade I did, the next time I started up ubuntu the loading screen took ages to complete, although when I finally logged everything was fine, so I restarted and pressed alt+ F1, and when it says "Configuring network devices", nothing seems to be happenning for a while, I think it there's some kind of error that's corrected or something and suddenly it continues booting normally and gets to the login screen. Not that anything's not working well nor anything, it just takes ages to get to work. Anyone have any idea what the problem is? Sorry if I wasn't very clear, I just dunno how to explain myself any better, haven't been using ubuntu for very long...

Why don't you file a bug report ?

---

### Post by iClouseau88 on 2007-04-05
How do you file a bug report?  I also experience an unusually long restart.  I am still waiting for my laptop to boot into Ubuntu (Feisty).

---

### Post by Valshar on 2007-04-05
Yeah I really dunno how to either,heh

---

### Post by maestrobwh1 on 2007-04-05
I have the same problem.  After the last update, the slider for startup seems to hang at about 1/3 the way over for a full minute.  I tried to see what was going on by using the recovery mode, and it really seemed to hang at configuring my network settings.  This is totally new and I have Edgy in the next partition and it does not do this so it is not my connection.

---

### Post by maestrobwh1 on 2007-04-05
I just did submit a report in Launchpad.

---

### Post by liveforfunnow on 2007-04-05
> **maestrobwh1 said:**
> I just did submit a report in Launchpad.

can you provide a link? thanks!

---

### Post by Foaming Draught on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+bugs?field.searchtext=%2Bfeisty+%2Bboot&amp;orderby=-datecreated&amp;search=Search&amp;field.status%3Alist=Unconfirmed&amp;field.status%3Alist=Confirmed&amp;field.status%3Alist=In+Progress&amp;field.status%3Alist=Needs+Info&amp;field.status%3Alist=Fix+Committed&amp;field.assignee=&amp;field.bug_reporter=&amp;field.omit_dupes=on&amp;field.has_patch=&amp;field.has_no_package=](https://launchpad.net/ubuntu/+bugs?field.searchtext=%2Bfeisty+%2Bboot&amp;orderby=-datecreated&amp;search=Search&amp;field.status%3Alist=Unconfirmed&amp;field.status%3Alist=Confirmed&amp;field.status%3Alist=In+Progress&amp;field.status%3Alist=Needs+Info&amp;field.status%3Alist=Fix+Committed&amp;field.assignee=&amp;field.bug_reporter=&amp;field.omit_dupes=on&amp;field.has_patch=&amp;field.has_no_package=) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Searching in Launchpad with <+feisty +boot>  produces lots of recent bug reports (link below).

They all seem to have in common that Ubuntu (& Kubuntu) is waiting for WEP/WPA but the keyring doesn't come into play until after the system's got fed up with waiting.  I wait for a couple of minutes or more at around a third of the way through the boot bar.

Then, when I get a screen after a long wait, I have to click on the Keyring item on the lower panel, <on top> , before  I can keep Keyring open long enough to enter a full password to release my WEP key and end Network Manager's frenzied whirling.

This condition has only existed for a couple of days.

---

### Post by old_geekster on 2007-04-06
> **Valshar said:**
> Well, after the last apt-get upgrade I did, the next time I started up ubuntu the loading screen took ages to complete, although when I finally logged everything was fine, so I restarted and pressed alt+ F1, and when it says "Configuring network devices", nothing seems to be happenning for a while, I think it there's some kind of error that's corrected or something and suddenly it continues booting normally and gets to the login screen. Not that anything's not working well nor anything, it just takes ages to get to work. Anyone have any idea what the problem is? Sorry if I wasn't very clear, I just dunno how to explain myself any better, haven't been using ubuntu for very long...
I did an upgrade from Edgy and I am having the same exact problem.  I believe it is a problem with the network devices, also,  Just before the boot process resumes, the Internet light on my modem lights up.

Since you are filing a bug report, I won't at this point.

---

### Post by donkyhotay on 2007-04-06
I have a similar issue, I just upgraded 2 different systems to feisty. One works just fine the other however appears to hang up during the boot process but if I wait long enough (about a minute or so) it will start booting normally. By switching TTY I found that at the part it slows up at it gives 1 of the 2 following error mesage: 
ata2.00:failed to set xfermode (err_mask=0x4)
or
ata2.01:failed to set xfermode (err_mask=0x4)
and does this about 4 times before going back to 'normal' booting. Once booted the system still doesn't recognize either of my two optical drives. Booting with kernel 2.17.* works just fine without any issues (not slow, optical drives work fine). I would think it was just a flawed kernel issue except this only happens to one of my computers and the other runs feisty with no issues. Anyone have any ideas?

---

### Post by unai_goiko on 2007-04-06
> **Foaming Draught said:**
> **This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+bugs?field.searchtext=%2Bfeisty+%2Bboot&amp;orderby=-datecreated&amp;search=Search&amp;field.status%3Alist=Unconfirmed&amp;field.status%3Alist=Confirmed&amp;field.status%3Alist=In+Progress&amp;field.status%3Alist=Needs+Info&amp;field.status%3Alist=Fix+Committed&amp;field.assignee=&amp;field.bug_reporter=&amp;field.omit_dupes=on&amp;field.has_patch=&amp;field.has_no_package=](https://launchpad.net/ubuntu/+bugs?field.searchtext=%2Bfeisty+%2Bboot&amp;orderby=-datecreated&amp;search=Search&amp;field.status%3Alist=Unconfirmed&amp;field.status%3Alist=Confirmed&amp;field.status%3Alist=In+Progress&amp;field.status%3Alist=Needs+Info&amp;field.status%3Alist=Fix+Committed&amp;field.assignee=&amp;field.bug_reporter=&amp;field.omit_dupes=on&amp;field.has_patch=&amp;field.has_no_package=) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Searching in Launchpad with <+feisty +boot>  produces lots of recent bug reports (link below).


There are 2 bug reports already filled in:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103413]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103413")
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/103085]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/103085")

In my personal opinion, it seems to be something related with the network configuration, more specifically with the fact that ubuntu tries to get a dhcp offer from the eth0 interface when it's not connected.

---

### Post by Valshar on 2007-04-06
when it's "loading hardware drivers", I get something like

[     22.5240000 intel_rng]: FWH not detected

should I file a bug report or do those other ones suffice?

---

### Post by chikko on 2007-04-07
same problem here.  using kubuntu feisty.  waiting for your updates guys..:)

---

### Post by chikko on 2007-04-08
sorry for double posting, but i've been examining the problem for the past half hour and here's a little temporary fix to this problem:

edit the networking boot file
```

sudo kedit /etc/rcS.d/S40networking

```
(if you got no kedit use gedit or something)

now, put "##" in your code as follow:
(or simply overwrite your code with those lines respectively)
```

case "$1" in
start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
##	if [ "$VERBOSE" != no ]; then
##	    if ifup -a; then
##		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	else
##	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

stop)

```

the result:  no pausing or stucking during bootup, and the network device still works as usual..

---

### Post by slkuhn on 2007-04-09
> **chikko said:**
> sorry for double posting, but i've been examining the problem for the past half hour and here's a little temporary fix to this problem:

the result:  no pausing or stucking during bootup, and the network device still works as usual..


Wow This works great. I booted up in no time. May I ask what does it do exactly?

---

### Post by pixeldotz on 2007-04-11
seems to me like it's over writing the timeout function from 120 seconds to 15 seconds. do i win a cookie?

this good to know since i'm currently upgrading from 6.10-->7.04. i've had enough problems installing ubuntu this would've got me frustrated.

thanks :)

---

### Post by amosharper on 2007-04-24
> **donkyhotay said:**
> I have a similar issue, I just upgraded 2 different systems to feisty. One works just fine the other however appears to hang up during the boot process but if I wait long enough (about a minute or so) it will start booting normally. By switching TTY I found that at the part it slows up at it gives 1 of the 2 following error mesage: 
ata2.00:failed to set xfermode (err_mask=0x4)
or
ata2.01:failed to set xfermode (err_mask=0x4)
and does this about 4 times before going back to 'normal' booting. Once booted the system still doesn't recognize either of my two optical drives. Booting with kernel 2.17.* works just fine without any issues (not slow, optical drives work fine). I would think it was just a flawed kernel issue except this only happens to one of my computers and the other runs feisty with no issues. Anyone have any ideas?

I have this problem, too, although my optical drives are fine. I had a little trouble with my wireless cards, and I'm not using the network-manager applet - seems to be since I fiddled around with ndiswrapper.

---

### Post by liveforfunnow on 2007-04-24
just an FYI, a clean install of the final version of 7.04 does not have this issue.

---

### Post by kernelsandirs on 2007-04-24
try this [http://ubuntuforums.org/showpost.php?p=2513159&postcount=4]("http://ubuntuforums.org/showpost.php?p=2513159&postcount=4")

I am not sure it fixes the network card issues for sure but it certainly fixed the "failed... ...xfermode" issue for me, and fixed my cdrw drive issues

---

### Post by vratnica on 2007-04-27
i have solved this problem


i had this problem first with feisty beta, and because of that i installed mint edgy and waited for LTS

as i have installed LTS Feisty, I saw that problem is still there, so I solved it by installing debian

maybe if I read one day here that the system is debugged i will try then Feisty again, till then-debian

but I must say that I am really really sorry for being forced to leave ubuntu (I dont want  to downgrade- if I am to downgrade, i would downgrade to windows)

---

### Post by DarkStarAeon on 2007-04-30
I just upgraded my wifes computer to Feisty from Edgy and hers also has a really really long boot time. My computer does not have this issue at all, so I was very surprised. 

When the loading bar is displayed it just stays at the very beginning for almost 6 minutes, then suddenly it rockets forward and loads.

Weird.

---

### Post by Arkian on 2007-04-30
I used the Official Upgrade method ([http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)) to perform an upgrade from Edgy to Feisty 7.04.

No delayed boot here.

---

### Post by vratnica on 2007-04-30
that s nothing to wonder

somebody has this bug and somebody not. nobody said that all people must have this slow down

---

### Post by DarkStarAeon on 2007-04-30
Exactly.

My computer boots fine, my wifes is slow.

I don't care if someone else **isn't** having that same problem, lol.

---

### Post by depele on 2007-05-01
My computer boot time is pretty well, around 1m30s.

But since the upgrade my network won't start on bootup. 

any ideas?

grtz

---

### Post by vratnica on 2007-05-01
downgrade if you want to stay with ubuntu. i would recommend mint 2.2

it s a bug that won`t be solved soon, I think

if somebody has contrary info, lets see it, I would be glad

---

### Post by depele on 2007-05-01
hmmz, I don't feel like downgrading.

not other idea's?

---

### Post by vratnica on 2007-05-01
I have been looking for other ideas since the Feisty was beta. i have never found some that works

---

### Post by DarkStarAeon on 2007-05-01
Mine boots in 34 seconds on Feisty, and booted in 31 seconds on Edgy.

My wifes takes over 5 minutes on Feisty, and took only about 45-60 seconds on Edgy.

That's a pretty big difference for hers.

---

### Post by vratnica on 2007-05-03
so my dear DarkStarAeon  , here is a present for your wife

[http://ubuntuforums.org/showthread.php?p=2525651](http://ubuntuforums.org/showthread.php?p=2525651)

the most important part>

> so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll 

:popcorn:

---

### Post by DarkStarAeon on 2007-05-03
vratnica , you bleepin' rule. :)  thank you for pointing me there!

That took care of it, and boot time went to 50 seconds, down from 5 minutes ;)

I noticed several people in that thread said they have Asus P4P800 motherboards, which is exactly what my wifes computer has. odd.

Thanks again! :guitar:

---

### Post by jack_teagarden on 2007-05-03
I edited the networking file (look on page 2), and now I have no networking!
I copied the backup "/etc/rcS.d/S40networking~" to "/etc/rcS.d/S40networking", and then remade the link from "etc/init.d/networking", with no effect.
I'm stumped!
Help?

---

### Post by jack_teagarden on 2007-05-03
If it helps, I have a nearby windoze box with networking, (i'm on it now!)
I also have all root priveledges and everything.
Please help me, I'm totally lost~!

---

### Post by vratnica on 2007-05-04
> **DarkStarAeon said:**
> vratnica , you bleepin' rule. :)  thank you for pointing me there!

That took care of it, and boot time went to 50 seconds, down from 5 minutes ;)

I noticed several people in that thread said they have Asus P4P800 motherboards, which is exactly what my wifes computer has. odd.

Thanks again! :guitar:

ur wellcome!

u know, the thing that fascinates me by ubuntu is ubuntu community. i tried debian, which I have on an other partition, but their forums are dead, and u cannot expect any help

@jack

I think u should search the forum or start a new topic. i dont think that u will solve it here

---

### Post by jack_teagarden on 2007-05-04
thanks

---

### Post by ZERO_SHIFT on 2007-05-08
Hi

My laptop running feisty is really slow on booting. Where do I exactly add the word **irqpoll** to?

This is how my boot/grub/menu.lst file looks like:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=54388bb1-ee98-4810-857b-8b2a5b3384c8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=54388bb1-ee98-4810-857b-8b2a5b3384c8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=54388bb1-ee98-4810-857b-8b2a5b3384c8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thanks

---

### Post by ZERO_SHIFT on 2007-05-08
never mind found it:lolflag:

---

### Post by DarkStarAeon on 2007-05-08
well, there you go. lol

---

### Post by ZERO_SHIFT on 2007-05-08
Actually there was no difference, I still have slow booting furthermore I constantly get the checking hard disk thing that takes ages saying that my disk has been mounted for 25 times without being checked so check forced.

Any Ideas??

Thanks

---

### Post by DarkStarAeon on 2007-05-08
Not sure really man. After I added that to my mine, I rebooted and got the check disk thing you described, but after another reboot it was fine.

---

### Post by digitalbenji on 2007-05-23
That solution of commenting out stuff in the startup S40 script cut a full minute off my boot time.  Even more than a minute.  That's great!

Thanks.

---

### Post by stchman on 2007-05-23
> **Valshar said:**
> Well, after the last apt-get upgrade I did, the next time I started up ubuntu the loading screen took ages to complete, although when I finally logged everything was fine, so I restarted and pressed alt+ F1, and when it says "Configuring network devices", nothing seems to be happenning for a while, I think it there's some kind of error that's corrected or something and suddenly it continues booting normally and gets to the login screen. Not that anything's not working well nor anything, it just takes ages to get to work. Anyone have any idea what the problem is? Sorry if I wasn't very clear, I just dunno how to explain myself any better, haven't been using ubuntu for very long...

Try fixing your /etc/hosts and /etc/hostname

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

It made my Ubuntu install very peppy.

---

### Post by CrankyFilipino on 2007-07-03
I'm sorry but I'm quite new to Linux.. am i supposed to only put in everything that starts with ##? Does that mean not the whole thing, or do I leave out the ##?

---

### Post by huffy318 on 2007-07-03
> **CrankyFilipino said:**
> I'm sorry but I'm quite new to Linux.. am i supposed to only put in everything that starts with ##? Does that mean not the whole thing, or do I leave out the ##?

Welcome to Linux, Cranky.
# is for comments, so those are lines you can leave out.
Or, if you are trying to comment out lines (IE, make them not run, but keep them in case you need them later), just add the #.  Multiple #'s (like ##) don't do anything different: they are there to make it easier to read.

---

### Post by CrankyFilipino on 2007-07-05
thanks.. i copy pasted what he said into that file and it increased my boot up speed by about 15-20 seconds.. which shows just how slow it was going already

---

### Post by yusufk on 2007-07-05
I have a problem with the amount of time it takes to get Gnome up and running. From the time I login to gnome to the time the panels have loaded, it takes more than 3 minutes. Sometimes I get an error about the trash can applet and I get asked if I want to delete it, which doesn't make a dif. At one stage, I used to pull out my lan cable, which would speed things up (network manager?), but that doesn't seem to make a difference. I've removed gdesklets and beagle from my session startup list but still no difference. If I press ctrl-alt-f1 and go to a terminal, I can login, top doesn't show any processes with high cpu and the hard disk is not busy. It just seems to be waiting for something.

---

### Post by GrouchoMarx on 2007-07-08
If you're using ndiswrapper, the delay may be because the network interface is being accessed before ndiswrapper is loaded. Try adding "ndiswrapper" to /etc/modules:

> ```
gksudo gedit /etc/modules
```

Then add "ndiswrapper"

This seems better than commenting out parts of /etc/network/interfaces and leaving the interfaces unconfigured, no?

---

### Post by arpi_amsterdam on 2007-07-18
I had the same problem and my fix was similar to the alteration of the networking init script..

Gnome uses the NetworkManager to manage the networks you can connect to. I read somewhere that you should comment all the interfaces mentioned in /etc/networking/interfaces. I yet have to find out why, but it works great! For me anyways.

---

### Post by WI_Mike on 2007-07-27
Hello,

I am also having a startup problem. I just did an aptitude update and when I restarted my startup hangs at these sections.

"Starting early crypto disks..."

Here is pauses for about 2 minutes, then startup pauses for about 90 seconds at 

"Starting Hardware Abstraction Layer hald"

I have never had these problems before until I aptitude updated. It seems from the other posts in the thread that it's network related, but my startup does not pause at that point.  

I searched and searched the forums, but there are no solutions. Help please, this is annoying.

Thanks.

---

### Post by WI_Mike on 2007-08-08
Hello?

Does any one have any idea how I can speed up the boot time so my system does not hangfor over a minute at 

Starting HALD 

???  ](*,)

---

### Post by vratnica on 2007-08-13
now I again have a problem with booting, although I have not done any experiments, only updated the system

after short time booting stops and I get the message "Eth2: Too much work at interrupt, status= 0x0000ffff" and I have to manually turn off my computer

and this problem I have only sometimes but recently it becomes more often, maybe every second time booting

Is there somebody with an idea?

---

### Post by nuclearj on 2007-10-24
> **vratnica said:**
> now I again have a problem with booting, although I have not done any experiments, only updated the system

after short time booting stops and I get the message "Eth2: Too much work at interrupt, status= 0x0000ffff" and I have to manually turn off my computer

and this problem I have only sometimes but recently it becomes more often, maybe every second time booting

Is there somebody with an idea?

Maybe you should start a new thread because this is a different problem then you had before...

After 5 pages of reading and six different solutions i still do not have an answer to this problem.  I'm not sure which one works!  I'll just wait for the next LTS release and put up with the long load time until then.

---

