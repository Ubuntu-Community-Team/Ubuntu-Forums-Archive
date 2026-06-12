---
title: "Grub2 Not Showing Menu (Hidden_Timeout is commented out)"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MTGap on 2009-10-02
Well this happened after I changed the Timeout in the config from 10 to 0 (Whoever decided on this timeout, should know better this is way to long) 

Here is what my /etc/default/grub looks like:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```


And yes I have run update-grub and there were no issues. Now I just see a blank screen for 20 seconds before it boots up. And even pressing ESC or the Shift button (I believe shift should work as well but not sure) does not give me a menu. I don't care too much about not seeing the menu but there are times I need a different kernel, the biggest issue is the 20 seconds of uselessness. Any help?

---

### Post by kansasnoob on 2009-10-02
I'm still learning myself but look here:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305+grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305+grub)

Specifically:

> /etc/default/grub

And more specifically:

> # GRUB_HIDDEN_TIMEOUT=0

    * The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The default setting initially depends on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
          o No other OS Detected: The menu will be hidden.
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    * 0 The menu will not be displayed. There will be no delay.
          o When this entry is set to 0:
                + The user may force displaying the menu as the computer boots by holding down the SHIFT key.
                + During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key.
    * If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected.

# GRUB_HIDDEN_MENU_QUIET=true

    * true - No countdown is displayed. The screen will be blank.
    * false - A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT va

---

### Post by MTGap on 2009-10-02
Thanks that appears to provide a good source of info. I'm just a little confused though since I did see the menu (I installed from a livecd of alpha6 just recently) in the beginning since it also detected Windows XP. I was trying to increase my boot time and the only things that I changed before this happened was the Timeout (The Hidden Timeout was still left uncommented as above) and the vm swappiness or whatever which supposedly makes it use more ram than swap and this I didn't make too much of a change in apparently so that shouldn't be an issue. I must say though once it starts loading it loads pretty fast. I just wish I could get to the menu and profile it as well to increase speed.



Once I get back to Kubuntu I'll post my grub.cfg and make sure it's actually updating it correctly.

---

### Post by kansasnoob on 2009-10-02
Well it's no longer a matter of "commenting out" that option.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by MTGap on 2009-10-02
I'm confused with what you mean: 

> GRUB_HIDDEN_TIMEOUT=0
The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
The default setting initially depends on the presence of other operating systems.
Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
No other OS Detected: The menu will be hidden.
For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
0 The menu will not be displayed. There will be no delay.
When this entry is set to 0:
The user may force displaying the menu as the computer boots by holding down the SHIFT key.
During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key.
If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected.

---

### Post by autocrosser on 2009-10-02
OK--my /etc/default/grub (older install) looks like:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=3
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
```

Notice I do not have "GRUB_HIDDEN_TIMEOUT_QUIET=true" at all in mine--Look at the example, modify yours & then run grub update

---

### Post by MTGap on 2009-10-04
I'm still having trouble, here is what my /etc/default/grub looks like now:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"



And my /boot/grub/grub.cfg after update-grub2:

> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro single 
	initrd	/boot/initrd.img-2.6.31-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c298efd998efca4d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


One thing I notice is if hit Esc during the time where the screen is all black my computer beeps. Off topic, right now my computer loads verbose (the one with all the text) how do I get the loading splash screen back?

---

### Post by drs305 on 2009-10-04
Change the GRUB_TIMEOUT value to something other than 0. The 0 indicates not to display the menu. If you put a positive value, the menu should display for that many seconds.

Then run "sudo update-grub".

Also note in Grub 2, you no longer use the ESC key to display the menu (although it may work). Grub 2 looks for a depressed SHIFT key to display the menu. It goes even further than that, actually. If it can't determine whether the SHIFT key is depressed or not, it assumes it IS and displays the menu.

Grub 2's default is to not show the menu. A time where the default changes is if Grub 2 initially detects another OS on the machine - then the default is to display the menu to allow the user to choose.

The GRUB_HIDDEN_TIMEOUT is the length of time the system will wait with a blank screen before continuing.

Seeing text messages after the Grub screen and before the xsplash Ubuntu screen is a bug they are still working on. Unless you specify it, you shouldn't see any text messages (unless you are looking down at your PDA ;-)  ).

