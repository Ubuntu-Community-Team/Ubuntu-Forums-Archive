---
title: "Fresh Install of 11.10 problem"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by merediths on 2011-10-16
So, I tried to do a fresh install of Oneiric, and after installation, when I'm restarting, I get a bunch of messages and a blinking underscore.  I can't exactly take a screen shot, but the contents of my screen say (roughly)

fsck from util-linux 2.19.1
/dev/sda1: clean, 152960/15007744 files, 1694799/60001536 blocks
*Starting network connection manager
*Stopping Flush boot log to disk
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
*Starting AppArmor profiles                            [OK]
speech-dispatcher disabled; edit/etc/default/speech-dispatcher
Checking for running unattended-upgrades:
*Stopping Failsafe Boot Delay                                          [OK]
*Stopping System V initialisation compatibility                   [OK]
*Starting System V runlevel compatibility                          [OK]
*Stopping automatic crash report generation                     [[COLOR=Red]fail[/COLOR]]
*Starting ACPI daemon                                                    [OK]
*Starting save kernel messages                                        [OK]
*Starting CPU interrupts balancing daemon                        [OK]
*Starting anac(h)ronistic cron                                            [OK]
*Starting regular background program processing daemon   [OK]
*Starting deferred execution scheduler                                [OK]
*Stopping save kernel messages                                        [OK]
*Stopping cold plug devices                                                [OK]
*Stopping log initial device creation                                    [OK]
*Starting configure network device security                         [OK]
*Starting LightDM Display Manager                                     [OK]
*Starting Userspace bootsplash                                          [OK]
*Stopping Userspace bootsplash                                          [OK]
*Starting bluetooth                                                            [OK]
[COLOR=Orange]*[/COLOR][COLOR=Black]Pulse Audio configured for per-user sessions
saned disabled; edit /etc/default/saned


At least that's what it says THIS time. Every time I boot, it looks slightly different, but they all end with a blinking underscore and then nothing happens.  I have tried reinstalling with both USB and CD, as well as redownloading the iso and reinstalling, but no luck. Also, it runs fine when I just boot off the CD/USB.

Is anyone else having this problem? Any solutions?
[/COLOR]

---

### Post by MAFoElffen on 2011-10-16
> **merediths said:**
> So, I tried to do a fresh install of Oneiric, and after installation, when I'm restarting, I get a bunch of messages and a blinking underscore.  I can't exactly take a screen shot, but the contents of my screen say (roughly)
```

fsck from util-linux 2.19.1
/dev/sda1: clean, 152960/15007744 files, 1694799/60001536 blocks
*Starting network connection manager
*Stopping Flush boot log to disk
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
*Starting AppArmor profiles                            [OK]
speech-dispatcher disabled; edit/etc/default/speech-dispatcher
Checking for running unattended-upgrades:
*Stopping Failsafe Boot Delay                                          [OK]
*Stopping System V initialisation compatibility                   [OK]
*Starting System V runlevel compatibility                          [OK]
*Stopping automatic crash report generation                     [[COLOR=Red]fail[/COLOR]]
*Starting ACPI daemon                                                    [OK]
*Starting save kernel messages                                        [OK]
*Starting CPU interrupts balancing daemon                        [OK]
*Starting anac(h)ronistic cron                                            [OK]
*Starting regular background program processing daemon   [OK]
*Starting deferred execution scheduler                                [OK]
*Stopping save kernel messages                                        [OK]
*Stopping cold plug devices                                                [OK]
*Stopping log initial device creation                                    [OK]
*Starting configure network device security                         [OK]
*Starting LightDM Display Manager                                     [OK]
*Starting Userspace bootsplash                                          [OK]
*Stopping Userspace bootsplash                                          [OK]
*Starting bluetooth                                                            [OK]
[COLOR=Orange]*[/COLOR][COLOR=Black]Pulse Audio configured for per-user sessions
saned disabled; edit /etc/default/saned
[/COLOR]
```[COLOR=Black]
At least that's what it says THIS time. Every time I boot, it looks slightly different, but they all end with a blinking underscore and then nothing happens.  I have tried reinstalling with both USB and CD, as well as redownloading the iso and reinstalling, but no luck. Also, it runs fine when I just boot off the CD/USB.

Is anyone else having this problem? Any solutions?
[/COLOR]Welcome to Ubuntu!

