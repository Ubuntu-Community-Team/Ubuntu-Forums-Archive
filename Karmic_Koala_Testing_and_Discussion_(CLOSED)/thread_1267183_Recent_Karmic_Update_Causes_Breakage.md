---
title: "Recent Karmic Update Causes Breakage"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by brandoncolorado on 2009-09-15
I have been using the 9.10 netbook remix for quite a while now.  It has worked wonderfully.  Today the upgrade manager asked to do a "partial upgrade," and I went ahead with that upgrade.  Everything seemed to work smoothly.  During the update, the manager asked me if I want to keep my old configuration file (for something like CUPSD) and I said to take the new one.

Now, upon reboot, I see the loading bar until it finishes.  After that, I see a black screen.  If I hit a key, I am shown the terminal login prompt.  I can login and it just leaves me there.

1)  What could be wrong?

2)  How can I boot in a mode where I can tell what is happening?

3)  What terminal command to start the GUI?

Sorry for the rookie questions.

[color=darkred]bodhi.zazen: Such is the nature of running an Alpha =) 

I am sorry there were problems with this update, I also was affected. Please note: This affects both updating an existing system and the Alpha 6 CD. There are several "fixes" posted in this section but be warned, they do not always work.

Hopefully the problem will be solved soon.[/color]

---

### Post by sergkop on 2009-09-15
I also have the same problem on my laptop.

---

### Post by paulmerchant on 2009-09-15
Karmic died on my laptop right after recommended updates today, too. I get a black screen even if I boot in safe mode (although I can blindly go to a prompt and, without a working display, blindly try upgrades and fixes. When I boot in normal mode, the GUI login shows, but I have no mouse or keyboard support.

My guess is that some of the initialization scripts are extremely buggy or weren't upgraded correctly. I could probably figure a little more out if I could get to a Karmic prompt where I could see something.

Anyone know what we can do?

[By the way, I didn't mean to hijack this thread. I just reread the first post and my problem is different.]

---

### Post by slakkie on 2009-09-15
See the karmic subforums, more people have a b0rked system (myself included).

---

### Post by ramsayeg on 2009-09-15
Same here on my laptop, Ubuntu dies after the loading screen fades away. There's the following error:

*Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory*

I use a regular Karmic installation.

---

### Post by LaDeuce on 2009-09-15
> **ramsayeg said:**
> 
*Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory*

I am experiencing this as well.

---

### Post by TunaCanTommy on 2009-09-15
Don't mean to jump on a "me-too" band-wagon, but I've had the same experience with today's update.  After the update I did a reboot and got a blank screen right after the Ubuntu logo started.

I have Karmic NBR (9.10) loaded on my EeePC 701/4G and it was really working great . . I was kinda proud of myself.

After it broke I was still able to boot off the Live CD - in this case a USB thumbdrive, and it booted and ran fine.  Just can't get the installed version running.

Hoping someone may have a solution . . . !

---

### Post by brandoncolorado on 2009-09-15
> **LaDeuce said:**
> I am experiencing this as well.

As the OP here, I just want to mention that this is my problem as well.  For anyone in the same situation, boot until you see GRUB mentioned, boot into the latest kernel in recovery mode, and then you should see this error as well.

---

### Post by taur on 2009-09-15
Me too on my desktop, however using
the (recovery mode) option (crashes at the same spot),
I get dropped to a frozen shell in which I can read:

```
waiting for resume device ...
mount: mounting /dev/disk/by-uuid/a1310172-8bc8-47cc-8497-040321b02fdd on /root
failed: Device or resource busy
```

This is with the 2.6.31-10 kernel,
the other ones gets past this part just fine.

I hope someone can make something out of it.

---

### Post by brandoncolorado on 2009-09-15
I will file a bug report if someone could help me figure out which package this problem derives from.

---

### Post by Citizen_Kane01 on 2009-09-15
Same problem here!

Tried restarting from the recovery mode menu and was offered a verbose process list.

Mine seems to hang at 'winbind daemon', whatever that may be.

---

### Post by Ric_NYC on 2009-09-15
The same issue here.
I was about to re-install Ubuntu because I thought I did something wrong when I updated my system.
then I found this new thread


Waiting for the solution.... PLEASE!

---

### Post by Ric_NYC on 2009-09-15
Should we post a warning in the "Community Cafe" asking people not to install the new update?

---

### Post by rolfc on 2009-09-15
seem to me as if /dev/pts disappeared. Anyone know how to recreate it?

---

### Post by tmschmitz on 2009-09-15
I got in by creating the directory /var/run/dbus, then ran dbus-daemon --system, then ran hald, and start gdm.  I also had to start my networking manually.  Upon reboot, the dbus directory is no longer in /var/run, so the whole thing begins again.

---

### Post by brandoncolorado on 2009-09-15
> **Ric_NYC said:**
> Should we post a warning in the "Community Cafe" asking people not to install the new update?

That is probably a good idea.  This could cause quite a few headaches if the solution is not easy.

---

### Post by useResa on 2009-09-15
> **ramsayeg said:**
> Same here on my laptop, Ubuntu dies after the loading screen fades away. There's the following error:

*Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory*

I use a regular Karmic installation.This is the same error I experience and I also run a regular Karmic installation. Completely (written down from the screen) it states:
> **(gdm-binary:1996): WARNING**: Couldn't connect to system bus. Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

> **brandoncolorado said:**
> I will file a bug report if someone could help me figure out which package this problem derives from.
Based on the error message I would say either gdm or dbus. I hoped that the /var/log/dpkg file would help me but both packages (dbus-X11 and gdm) were updated in the last update.

If I succeed in getting the login screen, after giving the commands sudo gdm killall and then startx, the login screen is completely frozen. No mouse or keyboard activity possible at all.

---

### Post by WhiteSphinx on 2009-09-15
Same here - display reads:
*** Starting the Winbind daemon winbind** 
the system halts at this point.

---

### Post by tmschmitz on 2009-09-15
I think the issue is in upstart.  I went ahead and ran the initscripts for dbus, hal, network-manager and gdm by hand, and all seems to be working.  Upstart and initscripts packages were not able to upgrade on the last time around.

The following packages have unmet dependencies:
  upstart: PreDepends: mountall which is a virtual package.
  initscripts: Breaks: rsyslog (< 4.2.0-2ubuntu3~boot1) but 4.2.0-2ubuntu2 is installed.
               Breaks: udev (< 146-2~boot6) but 146-1 is installed.

---

### Post by Vladimir Hidalgo on 2009-09-15
I found this thread by searching "2.6.31-10 breaks boot".

I just ran the partial upgrade and now it won't boot. It just stops after /script/init-bottom I think.

Seems this is not going to be an easy solution :(

> **tmschmitz said:**
> I think the issue is in upstart.  I went ahead and ran the initscripts for dbus, hal, network-manager and gdm by hand, and all seems to be working.  Upstart and initscripts packages were not able to upgrade on the last time around.

The following packages have unmet dependencies:
  upstart: PreDepends: mountall which is a virtual package.
  initscripts: Breaks: rsyslog (< 4.2.0-2ubuntu3~boot1) but 4.2.0-2ubuntu2 is installed.
               Breaks: udev (< 146-2~boot6) but 146-1 is installed.

How did you do it?, I can't even start in Recovery Mode, I just need to save 1 file and then I can wait for the next update/fix

---

### Post by tmschmitz on 2009-09-15
> **Vladimir Hidalgo said:**
> I found this thread by searching "2.6.31-10 breaks boot".

I just ran the partial upgrade and now it won't boot. It just stops after /script/init-bottom I think.

Seems this is not going to be an easy solution :(



How did you do it?, I can't even start in Recovery Mode, I just need to save 1 file and then I can wait for the next update/fix

Well, like others in the thread, it drops me to a text login prompt.  I logged in and ran the initscripts with sudo.  It seems you have a much worse problem.

---

### Post by ppjose on 2009-09-15
what are the commands to start the initscripts? i can login

---

### Post by ikkefc3 on 2009-09-15
> **Vladimir Hidalgo said:**
> I found this thread by searching "2.6.31-10 breaks boot".

I just ran the partial upgrade and now it won't boot. It just stops after /script/init-bottom I think.

Seems this is not going to be an easy solution :(



How did you do it?, I can't even start in Recovery Mode, I just need to save 1 file and then I can wait for the next update/fix
I have the same problem.

---

### Post by TunaCanTommy on 2009-09-15
> **Vladimir Hidalgo said:**
> How did you do it?, I can't even start in Recovery Mode, I just need to save 1 file and then I can wait for the next update/fix

Vladimir, you might be able to start using a Live CD (or USB Thumbdrive) to get the file you want.

---

### Post by tmschmitz on 2009-09-15
sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm

---

### Post by Vladimir Hidalgo on 2009-09-15
> **TunaCanTommy said:**
> Vladimir, you might be able to start using a Live CD (or USB Thumbdrive) to get the file you want.
Thank you, I'll download 9.04 Live CD because I gave my Live CD, seem it was a bad idea :P

For me, the progress bar at the boot just moves side to side, then drops me to a black screen and I'd wait for about 15 minutes with no luck.

I can pres CTRL+ALT+SUPR and reboot start along with a message about "unattended-upgrades:" and I can't stop it even with "shutdown -c".

Please Digg it:
[http://digg.com/linux_unix/Partial_Update_for_Karmic_is_broken_today]("http://digg.com/linux_unix/Partial_Update_for_Karmic_is_broken_today")

---

### Post by useResa on 2009-09-15
> **tmschmitz said:**
> I think the issue is in upstart.  I went ahead and ran the initscripts for dbus, hal, network-manager and gdm by hand, and all seems to be working.Do you mean that you started in recovery mode, then resumed, logged in in tty1 and then started dbus, hal, network-manager and gdm from there?

> **tmschmitz said:**
> Upstart and initscripts packages were not able to upgrade on the last time around.

The following packages have unmet dependencies:
  upstart: PreDepends: mountall which is a virtual package.
  initscripts: Breaks: rsyslog (< 4.2.0-2ubuntu3~boot1) but 4.2.0-2ubuntu2 is installed.
               Breaks: udev (< 146-2~boot6) but 146-1 is installed.I noticed this as well.
Let's just hope that these updates will resolve this.

---

### Post by ppjose on 2009-09-15
> **tmschmitz said:**
> sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm

thanks thanks!!!! It works!

i run update manager, initscripts and upstart is listed to update.... is fixed??? is safe update??

---

### Post by tmschmitz on 2009-09-15
> **useResa said:**
> Do you mean that you started in recovery mode, then resumed, logged in in tty1 and then started dbus, hal, network-manager and gdm from there?


All except starting in recovery mode, that is correct.  Sorry for not being explicit.

---

### Post by Vladimir Hidalgo on 2009-09-15
So... what we -that can't login- can do to try to fix this?.

---

### Post by tmschmitz on 2009-09-15
> **Vladimir Hidalgo said:**
> Thank you, I'll download 9.04 Live CD because I gave my Live CD, seem it was a bad idea :P

For me, the progress bar at the boot just moves side to side, then drops me to a black screen and I'd wait for about 15 minutes with no luck.


Oh it goes to black screen alright.  just hit a key.

---

### Post by tmschmitz on 2009-09-15
> **ppjose said:**
> thanks thanks!!!! It works!

i run update manager, initscripts and upstart is listed to update.... is fixed??? is safe update??


It worked for me.

---

### Post by zekopeko on 2009-09-15
I had the problem of network-manager not being recognized as a job when using the "start" command.

sudo /etc/init.d/NetworkManager start

fixed it for me.

---

### Post by Vladimir Hidalgo on 2009-09-15
> **tmschmitz said:**
> Oh it goes to black screen alright.  just hit a key.

Only thing that does something is ctrl+alt+supr and then it start to reboot.

Just echoes a message "Checking for unattended-upgrades:" or something like that before a bunch of "mountall"'s error start to appear.

---

### Post by zoomy942 on 2009-09-15
> **zekopeko said:**
> I had the problem of network-manager not being recognized as a job when using the "start" command.

sudo /etc/init.d/NetworkManager start

fixed it for me.

wtf

my command worked like that before but now it says Command Not Found?

---

### Post by john stiles on 2009-09-15
Thanks tmschmitz, that got me back in and updated. My understanding of the boot process has grown.

---

### Post by hype on 2009-09-15
The thing is now, you have to use upstart to start network-manager:
sudo start network-manager

---

### Post by tmschmitz on 2009-09-15
> **john stiles said:**
> Thanks tmschmitz, that got me back in and updated. My understanding of the boot process has grown.

So has mine, and I have been working with Linux since the early '90s.  Upstart is NOT what I am used to.

---

### Post by hype on 2009-09-15
To get an idea, here is a list of services that have been updated to "Replace init script with Upstart job.":

> [ubuntu/karmic] acpid 1.0.6-9ubuntu6 (Accepted)   Scott James Remnant 
[ubuntu/karmic] anacron 2.3-13.1ubuntu9 (Accepted)   Scott James Remnant 
[ubuntu/karmic] apport 1.9-0ubuntu4 (Accepted)   Scott James Remnant 
[ubuntu/karmic] at 3.1.11-1ubuntu4 (Accepted)   Scott James Remnant 
[ubuntu/karmic] avahi 0.6.25-1ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] cron 3.0pl1-106ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] dbus 1.2.16-0ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] debhelper 7.3.15ubuntu2 (Accepted)   Scott James Remnant 
[ubuntu/karmic] gdm 2.27.90-0ubuntu5 (Accepted)   Scott James Remnant 
[ubuntu/karmic] hal 0.5.13-1ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] hostname 2.95ubuntu1 (Accepted)   Scott James Remnant 
[ubuntu/karmic] ifupdown 0.6.8ubuntu20 (Accepted)   Scott James Remnant 
[ubuntu/karmic] initramfs-tools 0.92bubuntu46 (Accepted)   Scott James Remnant 
[ubuntu/karmic] module-init-tools 3.10-3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] netbase 4.35ubuntu2 (Accepted)   Scott James Remnant 
[ubuntu/karmic] procps 1:3.2.8-1ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] rsyslog 4.2.0-2ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] sreadahead 1.0-3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] sysvinit 2.87dsf-4ubuntu3 (Accepted)   Scott James Remnant 
[ubuntu/karmic] udev 147~-1 (Accepted)   Scott James Remnant