---

### Post by MTGap on 2009-10-04
Okay I'll see if that works when I reboot tomorrow, yeah with the loading I mean I don't even see any usplash, it's all text until kdm pops up.

---

### Post by MTGap on 2009-10-05
I just tried it and now I have made some progress, I now see the menu. However I can't select anything or hit enter it just stays there, and doesn't start up for a while just like before but when it was all black.

---

### Post by drs305 on 2009-10-05
> **MTGap said:**
> I just tried it and now I have made some progress, I now see the menu. However I can't select anything or hit enter it just stays there, and doesn't start up for a while just like before but when it was all black.

Can you change selections with the up/down arrow? If you press E on one of the selections do the settings appear?

---

### Post by MTGap on 2009-10-05
Nope it just hangs like it did when I didn't even see the menu, it will startup after maybe 20 seconds. My hard drives access light is on the whole entire time. 

Yeah it basically starts up and then appears to be frozen.

---

### Post by autocrosser on 2009-10-05
Is your /boot & the grub install on the same drive???  If not, you have been bitten with the bug I reported about a month ago. Look at:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)  & see if it is what you are having for a problem.

---

### Post by cheesypoof on 2009-10-05
If you have another OS, is there a way to force grub2 to not show the menu, but give you say 3 seconds to choose whether to hit escape to show it?

---

### Post by emarkay on 2009-10-05
Cheesypoof, this sounds like a whole new topic, but if you mean that if you have Window$ and Ubuntu Karmic, yes you can change the timeout in the /etc/default/grub file.  I don't have the list here, but repost as a new topic and someone will .

---

### Post by drs305 on 2009-10-06
> **cheesypoof said:**
> If you have another OS, is there a way to force grub2 to not show the menu, but give you say 3 seconds to choose whether to hit escape to show it?

The entries in /etc/default/grub you want to change are:
```

GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true

```

Change the value of timeout to a positive number. If you want to see a counter count down the seconds remaining, change true to false.

The link to Grub 2 in my signature line explains all this.

---

### Post by cheesypoof on 2009-10-06
drs305, changing those settings made absolutely no difference to the content of the grub.cfg file. Testing confirmed no behavioral change either. There are only 2 possibilities. 1, This component is disabled/broken in the current version. 2, My settings have not met the defined standards to be imported into grub.cfg. I have read your grub 2 basics thread in the past by the way. Sorry for the thread hijacking... It seems like the op's problem however is a bug that is not fixable through the forums, but through launchpad.

Oh and I did not forget to perform sudo update-grub

---

### Post by VMC on 2009-10-06
> **cheesypoof said:**
> drs305, changing those settings made absolutely no difference to the content of the grub.cfg file. Testing confirmed no behavioral change either. There are only 2 possibilities. 1, This component is disabled/broken in the current version. 2, My settings have not met the defined standards to be imported into grub.cfg. I have read your grub 2 basics thread in the past by the way. Sorry for the thread hijacking... It seems like the op's problem however is a bug that is not fixable through the forums, but through launchpad.

Oh and I did not forget to perform sudo update-grub

Did you look inside "/boot/grub/grub.cfg" to see if the changes were effective? Use sudo to do that.

---

### Post by ranch hand on 2009-10-06
Did you run "sudo update-grub"?  If not nothing has been changed.  Anything you do in grub2 MUST be followed by running that command to get it written to the /boot/grub/grub.cfg file.

---

### Post by cheesypoof on 2009-10-06
I did look inside grub.cfg and I did run "sudo update-grub" as my previous post stated. Can someone actually post the hidden timeout settings section of their grub.cfg, because I have yet to see it in anybody's posted grub.cfg in these forums. Oh and by the way I just found this script in the past couple minutes at [http://ubuntuforums.org/showthread.php?p=7731488&highlight=press+esc+menu#post7731488](http://ubuntuforums.org/showthread.php?p=7731488&highlight=press+esc+menu#post7731488) which seems to replicate the exact behavior I wanted all along...

---

### Post by drs305 on 2009-10-06
> **cheesypoof said:**
> drs305, changing those settings made absolutely no difference to the content of the grub.cfg file. Testing confirmed no behavioral change either. There are only 2 possibilities. 1, This component is disabled/broken in the current version. 

