---
title: "Desktop icons disappear"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-07
I have noticed that my desktop icons all disappear after a period of time.  When they do, they don't come back until reboot.  I believe they disappear when my screensaver kicks on. anyone else?

EDIT: I have an encrypted install with a 70 character key that I have to enter 2x (2 drives to mount) so I don't like to restart often and I have not verified the SS is when they go.  Will after next update push that requires restart.  Mainly just curious if anyone has similar problem.

EDIT 2:  This thread is not displaying properly for me I had to go to user CP and set posts per page to 20.  There have been more than 10 posts for a while but no page 2 link appeared at default 10 posts per page??

---

### Post by mobilediesel on 2009-01-07
> **LordVeovis said:**
> I have noticed that my desktop icons all disappear after a period of time.  When they do, they don't come back until reboot.  I believe they disappear when my screensaver kicks on. anyone else?

EDIT: I have an encrypted install with a 70 character key that I have to enter 2x (2 drives to mount) so I don't like to restart often and I have not verified the SS is when they go.  Will after next update push that requires restart.  Mainly just curious if anyone has similar problem.

My icons all disappeared after I went to the settings manager and selected "Desktop Icons = None"

Then again I prefer that there are no icons on the desktop. :D

---

### Post by autocrosser on 2009-01-07
Try doing a "killall nautilus" in a term--that should refresh your desktop--as to why your icons are going--I would need more time to think about why..

First try changing the screensaver you are using..
Next, try changing the icons/theme you are using..

You should also look thru your logs for anything strange.

---

### Post by Gina on 2009-01-07
I've had the desktop icons disappear for a short time then reappear - I haven't lost them for long.  This is accompanied by a general slow-up where the screen rewrites very slowly and black boxes appear all over the place.  The latter was reported some time ago and I thought it had been fixed but it's back.  I would think it's a display problem and due to updates to xorg and the nvidia drivers - I'm using the beta driver 180.18.  I think this is a different issue from the OP.

---

### Post by ShirishAg75 on 2009-01-07
> **mobilediesel said:**
> My icons all disappeared after I went to the settings manager and selected "Desktop Icons = None"

Then again I prefer that there are no icons on the desktop. :D

Where is this Settings manager? I'm unable to find it.

---

### Post by autocrosser on 2009-01-07
Not sure what the poster was talking about, but you can goto gconf manager & uncheck all the desktop icon options in Nautilus--  Personally, I like having them there.

---

### Post by LordVeovis on 2009-01-07
> **Gina said:**
> I've had the desktop icons disappear for a short time then reappear - I haven't lost them for long.  This is accompanied by a general slow-up where the screen rewrites very slowly and black boxes appear all over the place.  The latter was reported some time ago and I thought it had been fixed but it's back.  I would think it's a display problem and due to updates to xorg and the nvidia drivers - I'm using the beta driver 180.18.  I think this is a different issue from the OP.

I don't experience the slowing or black blocks anymore (that was fixed for me)  but Icons have been disappearing for a while, I figured I would get a patch to fix soon, but no.  I just restarted when I got home from work because of updates again.  Lets see if the SS does it.  If so we will try changing themes and SS.

---

### Post by LordVeovis on 2009-01-08
Ok, so it may not be the screensaver.  I was using my PC after 3 different reboots and they disappeared still while I was using it.  Maybe from apps that fullscreen.  Don't know. As I don't have many icons, i tend to not notice until likely 10 min later.  I guess I should start reseting more often to try to narrow it down.  /sigh/

---

### Post by Gourgi on 2009-01-08
i experienced the same today.
all desktop icons where gone
uptime was around 13 hours
the funny thing was that when i tried to "killall nautilus" i got "no such process" while i was still able to browse my files and folders properly,mount volumes properly !!:o
anyway , hitting Alt+F2 "nautilus" make desktop icons appear again.
very strange though

---

### Post by tawmas on 2009-01-08
I have a slight suspect that this is related with Nautilus crashing and restarting when you insert a CD (perhaps other removable media as well, but I didn't try with a USB key yet, and I'm not 100% sure it happens when I turn on my external USB disk as I usually turn it on before logging in).

At least once, after one such crash, it didn't restart and I lose my desktop icons.

You could look for segfaults in syslog. Mine look like this:

