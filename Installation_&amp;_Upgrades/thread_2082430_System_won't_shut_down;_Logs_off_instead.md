---
title: "System won't shut down; Logs off instead"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2012-11-09
I'm using 12.04 in dual boot with windows 7. I can't recall when this started but sometime in the past 2 months approximately, if I try to shut down or restart the computer from within Ubuntu, it only logs off my current session. I cannot force it to actually shut down without doing a hard stop (ie: power button).
I haven't been tweaking the system in any odd way so I don't know how this got introduced. I do need to shut down or restart when I want to enter the windows world for work purposes. Otherwise, the computer is almost always on in Ubuntu and used for general purpose computing & provides in-home media repository.
Any ideas of how to correct this would be appreciated as I hate to repetitively need to do hard restarts. Thank you.

---

### Post by 2F4U on 2012-11-09
Can you shutdown from a terminal? Open a terminal and enter

sudo shutdown -h now

---

### Post by flyingsolo on 2012-11-09
> **2F4U said:**
> Can you shutdown from a terminal? Open a terminal and enter

sudo shutdown -h now
Yes, this does perform a proper shutdown of the computer.
So, thanks, at least I don't have to keep using the power down button.
But, still, what could have occurred to change the usual manner of shutting down? I have gone to 'suspend' sometimes; could that somehow introduce a problem? (it comes out of suspend just fine)

---

### Post by flyingsolo on 2012-11-14
Still looking for more help, please.
Thanks to 2F4u for the command line method to shutdown the computer but still, what could have gone wrong with the standard method of shutting down from the panel button?
Any suggestions would be appreciated.
thanks

---

### Post by offgridguy on 2012-11-14
Do you have more than one user account?  If yes, you have to log out each user account to
shutdown.

Thank you 2F4U for that useful bit of information.

---

### Post by flyingsolo on 2012-11-14
No, just me as user.

---

### Post by offgridguy on 2012-11-14
> **flyingsolo said:**
> No, just me as user.
 
Well that takes care of theory #1.
Does it make any difference if you log out first, then try shutdown?

---

### Post by flyingsolo on 2012-11-17
Just caught up to your reply now.
No, it doesn't matter if I log out. In fact, when I try to shut down, essentially it just logs me out of the current session and then from that screen, if I try to shut down, nothing happens and I am left at the same log in screen.

---

### Post by yoramdavid on 2012-11-17
If I may use your threat as well, I am experiencing the exact same problem. This happened after upgrading to Ubuntu 12.04.

---

### Post by BLNCNMRQ on 2012-12-31
> **yoramdavid said:**
> If I may use your threat as well, I am experiencing the exact same problem. This happened after upgrading to Ubuntu 12.04.

I am having exactly the same problem. It occured a couple of days ago.

---

### Post by flyingsolo on 2013-01-21
I've been away from this thread for some time. Sorry to see more people with same. I haven't a solution but I usually leave it on anyway; just need to shutdown for some updates & occasional need to use Windows.
Anyone else discover why this happens or a fix?

---

### Post by Synnefo on 2013-01-22
I just upgraded from 12.04 to 12.10 and am facing the same problem.
Googling it leads to other threads/forums with the same problem with no solution. A bug this common should be fixed soon!

---

### Post by SlugSlug on 2013-01-22
Am getting this on a remote Mint machine

---

### Post by DaBungalow on 2013-01-26
> **yoramdavid said:**
> If I may use your threat as well, I am experiencing the exact same problem. This happened after upgrading to Ubuntu 12.04.


I also have this problem.  Have there been any solutions.  I have found that ```
sudo shutdown -P now
``` does work as a temporary solution.  Here is my error log after trying to shutdown.

```
[17755.647438] type=1400 audit(1359182078.488:100): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1101/stat" pid=1990 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=115 ouid=0

```

---

### Post by yoramdavid on 2013-01-26
If there are solutions, I do not know. I am still having this problem for a very long time now.

Half of the times I shut down, it reboots.

What amazes me is that there have been many updates and none corrected that problem!

Regards,
Yoram

---

### Post by QwUo173Hy on 2013-02-01
I'm having this problem on 12.04 since installing a backlog of updates in December 2011. Disabling networking altogether seems to fix it (or at least, on the next reboot).

It's not a viable solution but could you all verify that this fixes the issue? It may indicate the problem area.

---

### Post by lonewohlf42 on 2013-02-01
I have the same problem. I have 2 computers. 1 I built and an HP that I bought for my wife. Everything was working fine in 12.04 but since I upgraded both machines to 12.10 I can no longer shutdown my computers. When I try to shut them down I end up on the log in screen. I can log back in but I can never shutdown. I'm hoping a future update will fix them or maybe someone will come up with an idea. Maybe when 13.04 comes around the
problem will be fixed. It seems like a lot of people are having the same problem.

---

### Post by technoshaman on 2013-03-22
I have the same problem after upgrading to Ubuntu 12.10. If I log out, or command to shut down, I get back to the login screen. Sometimes it does a reboot, but just won't stay off.