I have retested the hidden menu options and confirm the settings are not currently working. The last time I tested this feature was in Grub 1.97 Beta 1 or 2. Grub 2 (grub-pc) is now at Beta 3 and this appears to be a regression. 

There have been significant changes to Grub 2 in the past several months. I have submitted a bug report on this at Launchpad.

If you experience problems with the hidden menu feature please subscribe to the bug and provide any additional information which may help the developers. 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495")

---

### Post by ranch hand on 2009-10-06
> **cheesypoof said:**
> I did look inside grub.cfg and I did run "sudo update-grub" as my previous post stated. Can someone actually post the hidden timeout settings section of their grub.cfg, because I have yet to see it in anybody's posted grub.cfg in these forums. Oh and by the way I just found this script in the past couple minutes at [http://ubuntuforums.org/showthread.php?p=7731488&highlight=press+esc+menu#post7731488](http://ubuntuforums.org/showthread.php?p=7731488&highlight=press+esc+menu#post7731488) which seems to replicate the exact behavior I wanted all along...
You are not interested in my settings.  I hate a hidden menu and my time out is 100.

Reading the problems with the cimt out currently, have you just changed the time out to 2 or 3?

If you remember a while back they had the menu hidden by default and you had to go and comment the bugger to get it to show.  The circle comes around again.

---

