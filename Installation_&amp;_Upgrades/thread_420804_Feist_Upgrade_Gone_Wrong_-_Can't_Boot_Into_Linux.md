---
title: "Feist Upgrade Gone Wrong - Can't Boot Into Linux"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Lothlómendil on 2007-04-23
Blah for making a typo in the title.

I don't usually post for help here, but I'm in sore need of assistance. I am not an advanced user. I can run things just fine, make my way around proficiently, and do some stuff in the terminal, but when things start breaking I'm of no use. I rely more on the GUIs to get things done, like Synaptic. All I have at this point is my ability to ask for help and follow directions. I'm currently using WinXP since I dual boot and my Ubuntu is utterly inaccessible.

Sorry for the lengthy post to come, but I want to try and be complete and tell about all the things I've tried.

I decided to upgrade to Feisty today. I was still running Dapper because I hadn't used Ubuntu for a while, so I first upgraded to Edgy. The upgrade to Edgy went very smoothly, I used the update manager and it did everything for me. No complaints there, so I went ahead and started upgrading to Feisty using the update manager again.

It was at least 40 minutes into the installation and everything had been fine, but suddenly the screen went black. I thought it might be because some monitor / display settings were being changed so I let it sit there for bit to sort itself out while I left to grab a bite to eat from the kitchen. When I came back, my laptop had turned itself off. This was not a good sign.

Turning it back on, I chose the most recent version of Ubuntu from GRUB as usual (kernel 2.6.17-11-generic Default). It began to load, but didn't get very far at all. The loading screen's progress monitor bar remained empty, and clearly wasn't doing anything after a few minutes of waiting. It "hung." I restarted my laptop a few times to let it try again, but nothing. I also tried booting into recovery mode to no avail.

At this point tried booting into the most recent "previous" version in the list (kernel 2.6.15-28-amd64-generic Previous). It worked, but not smoothly. I was able to log in and use the internet and chat with my boyfriend about how to resume the upgrade in this state. Some applications weren't working (most notably, update manager), several things showed "wtf squares" as I call them, those squares your computer displays when it doesn't understand a character you've typed. Alt tab wasn't working to flip between windows, and the windows themselves were kind of odd looking. Everything was a mess, but functional enough.

I opened the terminal and entered **sudo apt-get update**. It accomplished a bit, but then I had to enter **sudo dpkg --configure -a** to get it to finish properly. When it was done I moved on to **sudo apt-get dist-upgrade**. Everything seemed to be going fine from that point, I was starting to think that whatever went wrong would be fixed.

The updates / upgrade seemed to complete without a hitch, and when it fully finished it asked me to restart. When it was shutting down, however, it hung again. A plain black screen with a cursor in the top left as if waiting for some terminal command, though I was unable to type anything. I let it sit and sit, but nothing. I had to turn it off manually by pressing and holding the power button again.

When it rebooted I chose the most recent version again. I don't remember if it even got to the loading screen this time. It output some text to tell me what it was doing at the moment as it tried to boot, but it always ended up hanging pretty early into the booting. I tried booting into recovery mode, and the "previous" version again too, but not even those worked now. I can't access anything.

I wrote down some of the last bits of text it output before hanging if you're interested in seeing. Just let me know and I'll go about the tedious task of typing up what I wrote down on paper.

I cannot / will not do a full re-installation because I'm not the most familiar with that, nor am I comfortable with attempting. I dual boot and only have my laptop, so I don't want to screw up Windows too. I'd die if GRUB broke, I wouldn't know what to do! Heh.

So, please, any advice is really needed and appreciated. I much prefer Ubuntu over Windows and am heart-broken that Feisty hates my laptop. Again, sorry if I said too much, not enough, or wasn't clear. I've used Ubuntu for 2 years now but never got deep into the technical stuff, I don't know what is or isn't relevant. I'll do my best to answer any questions and follow any well-advised directions.

Laptop information:
Gateway MX7515
1 year old, prime operational condition
Using 64-bit version of Ubuntu
Mobile AMD Athlon 64 processor 4000+
ATI Mobility Radeon x600 display adapter
1 GB RAM
Ask if you need more.