```
nautilus[6045]: segfault at 255acb8 ip 000000000255acb8 sp 00007fffea063118 error 15
```


**EDIT**: I just tested turning on my USB disk. Nautilus crashed and didn't restart, so Desktop icons are gone. Below the relevant syslog fragment: note the nice segfault at line 4 :-)
Manually lanching Nautilus restores the icons.

```
Jan  8 17:06:39 tylke kernel: [ 6082.256015] usb 5-3: new high speed USB device using ehci_hcd and address 5
Jan  8 17:06:40 tylke kernel: [ 6082.397382] usb 5-3: configuration #1 chosen from 1 choice
Jan  8 17:06:40 tylke kernel: [ 6082.397914] scsi6 : SCSI emulation for USB Mass Storage devices
Jan  8 17:06:40 tylke kernel: [ 6082.403896] nautilus[6699]: segfault at 1e57748 ip 0000000001e57748 sp 00007fff807c3968 error 15
Jan  8 17:06:40 tylke kernel: [ 6082.420423] usb-storage: device found at 5
Jan  8 17:06:40 tylke kernel: [ 6082.420428] usb-storage: waiting for device to settle before scanning
Jan  8 17:06:45 tylke kernel: [ 6087.420266] usb-storage: device scan complete
Jan  8 17:06:45 tylke kernel: [ 6087.420733] scsi 6:0:0:0: Direct-Access     ST310003 33AS                  PQ: 0 ANSI: 2 CCS
Jan  8 17:06:45 tylke kernel: [ 6087.422807] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jan  8 17:06:45 tylke kernel: [ 6087.423588] sd 6:0:0:0: [sdg] Write Protect is off
Jan  8 17:06:45 tylke kernel: [ 6087.423592] sd 6:0:0:0: [sdg] Mode Sense: 34 00 00 00
Jan  8 17:06:45 tylke kernel: [ 6087.423595] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan  8 17:06:45 tylke kernel: [ 6087.430342] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jan  8 17:06:45 tylke kernel: [ 6087.431091] sd 6:0:0:0: [sdg] Write Protect is off
Jan  8 17:06:45 tylke kernel: [ 6087.431095] sd 6:0:0:0: [sdg] Mode Sense: 34 00 00 00
Jan  8 17:06:45 tylke kernel: [ 6087.431098] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan  8 17:06:45 tylke kernel: [ 6087.431105]  sdg: sdg1
Jan  8 17:06:45 tylke kernel: [ 6087.458154] sd 6:0:0:0: [sdg] Attached SCSI disk
Jan  8 17:06:45 tylke kernel: [ 6087.458246] sd 6:0:0:0: Attached scsi generic sg8 type 0
```

---

### Post by ShirishAg75 on 2009-01-08
please put up a bug-report of the same. 

Do

```
$ apport-cli -f -p nautilus
```

OR 

click on Report bug from Nautilus Help 

and attach the syslog.

---

### Post by ShirishAg75 on 2009-01-08
Put up a bug-report about the same on launchpad.

---

### Post by ShirishAg75 on 2009-01-08
Post if using Report a bug in Nautilus and attach the syslog.

---

### Post by ShirishAg75 on 2009-01-08
Put up the bug in launchpad using Nautilus > Help > Report a bug

---

### Post by LordVeovis on 2009-01-08
Odd I cant see all the posts in here, when I click reply more show up than what is on main page.  Oh well.  has anyone posted a bug yet on this?

---

### Post by ShirishAg75 on 2009-01-08
have you posted the bug in launchpad?

---

### Post by LordVeovis on 2009-01-08
This thread still seems to be broken even after the forum servers were down all day?

@Tawmas
Anyways, yes this is my problem as well.  Just never noticed it was related to that. (USB and CD both)  I am still new to the whole troubleshooting side here.  First alpha release here.  I have jumped on betas (mainly for new bleeding edge software or what not) cause they are more stable and I was newer to linux.  But I thought it would be a good timke to get more than just my feet wet!!

---

### Post by olskar on 2009-01-08
> **tawmas said:**
> I have a slight suspect that this is related with Nautilus crashing and restarting when you insert a CD (perhaps other removable media as well, but I didn't try with a USB key yet, and I'm not 100% sure it happens when I turn on my external USB disk as I usually turn it on before logging in).