### Post by MTGap on 2009-10-06
Well it should be on the same drive... I'm running on an external hdd and I'm almost positive that during the installation I installed it on the same drive. However when I run update-grub my other external hdd starts accessing as well for an extended period (I think it is just looking for other os's) 

Yeah grub is installed, my root on this hdd has the /boot directory. 

Because it is an external HDD during the BIOS I hit F12 to boot from other devices and I select External USB Drive which then goes to my external hdd. But after that it just hangs at the menu. I'm not sure if mine is related to yours because mine comes up immediately it just doesn't do anything afterwards for 20 seconds.





[I]I love ubuntuforms, I get hijacked and people continue to help the hijacker... 

Just to be mean, the next response not directed towards me, will be reported. [/I]

---

### Post by ranch hand on 2009-10-06
I have 3 drives, 2 of which are test platforms.

Of those two, one is internal and one external.  The internal I have 32bit on (I swing both ways with this box) and the external is 64bit.

I have been keeping them separate up until now.  I leave the external turned off, go to bios and turn off half my cpus and my "main" drive.  This boots me to the internal.  For the external I turn the  cpus back on and turn off the "testing" internal and hit the switch for the external.

Two days ago I installed another 9.10 just to play with multi drive booting.  It is on my internal.

When I installed it I had the external on so grub wrote the whole thing.  I copied my custom entry file to it from both drives and edited the externals to reflect the correct drive designation.

Every thing works great.

When I pull up that grub, though, while it responds to the up/down keys fine, takes a long time after clicking on an entry to start up.  There is a total of 21 OS' on 40 partitions.

The external drive is an enclosure with 2 drives.  I don't like anything even similar to raid and that means that I can only boot from one of those drives.  / on one drive and /home on the other.

I think that this makes grub have to do a little sorting out of things and slows it down.

Could something like this be your problem?  You say that it "hangs" but then say that it is for 20 seconds.  I am confused.  When something of mine hangs, it hangs real solid, forever.

This is why all my 9.10 installs have the "Force Quit" button in a handy place.

---

### Post by MTGap on 2009-10-06
I'm not exactly sure how to describe it... I only have on other OS and that is Windows XP. Right when I select to boot from an external usb device the menu will pop up, but once it does I can't select anything (arrow keys or enter don't work at all) The access light on my hdd is then constantly on (not just flashing) and it just sits there I guess then maybe after 20 seconds it will stop accessing and then the menu disappears and it starts loading as if nothing happened. I don't think it has to do any sorting with just a few kernels and only one other OS.

Could it possibly be that there is something wrong with it and it just has some failsafe timeout to start booting into the main option if it can't load something?

---

### Post by schmolch on 2009-10-06
grub2 only works for me if i don't have a config file.
I tried 3 times and have read the documentation every time, but the timeout-setting will never work and it will never autostart when i have a config file.

---

### Post by MTGap on 2009-10-06
You removed /boot/grub/grub.cfg ?

---

### Post by schmolch on 2009-10-06
No, i removed /etc/default/grub and ran update-grub

---

### Post by ranch hand on 2009-10-06
> **schmolch said:**
> No, i removed /etc/default/grub and ran update-grub
WOW, drastic surgery indeed.  Can't argue if it works.

We get grub updates quite often.  I am not sure that I would remove the file.  I would rename it (something like /etc/default/grub.OLD).  It will not be used but it would be there to try if it was not replaced.  It can be deleted at a later date if that is needed.

---

### Post by autocrosser on 2009-10-06
> **MTGap said:**
> I'm not exactly sure how to describe it... I only have on other OS and that is Windows XP. Right when I select to boot from an external usb device the menu will pop up, but once it does I can't select anything (arrow keys or enter don't work at all) The access light on my hdd is then constantly on (not just flashing) and it just sits there I guess then maybe after 20 seconds it will stop accessing and then the menu disappears and it starts loading as if nothing happened. I don't think it has to do any sorting with just a few kernels and only one other OS.

Could it possibly be that there is something wrong with it and it just has some failsafe timeout to start booting into the main option if it can't load something?

I'm not sure if it's the same problem either--depends if your system is still using the MBR on your internal drive--if so--you do have the same problem.....I would think that even forcing a boot from a external drive you access the Main MBR--so in that case you fall under the bug.

---

### Post by MTGap on 2009-10-07
I don't think grub touches my mbr. I only see grub when I boot from the external, the internal is all by itself.

I guess I'll try renaming my /etc/default/grub

---

### Post by MTGap on 2009-10-14
Well I just got around to removing /etc/default/grub and I'm back to my original spot, I see the menu and can select different kernels but afterwards I have to wait 30 seconds before it starts loading, here's my /boot/grub/grub.cfg:

> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "GNU/Linux, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro   
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "GNU/Linux, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "GNU/Linux, Linux 2.6.31-10-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro   
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "GNU/Linux, Linux 2.6.31-10-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=6ffb52ea-68e6-47fe-9c18-2fdc4388b9cc ro single 
	initrd	/boot/initrd.img-2.6.31-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c298efd998efca4d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by MTGap on 2009-10-15
Bump, could I get any help?

---

### Post by MTGap on 2009-10-16
I guess I'll try again...

---

### Post by kansasnoob on 2009-10-16
> **MTGap said:**
> I guess I'll try again...

OK, I'll try. I assume you can still boot Ubuntu, and Ubuntu is on an external drive??

If so (while booted into Ubuntu) post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by MTGap on 2009-10-16
Yes I can boot into it and it is on an external hdd, I've never had issues before grub2 fdisk -l:

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        9342    74983387+   7  HPFS/NTFS
/dev/sda3            9343        9725     3076447+  db  CP/M / CTOS / ...

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3c9998e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4659    37423386   83  Linux
/dev/sdb2            4660        4864     1646662+   5  Extended
/dev/sdb5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x150e6069

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    7  HPFS/NTFS


I'm on sdb.

sda is Windows and sdc is just an external hdd.

---

### Post by kansasnoob on 2009-10-16
> **MTGap said:**
> Yes I can boot into it and it is on an external hdd, I've never had issues before grub2 fdisk -l:



I'm on sdb.

sda is Windows and sdc is just an external hdd.

When you say that sdc is just an external drive I need to know if it contains an operating system.

We'll get through this!

---

### Post by kansasnoob on 2009-10-16
Regardless run this command:

```
sudo apt-get install --reinstall grub-pc
```

and then:

```
sudo update-grub
```

---

### Post by MTGap on 2009-10-16
Nope, sdc has no OS. I've just performed the commands and I'll get back to you once I reboot to see the results.

I don't have a /etc/default/grub file anymore due to the advice of one poster, which resolved the freezing issue but not the timeout issue. It's not there after reinstall should I create that file again?

---

### Post by kansasnoob on 2009-10-16
> **MTGap said:**
> Nope, sdc has no OS. I've just performed the commands and I'll get back to you once I reboot to see the results.

I don't have a /etc/default/grub file anymore due to the advice of one poster, which resolved the freezing issue but not the timeout issue. It's not there after reinstall should I create that file again?

I'm hoping we'll get you back to square one with those commands. That's why I recommended the reinstall.

---

### Post by kansasnoob on 2009-10-16
Just FYI:

> # GRUB_HIDDEN_TIMEOUT=0

    * The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * **[COLOR="Red"]Bugs still exist in this feature. Hiding the menu may or may not work.[/COLOR]**
    * The default setting initially depends on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
          o No other OS Detected: The menu will be hidden.
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    * 0 The menu will not be displayed. There will be no delay.
          o When this entry is set to 0:
                + The user may force displaying the menu as the computer boots by holding down the SHIFT key.
                + During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key.
    * If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected.


And I've personally found that to be true!

---

### Post by MTGap on 2009-10-16
Yes, but I don't believe that is my issue with seeing or not seeing the menu. Something else is happening where it doesn't actually start booting for 20+ seconds. 

Hidden Timeout means that the menu is hidden but you can access it with hitting SHIFT or ESC.

Mine I see the menu and then it just sits there after I select what to boot from.

---

### Post by kansasnoob on 2009-10-16
Uh, I'd honestly thought you'd lost the ability to boot after playing with grub2.

If you can boot and you're simply dissatisfied with how it works you might consider reverting to legacy grub:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

You have me quite confused.

---

### Post by MTGap on 2009-10-16
I guess I'm not unsatisfied with it, I can live with waiting 20 seconds.

---

### Post by drs305 on 2009-10-16
The 20 second issue was reported as a bug and I've heard of more than several users having that problem. I haven't seen a solution, or cause, for that matter.

@ kansasnoob,

I discovered that if I include the following line in my /etc/default/grub I can get the hidden menu to work (of course it disables the search of other partitions). FALSE doesn't work. It's the only way I've been able to do it so far on my 64-bit machine. 

> 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=15
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="15"
**GRUB_DISABLE_OS_PROBER="true"**


---

### Post by MTGap on 2009-10-17
Yeah I'm not sure what it is now, no change after reinstall. I'm thinking it may be not grub related at all.

---

### Post by ranch hand on 2009-10-17
What video card/controller do you use?
 
This may be GDM related.

---

### Post by MTGap on 2009-10-17
I have a NVIDIA 9400 GT, and I don't use Gnome, I use KDE. I don't think it is KDM, because this happens way before that and after the 20 second period I see the startup commands as Ubuntu boots up.

---

### Post by ranch hand on 2009-10-17
Sorry, I knew that.  Long day in the saddle after a month of pretty much laying down with a horendous leg infection.

I am even simpler than I normally am.  I am whipped.  Only rode for 7 straight hours, strange saddle but my horse.  Gathered cow/calf pairs in 6000 acre pasture, moved them down hill through the next pasture (same size), and out ot the next one.  300 pairs.  We will be back tomorrow and get the ones we missed (about 100 pair), move them down with the others, and then take the whole bunch another 6-7 miles to the corral so wee can process the calves for weaning/shipping.

God, I love my work.  Out doors, great company, hard work, FUN.

---

### Post by zika on 2009-10-18
> **ranch hand said:**
> God, I love my work.  Out doors, great company, hard work, FUN.Just enjoy, I do envy You even though I do not think I would endure that ...

---

### Post by VMC on 2009-10-18
> **ranch hand said:**
> Sorry, I knew that.  Long day in the saddle after a month of pretty much laying down with a horendous leg infection.

I am even simpler than I normally am.  I am whipped.  Only rode for 7 straight hours, strange saddle but my horse.  Gathered cow/calf pairs in 6000 acre pasture, moved them down hill through the next pasture (same size), and out ot the next one.  300 pairs.  We will be back tomorrow and get the ones we missed (about 100 pair), move them down with the others, and then take the whole bunch another 6-7 miles to the corral so wee can process the calves for weaning/shipping.

God, I love my work.  Out doors, great company, hard work, FUN.Sounds like a movie set. Montana's calling me.

---

### Post by ranch hand on 2009-10-18
Hey, today we had a bunch of riders of the female variety!  Better scenery than just us old crusty grumpy geezers.

---

