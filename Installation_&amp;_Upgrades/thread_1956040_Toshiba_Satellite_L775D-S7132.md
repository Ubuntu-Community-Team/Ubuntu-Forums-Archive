---
title: "Toshiba Satellite L775D-S7132"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by Das Goat on 2012-04-10
Mostly solved.....just a few unresolved issues.

Read until the end, it is only three pages, but it works now, and the laptop is great for the money!



Don't buy this laptop if you want to run Linux. I am no noob, as I have been running Ubuntu since 7.04. This is the second time over the years that I have found a laptop that simply refuses to take Linux. Here is a list of versions I tried:

Ubuntu: 10.04.4, 10.10, 11.04, 11.10, 12.04 beta 2

Mint 12

Fedora 16

Debian 6.0.4

Most lock up after the welcome screen.Higher Ubuntu versions and Fedora, the screen goes blank during boot and nothing happens.

I had some luck when I went into the bios and disabled the pointing device (sticker says it is a multi-touch pad). That let me load 10.04.4 and Debian. But Debian was crippled (or maybe it just comes that way :p )

10.04.4 would install, but no wireless drives would load. I tried getting the 10.10 alternate CD and doing an upgrade, but the upgrade hangs at "Removing update-grub hooks from /etc/kernel-img.conf in favor of /etc/kernel/hooks
Then, if you reboot, the installation is broken.

One other guy on the Toshiba site reported similar experiences. He seemed to think that the problem is in the video driver. That could be, or maybe it is the quad core, or the funky touch pad. Who can say.

One final bizarre thing is this: I have an external drive loaded with CentOS that I use for teaching class. It works fine. :confused: Too bad it is too difficult to use CentOS on my laptop for daily tasks. (server vs desktop applications)

Oh well, back to the store with this thing. Save yourself a lot of grief and don't buy this laptop.

---

### Post by 2F4U on 2012-04-10
My first guess for the black screen problem would be the graphics card and I would try to boot with the nomodeset grub kernel parameter.

---

### Post by Das Goat on 2012-04-23
I just went and tried that new Sangung laptop at Best Buy, NP305E7A-A02US. I saw it yesterday, but noticed that it looked like it had the same stickers as the Toshiba. This time, I took my trusty Ubuntu installed on a flash drive to see what would happen. It was a very similar experiance, everything seemd OK, then the video freaked out. I am trying to figure out eaxctly what the video card from AMD Radeon is. Maybe that way someone will have an answer. It is a shame, because both of these laptops are Quad-Core 17.3" under $500. :confused:

---

### Post by Das Goat on 2012-04-23
Just as I though, they both use AMD Radeon HD 6520G Graphics cards. Anyone have any tricks for getting this thing to work?:mad:

---

### Post by Toz on 2012-04-23
Did you try the suggestion from post #2?

