---
title: "grub UUID help"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by mark on 2007-10-27
I'm desperate - I had 7.10 and Win XP dual-booting, playing nice - and then I got cocky and decided to install Debian etch on my second HDD.  Having run into problems with the  UUID drive/partition/volume identification in the past, I told Debian's installer to write grub to the MBR on the second drive.  Note that I had a working grub entry in the MBR on my primary drive...

When I rebooted and selected Ubuntu from the grub menu, it started loading - and then I was presented with a BusyBox CLI.  I checked and found that the UUID for the 7.10 entry in menu.lst was different from the value returned by blkid.  OK, I managed to edit menu.lst to match the new UUID.  Rebooted - and got a BusyBox message with a blinking cursor to the right of (initramfs).

I have tried virtually everything I could find by googling "grub and UUID" (including trying the Super Grub Disk).  Am I doomed to a reinstall?

If anybody has any suggestions, I'm all ears...<g>

Mark

---

### Post by taurus on 2007-10-27
Instead of using UUID, why not use the device name like root=/dev/hda1 or whatever it is.

---

### Post by mark on 2007-10-27
> **taurus said:**
> Instead of using UUID, why not use the device name like root=/dev/hda1 or whatever it is.

If I could figure out a way to do it consistently, I'd love to.  However, it looks like the future belongs to the UUID...

---

### Post by mark on 2007-10-27
...and the interesting thing is, I can still boot Windows XP, no problems...

---

### Post by confused57 on 2007-10-27
> **mark said:**
> ...and the interesting thing is, I can still boot Windows XP, no problems...
You might try mounting your Ubuntu root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then try commenting out anything in /etc/fstab that was being mounted on your 2nd hard drive at boot.

---

### Post by khughitt on 2007-10-27
Can you paste your Debian menu.lst?

---

### Post by jennymanda on 2007-10-27
And blkid - to tie them up

---

### Post by mark on 2007-10-27
Too late - I already fdisked the 2nd HDD, hoping that would solve the problem.  To no avail, alas...

I'm about to try replacing the UUID strings in menu.lst and fstab with device (/dev/sdxx) and see if that works.  If it doesn't, I'll probably just reinstall (barring any miraculous information from this forum...)

---

### Post by khughitt on 2007-10-27
You could try and have ubuntu re-install grub for you over the debian install's. You should be able to do this from the liveCD, or possibly using grub-install. I've never done this before though so not sure of the exact steps, but I imagine it would work.

Goodluck!

---

### Post by louieb on 2007-10-27
> **mark said:**
> ...I'm about to try replacing the UUID strings in menu.lst and fstab with device (/dev/sdxx) and see if that works.  If it doesn't, I'll probably just reinstall (barring any miraculous information from this forum...)

UUID may be the future, but until a partitions UUID is locked in stone they are going to give people problems. Ive had the UUID change on me 3 times since I installed Feisty 6 months ago. I've been going into /etc/fstab and fixing them.   Next time I'm going back to the /dev/whatever method.

BTW: when editing your menu.lst don't forget to change the **kopt** option too.

---

### Post by toobuntu on 2007-10-27
Seems like you're giving up on using uuids because they change on you.

If it helps, here's a script I put together for myself to list my partitions, their mount points, and their uuids.  I called it get-uuids.sh.  If you wish to use it, don't forget ```
sudo chmod +x get-uuids.sh
```

```
#!/bin/bash
## get-uuids.sh
## run as root (i.e. sudo sh get-uuids.sh)
# because vol_id and parted commands require root privileges
# but will not alter anything as used in this script
echo
echo extended partitions do not have uuids and are not mountable:
for extended in `cat /proc/partitions | grep -v '[0-9]$' | awk '{print $4}' | grep '^[sh]d'` ; do echo $extended`parted /dev/$extended print | grep extended | awk '{print $1}' 2>/dev/nul` = extended partition ; done
extendeds=$extended`parted /dev/$extended print | grep extended | awk '{print $1}'`
echo
echo swap spaces \(virtual memory\) do have uuids:
for swaps in `cat /proc/swaps | grep [0-9] | awk '{print $1}'` ; do echo UUID \(`echo $swaps | cut -d/ -f 3` =\> swap\) = `vol_id -u $swaps 2>/dev/nul` ; done
echo
echo regular partitions \(primary or logical\) also have uuids:
for partition in `cat /proc/partitions | grep '[0-9]$' | awk '{print $4}' | grep -v $extendeds` ; do ( echo UUID \($partition =\> `df -l -x tmpfs -x usbfs | grep -w $partition | awk '{print $6}'`\) = `vol_id -u /dev/$partition 2>/dev/nul` ) ; done
```