---

### Post by jack_mcdowell on 2009-09-15
I got my internet working from the command line and did some more updates 10 minutes ago, and now... no eth1 network interface with ifconfig... something really hit the fan

---

### Post by tmschmitz on 2009-09-15
> **Vladimir Hidalgo said:**
> Only thing that does something is ctrl+alt+supr and then it start to reboot.

Just echoes a message "Checking for unattended-upgrades:" or something like that before a bunch of "mountall"'s error start to appear.

As far as saving the one file goes, a rescue disk, such as the Ubuntu Live disk, should get you where you can mount the drive and save the file.  Hopefully the "unattended-upgrades" will take care of the boot.

---

### Post by Vladimir Hidalgo on 2009-09-15
oh, I started in recovery mode and I did ctrl+alt+supr and inmeadiatly I ran "init 1" and finally got the recovery options, funny thing is that i can't connect to my WiFi 'cause there's not NetworkManager started :lolflag:

I'll have to look for a very long network cable as it seems...

---

### Post by WhiteSphinx on 2009-09-15
> **tmschmitz said:**
> sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm

I am confused, how do I use this info?
When I start in recover mode and drop to root shell prompt, these commands are not recognized.

---

### Post by tmschmitz on 2009-09-15
> **WhiteSphinx said:**
> I am confused, how do I use this info?

This is a series of commands that you can run from a text login (assuming you can get there) to get you bootstrapped into a working system.  At that point you can run the updates, and all seems to be fixed, now.

---

### Post by grandtoubab on 2009-09-15
> **tmschmitz said:**
> sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm
:KS:KS:KS:KS

thank you this works for me and I was able to recover my desktop with update-manager:P

---

### Post by WhiteSphinx on 2009-09-15
> **tmschmitz said:**
> This is a series of commands that you can run from a text login (assuming you can get there) to get you bootstrapped into a working system.  At that point you can run the updates, and all seems to be fixed, now.

The question is: How do I get to a text login?

---

### Post by Vladimir Hidalgo on 2009-09-15
ok, using the combination of ctrl+alt+supr and init 1 I've got to able to login, but / has the option "onerror=ro" and everytime I got a read-only system and I can update the system to fix the problem...

:lolflag:

How could I sort that problem?, would be easy to edit the fstab if I had the Live CD I guess...

There's any grub parameter to explicity tell to the kernel to mount in / in rw mode?.

---

### Post by TunaCanTommy on 2009-09-15
I can't get to the text log-in.  During the boot I see "Grub loading", I hit "ESC" and it just continues on to the Ubuntu logo and almost immediately goes to a a blank screen.  Can't get any log-in at all.

I booted from a live-CD (USB thumbdrive) and went looking for /boot/grub/menu.lst thinking I might edit it for a little more delay. But "no-joy" the file wasn't there ? ? ?  Do I need to create one ? ?

Found this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)  I'll give it a try!

---

### Post by zoomy942 on 2009-09-15
> **tmschmitz said:**
> This is a series of commands that you can run from a text login (assuming you can get there) to get you bootstrapped into a working system.  At that point you can run the updates, and all seems to be fixed, now.

so i get to a command line and type sudo start dbus, but i get a start : Unknown Job : dbus

whats that all about?

---

### Post by zekopeko on 2009-09-15
> **zoomy942 said:**
> so i get to a command line and type sudo start dbus, but i get a start : Unknown Job : dbus

whats that all about?

try something like:

sudo /etc/init.d/dbus start

---

### Post by WhiteSphinx on 2009-09-15
Okay I logged in but when I enter these commands I get:

~$ sudo start dbus
start: Unknown job: dbus

Okay I got it

---

### Post by Ric_NYC on 2009-09-15
> **tmschmitz said:**
> sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm

Ubuntu Starts...
I can log in, but the mouse and the touchpad don't work.

---

### Post by zoomy942 on 2009-09-15
so i thought i'd use the command line to navigate to the init.d foler and see if the nertwork manager folder is there.  is it, spelled network-manager, but its blue while everything else is green

---

### Post by thegodsquirrel on 2009-09-15
What is SUPR?

as in ctrl-alt-supr

---

### Post by Ric_NYC on 2009-09-15
One more reason to have a "system restore" in Ubuntu.

---

### Post by zoomy942 on 2009-09-15
> **zekopeko said:**
> try something like:

sudo /etc/init.d/dbus start

k.  dbus is alerady started
hal is already started

when i do the same command with network manager i get this..  (typing this sucks lol)

" Rather than invoking init scripts through /etc/init.d/network-manager start, use the service(8) utility, eg service network-manager start

Since ths script you are using has been converted to an Upstart job, you may also use the start(8) utility, eg. start network-manager network-manager start/running, process 3756
/etc/init.d/network-manager: 46: s: not found "


EDIT - wait wait.  saw the process number so i figured it was running and sure enough, sudo apt-get update is going.

