---
title: "Upg from 11.04 to 11.10 - LightDM fails to load"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2011-10-14
Count me among the many who now have an unusable system due to the in-place upgrade (I should've known better and done a clean reinstall).

My System76 laptop won't boot up properly. LightDM fails because the NVidia stuff is completely hosed. I can't see details why, but Xorg and lightdm logs just say the nv module failed to load. Might be something with the new Linux 3.0 kernel? I'm not sure. All I know is, I've gotta get stuff done and this really put a damper on things.

Any help would be appreciated.

---

### Post by 23dornot23d on 2011-10-14
alt+ctrl+f1 ..... will get to a terminal screen log on as normal and then ......

Try to install nvidia-current

[B]sudo apt-get install aptitude
sudo aptitude install nvidia-settings

[/B][B]sudo aptitude install nvidia-current

[/B]*watch what it says on screen as it installs ..... look for any fail ....**hopefully it will be ok and load the modules as required*

---

### Post by CaptSaltyJack on 2011-10-14
Those nvidia packages are already installed.

---

### Post by 23dornot23d on 2011-10-14
When you boot up can you still select to drop into the previous kernel

I have heard others say that this works for them ......

---

### Post by vortex-5 on 2011-10-14
I'm having a similar issue:

[http://ubuntuforums.org/showthread.php?t=1859887](http://ubuntuforums.org/showthread.php?t=1859887)

I sort have caused it.

After seeing that lightdm loaded fine I did

apt-get purge gdm 

and for whatever reason lightdm won't load anymore

---

### Post by 23dornot23d on 2011-10-14
to put gdm back

sudo apt-get install aptitude
sudo aptitude update
**sudo aptitude install gdm**

if you want lightdm

**sudo aptitude install lightdm**


choose the preferred DM when it asks you .......

I sometimes install kdm ( which works for me but pulls a lot of other packages in too )

---

### Post by CaptSaltyJack on 2011-10-14
Got it! The correct solution is:

- upon boot, ctrl+alt+F6 (or F5, F4) to get into a terminal
- log in
- "sudo dpkg-reconfigure lightdm"
- choose gdm as your greeter, go back to shell
- "sudo start gdm"

That should log you in.

And then I opened a gnome terminal and did:

- "sudo dpkg install --reinstall lightdm"
- "sudo dpkg reconfigure lightdm"
- choose lightdm as your greeter
- reboot

This seems to have worked for me.

---

### Post by 23dornot23d on 2011-10-14
Nice work - mark it as solved and I will add that in my list so others can see this solution

Thank you :)

---

### Post by thogor on 2011-10-16
> **CaptSaltyJack said:**
> Got it! The correct solution is:

- upon boot, ctrl+alt+F6 (or F5, F4) to get into a terminal
- log in
- "sudo dpkg-reconfigure lightdm"
- choose gdm as your greeter, go back to shell
- "sudo start gdm"

That should log you in.

And then I opened a gnome terminal and did:

- "sudo dpkg install --reinstall lightdm"
- "sudo dpkg reconfigure lightdm"
- choose lightdm as your greeter
- reboot

This seems to have worked for me.

Hi CaptSaltyJack, some questions:
the command "sudo dpkg install --reinstall lightdm" don't wor&#7729; for so I tried "sudo apt-get install --reinstall lightdm", is that ok ?

the command "sudo dpkg reconfigure lightdm" didn’t work either so I tried "sudo dpkg-reconfigure lightdm", is that ok ? becouse I got a response wierd response after choosing the greeter lightdm --> "dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing". please help!

---

### Post by CaptSaltyJack on 2011-10-17
Sorry, I meant sudo dpkg-reconfigure lightdm.

Actually I'm not sure this entirely fixes the problem, as this morning I had booting issues.

---

### Post by atentik on 2011-10-17
Why is this problem marked SOLVED when the person who addressed the issue is still have the same issue?

---

### Post by CaptSaltyJack on 2011-10-17
Don't get your panties in a bunch, kid. I thought I fixed my issue so I marked it as solved, though the problem resurfaced and I forgot to mark it as unsolved.

---

### Post by rsborn on 2011-10-18
I too seem to be having problems with the window manager. Some background:

This is a mythbuntu box that was originally at mythbuntu 8.04 LTS, I walked this through each version (10.04 to 10.10 to 11.04 then finally to 11.10) and each upgrade worked until the 11.10.

It seems that no window manager will load, I used dpkg-reconfigure to set window manager to gdm and still no joy. I can startx into my desktop from a terminal prompt but once in there, sometimes the mythtv front end continually restarts. I don't see anything out of the ordinary in Xorg.0.log but I can post if needed.

I have thought about trying to change to KDM but I just don't want to bring in all of the other baggage.

Here is some info from Lightdm log.

```
[+25.36s] DEBUG: Dropping privileges to uid 111
[+25.36s] DEBUG: Adding session authority to /var/lib/lightdm/.Xauthority
[+25.43s] DEBUG: Restoring privileges
[+25.43s] DEBUG: Launching process 4608: /usr/lib/lightdm/lightdm-greeter-session 'unity-greeter'
[+25.43s] WARNING: Failed to open log file /var/log/lightdm/x-0-greeter.log: Permission denied
[+25.43s] DEBUG: pam_setcred(0x86ba9d0, PAM_ESTABLISH_CRED) -> 0 (Success)
[+25.43s] DEBUG: PAM returns environment 'PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8'
[+25.54s] DEBUG: Read 8 bytes from greeter
[+25.54s] DEBUG: Read 9 bytes from greeter
[+25.54s] DEBUG: Greeter connected version=1.0.1
[+25.54s] DEBUG: Wrote 102 bytes to greeter
[+25.54s] DEBUG: Greeter connected, display is ready
[+25.54s] DEBUG: New display ready, switching to it
[+25.54s] DEBUG: Activating VT 7
[+25.54s] DEBUG: Stopping greeter display being switched from
[+25.54s] DEBUG: Process 4608 exited with return value 0
[+25.54s] DEBUG: pam_close_session(0x86ba9d0) -> 0 (Success)
[+25.54s] DEBUG: pam_setcred(0x86ba9d0, PAM_DELETE_CRED) -> 0 (Success)
[+25.54s] DEBUG: pam_end(0x86ba9d0) -> 0
[+25.54s] DEBUG: Ending ConsoleKit session a914fc4ede865248a0dee7be4b0dafc5-1318989770.657036-567922359
[+25.58s] DEBUG: Greeter quit
[+25.58s] DEBUG: Stopping display
[+25.58s] DEBUG: Sending signal 15 to process 4594
[+25.58s] DEBUG: Dropping privileges to uid 111
[+25.58s] DEBUG: Removing session authority from /var/lib/lightdm/.Xauthority
[+25.65s] DEBUG: Restoring privileges
[+25.66s] DEBUG: Got signal 15 from process 1
[+25.66s] DEBUG: Caught Terminated signal, shutting down
[+25.66s] DEBUG: Stopping display manager
[+25.66s] DEBUG: Stopping seat
[+26.14s] DEBUG: Process 4594 exited with return value 0
[+26.14s] DEBUG: X server stopped
[+26.14s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+26.14s] DEBUG: Releasing VT 7
[+26.14s] DEBUG: Display server stopped
[+26.14s] DEBUG: Display stopped
[+26.14s] DEBUG: Seat stopped
[+26.14s] DEBUG: Display manager stopped
[+26.14s] DEBUG: Stopping Light Display Manager
```

---

### Post by rsborn on 2011-10-18
tried a bunch of suggestions in the stick thread on general upgrade issues to no avail (removing all the nvidia drivers, reinstalling -173, etc).

Just for clarity, I now have a system that will boot but as soon as it switches to VT7 it just stays with either a blank screen or some remnants of the services starting screen (checking battery state, starting myth-backend, etc). If I ctrl-alt fx into anoter terminal, I can run startx and I get my xfce desktop. MythTV was hosed as well but for the time being that is uninstalled (So I guess I technically have Xubuntu now).

Everything else seems to work, I even have full 1080p resolution on my monitor.

Not my daily machine so no hurry to fix but would like to figure this out and not simply reload 11.10 fresh (or 11.04).

thanks,
Rick

---

### Post by gryzilepek on 2011-10-19
I seem to be having the same problem. LightDM fails to start (I set lightDM as the display manager). 

When I first upgraded to 11.10, I would get the login screen. When I typed my username and password, it would accept the password, then take me back to the login screen.

I tried the suggestions on this thread, but nothing seems to work. I did apt-get nvidia-current; after reboot, it wouldn't even give me the login screen. 

I can start gdm and get the message that it is running, but I don't get a desktop. Startx doesn't work, and tells me that nvidia failed to load with message "No drivers available"; the kernel log says that "No NVIDIA graphics adapters found!" Please help, I don't know what I'm doing!

---

### Post by CaptSaltyJack on 2011-10-19
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/804171](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/804171)

