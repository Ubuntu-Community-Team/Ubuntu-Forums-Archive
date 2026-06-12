---
title: "No boot after update 14.04 LTS"
date: 2016-03-02
forum: Installation &amp; Upgrades
---

### Post by pssturges on 2016-03-02
Hi,

This morning I ran the available updates on my mythbuntu backend/server as I do on a monthly basis. When I attempted to reboot at the end of this, the machine locked up and required a hard reset. After that the machine will not boot.

Grub loads OK, then it immediately goes to a blank screen with a blinking cursor and goes no further. I have tried recovery modes for available kernels without success. I have also tried nomodeset.

Not sure where I can go from here.

This is my hardware:
[http://www.asrock.com/mb/Intel/Q1900-ITX/?cat=Specifications](http://www.asrock.com/mb/Intel/Q1900-ITX/?cat=Specifications)

Any help much appreciated.
Phil

---

### Post by oldfred on 2016-03-04
First, do not do hard resets unless absolutely nothing else works. That often corrupts file system and then you created another issue. You first have to run fsck to resolve the new issue you created, then can reinstall grub or figure out actual issue.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/) 
    
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 


Did you have nVidia drivers or AMD drivers?
May be best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by pssturges on 2016-03-06
Thanks for the reply.

> **oldfred said:**
> Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown


I generally don't do hard resets if I can avoid it, but was totally unaware of this method. Will definitely keep that one for future reference!

> **oldfred said:**
> 
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 


I have done this. An error was found and repaired, but the same issue continues.

> **oldfred said:**
> 
Did you have nVidia drivers or AMD drivers?
May be best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
My box has intel graphics, so no nVidia or AMD.

I ran boot repair. It completes, saying it has successfully repaired, but the issue remains unaffected.

Here is my boot repair link
[http://paste.ubuntu.com/15305843/]("http://paste.ubuntu.com/15305843/")

Thanks for any further help

---

### Post by oldfred on 2016-03-06
Have you tried one of the Intel boot parameters:
       # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 

Found this which had another Intel boot parameter, but do not know if just Arch or for any Linux:
[https://bbs.archlinux.org/viewtopic.php?id=209280](https://bbs.archlinux.org/viewtopic.php?id=209280)

---

### Post by QLee on 2016-03-07
> **pssturges said:**
> I ran boot repair. It completes, saying it has successfully repaired, but the issue remains unaffected.


When I read the output from your boot repair run, I saw:
"Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached."

You write that your system gets to GRUB then stops, perhaps the error message gives some hints of why your system isn't booting, bad configuration file.

[Edit] I suspect that "Boot successfully repaired" is a generic "finished" message for the run.

---

### Post by oldfred on 2016-03-07
Good catch Qlee, I missed it.

I had same error years ago. I had added my own boot stanza to 40_custom. And early versions of grub2 were ok with it.
Then it stopped working and created the grub.cfg.new. In looking at grub.cfg.new was able to figure out that I was missing }. It gave errors on which line but in my case it was not exact line with error.

---

### Post by pssturges on 2016-03-07
Thanks for the responses. Sorry I haven't had much of a chance to put time into this yet, but I have done a little. I can only give quick update now but will add some more detail later.

It does appear to be a grub issue. I can't remember the exact details, but in boot repair there is an option to re-install grub. I tried this but it errors out. I then tried manually re-installing grub following these instructions:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
That errors out also.

Hopefully I'll get a bit of time with it later today and provide more details.

Thanks again for your help.

---

### Post by oldfred on 2016-03-07
Boot-Repair also has an option to do a full uninstall/reinstall of grub. That probably will fix it, but then we do not know issue. :)

Can you look in grub.cfg.new and see what the error message is at bottom. It should give a line number which may or may not be exact line with error.

---

### Post by QLee on 2016-03-08
> **pssturges said:**
> Thanks for the responses. Sorry I haven't had much of a chance to put time into this yet, but I have done a little.

Hopefully I'll get a bit of time with it later today and provide more details..

You've been around here for a long time so I imagine you realise how much easier it is to help someone when those trying to help get to see the exact wording of error messages, Linux error messages often give useful information for troubleshooting and even sometimes tell what to do to correct an issue.

