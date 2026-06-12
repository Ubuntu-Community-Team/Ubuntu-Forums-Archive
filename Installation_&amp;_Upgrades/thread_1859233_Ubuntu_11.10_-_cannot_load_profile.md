---
title: "Ubuntu 11.10 - cannot load profile"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by Starmaster on 2011-10-13
Hi!

After Ubuntu upgrade from 11.04 to 11.10 cannot load my profile. Login screen appears, then I enter password for my profile, screen blinks to black and then again to login screen. Although I can start guest session with Unity. Also, restart button doesn't work under login screen. With Ctrl+Alt+F1 I can load my profile in terminal.

Any suggestion on this issue?

Thanks in advance!

---

### Post by phiphi on 2011-10-13
Have the same issue. found no further info till now.
I can login with the other profile I have on the same machine. That one I used almost never.

Can you login if you create a new account? sudo adduser ?

---

### Post by phiphi on 2011-10-13
I found out that the problem was the .Xauthority file in the home folder:

> [+967.58s] WARNING: Failed to write authority: Error opening file '/home/phiphi/.Xauthority': Permission denied

It was owned by root. I deleted it and could login again.

---

### Post by phiphi on 2011-10-13
now i found also this bug report:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667)

---

### Post by Starmaster on 2011-10-13
Thanks, this worked for me!

```
ls -Shla | grep "Xauthority"
``` 

showed me 3 files. I deleted .Xauthority. After couple of reboots my profile started to load! :D Thanks!

---

### Post by justinwood on 2011-10-13
Alright, everything said so far mirrors my experience, but how exactly do I go about deleting Xauthority?

---

### Post by Starmaster on 2011-10-14
> **justinwood said:**
> Alright, everything said so far mirrors my experience, but how exactly do I go about deleting Xauthority?

Press Ctrl+Alt+F1 when you're on login screen. Then login under your profile. The default directory will be your home directory. Then simply do:
```
sudo rm .Xauthority
```
```
sudo shutdown -r now
```

Then you should be able to login under your profile.

---

### Post by outofthecave on 2011-10-14
I'm having the same problem. I upgraded Ubuntu 11.04 Natty Narwhal to 11.10 Oneiric Ocelot and now I cannot login to my user account. I can login as root or guest. When I try to login to my account, the screen turns black with white writing on it, which looks like the last screen when Ubuntu is shutting down. Unfortunately, I cannot read the text; it's too fast. Then, the login screen appears again.
There was no .Xauthority file in my home directory, so I copied that of root and changed ownership of it to myself. When I login now it takes ages and I get an error message "Could not update ICEauthority file /home/<username>/.ICEauthority" with only a "logout" button.
I can login to my account from a text terminal (e.g., tty1 at Ctrl+Alt+F1).
Edit: I own .Xauthority and I can chown and chmod it, but I cannot mv or rm it.  How come this?

---

### Post by Ditirambe on 2011-10-14
Hello 

