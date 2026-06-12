---
title: "Bad USB Port(s) Cause of Jaunty Crashes?"
date: 2008-12-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LaneLester on 2008-12-25
Ubuntu Intrepid runs just fine, but Jaunty Alpha 2 crashes fairly often (yes, I know). Another distro, Puppy Linux, also has crashes with the new *release* version.

These crashes seem to be related to USB activity, either the Logitech trackball or the Oregon WMR-200 weather station.

No one else in the Puppy Linux community is reporting this problem, and a search on here did not turn up any similar reports.

Since these crashing OSes have newer kernels, I'm wondering if there is some problem with them and the USB 2.0 ports on my several-years-old HP box.

I'm not eager to buy a new computer, but I would like to know if this one is not going to be able to keep up with Linux advances. Is there a way I can test the USB ports?

Lane

---

### Post by ronacc on 2008-12-25
well the obvious way would be to unplug those devices and see if the crashes go away , I had a mouse that was dying that crashed hardy 1 0r 2 times a day , I replaced it with the same make and model and no crashes, so it wasn't the port but the device itself that was causing the problem , since no one else seems to be reporting the problem that may be your case also .

---

### Post by LaneLester on 2008-12-25
Thanks, ronacc, for the suggestions. I did try a separate trackball of the same model and also got the crashes when clicking the trackball button. And I get them if I'm not at the computer, but the weather sotware is running and accessing the USB port continually.

The fact that the crashes do not occur with Intrepid makes me wonder if there's something conflicting between the computer's USB ports (chip, whatever) and the newer kernels.

That's why I'm interested in a program or some other way to check the computer's USB support.

Lane

---

### Post by ronacc on 2008-12-25
in another thread there is something about mouse speed and sensitivity problems with firefox maybe this is a symptom of the same thing , just for grins try setting your mouse (trackball) speed down just a little and mabye playing with your double click delay .

---

### Post by LaneLester on 2008-12-25
> **ronacc said:**
> in another thread there is something about mouse speed and sensitivity problems with firefox maybe this is a symptom of the same thing , just for grins try setting your mouse (trackball) speed down just a little and mabye playing with your double click delay .
OK, I'll give it a try (I'm replying in Intrepid so a crash doesn't get me too soon). But the fact that it crashes when I'm not at the computer and only the weather software is cooking makes it more than a mouse problem, I think.

Lane

---

### Post by ronacc on 2008-12-25
since we don't have much to go on I'm just throwing out ideas , I was thinking more of "input event" than mouse specificly and was thinking that maybe the input handler is interpeting something that the weather station does  as a mouse event what video driver are you using ? the problems with FF and mouse speed seem related to the Nvidia 180.16 driver , also anything in your /home/you/.xsession-errors ? or your system log ?

---

### Post by a fenderson on 2008-12-25
I'm getting crashes whenever I try to use the multimedia keys on my USB keyboard (Logitech Elite), could this be related?

---

### Post by ronacc on 2008-12-25
it certaily could be but without more info it is impossible to tell .

---

### Post by LaneLester on 2008-12-26
> **ronacc said:**
> since we don't have much to go on I'm just throwing out ideas , I was thinking more of "input event" than mouse specificly and was thinking that maybe the input handler is interpeting something that the weather station does  as a mouse event what video driver are you using ? the problems with FF and mouse speed seem related to the Nvidia 180.16 driver , also anything in your /home/you/.xsession-errors ? or your system log ?
OK, ronacc, now I understand your thinking. And you may have something: I set the mouse acceleration and sensitivity to half their default settings. I did a bunch of surfing without incident, and then I left the computer on last night with the weather software running. The system was still up this morning, whereas it had crashed overnight before.

I have an nVidia 5500 card, but I don't don't know if I'm using a proprietary driver. xorg.conf is a zero-byte file. 'locate nvidia' shows a lot of nvidia stuff, including the following: 
[INDENT]/usr/share/app-install/desktop/nvidia-driver-173.desktop
/usr/share/app-install/desktop/nvidia-driver-177.desktop
/usr/share/app-install/desktop/nvidia-driver-71.desktop
/usr/share/app-install/desktop/nvidia-driver-96.desktop[/INDENT]

I don't know how to see what driver I'm using or how to install a different one.