Please do as oldfred suggests if you can take the time, figuring out what caused this might uncover an issue that coders need to know about so they can improve the boot repair script and at the very least, others reading the forum can learn what to avoid. One of the powers of Ubuntu forums is the wealth of knowledge contained within and searchable.

---

### Post by pssturges on 2016-03-08
> **oldfred said:**
> Boot-Repair also has an option to do a full uninstall/reinstall of grub. That probably will fix it, but then we do not know issue. :)

Can you look in grub.cfg.new and see what the error message is at bottom. It should give a line number which may or may not be exact line with error.

Thanks,

Yes this is the option I had used and errros out. I get to the part where it says:
"Please open a terminal andtype the following commands:"
```
sudo chroot "/mnt/boot-sav/sda1" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda1" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda1" apt-get install -y --force-yes grub-pc
```

The first 2 work fne, but I get the following output on the third:
```
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda1" apt-get install -y --force-yes grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-50 linux-headers-3.16.0-50-generic
  linux-headers-3.16.0-51 linux-headers-3.16.0-51-generic
  linux-headers-3.16.0-53 linux-headers-3.16.0-53-generic
  linux-headers-3.16.0-57 linux-headers-3.16.0-57-generic
  linux-image-3.16.0-50-generic linux-image-3.16.0-51-generic
  linux-image-3.16.0-53-generic linux-image-3.16.0-57-generic
  linux-image-extra-3.16.0-50-generic linux-image-extra-3.16.0-51-generic
  linux-image-extra-3.16.0-53-generic linux-image-extra-3.16.0-57-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
0 upgraded, 5 newly installed, 0 to remove and 17 not upgraded.
Need to get 0 B/3,237 kB of archives./boot/grub/grub.cfg.new
After this operation, 16.4 MB of additional disk space will be used.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 22.
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown user 'root' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
lubuntu@lubuntu:~$ 

```

I wasn't entirely sure where I should find grub.cfg.new. The only one I could find was at /boot/grub.bak on my system drive. There is no /boot/grub/grub.cfg.new. In fact there is no /boot/grub directory, only /boot/grub.bak

Contents were:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

```

Manual install of grub following these instructions:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

All goes well untill:
```

I have no name!@lubuntu:/# grub-install /dev/sda
The program 'grub-install' can be found in the following packages:
 * grub
 * grub2-common
 * lupin-support
Try: apt-get install <selected package>
I have no name!@lubuntu:/# sudo apt-get install grub
sudo: unknown uid 0: who are you?
I have no name!@lubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-50 linux-headers-3.16.0-50-generic
  linux-headers-3.16.0-51 linux-headers-3.16.0-51-generic
  linux-headers-3.16.0-53 linux-headers-3.16.0-53-generic
  linux-headers-3.16.0-57 linux-headers-3.16.0-57-generic
  linux-image-3.16.0-50-generic linux-image-3.16.0-51-generic
  linux-image-3.16.0-53-generic linux-image-3.16.0-57-generic
  linux-image-extra-3.16.0-50-generic linux-image-extra-3.16.0-51-generic
  linux-image-extra-3.16.0-53-generic linux-image-extra-3.16.0-57-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
Need to get 0 B/2,591 kB of archives.
After this operation, 14.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 22.
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown user 'root' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
I have no name!@lubuntu:/# 

