---
title: "Upgrading to Trusty."
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by raccoonstrait on 2014-04-18
Upgrade seemed to progress normally (this is not my first) until the reboot. Login screen comes up, but after login all I get is a background image. AltF2 and I get a console. After some futzing I found that if I remove both lightdm processes and then startxfce4 I get my desktop. Rebooting requires the same procedure to get back to a desktop.

I have used Synaptic to check for broken packages and have reinstalled almost everything that is related to XFCE and xubuntu-desktop, as well as lightdm. No joy yet.

The desktop does run, I am using it now, but the system will not boot into the desktop

The machine is an IBM Thinkpad r50e, and has been running Ubuntu for about 10 years, originally as a dual boot system (actually tri boot, as at one time I have XP and Ubunto on the hard drive and Kubuntu on an external drive, all at the same time). There is only 756 meg of ram and a celeron CPU.

Looking for answers.:(

---

### Post by bapoumba on 2014-04-18
Moved to its own thread (the thread you posted to is not aimed at support but only experiences).

---

### Post by 23dornot23d on 2014-04-18
I used xdm to get a light but functioning login when that happened to me ........

> 
The desktop does run, I am using it now, but the system will not boot into the desktop



But you can use kdm too but it brings in lots of other things ...... so is maybe not what you need * ( my own preferred login )

Lightdm should work but try a re-install after using one of the others ........ seems it needs a lot more
things in place to function correctly ........ but there are options for a cleaner login - maybe there should be
a documented list of things that Lightdm needs to work properly ..... plymouth tends to be one thing where things
either hang or stop sometimes ........ ( maybe look to see if there is any error in the logs )

 - do you have to do ctrl + alt + f1 then stop lighdm ........ and then something else ....... maybe startx or run another
desktop manager ...... ?

---

### Post by raccoonstrait on 2014-04-18
yes, in tty2 or whatever I have to stop two lightdm instances and then startxfce4. I have some more information at

[http://askubuntu.com/questions/449370/trusty-tahr-14-04-upgrade-restart-no-xfce-desktop-fatal-io-error-11](http://askubuntu.com/questions/449370/trusty-tahr-14-04-upgrade-restart-no-xfce-desktop-fatal-io-error-11)

here is the output from lightdm.log

[+0.05s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.05s] DEBUG: Starting Light Display Manager 1.10.0, UID=0 PID=1110
[+0.05s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/40-kde-plasma.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/40-lightdm-kde-greeter.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-gnome.conf
[+0.05s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.05s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.05s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.05s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-xubuntu.conf
[+0.05s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.05s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.05s] DEBUG: Registered seat module xlocal
[+0.05s] DEBUG: Registered seat module xremote
[+0.05s] DEBUG: Registered seat module unity
[+0.05s] DEBUG: Registered seat module surfaceflinger
[+0.06s] DEBUG: Adding default seat
[+0.06s] DEBUG: Seat: Starting
[+0.06s] DEBUG: Seat: Creating greeter session
[+0.32s] DEBUG: Seat: Creating display server of type x
[+0.33s] DEBUG: Deactivating Plymouth
[+0.36s] DEBUG: Using VT 7
[+0.36s] DEBUG: Seat: Starting local X display on VT 7
[+0.36s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.36s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.36s] DEBUG: DisplayServer x-0: Launching X Server
[+0.36s] DEBUG: Launching process 1148: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.37s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.37s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.37s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.19s] DEBUG: Loading users from org.freedesktop.Accounts
[+2.19s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+6.00s] DEBUG: Got signal 10 from process 1148
[+6.00s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+6.00s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+6.01s] DEBUG: Quitting Plymouth; retaining splash
[+6.08s] DEBUG: Seat: Display server ready, starting session authentication
[+6.08s] DEBUG: Session pid=1207: Started with service 'lightdm-greeter', username 'lightdm'
[+6.84s] DEBUG: Session pid=1207: Authentication complete with return value 0: Success
[+6.84s] DEBUG: Seat: Session authenticated, running command
[+6.84s] DEBUG: Session pid=1207: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+6.92s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+6.92s] DEBUG: Session pid=1207: Logging to /var/log/lightdm/x-0-greeter.log
[+7.36s] DEBUG: Activating VT 7
[+7.36s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1
[+17.61s] DEBUG: Session pid=1207: Greeter connected version=1.10.0
[+25.74s] DEBUG: Session pid=1207: Greeter start authentication for raccoonstrait
[+25.74s] DEBUG: Session pid=1961: Started with service 'lightdm', username 'raccoonstrait'
[+26.10s] DEBUG: Session pid=1961: Got 1 message(s) from PAM
[+26.10s] DEBUG: Session pid=1207: Prompt greeter with 1 message(s)
[+53.45s] DEBUG: Session pid=1207: Continue authentication
[+53.91s] DEBUG: Session pid=1961: Authentication complete with return value 0: Success
[+53.91s] DEBUG: Session pid=1207: Authenticate result for user raccoonstrait: Success
[+53.91s] DEBUG: Session pid=1207: User raccoonstrait authorized
[+53.93s] DEBUG: Session pid=1207: Greeter sets language en_US
[+54.00s] DEBUG: Session pid=1207: Greeter requests session ubuntu
[+54.16s] DEBUG: Writing /home/raccoonstrait/.dmrc
[+54.38s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+54.38s] DEBUG: Session pid=1207: Sending SIGTERM
[+54.38s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+54.55s] DEBUG: Session pid=1207: Exited with return value 0
[+54.55s] DEBUG: Seat: Session stopped
[+54.55s] DEBUG: Seat: Greeter stopped, running session
[+54.55s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+54.63s] DEBUG: Session pid=1961: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+54.63s] DEBUG: Creating shared data directory /var/lib/lightdm-data/raccoonstrait
[+54.63s] DEBUG: Session pid=1961: Logging to .xsession-errors
[+55.68s] DEBUG: Activating VT 7
[+55.68s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c2
[+55.68s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+57.34s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+121.41s] DEBUG: User /org/freedesktop/Accounts/User1000 changed

[this is the point the log file gets to when I start killing the PID's for lightdm]

[+417.18s] DEBUG: Got signal 15 from process 2748
[+417.18s] DEBUG: Caught Terminated signal, shutting down
[+417.18s] DEBUG: Stopping display manager
[+417.18s] DEBUG: Seat: Stopping
[+417.18s] DEBUG: Seat: Stopping display server
[+417.18s] DEBUG: Sending signal 15 to process 1148
[+417.18s] DEBUG: Seat: Stopping session
[+417.18s] DEBUG: Session pid=1961: Sending SIGTERM
[+417.25s] DEBUG: Process 1148 exited with return value 0
[+417.25s] DEBUG: DisplayServer x-0: X server stopped
[+417.25s] DEBUG: Releasing VT 7
[+417.25s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+417.25s] DEBUG: Seat: Display server stopped
[+418.23s] DEBUG: Session pid=1961: Exited with return value 0
[+418.23s] DEBUG: Seat: Session stopped
[+418.23s] DEBUG: Seat: Stopped
[+418.23s] DEBUG: Display manager stopped
[+418.23s] DEBUG: Stopping daemon
[+418.24s] DEBUG: Exiting with return value 0

The system starts XFCE though slowly.

---

### Post by raccoonstrait on 2014-04-18
I appreciate the action. I am curious though, this wasn't an exprience? ;)

---

### Post by bapoumba on 2014-04-18
> **raccoonstrait said:**
> I appreciate the action. I am curious though, this wasn't an exprience? ;)

Most probably :)
But the thread was not intended for support:
> **cariboo907 said:**
> ...
Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.
...

---

### Post by monkeybrain20122 on 2014-04-18
Back up your data and do a fresh install. There is no point trouble shooting a badly blotched upgrade as you would have to end up reinstalling a lot of broken packages any way and it may not fix all your problems. Well, unless you want the 'experience'.

---

### Post by raccoonstrait on 2014-04-18
Thanks monkeybrain. I was so hoping not to have to do that this time. I have separate partitions for / and /home and /var and /tmp and will preserve the /home. Nothing critical is there, so if I loose it, no big deal. I have never had much success with dpkg --get-selections. The 'get' part works, but later the 'set' part always fails to install everything, or even most things. 

One day distrobution updates will get better, maybe even for old hardware. We might even get to the day where linux does not insist upon installing bluetooth on a machine where bluetooth hardware does not exist.

Thanks again for your analysis.

---

### Post by 23dornot23d on 2014-04-18
**sudo apt-get install xdm**

..... this worked for me ........ as it gave me a login that would work.

But if its not running properly - as said a clean install may be better as at least that way you are running
for a good base install scenario ........ instead of guessing if one configuration file or another might be 
causing problems ..........

Could try adding a new user see if that will go through the login procedure ok using lightdm ........

something like ........ ( see if it shows the same problems of just a background screen )

**sudo adduser testing**

---

### Post by raccoonstrait on 2014-04-18
Thanks for the though. I did reinstall, started with Xubuntu this time, and it seems to  be working, though an issue in synaptic has carried over, see:

[http://ubuntuforums.org/showthread.php?t=2217932](http://ubuntuforums.org/showthread.php?t=2217932)

The new user is something I would never have thought of. It is in the pipeline now. Thanks.

---

### Post by Nick3193 on 2014-04-29
I'm having this same issue, and I was really hoping I wouldn't have to completely rebuild the system. It's cr*p like this that is the reason Linux isn't getting any traction as a desktop environment to replace Windows. I've been running Ubuntu for 7 years now and have used Linux for over 10 years so I'm not unused to having something not work after an upgrade, but a non technical user just isn't going to handle having a non-functioning GUI like this.

---

### Post by monkeybrain20122 on 2014-04-29
> **Nick3193 said:**
> I'm having this same issue, and I was really hoping I wouldn't have to completely rebuild the system. It's cr*p like this that is the reason Linux isn't getting any traction as a desktop environment to replace Windows. I've been running Ubuntu for 7 years now and have used Linux for over 10 years so I'm not unused to having something not work after an upgrade, but a non technical user just isn't going to handle having a non-functioning GUI like this.

That's why "upgrade" is a bad idea, it is intrinsically a complex and fragile process, always do clean install. How does a non technical Windows user "upgrade"? Buy a new machine.

---