At least once, after one such crash, it didn't restart and I lose my desktop icons.

You could look for segfaults in syslog. Mine look like this:

```
nautilus[6045]: segfault at 255acb8 ip 000000000255acb8 sp 00007fffea063118 error 15
```


**EDIT**: I just tested turning on my USB disk. Nautilus crashed and didn't restart, so Desktop icons are gone. Below the relevant syslog fragment: note the nice segfault at line 4 :-)
Manually lanching Nautilus restores the icons.

```
Jan  8 17:06:39 tylke kernel: [ 6082.256015] usb 5-3: new high speed USB device using ehci_hcd and address 5
Jan  8 17:06:40 tylke kernel: [ 6082.397382] usb 5-3: configuration #1 chosen from 1 choice
Jan  8 17:06:40 tylke kernel: [ 6082.397914] scsi6 : SCSI emulation for USB Mass Storage devices
Jan  8 17:06:40 tylke kernel: [ 6082.403896] nautilus[6699]: segfault at 1e57748 ip 0000000001e57748 sp 00007fff807c3968 error 15
Jan  8 17:06:40 tylke kernel: [ 6082.420423] usb-storage: device found at 5
Jan  8 17:06:40 tylke kernel: [ 6082.420428] usb-storage: waiting for device to settle before scanning
Jan  8 17:06:45 tylke kernel: [ 6087.420266] usb-storage: device scan complete
Jan  8 17:06:45 tylke kernel: [ 6087.420733] scsi 6:0:0:0: Direct-Access     ST310003 33AS                  PQ: 0 ANSI: 2 CCS
Jan  8 17:06:45 tylke kernel: [ 6087.422807] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jan  8 17:06:45 tylke kernel: [ 6087.423588] sd 6:0:0:0: [sdg] Write Protect is off
Jan  8 17:06:45 tylke kernel: [ 6087.423592] sd 6:0:0:0: [sdg] Mode Sense: 34 00 00 00
Jan  8 17:06:45 tylke kernel: [ 6087.423595] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan  8 17:06:45 tylke kernel: [ 6087.430342] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jan  8 17:06:45 tylke kernel: [ 6087.431091] sd 6:0:0:0: [sdg] Write Protect is off
Jan  8 17:06:45 tylke kernel: [ 6087.431095] sd 6:0:0:0: [sdg] Mode Sense: 34 00 00 00
Jan  8 17:06:45 tylke kernel: [ 6087.431098] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan  8 17:06:45 tylke kernel: [ 6087.431105]  sdg: sdg1
Jan  8 17:06:45 tylke kernel: [ 6087.458154] sd 6:0:0:0: [sdg] Attached SCSI disk
Jan  8 17:06:45 tylke kernel: [ 6087.458246] sd 6:0:0:0: Attached scsi generic sg8 type 0
```


I have the very same problem, kind of annoying

---

### Post by olskar on 2009-01-08
Here is from my dmesg:
> [ 2281.470283] sd 4:0:0:2: [sdd] 3842048 512-byte hardware sectors (1967 MB)
[ 2281.471029] sd 4:0:0:2: [sdd] Write Protect is off
[ 2281.471031] sd 4:0:0:2: [sdd] Mode Sense: 03 00 00 00
[ 2281.471033] sd 4:0:0:2: [sdd] Assuming drive cache: write through
[ 2281.471652] sd 4:0:0:2: [sdd] 3842048 512-byte hardware sectors (1967 MB)
[ 2281.472397] sd 4:0:0:2: [sdd] Write Protect is off
[ 2281.472399] sd 4:0:0:2: [sdd] Mode Sense: 03 00 00 00
[ 2281.472401] sd 4:0:0:2: [sdd] Assuming drive cache: write through
[ 2281.472405]  sdd: sdd1
[ 2281.763665] nautilus[13648]: segfault at 19 ip 00000019 sp bfe5447c error 4 in nautilus[8048000+140000]

Is there a bugreport for this?

---

### Post by LordVeovis on 2009-01-08
I can say will 100% certainty that this is not the only time nautilus crashes.  I have been home 2 hours and it has crashed.  At no point did I mount / unmount anything, nor put any external media in the PC.