---

### Post by zoomy942 on 2009-09-15
it says 3 packages are still held back.  that normal?

---

### Post by jack_mcdowell on 2009-09-15
0Are they really fixed??? I have done all the updates with apt-get update/upgrade, and my system is still broken. I do have 4 packages left behind though... am I missing something?

---

### Post by Vladimir Hidalgo on 2009-09-15
> **thegodsquirrel said:**
> What is SUPR?

as in ctrl-alt-supr

sorry, I'm from Central America and "supr" is the key for "delete" in Spanish keyboards :lolflag: so I mean ctrl+alt+del

-------

Ok, finally I got it working!. For those who **can't even get to login screen** try this:

1. Start normal and wait for the black screen.
2. Press ctrl+alt+del and -as fast as you can- type "init 3" and press enter.
3. You may get the login screen or a stack trace of SMB, just press enter.
4. Youu may have your / in read-only mode, you won't be able to do anything, so run: "sudo mount -o remount,rw /"
5. As per tmschmitz instructions (thank you!):
sudo start dbus
sudo start hal
sudo start network-manager

6. Verify you have internet:
ping google.com (press Ctrl+C when you see a response)

7. If you have internet, then run: "sudo apt-get update && sudo apt-get dist-upgrade -y"

8. Wait until it finish and restart.

9. Everything should be normal again.

It will update several packages related to boot process.


P.S.: you may not be able to use your Wireless internet in the process, so you better connect a network cable to your Ethernet port to solve this.

---

### Post by VMC on 2009-09-15
> **Ric_NYC said:**
> One more reason to have a "system restore" in Ubuntu.

Its called backup! And that's what I'm doing again right now before I retry the newest updates. I have a spare partition and just use gparted and copy to it in the even of certain failure :)

I can recover at any time just lose some updates.

---

### Post by ilna on 2009-09-15
just few minutes ago 'hostname' package has apeared in updates (main servers), unblocking 'initscipts' - for me all is OK now. At first X was extremely slow. I have reinstalled (after digging in X11 log) drm-related packages - it cured the slowness.

---

### Post by Ric_NYC on 2009-09-15
> **VMC said:**
> Its called backup! And that's what I'm doing again right now before I retry the newest updates. I have a spare partition and just use gparted and copy to it in the even of certain failure :)

I can recover at any time just lose some updates.

It would be simpler if we could just "roll back" the distro.

---

### Post by Regenweald on 2009-09-15
> **Ric_NYC said:**
> It would be simpler if we could just "roll back" the distro.

Roll back can't work if we can't get to the rollback app ;) The existing Conary package manager accommodates rollbacks and this feature is planned for the App Store. It's coming

---

### Post by Ric_NYC on 2009-09-15
> **Regenweald said:**
> Roll back can't work if we can't get to the rollback app ;) The existing Conary package manager accommodates rollbacks and this feature is planned for the App Store. **It's coming**


Thanks.
That's really nice!

---

### Post by zoomy942 on 2009-09-15
running this


. If you have internet, then run: "sudo apt-get update && sudo apt-get dist-upgrade -y"


got me back into my TabletPC

---

### Post by thegodsquirrel on 2009-09-15
> **Vladimir Hidalgo said:**
> sorry, I'm from Central America and "supr" is the key for "delete" in Spanish keyboards :lolflag: so I mean ctrl+alt+del

-------

Ok, finally I got it working!. For those who **can't even get to login screen** try this:

1. Start normal and wait for the black screen.
2. Press ctrl+alt+del and -as fast as you can- type "init 3" and press enter.
3. You may get the login screen or a stack trace of SMB, just press enter.
4. Youu may have your / in read-only mode, you won't be able to do anything, so run: "sudo mount -o remount,rw /"
5. As per tmschmitz instructions (thank you!):
sudo start dbus
sudo start hal
sudo start network-manager

6. Verify you have internet:
ping google.com (press Ctrl+C when you see a response)

7. If you have internet, then run: "sudo apt-get update && sudo apt-get dist-upgrade -y"

8. Wait until it finish and restart.

9. Everything should be normal again.

It will update several packages related to boot process.


P.S.: you may not be able to use your Wireless internet in the process, so you better connect a network cable to your Ethernet port to solve this.

How fast do you need to be?  this is not working as I would have hoped

---

### Post by jack_mcdowell on 2009-09-15
> **zoomy942 said:**
> running this


. If you have internet, then run: "sudo apt-get update && sudo apt-get dist-upgrade -y"


got me back into my TabletPC

Thanks! Worked for me

---

### Post by zoomy942 on 2009-09-15
and yup - network manager isnt running. 

what was the command again?

EDIt - inside ubuntu

EDIT 2 - sudo start network-manager

---

### Post by Vladimir Hidalgo on 2009-09-15
> **thegodsquirrel said:**
> How fast do you need to be?  this is not working as I would have hoped

Well, not that fast, but start as soon as possible after you release ctrl+alt+supr.

It's easy to make typing mistakes, because of the hurry and the fact you can't see what you're typing.

If you unsure, just keep typing "init 3"+[Enter] over and over again. You may try "init 1" too (both worked for me).

BTW, what is happening to you?, computer finally restarts without login screen?.

---

### Post by inportb on 2009-09-15
Yeah, the initscripts package update fixed it, I think.

---

### Post by thegodsquirrel on 2009-09-15
> **Vladimir Hidalgo said:**
> Well, not that fast, but start as soon as possible after you release ctrl+alt+supr.

It's easy to make typing mistakes, because of the hurry and the fact you can't see what you're typing.

If you unsure, just keep typing "init 3"+[Enter] over and over again. You may try "init 1" too (both worked for me).

BTW, what is happening to you?, computer finally restarts without login screen?.



Did the lastest update no recovery console no login screen

---

### Post by zoomy942 on 2009-09-15
> **thegodsquirrel said:**
> Did the lastest update no recovery console no login screen

did you do the command i posted a few posts ago?

---

### Post by TunaCanTommy on 2009-09-15
Vladimir:  That's what's happening to me. After typing "init 3" several time the computer restarts.

---

### Post by Vladimir Hidalgo on 2009-09-15
> **thegodsquirrel said:**
> Did the lastest update no recovery console no login screen
You were able to do the **apt-get dist-upgrade -y **, restarted and nothing happened?. That's weird. You should try again and see if there's not packages hold.

> **TunaCanTommy said:**
> Vladimir:  That's what's happening to me. After typing "init 3" several time the computer restarts.
I'm supposing you're pressing [Enter] after each "init 3" (try also "init 1").

I that does not work, try in recovery mode, after the last message appears on screen and the computer is idle.

---

### Post by TunaCanTommy on 2009-09-15
Thank you Vlaimir . . I can't get to recovery mode, and the "init 3" / "init 1" doesn't seem to get me anything.  Guess I'll just have to re-install !

---

### Post by shuita on 2009-09-15
I restarted after doing
```
apt-get dist-upgrade -y
```

Now, the system stops with:
```
Begin: Running /scripts/init-bottom ...
Done.
```

No shell, nothing. Recovery mode does not work anymore!!!

---

### Post by shuita on 2009-09-15
Pressing Ctrl+Alt+Del causes:

```
Checking for running unattended upgrades:
```

And continues with "normal shutdown"

---

### Post by paulmerchant on 2009-09-15
To fix things, I just went to my recovery mode. I had no display , but I hit the down arrrow five times and pressed Enter. Then, still without a display, I knew there was a prompt somewhere with networking so I was able to type

sudo apt-get update && sudo apt-get dist-upgrade -y

and wait a few minutes. I had tried to do this a few times earlier today, but now that the fixes are in the repositories, everything works fine again.

---

### Post by Vladimir Hidalgo on 2009-09-15
> **shuita said:**
> I restarted after doing
```
apt-get dist-upgrade -y
```

Now, the system stops with:
```
Begin: Running /scripts/init-bottom ...
Done.
```

No shell, nothing. Recovery mode does not work anymore!!!

