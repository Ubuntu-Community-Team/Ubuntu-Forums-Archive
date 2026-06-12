---
title: "Grub=rubbish"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by LiLoather on 2007-04-30
I have tried installing to two machines in the last two days.

On a second hdd on my desktop I installed Debian Etch 4.0.  I was offered no choice between Grub and LiLo, it installed Grub which picked up XP on the first hard drive and would offer a boot into either - so long as it was a warm boot.  On a cold boot XP had disappeared and had to be recovered using the recovery console in the XP disk, which overwrote Grub.  Not just once, every cold boot until I gave up bothering to reinstall Grub.

I installed Ubuntu Server 7.0 on a laptop.  Grub, of course.  No choice offered.  Boot sequence?  Bios > Grub > reboot > Grub > Reboot > Grub > Reboot > Grub> Reboot > Grub etc etc.  Use esc. to get into Grub, select OS > reboot.

I've wasted hours on this junk.

---

### Post by antoz on 2007-04-30
can't really help myself but the link might solve your problems
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by rillip on 2007-04-30
1.  What have you done to fix it?  Googled it? Searched the forum?  Nothing?  You have to try to help yourself before anyone else will be interested in helping.  Posting grub suxxorz with no indication of what you've done doesn't get everybody jumping to help.

Here's another link you may find useful.  It's not Ubuntu specific, but does provide instructions for how to edit the grub menu list to show XP,

There's also a link from there on how to configure Window's boot loader.  It's linked from the bellow article.  The link is actually messed up, it'll prepend the base URL, so just click the link, then remove the duplicate section at the begining.