EDIT: Here is my dmesg:
```
[  130.495703] wlan0: RX AssocResp from 00:1e:e5:41:6c:d5 (capab=0x401 status=0aid=2)
[  130.495706] wlan0: associated
[  130.495913] wlan0: disassociating by local choice (reason=3)
[  461.173834] nautilus[4821]: segfault at 148a2e8 ip 000000000148a2e8 sp 00007fff3e7a0b88 error 15
```

/var/log/messages
```

Jan  8 19:24:13 ubuntu kernel: [  115.250393] usb 4-1.2: configuration #1 chosen from 1 choice
Jan  8 19:24:13 ubuntu kernel: [  115.301731] Bluetooth: Generic Bluetooth USB driver ver 0.3
Jan  8 19:24:13 ubuntu kernel: [  115.301885] usbcore: registered new interfacedriver btusb
Jan  8 19:24:25 ubuntu kernel: [  127.542090] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 19:25:58 ubuntu pulseaudio[4856]: module-alsa-sink.c: Increasing wakeup watermark to 40.00 ms
Jan  8 19:27:31 ubuntu sudo: pam_sm_authenticate: Called
Jan  8 19:27:31 ubuntu sudo: pam_sm_authenticate: username = []
Jan  8 19:27:31 ubuntu sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Jan  8 19:27:31 ubuntu sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Jan  8 19:27:31 ubuntu sudo: Passphrase key already in keyring
Jan  8 19:27:31 ubuntu sudo: There is already a key in the user session keyringfor the given passphrase.
Jan  8 19:29:59 ubuntu kernel: [  461.173834] nautilus[4821]: segfault at 148a2e8 ip 000000000148a2e8 sp 00007fff3e7a0b88 error 15
Jan  8 19:42:39 ubuntu sudo: pam_sm_authenticate: Called
Jan  8 19:42:39 ubuntu sudo: pam_sm_authenticate: username = []
Jan  8 19:42:39 ubuntu sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Jan  8 19:42:39 ubuntu sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Jan  8 19:42:39 ubuntu sudo: Passphrase key already in keyring
Jan  8 19:42:39 ubuntu sudo: There is already a key in the user session keyringfor the given passphrase.

```

EDIT: I have an encrypted file system, perhapse that is the pam_sm related messages?  Any idea what the errors mean?

Also I have not posted this on launchpad.  I take it no one else has?

---

### Post by ShirishAg75 on 2009-01-08
post it, atleast you would have had.

---

### Post by autocrosser on 2009-01-08
I would look at Launchpad with an eye towards nautilus segfaults...I remember last cycle having that problem, don't remember the fix right now, but the problem persisted for a couple of weeks (might have been Gutsy instead of Intrepid--)

---

### Post by tawmas on 2009-01-09
Awful.

For a while, this thread didn't work well for me. I wasn't subscribed for new post notification. I'm going to look in Launchpad if something is already reported (I recall seeing another thread here mentioning Nautilus crashes) and will report mine if I cannot find anything relevant.

I'll keep you posted.

---

### Post by tawmas on 2009-01-09
Filed [315373]("https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/315373")

---

### Post by ShirishAg75 on 2009-01-09
tawnas, please put up debugging symbols of libhal as well as gvfs as asked in the bug-report and rerun the whole thing again.

---

### Post by tawmas on 2009-01-09
> **ShirishAg75 said:**
> tawnas, please put up debugging symbols of libhal as well as gvfs as asked in the bug-report and rerun the whole thing again.

I've just done that, but there was a surprise: with libhal and gvfs symbols installed I cannot reproduce the crashes.

Installing the -dbgsym packages removed a lot of -dbg packages. This looks crazy to me, but what do I know? I think the problem could be in one of those -dbg packages, because I didn't do any other updates in the meanwhile.

Thinking twice about what I did:
1) This morning I updated, saw the crash was still present and filed my bug
2) I was asked so install nautilus-dbgsym, did so, and the bug crash was still there
3) I turned off my PC and went away
4) When I came back, I turned on my PC again, installed libhal1-dbgsym and gvfs-dbgsym as asked, and no more crashes.

So, it could well be the restart after the updates...

Can anybody check if udating to hal 0.5.12~rc1-0ubuntu4 and restarting fixes this? If not, can anybody check if installing the menioned -dbgsym packages fixes this for them?

---

### Post by ShirishAg75 on 2009-01-09
There is always a choice, either use -dbg or -dbgsym, never both. I read somewhere they don't play nice with each other. 

