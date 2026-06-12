---
title: "Upgrade to 16.04 LTS. Desktop won't load. Login throws me back to the login template."
date: 2017-09-04
forum: Installation &amp; Upgrades
---

### Post by ffrr on 2017-09-04
Hi all,

I upgraded a Dell Latitude E6530 from 12.15 LTS to 16.04 LTS from an ISO DVD. Installation completed. Desktop won't launch. Instead the login template pops up again after five seconds. So I opened an X-terminal (Ctl-Alt-F3), logged in and did an "apt-get update" and an "apt-get upgrade". The upgrade seemed to do a thorough job for a couple of minutes. Next, an attempt to open Firefox failed with the message "Error: GDK_BACKEND does not match available displays". The DVD apparently didn't make available required displays. Some manual package management seems to be necessary. I have no clue where to start and would greatly appreciate expert advice.

Thanks

Frederic

---

### Post by ubfan1 on 2017-09-04
Can you successfully login to the guest session?  If so, the problem is probably in the "hidden" files (those starting with a dot) in your home directory which are mainly configurations (old).  Try making a temporary directory in your home, mkdir tmpdir,  and move all the dot file .cache there so it wont be seen by login and see if that works.  The .cache directory is likely the cause of the problem, but maybe .Xauthority or .config   You can move any files back out of the tmpdir if you need them, like for mail or bookmarks, but they'll be recreated like in a guest session as needed.

---

### Post by ffrr on 2017-09-04
Ubfan1, thanks for your suggestions. No luck, so far. As Guest I have no access to other users' accounts. As registered user I can move .cache out of the way, But that has no immediate effect and when I restart, it is back where it was before I moved it. I have no effective root! I found a file named xsession-errors, which doesn't look too good. I have no way of copying the file to the machine I am using for this correspondence. So, I'll have to type it. There's a lot of killing:

Can't save user-dirs.dirs
OpenConnection: connect: No such file or directory
cannot connect to britty at :0
upstart:/home/fr/.config/upstart: Unable to load configuration: Permission denied
upstart: session-migration main process (2283) terminated with status 1
upstart: gnome-session main process (2287) terminated with status 1
upstart: unity-settings-daemon main process (2280) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: logrotate main process (2262) killed by TERM signal
upstart: bamfdaemon main process (2134) killed by TERM signal
upstart: hud main process (2278) killed by TERM signal
upstart: indicator-bluetooth main process (2318) killed by TERM signal
upstart: indicator-power main process (2326) killed by TERM signal
upstart: indicator-datetime main process (2327) killed by TERM signal
upstart: indicator-printers main process (2331) killed by TERM signal
upstart: indicator-session main process (2332) killed by TERM signal
upstart: indicator-application main process (2351) killed by TERM signal
upstart: unity-panel-service main process (2292) killed by TERM signal
upstart: unity7 main process (2385) killed by TERM signal

.config/upstart is indeed missing.  

apt-get seems to be working. I could start installing and uninstalling stuff, if I just knew what the offending item is. I am confused about the desktop managers. I understand that gnome has been replaced with GDK (?). I have been using gnome and have had annoying freezes which I attributed to gnome. They occurred seldom enough to not seriously impede work. After a complete reinstallation (apt-get install gnome), things seemed fine for a week or two, but the other day the freezes (of terminal windows) started to get so bad that the machine was no longer usable, So I figured the upgrade was the best solution to fix thing from the bottom up.

Frederic

---

### Post by ubfan1 on 2017-09-04
You would make those changes when logged into the ctrl-alt-F3 terminal as yourself.  Then try the gui login (ctrl alt F7).

---

### Post by ffrr on 2017-09-05
You are right. I can issue bash commands, opening a terminal with ctl-alt-F3. So I found out that there was no "gnome". I then apt-get installed it. (it's humongous. Took about ten minutes.) "unity" and "compiz" were ok. Starting up this morning I had a nicer login template, but its behavior hadn't improved. It still threw me back to the same template, over and over, and so I still cannot log in. It doesn't say user name or password are wrong. They aren't. They work in the terminal.

I discovered "dpkg -V" (Verifies the integrity of all packages.) It lists eleven files, nine of which don't seem relevant. (??5?????? /usr/lib/python3/dist-packages/__pycache__/(filename).pyc"). The two other ones also start with the question mark thing, followed, respectively, by: "/boot/vmlinuz-4.10.0-28-generic" and "/usr/share/gnome-mahjongg/themes/postmodern.svg". The "man dpkg" page says what that the function does  (compare information, installed vs. database), but doesn't say what its output means. Is it a list of all installed packages or a subset of either consistent or inconsistent ones? 

I discovered dselect. I didn't have it. So I installed it. The man page looks like it might get me somewhere. But it's bound to take me a few hours.

By the way, I remember holding some key (F-?) while firing up, and that would start a recovery mode or a safe mode, a minimal configuration with internet and USB access. F-2 and F-12 both start something, but it's nothing like a working environment. I would do another complete upgrade, but online rather than from this miserable DVD. For this I need to restore internet access.

---

### Post by ffrr on 2017-09-05
To get on with it, I had no alternative but to do a radical upgrade, pretending to trust my backups blindly. The upgrade was successful. I shall spend the rest of this week reconstructing my working environment and at least another week rewriting a job I had just completed and is now missing in the backup, but that's another story . . . What matters is that I thank the helpers for their support and that I can close the thread.

Frederic

(There is supposed to be a button for marking the thread "closed". I cannot find such a button.)

---

### Post by ubfan1 on 2017-09-05
I think the "close" is under the "thread tools" at the top of the thread.

---

### Post by wildmanne39 on 2017-09-05
You can not close a thread, only moderators can, but you can mark it solved in thread tools at the top of the page.

---

