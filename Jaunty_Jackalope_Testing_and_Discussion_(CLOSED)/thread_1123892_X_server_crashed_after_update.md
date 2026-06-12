---
title: "X server crashed after update"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by adalal on 2009-04-12
Hi,

I put my computer to download and install all updates and I left the room and went out. Now, I've got a problem, I came back, trying to access my computer, it wouldn't respond and come out of the power saving mode where the screen turns off.

I reboot the computer manually, and now, when X server starts up, I get this message:

```
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix thie problem.

View details (~/.xsession-errors file):

/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: 129: cannot create /dev/null: Permission denied

```

The /etc/gdm/Xsession errors listed the same problem with the numbers 129, 130, 148, 192 (this one a several times).. and then

```
 /etc/gdm/Xsession: executing default failed, will try to run x-terminal..
Failed to get the session bus: Failed to execute dbus-launch to auto ... * cannot see the rest *
Failed to contact the GConf daemon; exiting. 
```

The failsafe session i tried to login to would not respond at all... i think i'll revert back to resinstalling jaunty on it with a live CD...

oh, and i can't access any other screens (tty1, etc.)

EDIT:
Oh, just one more thing that might help, it's set to log in automatically.

EDIT 2:
Great! The daily live download today seems to be failing miserably... comes up with a BusyBox terminal...

---

### Post by ShelJ on 2009-04-20
Hi [adalal]("http://ubuntuforums.org/member.php?u=693413"),

I'm running into the same problem, wondering if you have fixed it?

At first I thought that a fresh install might help, but it made it worse.

here is the information that I get:

```
Your session only lasted less than 10 seconds. 
 If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  
Try logging in with one of the failsafe sessions to see if you can fix this problem.
```and here is the .xsession-error file:

```
                                        [LEFT]/etc/gdm/Xsession: Beginning session setup...[/LEFT]
    [LEFT]/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found[/LEFT]
    [LEFT]Setting IM through im-switch for locale=en_CA.[/LEFT]
    [LEFT]Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.[/LEFT]
    [LEFT]/usr/bin/xmodmap:  unable to open file '/usr/share/kubuntu-default-settings/kubuntu.xmodmap' for reading[/LEFT]
    [LEFT]/usr/bin/xmodmap:  1 error encountered, aborting.[/LEFT]
    [LEFT]/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading[/LEFT]
    [LEFT]/usr/bin/xmodmap:  1 error encountered, aborting.[/LEFT]
    [LEFT]** Message: Querying XF86Misc extension[/LEFT]
    [LEFT]** Message: XF86Misc extension found[/LEFT]
    [LEFT]** Message: Querying Xkb extension[/LEFT]
    [LEFT]** Message: Xkb extension found[/LEFT]
    [LEFT]** Message: Querying XINPUT extension[/LEFT]
    [LEFT]** Message: XINPUT extension found[/LEFT]
    [LEFT]** Message: Querying Xkb extension[/LEFT]
    [LEFT]** Message: Xkb extension found[/LEFT]
    [LEFT]** Message: another SSH agent is running at: /tmp/ssh-kqkdhH4891/agent.4891[/LEFT]
        [LEFT]** (nm-applet:5098): WARNING **: No connections defined[/LEFT]
       
  
```

---

### Post by adalal on 2009-04-20
not that i found a fix, but i ran it on the console (tty1), and ran upgrades... I switched off the computer and then turned it on the next day, and it was working again, so, I'm guessing it was an intermediary problem? I think the permissions get changed, although dev null does not exist and doesn't have any permission afaik... hoping to get a lil more insight into this...

---

### Post by ShelJ on 2009-04-21
Thanks, it's not the next day, but I've restarted my computer twice already, and there's no msg.

You should post your solution, which you've pretty much done, and mark it as solved.

Thanks. again!

---

### Post by adalal on 2009-04-21
> **ShelJ said:**
> Thanks, it's not the next day, but I've restarted my computer twice already, and there's no msg.

You should post your solution, which you've pretty much done, and mark it as solved.

Thanks. again!

Well, to be honest, I didn't to much, all i did is try chmod 666 on /dev/null and all, although something tells me that it isn't right, but other than that... it was a matter of updating for me... 

And I would've marked it as solved, but [the ability to do that has been removed]("http://ubuntuforums.org/showthread.php?t=767621&highlight=mark+solved").

---

