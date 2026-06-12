---
title: "Cursor is always busy cursor after upgrade to 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by snail2go on 2010-05-01
Am running Ubuntu NBR as the sole OS on my Dell Mini 9. Switched over in March to 9.10 NBR. Everything worked fine.
Upgraded to 10.04 when it was released. It's awesome EXCEPT for this busy cursor thing.
As soon as I log in, all the time my cursor is the spinning wheel of busyness.... It works just as a normal cursor would - my computer also does not seem to be slower due to any operations...
If I open an application, the cursor will behave as usual within the window but if I more my cursor to the title bar or switch out of the application, the "busy cursor" resumes.

I am very confused? Anyone else having this problem?

---

### Post by landar_c on 2010-05-03
Try this solution.  It worked for me.  I had told Ubuntu One to not load at bootup, since I don't use it but, it was still in the .gtk-bookmarks file.  Once I removed the Ubuntu One line and rebooted, all was back to normal.
 
[http://ubuntuforums.org/showthread.php?p=4414151#post4414151](http://ubuntuforums.org/showthread.php?p=4414151#post4414151)

---

### Post by snail2go on 2010-05-03
Awesome! Thanks a bunch!

---

### Post by XProflmfao on 2010-05-05
Hi there,
   I am currently using Ubuntu Lucid Lynx 9.10. Although I followed your steps on the other thread, however, I could not find the [FONT=monospace]‘[/FONT]x-nautilus-&#12290;desktop:///Music%20on%20server.volume‘ or anything similar to it inside my .gtk-bookmarks file. This is what mine showed:

[PHP]file:///home/bailey/My%20Files
file:///home/bailey/Music
file:///home/bailey/Pictures
file:///home/bailey/Videos
file:///home/bailey/Downloads[/PHP]

The loading mouse cursor happens within nautilus items on the desktop (for example, title bars, top panel and the drop down menus, and the file browser), and on AWN. There might be still some others that I have yet to uncover. I am not exactly sure what caused this, but I kind of remember it happening when I was using Compiz on the computer.

---

### Post by teplow on 2010-05-16
I have the same problem with 10.04 LTS on a Samsung NC-10. Cursor just spins all the time. Neither the .gtk-bookmarks fix or the Ubuntu One fix worked.  Anyone have an other ideas?

---

### Post by criball on 2010-05-19
I have the same problem with 10.04 LTS on an ASUS eee 1005h and it just occurred after the update to lucid. The cursor start spinning after the login and never stops. I tried to disable ubuntu one without result. Also .gtk-bookmarks file seems to be ok. What's really disappoints me is that, while the 90% of the session have this busy cursor, in some session the cursor is back to normal and I can't understand why.
If anyone have an idea about how to solve the problem it would be really great!

---

### Post by landar_c on 2010-05-23
Well, the previous "fix" I found only worked for a short time.  Still, on most boots I get the busy cursor and have not found the cause yet.  Nautulis is waiting for something....

---

### Post by XProflmfao on 2010-05-23
Actually, I might have found the possible problem that's causing all of this. I remember sometimes when I shut down the computer, it'll say, "The following programs are still running" and one of them will be "Unknown-Not Responding" which then I have to click on "Shut Down Anyway" at the bottom right corner of the window. However, I'm not sure what exactly it is, since it doesn't tell me what the program is that's not responding.
      It's possible that the program is actually compiz since it was the cause of the spinning cursor. Hoewever, this has in some cases spread to Metacity too so I might be wrong. :confused:

---

### Post by eliotpbrenner on 2010-06-03
I have the same problem.  Tried the fixes outlined above and they didn't help.  Did anyone manage to solve this?

Thanks.

---

### Post by landar_c on 2010-06-04
I'm stumped.  I created a new user and it doesn't have the problem, so I can replace the config files one at a time to find out what is causing it, or just move my files and change the owner to a new user.... boy, either way is going to be fun... :-(
 
I'll post my results when I get time to do either of these.

---

### Post by eliotpbrenner on 2010-06-04
for me the problem has now stopped just as mysteriously as it started, after a few reboots.  Maybe something I did following the threads above solved the problem but took some time to take effect, or maybe it will come back.  Time will tell...

---

### Post by eliotpbrenner on 2010-06-06
yeah, the problem comes back on most, but not all boots.
This makes the computer run hot all the time and the battery run out very quickly.  Very unfortunate...

---

### Post by glomboi on 2010-06-11
Not an exact fix, but it does get rid of that cursor!

[http://ubuntuforums.org/showthread.php?t=656232#4](http://ubuntuforums.org/showthread.php?t=656232#4)

Same link as before, but an earlier 'solution' from NiceGuy.

I don't have a problem with my .gtk-bookmarks but when I disable "Show Desktop", the busy cursor disappears.

Since the desktop isn't required on UNR, this part-solution is good enough for me for now.

To disable the traditional desktop:
[LIST]
[*]Alt + F2
[*]Enter 'gconf-editor'
[*]Apps > Nautilus > Preferences
[*]Uncheck the box next to "Show Desktop"
[/LIST]

Hope this helps someone!

---

### Post by eliotpbrenner on 2010-06-11
Thanks glomboi, but I tried your advice, but the box next to "Show Desktop" is already unchecked.  Under "key documentation" it says "This key is not writable" and it doesn't allow me to change (i.e., check) it.

Other ideas?

---

### Post by glomboi on 2010-06-13
> **glomboi said:**
> Not an exact fix, but it does get rid of that cursor!

[http://ubuntuforums.org/showthread.php?t=656232#4](http://ubuntuforums.org/showthread.php?t=656232#4)

Same link as before, but an earlier 'solution' from NiceGuy.

I don't have a problem with my .gtk-bookmarks but when I disable "Show Desktop", the busy cursor disappears.

Since the desktop isn't required on UNR, this part-solution is good enough for me for now.

To disable the traditional desktop:
[LIST]
[*]Alt + F2
[*]Enter 'gconf-editor'
[*]Apps > Nautilus > Preferences
[*]Uncheck the box next to "Show Desktop"
[/LIST]

Hope this helps someone!

Oops... Turns out this only worked for a few days, I'm back to square one with this cursor as well.

I did, though, have two instances of Nautilus running, is this normal?
I ended one process and the busy cursor went away, as did the netbook-launcher, and it is refusing to load again.

[Edit] Netbook launcher worked again after killing the previous netbook-launcher and restarting it via Alt+F2.

---

### Post by landar_c on 2010-06-16
Ok, I've noticed a pattern.  If I let my computer sit at the Login prompt for a few minutes (3-5) before logging in, I do NOT get the busy cusor.  There is some sort of race condition going on where something has to finish before you login.  And it explains our sporadic results, if we lengthen the boot time, whatever it is has time to finish before we login.
 
Maybe this will spur some other thoughts and a proper solution.
 
Randal

---

### Post by glomboi on 2010-06-17
> **landar_c said:**
> Ok, I've noticed a pattern.  If I let my computer sit at the Login prompt for a few minutes (3-5) before logging in, I do NOT get the busy cusor.  There is some sort of race condition going on where something has to finish before you login.  And it explains our sporadic results, if we lengthen the boot time, whatever it is has time to finish before we login.
 
Maybe this will spur some other thoughts and a proper solution.
 
Randal
Randal,

This seems to work for me too...

Only tried it once or twice but does seem to answer the quieries.

How do we find a solution to this one!?

---

### Post by Rorie on 2010-08-03
I've had trouble with this too. My best fix so far is to install a new user profile and copy your documents across. 

There must be something from your old (probably gnome) profile that conflicts after the upgrade, so starting with a fresh user profile has resolved this for me.

Hope this helps some of you.

---

### Post by Rorie on 2010-08-03
...having deleted all hidden directories in my old profile I have fixed the problem there too. If any boffins know which files cause the bug please post so this fix can be made more efficient.

---

### Post by mkulon on 2010-09-18
Same bug here after upgrade to Lucid Lynx.  I am 99% sure this is caused by nautilus launching & quitting repeatedly, but have not figured out a reason or a fix for this yet -- any ideas???

Notice that with each invocation of "ps", the process ID changes (2nd column), and sometimes there is a [nautilus] <defunct> process

me@Computer:~$ ps aux | grep "naut"
me    2643  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    2651  0.0  0.2 427640 13744 ?        Rl   16:52   0:00 nautilus
me    2654  0.0  0.0   7624   900 pts/0    S+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    2703  0.0  0.0      0     0 ?        D    16:52   0:00 [nautilus]
me    2705  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    2708  0.0  0.0   7624   900 pts/0    S+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    2741  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    2744  0.0  0.0   7624   900 pts/0    S+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    2763  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    2766  0.0  0.1 197692  9284 ?        R    16:52   0:00 nautilus
me    2768  0.0  0.0   7624   900 pts/0    S+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    2803  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    2807  0.0  0.0 168056  4264 ?        R    16:52   0:00 nautilus
me    2809  0.0  0.0    356   100 pts/0    R+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    2823  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    2830  0.0  0.1 197560  9060 ?        R    16:52   0:00 nautilus
me    2832  0.0  0.0   7624   896 pts/0    S+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    3448  0.0  0.0      0     0 ?        Zl   16:52   0:00 [nautilus] <defunct>
me    3452  0.0  0.1 197560  8616 ?        R    16:52   0:00 nautilus
me    3454  0.0  0.0   7624   900 pts/0    S+   16:52   0:00 grep --color=auto naut
me@Computer:~$ ps aux | grep "naut"
me    3601  0.0  0.1 280328 10580 ?        Rl   16:52   0:00 nautilus

---

### Post by mkulon on 2010-09-18
This seems to fix the problem, but I bet this will recur on reboot:
killall nautilus

Does anyone have an idea about a root cause?

---

### Post by quincunx on 2010-12-07
I've looked at everything listed previously.  My .gtk-bookmarks file looks clean, I looked in gconf-editor under Apps/Nautilus/Preferences and noticed that "Show Desktop" is unchecked.

While reading forums, I noticed something about Ubuntu One, and I had removed that long before upgrading (but it came back with the upgrade, along with other unwanted apps; Epiphany Gwitter).  After removing all references to "Ubuntu One" in Synaptec, the cursor was normal.  Later I logged out, and back in, and got the busy cursor again.

I keep thinking the "Upgrade" button isn't going to be a pain.  At least it's not as bad as upgrading from Breezy.

Anyone have any other ideas of where to look?

---

### Post by quincunx on 2010-12-17
This issue seems to behave inconsistently.  I think I've found one way to repeat it, and that is by selecting "Restart".  If I Shutdown, and boot up, the cursor usually behaves as normal (not always).  When I select Logout, and log back in, I get inconsistent results and believe this is related to how long I wait to login.

With the exception of one time, the wait cursor causes a dialog box to appear when logging out/restarting/shutting down.  It says:

```
A program is still running:
Unknown
Not Responding

Waiting for program to finish.
Interrupting program may cause you to
lose work.
[Lock Screen]   [Cancel]   [Logout Anyway]
```

I hope these clues can offer some insight as how to troubleshoot further.

Thanks in advance for any suggestions.

---

### Post by danacbor on 2011-01-13
I had the same problem.
It was nautilus issue, segmentation fault after update.

The solution:
1. delete cached packages from /var/cache/apt
2. disable all third party repositories
3. completely remove nautilus and gnome-session packages
4. reload package data
5. install nautilus and gnome-session
6. reboot

Steps 2-5 easily done from synaptic.

Good luck.

---

