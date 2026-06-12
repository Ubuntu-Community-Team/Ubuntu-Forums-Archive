---
title: "Unable to login..."
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by singh.mukul on 2011-10-16
Hi,

I upgraded to 11.10 from 11.04 and now I am unable to login. On trying to login with my credentials, I am brought back to the login screen once again. The guest account works fine. Also, I can login from the terminal mode.

Can anyone point out how to fix this issue?

Regards

---

### Post by hansdown on 2011-10-16
Hi, singh.mukul.

Sorry, if this doesn't apply to your situation.

The login screen in 11.10 no longer requires, that you hit enter, before you enter your password.

---

### Post by singh.mukul on 2011-10-16
Thanks. I am hitting enter only after typing the password. Username is selectable using mouse.

---

### Post by Toz on 2011-10-16
Try deleting the .Xauthority file in your home directory. The caveat is you will need to do this as root, so Ctrl+Alt+F1 to go to the first vt, login is as yourself at the text prompt, then:
```
sudo rm .Xauthority
```

Then go back to the gui screen (Ctrl+Alt+F7) and try logging in again.

---

### Post by singh.mukul on 2011-10-16
Tried that. Still the same, can't login.

---

### Post by youngunix on 2011-10-16
> **singh.mukul said:**
> Hi,

I upgraded to 11.10 from 11.04 and now I am unable to login. On trying to login with my credentials, I am brought back to the login screen once again. The guest account works fine. Also, I can login from the terminal mode.

Can anyone point out how to fix this issue?

Regards


If you can log in using the Terminal, try this (while in terminal mode):

1. sudo apt-get update

2. sudo apt-get upgrade

3. sudo apt-get autoremove
    sudo apt-get autoclean

4. sudo apt-get update

5. startx

---

### Post by singh.mukul on 2011-10-17
This has also not helped resolve the issue. Also, I have noticed that there is no sound.

---

### Post by Toz on 2011-10-17
Are there any error messages in your ~/.xsession-errors file that might identify why you are being dumped back out to the login screen?

---

### Post by cives on 2011-10-17
> **Toz said:**
> Are there any error messages in your ~/.xsession-errors file that might identify why you are being dumped back out to the login screen?

Hello, I have exactly the same problem. Also can login as Guest but not with my user. I have tried all that suggested before, I have deleted the ~/.Xauthority file and chown-ed by my user all the files in my user home..., with no result. 
I have just noticed that when I am stuck at the login page and go to a terminal (Ctrl+Alt+F1) and type my user login and password, it always allows me in but previously it warns me:
"-bash: /home/user/.profile: Permission denied".
I try to apply chown or chmod 650 to that file, but still. I logout with exit, and warns me now:
"-bash: /home/user/.bash_logout: Permission denied", but anyhow it allows me out.
If again I login, the .profile Permission denied warning once again. 
By the way, when I reboot, I find that the situation is again the same as in the beginning (even there is a new .Xauthority file created there)...
Any clue?
I have to say that I am making a fresh install but my home partition is separated and was having some problems with the .ICEauthority or something similar.
I have searched but nothing of what I found till today wad useful. I would appreciate your help. Thank you.

---

### Post by cives on 2011-10-17
> **cives said:**
> Hello, I have exactly the same problem. Also can login as Guest but not with my user. I have tried all that suggested before, I have deleted the ~/.Xauthority file and chown-ed by my user all the files in my user home..., with no result. 
I have just noticed that when I am stuck at the login page and go to a terminal (Ctrl+Alt+F1) and type my user login and password, it always allows me in but previously it warns me:
"-bash: /home/user/.profile: Permission denied".
I try to apply chown or chmod 650 to that file, but still. I logout with exit, and warns me now:
"-bash: /home/user/.bash_logout: Permission denied", but anyhow it allows me out.
If again I login, the .profile Permission denied warning once again. 
By the way, when I reboot, I find that the situation is again the same as in the beginning (even there is a new .Xauthority file created there)...
Any clue?
I have to say that I am making a fresh install but my home partition is separated and was having some problems with the .ICEauthority or something similar.
I have searched but nothing of what I found till today wad useful. I would appreciate your help. Thank you.

I forgot  to mention something, which I ignore if can be important.
I have tried with no success to "sudo dpkg-reconfigure lightdm", and it shows the message:
"dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing".
I haven't found anywhere what this means and/or how to solve it, if necessary.

---

### Post by effenberg0x0 on 2011-10-17
```
sudo chown $USER:$USER /home/$USER -R

sudo apt-get update && sudo apt-get install --reinstall dpkg

sudo apt-get install --reinstall lightdm unity-greeter

if [ ! -f /etc/X11/default-display-manager ]; then sudo touch /etc/X11/default-display-manager
echo -e "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager

if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf

sudo service lightdm stop

sudo service lightdm start
```

---

### Post by effenberg0x0 on 2011-10-17
Instead of installing from scratch, you could simply create a new user. The new user will have a new home, with all the default files and permissions.

sudo adduser **yournewusername**
sudo usermod -aG adm dialout cdrom plugdev lpadmin admin sambashare **yournewusername**

Copy your files (but not configuration files) from old home to new home (/home/yournewusername)

reboot, login with new user, try lightdm

Regards
Effenberg

---

### Post by cives on 2011-10-18
> **effenberg0x0 said:**
> ```
sudo chown $USER:$USER /home/$USER -R

sudo apt-get update && sudo apt-get install --reinstall dpkg

sudo apt-get install --reinstall lightdm unity-greeter

if [ ! -f /etc/X11/default-display-manager ]; then sudo touch /etc/X11/default-display-manager
echo -e "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager

if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf

sudo service lightdm stop
sudo service lightdm start
```

This solved it! Thank you very much, Effenberg0x0
When I wrote the "if" instructions, it showed just ">" and a blinking cursor, and I had to close with Ctrl+C, but at the end of all your instructions, it worked and started my session. Just in case, I rebooted and it still works. Thank you again.

---