Try this:
[http://ubuntuforums.org/showthread.php?p=7954999#post7954999](http://ubuntuforums.org/showthread.php?p=7954999#post7954999)

> **shuita said:**
> Pressing Ctrl+Alt+Del causes:

```
Checking for running unattended upgrades:
```

And continues with "normal shutdown"

In that exact time you have to start typing "init 3" and pressing [Enter] until you got a login screen.

> **TunaCanTommy said:**
> Thank you Vlaimir . . I can't get to recovery mode, and the "init 3" / "init 1" doesn't seem to get me anything.  Guess I'll just have to re-install !

When you boot and GRUB screen appears, please press Esc and choose the Kernel with "- Recovery".

While selected press "e" and then in the second line press "e" again, remove the "ro" from the line, then press "[Enter]" and "b".

When system is loaded (ie. hard disk is not working, there's no progress on screen) try the ctrl+alt+supr -> "init 3" / "init 1" thing.

You should be able to see the shutdown process "stopping" and init calls being made (daemons starting).

If that does not work, well, I'll be sorry to make you waste your time.

---

### Post by brandoncolorado on 2009-09-15
Does anyone know why this happened?  Did we get unlucky and update during a period when only part of the packages had been sent to the repositories?

---

### Post by dentaku65 on 2009-09-15
I can only able to boot and use the system inserting
> nomodeset
in grub command line option.

Press E in the kernel line and add nomodeset after splash, then ctrl-x to boot (both for kernel and recovery mode, this last one can be useful to go in console mode to make - sudo aptitude update && sudo aptitude dist-upgrade - in case some previous updates has failed)

So far, so good... many errors in the init stage anyway, but the system is up.

---

### Post by shuita on 2009-09-16
I have been as fast as possible, but "init 3" does not work for me - the shutdown wont stop!

Also adding "nomodeset" has no effect....

More ideas?

---

### Post by xArv3nx on 2009-09-16
sreadahead doesnt work in the latest updates because mountall isn't built yet. :P so it updates everything except sreadahead (because the dep mountall isn't built yet due to build errors) and that's probably why it won't boot.

try manually compiling the deb mountall with the .dsc and tar.gz. if you can't google how to do that, or don't want to, i don't think you should be using karmic. these types of things are bound to happen.

---

### Post by hdragomir on 2009-09-16
I'm using ubuntu 9.10, 64bit, latest kernel.
My problem is: no mouse. I can log in though, and I have X, but still no mouse.

Also, most of my config files seem to have gone amiss. Sadly, I could not spend time to dig deeper, but I'll do so later tonight.

Hopefully, the next update will fix these issues. Remember, though: this is the development branch and these things are bound to happen.

---

### Post by Jim March on 2009-09-16
An "unborking guide" that should work for most folks...it's what I did.

Boot-up is still funky-looking for me, but I'm back to 100% functionality.

[http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657)

---

### Post by TDK800 on 2009-09-16
I am able to go to kernel recovery mode, but when entering the full disk decryption password it says:

Unlocking the disk /dev/disk/by-uuid/b7w8.... (sda1_crypt)
Enter passphrase:
key slot 0 unlocked.
Command sucessful.
File descriptor 3 left open
2 logival volume(s) in volume group "x" now active
cryptsetup: unknown fstype, bad password or options?
Command failed: Device busy
Unlocking the disk /dev/disk/by-uuid/b7w8.... (sda1_crypt)
Enter passphrase: Command failed: Device already exists

---

### Post by thecityofgold2006 on 2009-09-16
I give in. No recovery mode, nothing here works to get to a prompt, let alone a prompt with networking.

Having installed my first Alpha at Jaunty Alpha 5, I decided to jump into Karmic at a similar stage. Big mistake! This thing is majorly f**ked.

---

### Post by other guy on 2009-09-16
I updated using Synaptic earlier. I selected "Mark Updates" and it went fine. Although it did remove Gnome games. I seen beforehand it was going to do it. Everything went fine on this end.
After the REISUB, I fired off the Update Manager to check what was missed. I seen it wanted a kernel header update. So I did that and all works fine.

---

### Post by barisurum on 2009-09-16
I did the "sudo apt-get dist-upgrade -y" and my problem was solved but now everytime I boot into gnome the network-manager is not running and I have to run it with "sudo start network-manager" is there a fix for this?

---

### Post by useResa on 2009-09-16
> **xArv3nx said:**
> sreadahead doesnt work in the latest updates because mountall isn't built yet. :P so it updates everything except sreadahead (because the dep mountall isn't built yet due to build errors) and that's probably why it won't boot.

try manually compiling the deb mountall with the .dsc and tar.gz. Not built yet??
[http://packages.ubuntu.com/karmic/mountall](http://packages.ubuntu.com/karmic/mountall)

> **xArv3nx said:**
> i don't think you should be using karmic. these types of things are bound to happen.I think most of us are aware these things are about to happen. IMHO that is part of the "fun" trying out alpha releases  :P
Additionally I think such things help devs to discover what works or does not work.

---

### Post by L_V on 2009-09-16
> **useResa said:**
>  that is part of the "fun" trying out alpha releases It's a point of view.
However Karmic becoming less and less stable, but closer and closer to final release (*next month*)  is may be not a good sign.

---

### Post by lcohen999 on 2009-09-16
> **L_V said:**
> It's a point of view.
However Karmic becoming less and less stable, but closer and closer to final release (*next month*)  is may be not a good sign.

Oh, please.  Every beta has the same post usually around thus time.  OMG, Jaunty is so unstable, blah, blah blah.

---

### Post by shuita on 2009-09-16
@Jim March

This guide doesnt work for me as well
[http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657)

"2) Reboot, using your last good kernel (probably -10) in RECOVERY MODE."
Boot stops at 
```
Running /scripts/init-bottom ...
Done.
```No shell, nothing. Recovery mode does not work anymore!!!) If you're doing whole-disk-encryption, put your password in.

4) At the menu, pick "netroot".
I do not even come to this point...

Does anybody have an idea how to recover from this?

---

### Post by 00b00nt00 on 2009-09-16
Karmic broke for me, too, however, I solved the problem easily.

When the cursor disappears from the boot screen, tap escape then log in via the command line (user name / password).

Type: sudo apt-get update

then: sudo apt-get upgrade

finally: sudo apt-get dist-upgrade.

Reboot & hey presto we're back into GNOME.

---

### Post by shuita on 2009-09-16
That is exactly what i did yesterday evening. This killed the system totaly:

As i wrote: it do not get a shell when the boot stops...

---

### Post by andresmh on 2009-09-16
So after the problems with the update yesterday, I reinstalled Alpha 5. Now I realize that other people were experiencing the same and I could have fixed the issue. Anyway, have the problems been fixed? is it safe to do an update now or should I wait a bit?

---

### Post by cykotiktek on 2009-09-16
I would say that it is safe to do updates now.  I ended up reinstalling yesterday because I couldn't get my eth0 to connect no matter what I did.  This was before someone came up with the idea of CHROOT but oh well it's a test box thats what it's for.

---

### Post by 00b00nt00 on 2009-09-16
My response was not aimed at anyone in particular.

I could not view the command line until I tapped a few keys, then it unexpectedly appeared.

Sounds like you lucked out, shuita. Maybe you can salvage your files using a live CD and do a re-install.

---

### Post by Vladimir Hidalgo on 2009-09-16
> **shuita said:**
> I have been as fast as possible, but "init 3" does not work for me - the shutdown wont stop!

Also adding "nomodeset" has no effect....

More ideas?

ups! :oops:, I forgot to add a step:

When  you see this:
```
Running /scripts/init-bottom ...
Done.
```

Press **ctrl+alt+f1**, that will take you to TTY1. Probably you'll not have login screen there either, but being there seems to be necessary for the "init 3" thing to work

---

### Post by fazza on 2009-09-16
Citizen_Kane, I have the same problem as you... Only problem is, I'm running grub2, so I don't know how to boot into recovery or any thing :S
I currently don't have a splash screen, don't know why, but that's the only way I know that it hangs at Winbind O_o

Sorry ignore me, I didn't realise there were lots of pages >.<

---

### Post by EzraReeves on 2009-09-16
I did a fresh install this morning and its still broken. (I updated the system 10 min ago)

---

### Post by kimda on 2009-09-16
I have the same problem. Cannot login with the recovery mode or with regular mode. I managed to chroot mount the lvm volume with a live cd. When I look into the messages log I get libc segfault errors with hal. Hopefully new packages will arrive soon to fix these issues.

---

### Post by grandtoubab on 2009-09-16
> **kimda said:**
> I have the same problem. Cannot login with the recovery mode or with regular mode. I managed to chroot mount the lvm volume with a live cd. When I look into the messages log I get libc segfault errors with hal. Hopefully new packages will arrive soon to fix these issues.

new packages don't fix anything for me
the only way to workaround I can do is
[http://ubuntuforums.org/showpost.php?p=7958872&postcount=14](http://ubuntuforums.org/showpost.php?p=7958872&postcount=14)

):P

---