EDIT: Here is a related post with detailed instructions: [http://ubuntuforums.org/showthread.php?p=11842752]("http://ubuntuforums.org/showthread.php?p=11842752")

---

### Post by techsupport on 2012-04-23
I recommend buying something with Intel CPU w/Intel Graphics Adaptor like this bad boy here:

[http://www.frys-electronics-ads.com/ads/2012/04/20/57528/HP-15-6-Laptop-2000-410US-with-Intel-Pentium-Processor-B960](http://www.frys-electronics-ads.com/ads/2012/04/20/57528/HP-15-6-Laptop-2000-410US-with-Intel-Pentium-Processor-B960)

Try to keep with specs like these:

[http://www.sears.com/shc/s/p_10153_12605_SPM6086594301P](http://www.sears.com/shc/s/p_10153_12605_SPM6086594301P)

Avoid ATI Graphics at all costs if you want it to work without any problems down the road. Nvidia Graphics are better than ATI, of course, but Intel Graphics adapters have never caused me one minute of grief with Ubuntu Linux.
:guitar:

> **Das Goat said:**
> Don't buy this laptop if you want to run Linux. I am no noob, as I have been running Ubuntu since 7.04. This is the second time over the years that I have found a laptop that simply refuses to take Linux. Here is a list of versions I tried:

Ubuntu: 10.04.4, 10.10, 11.04, 11.10, 12.04 beta 2

Mint 12

Fedora 16

Debian 6.0.4

Most lock up after the welcome screen.Higher Ubuntu versions and Fedora, the screen goes blank during boot and nothing happens.

I had some luck when I went into the bios and disabled the pointing device (sticker says it is a multi-touch pad). That let me load 10.04.4 and Debian. But Debian was crippled (or maybe it just comes that way :p )

10.04.4 would install, but no wireless drives would load. I tried getting the 10.10 alternate CD and doing an upgrade, but the upgrade hangs at "Removing update-grub hooks from /etc/kernel-img.conf in favor of /etc/kernel/hooks
Then, if you reboot, the installation is broken.

One other guy on the Toshiba site reported similar experiences. He seemed to think that the problem is in the video driver. That could be, or maybe it is the quad core, or the funky touch pad. Who can say.

One final bizarre thing is this: I have an external drive loaded with CentOS that I use for teaching class. It works fine. :confused: Too bad it is too difficult to use CentOS on my laptop for daily tasks. (server vs desktop applications)

Oh well, back to the store with this thing. Save yourself a lot of grief and don't buy this laptop.

---

### Post by Das Goat on 2012-04-24
> **Toz said:**
> Did you try the suggestion from post #2?

EDIT: Here is a related post with detailed instructions: [http://ubuntuforums.org/showthread.php?p=11842752]("http://ubuntuforums.org/showthread.php?p=11842752")

You know, I found a related post with similar instructions, so I came home last night and tried it again.

This time it installed like normal. I didn't have to do anying at all. Video is not a problem.

But now I have a new issue. The touch pad doesn't work. I plugged in a mouse and it works, so that is clearly a driver issue. But the keyboard doesn't work either. I can't find a usb keyboard in my garage, so I am taking it to work. The onscreen keyboard works, so I can log in, but I can't seem to find it when I am on the desktop. :confused:

---

### Post by Toz on 2012-04-24
> **Das Goat said:**
> You know, I found a related post with similar instructions, so I came home last night and tried it again.

This time it installed like normal. I didn't have to do anying at all. Video is not a problem.
Glad to hear.

> But now I have a new issue. The touch pad doesn't work. I plugged in a mouse and it works, so that is clearly a driver issue. But the keyboard doesn't work either. I can't find a usb keyboard in my garage, so I am taking it to work. The onscreen keyboard works, so I can log in, but I can't seem to find it when I am on the desktop. :confused:
According to [https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340]("https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340") (similar type system), the solution appears to be to add:
```
i8042.nomux=1 i8042.reset
```
...to your grub kernel command line (note: its not menu.lst as noted in that article - thats for a different system). 

You should be able to add it to the kernel command line while booting as per: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot"), and then make it permanent via editing the /etc/default/grub file:
```
gksudo gedit /etc/default/grub
```
...adding the parameters, then running:
```
sudo update-grub
```

---

### Post by Das Goat on 2012-04-24
> **Toz said:**
> Glad to hear.


According to [https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340]("https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340") (similar type system), the solution appears to be to add:
```
i8042.nomux=1 i8042.reset
```
...to your grub kernel command line (note: its not menu.lst as noted in that article - thats for a different system). 

You should be able to add it to the kernel command line while booting as per: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot"), and then make it permanent via editing the /etc/default/grub file:
```
gksudo /etc/default/grub
```
...adding the parameters, then running:
```
sudo update-grub
```

Wow, this just gets stranger and stranger. I figured out how to get the onscreen keyboard to stick, then I saw your replay, so I thought I would try it. I told Ubuntu to shut down, so I could catch it when it booted up, but it reset instead. No biggie, right? Force of habit made me try the keyboard and shazam! it was working now, but I hadden't done anything yet. Weired. told it to shut down and it rest instead again. I caught grub and did what you suggested, it booted up and the keyboard still works.

```
gksudo /etc/default/grub
```

this didn't do anything, literally I just got the promt back with out anything happening, so I used this instead .....

```
sudo gedit /etc/default/grub
```

after putting in the code you suggested, I got an error about a missing callback when exiting gedit

```
sudo update-grub 
```

returned an error i8042.nomux=1: not found

Sorry, now that I can type on it, I should have sent this from that computer. I am going to update the video driver they way you suggested, remove the line in the grub file, and reboot.

---

### Post by Toz on 2012-04-24
My apologies - forgot the gedit command.

After double-checking the parameters at [http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"), the parameters should be:
```
i8042.nomux i8042.reset
```

Thats two knocks against me. Sorry again.

---

### Post by Das Goat on 2012-04-24
> **Toz said:**
> My apologies - forgot the gedit command.

After double-checking the parameters at [http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"), the parameters should be:
```
i8042.nomux i8042.reset
```

Thats two knocks against me. Sorry again.

Well, we are getting closer anyway.

I turned off the onscreen keyboard. booted into Win7 to verify that the touch pad was working, then booted back to Ubuntu. Lost the keyboard totally and couldn't turn it on in accesabilty because the screen was freaking out. Couldn't shut down either becaus e the menues were wacked as well. Had to hold the button down.

I saw your update and tried to put in the command in grub again. I got an error saying that it didn't know what i8024.nomux was.

As I was trying to figure out what to do, it timed out and finished booting. Suddenly the keyboard was back. So I tried to put the command in grub file again. When I ran update-grub I got this error

```
 /usr/sbin/grub-mkconfig: 37: /etc/default/grub: i8042.nomux: not found 
```

Do you think it might just be the i8042.reset? No, that isn't it. I took out the first part and left the reset, but it doesn't know what that is either.

I am going to try rebooting. See you in a minute.

---

### Post by Das Goat on 2012-04-24
Well, now I am just at a loss. I commented out the i8042 commands and updated grub. Now the keyboard is acting fine. :confused:

I hate mystery fixes.

Anyway, the only problems I have left are:

No touch pad

Will not shut down, always resets.

I have to leave for work, but I will take it with me. I don't like work and getting this working seems to be a better use of my time.

:popcorn:

See ya in two hours.

---

### Post by Toz on 2012-04-24
> **Das Goat said:**
> Well, we are getting closer anyway.

I turned off the onscreen keyboard. booted into Win7 to verify that the touch pad was working, then booted back to Ubuntu. Lost the keyboard totally and couldn't turn it on in accesabilty because the screen was freaking out. Couldn't shut down either becaus e the menues were wacked as well. Had to hold the button down.

I saw your update and tried to put in the command in grub again. I got an error saying that it didn't know what i8024.nomux was.

As I was trying to figure out what to do, it timed out and finished booting. Suddenly the keyboard was back. So I tried to put the command in grub file again. When I ran update-grub I got this error

```
 /usr/sbin/grub-mkconfig: 37: /etc/default/grub: i8042.nomux: not found 
```

Do you think it might just be the i8042.reset? No, that isn't it. I took out the first part and left the reset, but it doesn't know what that is either.

I am going to try rebooting. See you in a minute.

Can you post back the contents of your /etc/default/grub file?

---

### Post by Das Goat on 2012-04-24
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#Keyboard fix
#i8042.nomux i8042.reset

```

I hope this helps. BTW, I have it hooked up here at work and the keyboard is working fine. Still no touchpad though.

I appreciate your efforts, I really do. This is a great laptop and I don't want to get rid of it.

---

### Post by jadtech on 2012-04-24
just a thought here, I am not sure what version you installed how ever if it was 12.04 as I understand it  12.04 has a feature that disables the touch pad when you type. 

not sure this is possible  but maybe worth a check do you maybe have a sticky or stuck key that could be causing the touch pad to be disabled , maybe even a good test would be to plug in a wireless keyboard as a test  dont know .. 

Just a thought

---

### Post by Toz on 2012-04-24
> **Das Goat said:**
> ```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#Keyboard fix
#i8042.nomux i8042.reset

```

I hope this helps. BTW, I have it hooked up here at work and the keyboard is working fine. Still no touchpad though.

I appreciate your efforts, I really do. This is a great laptop and I don't want to get rid of it.

ahhh, you've put the commands in the wrong place. They need to be appended to the existing GRUB_CMDLINE_LINUX_DEFAULT line so that it reads like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.reset"
```

---

### Post by Das Goat on 2012-04-24
> **jadtech said:**
> just a thought here, I am not sure what version you installed how ever if it was 12.04 as I understand it  12.04 has a feature that disables the touch pad when you type. 

not sure this is possible  but maybe worth a check do you maybe have a sticky or stuck key that could be causing the touch pad to be disabled , maybe even a good test would be to plug in a wireless keyboard as a test  dont know .. 

Just a thought

Thanks for the thought. I did look into that and it is not the issue. It must be the driver, I think. The sticker on the hand rest says it is a multi-touch control touch pad.

---

### Post by Das Goat on 2012-04-24
Toz,

Thanks for all of the help today. I fixed the grub file and now I get no errors. Keyboard is working nicely.

Any thoughts on the touch pad? Is there a way to get the windows driver and use NSwrapper like in the old days for wireless support?

Also, any idea why shutdown reboots instead of turning off?

Lastly, when the finally release happens in two days, should I re-install using the approved CD, or just run the updates?

Thanks again for all of your help!:popcorn:

---

### Post by Toz on 2012-04-24
> **Das Goat said:**
> Toz,

Thanks for all of the help today. I fixed the grub file and now I get no errors. Keyboard is working nicely.
Great news.

> Any thoughts on the touch pad? Is there a way to get the windows driver and use NSwrapper like in the old days for wireless support?
I've come across a number of references indicating **i8042.nomux=1**. Can you give that a try in your grub file (instead of just i8042.nomux) - just to see if it works? Here is a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889660]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889660").

> Also, any idea why shutdown reboots instead of turning off?
That previous bug report is specific to this issue. What does the following return for you, on or auto?
```
cat /sys/bus/pci/devices/*/power/control
```
Also, double-check your bios to make sure that you don't have something set to reboot.

> Lastly, when the finally release happens in two days, should I re-install using the approved CD, or just run the updates?
If you're running the 12.04 beta, just keep updating and you will be at release status. In fact, its almost there now - just a few more final patches I'm guessing.

> Thanks again for all of your help!:popcorn:
No worries.

---

### Post by Toz on 2012-04-24
A couple of other notes:

1. If you find that your audio crackles, edit your /etc/pulse/default.pa file and change the line:
> load-module module-udev-detect 
...to read
```
load-module module-udev-detect tsched=0
```

2. If you have a problem suspending, follow the solution here: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug").

---

### Post by Das Goat on 2012-04-24
> **Toz said:**
> 

I've come across a number of references indicating **i8042.nomux=1**. Can you give that a try in your grub file

Did that, updated grub, and now it shuts down properly, still no touch pad.


> **Toz said:**
> 
That previous bug report is specific to this issue. What does the following return for you, on or auto?


FYI, it returned everything on, but as I said, it now shuts down like it is supposed to.



Work is done, see you in the morning. Thanks again! ):P

---

### Post by Das Goat on 2012-04-25
OMG! The last fix is so stupid I am embarased! FN+F9 key turned the touch pad on. It is DISABLED BY DEFAULT during installation. That is crazy! Maybe the developers could fix that, but I doubt by tomorrow. Maybe a patch next week?

Holly cow, I turned down three more of these laptops at a great price becaus the touch pad was turned off in the installation CD. Oh well, live and learn.

Thanks everyone who tried to help, and especially to Toz for the great tips.

:popcorn:

):P

---

### Post by Das Goat on 2012-05-13
@ TOZ, I hope you are still checking this tread.

For work reasons, I triple booted my system to show the students what Win8 (loveing dubbed VistaME) looked like. I figured I would rebuild the whole thing anyway after 12.04 offical came out.

When I scrubbed the laptop and started over, 12.04 loads just fine, except that I don't have a keyboard or touch pad. On screen keyboard doesn't work either. No fear, I plugged in a USB keyboard and mouse, and all the updates, and the keyboard and touchpad work without a problem. On screen keyboard still doesn't work. I get a wierd splash like it wants to load the on screen keyboard after I put in my password. I will try the fixed we used before to see if I can get it back, but it is a low priority right now.

My main last two complaints is that it never goes to sleep, and it will not shut off, only reboots. I was watching another thread with similar issues, but it covered an encrypted home folder and ancrypted swap file. I am not doing any of that. Just a straight forward installation.

Anyone have any hints for me?

---

### Post by Toz on 2012-05-13
> **Das Goat said:**
> My main last two complaints is that it never goes to sleep, and it will not shut off, only reboots. I was watching another thread with similar issues, but it covered an encrypted home folder and ancrypted swap file. I am not doing any of that. Just a straight forward installation.

Anyone have any hints for me?
For the suspend issue, try the fix from here: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")

As for the shutdown issue, wasn't it solved earlier in this thread by using the **i8042.nomux=1** kernel parameter?

---

### Post by Das Goat on 2012-05-14
@ Toz

You are correct sir! I appologize most profusely! That was the solution. I got caught up in the keyboard solution and didn't see that it was the power solution.

When I have imbided less grain beverages, I will try that most complicated solution to the sleeping promblem.

Again, my appologies!

:popcorn:

---

### Post by Das Goat on 2012-11-16
I am going to close this thread. On 11/15/2012, after a frustrating several trys to get 12.10 to work, I gave up and went back to 12.04

Staright up install, did the nomux=1 fix from earlier in the thread. Ran all of the upades, and loaded the propriatary Ati driver from the binaries, and holly cow! it works fine!

I left it in sleep / suspend mode all night. When I opened the lid this morning, it resumed just fine. Then I unplugged it so it was on battiery, and it also sleep / suspend / resumed just fine.

What ever was wrong, Ubuntu seemed to fix it.  :popcorn:

---

