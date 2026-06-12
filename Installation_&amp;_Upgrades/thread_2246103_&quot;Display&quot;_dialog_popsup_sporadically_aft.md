---
title: "&quot;Display&quot; dialog popsup sporadically after 12.04 --&gt; 14.04"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by neandr on 2014-09-28
After working successfully with Xubuntu 12.04 I decided to upgrade to 14.04.
Unfurtunately with 14.04 (and Mint17) frequently I get sporadic opening the "Display" dialog. All possible settings on that dialog seem to be OK. 

A test with a Mint13 (which is based on 12.04 I guess) don't shows any problem!

I already asked on the German ubuntuusers forum without getting a final solution. Only one hint:
> It could be a driver problem. 
That statement could lead the way to a solution, like holding 14.04, but moving back to the 12.04 drivers. 
Would that be possible .. if yes .. But how? 

Please let me know if you need additional details beside this:
**Dell Vostro 3550** 
```
$ ps -aux | grep display-settings
guenter   3939  0.5  0.1 378388 15808 ?        Sl   16:07   0:00 xfce4-display-settings --minimal
guenter   3942  0.4  0.1 378508 15788 ?        Sl   16:07   0:00 xfce4-display-settings --minimal
guenter   3946  0.0  0.0  13212   956 pts/1    S+   16:08   0:00 grep --colour=auto display-settings

$ lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
	Subsystem: Dell Device [1028:04cd]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] [1002:6741] (rev ff)
	Kernel driver in use: radeon
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)

 $ uname -a
Linux guenter-V3550-Mint 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Toz on 2014-09-28
I've seen this before. If you go to Settings Manager >> Keyboard >> Application Shortcuts, you'll see a shortcut to "xfce4-display-settings --minimal" mapped to "XF86Display". If you delete that mapping, the display dialog should stop popping up.

If this works, then your system is emitting the XF86Display signal for some reason. However, I don't know why this is happening.

---

### Post by neandr on 2014-09-29
Thanks for your answer ..
> 
Settings Manager >> Keyboard >> Application Shortcuts, you'll see a shortcut to "xfce4-display-settings --minimal" mapped to "XF86Display". 
.. yes I'll get that dialog and have the entry you mention, but ..
> 
If you delete
.. with using the [Remove] button nothing happens, same with [del] key. Also closing / reopen, the entry remains there.

I tried to find an xml file holding that entry (following another of your threads, like [http://ubuntuforums.org/showthread.php?t=2244015&p=13120790&highlight=#post13120790](http://ubuntuforums.org/showthread.php?t=2244015&p=13120790&highlight=#post13120790)), ```
$ dir ~/.config/xfce4/xfconf/xfce-perchannel-xml
keyboards.xml  xfce4-appfinder.xml  xfce4-session.xml
ristretto.xml  xfce4-desktop.xml    xfwm4.xml
thunar.xml     xfce4-panel.xml	    xsettings.xml
```... but there is nothing like that with those files!?

Any further help?

---

### Post by Toz on 2014-09-29
Can you post back the results of:
```
ls -l ~/.config/xfce4/xfconf | grep xfce-perchannel-xml
```
...and
```
ls -l ~/.config/xfce4/xfconf/xfce-perchannel-xml
```

And if all the permissions are correct on both the directory and the files, then logout and move in the default shortcuts xml file:
1. Logout
2. Ctrl+Alt+F1 and login
3. Run:
```
cp /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml
```
4. Go back to the Gui (Ctrl+Alt+F7)
5. Log in and try to delete the entry again.

---

### Post by neandr on 2014-09-29
> **Toz said:**
> Can you post back the results of:
5. Log in and try to delete the entry again.

All permissions are OK, so I followed the 5 points and the Display dialog seems NOT to popup anymore.

1000 Thanks !

Will post back later this afternoon/evening about a "final" SOLVED ... fingercrossing ;)

Guenter


PS This is with XUbuntu 14.04.01 .. will check it for Mint17 also, hope it's the same

---

### Post by neandr on 2014-09-29
> will check it for Mint17 also, hope it's the same 

No, with mint17 it's not solving that way:mad:

Also I have changed the 'source' dir for that action with:
```
 ~ $ ls -l /etc/xdg/xdg-default/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