### Post by omarly on 2009-09-16
This goes for me too. :(

---

### Post by Johnsie on 2009-09-16
Well, this didn't happen to me when I was testing Windows 7

---

### Post by useResa on 2009-09-16
For me everything is up and running again with all the latest updates installed.
Although ... I have to admit ... I did a reinstall since I "destroyed" my previous install by manually adding the package mountall before it was released.
Ah well ... that is how you learn :P

---

### Post by fazza on 2009-09-16
> **Johnsie said:**
> Well, this didn't happen to me when I was testing Windows 7

That's because win7 is a beta and microsoft can't afford to scare people off with buggy betas
but this is ubuntu 9.10 ALPHA 5 - 6 is released tomorrow I think - so it's bound to have issues like this :P :)

---

### Post by bodhi.zazen on 2009-09-16
I have this problem server side.

Too bad, 9.10 has been sooo stable, up to now :(

---

### Post by kaotiko on 2009-09-16
Solved for me

The problem is the black screen, then
1- ctrl+alt+F1
2- introduced login
3- introduced password
4- "sudo mount -o remount,rw /"
(starting....)
5- sudo start dbus
6- sudo start hal
7- sudo start network-manager
8- sudo start gdm
(I needed to restart network-manager again, but then all fine...)
9- sudo apt-get update
10- sudo apt-get dist-upgrade
11- beer

(sorry for my bad english!!)

CYA!!

---

### Post by VMC on 2009-09-16
> **kaotiko said:**
> Solved for me

The problem is the black screen, then
1- ctrl+alt+F1
2- introduced login
3- introduced password
4- "sudo mount -o remount,rw /"
(starting....)
5- sudo start dbus
6- sudo start hal
7- sudo start network-manager
8- sudo start gdm
(I needed to restart network-manager again, but then all fine...)
9- sudo apt-get update
10- sudo apt-get dist-upgrade
11- beer

(sorry for my bad english!!)

CYA!!
 Step #7 help solve a problem I had. There was the network icon top right that said network disabled. That's weird because I was able to connect to internet just nothing inside the dialog box. 7- sudo start network-manager, solved my issue. Thanks.

---

### Post by PRGUY85 on 2009-09-16
> **kaotiko said:**
> Solved for me

The problem is the black screen, then
1- ctrl+alt+F1
2- introduced login
3- introduced password
4- "sudo mount -o remount,rw /"
(starting....)
5- sudo start dbus
6- sudo start hal
7- sudo start network-manager
8- sudo start gdm
(I needed to restart network-manager again, but then all fine...)
9- sudo apt-get update
10- sudo apt-get dist-upgrade
11- beer

(sorry for my bad english!!)

CYA!!

I can't get my laptop trackpad/mouse to work.

---

### Post by Nullack on 2009-09-16
I cant TTY into a console login using CTR ALT F1 or indeed any screen up to F6.

Therefore I cant repair it.

Is the daily CD binary in a stable state yet?

---

### Post by Regenweald on 2009-09-16
I think the recent round of changes makes up for all the 'stability' thus far. I'm afraid to restart :P On the upside, I learned to chroot this cycle and actually understand how it works....

---

### Post by VMC on 2009-09-17
[SIZE="4"][/SIZE]> **Regenweald said:**
> I think the recent round of changes makes up for all the 'stability' thus far. I'm afraid to restart :P On the upside, I learned to chroot this cycle and actually understand how it works....

You bring up a good point. If everything went smoothly we wouldn't learn a thing. I think all of us took away something positive from all this.

We must bear in mind where we are anyway. Testing. Things will break from time to time. Just hope it isn't all the time.

I think we need to change the entry to this testing forum to read those famous words of Dante's:

[B][FONT="Arial Black"][SIZE="4"]Abandon hope all ye who enter here[/SIZE]
[/FONT][/B]

---

### Post by mojorising on 2009-09-17
Hi, everyone. 

Has anyone out there using encrypted LVM (full-disk encryption) successfully recovered from this issue?

If so would you please, please post the steps you took to do so?

I have tried all the applicable suggestions in this post, including using a live CD (Jaunty) to mount my filesystem and read from there (as in this link that was posted a while back [http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)) but I can not even see my volume groups with the LVM utilities. I can not use the recovery mode methods because of those 'cryptsetup:cryptestup failed' and 'device already exists' errors. So I'm basically stuck at the very start of the boot process, just after GRUB.


Thanks very much, 

Mike

---

### Post by dino99 on 2009-09-17
Happy news:

with last packages upgraded, karmic start again without trouble  :P
looking the logs don't reveal bad things.

Thanks dev

---

### Post by kaotiko on 2009-09-17
> **Nullack said:**
> I cant TTY into a console login using CTR ALT F1 or indeed any screen up to F6.

Therefore I cant repair it.

Is the daily CD binary in a stable state yet?

The only problem is that you can't see what are you writing, but you are.

---

### Post by MichaëlVD on 2009-09-17
These work fine here:

```
sudo start dbus
sudo start hal
sudo start gdm
```

However, this one doesn't:

```
sudo start network-manager
```

It doesn't seem to recognise this command.

Which means that I have access to my desktop, but that I can't update/upgrade.

Any ideas on why this doesn't work?

Thanks!

---

### Post by Awareness on 2009-09-17
when i try to upgrade it does not upgrade some packages... it only says its keeping them back... :S

(packages are upstart, initscripts and some others :S

Should i force the upgrade somehow? I mean, if it wants to keep them is for some reason, even if is unknown for me...


PS: btw, it says "there was an error creating the child process for this terminal" when i try to open terminal in gnome

---

### Post by mojorising on 2009-09-17
Okay I found something that might be of some help to fellow users of encrypted LVM. 


[http://roderick-greening.blogspot.com/2009/09/recover-non-booting-linux-system.html](http://roderick-greening.blogspot.com/2009/09/recover-non-booting-linux-system.html)

Near the bottom there is a comment about making some changes to GRUB to get a command line and then get on to doing this - '/etc/init.d/cryptdisks start', which is supposed to get everything running again so you can read your disks. 

The problem I'm having is that the comment says this:

"edit grub to boot rw and init=/bin/bash

this will get you to a command line, then you can get network (if you are plugged in) by doing 'dhclient &'. Then you and apt-get update and upgrade :)"

... and I'm not exactly sure where to put the 'rw and init=/bin/bash' bit. Does anyone out there know enough about this to fill in the blanks and make the process a little more verbose?


Thanks in advance, 
Mike

---

### Post by zika on 2009-09-17
> **MichaëlVD said:**
> These work fine here:

```
sudo start dbus
sudo start hal
sudo start gdm
```However, this one doesn't:

```
sudo start network-manager
```It doesn't seem to recognise this command.

Which means that I have access to my desktop, but that I can't update/upgrade.

Any ideas on why this doesn't work?

Thanks!Try **sudo dhclient eth0**(or whatever You are using) ...
Or **start network-interface INTERFACE=eth0 **...

---

### Post by dino99 on 2009-09-17
> **MichaëlVD said:**
> These work fine here:

```
sudo start dbus
sudo start hal
sudo start gdm
```

However, this one doesn't:

```
sudo start network-manager
```

It doesn't seem to recognise this command.

Which means that I have access to my desktop, but that I can't update/upgrade.

Any ideas on why this doesn't work?

Thanks!

remember that's case sensitive:

try Network-Manager instead

---

### Post by oztrailrider on 2009-09-17
I have just installed the latest updates. I am not seeing the kinds of serious breakage that some people are however my video performance is now completely shot (Intel GMA3100). Windows are slow to draw and compiz cannot be enabled anymore. It's been smooth sailing till now. 

Anyone else on Intel video seeing the same thing?.

Edit: Just noticed x.org is chewing large amounts of CPU whenever anything gets redrawn. The only xserver update that got installed was xserver-xorg-video-nv? Need to investigate..

Edit 2: Removed xserver-xorg-video-nv. Was able to re-enable compiz and performance is restored mostly. Performance is still quite poor without compiz enabled though.

---

### Post by Johnsie on 2009-09-17
> That's because win7 is a beta and microsoft can't afford to scare people off with buggy betas
but this is ubuntu 9.10 ALPHA 5 - 6 is released tomorrow I think - so it's bound to have issues like this  

No, Windows 7 has been RTM for about a month now, even longer for manufacturers.

Microft did several test releases during the process including alphas, betas and release candidates. While some of the releases probably caused breakage to a small number of users they didn't release anything that was just broken for all users. I guess it's a quality assurance issue. And yes, Microsoft doesn't want to have buggy betas because it could scare companies/customers away. The problem with Ubuntu for professional sysadmins is that you wont have any idea how Ubuntu will work until a matter of days before the release and software versions are pretty much locked down to OS versions unless you add PPA's.

I have to say I actually prefer the Microsoft way of testing because it seems they do more QA before throwing stuff at testers... Also, the more lengthly development cycle gives developers and sysadmins more time to test and work with the new technology.

---

### Post by ELD on 2009-09-17
> **Johnsie said:**
> 
I have to say I actually prefer the Microsoft way of testing because it seems they do more QA before throwing stuff at testers... Also, the more lengthly development cycle gives developers and sysadmins more time to test and work with the new technology.

This, opensuse has figured it out and doesn't have such a short dev cycle, i would prefer ubuntu have it's 6months for adding in new stuff and then another 2 months to properly stabalise it all.

---

### Post by KrazyPenguin on 2009-09-17
[B][U] Today the upgrade manager asked to do a "partial upgrade," and I went ahead with that upgrade.  
[/U][/B]

I was told to NEVER NEVER NEVER EVER do a partial upgrade.
It could break your system.  So when it said "Partial Upgrade" is available, I clicked on "Cancel" button, and everything still works ;-)
:guitar:

Would you drive a car if it were partially fixed?? lol

---

### Post by Awareness on 2009-09-17
> **Awareness said:**
> when i try to upgrade it does not upgrade some packages... it only says its keeping them back... :S

(packages are upstart, initscripts and some others :S

Should i force the upgrade somehow? I mean, if it wants to keep them is for some reason, even if is unknown for me...


PS: btw, it says "there was an error creating the child process for this terminal" when i try to open terminal in gnome

I answer myself :) (taken from [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430125](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430125) )

#27   	 pablomme  wrote on 2009-09-15:

A quick summary of how to fix this:

- Boot
- When booting stops at a black screen with a blinking cursor, press Ctrl-Alt-F2 and log in
- Type (assuming a wired connection on eth0):
   sudo dhclient eth0
   sudo apt-get update
   sudo apt-get install mountall
   sudo apt-get upgrade
- Press Ctrl-Alt-Delete

Now, I also get the NetworkManager problem (solved simply by running "sudo NetworkManager") after reboot. It'd be useful if whoever reports it posted a link here.

---

### Post by mrlika on 2009-09-17
I managed to get to my command line using Ctrl+Alt+Del and quickly typing 'init 3'. Then I setup network using ifconfig and route but commands

 sudo apt-get update
 sudo apt-get dist-upgrade

did not help to make my system boot normally. But then I tried

sudo apt-get autoremove

and it helped!!! Now my system boots almost normally (with few strange error messages related to udev).

'autoremove' made apt-get to reinstall some of my startup scripts and configuration that is why it hepled. AFAIK 'sudo apt-get --reinstall install {package}' for some packages related to system and boot process (like udev)  will do the same job.

---

### Post by jackhynes on 2009-09-17
> **Vladimir Hidalgo said:**
> Ok, finally I got it working!. For those who **can't even get to login screen** try this:

1. Start normal and wait for the black screen.
2. Press ctrl+alt+del and -as fast as you can- type "init 3" and press enter.
3. You may get the login screen or a stack trace of SMB, just press enter.
4. Youu may have your / in read-only mode, you won't be able to do anything, so run: "sudo mount -o remount,rw /"
5. As per tmschmitz instructions (thank you!):
sudo start dbus
sudo start hal
sudo start network-manager

6. Verify you have internet:
ping google.com (press Ctrl+C when you see a response)

7. If you have internet, then run: "sudo apt-get update && sudo apt-get dist-upgrade -y"

8. Wait until it finish and restart.

9. Everything should be normal again.


1-4 work fine. "sudo start dbus" works fine. "sudo start hal" and "sudo start network-manager" return unknown job errors. "sudo /etc/init.d/NetworkManager start" and "sudo /etc/init.d/hal start" return relocation errors and say that GLIBC_PRIVATE is not defined with link time reference.

Without being able to connect to the internet I can't update. Can anyone remind me how to upgrade my existing installation from the LiveCD? i.e. how to mount my hard drive and access it as root...

---

### Post by Leighman on 2009-09-17
Rebooting fine here now =D

---

### Post by Schendje on 2009-09-17
If I use the daily build, or wait for A6, I won't have these problems, right? :P

---

### Post by GuidoVb on 2009-09-17
This worked fine for me (Chroot from LiveCD)

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430272/comments/26]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430272/comments/26")

:)