.xsession-errors is about a 40K file, and I had to zip it to attach it. /var/log/syslog shows a lot of stuff like the first three lines of the following bottom of the file:
[INDENT]Dec 26 07:00:01 PC1 /USR/SBIN/CRON[3037]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 26 07:00:01 PC1 /USR/SBIN/CRON[3040]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Dec 26 07:10:01 PC1 /USR/SBIN/CRON[3597]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 26 07:12:39 PC1 kernel: [38945.186195] ppdev0: registered pardevice
Dec 26 07:12:39 PC1 kernel: [38945.232036] ppdev0: unregistered pardevice
Dec 26 07:12:40 PC1 kernel: [38946.648556] ppdev0: registered pardevice
Dec 26 07:12:40 PC1 python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Dec 26 07:12:40 PC1 kernel: [38946.696203] ppdev0: unregistered pardevice
Dec 26 07:12:41 PC1 kernel: [38947.890167] ppdev0: registered pardevice
Dec 26 07:12:42 PC1 hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Dec 26 07:12:42 PC1 kernel: [38947.936265] ppdev0: unregistered pardevice
Dec 26 07:17:01 PC1 /USR/SBIN/CRON[3964]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 26 07:20:01 PC1 /USR/SBIN/CRON[4146]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)[/INDENT]

Lane

---

### Post by ronacc on 2008-12-26
If you did not take some action to activate a propriatary driver you probably aren't using one . you can check by going to system>administartion>hardware drivers and that will show which ones are available ( the ones you found with locate ) and if one is in use it will be marked . I don't think that 0 byte xorg.conf is right , in jaunty it should be very minimal but I don't think 0 bytes . But leave things as they are for awhile and lets see if the crashes stay gone . If we make too many changes we won't know which did what . That part you posted from .xsession-errors has to do with your paralell port, do you have a printer or scanner on that port ? anyway I don't think that has anything to do with the crashes.

---

### Post by LaneLester on 2008-12-26
> **ronacc said:**
> If you did not take some action to activate a propriatary driver you probably aren't using one . you can check by going to system>administartion>hardware drivers and that will show which ones are available ( the ones you found with locate ) and if one is in use it will be marked.
The hardware drivers utility shows none available, which seems strange. I'm attaching a relevant part of the synaptic window.

> I don't think that 0 byte xorg.conf is right , in jaunty it should be very minimal but I don't think 0 bytes . But leave things as they are for awhile and lets see if the crashes stay gone . If we make too many changes we won't know which did what .
Yes, that's my usual experience: change a bunch of things, problem fixed, but nothing learned.

> That part you posted from .xsession-errors has to do with your paralell port, do you have a printer or scanner on that port ? anyway I don't think that has anything to do with the crashes.
No, no printer or other parallel device attached.

Lane

---

### Post by LaneLester on 2008-12-26
I copied my xorg.conf from my Intrepid partition, but Jaunty complained that the "nvidia" driver wasn't installed. So I changed it to "nv" and I have video again.

I read online that Jaunty is using a new Xorg system, and I see some others have reported the zero-byte xorg.conf. I also read that there is a new GUI xorg config program being developed for Jaunty. So maybe I just have to wait for things to catch up.

I bought this old nVidia (5500) card for Linux, but it looks like another brand would have been better.

Lane

---

### Post by ronacc on 2008-12-26
Nvidia cards play well with linux, jaunty is a developement alpha so things don't always go smoothly. I wasn't aware of the 0 byte xorg.conf though I had seen the short ones , the new xorg is supposed to be autoconfig so it doesn't need an xorg.conf but will use one if it's there ,just putting in your intrepid xorg.conf doesn't activate the Nvidia driver you still need to go to the pannel , system>administration>hardware drivers and select the one you want there that it is showing none of the ones that synaptic is showing installed may mean something isn't built yet, this is a dev version ,you should get a notification in the pannel notification area when a driver is available the 173.xx.xx driver is the nvidia recomends for your card go to synaptic and see if it will install (nvidia-glx-173) then it should become available . You probably want to return to the 0 byte xorg.conf and let the system handle things , just rename your intrepid xorg.conf (say to xorg.confi ) and make a 0 byte text file xorg.conf if you haven't already got one that way your intrepid one will be handy if you want to try it later . Once the driver is activated in order to get compiz if you want it  go to system>preferences>appearence>visual effects and enable extra.

---

### Post by LaneLester on 2008-12-26
Well, I broke it. :)

I returned xorg.conf to zero bytes and then tried to install the 173 driver with synaptic. Unfortunately, it wanted to delete 42 packages along with adding 6. Most of them were video drivers for other cards, so I went ahead and let it fly.