---

### Post by vince2k on 2011-10-19
I had similar problems.. The first one that the log file (and it's corresponding directory) lightdm tried to write to wasn't owned by the  right user.. After fixing that, the newly created logfile reported that the unity greeter missed some schema's of the gnome-settings-daemon. After installing this gnome-gnome-settings daemon I at least had a running DM.. Strangely the new greeting needed this.. 
Thus my suggestion is to check the ownership of /var/log/lightdm and the log files in this directory and then check the contents of these logs..

---

### Post by rsborn on 2011-10-19
Hey, thanks for the bug links, looks like a lot of possibilities for fixes and workarounds, I will give those all a try when I get home tonight and report back what fixed the issue.

Rick

---

### Post by rsborn on 2011-10-19
@vince2k, who is the proper owner for these log directories, I am getting closer to fixing it but I opened up these directories a bit too much for my comfort, I'd rather get them back to how they should be. When I started they were owned by root with 644 permissions (root as group as well)

thanks,
Rick

---

### Post by rsborn on 2011-10-19
@vince2k, this fixed it for me, a combination of the permissions and Gnome-settings-daemon. 

Thank you so much

Rick

p.s. still interested in the proper permissions if you have a moment

---

### Post by ozelbaris@gmail.com on 2011-10-20
sudo cp /usr/share/xgreeters/unity-greeter.desktop /usr/share/xgreeters/.desktop
solved my problem.

---

### Post by CaptSaltyJack on 2011-10-20
For me, the error shows up in /var/log/lightdm/x-0.log, and complains about the nvidia kernel not loading. Which is obviously false, because I do have the kernel installed fine.

My personal fix when boot-up hangs at the "checking battery state" is to ctrl-alt into another terminal, log in, and do "sudo apt-get install --reinstall lightdm" and then reboot. Of course, the problem always comes back later quite randomly.

---

### Post by macho on 2011-10-21
I had this same problem; nothing in this thread helped, but [installing lightdm-gtk-greeter did]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/816809"). There's a dependency problem, apparently.

---

### Post by CaptSaltyJack on 2012-01-08
Wow, is this bug STILL in 11.10?? I thought maybe they fixed it (I had a bunch of updates), so I removed my "sleep 2" line from /etc/init/lightdm.conf, and rebooted, and it this bug still rears its ugly head.

---

### Post by marty331 on 2013-03-22
Was having this issue on 12.04, I followed macho's advice and installed [COLOR=#333333][FONT=Ubuntu Mono]lightdm-gtk-greeter.  Problem Solved!  Thanks Macho!![/FONT][/COLOR]

---

### Post by Toz on 2013-03-22
Thread closed.

---

