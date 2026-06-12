---
title: "ubuntu 16.04 LTS black screen with cuser after upgrade"
date: 2016-05-30
forum: Installation &amp; Upgrades
---

### Post by lance bermudez on 2016-05-30
did upgrade now have black screen put lucks password then still black screen then type user password then I have black screen but with white mouse cuser.

I did crtl+alt+f1 to get cli screen to log in then type "startx" then crtl+alt+f7 left mouse click screen then I get a gui. How do I fix this???

ssh into this computer.
user:~$ xrandr
Can't open display

:~$ sudo service lightdm status
[sudo] password for lance: 
&#9679; lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2016-05-30 18:37:02 MDT; 45min ago
     Docs: man:lightdm(1)
  Process: 1170 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exited, status=0/SUCCESS)
 Main PID: 1181 (lightdm)
    Tasks: 6
   Memory: 24.1M
      CPU: 8min 27.150s
   CGroup: /system.slice/lightdm.service
           &#9500;&#9472;1181 /usr/sbin/lightdm
           &#9500;&#9472;1194 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
           &#9492;&#9472;2627 lightdm --session-child 12 19

May 30 18:37:57 bermudezl lightdm[2618]: PAM adding faulty module: pam_kwallet5.so
May 30 18:37:57 bermudezl lightdm[2618]: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lance"
May 30 18:38:09 bermudezl lightdm[2618]: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=lance
May 30 18:38:11 bermudezl lightdm[2627]: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or
May 30 18:38:11 bermudezl lightdm[2627]: PAM adding faulty module: pam_gnome_keyring.so
May 30 18:38:11 bermudezl lightdm[2627]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
May 30 18:38:11 bermudezl lightdm[2627]: PAM adding faulty module: pam_kwallet.so
May 30 18:38:11 bermudezl lightdm[2627]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
May 30 18:38:11 bermudezl lightdm[2627]: PAM adding faulty module: pam_kwallet5.so
May 30 18:38:11 bermudezl lightdm[2627]: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lance"

ssh -X used then
:~$ xrandr 
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.02*+
   1280x720      59.86  
   1152x768      59.78  
   1024x768      59.92  
   800x600       59.86  
   848x480       59.66  
   720x480       59.71  
   640x480       59.38  
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)

---

### Post by lance bermudez on 2016-05-30
I did crtl+alt+f1 to get cli screen to log in then type "startx" then crtl+alt+f7 left mouse click screen then I get a gui. How do I fix this???

---