-rw-r--r-- 1 root root 10002 Dez 18  2013 /etc/xdg/xdg-default/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```

On the dialog the [FONT=System]xfce4-display-settings --minimal XF86Display[/FONT] can't be deleted!

Any other idea for mint17?

---

### Post by Toz on 2014-09-29
Check the permissions of the ~/.config/xfce4/xfconf/xfce-perchannel-xml folder and the files inside them and make sure that they are owned by you.
Make sure that the ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml file exists. If not, copy it over.

I don't have a mint install handy, is the mint default config directory /etc/xdg/xdg-default? Or is it maybe something else?

---

### Post by neandr on 2014-09-29
This is 'all' I can tell you:
```

$ ls -ll /home/gneandr/.config/xfce4/xfconf/xfce-perchannel-xml/
total 52
-rw-r--r-- 1 gneandr gneandr   204 Sep 27 00:07 keyboards.xml
-rw-r--r-- 1 gneandr gneandr   379 Sep 28 22:57 ristretto.xml
-rw-r--r-- 1 gneandr gneandr  1309 Sep 29 20:01 thunar.xml
-rw-r--r-- 1 gneandr gneandr   329 Sep 28 01:55 xfce4-appfinder.xml
-rw-r--r-- 1 gneandr gneandr  3400 Sep 29 17:23 xfce4-desktop.xml
-rw-rw-rw- 1 gneandr gneandr 11937 Sep 29 20:04 xfce4-keyboard-shortcuts.xml
-rw-r--r-- 1 gneandr gneandr  5605 Sep 29 18:40 xfce4-panel.xml
-rw-r--r-- 1 gneandr gneandr  1232 Sep 27 13:02 xfce4-session.xml
-rw-r--r-- 1 gneandr gneandr  4093 Sep 26 23:51 xfwm4.xml
-rw-rw-rw- 1 gneandr gneandr  1755 Sep 27 01:29 xsettings.xml

 ~ $ dir /etc/xdg/xdg-default
applications  autostart  Terminal  Thunar  xfce4

 $ dir /etc/xdg/xdg-default/xfce4
desktop  helpers.rc  panel  Xcursor.xrdb  xfconf  Xft.xrdb  xfwm4

 $ dir /etc/xdg/xdg-default/xfce4/xfconf
xfce-perchannel-xml

 $ dir /etc/xdg/xdg-default/xfce4/xfconf/xfce-perchannel-xml
thunar-volman.xml	      xfce4-notifyd.xml        xfce4-session.xml
xfce4-desktop.xml	      xfce4-panel.xml	       xfwm4.xml
xfce4-keyboard-shortcuts.xml  xfce4-power-manager.xml  xsettings.xml

 $ ls -ll  /etc/xdg/xdg-default/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
-rw-r--r-- 1 root root 10002 Dez 18  2013 /etc/xdg/xdg-default/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml

```

Does that help in any way ... need you more details from the system?

PS for these files .. 
```
-rw-rw-rw- 1 gneandr gneandr 11937 Sep 29 20:04 xfce4-keyboard-shortcuts.xml
-rw-rw-rw- 1 gneandr gneandr  1755 Sep 27 01:29 xsettings.xml
``` .. I manually changed the 'rw' attributes. But that doesn't help for the [Remove]

---

### Post by Toz on 2014-09-29
Try doing it manually. 

Open the file "/home/gneandr/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml" in an editor of your choice. Locate the line that reads:
```
      <property name="XF86Display" type="string" value="xfce4-display-settings --minimal"/>
```
...and change it to read:
```
      <property name="XF86Display" type="string" value=""/>