Oops! No more X! So I booted to a recovery terminal and let aptitude install both xorg and xserver. But still no joy.

It looks like a full reinstall will be needed to get me going again. I'll do it, but I'll put off trying to do real work until things get further along.

I might mention that I moved the weather station to another computer in order to simplify things. And I discovered that, even with the slowed down mouse, I had repeated crashes when I was doing some heavy mousing in OpenOffice.

**Later:** I have Jaunty installed again. I saved a bunch of files from the old install, so it didn't take much to get going again. But with the inability to install the 173 driver without uninstalling the stuff needed to use it (strange!), I think I'm stuck as far as that approach goes.

Lane

---

### Post by ronacc on 2008-12-26
always be very careful when something wants to remove a whole bunch of stuff , especialy in a dev version its easy to end up with an unuseable system .It might be better for you to wait for  alpha 3 or 4 and watch this forum for nvidia discussions to see when the current problems are resolved , nvidia cards play well with linux but the 3d accelerated drivers are propriatary and it takes awhile for them to catch up to a new kernal or xorg sometimes .

---

### Post by Gina on 2008-12-26
> if it ain't broke you haven't tweaked it enough Broke mine too and it only wanted to remove nvidia-180 but now have no display at all.  Tried installing nvidia stuff etc with apt-get but no joy.  I'll be watching and will try a daily build when it looks promising.  That's on the AMD64 - Jaunty is still running fine on my 32 bit laptop and ATI mobility 200 graphics.

---

### Post by LaneLester on 2008-12-26
Yes, I'll keep letting Synaptic bring me up to date, and I feel sure we'll the nVidia stuff come around. I have Compiz running fine with this machine and Ubuntu Intrepid.

My understanding is that the use of Synaptic (or however one wishes to keep the packages up to date) will upgrade a system through the versions all the way into the release version. If that's incorrect, please correct me!

Ah, the AMD64! Gina, my main machine is an HP with that chip, and I'd love to run a 64-bit OS on it... just because I could. But whenever I've tried it, there was always one or more programs that I had to have which wouldn't run in 64 bits.

Lane

---

### Post by ronacc on 2008-12-26
I haven't cratered mine (yet) but then I'm running a hand installed 180.16 and custom xorg.conf guess I'll wait awhile before changing back to dkms , it worked great in intrepid I have faith they'll get it up to speed here , then of course we may have the .29 kernel waiting in the wings .:P

---

### Post by LaneLester on 2008-12-26
I've seen only two driver entries in xorg.conf: nv and nvidia. Yet there is quite a number of nVidia driver versions. What controls which actual version gets referred to by "nvidia"?

Lane

---

### Post by autocrosser on 2008-12-26
Lane: nvidia is just a generic term for whatever nvidia driver is linked to it--all depends on what Jockey or synaptic installs---right now anything older that the 8xxx cards series is broken with the new version of Xorg--if you were to up to a newer card you could use the driver that Alberto made--180.16 from the PPA I referenced in the broken xorg thread.....


Gina: Did you try the driver I referenced? Have not had any problems with it--Alberto is planning to update it as soon as things are stable with Xorg--couple of weeks (shrug?)--in any case you need to do the "no ABI" fix & then D/L the driver--restart xorg--post back if that is not a fix & I'll see where Alberto is with the current beta driver.......

---

### Post by ronacc on 2008-12-26
the entry in xorg.conf controls which driver is loaded ( possible choices vesa ,nv,nvidia ) if you set it to nvidia you need to have one of the nvidia-glx drivers installed and enabled in system>administration>hardware drivers  the one you have enabled will be the one that is loaded there is also an opensource nvidia driver called nouveua that is under heavy developement , I haven't tried that one yet .even if you have a driver set in xorg.conf that does't exist X is suposed to fail to low graphics mode ( vesa ) and atleast give you a working if horrible looking desktop unless something is really borked . the nv driver is a step up from vesa , no 3d accel but at least you will probably be able to get a decent resolution  800x600 sucks on a 1440 0r 1680 WS

---

### Post by Gina on 2008-12-27
> **autocrosser said:**
> Gina: Did you try the driver I referenced? Have not had any problems with it--Alberto is planning to update it as soon as things are stable with Xorg--couple of weeks (shrug?)--in any case you need to do the "no ABI" fix & then D/L the driver--restart xorg--post back if that is not a fix & I'll see where Alberto is with the current beta driver.......I'll look into that - thank you :)