[http://www.devhood.com/tutorials/tutorial_details.aspx?tutorial_id=405](http://www.devhood.com/tutorials/tutorial_details.aspx?tutorial_id=405)

2. I'm sure if you look, you can find a way to instal Lilo instead, if you perfer it.  If you would like to make a sugestion that it be used instead of Grub, this is not the correct forum for that, you should go to the development area and look for the thread asking for recommendations.

3.  I would demand a full refund from Grub's developers.

---

### Post by bulldog on 2007-04-30
> **LiLoather said:**
> I have tried installing to two machines in the last two days.

On a second hdd on my desktop I installed Debian Etch 4.0.  I was offered no choice between Grub and LiLo, it installed Grub which picked up XP on the first hard drive and would offer a boot into either - so long as it was a warm boot.  On a cold boot XP had disappeared and had to be recovered using the recovery console in the XP disk, which overwrote Grub.  Not just once, every cold boot until I gave up bothering to reinstall Grub.

I installed Ubuntu Server 7.0 on a laptop.  Grub, of course.  No choice offered.  Boot sequence?  Bios > Grub > reboot > Grub > Reboot > Grub > Reboot > Grub> Reboot > Grub etc etc.  Use esc. to get into Grub, select OS > reboot.

I've wasted hours on this junk.

Well I'm sorry to hear of the malfunction of GRUB,your hardware is top,that's out of the question of course.
And you yourself have all the knowledge to configure GRUB as it should be,that's out of the question too,I suppose.

So all is to blame at GRUB,it's a shame they develop a piece of software which is working so well on so many computers.

---

### Post by Chrisj303 on 2007-04-30
GRUB can be so frustrating - as we speak, i'm desperatley trying to find out how to completley remove it from my feisty install. I need to use lilo, but it won't work while grub still here.

Can anyone help? I've apparantly completley removed it via synaptic - but it still kicks in on boot.
In my /boot file there is still a grub folder, and it won't let me trash it.

I've tried logging in as root - but i'm getting the message "system administrator cannot access through this login screen".

If anyone could tell me how to get rid of it i would be VERY pleased!

P.s I'm running feisty as part of a triple boot setup on a macbook.- I've done this before, but last time the grub failed during install, so i didn't have to worry about removing it.

---

### Post by bulldog on 2007-04-30
You can only remove it from the MBR by installing another OS,uninstalling it with synaptic won't do.
If you have a windows install cd you can use the recovery console to fix your MBR in windows style.
Commands:fixmbr  and  fixboot
GRUB isn't frustrating,you only have to know it works and how you should use it.

You can try the [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) to see if you can boot the OS of your choice.

More info, [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Chrisj303 on 2007-04-30
SORTED! = system>administration>login window>security>Allow Local system admin at login

Once i had that checked, i could login as root, and destroy the remaining grub folder!

Honestly though, i HATE grub - it's just butt ugly. Lilo allows me to boot either windows or ubuntu straight from the rEFIt bootscreen, with no second layer bios-like menu to navigate. Much more elegant!


303

---

### Post by psusi on 2007-04-30
I can't make sense out of most of what you have said.  If windows is on grub's menu, then it is on the menu - grub doesn't care if the machine is warm or cold booted.  If you want to install lilo, then you have to install lilo, i.e. by running sudo lilo.  Grub is far more flexible than lilo though, and doesn't require a reinstall every time you want to modify the boot menu or options.  

Also what did you expect windows' fixmbr command to do?  How do you figure it is a fault in grub that you asked windows to remove it and it did?

---

### Post by bulldog on 2007-04-30
> **Chrisj303 said:**
> SORTED! = system>administration>login window>security>Allow Local system admin at login

Once i had that checked, i could login as root, and destroy the remaining grub folder!

Honestly though, i HATE grub - it's just butt ugly. Lilo allows me to boot either windows or ubuntu straight from the rEFIt bootscreen, with no second layer bios-like menu to navigate. Much more elegant!


303

Well you could  be right,everybody is in title to use what he want :) 
Good luck with your  Lilo then.

---

### Post by LiLoather on 2007-04-30
> **psusi said:**
> I can't make sense out of most of what you have said.  If windows is on grub's menu, then it is on the menu - grub doesn't care if the machine is warm or cold booted.  If you want to install lilo, then you have to install lilo, i.e. by running sudo lilo.  Grub is far more flexible than lilo though, and doesn't require a reinstall every time you want to modify the boot menu or options.  

Also what did you expect windows' fixmbr command to do?  How do you figure it is a fault in grub that you asked windows to remove it and it did?

OK.  First, I apologise for the tone of my initial post - But I had been struggling with the installation of TWO different dists (Debian Etch & Ubuntu Server) on two different CD's on TWO different machines for a full day solid (and I have better things to  do)  and been beaten by the same problem each time, leaving me with two machines that won't boot at all.  Sorry, but I don't have the patience of a Mother Teresa.

To answer the above - I pre-read three different sets of on-line installations before starting and followed the on-screen instructions of the installer with anal attention to detail, and it failed.  Twice.

What's the problem?  I have absolutely no idea.  On the desktop (a Celeron)  with Etch Grub worked perfectly well for dual booting if I did a restart, but from a cold boot I was fired back to BIOS boot as soon as BIOS tried to initialise the loader.  The machine didn't hang, which it would if there was no MBR at all, but whatever was there just triggered a reboot.

With the laptop (an AMD-K6) the same thing happened, except that there I had given Ubuntu the entirety of the one and only disk and let the installer do the partitioning.  BOIS calls Grub, if Grub tries to start the OS the machine re-boots: if I 'esc' into the menu whatever I select from there (including the rescue) triggers a re-boot.

My POINT is that I am using the bog-standard installation disks on pretty-much bog-standard machines.  I HAVE read the installation instructions, I DO have a better than vague idea what I'm doing and it STILL seems that I'm using a third-rate, amateur, run-it-and-hope assembly.  I WANT to have two working OS's on two machines so I can spend my time finding out how to use them for running and controlling a network - and  that's going to be hard enough - I DON'T want, or expect, to have to spend hours if not days finding out how to get the bl**dy OS to boot in the first place!  But that's what it seems I'm going to have to do - which doesn't give me much confidence in what I'm going to find when I've climbed this mountain!!!

---

### Post by Chrisj303 on 2007-04-30
> **psusi said:**
> I can't make sense out of most of what you have said.  If windows is on grub's menu, then it is on the menu - grub doesn't care if the machine is warm or cold booted.  If you want to install lilo, then you have to install lilo, i.e. by running sudo lilo.  Grub is far more flexible than lilo though, and doesn't require a reinstall every time you want to modify the boot menu or options.  

Also what did you expect windows' fixmbr command to do?  How do you figure it is a fault in grub that you asked windows to remove it and it did?

I'm triplebooting OSX/UBUNTU/XP on a Macbook - grub dosen't play nice with my keyboard. And the boot process with LILO, when used in combo with rEFIt, is much faster, efficient and better looking.

LILO dosen't even have to know about my XP partition.

My problem WAS that i couldn't get rid of GRUB completley (in order to install LILO) - it turned out that i hadn't allowed root access at the login screen.

LILO dosen't require reinstall when you make changes to the menu/config file - just 'sudo lilo' after youve done what you need to do!

---

### Post by bulldog on 2007-04-30
> **LiLoather said:**
> OK.  First, I apologise for the tone of my initial post - But I had been struggling with the installation of TWO different dists (Debian Etch & Ubuntu Server) on two different CD's on TWO different machines for a full day solid (and I have better things to  do)  and been beaten by the same problem each time, leaving me with two machines that won't boot at all.  Sorry, but I don't have the patience of a Mother Teresa.

To answer the above - I pre-read three different sets of on-line installations before starting and followed the on-screen instructions of the installer with anal attention to detail, and it failed.  Twice.

What's the problem?  I have absolutely no idea.  On the desktop (a Celeron)  with Etch Grub worked perfectly well for dual booting if I did a restart, but from a cold boot I was fired back to BIOS boot as soon as BIOS tried to initialise the loader.  The machine didn't hang, which it would if there was no MBR at all, but whatever was there just triggered a reboot.

With the laptop (an AMD-K6) the same thing happened, except that there I had given Ubuntu the entirety of the one and only disk and let the installer do the partitioning.  BOIS calls Grub, if Grub tries to start the OS the machine re-boots: if I 'esc' into the menu whatever I select from there (including the rescue) triggers a re-boot.

My POINT is that I am using the bog-standard installation disks on pretty-much bog-standard machines.  I HAVE read the installation instructions, I DO have a better than vague idea what I'm doing and it STILL seems that I'm using a third-rate, amateur, run-it-and-hope assembly.  I WANT to have two working OS's on two machines so I can spend my time finding out how to use them for running and controlling a network - and  that's going to be hard enough - I DON'T want, or expect, to have to spend hours if not days finding out how to get the bl**dy OS to boot in the first place!  But that's what it seems I'm going to have to do - which doesn't give me much confidence in what I'm going to find when I've climbed this mountain!!!

Did you actual see the GRUB menu?
Because I know a little about GRUB and what it's supposed to do.
If GRUB fails you have actual seen the menu,you did choose a boot option,and then you get any error.
That is what GRUB does.
If your MBR is empty,no grub installed,you should get the message 'no OS installed' or something similar.
You can reinstall grub with the live cd very easy and quick.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Just keep in mind,if you use more than one hdd,you should specify in the setup command the right disk where to install grub in the mbr.
You have to boot from this hdd,but I think you know that.

In case of one hdd use the (hd0) setup.

After the install```
sudo update-grub
``` in your terminal to save any change to menu.lst.

---

### Post by rillip on 2007-04-30
I'm confused by the process you're describing.

Let me see if I have this straight.

1. You boot up cold.  Bios runs POST.  You see the grub menu.  You do not see your Windows option.  You pick something, and then the screen goes black and puts you back to the BIOS start, because the mchine rebooted.

2,  If, during this process, you manually do a reboot (warm boot), you see the Windows choice.  However, chosing it or any other option causes the screen to black out and then go back to the bios dfue to a reboot.

I'm not sure what you mean by "Escape into the menu."

If this is accurate, please confirm.  If it is not accurate, please explain, in excrutiating detail, the exact process you're having when you do and do not see the options.

---

### Post by LiLoather on 2007-04-30
> **rillip said:**
> I'm confused by the process you're describing.

Let me see if I have this straight.

1. You boot up cold.  Bios runs POST.  You see the grub menu.  You do not see your Windows option.  You pick something, and then the screen goes black and puts you back to the BIOS start, because the mchine rebooted.

2,  If, during this process, you manually do a reboot (warm boot), you see the Windows choice.  However, chosing it or any other option causes the screen to black out and then go back to the bios dfue to a reboot.

I'm not sure what you mean by "Escape into the menu."

If this is accurate, please confirm.  If it is not accurate, please explain, in excrutiating detail, the exact process you're having when you do and do not see the options.

I am talking about two machines with the same problem:

ONE is a desktop - an Intel Celeron 733Mhz on a 6VXC7-4X-P motherboard with a VIA Apollo Pro 133A chipset, 512MB RAM.  One drive (primary master) is 80GB devoted to Windows XP Pro (SP2).  I added a second, 10GB, drive as secondary slave with a CD-ROM as master and installed Debian ETCH 4.0 (I386) to it.  A straight install, following instructions to the best of my ability.  Seemed to complete OK.  Followed instructions to remove CD, machine did a warm reboot, Grub (ugly, ugly, ugly) came up offering me Debian or XP, would boot into either no problem on restart.  Powered system down.  Restarted later,  POST, BIOS as usual, flash of what I think is the Grub loading message but it's too quick to read then machine re-boots.  Use XP recovery to reinstall MBR - boots into XP OK.  Use Debian disk as rescue to re-install Grub - as before.  Works OK on re-start but after power-down - zilch.  Re-installed Windows MBR so I can actually use machine.

TWO is an old Compaq Presario 1200 laptop I want to use as a network server.  CPU=AMD-K6, 190MB RAM, VIA-TECH VT 8501 Chipset, 5GB hdd.  Downloaded with Jigdo the current Ubuntu-7.04- server-i386.iso.  Burned to disk, MD5 OK.  Ran installation, give it whole disk, selected 'yes' and 'no' as seemed appropriate.  Installation finished with congratulations, removed disk, hit finish, machine re-booted to boot-loader, re-booted to boot-loader, rebooted to boot-loader etc.    From cold boot I get a "grub loading to 1.5' or something similar message, then if I don't hit 'esc' it flashes a message about a 'stage 2', then a 'starting up' but almost instantly goes into a re-boot, with the POST, BIOS etc.  If I hit 'escape' I get a menu offering me Ubuntu, kernel 2.6.20-15-server, ditto with (recovery mode) and Ubuntu, memtest86+.  Memtest reveals no problems.

Hitting 'e' (edit select command for ordinary boot) from the Grub menu offers me the following script:

root (hd0,0)
kernel  /boot/vmlinuz-2.6.20-15-server root=UUID=fa8a79e9-5c3b-4093-b>
initrd   /boot/initrd.img-2.6.20-15-server
quiet
savedefault

hitting 'b' for boot from this menu gets me the 'starting-up' message and then bang, straight into a reboot.

I can't describe exactly what the desktop does - that would mean reinstalling Grub from rescue which means going all through half the installation process again, and then having to reinstall Windows MBR to get back into XP again and I've already spent an hour on this when I have plenty of other things I should be doing.

---

### Post by LiLoather on 2007-04-30
> **bulldog said:**
> Did you actual see the GRUB menu?
Because I know a little about GRUB and what it's supposed to do.
If GRUB fails you have actual seen the menu,you did choose a boot option,and then you get any error.
That is what GRUB does.
If your MBR is empty,no grub installed,you should get the message 'no OS installed' or something similar.
You can reinstall grub with the live cd very easy and quick.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Just keep in mind,if you use more than one hdd,you should specify in the setup command the right disk where to install grub in the mbr.
You have to boot from this hdd,but I think you know that.

In case of one hdd use the (hd0) setup.

After the install```
sudo update-grub
``` in your terminal to save any change to menu.lst.

Thanks Bulldog - can do that on the desktop machine as far as finding where Grub stage 1 is (hd1.1) but I also need it to be able to boot XP.  Maybe I'll be able to find time later today to do all the searching and reading I need to be able to do what the installer couldn't get right first time, but for the moment I've a living to earn.

---

### Post by psusi on 2007-04-30
> **Chrisj303 said:**
> 
LILO dosen't require reinstall when you make changes to the menu/config file - just 'sudo lilo' after youve done what you need to do!

That IS reinstalling lilo.  When you modify your config or kernel, you must run lilo to read the new config and build a new boot sector and block map and write it out to the disk.  Grub is smart enough to go read the filesystem on the disk to locate menu.lst, read it, process it, and then find and read the kernel image all at boot time.

Practically speaking this means you can boot up and have grub load another kernel it otherwise has no idea about, possibly on a disk that wasn't there last boot.  With lilo you have to tell it about the new kernel by editing lilo.conf, then reinstall, then reboot.  You can also do other things like defrag or resize the partition and grub doesn't care, but lilo needs reinstalled.

---

### Post by LiLoather on 2007-04-30
More Linux headbanging....

As I had Kubuntu 6.10 'Edgy Eft' running on the desktop machine in order to follow Bulldog's advice I took the opportunity to hit the 'install to your hard-drive' option offered on the desktop - followed the 6-step installation process and the machine re-booted to Grub which offered XP as an option.  I booted into Kubuntu, no problems, except that I couldn't access root.  Setting up 'root' with a password wasn't offered at any time in the 6-step installation, just an ordinary user, and nothing I tried to access 'root' with worked.  Just a point of interest.

Anyway doing a reboot from kubuntu took be back into Grub, I selected XP and it loaded no problems.  Did a restart from XP and - bang, no Grub again. Just BIOS > reboot > BIOS > reboot.  Not even the Grub stage 1.5 message.

So is something in Windows interfering with Grub, possibly, though it's not restoring its own MBR if it is.  And it's EXACTLY the same as is happening with the laptop which hasn't had anything later than Windows 98 on it, and doesn't have anything of Windows on it now.

---

### Post by psusi on 2007-04-30
That's because you aren't supposed to log in as root.  Use sudo to run commands as root if needed, and if you don't want to have to keep retyping it when issuing several commands that need root access, just do sudo -s first.  

As for the grub problem, are you running some kind of antivirus in windows?  Sounds like you either have a virus or an antivirus program hosing up grub.

---

### Post by rillip on 2007-04-30
Could it be a bios virus scanner?  I can easily see rewriting the MBR as a potential for it to think it is a virus

---

### Post by psusi on 2007-04-30
No because it only gets messed up when windows boots.

---

### Post by LiLoather on 2007-04-30
> **psusi said:**
> No because it only gets messed up when windows boots.

Not true.  It might appear to be XP messing it up on the desktop but the laptop doesn't have a hint of Windows on it.

I'll check the anti-virus point on the desktop - only to do that I've now got to make the time to fire up the XP rescue console in order to restore the MBR in order to get into XP again!

Boot protection in the desktop's BIOS is disabled.  I can't find anything along those lines in the laptop's BIOS, but anyway the laptop has accepted, booted and run quit happily the SME server (CentOS) and FreeBSD at different times.

---

### Post by LiLoather on 2007-04-30
> **bulldog said:**
> Did you actual see the GRUB menu?
Because I know a little about GRUB and what it's supposed to do.
If GRUB fails you have actual seen the menu,you did choose a boot option,and then you get any error.
That is what GRUB does.
If your MBR is empty,no grub installed,you should get the message 'no OS installed' or something similar.
You can reinstall grub with the live cd very easy and quick.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Just keep in mind,if you use more than one hdd,you should specify in the setup command the right disk where to install grub in the mbr.
You have to boot from this hdd,but I think you know that.

In case of one hdd use the (hd0) setup.

After the install```
sudo update-grub
``` in your terminal to save any change to menu.lst.

OK Bulldog, did this with the live kubuntu 'edgy eft' running on the laptop.  Everything seemed to work - got at one point a screed of text about finding Grub stage 1=yes, Grub stage?=yes. Grub stage 5=yes(5) -can't remember exactly but it looked promising - followed your instructions, now have the following;-

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives.  This might take a long time.
ubuntu@ubuntu:~$ sudo update-grub    #I think the bit about finding Grub stages was before this?
Searching for Grub installation directory...
No Grub directory found.
  To create a template run 'mkdir /boot/grub' first
  To install grub, install it manually or try the 'grub-install' command.
  ### warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$

Horse flogged some more but remains stubbornly dead.

---

### Post by LiLoather on 2007-04-30
Still flogging dead horse.

Retried Bulldog's suggestion.  'grub> setup (hd0)" produced the following text:-

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Runnning "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done

ubuntu@ubuntu:~$sudo update grub produced the "no grub directory' found response.  But a "find /boot/grub/stage1" command returns (hd0,0).

And then we're back on the merry-go-round of grub 'starting up' and then straight back into a reboot.

---

### Post by LiLoather on 2007-04-30
> **LiLoather said:**
> 

Boot protection in the desktop's BIOS is disabled.  I can't find anything along those lines in the laptop's BIOS, but anyway the laptop has accepted, booted and run quit happily the SME server (CentOS) and FreeBSD at different times.

OK, in the laptop's BIOS "Write protection of fixed disk boot sector" is off and always has been.

---

### Post by LiLoather on 2007-05-01
OK, so I took the second hd off the desktop.  After restoring Windows MBR for the fourth time just so I could boot into XP I just couldn't trust any form of Linux on the machine - Windows is where I do my REAL work and if Ubuntu or anything else screwed up XP I'd be screwed too.

So I decided to try Ubuntu server on yet another machine - an old VA-503+ motherboard with an AMD-K6.-2/500 and 64MB RAM.  Spent half-an-hour fitting it up with a CD-ROM, booted it and told Ubuntu server to install.  It got as far as:-

[   35.468002]  EIP: [<c01311f5>] do_sigaction+0xf5/0x1c0 SS:ESP 0068:c2e4df6e
[   35.468127]

and has stopped.  Motionless.  The horse has finally expired.  Dead.  Useless except to feed the dogs with.

I'm sorry.  I really am.  What I occasionally see of Debian I like.  It has the potential to be really useful but it still can't be allowed to play with the big boys.  I've spent two days on this - including most of an entire working day - and got nowhere.  A complete and utter waste of time.  

I would really have liked to have had Ubuntu server on the laptop to administer a small network and Kubuntu on a desktop here running Webmin to remotely administer the server with.  Would have like that, but it ain't gonna be.  FreeBSD 6.2 sans X has happily installed itself on the old VA-503+ and I know it will work on the laptop because it already has.  Ubuntu would have been snazzier and I don't yet know if I can install and run Webmin on FreeBSD, but clearly FreeBSD has one clear advantage over Debian/Ubuntu.

It bl**dy works.

I've got to get on with some real work now but I'll pop back now and then to see if any of you care enough or are interested in getting to the bottom of these problems - I won't put FreeBSD on the laptop just yet, I haven't time - as, well, you know, maybe I can help Ubuntu take another small step into actually, one day, eventually, turning into something useful.

---

### Post by Chrisj303 on 2007-05-01
I would like it if ubuntu were to include both GRUB and LILO, and let you choose which one to use at install.

A lot of people seem to have real problems getting both bootloaders to work, i fond it difficult when i first tried ubuntu, as i was so used to the GUI of Mac OSX and XP. And it's important to remember that for many people setting up grub will be the first time they have ever approached a config file.

Maybe it would also be a good idea if Grub and LILO had a GUI frontend, to allow for easy use for those not familiar with them.

To the OP - I think it's a shame to give up on ubuntu as a result of Grub. Have you considered trying LILO?


cheers,
303

---

### Post by LiLoather on 2007-05-01
> **Chrisj303 said:**
> 

To the OP - I think it's a shame to give up on ubuntu as a result of Grub. Have you considered trying LILO?

cheers,
303

Well I am more familiar with LiLo as it was the loader I had to wrestle with back when I tried Corel Linux and dual-booted it with Windows98 SE.  Oh, and the Red Hat distro that came with the 'Linux for Dummies' book.  Oh, and of course Caldera, and not forgetting SuZE, and the two disc set of Debian 3.0 that cost me $45 back in September '02.

I thought the SME server with CentOS might be what I wanted and it installed and ran on the laptop a treat, but it wasn't really what I needed.  Now I've a disk of Debian Etch 4.0 that won't install and run, ditto Ubuntu server 7.0, a Kubuntu 6.10 live CD that will run live but not install and run, and FreeBSD which installs and runs on anything I point it at but is, well, rather dour - real hair-shirt stuff even for Unix-clones.

What's depressing is that my 1999 Corel Linux is actually better at installing itself than 2007 Ubuntu!

---

### Post by mozetti on 2007-05-01
Just out of curiosity, and you sound knowledgabe enough for this not to be the case, but are you installing GRUB to the same HDD that the BIOS's on both machines set to boot from (1st Primary/Secondary or 2nd Primary/Secondary)?

I just haven't heard of anyone have this much trouble with GRUB.

---

### Post by LiLoather on 2007-05-01
> **mozetti said:**
> Just out of curiosity, and you sound knowledgabe enough for this not to be the case, but are you installing GRUB to the same HDD that the BIOS's on both machines set to boot from (1st Primary/Secondary or 2nd Primary/Secondary)?

I just haven't heard of anyone have this much trouble with GRUB.

I'M not installing Grub at all - the installer is and I assume it knows where to put it.  It certainly doesn't ask me where it should go and I wouldn't know what to tell it if it did.

However in the case of the laptop there is only one HDD, and in the case of the desktop it was set to boot from the HDD it always did, which it knew as C. (C,CD-ROM, A)

Oh, and I've found other references to the same problem on other forums.  One guy reckons he fixed it because his BIOS was set to LBA but I tried changing that to 'Other' in both my BIOSs and re-installed, but it made no difference.  Same for another guy in the same thread, and he reckoned he couldn't get LiLo to work either.

So what do you do?

---

### Post by psusi on 2007-05-01
This conversation has bounced around too much to be useful.  Let's try to focus on one problem shall we?  The installer assumes that you are installing to the primary boot disk in the system.  It might be nice if it asked you if that was not the case, but it doesn't.  If this is not the case, you need to manually setup grub.  

Now... let's focus on one computer.  What is the disk layout of that computer, and what does fdisk -l show?

---

### Post by bulldog on 2007-05-01
What worries me the most,it will reboot and start perfect,but when the computer is set to  off,it won't boot at all.
Can't imagine it's GRUB causing this.

One should say 'hardware failure' but then again,on two computers at  the same is too much of a coincidence. 

You did reinstall GRUB on the desktop machine,which has two hdd's,one master with XP and one slave with ubuntu.
Let us focus on this machine.
When you reinstalled GRUB,can you remember on which hdd you did this?
I think it was the (hd0) because you had to recover the windows MBR.
I would like to see some output of the next command,
```
sudo fdisk -l
```
If you mount your ubuntu partition with the live cd,can you give me a copy of your menu.lst , fstab and device.map

---

### Post by LiLoather on 2007-05-01
> **psusi said:**
> This conversation has bounced around too much to be useful.  Let's try to focus on one problem shall we?  The installer assumes that you are installing to the primary boot disk in the system.  It might be nice if it asked you if that was not the case, but it doesn't.  If this is not the case, you need to manually setup grub.  

Now... let's focus on one computer.  What is the disk layout of that computer, and what does fdisk -l show?

There is only one computer to focus on now - the laptop.  FreeBSD is running quite happily on the old VA-503+ Ubuntu server refused to boot.

The laptop only has one disk.  fdisk - l :=

Disk /dev/hda:  5124MB, 5124833280 bytes
255 heads , 63 sectors/track,  623 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes

Device         Boot       Start       End       Blocks      Id     System
/dev/hda1     *           1           589        4731111  83     Linux
/dev/had2                 590       623           273105    5     Extended
/dev/hda5                 590       623          273073+  82    Linux swap / Solaris
~#

This was after yet another fresh installation.  For partitioning I selected "Guided - use entire disk".  Later the installer informed me it was "running Grub install (hd0)".

Following installation the machine failed to boot in the usual way - Grub would run to the 'starting up' message and then a re-boot was triggered.  The above information was recovered using the 'rescue' function of the install disk with a shell in the installer environment.

Just after lunch on Sunday I sat down to install Ubuntu on two machines.  It's now 10.49am on Wednesday morning, I have done very little else but wrestle with this in the intervening period and still have no functioning ubuntu system.  Not a great success, I'd say.

---

### Post by LiLoather on 2007-05-01
> **bulldog said:**
> What worries me the most,it will reboot and start perfect,but when the computer is set to  off,it won't boot at all.
Can't imagine it's GRUB causing this.

One should say 'hardware failure' but then again,on two computers at  the same is too much of a coincidence. 

You did reinstall GRUB on the desktop machine,which has two hdd's,one master with XP and one slave with ubuntu.
Let us focus on this machine.
When you reinstalled GRUB,can you remember on which hdd you did this?
I think it was the (hd0) because you had to recover the windows MBR.
I would like to see some output of the next command,
```
sudo fdisk -l
```
If you mount your ubuntu partition with the live cd,can you give me a copy of your menu.lst , fstab and device.map

Hi Bulldog.  I've taken the HDD I was going to put Ubuntu on and dual-boot with XP, out of the desktop as I simply daren't risk Ununtu fouling up XP as well.  I agree it didn't and I was able to recover XP four times, but maybe the fifth...

From memory I didn't install Grub at all. The installer informed me it was doing it and didn't ask me for any input.  I can't remember where it said it was putting it but if it hadn't been on the primary master I presume Xp would have booted normally with wininit.  

What I can't say now is whether it was calling Windows from Grub that wrecked it or just powering down the system.  After a 'successful' installation I booted into both Ubunutu and XP from Grub just be sure I could, and then powered down the system.  On a subsequent cold boot Grub failed.  To resolve that I'd have to put the hdd back into the desktop and reinstall Ubuntu to conduct tests, and I have neither the time nor the inclination.

---

### Post by LiLoather on 2007-05-03
Ah well, I gave it my best shot and now Ubuntu Server, Kubuntu 6.10 and Debian 'Etch' will have to join the growing pile of Debian distributions that simply didn't measure up - or as in the case of Ubuntu, didn't even work at all - because I assume from the silence you don't have a clue either what the problem is and I can't afford to faff around any longer with it.  FreeBSD works so FreeBSD it is.

Other little niggles?  Why does the installer waste time chasing after DHCP before even giving you a chance to set the network up?  Why not just offer it as a choice? 

The first time I tried the installer I set the network up because it asked me to and later the installer went chasing off after security updates without asking me.  As I hadn't set my firewall to let it out it couldn't get anywhere so the installer just hung with no way of backing out and no keyboard response, so to get out of it I had to power-down in the middle of an unfinished install and start again.  Thoughtless.  Subsequently I didn't even bother to set the network up as part of the installation but the installer still wasted my time doing a DHCP call.  Amateurish.

More idiotically, I did try to save the day by looking to install LiLo instead of Grub, but the stupid installer wouldn't let me do it without I'd partitioned the hard-drive all over again and despite the fact I already had the hdd partitioned and the OS installed, and ONLY wanted to install a boot-manager.  Stupid.

Sorry guys but Ubuntu is a dead horse and I've flogged it more than enough.

---

### Post by psusi on 2007-05-03
I probably could have helped you fix it if we could stay focused on one problem, but all the tangents have thrown me off.

---

### Post by LiLoather on 2007-05-03
> **psusi said:**
> I probably could have helped you fix it if we could stay focused on one problem, but all the tangents have thrown me off.

I've no doubt you could have.  I'm also pretty sure it would have turned out to have been something simple.

But the bottom line is that I began installing Unbuntu server just after lunch on Sunday and at 4.00pm the following Thursday still didn't have a working installation despite having spent perhaps 25 hours on it.  At 4.00pm Thursday I decided to scrap Ubuntu and use FreeBSD instead, and by 10.00 pm that evening had it installed and booting happily with a working Gnome desktop, was browsing the web with Epiphany and controlling it remotely with VNC.

That suggests to me that Grub=rubbish and/or there is a serious flaw in the installer.  I have nothing invested in Ubuntu, I just want an OS that does what I want it to.  Ubuntu doesn't, FreeBSD does.

If my experience -and a lost potential Ubuntu user - doesn't bother you, fine.  If it does and you think there might be something to be learned from my experience that might assist the Ubunutu project I'm willing to try another install on the laptop/server and focus on fixing that for a couple of days to uncover the problem for future reference.  Either way it's no skin off my nose.

Your call.

---

### Post by hessiess on 2007-05-06
this sounds like the exact same problem ive got! works perfect untill i boot xp then on restart: 

bios>grub>restart>bios>grub>restart......

this only hapens wen i boot windows.

at the moment i can only boot from the super grub disk, major problem as i use this computer in lesons as im deslexic. this is part of the resen i wanted to try linux as windows is becoming madaningly slow to boot.

i need this sorted by tuesday or ubuntu will haft to go. :(

---

### Post by LiLoather on 2007-05-11
Ah well, Hessiess, looks like the cult doesn't want to know.   As long as you're content to treat Ubuntu as a cheap computer game - something to amuse yourself with at playtime like the old banger in the shed - you're in the in-crowd but need it for something real - something serious - you'd better stick to Windows and the folk who know what they're doing.

---

### Post by psusi on 2007-05-12
Please take your trolling elsewhere.

---

### Post by bulldog on 2007-05-12
> **LiLoather said:**
> Ah well, Hessiess, looks like the cult doesn't want to know.   As long as you're content to treat Ubuntu as a cheap computer game - something to amuse yourself with at playtime like the old banger in the shed - you're in the in-crowd but need it for something real - something serious - you'd better stick to Windows and the folk who know what they're doing.

Well,back to windows then.:) 

FYI,there are some things we can't explain,your computer boots fine with a warm boot,but fails with cold boot.
What do you think?
Maybe it's windows,maybe a piece of hardware,who knows.
But if you can't get it right,well, don't use ubuntu,choose another OS which is working for you.

Ranting isn't gonna help you,grow up and move on!!

---

### Post by hessiess on 2007-05-24
somone at school fixed it, if i new what then i would post it to help the comunaty. windows is becoming a nightmere to use, its just so slow! its going wen ubuntu is working propaly

---

### Post by Arbo on 2007-08-07
I am actually glad to have found this thread.   I have the same sort of thing happening.

I did a new install of 7.04, install went fine, now the machine boots up, Grub comes up, goes to default load ubunto,  then the system reboots, and over and over endlessly.   Does it even if I go to the grub menu and do the boot for 'rescue'.    

Only way to get to a prompt at all is to put the install cd in and then go to 'rescue', then at least I can get to shell.   I've reloaded grub, tried different command line options, always does the same thing.

Getting frustrated.

Paul

---

### Post by LaRoza on 2007-08-07
I love Grub, I use it to boot 10 different OS's. 

I have manually altered it to suit my needs.

If anyone has trouble with it, the forum is a great place to look for answers.

-EDIT The 10 different OS's are on the same harddrive.

---

### Post by Pumalite on 2007-08-07
All of you guys complaining of Grub don't post your specs or give much detail about anything. I suspect is your hardware or you are just ranting ( or trolling ). I run 6 OS's, all with Grub. Never a problem.

---

### Post by hessiess on 2007-08-08
no more problems for me:) winblows is in the crusher!

system specs incise somebody else has this prob
its a hp dv2000 with 1.66 gigaherts intell dual core and gforce go 7200/ 7600 (varies depending on what program i look at!)

```
a@a-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
a@a-laptop:~$ 

```

---

### Post by Arbo on 2007-08-09
You can suspect anything you'd like.   Grub wasn't working.  I went to gentoo, and used grub, and it does the same thing.

Seems to be a grub issue.  Perhaps I'll try lilo.

---