Sidenote- Administrative wise in this forum, please post logs, commands and output within CODE tags. hjem posting or editing plaease hightlight the text , then press the "#" icon in the posting toolbar. Iaht will put the CODE tags around your selected text.

On your posted output...  It looks okay, albeit the crash report line.  Usually it gets about there or sooner if there a graphics problem... First you should confirm that the Linux kernel is booting.

Can you get to a Grub Menu?  If you don't usually see it when booting- On boot, hold down the shift key.  When the grub menu comes up, press "e'.  That will put you into an edit mode.  Arrow down to the line that begins with "linux".  Arrow right to where is says "quiet splash vt.handoff=7" and replace it with "--verbose single". Press <cntrl><x> to boot.  That should get it to try to boot the kernel with verbose meassging turned on- to a TTY Text Console.

If it finishes booting to a command prompt, the step above should confirm that everything is okay with the kernel and it's system modules.  If all is well with that, then your problem lies on a different layer... In the X-Session, graphics drivers or desktop.

I'll stop there... I think that seeing the crash report generated halfway through the boot sequence, that there is some kind of problem there. It's at the point where it might be hitting the graphics and having a problem, but that doesn't usually throw a generated problem report.  That concerns me.

---

### Post by Namloc on 2011-10-17
Hello,

I appear to be having the exact same problem (I get the same screen on start-up). I have followed the steps in the previous post and can confirm that the problem is not kernel-related. It must therefore be another issue.

Is there any straight forward way to sort this out?

---

### Post by Stepway on 2011-10-17
I'm having the same problem, noticed another thread - others with intel gma chipset have identical issues. Can't even run on the usb flash drive. Waiting for a solution!

---

### Post by MAFoElffen on 2011-10-17
> **MAFoElffen said:**
> Welcome to Ubuntu!

[COLOR=Red]Can you get to a Grub Menu?  If you don't usually see it when booting- On boot, hold down the shift key.  When the grub menu comes up, press "e'.  That will put you into an edit mode.  Arrow down to the line that begins with "linux".  Arrow right to where is says "quiet splash vt.handoff=7" and replace it with "--verbose single". Press <cntrl><x> to boot.  That should get it to try to boot the kernel with verbose messaging turned on- to a TTY Text Console.[/COLOR]

If it finishes booting to a command prompt, the step above should confirm that everything is okay with the kernel and it's system modules.  If all is well with that, then your problem lies on a different layer... In the X-Session, graphics drivers or desktop.


@merediths, Namloc and Stepway

If it boot using the instructions highlighted above in red, then do 
```

lspci -vnn | grep VGA

```
Write down those results.

Type 
```

sudo reboot.

```
[COLOR=Black]On boot, hold down the shift key.  When the grub menu  comes up, press "e'.  That will put you into an edit mode.  Arrow down  to the line that begins with "linux".  Arrow right to where is says  "quiet splash" and before it says "vt.handoff=7"... 
 - If the output you wrote down said "nVidia", insert "nomodeset"
 - If the output you wrote down say "ATI Radeon", insert "radeon.mode=0"
 - If the output you wrote down said ", Intel" insert "i915.modeset=0"
Press <cntrl><x> and it will boot.

If it boot into the GUI, Click on the user_name in the upper-right-most of the top bar > select Sytem Settings > Select Additional Drivers. > Install appropriate driver.
[/COLOR]

---

### Post by Stepway on 2011-10-17
Thanks for feed back. Should add, sadly, mine didn't get as far as the 1st post. I get the same result, but on the install:(.
 It won't even run 11.10 from the flash drive. It stops during the Ubuntu 11.10 purple screen, has a brief message that begins with    "**B43-phyo error firmware file B43/uncode15.fw**    "  then I end up with the screen much like that posted on the 1st thread. 
I can't help thinking this is an issue with the **intel gma chipset**On my Dell 12 mini
11.04 was fine.
Stuck at this stage I don't think I can use the MAFoElffen fix?  maybe the error message sheds some light?

---

### Post by Namloc on 2011-10-17
Thanks for helping out MAFoElffen. I have just tried to go through your suggested troubleshoot however once I got into the TTY Text Console I could not type the symbol "|". Instead the button (shift + \) came up with "~".

Nevertheless, I tried all three of the options you mentioned and not much happened. For the "nVidia" and ",Intel" outputs, the insertions resulted in the boot screen stopping at the line "Checking battery state ... ". I wait for several minutes and nothing. When I inserted "radeon.mode=0", I got another line past this, but it too finished on the line:
```
[  20.378333] iwlagn 0000:03:000: Aggregation not enabled for tid 0 because load=6
```

