---
title: "Upgrade to 10.04 issue - Boot Screen Hang"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Remixer96 on 2010-05-02
I'll say up front I'm still new to Ubuntu, so if I've missed anything obvious please forgive me.

I chose to upgrade my 9.10 installation to 10.04 via the update manager. Especially since I was going to be gone for long periods of time, this seemed like a good idea.

Downloading went fine, but I had to leave for a two day trip once I clicked install. When I returned, I noticed the machine was still on the purple loading screen with four dots. When I shut it down and rebooted, it got to the same screen. 

Pressing escape to show the text behind the screen showed two fails and one oddity: 

(1)
* Setting sensors limits
"Rather than invoking init scirpts through /etc/init.d, use the service(8) utility, e.g. service S49console-setup start

Since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility, e.g. start S49console-setup
start: Unkown job: S49consile-setup"

(2)
* Starting VirtualBox kernel modules
* No suitable module for running kernels found

(3)
* Starting TiMidity++ ALSA midi emulation...         [ok]
Home directory /etc/timidity not ours
<<<Output ends here>>>

============

Any ideas (sans a full fresh install) would be helpful at this point.

---

### Post by mettlewk on 2010-05-02
Same problem,

I have been using Hardy Heron and wanted to upgrade.

I downloaded the iso Image to do a clean install on a gateway 7330G7 laptop. 

The laptop fails to boot from the CD rom.  I thought I would go in by the back door, I did a clean install from the 9.10 iso image disk. The laptop had NO problem booting from that disk.

I did a clean install, did all the updates and then told it to upgrade to 10.4. 

all went well until the reboot, when I was locked out.

There is something wrong in the 10.4 boot sequence.

Luckily for me, I have full backup of data, so reloading 9.10 and running with that will work for now.

Now I know that if the CD won't boot, neither will the upgrade.

Just a few hours of mucking around lost.

I have 10.4 running just fine in Parallels on my Mac after upgrading from 9.10
The 10.4 iso image disk booted just fine when run on older Compac desktop. 

Mettlewk.

---

### Post by kimberfella616 on 2010-05-09
I am having similar problems.  Sadly, I am not in as good a shape with backups.  I did a 10.04 update and lef for the evening; when I came back and started my laptop I keep getting hung up on the boot screen.  I get the following:

```
fsck from util-linux-ng 2.17.2
udevd[2849]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10

udev[2849]: specified user 'usbmux' unknown

/dev/sda1: clean, 2273797/14721024 files. 42775053/58880225 blocks
 * Starting AppArmor profiles          Skipping profile in /etc/apparmor .d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5
                         [OK]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S49console-setup start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may use the start8) utility, e.g. start S49cnsole-setup
start: Unknown job: S49console-setup
*Speech-dispatcher configured for user sessions
*Starting the Winbind daemon winbind           [OK]
*Starting Common Unix Printing System: cupsd           [OK]
*PulseAudio configured for per-user sessions
*Enabling additional executable binary formats binfmt-support           [OK]
*Checking battery state...           [OK]
*Starting init crypto disks...           [OK]
```



THANKS FOR ANY AND ALL HELP!!!!!!!!!!

---

### Post by brent0n on 2010-05-15
i'm having the same issue. it says

starting apparmor profiles [ok]
skipping profile in /etc/apparmor.d/disable: usr.bin.firefox [ok]
setting sensor limits
setting console screen modes and fonts
^[[8;2R


then hangs. it's also after an upgrade from kubuntu 9.10 to 10.04


note, i had been using it and have rebooted successfully a few times, it just happened the last time it rebooted.

---

### Post by trians on 2010-07-26
Have the same problems as Remixer96 here.

any idea ?

thanks before.

---

### Post by LtPitt on 2010-08-27
I'm in the same deep mud.

Can anybody help?

I need desperately this machine back running again since it's a server :(

The services still work (like samba) but I can't use the computer anymore...

ps
I've managed to log in!
ctrl+alt+f4 (or any other screen) did the game.

phew.

pps
If anyone has a final solution for this I'd be the happiest

---

### Post by LtPitt on 2010-08-31
Nope :/

The problem's still there and I think I've just been lucky to log on...

The server works perfectly, btw (samba, mysql and other services 
running greatly) and I can logon using ssh...

Any hints about command or modifications to let my little buddy live again? :(

I've disabled apparmor but the problem is not there...

Is there any way to get a verbose output of my boot with errors in 10.4?

Thanks :'(

---

### Post by e.m.fields on 2010-09-06
Hi. Having same issue in Maverick Alpha 3.  Hangs at "checking battery state".

most common suggestion I've seen posted is that it has something to do with graphics drivers, maybe solution to reconfigure xorg.

Please post if you get a solution, thanks.

---

### Post by LtPitt on 2010-09-11
I've set grub in debug mode and disabled the splash screen so now I can see all errors and the text displayed during boot...

No luck :/

It just hangs without letting terminal 1 to get to login.

If I switch terminal manually to 2, 3 or anything else I'm able to log on happily.

I don't have a clue to solve this :(
I thought linux was the best choice to setup a small fileserver and a mysql server but I start thinking that some problems take a lot of effort to be solved and finding information is not easy, at least for me...

---

### Post by morrcahn on 2010-12-10
Yeah, I am having the same problem with 10.10 so I uninstalled apparmor. That got rid of that problem but it still hangs with
```
fsk from util-linux-ng 2.17.2
/dev/sda1: clean, 1412115/610800 files, blah blocks
fsck from '  '
/dev/sda2: clean blah files, blah blocks
init: ureadahead-other main process (755) terminated with status 4
* Setting sensors limits                                                                 [OK]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
                                                                                                  [OK]
_

```Similar to above, anything would help. Thanks.

---

### Post by Francis Russell on 2012-02-17
I don't know if anyone's still watching this thread, but I recently encountered a similar issue. The problem appears to be something with console-tools.sh, but it's non-deterministic so my attempt to debug it failed.

Removing the console-tools package fixed it for me.

---

