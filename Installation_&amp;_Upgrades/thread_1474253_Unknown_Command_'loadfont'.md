---
title: "Unknown Command 'loadfont'"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by xavierc on 2010-05-05
I did some updates for 10.04 last night and when I went to boot up this morning it came up with:

error: unkown command 'loadfont'
error: file not found

Any ideas? Please note: I'm no Linux whiz! Just a "normal" user so treat me like I'm an idiot, thanks!

---

### Post by roninio on 2010-05-06
got the same error on XUBUNTU

i have dual boot and when i select the xubuntu the error appears, and computer restarts :(

---

### Post by xavierc on 2010-05-06
> **roninio said:**
> got the same error on XUBUNTU

i have dual boot and when i select the xubuntu the error appears, and computer restarts :(

Yeah I also have a dual boot (for the first time I'm glad I have Windows installed as well). Mine doesn't even roboot, just sits there and I have to turn the power off then on. I'm hoping someone can help us out 'cause I feel so dirty being in Windows for any other reason than to play Football manager!

---

### Post by hibrahimkhail on 2010-05-06
Got exactly the same error on my HP laptop with windows Vista after I ran the updater which updated to ubunto 10.04.  Now I cannot even boot ubunto, but can boot windows fine.  Sorry I missed this post and posted mine under a seperate thread.

---

### Post by xavierc on 2010-05-06
*bump* Anyone?

---

### Post by roninio on 2010-05-06
hello

I have run the boot info script and it is attached to this post. 

I hope this brings some light. how to fix this. I think it is something to do with the WUBI and grub 

thanks

---

### Post by roninio on 2010-05-06
any one !!! :(

---

### Post by xavierc on 2010-05-06
*bump* Again. Anyone?

---

### Post by xavierc on 2010-05-06
Okay. I don't know about the other two that had this problem, but it seems to be fine now. I got up this morning and Ubuntu booted perfectly. Would still like to know what was going on; why it didn't work and now does; and if it will happen again.

---

### Post by alco75 on 2010-05-07
I've got the same problem.

When I first booted into Wubi 10.04 this morning, I did an update via the Update Manager, which it said a restart was required. After restarting, I get:

[B]error: unknown command 'loadfont'
error: file not found
[/B] 
and the system reboots immediately.

I cannot get in Ubuntu, so I'm stuck in XP without my LAMP development environment.

Is anyone able to help? If I can't get back into Ubuntu, I'll lose at least a couple of days of setup & config and all my Tomboy notes.

---

### Post by binhtam on 2010-05-09
pls, can someone help?

---

### Post by alco75 on 2010-05-09
Well, I recovered my Tomboy notes from the Live CD by mounting the root.disk file.

However, I decided just to go with a proper dual boot solution as I'm already sick of flakey Wubi.

This means I'll have to setup LAMP, Eclipse, Subclipse, XDebug, Tomcat (with SSL), CAS and all my other packages and settings all over again. :mad:

---

### Post by ldumont on 2010-05-10
Same problem here, nobody has a fix?

---

### Post by antonius uno on 2010-05-11
same here on a Dell 1558 wiht dual boot with windows 7. Can't get into Ubuntu so am glad I still got the dual boot option.
The error: unknown command 'loadfont' flashes very briefly on the screen and the laptop reboots immediately. Took me 4 times rebooting before I could read the entire error message.

Would also appreciate some help here.

---

### Post by lubom on 2010-05-12
I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
sudo mkdir /win
sudo mount /dev/sda2 /win

Then mount virtual disk
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 

Then I edit grub.cfg
sudo nano /vdisk/boot/grub/grub.cfg

and comment this lines

#if loadfont /usr/share/grub/unicode.pf2 ; then
#  set gfxmode=640x480
#  insmod gfxterm
#  insmod vbe
#  if terminal_output gfxterm ; then true ; else
#    # For backward compatibility with versions of terminal.mod that don't
#    # understand terminal_output
#    terminal gfxterm
#  fi
#fi

save changes and reboot

In my case, this resolve my problem with booting. I'm waiting for better solution. I hope that helped somebody.

---

### Post by antonius uno on 2010-05-13
thanks lubom. Have tried the same thing and can boot again indeed. First thing I am going to try is to convert wubi to a normal installation.
Fastest way is to make a USB start up disk when doing your suggestion.

---

### Post by FuturePusher on 2010-06-06
Hey all... hopefully You have some kind of forum notification of new post set since it's been 3 weeks since the last post.


I'm on Jaunty (Ubuntu 9.04) and have been messing around with stuffing in "grub-pc"/GRUB2 in it (on Jaunty, the older "grub-legacy" is the default).

I initially put in GRUB2 from an install-CD with Ubuntu 10.04 LTS... didn't go that smooth (the newer GRUB handles either the boot-sector, or the entire MBR, differently... so I got an unbootable system. My "skillz" came to use though, so I got it fixed :) ).

Anyway, what I noticed from that whole ordeal, was that Ubuntu 10.04 uses a more Debian style GRUB2, while the GRUB2 in the repositories for older Ubuntu distributions (like my 9.04, and maybe 9.10 as well) seems more "customized" by the developers for Ubuntu.


SO... to make this unecessarily long story into a productive tip for You guys to test:

Try editing the template-scripts which produce the final "grub.cfg" ("/etc/grub.d/00_header" is probably the primary one here...), so that all "critical"/relevant occurences of the "loadfont" instruction (Debian style) **are replaced with** a "font" instruction simply (this seems to be "Ubuntu style" after analysing the template-scripts)...


Please let the whole thread know it this results in fonts being loaded or not! :)

---

### Post by Alex Ber on 2010-07-01
Same error on HP laptop using wubi after last update. 
I will try fix from FuturePusher.

---

### Post by JasonSilver on 2010-07-02
> I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
sudo mkdir /win
sudo mount /dev/sda2 /win

Then mount virtual disk
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 

Then I edit grub.cfg
sudo nano /vdisk/boot/grub/grub.cfg

and comment this lines

#if loadfont /usr/share/grub/unicode.pf2 ; then
# set gfxmode=640x480
# insmod gfxterm
# insmod vbe
# if terminal_output gfxterm ; then true ; else
# # For backward compatibility with versions of terminal.mod that don't
# # understand terminal_output
# terminal gfxterm
# fi
#fi

save changes and reboot

What can one do it there's no way to boot from a live CD? I can get into Windows Vista, but cannot get into Ubuntu.

Jason

---

### Post by JasonSilver on 2010-07-02
Please, can anyone help me? I'm on Ubuntu withdrawal.

Jason

---

### Post by JasonSilver on 2010-07-02
> **JasonSilver said:**
> What can one do it there's no way to boot from a live CD? I can get into Windows Vista, but cannot get into Ubuntu.

Jason

Update: I downloaded Ubuntu, put it on a 2gig flash drive, (no CDROM here) and booted in.

I then followed the above directions to mount the virtual drive, root.disk from within the "live cd"

I edited the grub.cfg file, commenting out the offending lines, saved, and rebooted.

I'm still not able to get in... now the message is simple:

error: file not found

What else can I try?

Jason

---

### Post by alvaroguillen on 2010-07-02
Help!

I have the same error message. same symptoms,

i tried the fix, booted from live CD, opened terminal, but when i type the first command "sudo mkdir/win"  it says command not found? or no such command?


is a fix in the works for this?

why is this happenig? how do i fix it?

DELL laptop, Latitude D810, windows XP installed UBUNTU under WUBI, I use UBUNTU as my main system.

-

---

### Post by Dale61 on 2010-07-03
Surprise, surprise, another trashed Ubuntu install.

I also get the 
'error: unknown command 'loadfont'
error: file not found'

message on an otherwise blank screen.  I wait and wait and wait in the hope something might just happen, but I eventually have to turn the laptop off at the power, then restart and boot in Windows in an effort to find a fix.  That's how I'm able to post now.

In all honesty, I'm over it.  Had a gutful.  I'll next reboot from the LiveCD and try to recover what I can, then give some serious thought about retaining 10.04.  Fortunately, I have the CD of 9.10 and can't remember ever having a problem with that, so IF I come back to Ubuntu, 9.10 will be where I come back to.

---

### Post by JasonSilver on 2010-07-03
> **alvaroguillen said:**
> Help!

I have the same error message. same symptoms,

i tried the fix, booted from live CD, opened terminal, but when i type the first command "sudo mkdir/win"  it says command not found? or no such command?


is a fix in the works for this?

why is this happenig? how do i fix it?

DELL laptop, Latitude D810, windows XP installed UBUNTU under WUBI, I use UBUNTU as my main system.

-
You forgot the space before /win

---

### Post by JasonSilver on 2010-07-03
The way I was able to restore was to backup my root.disk in C:/ubuntu/disks/

First I went in through Windows, then I zipped that file (root.disk), then I copied it to an 8 gig SD card.

Then I downloaded Ubuntu again, put it on a USB drive using the tools at Ubuntu.com to make a bootable USB.

Then I booted into the USB drive, (you have to go into your BIOS and set it up to boot from the USB -- make sure the USB is in when you do this).

I installed Ubuntu fresh, and let it use the whole drive this time (good bye Windows, and other partitions).

Once the installation was done, I mounted the backup in the SD card.

1. Unzipped the root-disk.zip to the desktop.
2. Mounted the root.disk from a terminal window like this:
```

sudo mkdir /wubiDisk
sudo mount -o loop /home/USERNAME/Desktop/root.disk /wubiDisk

```
3. I then went into the /wubiDisk folder to view this mounted disk
4. I navigated to my home folder, and turned on hidden file view (control-H)
5. I then selected and copied all of the folders and files which I wanted to keep 
6. I then navigated to my new home folder (/home/USERNAME) and pasted the wubi contents here
7. I then rebooted the PC
8. Now many of my settings are back, but not all of my installed software. I reinstalled the Gimp, Google Chrome, Skype, etc.

That's it! Have fun, and good luck.

Jason

---

### Post by alvaroguillen on 2010-07-06
yeah,

got same "file not found" then the computer hangs, with no way out except push the power button.


i saved the root disk from the WUBI folder in windows, going to try and recover my files.

what an annoying problem, lost a lot of data, had to re-install wubi and ubuntu with 10.point whatever..

maybe ubuntu is trying to get me to pay for "ubuntu one" so i can auto-back up my install,,and not worry about screw-ups like that one...



-

---

### Post by Dale61 on 2010-07-06
I solved my problem quite easily and simply - I just deleted Ubuntu from laptop.

As it was a WUBI install inside Windows, I have had nothing but problems.  I would finally get it set up and working like a charm, and then, without warning, something else would go wrong.

My desktop install doesn't have these problems, but that is a different set-up on it's own partition, not inside Windows.

I doubt I'll re-install Ubuntu on the laptop again at this point in time, not until I actually own it, then I can wipe the existing Windows partition and do a clean install, as it should be.

---

### Post by oulipian on 2010-07-08
Yep, same error for me. I have a dual boot HP laptop, both Ubuntu and Windows have worked fine til now, then bam, one day after a security upgrade Ubuntu refuses to boot with that "Unknown command: 'loadfont'" message.

It's really frustrating because I really want to like Ubuntu.

Can anyone help, please?

---

### Post by JasonSilver on 2010-07-09
> **oulipian said:**
> Yep, same error for me. I have a dual boot HP laptop, both Ubuntu and Windows have worked fine til now, then bam, one day after a security upgrade Ubuntu refuses to boot with that "Unknown command: 'loadfont'" message.

It's really frustrating because I really want to like Ubuntu.

Can anyone help, please?
Let me say, as one who has made the transition over the last three years - it is SO worth it. Drop Windows and move to Ubuntu... forget WUBI, it's STUPID. Either put Ubuntu on its own partition, or wipe Windows.

---

### Post by matt! on 2010-07-26
> **lubom said:**
> I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
sudo mkdir /win
sudo mount /dev/sda2 /win

Then mount virtual disk
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 

Then I edit grub.cfg
sudo nano /vdisk/boot/grub/grub.cfg

and comment this lines

#if loadfont /usr/share/grub/unicode.pf2 ; then
#  set gfxmode=640x480
#  insmod gfxterm
#  insmod vbe
#  if terminal_output gfxterm ; then true ; else
#    # For backward compatibility with versions of terminal.mod that don't
#    # understand terminal_output
#    terminal gfxterm
#  fi
#fi

save changes and reboot

In my case, this resolve my problem with booting. I'm waiting for better solution. I hope that helped somebody.
This worked for me - using /dev/sda1. Thank you!

The state of official ubuntu support and quality control - especially regarding wubi installations - really leaves a lot to be desired. Every update leads to a new problem, at least for me.

matt

---

### Post by Dale61 on 2010-07-27
Yeah matt, I know how you feel, but for me, it's every 2nd update that I'm faced with hours of searching forums on how to fix the latest problem.

I didn't have the problem on my desktop as that is a stand-alone install, but the laptop is a totally different plate of kippers.  I've decided that whilst the laptop is still under warranty, it will remain totally Vista (which I still hate with a passion), then once I own the laptop outright, I'll reformat and do a fresh install of whatever flavour is the latest at the time (2012).

---

### Post by bluefrogprince on 2010-07-28
> **lubom said:**
> I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
sudo mkdir /win
sudo mount /dev/sda2 /win

Then mount virtual disk
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 

Then I edit grub.cfg
sudo nano /vdisk/boot/grub/grub.cfg



I tried this and like [alco75]("http://ubuntuforums.org/member.php?u=1048749") also ended up with a "file not found" message - but I've found a fix. Instead of editing grub.cfg as above, move it out of the way:

sudo mv /vdisk/boot/grub/grub.cfg /vdisk/boot/grub/grub.cfg.broken

Now when you restart you should get dropped to a grub prompt, at which point you can boot manually. At the prompt do:

linux /boot/vmlinuz-<Your version of the kernel...use TAB to find it> root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  
initrd /boot/initrd.img-<Your version of the kernel)>
boot

Once you're up and running you should be able to reinstall grub-pc via synaptic, or check [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for further options

Hope that helps someone!

---

### Post by firou on 2010-09-12
See this post: [http://ubuntuforums.org/showpost.php...19&postcount=8](http://ubuntuforums.org/showpost.php...19&postcount=8)
May be helpful to you.

---

### Post by Dale61 on 2010-09-12
Thx firou, but your link takes me back to the index page.

---

### Post by mandazi on 2010-09-30
I just installed some updates for my 64-bit ubuntu 10.04 and now I'm also getting this same error.  I installed Ubunut via windows installer.  I have dual boot with windows 7.

I'm still a newb, so I really have no idea how to fix this.

---

### Post by Ltlevim on 2010-10-06
> **bluefrogprince said:**
> I tried this and like [alco75]("http://ubuntuforums.org/member.php?u=1048749") also ended up with a "file not found" message - but I've found a fix. Instead of editing grub.cfg as above, move it out of the way:

sudo mv /vdisk/boot/grub/grub.cfg /vdisk/boot/grub/grub.cfg.broken

Now when you restart you should get dropped to a grub prompt, at which point you can boot manually. At the prompt do:

linux /boot/vmlinuz-<Your version of the kernel...use TAB to find it> root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  
initrd /boot/initrd.img-<Your version of the kernel)>
boot

Once you're up and running you should be able to reinstall grub-pc via synaptic, or check [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for further options

Hope that helps someone!
Do this. Another problem is that when I reinstall grub, I have to start over in fixing this problem. Anyone know what's up?
Until there's a fix, I've been entering these:
linux /boot/vmlinuz-<Your version of the kernel...use TAB to find it> root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  
initrd /boot/initrd.img-<Your version of the kernel)>
boot
on every startup. It sucks.

---

### Post by jobsworth on 2010-11-24
> **xavierc said:**
> Yeah I also have a dual boot (for the first time I'm glad I have Windows installed as well). Mine doesn't even roboot, just sits there and I have to turn the power off then on. I'm hoping someone can help us out 'cause I feel so dirty being in Windows for any other reason than to play Football manager!

Much as I love Ubuntu I too am glad that I have Windows as well.
Most of these problems, and there are many of them, seem to be concerned with WUBI (the UBUNTU Windows bootloader).
The intention is that the user should stop using Windows altogether and consequently stop using WUBI.
If the user does this the problems will probably go away
but it is hard to explain to a student that discontinuing Windows
will solve the problem and that Ubuntu is so wonderful, which it is, when Ubuntu will not boot.
My solution is to keep a backup copy of the file root.disk
and then to restore it whenever there is a WUBI problem,
which is frequently. Also I keep /home/ on a separate disk home.disk so that little is lost on a restore.
I am doing a restore right now (using Windows) then I will wait a bit for any new updates until some kind person fixes the problem.
I know that there are some excellent programmers out there who donate their time free of charge and for this I thank them.
Can nobody see that most of the world is using Microsoft Windows
and that WUBI is an important advertisement for the advantages of UBUNTU, the better operating system?
Until there is a change in thinking WUBI will always be given a low priority.
After all everything works just fine in a dedicated UBUNTU system or in a  Virtualbox doesn't it?

---

### Post by Dale61 on 2010-11-24
I did fix the problem ....... by installing 10.04 on a reformatted and clean HDD.  This removed the WUBI problem, and the reboot hanging.

Fortunately, I don't need Windows and can live without it.

I have since upgraded to 10.10, and as the downloads are free with my ISP, I did it as an online upgrade.

---

### Post by WhatAbout on 2010-11-27
> **lubom said:**
> I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
sudo mkdir /win
sudo mount /dev/sda2 /win

Then mount virtual disk
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 

Then I edit grub.cfg
sudo nano /vdisk/boot/grub/grub.cfg

and comment this lines

#if loadfont /usr/share/grub/unicode.pf2 ; then
#  set gfxmode=640x480
#  insmod gfxterm
#  insmod vbe
#  if terminal_output gfxterm ; then true ; else
#    # For backward compatibility with versions of terminal.mod that don't
#    # understand terminal_output
#    terminal gfxterm
#  fi
#fi

save changes and reboot

In my case, this resolve my problem with booting. I'm waiting for better solution. I hope that helped somebody.

Instead of commenting out the ifs, do change the red lines ive posted below to [COLOR=SeaGreen]loopback loop0 /host/ubuntu/disks/root.disk[/COLOR]     And then reboot. 

```
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
```

---

### Post by windozh8ter on 2010-11-27
The loopback edits from WhatAbout worked for me. Thanks for the help!!

---

### Post by john_rogers on 2010-11-28
Thank you WhatAbout!  Your solution worked for me as well.

---

### Post by BLTicklemonster on 2010-11-29
> Originally Posted by lubom View Post
I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
sudo mkdir /win
sudo mount /dev/sda2 /win

Then mount virtual disk
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Then I edit grub.cfg
sudo nano /vdisk/boot/grub/grub.cfg

and comment this lines

#if loadfont /usr/share/grub/unicode.pf2 ; then
# set gfxmode=640x480
# insmod gfxterm
# insmod vbe
# if terminal_output gfxterm ; then true ; else
# # For backward compatibility with versions of terminal.mod that don't
# # understand terminal_output
# terminal gfxterm
# fi
#fi

save changes and reboot

In my case, this resolve my problem with booting. I'm waiting for better solution. I hope that helped somebody.

I just finished an upgrade and restarted, and voila, here I am looking up an answer for how to get OUR BUSINESS COMPUTER working.

I'd say the culprit is sloppiness on the part of canonical in regards to updates, rushing them out without giving any thought to whether they'd leave anyone stranded. 

My advice: if you're dual booting, DO NOT let anyone talk you into booting just ubuntu if you aren't savvy in the ways of searching the internet for ways to bring a brain dead device back to life. If not for dual booting, I doubt many of you would be here finding answers.

I'm going to try the fix posted above this evening when I get home from work and have time to sit down and get on it. Thank you for the post. I was afraid it was a grub issue, and I'd have to redo grub once again. Whew!

---

### Post by windozh8ter on 2010-11-29
> **windozh8ter said:**
> The loopback edits from WhatAbout worked for me. Thanks for the help!!

UPDATE: I had to repeat this process when I upgraded from 10.04 to 10.10. Solution still worked. Thanks, again!

---

### Post by BLTicklemonster on 2010-11-29
Whew. So I had to open System>Administration>System Monitor and look at /dev/sda2 and instead of sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk I put sudo mount -o loop /media/2450dz568842/ubuntu/disks/root.disk /vdisk otherwise I could not mount vdisk. ( /dev/sda2 was already mounted I guess, heck, I don't know)

Anyway, from there I was able to bring up the grub file and edit it.

BUT I haven't rebooted yet. I just wanted to post this here so I could have a place to come back to to see where I left off if this doesn't work.

And I really hope it does, because I have photographs on ubuntu that I have got to get access to, or my goose is cooked.

Crossing fingers and rebooting...

---

### Post by BLTicklemonster on 2010-11-29
Muahaha. Thank you WhatAbout.

---

### Post by BLTicklemonster on 2010-11-30
And what do we see this morning? Another update. Does this one fix things that could have been wrong in the last one? 

Well, yesterday was too close. I cannot lose access to my data on our work computer. I have turned updates totally off. If this leaves me vulnerable, I guess it's the price I pay for not paying a price, eh?

For the record, I've been left stranded by Ubuntu more times since I began using it than anyone here or at work has been stranded by Windows. Not a good tale. Not a good tale at all.

---

### Post by WhatAbout on 2010-11-30
> **BLTicklemonster said:**
> And what do we see this morning? Another update. Does this one fix things that could have been wrong in the last one? 

Well, yesterday was too close. I cannot lose access to my data on our work computer. I have turned updates totally off. If this leaves me vulnerable, I guess it's the price I pay for not paying a price, eh?

For the record, I've been left stranded by Ubuntu more times since I began using it than anyone here or at work has been stranded by Windows. Not a good tale. Not a good tale at all.

It seams that on the new updates one needs to change the grub.cfg before rebooting for not getting into the same problem. I guess its going to be this way for a time to come on every update. So i recommend that people just sit tight and update, but before rebooting check the grub.cfg.

My guess is that its actually a grub bug. If one dose *sudo update-grub *the grub.cfg will be generated wrongly. (for certain WUBI installations) And hence on every update this command is properly and possibly run, and therefore a need to edit for us who are on WUBI.

---

### Post by jlapier on 2010-12-02
Many Thanks WhatAbout! Fixing the loopback lines worked for me too.

---

### Post by roothsmz on 2010-12-03
I get this same error. I have another install of Ubuntu on my system that did not have the updates and it will load fine. not sure what the problem is with the updates but that's the problem.

---

### Post by bcbc on 2010-12-03
Here's *drs305*'s summary of the issue and the suggested permanent manual fix:
[http://ubuntuforums.org/showpost.php?p=10183394&postcount=87](http://ubuntuforums.org/showpost.php?p=10183394&postcount=87)

---

### Post by Stanich on 2010-12-27
> **WhatAbout said:**
> Instead of commenting out the ifs, do change the red lines ive posted below to [COLOR=SeaGreen]loopback loop0 /host/ubuntu/disks/root.disk[/COLOR]     And then reboot. 

```
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
```

I do all as you say, but than a problem appears. Changes doesn't appear to be saved. Do you know, how to save changes in grub.cfg? Sorry for asking such dump question, but I am newbie.

EDIT: Or should I simply reboot without saving changes? :S

---

### Post by Rubi1200 on 2010-12-27
Hi Stanich and welcome to the forums :)

There is now a Wubi Megathread which provides information about Wubi installs, issues, and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I suggest you read through it and see if there is anything there that can help. Look particularly at how to prevent problems occurring in the first place.

If not, post back here and we can take it from there.

Thanks.

---

### Post by WhatAbout on 2010-12-28
Stanich, what you need to do is:

 					*Originally Posted by **lubom** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9287550#post9287550")* 				
  				[I]I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
 sudo mkdir /win
 sudo mount /dev/sda2 /win
  
 Then mount virtual disk
 sudo mkdir /vdisk
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 
  
 Then I edit grub.cfg
 sudo gedit /vdisk/boot/grub/grub.cfg[/I]  

I think its cause you dont open the .cfg as root. Use sudu for that. You  should save and reboot. Be sure to save the changes as you will need to  use the live CD again. And thats just pain. 

But Rubi1200 

Ive seen the post linked and ive seen bcbc solution, but i dont feel compelled  to use it. Hes using a sledgehammer to crack a nut. As the functions in  the .cfg are handy so really no need to delete them.
The "permanent" solution removes all the grub files so the command *sudo update-grub*  stops working, no updates are made and so on. There is a really good  point behind updates, and disabling this is not a solution.

If one finds it too hard to check and update the few lines in the .cfg  after big updates then make a script that dose it after every update. At  least till a real solution is made possible.

---

### Post by bcbc on 2010-12-28
> **WhatAbout said:**
> 
Ive seen the post linked and ive seen bcbc solution, but i dont feel compelled  to use it. Hes using a sledgehammer to crack a nut. As the functions in  the .cfg are handy so really no need to delete them.
The "permanent" solution removes all the grub files so the command *sudo update-grub*  stops working, no updates are made and so on. There is a really good  point behind updates, and disabling this is not a solution.

If one finds it too hard to check and update the few lines in the .cfg  after big updates then make a script that dose it after every update. At  least till a real solution is made possible.

I'd like to point out some inaccuracies in what you've said. My solution actually restores /boot/grub to it's initial state - what you have on a fresh wubi install. 

Update-grub is not prevented from working - on the contrary it is enabled - as it means that grub.cfg continues to be automatically updated, but instead of breaking your boot each time, it works as intended.

So - and this is the whole point - you don't have to edit grub.cfg each time you update a kernel.

And of course you - and other wubi users - are free to keep manually editing your grub.cfg files each time. No one is forcing you to use it.

PS here is the analysis that resulted in that permanent fix: [https://bugs.launchpad.net/wubi/+bug/653134](https://bugs.launchpad.net/wubi/+bug/653134) (the relevant bits are from post 53 on). It's written more for the developers, but basically I did this:
1. Fresh wubi install
2. Reinstalled the same version of grub-pc to simulate a grub package update (but without the variability of any actual code changes)
3. Noted changes
4. Reverse changes
By the way that 'sledgehammer' edit is just to get wubi booting so you can do the fix. grub.cfg is identical to that of a fresh install once you run sudo update-grub again.

PPS Stanich, change the grub.cfg from read only before editing with gedit, or use nano or vi instead.

---

### Post by Stanich on 2010-12-29
> **WhatAbout said:**
> Stanich, what you need to do is:

                     *Originally Posted by **lubom**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9287550#post9287550")*                 
                  [I]I use wubi, for quick fix, I boot from live CD and then mount windows partition sda2:
 sudo mkdir /win
 sudo mount /dev/sda2 /win
  
 Then mount virtual disk
 sudo mkdir /vdisk
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 
  
 Then I edit grub.cfg
 sudo gedit /vdisk/boot/grub/grub.cfg[/I]  

I think its cause you dont open the .cfg as root. Use sudu for that. You  should save and reboot. Be sure to save the changes as you will need to  use the live CD again. And thats just pain. 

But Rubi1200 

Ive seen the post linked and ive seen bcbc solution, but i dont feel compelled  to use it. Hes using a sledgehammer to crack a nut. As the functions in  the .cfg are handy so really no need to delete them.
The "permanent" solution removes all the grub files so the command *sudo update-grub*  stops working, no updates are made and so on. There is a really good  point behind updates, and disabling this is not a solution.

If one finds it too hard to check and update the few lines in the .cfg  after big updates then make a script that dose it after every update. At  least till a real solution is made possible.

The problem is not with opening grub.cfg, the problem is with saving changes. When I press ctrl+s it refuses to save it.

EDIT nevermind. Now it succeeded in saving. Thanks. Will reboot now. Hope it will work.

EDIT2: It worked after rebooting. But as I later turned it off, and today morning back on, it was same problem again. :(

---

### Post by Neva on 2011-07-16
My permanent manual solution:

Since the problem is caused by incorrect grub commands in the header part, I'll just move it to a lower priority since I don't really need any of the header functionality to boot wubi.
```
cd /etc/grub.d
sudo mv 00_header 50_header
sudo update-grub
```This way, the booting will work even after new kernel (and grub) updates

---