```
...and save the file.

Then you need to restart xfconfd. This will depend on where the executable is. 
First, run the following command to find the path of the existing xfconfd process:
```
ps -ef | grep xfconfd | grep -v grep
```
...mine returns:
> $ ps -ef | grep xfconfd
toz       6273  6271  0 19:29 pts/1    00:00:00 /usr/lib/xfce4/xfconf/xfconfd
...which means my xfconfd executable is located at "/usr/lib/xfce4/xfconf/xfconfd".

So to restart xfconfd, run:
```
killall xfconfd && /usr/lib/xfce4/xfconf/xfconfd &
```
...using of course your correct path to the xfconfd executable.

This will reload the file that you just edited into memory. Double-check to see if the setting is gone.

---

### Post by neandr on 2014-09-30
Searching to whole Mint17 system for **xfce4-keyboard-settings.xml**, there is ***NO*** result for it!
The only relevant files are:
```

$ ls -ll /usr/share/applications/xfce-keyboard-settings.desktop
-rw-r--r-- 1 root root 5453 Mär 31  2014 /usr/share/applications/xfce-keyboard-settings.desktop

 $ ls -ll /usr/share/man/man1/xfce4-keyboard-settings.1.gz
-rw-r--r-- 1 root root 596 Mär 31  2014 /usr/share/man/man1/xfce4-keyboard-settings.1.gz

 $ ls -ll /usr/bin/xfce4-keyboard-settings
-rwxr-xr-x 1 root root 92320 Mär 31  2014 /usr/bin/xfce4-keyboard-settings

```

So no chance to solve it this way. 
I'm going to ask on the Linux Mint Forum
[http://forums.linuxmint.com/viewtopic.php?f=49&t=179340](http://forums.linuxmint.com/viewtopic.php?f=49&t=179340)

Thanks Toz
Greetings
Guenter

---

### Post by Toz on 2014-09-30
Sorry, I got the file name wrong. It should be **xfce4-keyboard-shortcuts.xml**. My apologies.

I'll correct my last post.

---

### Post by neandr on 2014-09-30
Upps, yes I think I have used that **xfce4-keyboard-shortcuts.xml** already. 
But to be sure I repeated with:
```
 /etc/xdg/xfce4/xfconf/xfce-perchannel-xml $ sudo nano xfce4-keyboard-shortcuts.xml

 $ sudo killall xfconfd && /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd &
[3] 8334
```

The "Application Shortcut" menu is OK, no entry "xfce4-display-settings --minimal" mapped to "XF86Display" anymore.

But sorry, the "Display" dialog keeps showing up ...

---

### Post by Toz on 2014-09-30
You need to edit the **~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml** instead. That's the active shortcuts file for your profile.

---

### Post by neandr on 2014-09-30
Hi Toz,

SURPRISE, SURPRISE ... the last boot is 2h ago and I didn't get the "Display" dialog!

So it seems to be **SOLVED**![COLOR=#ff0000]**?**[/COLOR]

With questions mark because I did two actions:
-- your purposed editing (re-checked what I did, but couldn't see any incomplete/false action)
-- on the Display dialog I changed from 1366x768 --> 1360x768 !!

For now I'll not re-check if the second action is/was the solution. But will come back to it ...

For the moment, once more thanks for your help :p

Guenter

---

### Post by Toz on 2014-09-30
> **neandr said:**
> -- on the Display dialog I changed from 1366x768 --> 1360x768 !!

^^^This might actually be the root of the problem. Just to confirm, you have both the 1366x768 and 1360x768 options available as resolutions?

To check whether this is the root of the problem, after you've changed the resolution, try adding back the XF86Display shortcut. If the display window does not pop-up, then you can confirm that it was an incorrect resolution setting that was causing the problem.

---

### Post by neandr on 2014-10-04
OK, it's time to close this thread with  ... SOLVED!

Thanks to Toz I was able to fix the problem with XUbuntu 14.04 and also Mint17!

With Mint17 it wasn't clear if the display solution change to 1360x768 was the solver. But I changed back to 1366x768 some days ago and the display dialog was not coming back. With that finding, the change proposed by Toz was the right point.

Thanks again for a GREAT help ;)  Keep going!

Guenter

---