The output looks like this:
> $ sudo sh ~/Documents/get-uuids.sh

extended partitions do not have uuids and are not mountable:
sda2 = extended partition

swap spaces (virtual memory) do have uuids:
UUID (sda8 => swap) = 4f5310f6-eab0-4bf9-b5d0-3f16798fa486

regular partitions (primary or logical) also have uuids:
UUID (sda1 => /boot) = 28b8babf-78a2-46c9-8536-7f43977251ab
UUID (sda5 => /) = be6b2de8-4fcf-4379-9ace-dfa258892a9a
UUID (sda6 => /usr) = d3193f5a-c607-4013-a4b7-06cc7abc5fa3
UUID (sda7 => /home) = 7b75a60f-09c9-44f7-94f8-a87305c25d6a
UUID (sda9 => /data) = 294d6e3f-3b8a-43d4-a792-361a7be4fc14
UUID (sda10 => /virtual) = 33cb8f1a-0978-490a-8c30-08296a97f372

---

### Post by khughitt on 2007-10-27
Cool script. I just tried it out myself. Pretty useful :)

---

### Post by louieb on 2007-10-27
Cool Script. Much nicer that ls.  How hard would it be to enhance it to compare the UUIDs in /etc/fstab and menu.lst  to see if they match.

---

### Post by mark on 2007-10-27
I agree with louieb and pwnedd, toobuntu.  It does look like a very handy script.  As soon as I finish reinstalling, I'll check it out <g>.

But, no, I'm not giving up on UUIDs because they change - in theory, I think the UUID concept is very powerful.  *My* problem at this time is that I can't get my bloody desktop to boot, no matter how many ways I've tried to edit menu.lst and/or reinstall grub.

I think I've tried every mother-loving "howto" I've found on the 'net re: reinstalling grub - and none of 'em has worked for me.  Back in the day (a year and a half ago!), I could follow a relatively simple step-by-step (authored by panickedthumb) and get grub working again, come hell or high water.  Now, I install another distro on a separate drive, tell the installer not to go anywhere near the MBR on /dev/sda - and I'm still doomed...<g>

Ah, well.  At least my laptop is still working (meaning I haven't gotten "cute" with it - yet) and I have /home set up in its own partition on my desktop, so I didn't have to worry about losing anything but a little time.  As for that, I've got a fairly nice bottle of Pinot Noir, The Classical Station (WCPE) streaming from my laptop - I've had worse Saturday evenings...

Thanks to all for the feedback - and if anybody runs across a "no kidding, this really works" method of repairing grub, lemme know, will ya?

Mark

---

### Post by toobuntu on 2007-10-27
i just reminded myself of my own grub woes earlier this year.  it's not the same issue you're having, but maybe Herman's advice in this post can give you some ideas:

[http://ubuntuforums.org/showthread.php?t=378517]("http://ubuntuforums.org/showthread.php?t=378517")

---

### Post by mark on 2007-10-27
There, now.  That didn't hurt too badly, did it?

I'm back on my desktop, having done a fresh install - including adding all the "extras" one must have for a functioning system - in a minimal amount of time.  Good thing, too - I'm on the last glass of Pinot Noir...<g>

toobuntu, I appreciate the pointer to Herman's advice - but the Super Grub Disk was one of the things that I tried in my attempt to recover a working system.  It just didn't fly, for some reason...

The good news is that Linux installation has come light-years from where it was, even just a couple of years ago.  While I wouldn't care to repeat this every weekend, at least we're not talking about a 12-hour ordeal...

So, what did I learn?  First of all, breaking the disk layout into /boot, /, /usr and /home is a good idea - especially have /home separate.  Beyond that?  The next time I install a test distro on the second HDD, I'll just let it have its way with the MBR on /dev/sda - because that seems to be the safest route.  Even a backup copy of menu.lst didn't help, in this case.

Oh, yeah - I'd still like to find an updated version of panickedthumb's masterpiece on reinstalling grub...

Mark

---