---

### Post by rajeev1204 on 2009-09-17
> **Schendje said:**
> If I use the daily build, or wait for A6, I won't have these problems, right? :P


THats not correct,probably the daily builds are fixed by now , but they had problems too 2 days back.

Aplha 6 should be fine though.

---

### Post by Schendje on 2009-09-17
Yeah, I'll just wait for A6 I think. I'm not in any hurry and if it's still in A6 I'll hear about it soon enough via the forums. Thanks.:)

---

### Post by bodhi.zazen on 2009-09-17
> **rajeev1204 said:**
> THats not correct,probably the daily builds are fixed by now , but they had problems too 2 days back.

Aplha 6 should be fine though.

It is not fixed yet, at least not on my 9.10 server.

The various fixes and work arounds work for some people , but not everyone.

---

### Post by LKjell on 2009-09-17
My wired connection is dead. But I am grateful that my wireless is not. Though it is a bit slow when watching stream :popcorn:

---

### Post by Vladimir Hidalgo on 2009-09-17
Today I tried luck updating a Wubi-based Ubuntu 9.04 to devel 9.10 and everything went really fine!.

I just can't believe how fast this machine (VGN-CR240F) boots, I just saw the grub screen followed by 3 seconds of black screen and then bam! login screen!.

Amazing job!.

BTW, this is to confirm that currently is safe to upgrade.

---

### Post by rogerdean on 2009-09-17
I just updated everything from a fresh alpha5 in Virtualbox, and troubles a-plenty still there...

---

### Post by popejeremy on 2009-09-17
I'm running Koala on an EEE 1005HA. I tried:

```
sudo start dbus
sudo start hal
sudo /etc/init.d/NetworkManager start
sudo start gdm
```

...which gave me a slowly flickering screen.

After a bunch of aimless hacking, I got out the flash stick from which I installed Koala originally, and reinstalled an older version. I guess I'll wait to do an upgrade again until I know it's gonna be stable.

---

### Post by cecilpierce on 2009-09-17
Well I've tried everything posted and mine is so screwed up now I don't think Linus could fix it. I do have one other install that is kinda working but it was the kdm login fix and its not very stable, I did an update on my old Dell which still had 2.6.31-9 and it works great but the 10 don't, hmmm!

---

### Post by Awareness on 2009-09-17
> **cecilpierce said:**
> Well I've tried everything posted and mine is so screwed up now I don't think Linus could fix it. I do have one other install that is kinda working but it was the kdm login fix and its not very stable, I did an update on my old Dell which still had 2.6.31-9 and it works great but the 10 don't, hmmm!

This is exactly one of the 1st things i learned from linux... don't try everything you read unless u kinda know what you are doing or know how to roll it back

It happened trying to make works 3d acceleration on via chipsets... i followed so many tutorials and i screwed so bad, there was no way to make it work following any instructions... general and default instructions were no longer valid for me :)

I now do only one thing at a time... :) and roll it back if it doesn't work... for example, i didn't try to force the upgrade when apt-get detected there was new packages that could solve the problem (initscripts and upstart for example)

anyway, I had luck and had mine working...  i don't know why i update to unestable version... i guess i like living in the edge... ;)

(btw, the update made the sound in ff stop working too...)

---

### Post by mojorising on 2009-09-17
Well. It's been a wild ride with this. 

I had almost everything on my messed drive backed up so getting the system working or at least what little data was there back was really just a test of will. 

Anyway, I was able to mount my encrypted filesystems by using this tutorial [http://wiki.debian.org/DebianInstaller/Rescue/Crypto](http://wiki.debian.org/DebianInstaller/Rescue/Crypto) You can't use it verbatim as everything in doesn't apply to Karmic but it is a great help. 

After that, I used fsck.ext4 -y to repair my volume and eventually was able to read it, though it was a total mess (many directory names replaced with numbers and such). I was able to get my documents off the drive, however, which was the most important thing. I will need to reinstall the OS again but I learned a lot. 

I hope this helps those of us who got stung by these issues and were running encrypted LVM. 

I'll post more details on what I did to get my data back as soon as I get the chance. 

Mike

---

### Post by andresmh on 2009-09-18
So I have Alpha 5 installed without any updates. I would like to run aptitude upgrade now to get the latest stuff from Alpha 6.

Is the massive breakage that happened two days ago going to affect me or are those problems fixed?

---

### Post by bodhi.zazen on 2009-09-18
> **andresmh said:**
> So I have Alpha 5 installed without any updates. I would like to run aptitude upgrade now to get the latest stuff from Alpha 6.

Is the massive breakage that happened two days ago going to affect me or are those problems fixed?

The problem, or similar fatal problem, can occur at any time if you are running an Alpha release, or even a Beta.

With that said, the problem is actively being worked out and updates have fixed some (most) systems.

Will it work for you , no way to be certain.

---

### Post by useResa on 2009-09-18
> **andresmh said:**
> So I have Alpha 5 installed without any updates. I would like to run aptitude upgrade now to get the latest stuff from Alpha 6.
Is the massive breakage that happened two days ago going to affect me or are those problems fixed?I can only speak for my situation, but the massive breakage that happened two days ago were fixed for me the day after. See [my earlier post]("http://ubuntuforums.org/showpost.php?p=7960147&postcount=106").
Although ... I have to admit ... I did a reinstall (because I messed up) and a full safe-upgrade after that.
But I have no issues anymore.

Having the above said, what is stated bodhi.zazen is very true:
> **bodhi.zazen said:**
> The problem, or similar fatal problem, can occur at any time if you are running an Alpha release, or even a Beta.

With that said, the problem is actively being worked out and updates have fixed some (most) systems.

Will it work for you , no way to be certain.

---

### Post by trulan on 2009-09-18
> **andresmh said:**
> So I have Alpha 5 installed without any updates. I would like to run aptitude upgrade now to get the latest stuff from Alpha 6.

Is the massive breakage that happened two days ago going to affect me or are those problems fixed?
Both of my Karmic installs went through a brief period of being unable to boot, and I waited to update the second one until the first one was fixed, and everyone was saying the recent updates fixed the problem.  It almost seemed like it needed to crash a few times before it decided to work properly.  I didn't do anything special to fix it, just tried different key combinations to see if it would respond to them.  After a few reboots it righted itself.

---

### Post by Giwex on 2009-09-18
I made a fresh install of Alpha 6 on my Acer Aspire 2920z (powered by Intel :)) that worked worked wonderful before few days ago and now during the boot it freezes to a black screen. Before the black screen a huge list of errors.

Cross fingers for next daily live.

---

### Post by andrewabc on 2009-09-18
> **andresmh said:**
> So I have Alpha 5 installed without any updates. I would like to run aptitude upgrade now to get the latest stuff from Alpha 6.

Is the massive breakage that happened two days ago going to affect me or are those problems fixed?

Maybe download and burn alpha 6 to cd (make sure it works). Then try update, and if it fails, you can install alpha 6. :P

---

### Post by maheshasolkar on 2009-09-18
My karmic test laptop (Vaio VGN-T140P) is also affected by this breakage. I tried to follow the 'chroot from LiveCD' method suggested in this thread for the last few days - I am still trying - but to no avail. There are new updates, but nothing seems to be fixing the install.

Last night, I installed Alpha 6 (keeping the /home intact). I still have the same problem. I turn on the laptop, the splash goes on for a while, then a few errors on black console and then black screen. The HDD LED goes on for a few seconds and the system is idle.

I read some folks got their machines up and running after Alpha 6. I wonder if I did anything wrong. Should I try a completely fresh install - including /home? Or should I keep updating the system in chroot until some update fixes it?

---

### Post by autark on 2009-09-18
After suffering a few days without a working Karmic environment, a few hours ago I performed a safe-upgrade (to post-Alpha 6) in a chroot shell, but that didn't really help: the system still tries to switch to graphics mode again and again.  Then I installed and enabled kdm, and that helped! So on my system, gdm doesn't work whereas kdm does. I have an Nvidia card.

---

### Post by beameup on 2009-09-18
Forgive my ignorance here but which log do I look in for those boot up error messages so I can post them here. Maybe that will help. I can boot up after a couple of tries using the technique "hit alt-ctrl-delete and type init3 asap". It reboots then it boots up fine. But if I reboot again it gives a list of kernel errors then goes to black screen. I've done all the recent updates and no change. Nothing lost but time here, it's a test machine that I did a dist-upgrade from jaunty on.

---

