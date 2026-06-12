---
title: "Ubuntu Freezes after Install."
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by zellfaze on 2010-02-17
**Problem:** Ubuntu freezes up 30 seconds or so after a successful login.

**Background:**
I am running a [Compaq Presario SR5030NX](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12132708-12133156-78308260-78308260-78308260-79685091-80248998.html).  It has had issues for a while with running Ubuntu properly.  My computer suffers from [this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421).  I have managed to get the LiveCD running by adding the following to my boot parameters:

```
vga=792 i915.modeset=0
```

When I was running the LiveCD I found that it would freeze after about 30 seconds.  I solved this problem by again changing the boot options.  This time I:
[list][*]Press _F6_
[*]Check *noapic*, *nolapic*, and *pci=noacpi*[/list]

I then proceeded to install Ubuntu.

My problem arose when Ubuntu did not modify *grub.cfg* to match the setting I needed in order to boot.  I managed to modify in some of the settings correctly, I believe at least, but not all of them.

In its current state Ubuntu is able to boot, but freezes 30 seconds or so after a successful login.  If I do not graphically login, I do still have access to VTY1-6.  The machine does not freeze until a successful graphical login has been made.

Below is the relevant section of my *grub.cfg*:
```
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set daa29a0c-e7d1-43ed-99fc-b52dcc504b4a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=daa29a0c-e7d1-43ed-99fc-b52dcc504b4a ro noapic nolapic pci=noacpi  vga=792 i915.modeset=0 splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
```
Full file is available here: [http://pastebin.com/f66a14138](http://pastebin.com/f66a14138)

Here is a copy of my */etc/default/grub*:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="vga=792 i915.modeset=0 splash"
GRUB_CMDLINE_LINUX="noapic nolapic pci=noacpi"

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

I would greatly like to see this problem solved quickly.  I have been running off a liveCD for over 6 months now.  Which as one can imagine, is not fun.

On another note:
The liveCD I have been running for 6 months is BackTrack 3 Final.  Which does not have this issue at all.  I would wager a guess that BackTrack 4 does though as it is based off Ubuntu instead of Slax.

---

### Post by zellfaze on 2010-02-19
I hate to double post, but I think I have good reason to this time.

I found a work-around to my problem in the above post.

But before I get to that, I want to continue the story of my problem.  Before I found a work-around I spent more time trying to diagnose and correct the issue.

The additional steps I took, and their outcome have been listed below:
[list][*]I booted my computer.
**Result:** Same as nothing was changed.
[*]I changed the /etc/default/grub to its current state.  In its current state only the word splash is on the line LINUX_DEFAULT, everything else is just on LINUX.
**Result:** Computer still froze.  But I could now boot recovery mode.
[*]I booted up.  Logged into a VTY1 just to make sure it still worked.
**Result:** Computer worked, until I logged into a graphic login.  Then it froze.
[*]I booted up. Logged into the graphical login, then quickly switched to VTY1 to check for error messages.
**Result:** Interesting, all I saw was the the picture below.
[[IMG]http://img715.imageshack.us/img715/4060/palringo134222941533727.th.jpg[/IMG]](http://img715.imageshack.us/i/palringo134222941533727.jpg/)
*Click for full view.*[/list]

Anyhow, as I said, I did find a work-around. If anyone could explain to me why my work-around works, I would appreciate it greatly.

**Work Around:**
[LIST=1][*]Modify Grub to have a timeout. This way you can access the boot menu. *This can be done via /etc/default/grub*
[*]When your computer boots, select recovery mode kernel from the boot menu.
[*]Select Login as root from the next menu to pop up.
[*]You are now dropped into a root shell.
[*]Type *su yourUserName* This will log you in.
[*]Type *startx* This will give you a GUI.
[/LIST]

As I said, I am not sure why it works, and I would love to know.  I suspect it has something to do with GDM not being loaded.

Best of luck to anyone else who has this issue.

Love,
Haxor ~Zell Faze~
<3

**EDIT *(about 20 seconds after original posting)*:**
I just wanted to make note of this.  I have not marked this topic as solved for a reason.  This problem was not solved, an acceptable work-around was just found.  I still consider this a problem, I am thinking about reporting it to Bugzilla in fact.

---

### Post by chris_lukehart on 2010-02-20
After installation of 9.10 it does not apply kernel options for some odd reason 

Steps to fix it:

1)press shift to get to grub2

2)press a letter (not sure) look below it tells you

3)apply kernel options (this is temporary to get it to boot)

4)it should boot now

5)in terminal sudo nano /etc/default/grub
   A)enter your password
  
6)apply kernel options (permently)
A)ctrl o (to save)
b)ctrl x (to exit)

7)update-grub

8)shutdown -r now

9)It should finally work!!!!!!!!:p;):D:):P

---

