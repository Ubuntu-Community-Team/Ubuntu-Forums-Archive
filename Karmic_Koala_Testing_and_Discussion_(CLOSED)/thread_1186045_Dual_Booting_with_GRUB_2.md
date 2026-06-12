---
title: "Dual Booting with GRUB 2"
date: 2009-06-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-06-12
Karmic Alpha 2 put Grub2 on.  

On two machines I've tried so far Grub2 did NOT find the existing Karmic Alpha 1, Jaunty, or Intrepid images.  For testing Ubuntu pre-releases I usually have 3 or 4 or more bootable images on my test pc's since some of them are broken at any one time by Ubuntu updates etc.

I looked thru the Alpha 2 announcement, the Grub2 introductory manual pages, etc.  I didn't find anywhere what to do if Grub2 installed and missed the existing Ubuntu multiboot setup.

I didn't see anywhere any script that told Grub2 to go back and look for the images Grub2 missed the first time.

What do I do, put Grub back on with Super Grub?  

If I'm going to do that, I'll make a stab at editing the file it says not to edit by copying the UUID's etc. from the existing /boot/grub/menu.list entries.

Jerry

---

### Post by ranch hand on 2009-06-12
[http://ubuntuforums.org/showthread.php?p=7445044#post7445044](http://ubuntuforums.org/showthread.php?p=7445044#post7445044)

I just installed Kinky Kitten (9.10alpha-2, I know they call it something else) and havethe same problem.  I have been following the above thread because I really like messing with grub, as you must, and love it.

I assume that we will like this version once it is mature and we get to know it.

---

### Post by autocrosser on 2009-06-12
Jerry--I have a bug report about multi-boot fail--look in my thread about grub2 theming & the main grub2 thread....I also have posted a "fix" to grub.cfg in the theming thread.

---

### Post by super.rad on 2009-06-12
> **jerrylamos said:**
> Karmic Alpha 2 put Grub2 on.  

On two machines I've tried so far Grub2 did NOT find the existing Karmic Alpha 1, Jaunty, or Intrepid images.  For testing Ubuntu pre-releases I usually have 3 or 4 or more bootable images on my test pc's since some of them are broken at any one time by Ubuntu updates etc.

I looked thru the Alpha 2 announcement, the Grub2 introductory manual pages, etc.  I didn't find anywhere what to do if Grub2 installed and missed the existing Ubuntu multiboot setup.

I didn't see anywhere any script that told Grub2 to go back and look for the images Grub2 missed the first time.

What do I do, put Grub back on with Super Grub?  

If I'm going to do that, I'll make a stab at editing the file it says not to edit by copying the UUID's etc. from the existing /boot/grub/menu.list entries.

Jerry

I tried editing the file it says not to edit (/boot/grub/grub.cfg) and it wouldn't let me save even as root

---

### Post by taavikko on 2009-06-12
> **super.rad said:**
> I tried editing the file it says not to edit (/boot/grub/grub.cfg) and it wouldn't let me save even as root

check it's permissions! it's for a good reason that way.
Like it states, "Do not edit"

---

### Post by autocrosser on 2009-06-12
I have been editing a copy of it & then using the copy without problems---have been talking to the dev of grub2's gfxmenu & am trying to get the dev for SUM involved so we can get a reasonable way to edit the file.....Please take a look at the Grub2 theming thread.

[http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)

---

### Post by ranch hand on 2009-06-12
Do not edit that file.

The file you need is in /etc some place.  Check 

[http://ubuntuforums.org/showthread.php?t=1182199](http://ubuntuforums.org/showthread.php?t=1182199)

It is in there somewhere.

---

### Post by autocrosser on 2009-06-12
Sorry--there are times you NEED to---from what I hear you can get to parts of it, but not all---if you accept the possible fact that the .cfg will be over-written on the next sudo update-grub & keep a backup file around you will be OK--I'm trying to get people that are involved in Grub2 to get a editor ASAP......As for now manual editing is the ONLY answer for several use cases.

I have been following development of Grub2 for over a year now & have a rather firm idea of what is going on.

---

### Post by ranch hand on 2009-06-12
/etc/default/grub

---

### Post by autocrosser on 2009-06-12
> **ranch hand said:**
> /etc/default/grub

Sorry--that still will not change some of the variables I need changed. OS-Prober has barfed values that I need to manual edit.

---

### Post by super.rad on 2009-06-12
> **autocrosser said:**
> 
I have been following development of Grub2 for over a year now & have a rather firm idea of what is going on.
Then could you explain how I chainload fedora and suse's grub's from grub2, i would usually just edit menu.lst and put
```
title Fedora
root (hd0,0)
chainloader +1
```
but with grub2 i have no idea what to put and where to put it :p
A few people have suggested os-prober but that won't run for me, just throws out a load of errors

---

### Post by autocrosser on 2009-06-12
I don't have anything chain-loaded on my system--I'll ask on the developer's list tonight when I get home.....

---

### Post by super.rad on 2009-06-12
thanks, is a bit annoying not being able to boot into fedora or suse

---

### Post by jerrylamos on 2009-06-12
> **super.rad said:**
> I tried editing the file it says not to edit (/boot/grub/grub.cfg) and it wouldn't let me save even as root

First you have to 
sudo chmod 644 /boot/grub/grub.cfg
then
sudo gedig /boot/grub/grub.cfg
after saving original, of course.....

Good luck.  I edited it and it won't cooperate.  Still boots the Karmic A2 but nothing else.

Jerry

---

### Post by jerrylamos on 2009-06-12
> **super.rad said:**
> thanks, is a bit annoying not being able to boot into fedora or suse

I presume we have to put Grub back on until (maybe) A3....

Jerry

---

### Post by jerrylamos on 2009-06-12
> **taavikko said:**
> check it's permissions! it's for a good reason that way.
Like it states, "Do not edit"

Yes, it says "Do not edit" because you are up the proverbial creek without a paddle.  They are not about to tell us how to get back to Karmic A1 Grub functionality.  Maybe A3?

Let me give another feeble attempt or two of finding the (hidden from us users) syntax for Grub2, then on to SuperGrub and install Grub.  If it will boot A2?

Jerry

---

### Post by super.rad on 2009-06-12
best guide for grub2 I have found so far is from the Arch Wiki (best linux documentation anywhere)
[http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2)

---

### Post by MacUntu on 2009-06-12
> **autocrosser said:**
> Sorry--that still will not change some of the variables I need changed. OS-Prober has barfed values that I need to manual edit.

Can't you edit them in let's say /etc/grub.d/10_linux?

---

### Post by autocrosser on 2009-06-12
> **MacUntu said:**
> Can't you edit them in let's say /etc/grub.d/10_linux?

It would be very nice if that would cure my problem....I have 4 drives in my system with 5 installs spread between them. OS-Prober is where my problem stems from....As of this date (I just saw yesterday information about a commit that changes this)--OS-Prober works with /dev/sdx instead of UUID's.....My problem is that Grub2 & OS-Prober are not playing nice with my BIOS (or the reverse)---I find that this Gigabyte board changes my drive locations at random intervals---this is not a problem as long as the partitions are called by UUID---but it's a BIG problem when partitions are called by /dev/sdx..

I saw a proposed commit to OS-Prober yesterday to allow OS-Prober to use UUID---I would guess that we will see it in about a month or so---depends on several factors--So as of right now I have very little choice but to manual edit until things are updated...I have a bug report in about this & I would guess that I am one of very few that have been "hit" by this, so I don't expect fast fix work..........

The OS-Prober section of grub.cfg will not accept UUID right now, so I created root=LABEL="name of partition" in the kernel lines to keep things pointed the right direction...I am editing only the grub.cfg so I can see when the commit I noted above comes thru---I keep a backup of my modified file so I can just change info as needed & reuse it until I (cross-fingers) don't need to any more.

---

### Post by autocrosser on 2009-06-12
> **super.rad said:**
> best guide for grub2 I have found so far is from the Arch Wiki (best linux documentation anywhere)
[http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2)

Did that chainloading info help you?  I can still post in the development list if you need it......

---

### Post by super.rad on 2009-06-12
> **autocrosser said:**
> Did that chainloading info help you?  I can still post in the development list if you need it......
Not really as the instructions there say to edit the /boot/grub/grub.cfg file

---

### Post by autocrosser on 2009-06-12
Well--IF you follow the syntax EXACTLY you can edit the grub.cfg without problems---I expect that will be the only short-term answer to the problems we all are having....OS-Prober is the real problem with multi-boot & I have seen commits to "repair or fix" the short-comings....

This is what my grub.cfg looks like after editing work--I can boot into all of my installs---ALL the time.

```

# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from  and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd2,2)
search --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
if loadfont /usr/share/grub/ascii.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd2,2)
search --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
insmod tga
if background_image /usr/share/images/grub/splash.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Karmic 2.6.30-8-generic" {
    set root=(hd2,2)
    search --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
    linux    /boot/vmlinuz-2.6.30-8-generic root=UUID=fc1446a5-94e9-40f8-9ebb-2442107fc13c ro  quiet splash
    initrd    /boot/initrd.img-2.6.30-8-generic
}
menuentry "Karmic 2.6.30-8-generic (recovery mode)" {
    set root=(hd2,2)
    search --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
    linux    /boot/vmlinuz-2.6.30-8-generic root=UUID=fc1446a5-94e9-40f8-9ebb-2442107fc13c ro single 
    initrd    /boot/initrd.img-2.6.30-8-generic
}
menuentry "Karmic 2.6.30-7-generic" {
    set root=(hd2,2)
    search --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
    linux    /boot/vmlinuz-2.6.30-7-generic root=UUID=fc1446a5-94e9-40f8-9ebb-2442107fc13c ro  quiet splash
    initrd    /boot/initrd.img-2.6.30-7-generic
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###

menuentry "Karmic Backup" {
    set root=(hd2,1)
        search --fs-uuid --set 356e0a23-302e-4054-9bdf-025cc85f1089
    linux /boot/vmlinuz-2.6.30-4-generic root=LABEL=backup
    initrd /boot/initrd.img-2.6.30-4-generic
}
menuentry "Jaunty 9.04" {
    set root=(hd4,1)
        search --fs-uuid --set 527253c9-7db5-458b-85b9-1aba8bb85955
    linux /boot/vmlinuz-2.6.28-11-generic root=LABEL=stable
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Foresight Linux (2.6.29.2-3-fl.smp.gcc4.1.x86.i686) (on /dev/sdc1)" {
    set root=(hd3,1)
    linux /boot/vmlinuz-2.6.29.2-3-fl.smp.gcc4.1.x86.i686 quiet ro vga=0x317 splash root=LABEL=testing1
    initrd /boot/initrd-2.6.29.2-3-fl.smp.gcc4.1.x86.i686.img
}
menuentry "Karmic x64" {
    set root=(hd3,3)
        search --fs-uuid --set 358ac090-55d8-4b7d-93ee-eb02fa538ca5
    linux /boot/vmlinuz-2.6.28-11-generic root=LABEL=testing2
    initrd /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###
```Note in the "os-prober" area I first tried UUID's---that resulted in the same sometimes the install would boot---sometimes not problem....

I next thought about LABELS--that is really another simple way to correctly define a partition---So I thought I'd give that a try..changing the "set root=" line did nothing, but adding the "root=LABEL=" after the kernel line resulted in correct loading of the selected OS every time......So, of course, you need to unmount the partition you want to label & in Partition-editor (Gparted)--select the unmounted partition & set the label....then you can edit the kernel line & have things boot correctly.

---

### Post by autocrosser on 2009-06-12
I found the post I was looking for.....Let's hope it gets to our level soon!!!!!

> Message: 1
Date: Thu, 11 Jun 2009 21:00:15 +0200
From: Felix Zielcke [EMAIL="fzielcke@z-51.de"]<fzielcke@z-51.de>[/EMAIL]
Subject: Re: [PATCH] add drivemap support to 30_os-prober.in and use
    UUIDs
To: The development of GRUB 2 [EMAIL="grub-devel@gnu.org"]<grub-devel@gnu.org>[/EMAIL]
Message-ID: [EMAIL="1244746815.3552.55.camel@fz.local"]<1244746815.3552.55.camel@fz.local>[/EMAIL]
Content-Type: text/plain

Am Sonntag, den 07.06.2009, 17:37 +0200 schrieb Felix Zielcke:[INDENT]> Attached patch uses `prepare_grub_to_access_device' to set the root in
> the generated entrys.
> And it adds drivemap to the chainload ones, if root isn't (hd0).
> 
> The Debian grub-installer adds map only with Dos and Windows, should I
> do the same or is it okay to do it for all?
> 
> -# update-grub helper script.
> +# grub-mkconfig helper script.
> Does this needs to be mentioned in ChangeLog?
[/INDENT]Commited.
-- 
Felix Zielcke




My bug report about the problem:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500)

---

### Post by ronacc on 2009-06-12
when I updated tonight a new kernel came down (2.6.30-9) , neither the menu.lst or grub.cfg was updated to boot the new kernel . manualy editing both files allows the new kernel to boot either by chainload or selecting it from the menu . as a side note on editing grub.cfg I found out that it had written the correct uuid there even though it had written an incorrect one in the menu.lst it generated .

---

### Post by autocrosser on 2009-06-12
Yes---looks like a bit more info collecting then a bevy of bug reports.......

---

### Post by ronacc on 2009-06-12
I bugged the uuid thing a couple of days ago .
[https://bugs.launchpad.net/bugs/385021](https://bugs.launchpad.net/bugs/385021)

---

### Post by autocrosser on 2009-06-12
> **ronacc said:**
> I bugged the uuid thing a couple of days ago .
[https://bugs.launchpad.net/bugs/385021](https://bugs.launchpad.net/bugs/385021)


Hmmmm---take a look at mine: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500)

I'm beginning to see a pattern.........

---

### Post by baneberry on 2009-06-12
I installed kubuntu 9.10 alpha2 today with the new GRUB 2.  I'd like to know how to be able to also boot into my Windows partition and FreeBSD partition.  I couldn't find documentation on GRUB 2.

Thanks.

---

### Post by autocrosser on 2009-06-12
I'm going to try UUID's in my kernel lines in the OS-Prober section to see if that works....

Edited file looks like:
```
### BEGIN /etc/grub.d/30_os-prober ###

menuentry "Karmic Backup" {
    set root=(hd2,1)
        search --fs-uuid --set 356e0a23-302e-4054-9bdf-025cc85f1089
    linux /boot/vmlinuz-2.6.30-4-generic root=UUID=356e0a23-302e-4054-9bdf-025cc85f1089
    initrd /boot/initrd.img-2.6.30-4-generic
}
menuentry "Jaunty 9.04" {
    set root=(hd4,1)
        search --fs-uuid --set 527253c9-7db5-458b-85b9-1aba8bb85955
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=527253c9-7db5-458b-85b9-1aba8bb85955
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Foresight Linux" {
    set root=(hd3,1)
    linux /boot/vmlinuz-2.6.29.2-3-fl.smp.gcc4.1.x86.i686 quiet ro vga=0x317 splash root=LABEL=testing1
    initrd /boot/initrd-2.6.29.2-3-fl.smp.gcc4.1.x86.i686.img
}
menuentry "Karmic x64" {
    set root=(hd3,3)
        search --fs-uuid --set 358ac090-55d8-4b7d-93ee-eb02fa538ca5
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=358ac090-55d8-4b7d-93ee-eb02fa538ca5
    initrd /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/30_os-prober ###
```

Will post back with info......

---

### Post by Slug71 on 2009-06-13
> **baneberry said:**
> I installed kubuntu 9.10 alpha2 today with the new GRUB 2.  I'd like to know how to be able to also boot into my Windows partition and FreeBSD partition.  I couldn't find documentation on GRUB 2.

Thanks.

Try this in Terminal

```
sudo os-prober

sudo update-grub
```

reboot.

---

### Post by ronacc on 2009-06-13
added myself to your bug . It does seem to mostly affect multiboot systems . let us know how your try of the uuids works out .I was going to try using my backup menu.lst and just adding the chainload line to it to let me boot my other installs , but thats for tomorrow , Its late and I want to get up early to watch the shuttle launch .

---

### Post by autocrosser on 2009-06-13
OK--I'm in my backup Karmic install after trying all in the OS-Prober menu section---adding the UUID to the kernel line works as well as the label method.....If you try to add UUID to any other location it's a no-go.....

So, I'm hoping the commit for UUID being set by OS-Prober works as well.....

Again---If you watch the syntax it goes without a hitch--slip anywhere & Grub2 b0rks rather badly........

---

### Post by baneberry on 2009-06-13
Thanks Slug!  It will be my project tomorrow morning.

---

### Post by taavikko on 2009-06-13
> **ronacc said:**
> I bugged the uuid thing a couple of days ago .
[https://bugs.launchpad.net/bugs/385021](https://bugs.launchpad.net/bugs/385021)

> **autocrosser said:**
> Hmmmm---take a look at mine: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500)

I'm beginning to see a pattern.........

Good stuff guys.

So it seems only to affect multi-boot enviroments.
My "one system/one machine" method of usage isn't affected.

---

### Post by ronacc on 2009-06-13
ok I tried merging my backup menu.lst (from just before installing grub2) with the one grub2 wrote (edited to correct the uuid).
it worked and I can now access my other installs from the menu . here is what I did , copied my bu menu.lst and grub2's menu.lst to a tmp directory for editing , opened both with gedit and from the bu cut everything above "## ## End Default Options ##" then from the grub2 menu.lst copied everything above "## ## End Default Options ##" and pasted it to the bu ,then copied the chainloader lines and pasted them just below "## ## End Default Options ##" , and saved the result under a different name . then opened a root nautilus , went to /boot/grub/ and renamed menu.lst to something else then copied over my merged version and named it to menu.lst .

@ autocrosser  sorry about the longwinded explanation , I'm sure you know how ,but others will read this too .

---

### Post by jerrylamos on 2009-06-13
> **Slug71 said:**
> Try this in Terminal

```
sudo os-prober

sudo update-grub
```

reboot.

On Alpha2:

sudo os-prober

Results in a screenfull of:

mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
.....

sudo update-grub

found only Alpha 2, not any of the other three jaunty & karmics.

Jerry

---

### Post by Slug71 on 2009-06-13
> **jerrylamos said:**
> On Alpha2:

sudo os-prober

Results in a screenfull of:

mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
.....

sudo update-grub

found only Alpha 2, not any of the other three jaunty & karmics.

Jerry

In that case try:

```
sudo apt-get install --reinstall libdebian-installer4

sudo os-prober

sudo update-grub
```


Reboot.

---

### Post by autocrosser on 2009-06-13
No prob---The more information we put out there, the more people with correctly working systems!!!!!!

Sounds like you've got it pat---I just make sure I have a backup of my current file just in case.......

---

### Post by autocrosser on 2009-06-13
> **taavikko said:**
> Good stuff guys.

So it seems only to affect multi-boot enviroments.
My "one system/one machine" method of usage isn't affected.

Yes--OS-Prober needs some serious "luv"--as soon as it can read/use UUID's, the problem will go away (I hope).....

---

### Post by super.rad on 2009-06-13
Well after reinstalling libdebian-installer4 os-prober now works for me but it only found my suse install and not fedora

---

### Post by autocrosser on 2009-06-13
> **super.rad said:**
> Well after reinstalling libdebian-installer4 os-prober now works for me but it only found my suse install and not fedora

Looks like a job for "manual edit" & then a bug report---Take a look at ronacc's & my reports---add to the bug of your choice ;)

---

### Post by super.rad on 2009-06-13
Only thing I'm unsure about manually adding fedora is /boot and / are on 2 different partitions (/dev/sda1 and /dev/sda2) so what do I add?
Had a look at both bug reports but neither seem the same problem, both are a problem with grub setting the wrong UUID or partition, once I got os-prober to work it found suse and that worked fine, just didnt find fedora at all. Should I start a new bug or just add a comment to one of the other reports?


EDIT: Nevermind I didn't think of looking at fedora's menu.lst, now added to grub2
I'd still prefer to be able to chainload both systems grub's from grub2, otherwise I'm guessing I have to run os-prober from ubuntu everytime one of them gets a new kernel

---

### Post by ronacc on 2009-06-13
actualy you could add the boot stanza for fedora to either /boot/grub/menu.lst or /boot/grub/grub.cfg  , added to menu.lst it will appear in the first menu that comes up , added to grub.cfg it will show up after the chainloader starts .just copy your fedora boot stanza from your bu menu.lst .

---

### Post by super.rad on 2009-06-13
First menu that comes up? I'm pretty sure mine goes straight to grub2 as I have no menu.lst and grub-legacy isn't installed

---

### Post by jerrylamos on 2009-06-13
From please help test Grub2:

sudo apt-get install --reinstall libdebian-installer4
sudo os-prober
sudo update-grub

which worked for me on one of my test systems Thinkpad T40.  It's got 4 images, various jaunty & karmic & karmic A1 & now A2.

Now to try on another test system a Compaq tower.

Hmmmm.   Jerry

---

### Post by ronacc on 2009-06-13
@ super.rad , ok you must have installed A2 , so add it to grub.cfg if what jerrylamos  said doesn't work .

---

### Post by super.rad on 2009-06-13
Already done what jerrylamos said and it found suse but not fedora but I've now added that manually. Yeah i reinstalled alpha2 as I'd messed up a few things

---

### Post by jerrylamos on 2009-06-14
> **Slug71 said:**
> In that case try:

```
sudo apt-get install --reinstall libdebian-installer4

sudo os-prober

sudo update-grub
```


Reboot.

Worked on my Thinkpad.  On my compaq I had to re-install os-prober which I did with synaptic.  I presume
sudo apt-get install --reinstall os-prober
would have worked as well.

On the "installer4" I don't understand why that didn't go out as an update?

Jerry

---

### Post by TwiStEr55 on 2009-06-14
after install of the Alpha 2 my Windows partition wasnt there either.

And even after a Kernel Update there still was only the old kernel in the boot loader. 

I found that there is a command: **grub2-update**


that did the trick, it updated the bootloader for the new kernel and included windows xp

hope that helps.

---

### Post by Slug71 on 2009-06-14
> **jerrylamos said:**
> Worked on my Thinkpad.  On my compaq I had to re-install os-prober which I did with synaptic.  I presume
sudo apt-get install --reinstall os-prober
would have worked as well.

On the "installer4" I don't understand why that didn't go out as an update?

Jerry

Nice.

Yep, sudo apt-get install --reinstall os-prober, would have worked.

Im positive there must be a bug with those installer4 errors or perhaps the devs forgot something with the integration of Grub2/os-prober.

---

### Post by ranch hand on 2009-06-14
I had to reinstall 9.10A2 due to playing with Fedora on the same HDD.  If I don't install it first it always screws something up.

But, to the point, I have tried for 2 days to get grub to work and it would not on this box.  Tried all of the above and several others too.

Today, install, update, reboot and do not have the new kernal to boot to.  So I run the above on the old kernal and, low and behold, not only got 2.6.30-9 but also 8.04 and 9.04.

Now if I could just set the timeout on the boot menu I would be in hog heaven.

---

### Post by ranch hand on 2009-06-14
OK, I have set the external up the way it was before I buggered it.  I installed another 9.04 version after 9.10A2.  This, of coarse, means I am now booting from it.

Booted back into 9.10 and ran the prober and updated.  Found all OSs including the new one.  Happy happy.

Now, how in flinderation do I make 9.10 back into the OS I am booting from?

I hope someone has an idea.

I have A1-32 (A2 is 64) on another HDD and it is where I boot from on that one.  I thiink I will try updating it to A2 an see what happens then.  That HDD has 6 other OSs on it including Mandriva2001-1-Gnome.

---

### Post by ronacc on 2009-06-14
did you let the 9.04 you installed after 9.10a2 install it's own grub ? or are you still booting with grub2 ?

---

### Post by freeman2000 on 2009-06-14
> **ranch hand said:**
>   Now if I could.... I would be in hog heaven.  

SE Montana - isn't that already hog heaven?  Or would that be the Dakotas?

---

### Post by ranch hand on 2009-06-14
ronacc
Yes I let 9.04 install grub.  I am trying to recreate the HDD as it was before I screwed it and see what happens to A2.  This is how any other OS is treated on this box.

I am real happy that Grub2 seems to be coming along faster than I thought it would.  I just wish we new what files to edit for what and how to make a particular partition the one being booted from.

One thing that I depend on is having all partitions loaded with grub when being installed so that if I have problem I can use any on that HDD (I keep each HDD/Enclosure booting separately).

At one time I had a drive that I had 5Gb swap at the end and just before it, at the end another 5gb partition that I had 8.04 on and could just reinstall if needed (paranoid safety net).  This could be done for grub2 but it seems silly.  JUst need a way to activate it.

I am sure it is there or coming.

freeman2000
Montana is pretty nice and the population dencity (population densilation) is nice too.  I like living somewhere where cattle (even sheep) out number people.

The more you pack people together the more de-humanized they become.  Here, in the county seat, we have a population of about 500.  If you need your cell phone to work ALL the time you would not like gettig to far out of town.  The ranch where I worked until the boss died will probably get cell service sometime around 2050.

---

### Post by RAOF on 2009-06-14
> **ranch hand said:**
> ...

Now, how in flinderation do I make 9.10 back into the OS I am booting from?
...

You might mean "how do I install Karmic's grub2 to be the bootloader in the MBR", in which case it would be something like
```

sudo grub-install /dev/*sdwhatever*

```

---

### Post by ronacc on 2009-06-15
you should be able to install it from synaptic also , both RAOF's method and the synaptic way assume you are booted into 9.10 . I'm pretty sure the file you need to edit to change the timeout and what boots by default is /boot/grub/grub.cfg  , I havent tried changing those I just edited the messed up uuid's , I'm still on an updated jaunty>karmic , I'll try to get around to installing A2 tomorrow . I've got a dedicated test box and put each install on its own drive to limit potential disasters .the settings for timeout and default boot are right at the top , remember grub starts counting at 0 .

---

### Post by psyke83 on 2009-06-15
Just a quick note for people who dual-boot (this thread seems the most appropriate place) and are trying to perform a fresh installation via the alpha 2 desktop CD:

Alpha 2 has a bug in the Ubiquity installer where GRUB2 installation fails if you try to install on a system which has another OS installed (such as Windows). The alpha 2 release notes lists a [workaround]("http://www.ubuntu.com/testing/karmic/alpha2#Known%20issues") but it did not work for me.

I posted a [different workaround]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/385995/comments/11") on the bug report that does work, however, and it will save users who want to install alpha 2 but don't want to waste bandwidth on a daily image (or wait for alpha 3).

---

### Post by MacUntu on 2009-06-15
Hm... os-prober detects my Windows XP two times:

foo@bar:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sda2:Microsoft Windows XP Professional:Windows1:chain

I have parts of Windows on /dev/sda2 (pagefile.sys, user data) but never installed Windows there. Anyone else experienced that?

---

### Post by ranch hand on 2009-06-15
psyke83
I installed A2 as the 4th OS on the drive.  Yes I got a message at the end of installation that ubiquity had failed unexpectedly.  The installation process ended there.

I rebooted and everything was fine as far as A2 was concerned.

Suse LiveCDs always freeze when I try to exit them (acoup[le more that I can't remember do too) and I have to unplug to get that to work.  I thought that was going to be what was going to be the deal here but it was not that bad.

---

### Post by super.rad on 2009-06-15
Thought I'd finally found a way to chainload my other OS's.
Found this on the debian forums
Create a file called **/etc/grub.d/35-fedora** which contains:
```
#!/bin/sh
cat << EOF
menuentry "Fedora" {
  set root=(hd0,7)
  chainloader +1
}
EOF
```
Then make it executable and run **update-grub**

Tried that and I now have a "Fedora" option on grub2 but if i select it I get "Invalid Signature". Anyone know what this means or how to fix it?
I have 2 other OS (Fedora 11 & Fedora Rawhide) and it does the same for both

---

### Post by ranch hand on 2009-06-15
RAOF
Finaly had a chance to mess with this and it did not work;
```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda7
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

```
I also tried this using the old "hdo" combo with and without () just to check.

It is a bugger but it is a learning experience.

---

### Post by ranch hand on 2009-06-15
> **ronacc said:**
> you should be able to install it from synaptic also , both RAOF's method and the synaptic way assume you are booted into 9.10 . I'm pretty sure the file you need to edit to change the timeout and what boots by default is /boot/grub/grub.cfg  , I havent tried changing those I just edited the messed up uuid's , I'm still on an updated jaunty>karmic , I'll try to get around to installing A2 tomorrow . I've got a dedicated test box and put each install on its own drive to limit potential disasters .the settings for timeout and default boot are right at the top , remember grub starts counting at 0 .

I have tried editing that file and I am glad that is done.  I was happy to see that it said "set root=(hd0,8)" which is the Jaunty / partition.  Changing that from 8 to 7 did not (big surprise) effect anything.

Are you saying that I need to reinstall grub2?  It has all the partitions in /boot/grub/grub.cfg that are on this HDD right now.  Reinstalling grub2 does not seem, to me, to make sence.  Reinstalling 9.10 / would change where I am booting from but this seems awfully drastic.

I really want to learn how to run this version of grub.  I admit to using SUM on grub OSs but i never did until I learned to work grub without it.  I need to learn that in grub2.

---

### Post by ranch hand on 2009-06-15
Been playing some more.  Unfortunately to no good result.  On the other hand, no bad result either.
```

ker@ker-desktop:~$ grub-setup --help
Usage: grub-setup [OPTION]... DEVICE

Set up images to boot from DEVICE.
DEVICE must be a GRUB device (e.g. ``(hd0,1)'').

  -b, --boot-image=FILE   use FILE as the boot image [default=boot.img]
  -c, --core-image=FILE   use FILE as the core image [default=core.img]
  -d, --directory=DIR     use GRUB files in the directory DIR [default=/boot/grub]
  -m, --device-map=FILE   use FILE as the device map [default=/boot/grub/device.map]
  -r, --root-device=DEV   use DEV as the root device [default=guessed]
  -f, --force             install even if problems are detected
  -h, --help              display this message and exit
  -V, --version           print version information and exit
  -v, --verbose           print verbose messages

Report bugs to <bug-grub@gnu.org>.
ker@ker-desktop:~$ sudo su
root@ker-desktop:/home/ker# grub-setup --root-device=(hd0,7)
bash: syntax error near unexpected token `('
root@ker-desktop:/home/ker# grub-setup --root-device=hd0,7
No device is specified.
Try ``grub-setup --help'' for more information.

```
I will admit to being stumped, for  now.

---

### Post by ranch hand on 2009-06-15
Tried that again;
```

root@ker-desktop:/home/ker# grub-setup -r --root-device=hd0,7
No device is specified.
Try ``grub-setup --help'' for more information.
root@ker-desktop:/home/ker# grub-setup -r --root-device=(hd0,7)
bash: syntax error near unexpected token `('
root@ker-desktop:/home/ker# 

```

---

### Post by psyke83 on 2009-06-15
> **ranch hand said:**
> Tried that again;
```

root@ker-desktop:/home/ker# grub-setup -r --root-device=hd0,7
No device is specified.
Try ``grub-setup --help'' for more information.
root@ker-desktop:/home/ker# grub-setup -r --root-device=(hd0,7)
bash: syntax error near unexpected token `('
root@ker-desktop:/home/ker# 

```

You may need to encapsulate the brackets like this:
```
$ grub-setup -r --root-device=\(hd0,7)\
```

---

### Post by ronacc on 2009-06-16
installed A2 from smd64 livecd , ubiquity failed right at the finish , rebooted livecd applied psyke83,s workaround from page 6 this thread , reinstalled A2 and all went well , clean boot to karmic and all other installs were found .

---

### Post by theozzlives on 2009-06-16
Alpha 2 has GRUB2, no matter how many times I try I can't get it to Dual Boot. I have it on an old 500 MHz machine that has XP on it for fax and such. I can't find a menu.lst to set it up manually. please advise.

P.S. I almost forgot... XP is on sda, and Ubuntu is on sdb.

---

### Post by froggyswamp on 2009-06-16
The release notes for Alpha 2 state something like: support for dual boot in GRUB 2 will be available/fixed in Alpha 3. So I'd suggest waiting a bit, the developers are aware and working at it, no need to run ahead of the train.

---

### Post by 23meg on 2009-06-16
[http://ubuntuforums.org/showthread.php?t=1186045](http://ubuntuforums.org/showthread.php?t=1186045)

---

### Post by theozzlives on 2009-06-16
> **froggyswamp said:**
> The release notes for Alpha 2 state something like: support for dual boot in GRUB 2 will be available/fixed in Alpha 3. So I'd suggest waiting a bit, the developers are aware and working at it, no need to run ahead of the train.

I've already got Alpha 2 running in a VirtualBox without issue. I want to test it on a low end computer in a Dual Boot environment. Are you saying I should restore XPs MBR and wait for Alpha 3??? How do I use the old GRUB for now?

---

### Post by 23meg on 2009-06-16
Threads merged.

---

### Post by regala on 2009-06-16
> **psyke83 said:**
> You may need to encapsulate the brackets like this:
```
$ grub-setup -r --root-device=\(hd0,7)\
```

not enclose them, escape them:
```

grub-setup -r --root-device=\(hd0,7\)

```
(notice the \ always before the character to escape)

---

### Post by ronacc on 2009-06-16
re my post #67 above , my other installs were found but wouldn't boot , looking at grub.cfg I foud that the boot stanza for karmic looked like this .
```
menuentry "Ubuntu, linux 2.6.30-9-generic" {
	set root=(hd4,1)
	search --fs-uuid --set c86b5172-051c-43e3-916c-3799afaba6ef
	linux	/boot/vmlinuz-2.6.30-9-generic root=UUID=c86b5172-051c-43e3-916c-3799afaba6ef ro  quiet splash
	initrd	/boot/initrd.img-2.6.30-9-generic

```

and the boot stanzas for the other installs looked like this ,using my jaunty install as an example .

```
menuentry "Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (on /dev/sdc1)" {
	set root=(hd2,1)
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=1f603d8b-0fe4-4846-92f9-54b572ff1924 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic

```

note that the "search" line is missing , edited to add the line (with the proper uuid) so it looks like this .

```
menuentry "Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (on /dev/sdc1)" {
	set root=(hd2,1)
	search --fs-uuid --set 1f603d8b-0fe4-4846-92f9-54b572ff1924
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=1f603d8b-0fe4-4846-92f9-54b572ff1924 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic

```

the edited version allows my jaunty install to boot . going to add a similar edit to my other installs boot stanzas .

---

### Post by ranch hand on 2009-06-16
> **regala said:**
> not enclose them, escape them:
```

grub-setup -r --root-device=\(hd0,7\)

```
(notice the \ always before the character to escape)

No, this one returns a syntax error.

---

### Post by ranch hand on 2009-06-16
> **psyke83 said:**
> You may need to encapsulate the brackets like this:
```
$ grub-setup -r --root-device=\(hd0,7)\
```
All I am geting with this is;
```

root@ker-desktop:/home/ker# grub-setup -r --root-device=\(hd0,7)\
> 

```
I guess we just need to wait for A3.

My A1-32 install is up to date except no grub2.  The partition that it is on is booted from  it.  I may install grub2 there and see what happens.

---

### Post by Gourgi on 2009-06-16
maybe
```
grub-setup -r --root-device=\(hd0,7\)
```

---

### Post by ranch hand on 2009-06-16
> **Gourgi said:**
> maybe
```
grub-setup -r --root-device=\(hd0,7\)
```
I tried that one but got the sysntax error for ")"

---

### Post by plun on 2009-06-19
> **MacUntu said:**
> Hm... os-prober detects my Windows XP two times:

foo@bar:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sda2:Microsoft Windows XP Professional:Windows1:chain

I have parts of Windows on /dev/sda2 (pagefile.sys, user data) but never installed Windows there. Anyone else experienced that?


Yep confirmed.

I took the time and upgraded to Grub2 on my Laptop and also got Windows 7 installed.

Windows 7 creates a small partition for boot recovery files, 100MB "System reserved".

gparted picture:
[[img]http://www.ubuntu-pics.de/thumb/16727/snapshot2_eK4zWt.png[/img]](http://www.ubuntu-pics.de/bild/16727/snapshot2_eK4zWt.png)


os-prober output:
```
plun@plun-laptop:~/$ sudo os-prober
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Windows Vista (loader):Windows1:chain
```


I can confirm if you file a bug....:D

---

### Post by MacUntu on 2009-06-19
Yes, I will. Just want to take a look at os-prober's code first. :)

**Edit:** Hm, I'm not so sure anymore that it's not my fault os-prober detects two Windows installations. For XP os-prober checks for the files ntldr and ntdetect.com in the root directory of the partition and I have them in both partitions. I first have to confirm it's normal that those files get doubled when putting user data and pagefile.sys on another partition (woohoo, virtualbox is my friend!).

---

### Post by plun on 2009-06-19
Its clearly a bug and it might be difficult to find anything else to probe....  or maybe a logic which not checks partitions smaller then XXX MB ?

I have no plans buying W7 but this must be solved because there are so many "Dual-booters", Windows<>Ubuntu

---

### Post by MacUntu on 2009-06-19
> **plun said:**
> Its clearly a bug

Your problem - yes! But I'm not sure about mine (currently installing XP - what a pain!)...

Is this a Win 7 Beta or RC installation? I had this small additional partition with Win 7 Beta but not with Win 7 RC. On my test machine I have Ubunut and Win 7 RC and os-prober only detects one "Windows Vista (loader)".

---

### Post by Balaviswanathan on 2009-06-19
Hi all,

Does anyone know how to dual boot Ubuntu 9.04 with Windows and Sun solaris 10

Thanks and regards

V.Balaviswanathan

---

### Post by plun on 2009-06-19
> **MacUntu said:**
> Your problem - yes! But I'm not sure about mine (currently installing XP - what a pain!)...

Is this a Win 7 Beta or RC installation? I had this small additional partition with Win 7 Beta but not with Win 7 RC. On my test machine I have Ubunut and Win 7 RC and os-prober only detects one "Windows Vista (loader)".

Its a clean W7 RC install, I don't know why this System Reserved partition is created.

A few search results

[http://www.wilderssecurity.com/showthread.php?t=242923](http://www.wilderssecurity.com/showthread.php?t=242923)

[http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/](http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/)

---

### Post by MacUntu on 2009-06-19
> **plun said:**
> Its a clean W7 RC install, I don't know why this System Reserved partition is created.

A few search results

[http://www.wilderssecurity.com/showthread.php?t=242923](http://www.wilderssecurity.com/showthread.php?t=242923)

[http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/](http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/)

Hm, why I don't have it? Maybe I already deleted it. Or it's because I installed Win 7 RC after Ubuntu (beginning of the disk already in use). Well... seems after installing XP I'll install RC to confirm. Too much Windows for one day tbh. :lolflag:

---

### Post by plun on 2009-06-19
> **MacUntu said:**
>  Too much Windows for one day tbh. :lolflag:

Well.... don't get lost....):P

Everything just works with W7.....  ;)  and no scruples....

---

### Post by MacUntu on 2009-06-19
Seems I can confirm neither of the problems.

Installing XP and moving user data and pagefile didn't create those system files on the target partition. os-prober only shows the XP partition.

Installing Win 7 RC produced the 100MB partition but only this partition contains the system files picked up by os-prober. os-prober only shows the 100MB partition.

Do you have files called "bootmgr" and "Boot/BCD" on your real Win 7 RC partition (root directory)?

---

### Post by plun on 2009-06-19
> **MacUntu said:**
> Seems I can confirm neither of the problems.

Installing XP and moving user data and pagefile didn't create those system files on the target partition. os-prober only shows the XP partition.

Installing Win 7 RC produced the 100MB partition but only this partition contains the system files picked up by os-prober. os-prober only shows the 100MB partition.

Do you have files called "bootmgr" and "Boot/BCD" on your real Win 7 RC partition (root directory)?


OK.... crap...):P

My "root" partition:
[[img]http://www.ubuntu-pics.de/thumb/16735/snapshot4_gvc22y.png[/img]](http://www.ubuntu-pics.de/bild/16735/snapshot4_gvc22y.png)

System reserved partition:
[[img]http://www.ubuntu-pics.de/thumb/16736/snapshot5_tv4Pp5.png[/img]](http://www.ubuntu-pics.de/bild/16736/snapshot5_tv4Pp5.png)

It seems to boot from both partitions....):P

---

### Post by MacUntu on 2009-06-19
So your situation is similar to mine with XP: Boots from both partitions but I've no idea why there are boot files on both partitions. :D

Well, we need a third input. :P

---

### Post by plun on 2009-06-19
> **MacUntu said:**
> So your situation is similar to mine with XP: Boots from both partitions but I've no idea why there are boot files on both partitions. :D

Well, we need a third input. :P


Yup, I believe we have enough for filing a bug.....:D

---

### Post by ranch hand on 2009-06-24
I have just updated my A1-32 partition and it is still using "old" grub on 2.6.30.10.  I did get, along with the kernal upgrade, a grub-common version2.  Also some update to grub .97.

This, I'm thinking, leading up to the release of A3 (July 23) when Grub2 is supposed to support multi-boot.

I was planning to put A3 on this partition but I think I will keep both A1-32 and A2-64 going and just put A3 on a new partition just to see when they come together.

---

### Post by MacUntu on 2009-06-24
> **ranch hand said:**
> when Grub2 is supposed to support multi-boot

GRUB2 supports multi-boot, it's just the setup that not working flawlessly.

---

### Post by budluva04 on 2009-06-25
[https://wiki.ubuntu.com/Grub2#Dual-booting]("https://wiki.ubuntu.com/Grub2#Dual-booting") anyone tried this????
```

$ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub
```

---

### Post by ranch hand on 2009-06-26
> 
 Originally Posted by Slug71  View Post
In that case try:

sudo apt-get install --reinstall libdebian-installer4

sudo os-prober

sudo update-grub


Reboot.

I have been trying to do this to along with

sudo grub-install /dev/sda8

since my last post.  This has not worked to restore boot to that partition as grub root.

That installation of 9.10A2 worked fine until I installed another 9.04.  All OS' are on 2 partitions, /root on sda and /home on sdb.  This is how it has to be so that I can use my dual external enclosure.  I do not us RAID because I do not like it. 

Both update-grub and grub install had the same problem - they could not find a "device for /".  I tried this logged into sda8 and with a live CD.

I have grub2 working but my solution is not elegant.  I installed A2 on another partition (15Gb) on sda.  Updated to current and did the three steps from Slug71, edited /boot/grub/grub.conf so that I have a time out of 100 seconds and the thing works fine.

I will install A3 on the next partition (larger) and see if I can get it changed to sda8 at that time.  If not I will try to get it changed to this partition - sda10.

If the latter works it will indicate that the problem is that sda8 is /root for an OS whose /home is sdb7.  I do not know if that is the problem or, if so, why as grub .97 has no problem with that at all.

Grub 2 may just work out.  Right now it takes about 3 times as long to boot compared to legacy grub but it is early days.

My A1 installation on another HDD (I boot from it) has not had an update to Grub2 yet.  Did get a grub-common version2 which is supposed to have files common to both grubs and anupdate of grub .97.

This new 9.10 that I just installed will be updated but not used for anything but playing with Grub2.

Anyway, I thought all you helpful folks deserved an update on my playing.

Thanks a bunch.  Any other thoughts or idea will be very welcome to me, maybe not to this poor OS.

---