Anything else I should try?

---

### Post by Bao2 on 2011-10-17
I had the same problem, usually it stopped with the fail in this line:

*Starting System V runlevel compatibility            [FAIL]

but also in others.


I could solve the problem. Here is what I did:

Instead starting using the default first entry in GRUB (kernel 3...)
I used the second entry (kernel 3 (recovery mode)

Then a new window with options appears and I choose the first one that
said "resume ...."

And ubuntu started using this recovery mode. Then open the "Additional Drives" program and there are two drivers:

1): NVIDIA accelerated graphics driver (version current) [Recommended]
2): NVIDIA accelerated graphics driver (post-release updates) (version current-updates)

I was using the SECOND one. I deactivated it and now ubuntu 11.10 starts without any problem.

Now go to Additional Drivers and active the FIRST one and no hangings at the moment.

So the second driver seems have some problem and the solution is use the first one.

---

### Post by Namloc on 2011-10-17
Thanks Bao2. Unfortunately I haven't worked with these text based terminals before. What do I need to type in to open the "Additional Drives" program and what do I need to type in for the deactivation?

---

### Post by Bao2 on 2011-10-17
In the launcher to the left you have System Settings. Open and you have Additional drivers there too.

Then in Additional drivers you see two nvidia drivers and they must have the dot to the left in gray. If one is in green you are using that driver at this moment.
You must activate the driver that has "recommended". If you have the other, deactivate it, reboot and activate the "recommended".

---

### Post by MAFoElffen on 2011-10-17
> **Namloc said:**
> Thanks for helping out MAFoElffen. I have just tried to go through your suggested troubleshoot however once I got into the TTY Text Console I could not type the symbol "|". Instead the button (shift + \) came up with "~".

Nevertheless, I tried all three of the options you mentioned and not much happened. For the "nVidia" and ",Intel" outputs, the insertions resulted in the boot screen stopping at the line "Checking battery state ... ". I wait for several minutes and nothing. When I inserted "radeon.mode=0", I got another line past this, but it too finished on the line:
```
[  20.378333] iwlagn 0000:03:000: Aggregation not enabled for tid 0 because load=6
```Anything else I should try?
Thats the wrong symbol... look to ight of keyboard, above the <enter> Key... It says "\" and if you hold the <shift> key it says '|"... which in Linux is a directional piping symbol.

While in the text console... does it say it has an xorg.conf file present?
```

ls /etc/X11/xorg.conf

```

---

### Post by MAFoElffen on 2011-10-17
> **Bao2 said:**
> I had the same problem, usually it stopped with the fail in this line:

*Starting System V runlevel compatibility            [FAIL]

but also in others.


I could solve the problem. Here is what I did:

Instead starting using the default first entry in GRUB (kernel 3...)
I used the second entry (kernel 3 (recovery mode)

Then a new window with options appears and I choose the first one that
said "resume ...."

And ubuntu started using this recovery mode. Then open the "Additional Drives" program and there are two drivers:

1): NVIDIA accelerated graphics driver (version current) [Recommended]
2): NVIDIA accelerated graphics driver (post-release updates) (version current-updates)

I was using the SECOND one. I deactivated it and now ubuntu 11.10 starts without any problem.

Now go to Additional Drivers and active the FIRST one and no hangings at the moment.

So the second driver seems have some problem and the solution is use the first one.
Good Job.  One down- 2 to go...

---

### Post by MAFoElffen on 2011-10-17
> **Namloc said:**
> Thanks Bao2. Unfortunately I haven't worked with these text based terminals before. What do I need to type in to open the "Additional Drives" program and what do I need to type in for the deactivation?
Unfortunately, that applet is GUI based and you have to have it booting into a graphics screen to use that. 

Please post the output of the lspic command using the clarification from 2 posts back... Post that info and that will tell us what Video card you have... so we can figure out how to get you going.

---

### Post by MAFoElffen on 2011-10-17
> **Stepway said:**
> Thanks for feed back. Should add, sadly, mine didn't get as far as the 1st post. I get the same result, but on the install:(.
 It won't even run 11.10 from the flash drive. It stops during the Ubuntu 11.10 purple screen, has a brief message that begins with    "[COLOR=Red]**B43-phyo error firmware file B43/uncode15.fw** [/COLOR]   "  then I end up with the screen much like that posted on the 1st thread. 