```

So, similar result I guess.

Hopefully this will give you a little more info to go on. Thanks again.

---

### Post by oldfred on 2016-03-08
Did you create your user id as:
I have no name!
And it said this:
sudo: unknown uid 0: who are you?
So you may not be at admin or root to run commands.

Linux does not like spaces, and you have to escape them, or put entire entry in quotes. Best not to use spaces anywhere.
When I converted from XP to Ubuntu I stopped using spaces. I use onelongname, CamelCase, or under_score instead.

The name space issue could be part of all the issues, but not sure.

---

### Post by pssturges on 2016-03-09
No, my username in this system is 'phil'. I do generally try to avoid spaces for as much as I can under linux. Just simplifies things.

The references to those usernames I thought was something to do with the boot repair live cd. So is it referring to usernames on my system? There's something very wrong if it is.

---

### Post by QLee on 2016-03-09
phil, because you are a longtime user I am assuming you're doing things correctly. However, it's probably a good idea to just try one thing at a time and wait until that thing has been discussed before trying another "fix" that you find on another site (the goalposts may be moving on us). 

I guess we might need to look at /etc/passwd to make sure root is in there because what you've told us seems to indicate that the system doesn't recognise user 0.

I don't understand how any of the things you've told us that you did could have messed with that, except, possibly that time when you had to crash the system to shut down. 

I'm running out of ideas.

@oldfred Please come up with one of your magic incantation to fix this. ;-)

---

### Post by oldfred on 2016-03-09
This is a new one for me.

When running live installer this is or should be your id, and on first post that is what it is:
lubuntu@lubuntu:~$
so not sure where this came from, it is like you logged into root which does not have a name, password in Ubuntu.
I have no name!@lubuntu:/#

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by QLee on 2016-03-09
@oldfred, my thinking on this was that when sudo was used that would give the system uid 0 because sudo is suid but it seems the system doesn't recognise that uid 0 is "root".

@pssturges, maybe we should look at what's in that statoverride file too which was mentioned in the error message. /var/lib/dpkg/statoverride.

---

### Post by pssturges on 2016-03-10
> **QLee said:**
> phil, because you are a longtime user I am assuming you're doing things correctly. However, it's probably a good idea to just try one thing at a time and wait until that thing has been discussed before trying another "fix" that you find on another site (the goalposts may be moving on us). 

I guess we might need to look at /etc/passwd to make sure root is in there because what you've told us seems to indicate that the system doesn't recognise user 0.

I don't understand how any of the things you've told us that you did could have messed with that, except, possibly that time when you had to crash the system to shut down. 

I'm running out of ideas.

@oldfred Please come up with one of your magic incantation to fix this. ;-)

Hmm, there is no /etc/passwd. There is a /etc/passwd-. It's contents are:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
mysql:x:102:106:MySQL Server,,,:/nonexistent:/bin/false
messagebus:x:103:107::/var/run/dbus:/bin/false
usbmux:x:104:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:105:65534:dnsmasq,,,:/var/lib/misc:/bin/false
ntp:x:106:109::/home/ntp:/bin/false
avahi-autoipd:x:107:114:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
sshd:x:108:65534::/var/run/sshd:/usr/sbin/nologin
rtkit:x:109:115:RealtimeKit,,,:/proc:/bin/false
saned:x:110:116::/home/saned:/bin/false
avahi:x:111:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm:x:112:119:Light Display Manager:/var/lib/lightdm:/bin/false
pulse:x:113:121:PulseAudio daemon,,,:/var/run/pulse:/bin/false
colord:x:114:123:colord colour management daemon,,,:/var/lib/colord:/bin/false
mythtv:x:115:124::/home/mythtv:/bin/sh
phil:x:1000:1001:Phil Sturges:/home/phil:/bin/bash
marion:x:1001:1001:Marion Sturges:/home/marion:/bin/sh
kaitlyn:x:1002:1001:Kaitlyn Sturges:/home/kaitlyn:/bin/sh
megan:x:1003:1001:Megan Sturges:/home/megan:/bin/sh
jacob:x:1004:1001:Jacob Sturges:/home/jacob:/bin/sh
sam:x:1005:1001:Sam Sturges:/home/sam:/bin/sh
dhcpd:x:116:126::/var/run:/bin/false
hplip:x:117:7:HPLIP system user,,,:/var/run/hplip:/bin/false
squeezeboxserver:x:118:65534::/usr/share/squeezeboxserver:/bin/false
```

So, so far we have no /etc/passwd and no /boot/grub, but there are some kind of backups for each we could potentially restore.

> **oldfred said:**
> This is a new one for me.

When running live installer this is or should be your id, and on first post that is what it is:
lubuntu@lubuntu:~$
so not sure where this came from, it is like you logged into root which does not have a name, password in Ubuntu.
I have no name!@lubuntu:/#

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