On the issue you are having, I don't have it so sorry.

---

### Post by LordVeovis on 2009-01-09
> **tawmas said:**
> I've just done that, but there was a surprise: with libhal and gvfs symbols installed I cannot reproduce the crashes.

Installing the -dbgsym packages removed a lot of -dbg packages. This looks crazy to me, but what do I know? I think the problem could be in one of those -dbg packages, because I didn't do any other updates in the meanwhile.

Thinking twice about what I did:
1) This morning I updated, saw the crash was still present and filed my bug
2) I was asked so install nautilus-dbgsym, did so, and the bug crash was still there
3) I turned off my PC and went away
4) When I came back, I turned on my PC again, installed libhal1-dbgsym and gvfs-dbgsym as asked, and no more crashes.

So, it could well be the restart after the updates...

Can anybody check if udating to hal 0.5.12~rc1-0ubuntu4 and restarting fixes this? If not, can anybody check if installing the menioned -dbgsym packages fixes this for them?

As of this morning on my way to work I still had the porblem.  I ran the latest updates before I left too.  Did not reboot though.  Once I am home I will see.  Have you noticed the icons going away at other points as well?  As I mentioned I am 100% sure that the crash is not only from new media.

---

### Post by tawmas on 2009-01-09
> **ShirishAg75 said:**
> There is always a choice, either use -dbg or -dbgsym, never both. I read somewhere they don't play nice with each other. 

On the issue you are having, I don't have it so sorry.

The -dbg packages were installed automatically during the upgrade from Intrepid to Jaunty. I don't know if and how they differ from the -dbgsym.

What is the issue you don't have? The crashes on media insertion?

> **LordVeovis said:**
> As of this morning on my way to work I still had the porblem.  I ran the latest updates before I left too.  Did not reboot though.  Once I am home I will see.  Have you noticed the icons going away at other points as well?  As I mentioned I am 100% sure that the crash is not only from new media.

Yes, please, let me know.

As for the reasons of crashes, I didn't see any other crashes except from removable media, but then my system is a desktop and the only "elements" changing at runtime are removable media. Since the crash is related to libhal, I guess that any other hal event could trigger a crash -- for example, and please bear in mind that this is just a wild guess, switching the wifi radio on or off etc...

---

### Post by ShirishAg75 on 2009-01-10
> **tawmas said:**
> The -dbg packages were installed automatically during the upgrade from Intrepid to Jaunty. I don't know if and how they differ from the -dbgsym.

There is a difference, either have all the -dbg or all -dbgsym don't try to mix them up. 

[quote=tawmas]
What is the issue you don't have? The crashes on media insertion?[/quote]

Both neither crashes on media insertion. I have both an external USB thumbdrive as well as an external USB HDD. 

The interface is though 1.1 so don't know if that makes a difference or not. 

<snip>

---

### Post by LordVeovis on 2009-01-10
> **tawmas said:**
> 

Yes, please, let me know.

As for the reasons of crashes, I didn't see any other crashes except from removable media, but then my system is a desktop and the only "elements" changing at runtime are removable media. Since the crash is related to libhal, I guess that any other hal event could trigger a crash -- for example, and please bear in mind that this is just a wild guess, switching the wifi radio on or off etc...

Ok, the crash still was happening.  I just today installed the gvfs-dbgsym=1.1.3-0ubuntu2 package so I could backtrace and then it stopped crashing on me.  I dont know what fixed it.

---

### Post by ronacc on 2009-01-10
someone who's icons disapearing has been "cured" please try this , using nautilus browse to /usr/share/applications and see if that crashes nautilus , I was not having a problem with the Icons disapearing until I did that  , that causes nautilus to crash , the icons to disapear and the desktop to become unresponsive to clicks although the pannels still work ,  installing the -dbgsym's did not help , sudo killall nautilus does not help , running nautilus from term brings the icons back until you close it , then they disapear again .

---

### Post by ShirishAg75 on 2009-01-10
> **ronacc said:**
> someone who's icons disapearing has been "cured" please try this , using nautilus browse to /usr/share/applications and see if that crashes nautilus , I was not having a problem with the Icons disapearing until I did that  , that causes nautilus to crash , the icons to disapear and the desktop to become unresponsive to clicks although the pannels still work ,  installing the -dbgsym's did not help , sudo killall nautilus does not help , running nautilus from term brings the icons back until you close it , then they disapear again .