I can't help thinking this is an issue with the **intel gma chipset**On my Dell 12 mini
11.04 was fine.
Stuck at this stage I don't think I can use the MAFoElffen fix?  maybe the error message sheds some light?
I believe that error is a separate issue, as that error concerns wireless card firmware files.

Can you boot a LiveCD (without having to use any kernel boot settings) into the "try" Live Image?

If you can, maybe it would be corrected with a reinstall fresh as new(?)

---

### Post by jimbo99 on 2011-10-17
> **MAFoElffen said:**
> Welcome to Ubuntu!

Sidenote- Administrative wise in this forum, please post logs, commands and output within CODE tags. hjem posting or editing plaease hightlight the text , then press the "#" icon in the posting toolbar. Iaht will put the CODE tags around your selected text.

On your posted output...  It looks okay, albeit the crash report line.  Usually it gets about there or sooner if there a graphics problem... First you should confirm that the Linux kernel is booting.

Can you get to a Grub Menu?  If you don't usually see it when booting- On boot, hold down the shift key.  When the grub menu comes up, press "e'.  That will put you into an edit mode.  Arrow down to the line that begins with "linux".  Arrow right to where is says "quiet splash vt.handoff=7" and replace it with "--verbose single". Press <cntrl><x> to boot.  That should get it to try to boot the kernel with verbose meassging turned on- to a TTY Text Console.

If it finishes booting to a command prompt, the step above should confirm that everything is okay with the kernel and it's system modules.  If all is well with that, then your problem lies on a different layer... In the X-Session, graphics drivers or desktop.

I'll stop there... I think that seeing the crash report generated halfway through the boot sequence, that there is some kind of problem there. It's at the point where it might be hitting the graphics and having a problem, but that doesn't usually throw a generated problem report.  That concerns me.


Oh please, listen to yourself.  If he can't get it installed how can he get to the logs, and what good are logs to people helping others.  Please read what the users are posting in this forum and then work from that.  If you need a specific log to help them you need to tell them where to go and what part of the log you need and how to get at that and where to post.  I certainly don't want to see log files here because they often do little good, confuse new users, and spam the threads.

Whatever happened in the world when there were few if any logs?  Did no one get help?

---

### Post by MAFoElffen on 2011-10-17
> **jimbo99 said:**
> Oh please, listen to yourself.  If he can't get it installed how can he get to the logs, and what good are logs to people helping others.  Please read what the users are posting in this forum and then work from that.  If you need a specific log to help them you need to tell them where to go and what part of the log you need and how to get at that and where to post.  I certainly don't want to see log files here because they often do little good, confuse new users, and spam the threads.

Whatever happened in the world when there were few if any logs?  Did no one get help?
Sir, 
Your Post was insulting to Users and Myself...

Since you have private messaging turned off, I had to send this for all to view, which I feel bad about.  Viewing your other posts, You seem to be a negative kind of lot, and I think you try...
> **jimbo99 said:**
> If he can't get  it installed how can he get to the logs, and what good are logs to  people helping others.
Whatever happened in the world when there were few if any logs?
What good are the logs?  
 - When needed, I explain what log(s) I need posted and where it is...
 - They don't need to understand how to read the log, that is for me to read.
 - In Unix and Linux, there is not a public version past-tense that didn't have logs.
> **jimbo99 said:**
> Did no one get help?
I've been on this forum helping users almost around-the-clock for the past five days resolving user problems.  (I am physicall disabled and cannot sleep.)  I've had a "Graphics Resolution Sticky" since last June where I've actively helped others...

I explained am overall process of what might  be.  ATI and nVidia support explains less, but expects more, assuming  that a user has a skill set to do what needs to be done. I assess a users skills and try to guide a  user through what needs to be done.

I am here to help. If I am not at the problem personally, but I still need an idea of what  is going on.  The user has to paint a picture for us to see.  I  specialize in Graphics issues in Linux and Unix.  I've been working on  Oneiric since June with various hardware, so am a bit familiar with it's work-arounds for nVidia, ATI and Intel GPU's.

Am I tired, Yes. Do I feel offended by your post... No. If I am here to help others, that makes me feel good.

---