[http://paste.ubuntu.com/15340394/](http://paste.ubuntu.com/15340394/)

> **QLee said:**
> @oldfred, my thinking on this was that when sudo was used that would give the system uid 0 because sudo is suid but it seems the system doesn't recognise that uid 0 is "root".

@pssturges, maybe we should look at what's in that statoverride file too which was mentioned in the error message. /var/lib/dpkg/statoverride.

```
root lp 775 /var/log/hp/tmp
root mlocate 2755 /usr/bin/mlocate
hplip root 755 /var/run/hplip
root ssl-cert 710 /etc/ssl/private
root crontab 2755 /usr/bin/crontab

```

Thanks for all your help on this. I should also mention that I do have a system backup from about a week prior to the crash that we could potentially use to restore lost/broken files or indeed the entire system if it comes to it. I would prefer to fix it if possible though. 

Thanks again
Phil

---

### Post by QLee on 2016-03-10
> **pssturges said:**
> Hmm, there is no /etc/passwd. There is a /etc/passwd-


That passwd~ is supposed to be a backup of passwd. I don't know any reason why anything we have discussed could have lost your passwd file but I'd guess not having it could be a problem. If there was corruption when you crashed the system it would be very bad luck if it resulted in a problem like this but sometimes, stuff happens. Don't post it but does your system have a /etc/shadow file? (another part of the authentication system)

You have a backup, and good for you for having one. If it was my system, I think I would try copying that /etc/passwd~ in your system as /etc/passwd, and then try re-running the suggestion that oldfred gave to restore GRUB. The system needs both the passwd and shadow files. At some point your system is going to have to be able to update-grub to generate a grub.cfg. I hope you did check the grub files in /etc/default/grub that were mentioned in the error message we saw.

Phil, note that I'm just speculating at this point, it might be wise to wait until oldfred or someone else reading this comments.

---

### Post by oldfred on 2016-03-10
I have not dealt with password issues, best to follow Qlee's suggestions and then see where we are at.

---

### Post by pssturges on 2016-03-10
Some progress! Still a way to go but I feel we are getting there.

Here is what I have done:
There was no /etc/shadow. I went ahead and restored the /etc/passwd- to /etc/passwd.
Re-ran boot repair but there was still errors. 
I followed the instructions to repair grub I posted earlier and it worked!
So, now when I boot, grub appears, and the boot process starts. After a few seconds it halts here:
[ATTACH=CONFIG]267738[/ATTACH]
I then press enter and I get the following:
[ATTACH=CONFIG]267737[/ATTACH]
At this point it doesn't accept my root password and pressing control-d repeats the error.
So this is where I'm kind of stuck again. Perhaps the password is not being accepted due to the lack of /etc/shadow?

I have also tried booting into recovery mode, which works. Tried doing a disk check which is successful. Still doesn't allow the system to boot though. Not sure what else useful I can do in recovery mode?

---

### Post by QLee on 2016-03-10
Phil, as I wrote, the system needs both files, passwd and shadow. Is there a backup of shadow (shadow~) like there was of passwd that you could use to restore like you did passwd~? You aren't going to be able to login without shadow.

What were the errors when you re-ran boot repair, different from before or the same, sometimes (often) the error messages give hints of what is happening. If GRUB reinstall was successful you shouldn't need to do that step again but you are still going to have to update-grub so that there is a working grub.cfg or have you done that?

But, you mentioned it didn't accept your root password, is this a server version that could actually have a root password?

Glad you have a recent backup Phil because we aren't making much progress. If the crash took out both passwd and shadow, who knows how many other files were trashed.

I'm leaving tomorrow for a week, so the only thing further I can add is good luck.

---

### Post by oldfred on 2016-03-10
I think the quick fsck that is on a boot, is not as complete as a full fsck. With ext4 it self reports issues and fsck just checks if drive is saying it has issues.

Best to run full fsck.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
   [http://askubuntu.com/questions/642504/ubuntu-14-04-is-not-booting-normaly-after-a-manual-hard-boot/642789#642789](http://askubuntu.com/questions/642504/ubuntu-14-04-is-not-booting-normaly-after-a-manual-hard-boot/642789#642789)

---

### Post by pssturges on 2016-03-11
> **QLee said:**
> Phil, as I wrote, the system needs both files, passwd and shadow. Is there a backup of shadow (shadow~) like there was of passwd that you could use to restore like you did passwd~? You aren't going to be able to login without shadow.

What were the errors when you re-ran boot repair, different from before or the same, sometimes (often) the error messages give hints of what is happening. If GRUB reinstall was successful you shouldn't need to do that step again but you are still going to have to update-grub so that there is a working grub.cfg or have you done that?

But, you mentioned it didn't accept your root password, is this a server version that could actually have a root password?

Glad you have a recent backup Phil because we aren't making much progress. If the crash took out both passwd and shadow, who knows how many other files were trashed.

I'm leaving tomorrow for a week, so the only thing further I can add is good luck.

From what I remember, the boot repair errors were much the same as previously. 
The grub repair does seem to be complete including update-grub, so there does appear to be a reasonably coherent grub.cfg. Seems the grub issues are pretty much resolved.

I have managed to retrieve my backed up /etc/shadow and restore it. The system now boots to same point as the previous post, except now after I press enter it drops into a console logged in as root@htpcserver. 

So it appears I now have a somewhat functioning system! I can navigate around the files system and run commands. Its a start!

As you are, I am concerned how much more of the system has been damaged. I am tempted to start restoring some more parts of the system from my backup. Say things like the /etc directory. My main concern is maintaining the most up to date possible version of my mysql tables. Most other variable data is stored on separate hard drives.

Thanks for all your help QLee. Very much appreciated and enjoy your trip! Hopefully this will be all fixed by the time you get back!

---

### Post by pssturges on 2016-03-11
> **oldfred said:**
> I think the quick fsck that is on a boot, is not as complete as a full fsck. With ext4 it self reports issues and fsck just checks if drive is saying it has issues.

Best to run full fsck.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
   [http://askubuntu.com/questions/642504/ubuntu-14-04-is-not-booting-normaly-after-a-manual-hard-boot/642789#642789](http://askubuntu.com/questions/642504/ubuntu-14-04-is-not-booting-normaly-after-a-manual-hard-boot/642789#642789)

I have now done this on all partitions in the system. Didn't seem to come up with any errors and doesn't seem t have made any difference.

Not that it matters too much at this stage, but my theory as to why this has all happened is that I somehow have managed to interrupt the update process. I can't remember which way I did it this time, but most times I use the terminal to run updates, occasionally I'll use the GUI. I usually set it on it's merry way, then come back sometime later when it's all done and do a reboot if necessary. I'm thinking that this time I didn't notice that the update was still running or perhaps hung up for some reason and initiated the reboot. No surprise, I guess that the shutdown hung and files that were being worked on at that moment got fried or lost. Anyway that's the only explanation I can come up with.

---

### Post by oldfred on 2016-03-11
If that is the case, you probably need to finish update.
It may require you to chroot into system, if you cannot boot to recovery mode.

 UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597) 

Examples above are more to reinstall grub, you want to restart or finish update if possible.
These are some of commands:

 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

---

### Post by pssturges on 2016-03-17
Firstly thank you oldfred & QLee for you wonderful assistance. It really is appreciated.

In the end, despite everyones best efforts I decided the effort required to get it up and running again was not worth it. It looked like there were going to be too many problems to overcome, so it was a much easier proportion to do a fresh install, then restore the important parts from my backup. I was also able to recover my mysql tables from the crashed system and resort those so no data lost.

Thank you again
Phil

---

### Post by pssturges on 2016-04-01
I can't believe its happened again! Although, slightly different this time. It's been running fine the last couple of weeks, then I ran the updates, rebooted, now I'm stuck in a reboot loop.

I get grub, then a flash of text too fast to read, then the system reboots. Repeats.

So I  guess I need to use a live cd to look at logs on my system drive, just not sure which ones might be useful.

I ran  boot repair and it completes successfully, but nothing changes.

Thanks yet again!

---

### Post by oldfred on 2016-04-02
Can you boot using second grub entry or recovery?

Post link to Summary Report from Boot-Repair.

---

### Post by pssturges on 2016-04-02
Same result with other kerenels and recovery.

Boot repair log here:
[http://paste.ubuntu.com/15594325/](http://paste.ubuntu.com/15594325/)

---

### Post by oldfred on 2016-04-03
I see this: 
 Atom Processor Z36xxx/Z37xxx Series Graphics 

Is that a Bay Trail Processor? New Kernels or Intel support software has regressed.


 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by QLee on 2016-04-03
> **pssturges said:**
> I can't believe its happened again! Although, slightly different this time. It's been running fine the last couple of weeks, then I ran the updates, rebooted, now I'm stuck in a reboot loop.

Well, "it" isn't happening "again", as this is clearly not the same problem. Gee, it doesn't even look like exactly the same computer.

```
Excerpt from original boot repair script:

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        cb664320-fe0b-4fe8-a2b6-177932c50882   ext4       
/dev/sda5        3732c95b-12d1-4774-8373-daab9ea66279   swap       

Excerpt  from current boot repair script:

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        900e0a98-782e-41da-9553-fee1da20f1de   ext4       storage
/dev/sdb1        3e6a92bb-3fd0-4232-9602-08431e2d43fe   ext4       
/dev/sdb5        433917dd-5784-4d49-a57f-b5f28b5636f5   swap       
/dev/sdc1        c83fc0d6-9773-4692-8f90-e02ef6e901c5   ext4       recordedtv
/dev/sdc2        9fdf4c95-ce81-492b-aabb-b138d04bb147   ext4       storage2
```

You seem to have added drives, also different UUIDs for the drives involved than what were there previously and now an unknown bootloader on sdb2 from boot repair script, ... huh, there is no sdb2 or rather it's the extended partition? Is this all due to your re-install?

So, have you been doing things that you haven't told us about, or is someone else accessing your system? All that stuff about torrents in the unknown bootloader on sdb2 seems suspicious.

Did you do the last thing suggested in the boot repair script? 
"You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (60.0GB) disk!"

---

### Post by pssturges on 2016-04-03
> **oldfred said:**
> I see this: 
 Atom Processor Z36xxx/Z37xxx Series Graphics 

Is that a Bay Trail Processor? New Kernels or Intel support software has regressed.


 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

Thanks. Yes!
This is my hardware:
[http://www.asrock.com/mb/Intel/Q1900-ITX/?cat=Specifications](http://www.asrock.com/mb/Intel/Q1900-ITX/?cat=Specifications)

Although, it doesn't 'feel' like this is my issue here as apparently the issue involves X freezes? With both my occurrences, the system isn't getting close to loading X.

---

### Post by pssturges on 2016-04-03
> **QLee said:**
> Well, "it" isn't happening "again", as this is clearly not the same problem. Gee, it doesn't even look like exactly the same computer.

```
Excerpt from original boot repair script:

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        cb664320-fe0b-4fe8-a2b6-177932c50882   ext4       
/dev/sda5        3732c95b-12d1-4774-8373-daab9ea66279   swap       

Excerpt  from current boot repair script:

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        900e0a98-782e-41da-9553-fee1da20f1de   ext4       storage
/dev/sdb1        3e6a92bb-3fd0-4232-9602-08431e2d43fe   ext4       
/dev/sdb5        433917dd-5784-4d49-a57f-b5f28b5636f5   swap       
/dev/sdc1        c83fc0d6-9773-4692-8f90-e02ef6e901c5   ext4       recordedtv
/dev/sdc2        9fdf4c95-ce81-492b-aabb-b138d04bb147   ext4       storage2
```

You seem to have added drives, also different UUIDs for the drives involved than what were there previously and now an unknown bootloader on sdb2 from boot repair script, ... huh, there is no sdb2 or rather it's the extended partition? Is this all due to your re-install?

So, have you been doing things that you haven't told us about, or is someone else accessing your system? All that stuff about torrents in the unknown bootloader on sdb2 seems suspicious.

Did you do the last thing suggested in the boot repair script? 
"You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (60.0GB) disk!"

Sorry for the confusion here. I had removed the other disks when trying to de-bug in an effort to keep things simple last time round. I hadn't bothered with that this time.

My 'fix' last time was to do a fresh install then restore the important stuff from my backup, which is why my system drive has a different UUID.

"All that stuff about torrents in the unknown bootloader on sdb2 seems suspicious." - Yes it is. And a bit weird?
"You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (60.0GB) disk!" - Yes

---

### Post by QLee on 2016-04-04
> **pssturges said:**
> 
"All that stuff about torrents in the unknown bootloader on sdb2 seems suspicious." - Yes it is. And a bit weird?
"You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (60.0GB) disk!" - Yes


Well, from what I saw in the results from the boot info script, your system should have booted if you booted from the "Kingston" drive first which would then make it sda. It has the bootloader in the mbr and it has the necessary files at the normal location.  At this point I would likely try one of two things, disconnect the Western Digital drive and try to boot the system from the Kingston (likely would boot slow because of looking for the drive noted in the fstab) or, with the WD still connected I, might try the reinstalling GRUB to the mbr of sda (WD)  from the chrooted sdb1 (Kingston) partition and then do an update GRUB from there and watch to see if it probes and finds the two kernels that you have now on your system.  

I am assuming that the Kingston drive is the same one that we were working with as sda in the beginning and that unrecognised bootloader wasn't identified then so something must have happened to the extended partition 2 between then and now. I doubt the new install caused that. Are we sure that drive is still good or could it have caused the corruption that we saw in the beginning of this thread?


[edit]
> **pssturges said:**
> I get grub, then a flash of text too fast to read, then the system reboots. Repeats.

Of course, as I'm sure you realise, it would be best if we had some idea of what the system was trying to tell us at this point but if you can't see it, you can't see it.  Can you determine if it is an actual system reboot or does it just return to the GRUB menu.

---

### Post by pssturges on 2016-04-04
I'm not home for the next 24 hours or so, so I can't do much until then, but I can add the following in the meantime.

> **QLee said:**
> Can you determine if it is an actual system reboot or does it just return to the GRUB menu.
Definitely a proper reboot. 

It's hard to say for sure, but to me it 'feels' like the grub part of the process is proceeding OK, but the crash happens as the kernel/system starts to load.

Hopefully more info to follow tomorrow.

Thanks

---

### Post by QLee on 2016-04-05
> **pssturges said:**
> It's hard to say for sure, but to me it 'feels' like the grub part of the process is proceeding OK, but the crash happens as the kernel/system starts to load.

I'm running out of ideas and starting to grasp at straws now. :-)

I agree that your system seems to be proceeding normally through the boot process, sees the master boot record, finds GRUB and presents the menu, then it is supposed to find (your choice from the menu) and hand off to the kernel. This seems like the point at which you see the reboot.  If it doesn't find the kernel I would expect it to go back to the menu so maybe it fails when the kernel tries to start init, maybe that is what you see flash by on the screen.
[edit] I suppose you could try catching the boot process at the GRUB menu and editing out the "quiet splash"  from the command line of the kernel that you are trying to boot to see if that gives us any useful information on screen. Ah, good, I see oldfred thinks that is worth a try also.[/edit] 

Just to clarify, you do have secure boot turned off in the BIOS don't you? And rapid start.

I don't know what would happen if secure boot was on and you somehow managed to get your install done without signed kernels. I don't know if it would fail with a error message that flashed by like you describe or if it would just fail quietly, I would expect it to go back to the GRUB menu rather than a reboot but I don't have any experience with secure boot so I can't say for sure.  Maybe secure boot is handled by the BIOS and then this wouldn't apply because your system is getting past that point.  

@oldfred will probably see this and let us know.

---

### Post by oldfred on 2016-04-05
I have never turned Secure boot on. (may have to someday, but for now I do not consider it required).

Error could be something like that.

Can you get grub menu?
UEFI uses Escape key to bring up menu at or just after UEFI/BIOS screen. If UEFI fast boot on, there usually is not enough time to register a key.
If booting in BIOS mode, the holding shift key is required to get into grub menu.

And then try removing quiet splash on linux line. Use e to edit grub entry. Then you see boot process, perhaps still very quick.

---