same problem here, I've tried to find the file .Xauthority logging in as admin in CTRL+ALT+F1 but without success.Is it possible I don't have that file?when I had Ubuntu 11.04 I already had problems with this file every time I was logging in, not sure if finally I deleted :(

Thanks in advance for your support

---

### Post by justinwood on 2011-10-14
Thank you so much! My computer is working great now! You guys always follow through, thank you thank you.

---

### Post by outofthecave on 2011-10-14
This problem only occurs if Ubuntu was upgraded to 11.10. It did not occur on my other machine where I installed Ubuntu 11.10 from USB.
I'm backing up my files right now, so I can re-install Ubuntu from USB. I know this is not really a solution, but I just need a running system by Monday.

---

### Post by cajunaggie on 2011-10-14
I get the same error message, but when I log-in via command line, I get:
```
/usr/live/update-notifier/update-motd-fsck-at-reboot: 66: cannot create /var/lib/update-notifier/update-motd-fsck-at-reboot: Read-only file system
run-parts: /etc/update-motd.d/98-fsck-at-reboot exited with return code 2
```
and after the disclaimers, I get:
```
open: no such file or directory
Error locking counter-bash: cannot create temp file for here-document: Read-only file system
```

I used the GUI update manager, so what the heck happened?

---

### Post by The Bright Side on 2011-10-14
Hey guys!

Yeah, this is pretty uncool:

```
rm: cannot remove `.Xauthority': Read-only file system
```

Any takers? I'd appreciate the help.

Thanks!
Peace.

EDIT: fixed. For some reason, my home partition was indeed marked as read-only in fstab. So I finally deleted Xauthority and am back in action, and kicking. Thanks!

---

### Post by longhai on 2011-10-15
On my laptop, I cannot even log in using recovery mode. I have no way to access any of the files under my name. What can I do? From somewhere, it says that using live cd is a solution. I will try it but don't know whether the live cd can access my files.

---

### Post by kchida on 2011-10-15
This may not apply to everyone, but after >24 hours of straight troubleshooting, I finally narrowed it down to my .profile in my home folder.  I happen to have Python Pip installed -- if you don't know what it is, don't worry.  The bottom line is, I had some bash script in my .profile that was not working quite right. For some reason, Ubuntu didn't have much fault tolerance and kicked me right back out during log in when it hit the part of the file that enables code completion for Python programmers.

I still can't explain exactly how this causes a problem, but I've isolated the problem down to this file and I can now reproduce the problem at will.  If I recall correctly, I think this script was causing a problem before in 11.04 -- in the pip portion -- but 11.04 was able to tolerate it.

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# pip bash completion start
_pip_completion()
{
    COMPREPLY=( $( COMP_WORDS="${COMP_WORDS[*]}" \
                   COMP_CWORD=$COMP_CWORD \
                   PIP_AUTO_COMPLETE=1 $1 ) )
}
complete -o default -F _pip_completion pip
# pip bash completion end

export LANGUAGE="en_US:en"
export LC_MESSAGES="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
export LC_COLLATE="en_US.UTF-8"
```

---

### Post by edgardol on 2011-10-15
I'm going through a similar nightmare. Please help !
Deleting .Xauthority didn't work for me.

Here are the details:
Updated my desktop with the update manager from 11.04 to 11.10
During update I chose to keep the login.defs file since I use UIDs with lower numbers than 1000, and accepted to replace the file association file (I forgot the name). I didn't get any other options.
Reboot after update.
No problem login as a guest.
Trying to login as myself takes me back to the login screen.
From a terminal window in the guest account I can get to my account in text mode, and delete the .Xauthority file from my home directory. Side note (although it doesn't seem to matter): my home directory is mounted from my home file server (OpenFiler) using a line in /etc/fstab, but the guest home directory is local.
Logout from guest, try to login as myself, back to login screen.
Login as guest, su to myself and delete .Xauthority again, reboot.
Try to login as myself, and this time I get a terminal window with suggestions about running commands as administrator.
I look and confirm that there is a .Xauthority file in my home directory.
A previous poster said that his problem was solved after a couple of reboots, so, that is what I tried next:
Exit the terminal and reboot, try to login as me, back to login screen.
Reboot once more, try to login, get a terminal, reboot yet another time, try to login, get a terminal, exit the terminal and get to the login screen, try to login, back to the login screen (not even a terminal this time).
Go to ubuntuforums and start typing this message...

---

### Post by juanortiz on 2011-10-15
Same problem after upgrade. In my home folder I saw (ls -al) that .Xauthority was owned by root. I removed it (sudo rm ~/.Xauthority) and I was able to logon

---

### Post by horace on 2011-10-15
> **edgardol said:**
> 
Deleting .Xauthority didn't work for me.


Same here - I deleted .Xauthority, and now when I try to log in I get a small terminal in the corner of the screen, but that's it. I can create new user accounts which work fine, but my original account from which I upgraded is still non-doing.

What else might be the problem?

---

### Post by horace on 2011-10-15
> **horace said:**
> 
What else might be the problem?

In case it helps anybody in the same position, following the instructions in #2 of [the thread linked here]("http://ubuntuforums.org/showthread.php?t=1860780") finally fixed it for me.

---

### Post by prupert on 2011-10-15
Anyone have shutdown issues after fixing this big (as in the computer doesn't shutdown and just gets stuck on the final four dots scree)?

I had this bug, rebooting a few times fixed it (I didn't remove the Xuthority file) and now I can never shutdown....

---

### Post by phantomn on 2011-10-16
I'm having this problem too,after altering the libimobiledevice packages. Just stuck on the login screen. I've tried deleting/altering the xauthority file and the lightdm, neither has worked for me. Also none on my software sources seem to be able to download anything all are failing to fetch files. Any ideas appreciated.
P

---

### Post by flitbee on 2011-10-27
> **Starmaster said:**
> Press Ctrl+Alt+F1 when you're on login screen. Then login under your profile. The default directory will be your home directory. Then simply do:
```
sudo rm .Xauthority
``````
sudo shutdown -r now
```Then you should be able to login under your profile.

I don't understand. The whole reason this thread was started was because we're unable to login to my normal user. How then can I  "Then login under your profile." If I could do that I wouldn't be typing this post.. Or am i missing something obvious? I'm logged in as guest and if i try to access my usual users home dir (/home/myusername) I am denied permission. What is it I'm missing?

---

### Post by horace on 2011-10-28
> **flitbee said:**
> I don't understand. The whole reason this thread was started was because we're unable to login to my normal user. How then can I  "Then login under your profile." If I could do that I wouldn't be typing this post.. Or am i missing something obvious? I'm logged in as guest and if i try to access my usual users home dir (/home/myusername) I am denied permission. What is it I'm missing?

You need to log in on tty1 - do Alt/Ctrl/F1 and you should get a login prompt; no graphical interface, but you will be able to delete the file and try again.

---

### Post by flitbee on 2011-10-28
> **horace said:**
> You need to log in on tty1 - do Alt/Ctrl/F1 and you should get a login prompt; no graphical interface, but you will be able to delete the file and try again.

 Thanks, i did do this but I see no .Xauthority file in my home dir (Yes i did ls -a). Is that where I should be looking?  /home/username/  I see no .Xauthority file, am able to login via tty1 with the user that is unable to login via the GUI and experience the exact same issue mentioned in this thread.  Am I missing something?

---

### Post by horace on 2011-10-29
> **flitbee said:**
> Thanks, i did do this but I see no .Xauthority file in my home dir (Yes i did ls -a). Is that where I should be looking?  /home/username/  I see no .Xauthority file, am able to login via tty1 with the user that is unable to login via the GUI and experience the exact same issue mentioned in this thread.  Am I missing something?

That's where the file would be. Not sure what else might help, though for me the instructions in [http://ubuntuforums.org/showthread.php?t=1860780]("http://ubuntuforums.org/showthread.php?t=1860780") (post #2) did the trick.
hth,

---

### Post by Oscar.dR on 2011-11-30
Thanks very much, deleting .Xauthority worked like a charm!

For those of you not finding .Xauthority: It might be the case you changed your password from the console instead of doing it from the GUI, or something else screwed up. Anyway, when that happens it is possible that your personal data hasn't been mounted because the login screen couldn't use your old password to do so.

The procedure here is to execute from tty1 (Ctrl+Alt+F1 at login screen will show up the console):

```
ecryptfs-mount-private
```

then, to mount your data you will need your OLD password. After doing so, you will find .Xauthority in your home folder. Delete it!

```
cd ~
ls .Xauthority
rm .Xauthority
```

Now hit Alt+F7 to return to your login screen. Login with your new password and welcome to your desktop again.

Hope this helps! :D

---

### Post by flitbee on 2011-12-01
> **Oscar.dR said:**
> Thanks very much, deleting .Xauthority worked like a charm!

For those of you not finding .Xauthority: It might be the case you changed your password from the console instead of doing it from the GUI, or something else screwed up. Anyway, when that happens it is possible that your personal data hasn't been mounted because the login screen couldn't use your old password to do so.

The procedure here is to execute from tty1 (Ctrl+Alt+F1 at login screen will show up the console):

```
ecryptfs-mount-private
```then, to mount your data you will need your OLD password. After doing so, you will find .Xauthority in your home folder. Delete it!

```
cd ~
ls .Xauthority
rm .Xauthority
```Now hit Alt+F7 to return to your login screen. Login with your new password and welcome to your desktop again.

Hope this helps! :D

Thank u for that alternative, but when I tried that, this is what I got:

[IMG]http://img440.imageshack.us/img440/2150/photofg.jpg[/IMG]

:( It's been 2 months since I've been stuck with a non-working Ubuntu!

---

### Post by pier433 on 2011-12-02
I have the same problem. During installation of Ubuntu 11.10 i changed my password. So i mount my old home with my old password over console. But when i do rm .Xauthority there is still no .Xauthority that can be removed. Any suggestions? Thank you if you can help me.:popcorn:

---

### Post by pier433 on 2011-12-02
I solve it!

All the things with this kind of console manipulation didn't worked for me.

At the end i logged in as a guest into ubuntu desktop (unity, there where you start firefox and so on).

Then i opend the document browser/ home (called nautilus, there where you see the home directory with all the personal staff of guest).

I went into options of the browser where you can activate the possibility to see hidden documents and files.

Then i saw  a .Xauthority file and a .xession-errors file

I deleted both.

Then i was able to login into ubuntu with my old user that i used before when i upgraded to 11.10

This problem cost me 1 day. Thanks.

:guitar:

---

### Post by OstensiblyFeet on 2012-01-28
I'm having a remarkably similar problem to this, although not for the same reason.

I'm running Xubuntu, and I changed the password setting on my Users Settings to "not asked on login". After this, I had the same problem people describe: click on user account at the login screen, some text ran (too fast for me to read it) and then took me back to the login screen.

Ctrl-Alt-F1 and logged in via the terminal screen, and went back to the login screen by Alt-F7. This then allows me to login.

Afterwards however, I find I can't shut down or reboot the computer from inside Xubuntu (options are greyed out). I also cannot shut down from the login screen.

I also have to do the same steps every time I reboot manually.

Anyone got any idea what might be causing this?

---

### Post by swissinvestor on 2012-01-29
The same problem here. None of the solutions mentioned above worked for me. I cannot log in again.

I also deleted .ICEauthority as recommended somewhere. But this did not help either. I always end up at the login screen.

---

### Post by the|Gamer on 2012-05-05
I had the Same error on Ubuntu 12.04 and solved it with "sudo chmod -R username:group /tmp"

---

### Post by outtadecage on 2012-08-16
I had a similar problem after changing UMASK setting in /etc/login.defs I logged in via tty as above and changed UMASK back to 0022 and the problem disappeared. I don't know if this is related, but I'm linux new so yeah maybe someone who understands it better can tell us.

---