### Post by VMC on 2009-09-18
> **beameup said:**
> Forgive my ignorance here but which log do I look in for those boot up error messages so I can post them here. Maybe that will help. I can boot up after a couple of tries using the technique "hit alt-ctrl-delete and type init3 asap". It reboots then it boots up fine. But if I reboot again it gives a list of kernel errors then goes to black screen. I've done all the recent updates and no change. Nothing lost but time here, it's a test machine that I did a dist-upgrade from jaunty on.

There's kernel messages in /var/log/messages & syslog & demesg.

---

### Post by zika on 2009-09-18
> **VMC said:**
> There's kernel messages in /var/log/messages & syslog & demesg./var/log/messages & syslog & dmesg

---

### Post by beameup on 2009-09-18
thanks, i looked through there and didn't see anything resembling the boot errors. Will try ctrl s or the pause key and see if I can stop it to record them by hand or camera.

---

### Post by beameup on 2009-09-18
OK, see attached images. Something about a bad symlink

---

### Post by darco on 2009-09-18
> **Vladimir Hidalgo said:**
> 

1. Start normal and wait for the black screen.
2. Enter login/pw
3. As per tmschmitz instructions (thank you!):
sudo start dbus
sudo start hal
sudo /etc/init.d/NetworkManager start

4. Verify you have internet:
ping google.com (press Ctrl+C when you see a response)

7. If you have internet, then run: "sudo apt-get update && sudo apt-get dist-upgrade -y"

8. Wait until it finish and restart (took about 20-30 mins)

9. Everything should be normal again.

It will update several packages related to boot process.


P.S.: you may not be able to use your Wireless internet in the process, so you better connect a network cable to your Ethernet port to solve this.

This worked for me.......

darco

---

### Post by maheshasolkar on 2009-09-18
> **beameup said:**
> OK, see attached images. Something about a bad symlink

I get exactly this! Sadly, I haven't been able to find any bug report on Launchpad that matches this. Is there one?

---

### Post by darco on 2009-09-18
> **maheshasolkar said:**
> I get exactly this! Sadly, I haven't been able to find any bug report on Launchpad that matches this. Is there one?

After I successfully logged back in KK, I still see that Symlink error.....

darco

---

### Post by akernan on 2009-09-18
I was able to use the live cd for recovery and issue the chroot cmd.  I had to run apt-get upgrade a few times to get everything. I am able to boot with 2.6.31-9 but not 2.6.31-10.  Boot seems slower, but at least I can boot now & recovered.  Thanks for all the info in this post.

---

### Post by VMC on 2009-09-18
> **maheshasolkar said:**
> I get exactly this! Sadly, I haven't been able to find any bug report on Launchpad that matches this. Is there one?