---

### Post by Lothlómendil on 2007-04-24
I know double posting is a bad, bad thing, but wow. Over night this was pushed back to page 10! So to make this post useful, I've included the text output that I see last before everything starts hanging. I may have typo'd something or written it down slightly off, but it's mostly correct and I think that someone who knows what they're doing can understand it.

I'm quite worried at this point, browsing through those 10 pages and reading the topics, there seem to be a ton of problems with Feisty. I regret trying to upgrade. -_-

When booting into the most recent version (kernel 2.6.17-11-generic Default) and previous version (kernel2.6.15-28-amd64-generic Previous), the code block ends where everything starts hanging:
```
Decompressing linux... Done.
Booting the kernel.
Loading, please wait...
bogl_init failed: opening /dev/fb0: No such file or directory
screen init failed
init:/etc/event.d/tty1:13: Unknown Stanza
init:/etc/event.d/tty2:13: Unknown Stanza
init:/etc/event.d/tty3:13: Unknown Stanza
init:/etc/event.d/tty4:13: Unknown Stanza
init:/etc/event.d/tty5:13: Unknown Stanza
init:/etc/event.d/tty6:13: Unknown Stanza
init:/etc/event.d/logd:11: Unknown Stanza
init:/etc/event.d/control-alt-delete:6: Unknown Stanza
init:/etc/event.d/sulogin:6: Unknown Stanza
udevd[2301]: udev_rules_init: Cound not read '/etc/udev/rules.d/60-libpisock.rules': No such file or directory
*Activating swap... [OK]
*Checking root file system...
fsck 1.40WIP (14-Nov-2006)
/: clean, 168324/2321984 files, 1552039/4638760 blocks   [OK]
*Checking file systems...
fsck 1.40WIP (14-Nov-2006)   [OK]
```

When booting into the most recent version's recovery mode, the code block ends where everything starts hanging:
```
*Mounting local filesystems...
*Configuring network interfaces...
*Setting up console and keymap...
```

[edit]
Reading some of these other topics, and thinking back, I feel like the upgrading may have overheated my laptop. Which is odd, it's never done that before. I read [here](http://ubuntuforums.org/showthread.php?t=420914) and it seems to be what caused my laptop to go black and power down during the initial installation. I can't be sure, this is just a possibility, and I don't know how to check the temperature. I do know that when this happened, I noticed my laptop was unusually hot (it hurt to touch it).

[edit2]
[This topic](http://ubuntuforums.org/showthread.php?t=415639) seems to have the same error messages.

---

### Post by kiikkuja on 2007-04-26
I have the exact same problem!! I upgraded my edgy and it didn't go nicely...please help us!! I really don't want to erase my edgy/feisty.

---

### Post by James Keating on 2007-04-30
rdejean may have the found the solution for this ([http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2540263)](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2540263)).

In my case, the boot process would hang after the last script in /etc/rc2.d, no matter which script that was. (I have put the nosplash option in /boot/grub/boot/menu.lst, so I can see the boot messages.)
Earlier in the boot process, I would get the messages
init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza

The problem was in /etc/event.d/tty1 (and tty2 etc.)
The last two lines were
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should have been
exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.

This seems to be a known bug. The release notes ([http://www.ubuntu.com/getubuntu/releasenotes/704](http://www.ubuntu.com/getubuntu/releasenotes/704)) say:
Users who have serial consoles, or have made custom changes to the /etc/inittab file or files in the /etc/event.d directory should be aware that the format of these files have changed slightly and your changes will not be automatically migrated. Bug #89314. The following changes should be made.
"respawn COMMAND" should be changed to "exec COMMAND" with "respawn" on a seperate line.
"on EVENT" should be changed to "start on EVENT"
the "runlevel-X" events should be changed to "runlevel X"

I only changed inittab to comment out all but the first two tty processes (# 3:23:respawn:/sbin/getty 38400 tty3) to not waste the memory. I didn't make the kind of change Ubuntu warned about, but it seems to have been enough.

---