---

### Post by Dabo Ross on 2013-04-05
I am getting this in 12.10. It is a relatively new install, and this problem started 2 days ago. I re-installed Ubuntu 2-3 weeks ago.
I am the only user on the computer. When I click shutdown or restart in menu, I end up on log-in screen, with no error message.
When I try shutdown or restart from the login screen nothing happens. 
I have been just hibernating for the past few days, to get around this problem.

I am getting This in /var/log/syslog:
Apr  5 10:48:43 DaboUbuntu gnome-session[30423]: WARNING: Unable to stop system: Authorization is required
When I try to shutdown.

[SIZE=3][B]I think I found what was happening to me. Someone had logged on to the guest account, and hadn't logged off.
Logging into then out of the guest account fixed it for me.[/B][/SIZE]

Oh, and BTW, I found these other things on this bug:
[http://askubuntu.com/questions/71506/i-cant-shut-down-nor-reboot-without-console](http://askubuntu.com/questions/71506/i-cant-shut-down-nor-reboot-without-console)
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/861171](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/861171)
[http://askubuntu.com/questions/243630/shut-down-takes-me-to-greeter-now](http://askubuntu.com/questions/243630/shut-down-takes-me-to-greeter-now)

And that last one has a solution:

> Create a file named /etc/polkit-1/localauthority/50-local.d/usershutdown.pkla (the name must end in .pkla) and put the following in it:

```
[Allow Shutdown]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=yes
ResultInactive=yes
ResultActive=yes

[Allow Restart]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=yes
ResultInactive=yes
ResultActive=yes
```

---

### Post by Allavona on 2013-04-05
I am experiencing a similar problem. Sometimes the computer will actually shutdown but more often than not it hangs on the screen with the Ubuntu name and the purple dots. Two dots will fill, and then nothing. I left it one night for about ten minutes thinking that it would "catch up" with itself, but it didn't. On a crazy note, I can shutdown properly with a *sudo poweroff *command in the terminal.

---

### Post by redemption024 on 2013-04-14
I'm on a fresh install of 12.10 (wubi) and I got this problem every couple shutdown or restart. Thanks to the answer given, that really helps coz I'm going nuts trying to shut this damn thing down.

---

### Post by notbitmonk on 2013-06-13
I have the same problem. It started a couple of weeks ago. Using 12.04 since it came out. I have done a couple fresh installs during the year. Mostly a vanilla configuration with Geographical Information Software and DarkTable (photographt) repositories added. I am the only user configured in the computer.  sudo shutdown -P now works OK.

---

### Post by zivley on 2013-06-14
> **Dabo Ross said:**
> I am getting this in 12.10. It is a relatively new install, and this problem started 2 days ago. I re-installed Ubuntu 2-3 weeks ago.
I am the only user on the computer. When I click shutdown or restart in menu, I end up on log-in screen, with no error message.
When I try shutdown or restart from the login screen nothing happens. 
I have been just hibernating for the past few days, to get around this problem.

I am getting This in /var/log/syslog:
Apr  5 10:48:43 DaboUbuntu gnome-session[30423]: WARNING: Unable to stop system: Authorization is required
When I try to shutdown.

[SIZE=3][B]I think I found what was happening to me. Someone had logged on to the guest account, and hadn't logged off.
Logging into then out of the guest account fixed it for me.[/B][/SIZE]

Oh, and BTW, I found these other things on this bug:
[http://askubuntu.com/questions/71506/i-cant-shut-down-nor-reboot-without-console](http://askubuntu.com/questions/71506/i-cant-shut-down-nor-reboot-without-console)
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/861171](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/861171)
[http://askubuntu.com/questions/243630/shut-down-takes-me-to-greeter-now](http://askubuntu.com/questions/243630/shut-down-takes-me-to-greeter-now)

And that last one has a solution:

Create a file named /etc/polkit-1/localauthority/50-local.d/usershutdown.pkla (the name must end in .pkla) and put the following in it:

[Allow Shutdown]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=yes
ResultInactive=yes
ResultActive=yes

[Allow Restart]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=yes
ResultInactive=yes
ResultActive=yes



I had the same problem, it started after upgrading from 12.10 to 13.04, so if someone is hoping the upgrade to 13.04 will fix it, don't hold your breath...
Anyway, this solution proposed by Dabo Ross worked for me!
Thanks!

---

### Post by barefootNH on 2013-07-02
> **offgridguy said:**
> Do you have more than one user account?  If yes, you have to log out each user account to
shutdown.


Since this thread is still alive and the bug hasn't been fixed, I'll hop on here and share my similar problem that always seems to have been there. I have 12.04 LTS, always fully updated, on a year-old Acer laptop; 12.04 was fresh installed dual-boot with Windows 7 when the laptop was just a day or so old. 

I have this shutdown problem only when there is another user logged on. Even Windows allows you to log off even if there are other users logged on.

Thanks to this thread I just tried sudo poweroff and it worked.

Is this a bug, or a dangerous undocumented feature?!

---