LP [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654"), Read post#12 of the LP.

---

### Post by beameup on 2009-09-18
Here's a good one. My laptop boots OK up when it's on battery only. Still shows those errors but it boots into X.  Thanks for the link VMC, I'll wait until next week and see how it goes. 

I was gonna take that advice and edit the bad symlinks but I opened up one of those udev rule files and that %k was all over it.

---

### Post by maheshasolkar on 2009-09-19
> **VMC said:**
> LP [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654"), Read post#12 of the LP.

So these warnings are harmless and will be fixed next week? The lock up (black screen) is not related to this?

I still fail to understand what is the root cause of the boot failure and which LP bug I should be following!

---

### Post by trulan on 2009-09-19
The udev warning messages (bad symlinks) are supposed to be harmless.  Everyone who has been updating should be seeing those right now.  They are supposed to be unrelated to the black screen boot failures.  I think the main reason the udev errors are getting so much attention is that we are all a little jumpy thanks to the Sept. 15 meltdown.

The main cause of the boot failures, as I understand it, was that the Sept. 15 updates turned the boot process over to upstart.  Upstart called for mountall, only mountall was not yet installable.  Hence, every system that was updated between the upstart update and the roll-out of mountall was rendered un-bootable.

Obviously, it's a lot more complicated than that and there are still some residual breakages left over from the mess.

---

### Post by beameup on 2009-09-19
Yea, I get those symlink messages on our Acer Netbook but it boots OK. Something else is stopping my old test laptop from booting when power is attached.

---

### Post by VMC on 2009-09-19
From a terminal type ```
grep "SYM" /var/log/syslog
```  I believe those .3 & .4 refer to line numbers. Then look inside "/lib/udev/rules.d/50-udev-default.rules", for lines3&4:

```
SUBSYSTEM=="block", SYMLINK{unique}+="block/%M:%m"
SUBSYSTEM!="block", SYMLINK{unique}+="char/%M:%m"
```


So I'm thinking the above lines are the cause of the errors.

---

### Post by LindsayD on 2009-09-19
OK, I've tried what Jim and others have suggested:

I plugged into the hub with a network cable

I booted into recovery mode and chose the netroot option

simply using ping [www.google.com](www.google.com) gives the error message:
host google.com not found

I then tried start dbus 
start hal

/etc/init.d/NetworkManager start 

(using start network-manager gives error message about upstart)

I was given a number of comments about options and then used 
/etc/init.d/NetworkManager restart

This seemd ok, then tried 
ping [www.google.com](www.google.com)

and again host not found

trying various update/upgrade etc did not work because there was no internet connection!!!

I did try start gdm as suggested by another user, but all this did was give me a flashing black screen and I had to force quit using the off button. 

So it looks like reinstall unless anyone else has any suggestions.

---

### Post by VMC on 2009-09-19
Are you getting "host not found" or "unknown host"
cat /etc/hosts
Does your hardware work with another OS?

---

### Post by maheshasolkar on 2009-09-19
> **trulan said:**
> The udev warning messages (bad symlinks) are supposed to be harmless.  Everyone who has been updating should be seeing those right now.  They are supposed to be unrelated to the black screen boot failures.  I think the main reason the udev errors are getting so much attention is that we are all a little jumpy thanks to the Sept. 15 meltdown.

The main cause of the boot failures, as I understand it, was that the Sept. 15 updates turned the boot process over to upstart.  Upstart called for mountall, only mountall was not yet installable.  Hence, every system that was updated between the upstart update and the roll-out of mountall was rendered un-bootable.

Obviously, it's a lot more complicated than that and there are still some residual breakages left over from the mess.

Well that is a really informative post, thanks!

So, is mountall still uninstallable - at least the right version? I've been updating my system via chroot daily since 15th Sept. It has mountall (0.1.6) installed. But it still fails to boot.

To me, reason the udev errors are getting so much attention is that my system won't boot! I am wondering if I am in the minority. Or all systems that were rendered unbootable by 15th Sept updates are still unbootable.

---

### Post by trulan on 2009-09-19
By now, you are in the minority.  All the breakage from Sept. 15 **should** have been fixed by updating on Sept. 16.  Obviously in your case something is still broken.

Saying that is easy enough.  Actually finding your problem and fixing it is another story.  I'm pretty sure you can rule out the udev errors though.

I held back the updates on my laptop until the evening of Sept. 16, and when I rebooted it I was greeted with a black screen.  Ctrl+Alt+F1 (maybe Ctrl+Alt+Del) got me to a tty login I think (or maybe I used one of the other tricks I read about - I don't remember).  The screen never displayed anything.  But it responded to typed commands by blinking the hard drive light.  So I ran 'sudo fsck' and the hard drive worked for several minutes.  I then typed 'sudo reboot' and the system rebooted successfully.

I guess that would constitute 'blindy typing commands' which is something we all know better than doing. ;)

Not that I expect that to help you - sorry, wish I could.

---

### Post by bodhi.zazen on 2009-09-19
my ubuntu servers were affected by the updates and my bug on launchpad is still open.

9.10 is still in alpha and you should not run 9.10 unless you are prepared for (potential)  breakage.

---

### Post by maheshasolkar on 2009-09-20
Well, in my case, turns out KMS was the issue. I came across this thread that shed some light on the situation:

  [http://www.gossamer-threads.com/lists/linux/kernel/1121485#1121485](http://www.gossamer-threads.com/lists/linux/kernel/1121485#1121485)

I added 'nomodeset' to GRUB_CMDLINE_LINUX_DEFAULT variable in the /etc/default/grub file and ran 'update-grub'.

This gets me a desktop. Its a really ugly boot experience - text mode first, then the new dark splash, then a login prompt, new dark splash again. But that is still so much better than no boot at all!

---

### Post by luvr on 2009-09-20
I wanted to try out Karmic Alpha6, so I downloaded and burned the i386 and amd64 desktop images. On my AMD64 computers, with an integrated ATI video adapter, neither version will properly initialise the GUI, though.

When the GUI starts, the gdm splash screen gets shown. Then, a little later, the screen goes black, the splash screen reappears, the screen goes black again, etc.; the screen simply keeps flashing on and off.

I try to switch to a character-based console (*<Ctrl>-<Alt>-<F1>*), but that doesn't do anything. Sometimes *<Ctrl>-<Alt>-Del>* will reboot the computer, at other times, even that won't work; the *<Alt>-<PrtScr>-**REISUB*** sequence will work, though.

I did once succeed in getting to a character-based console (but, unfortunately, I don't remember which special options I used), but as soon as I attempted to start gdm, the problem reoccurred.

There's not much more I can do; I don't even get far enough to install the system--let alone update it to try and solve any of these problems. Obviously, I'm not the only one with this problem--see, e.g., [Just can't log in! Problem with GDM?]("http://ubuntuforums.org/showthread.php?t=1269047")

**P.S.:** On my Dell Studio 17 laptop, the Karmic Alpha6 LiveCD *does* successfully start up, but I don't want to install it on that computer.

I'll try the alternate images next, and see how far I get with these.

---

### Post by ELD on 2009-09-20
@[luvr]("http://ubuntuforums.org/member.php?u=68732") to quote my post in another thread:
> 
Sounds like the ATi problem i am having, although it got fixed a day after alpha6 i think so i am waiting for the daily cds to start being built again so i can use one of them (none have been built since 17th?).

Someone did fix their problem in alpha6 by doing this:
> 
OK, fixed, in my case:

1. Boot to 'recovery' mode.
2. Do apt-get update, upgrade, dist-upgrade.
3. Reboot.

I'm now able to login to GNOME in regular mode.


---

### Post by bodhi.zazen on 2009-09-20
> **ELD said:**
> @[luvr]("http://ubuntuforums.org/member.php?u=68732") to quote my post in another thread:

Someone did fix their problem in alpha6 by doing this:

My previous installations of 9.10 all remain broken. Updating has not fixed any of my (3) broken systems (all 3 are up to date).

I performed a fresh install on a desktop, and Alpha 6 , both 32 and 64 bit, are working.

I doubt my old installations will ever recover.

Server side, 9.10 continues to have problems, even with a fresh install.

---

### Post by c3apollyon on 2009-09-20
Also having these problems but my issues seem to worse because I am using a Bluetooth mouse and keyboard which do not seem to initialize if the boot crash happens too early on - leaving me stuck at the command prompt with no hope.

Does anyone know how to pass a command through Grub or otherwise when I have keyboard access so that bluetooth is immediately loaded - giving me at least keyboard access when the boot interrupts seconds later...?

---

### Post by ELD on 2009-09-20
> **bodhi.zazen said:**
> My previous installations of 9.10 all remain broken. Updating has not fixed any of my (3) broken systems (all 3 are up to date).

I performed a fresh install on a desktop, and Alpha 6 , both 32 and 64 bit, are working.

I doubt my old installations will ever recover.

Server side, 9.10 continues to have problems, even with a fresh install.

Well alpha6 cd for me did not boot and the bug was marked as fix released after alpha6 was released, so i am hoping in a day or so once the daily cd's start up again i can finally test out karmic heh.

---

### Post by luvr on 2009-09-20
> **ELD said:**
> @[luvr]("http://ubuntuforums.org/member.php?u=68732") to quote my post in another thread:

Someone did fix their problem in alpha6 by doing this:[QUOTE=tchock;7979835]OK, fixed, in my case:

1. Boot to 'recovery' mode.
2. Do apt-get update, upgrade, dist-upgrade.
3. Reboot.

I'm now able to login to GNOME in regular mode.[/QUOTE]
That's all good and well, but this assumes that you can *at least* get alpha6 **installed** in the first place... but I cannot even get the CD to successfully boot, let alone start the install.

Having said that, if I'm more successful with the alternate CD, this advice may come in handy still. I'll certainly keep it in mind!

---

### Post by ELD on 2009-09-20
> **luvr said:**
> That's all good and well, but this assumes that you can *at least* get alpha6 **installed** in the first place... but I cannot even get the CD to successfully boot, let alone start the install.

Having said that, if I'm more successful with the alternate CD, this advice may come in handy still. I'll certainly keep it in mind!

Can you not just choose the "install" option instead of booting into the live environment?

---

### Post by VMC on 2009-09-20
> **ELD said:**
> Can you not just choose the "install" option instead of booting into the live environment?
Thinking about this a minute. The "install" option tries to boot to a live system **before** it actually installs. It would be great it the livecd had an option from recovery to allow this. Maybe it does, so you wouldn't have to again download the alternate install.
I haven't tried that before.

---

### Post by beameup on 2009-09-20
I just caught a glimpse of an error right as the screen went black, something like "Acer Travelmate - Unsupported BIOS version" blah blah. too fast for me to capture, but that's probably what my issue is. If I get back into the system I'll search the logs for it. If not, it's back to Jaunty to stay or try something else for fun.

---

### Post by Kareeser on 2009-09-21
Got breakage here too. Boots, lots of error messages about udev and rules (too quick to see), and then the boot process hangs at "Starting NFS Kernel Daemon". Doesn't pass or fail, just hangs.

I figured it was a borked update since I hadn't updated for awhile, and it was never a fresh install to begin with (upgraded from Jaunty by changes sources.list, way back in Alpha 1!), but a fresh re-install did nothing.

Other problems: The resolution in the terminal session didn't change like the older kernel did. I was stuck with the huge font... unlike the smaller terminal fonts and properly proportioned Ubuntu loading graphic.

Reverted back to Jaunty for the time being :)

---

### Post by Richy on 2009-09-21
Yesterday, I did an update on Jaunty ( as this used to be pretty save)
Today morning, my laptop didn't want to boot anymore..

fixed it by:

mount -a /dev/sda.. /boot
/etc/init.d/dbust start #where it complains that this is a upstart-script now..
/etc/ini.d/hal start
/etc/init.d/NetworkManager start
mount i915 //my intel graphics
/etc/init.d/gdm start

It's working again after..
how can I automize that?

Richard

---

### Post by luvr on 2009-09-21
> **ELD said:**
> Can you not just choose the "install" option instead of booting into the live environment?
Nope--Same issue, as **VMC** noted in a follow-up post.

---

### Post by luvr on 2009-09-21
I have just installed Karmic Alpha6 from the alternate CD; in fact, I'm running it right now.

Installation went smoothly. When I subsequently attempted to boot the system, the same kind of problem happened as on the LiveCD. The gdm splash screen would appear, and the login prompt would show up. Then, when I specified my username and password, the screen would blank, ..., and the splash screen with the login prompt would reappear. *(On the LiveCD, the login prompt would not appear, since the system would attempt a default login straight away, without prompting.)*

I then rebooted, and selected recovery mode. The *"Recovery Menu"* would briefly display--**very** briefly, indeed--and the system would proceed with a normal startup (i.e., it would show the gdm splash screen with the login prompt). This time, however, I could get at a character-based console (*<Ctrl>-<Alt>-<F1>*), and select a root console from the recovery menu.

I stopped gdm (just in case), with the following command:
```
/etc/init.d/gdm stop
```(Note that I didn't have to type *"sudo"* because I was running a root console.)

Then, I simply did:
```
apt-get update
apt-get dist-upgrade
```
... and now, the system is running fine.

Obviously, this is just an alpha release, so I wasn't all too surprised to see a crash report being generated at one point (it was a Nautilus crash, which was already reported to Launchpad).

All in all, the system works pretty well now.

---

### Post by pystyj on 2009-09-21
I don't have a access to wired network at the moment, so what are my options?

Is there a few packages that I could download and install and get to gnome?
Is there a way to get wlan connection work from terminal and use it to dist-upgrade?

Thanks!

---

### Post by rbmorse on 2009-09-21
Just installed from today's daily 64-bit LiveCD.

All is well.  It installs and boots to the desktop. All is forgiven.

---

### Post by pystyj on 2009-09-21
> **pystyj said:**
> I don't have a access to wired network at the moment, so what are my options?

Is there a few packages that I could download and install and get to gnome?
Is there a way to get wlan connection work from terminal and use it to dist-upgrade?

Thanks!

[http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657)

It worked for me with packages:
mountall
upstart (dep mountall)
initscripts (deb upstart)

Now I'm too afraid to upgrade ;)

---

### Post by omarly on 2009-09-21
> **darco said:**
> This worked for me.......

darco

I did a fresh install on top of 9.04. Then just nr 

7: "sudo apt-get update && sudo apt-get dist-upgrade -y"

Everything OK. :) thx

---

### Post by hewhocutsdown on 2009-09-21
I get stuck running 'sudo start hal', it responds with:

init: hal main process (<pid>) killed by SEGV signal
init: hal main process ended, respawning
...
init: hal respawning too fast, stopped

Any ideas on this?

---

### Post by Thura on 2009-09-21
If you are dropped to a console prompt, without starting gdm, don't forget to check your grub-version .... After installing grub2, that prob is solved.:)

---

### Post by hewhocutsdown on 2009-09-22
Just to follow up

I reinstalled from the Alpha 6 disc, without formatting. Things are looking ok at present.

---

### Post by narunas on 2009-09-26
OK - having the same issue - patiently awaiting a fix of some kind

Sony Vaio TX650
Karmic

was working just fine this morning before update.
it appears to be a display renderer issue - any way to try to a basic Ubuntu display using recover type drivers?

Narunas

---

### Post by jazz452 on 2009-10-09
> **Thura said:**
> If you are dropped to a console prompt, without starting gdm, don't forget to check your grub-version .... After installing grub2, that prob is solved.:)

I pressed alt+ctrl+f2 and logged in as root and that worked fine then did all updates will let u know ho it goes.
O and like the new splashy look lets just hope these updates im doing solve problems

---

### Post by rv65 on 2009-10-12
My Dell D610 had the init breakage. I had just bought a new wireless mouse which really came in handy. I downloaded the updates and used my ethernet connection to get the. I had to updated using without the GUI. It took 2 major update packages to get it working. Once that was done it's perfect.

Edit:  I also had to go into software sources to add my repos again. It wouldn't get the updates but doing that did.

---

### Post by Nightstrike2009 on 2009-10-13
Me too I installed karmic beta on my system and got an error relating to hd0 (Wrong drive it was hd3) and wubi installation also broke. The only way i can use it is "Live" from CD neither wubi or dual-booting the full system work for me hope this is fixed before final release or I will stick with 9.04 until 10.4 is released. 
(As no other choice will be available to me as I prefer to use Ubuntu for my linux)) :-(

---