---

### Post by ronacc on 2008-12-27
@ autocrosser Thanks for the info about the Nvidia drivers for earlier cards being broken . 
@ lanelester I guess you need to stick with the nv driver for awhile yet , Like I said earlier , in a dev version like jaunty is now sometimes things get out of sync and it takes awhile for the propriatary drivers from Nvidia to catch up .

---

### Post by plun on 2008-12-27
> **ronacc said:**
> @ autocrosser Thanks for the info about the Nvidia drivers for earlier cards being broken . 
@ lanelester I guess you need to stick with the nv driver for awhile yet , Like I said earlier , in a dev version like jaunty is now sometimes things get out of sync and it takes awhile for the propriatary drivers from Nvidia to catch up .

Well... I cannot verify it myself but the beta driver should work for 5XXX cards..  **173.14.15**  

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

But must be installed in recovery mode (tty still broken)  and ignoreABI option within xorg.conf.  (the same as with the 180 driver)

---

### Post by ronacc on 2008-12-27
@plun I wasn't sure I wanted to try to "walk him through" a self compile of one of the Nvidia drivers thats why I didn't mention it . and yes the 173.14.15 should be right for his 5500 , thats the one I'm using on my "stable" box (hardy) with an fx5200 card .

---

### Post by plun on 2008-12-27
> **ronacc said:**
> @plun I wasn't sure I wanted to try to "walk him through" a self compile of one of the Nvidia drivers thats why I didn't mention it . and yes the 173.14.15 should be right for his 5500 , thats the one I'm using on my "stable" box (hardy) with an fx5200 card .

Yup... just a sad situation...:(

A neighbor just came in with Windows 7 Beta....:^o](*,)](*,)](*,)

---

### Post by Gina on 2008-12-27
> **plun said:**
> yup... Just a sad situation...:(

a neighbor just came in with windows 7 beta....:^o](*,)](*,)](*,)aaarrrgghh :(:(

---

### Post by plun on 2008-12-27
> **Gina said:**
> aaarrrgghh :(:(

Yup... Ubuntu should just be fun without limitations...:lolflag:

Windows 7....
[http://www.winsupersite.com/win7/win7_beta_screens_01.asp](http://www.winsupersite.com/win7/win7_beta_screens_01.asp)


So Alberto... where are the drivers ?.. or what where Ubuntu doing at UDS ???  Telling everyone thats the Fedora way is fun...:confused::confused::confused:

Sad, Sad, Sad.... :(

---

### Post by Gina on 2008-12-27
Windows 7 looks almost as much of a pain to install as XP :lolflag:  I wouldn'twant to do all that too often!!

---

### Post by autocrosser on 2008-12-27
> **plun said:**
> Yup... just a sad situation...:(

A neighbor just came in with Windows 7 Beta....:^o](*,)](*,)](*,)


Barf-----I sign my life & worldly goods to the great god Microsoft:P

---

### Post by autocrosser on 2008-12-27
> **plun said:**
> Yup... Ubuntu should just be fun without limitations...:lolflag:

Windows 7....
[http://www.winsupersite.com/win7/win7_beta_screens_01.asp](http://www.winsupersite.com/win7/win7_beta_screens_01.asp)


So Alberto... where are the drivers ?.. or what where Ubuntu doing at UDS ???  Telling everyone thats the Fedora way is fun...:confused::confused::confused:

Sad, Sad, Sad.... :(

Yes--Alberto has been quiet about it--I would guess that he is waiting for the final drivers before releasing--And of course, this time of years slows that sort of thing down quite a bit........I could ask if he could include the other card betas, but that will increase his workload a fair amount------

---

### Post by ronacc on 2008-12-27
@ Plun we all know the situation with dev versions and thats why were here , for the fun :lolflag: a few days ago I did a fresh install of intrepid on a box that suffered a mobo failure and it was answer about 4 questions and come back a few minutes later and eject the dvd and boot the new install , job done .

---

### Post by LaneLester on 2008-12-28
I now have another observation that points the finger at the video driver as the probable culprit.

Another distro I'm playing with is Puppy Linux, and recent releases have been crashing in a similar fashion to those I'm experiencing in Jaunty. Another Puppy user made it easy to install the nVidia 173 driver, and the crashes went away.

So I have every hope that the Jaunty problem will also clear up when the driver needed for my nVidia 5500 card becomes available. I'll keep updating Jaunty with Synaptic and watching this forum for further developments.

Lane

---