ronacc, this process/procedure has got my desktop icons disappearing, so let's get the -nautilus-dbgsym and file a bug with the results.

Ok, have put up [lpbug]315983[/lpbug]

Would also try Valgrind and see what the issue might be.

---

### Post by ronacc on 2009-01-11
installed nautilus-dbgsym and ran backtrace , attached same to your bug report , you go there first :)

---

### Post by LordVeovis on 2009-01-11
This happened to me as well.  Great job narrowing it down so far guys!!

---

### Post by LordVeovis on 2009-01-11
> **ShirishAg75 said:**
> ronacc, this process/procedure has got my desktop icons disappearing, so let's get the -nautilus-dbgsym and file a bug with the results.

Ok, have put up [lpbug]315983[/lpbug]

Would also try Valgrind and see what the issue might be.

Why did you post a new bug, we had a report in already....

---

### Post by ronacc on 2009-01-11
didn't know it was the same bug since I was not having disapearing icons until I happened to browse to /usr/share/applications.

---

### Post by ShirishAg75 on 2009-01-11
you never know if its same bug or shares symptons. Let the devs figure out if its one and the same bug or not.

---

### Post by LordVeovis on 2009-01-11
> **ronacc said:**
> didn't know it was the same bug since I was not having disapearing icons until I happened to browse to /usr/share/applications.

Oh, my mistake.

---

### Post by tawmas on 2009-01-11
**ronacc**, **shirish**, are you on 32 or 64 bits?

---

### Post by tawmas on 2009-01-11
> **ronacc said:**
> didn't know it was the same bug since I was not having disapearing icons until I happened to browse to /usr/share/applications.