### Post by Stepway on 2011-10-19
For my part I very much appreciate the help, though I am still stuck..:(. ..with Ubuntu, it can usually be worked out.
To clarify, have Ubuntu 11.10 on a bootable pen drive & I am trying to install it on Dell 12 mini :- Processor intel Atom & **Intel 500 GMA video**.
After past installations it normally needs additional graphics drivers... This time it won't install or even boot up from the pen drive. (I don't have a cd rom)  
 As I mentioned earlier, during attempted installation:-     " It stops during the Ubuntu 11.10 purple screen, has a brief message that begins with "B43-phyo error firmware file B43/uncode15.fw " then I end up with the screen much like that posted on the 1st thread." 

?what to do ...what to do?

---

### Post by Namloc on 2011-10-19
deleted

---

### Post by Namloc on 2011-10-19
> Thats the wrong symbol... look to ight of keyboard, above the <enter> Key... It says "\" and if you hold the <shift> key it says '|"... which in Linux is a directional piping symbol.

I realise this makes me appear stupid, however I am not kidding you when I say that pushing this button comes up with a "~" rather than the required "|". I have tried it numerous times with different people present and can't work it out. Oddly, there is no such problem with this button in Windows or even when I'm in edit mode in the Grub. Is there any way I can copy/paste to the text console?

> While in the text console... does it say it has an xorg.conf file present?
Code:
ls /etc/X11/xorg.conf 

Upon entering this, I simply see the line /etc/X11/xorg.conf

Does this imply that the file is present?

Cheers.

---

### Post by Stepway on 2011-10-20
Hi Namloc,  I think I can help you find the  |  symbol.... I had to hunt as it wasn't what was on my keyboard....   on my dell the number or hash symbol next to the return key did it.

---

### Post by Namloc on 2011-10-23
Ok MAFoElffen,

I've finally managed to get this code into my computer thanks to the ALT key. So, it turns out my video card is nVidia. The output was ...
> 01:00 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 9300MGS][10de:06e9](rev a1)(prog-if 00 [VGA controller])

Nevertheless, the "nomodeset" insert still doesn't help me.

Can you think of anything I can do from here? I'm trying really hard to persevere with this but it's becoming quite frustrating.

Cheers.

---

### Post by Stepway on 2011-10-30
Maybe this may help:-     [http://ubuntuforums.org/showthread.php?t=1807612](http://ubuntuforums.org/showthread.php?t=1807612)   
Others found some fixes that might be helpful. Mine working fine now! :D... though never did succeed with the flash drive install, got stuck with the error messages others had here & on the link quoted. Hope you get it working too, it is awesome!

---

### Post by Hakunka-Matata on 2011-10-30
> **Namloc said:**
> Ok MAFoElffen,

I've finally managed to get this code into my computer thanks to the ALT key. So, it turns out my video card is nVidia. The output was ...


Nevertheless, the "nomodeset" insert still doesn't help me.

Can you think of anything I can do from here? I'm trying really hard to persevere with this but it's becoming quite frustrating.

Cheers.
Bring me up to speed here please:  So many posters I loose track of who said what, it's contents by inputting code:
[LIST]
[*]you are booting to liveCD/USB now?
[*]yes, you have an **xorg.conf** file, you can see **#**&/OR# optionally edit the file with the following commands: ```

[LIST]
[*]cat /etc/X11/xorg.conf  **# that lists the file, remember, everything is case sensitive: that's a reason to simply copy & paste commands, rather than trying to type them in correctly.**
[*]sudo **nano** /etc/X11/xorg.conf** #that will open it for editing.**
[/LIST]

```
[*]There are many other codes you can add to the boot line besides **nomodeset.**  I'll find it here shortly..............
[*]Oh yeah, you can try simply deleting the xorg.conf file too, save it as a backup which will effectively prevent the system from loading it, then change it back if that doesn't help.  How?
[LIST]
[*]```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
[/LIST]
 
[/LIST]
The **Sticky Thread to the graphics driver problems** is: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by dc.ricardo on 2011-11-27
See if you have lightdm and lightdm-gtk-theme.
Installing gdm package helps.
Run dpkg-reconfigure gdm.

---

### Post by tombott on 2013-03-07
I had a very similar problem upgrading from 12.04 to 12.10 with an ATI Raedon card.
In the end I dropped down to root terminal via Recover mode and removed fglrx

```
sudo apt-get remove fglrx
```

Rebooted and all was well in the world again.

---

### Post by oldos2er on 2013-03-07
Old thread closed.

---