This doesn't look like the same bug. It crashes in a totally different function, and it's not cured by installing the -dbgsym packages (I've just replicated it as well).

---

### Post by ShirishAg75 on 2009-01-11
I'm on 32 bits.

---

### Post by ronacc on 2009-01-11
64bit here . I wonder why that particular dir , thats the only one I've stumbled on so far .

---

### Post by tawmas on 2009-01-11
> **ronacc said:**
> 64bit here . I wonder why that particular dir , thats the only one I've stumbled on so far .

I think it's one of the files in there. I will try to narrow it down later this afternoon.

---

### Post by tawmas on 2009-01-11
Got it! I can get a crash with this:

```
mkdir ~/test
cp /usr/share/applications/compiz.desktop ~/test/
nautilus ~/test
```

I'm going to leave a comment in the bug.

---

### Post by ronacc on 2009-01-11
whatever it is it seems confined to nautilus , browsing to /usr/share/applications does not crash krusader,MC ,dolphin or emelFM2 .

---

### Post by ronacc on 2009-01-11
it looks like you found the problem , I used dolphin to copy /usr/share/applications/compiz.desktop to my ~/tmp dir and then deleted it from  /usr/share/applications and now nautilus will go there without crashing .

EDIT:  yes definately that file (compiz.desktop) now if I use nautilus to browse to my ~/tmp dir it crashes .

---

### Post by LordVeovis on 2009-01-11
I'm on 64 as well.  So both 32 and 64 looks to have this issue.

---

### Post by tawmas on 2009-01-11
Ok, so one's narrowed down.

I'd like to reinstall the -dbg packages to see if I can replicate again the crashes on media insertion, but I don't know how to proceed. A bunch of these were uninstalled automatically and I didn't keep note of which.

Suggestions, anybody?

I've already reinstalled gnome-dbg, hoping it would bring back the whole lot as dependencies, but it wasn't so.

---

### Post by LordVeovis on 2009-01-11
> **tawmas said:**
> Ok, so one's narrowed down.

I'd like to reinstall the -dbg packages to see if I can replicate again the crashes on media insertion, but I don't know how to proceed. A bunch of these were uninstalled automatically and I didn't keep note of which.

Suggestions, anybody?

I've already reinstalled gnome-dbg, hoping it would bring back the whole lot as dependencies, but it wasn't so.

I think I may try to install jaunty 32 to my laptop (as NVIDIA isn't working nicely at the moment anyways with 8.10 on it) and I wont have any of the debuggin packages and I will try to reconfirm

---

### Post by tawmas on 2009-01-11
> **LordVeovis said:**
> I think I may try to install jaunty 32 to my laptop (as NVIDIA isn't working nicely at the moment anyways with 8.10 on it) and I wont have any of the debuggin packages and I will try to reconfirm

Thanks, that might be easier, although it looks like everybody having this bug is on 64 bits.

---

### Post by ronacc on 2009-01-11
I'm not getting the crash on media insertion here , either usbstick or dvd , mabye that is a 32bit thing .
 woops just read your last post , I am on 64bit and am not getting the media insertion crashes.

---

### Post by tawmas on 2009-01-11
> **ronacc said:**
> I'm not getting the crash on media insertion here , either usbstick or dvd , mabye that is a 32bit thing .
 woops just read your last post , I am on 64bit and am not getting the media insertion crashes.

I'm on 64 bits... In fact, I thought it could be a 64 bit thing before learning you were on 64 bits as well.

---

### Post by LordVeovis on 2009-01-11
I am D/Ling the 32 bit now, will take about 10 min. 10Mbps is nice

Also is there any difference in your installation ronacc?

I installed via the alternate CD.

---

### Post by ronacc on 2009-01-11
I installed from the dec 31 alternate (64bit) I have since added a bunch of stuff but I dont think any of it would affect this ( only possibly K3B brasero sucks ) .

---

### Post by LordVeovis on 2009-01-11
> **ronacc said:**
> I installed from the dec 31 alternate (64bit) I have since added a bunch of stuff but I dont think any of it would affect this ( only possibly K3B brasero sucks ) .

Hmm.. Perhaps this is chipset related then.  Maybe we can look at the difference in our chipsets?  I think I will have to browse ASUS's board to see the type of chipset I have.  Is this worth a look at?

---

### Post by ronacc on 2009-01-11
I don't see how it could be chipset related if it affects both cd/dvd's and usbsticks but for reference my mobo is a gigabyte ga-m55plus-s3g rev2.1 and the cd/dvd drive is ide .

---

### Post by LordVeovis on 2009-01-11
I was thinking chipset because all removable media is controlled by 1 chip (I believe)  I tried this on my laptop and cannot reproduce.

EDIT: Going to /usr/share/applications does not crash nautilus either.

---

### Post by ronacc on 2009-01-11
do you have compiz installed ? that file (compiz.desktop) would probably only exist if you had compiz enabled . atleast I think its that way .

---

### Post by ShirishAg75 on 2009-01-11
ronacc, you forgot to tell whom you are addressing?

---

### Post by ronacc on 2009-01-11
I was addressing LordVeovis , the post immeadiately above mine .

---

### Post by LordVeovis on 2009-01-11
> **ronacc said:**
> do you have compiz installed ? that file (compiz.desktop) would probably only exist if you had compiz enabled . atleast I think its that way .

It is there, the file that is.  I ran all the updates then I was able to reproduce.  It seems it is in one of the updates.  Also after I went to the folder and it crashed nautilus (which did restart on its own) it no longer auto detected my flash drive being added.

EDIT: Also compiz is not enabled and it was crashing by viewing that folder.  I don't even have the nvidia restricted driver enabled... completely bare install with only the updates run.

---

### Post by LordVeovis on 2009-01-11
Ok, rebooted so it would recognise flash drive again and it did not cause a crash.  Navigated back to /usr/share/applications and it crashed again and did not reload nautilus.  However after I manually loaded nautilus again and inserted my flash drive it was recognised as it should have been the prior time.

---

### Post by ronacc on 2009-01-12
since updates last night it takes a long time of holding the button on my dvd drive to get it to open the drawer and then closes it as soon as the button is released , media insertion does not crash the system .

---

### Post by LordVeovis on 2009-01-12
I will try to reproduce when I get back home myself.  I can't get media crash anymore though because I installed the debugging packages.  But I should still get the cd drive problem.

---

### Post by tawmas on 2009-01-12
> **ronacc said:**
> since updates last night it takes a long time of holding the button on my dvd drive to get it to open the drawer and then closes it as soon as the button is released , media insertion does not crash the system .

Ugh! I had something like this before the crashes started. I seem to recall there was a forum thread and a bug report for this, which got fixed.

I'm just back from work and about to run the updates, let's see what happens.

---

