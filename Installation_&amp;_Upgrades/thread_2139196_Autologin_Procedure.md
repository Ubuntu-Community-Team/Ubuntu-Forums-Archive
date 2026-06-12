---
title: "Autologin Procedure"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by exarchate on 2013-04-26
Hello,

I am in the process of setting up a VirtualBox using Ubuntu Server 12.04.2 32-bit using LXDE. The box is on a password-protected host and does not need its own password-protected login.

There seem to be countless procedures and answers for this question across various forums, but none seem to work for me.

To ensure that there is no confusion let me note the following:

(1) The box is first created and Ubuntu Server 12.04.2 32-bit is installed. I then install LXDE as root using the command: "apt-get install lxde". I have not yet made any other alterations to the box (I keep a snapshot at this point so that I can easily revert failed attempts.)

(2) I am not installing lubuntu (which would be installed using the command: "apt-get install lubuntu-core lubuntu-icon-theme lubuntu-restricted-extras"). I tried a lubuntu box, which is similar, but since I was unable to get that to work after about an hour, I decided to focus back on the default LXDE with lxdm. Should also note that I have tried the lubuntu-specific instructions in LXDE with lxdm and they had no effect. I don't even think the config file was ever read by the system at boot up.

(3) I am not using lightdm. I tried a lightdm box and it isn't what I want.

(4) There is no directory /etc/xdg/lxdm/ and no file /etc/xdg/lxdm/lxdm.conf (this would apply to a different setup anyway.)

(5) I have confirmed that the display manager is lxdm by using the following command: "cat /etc/X11/default-display-manager"

(6) Uncommenting #autologin=USERNAME (and obviously changing the USERNAME) in /etc/lxdm/lxdm.conf (which is linked to /etc/lxdm/default.conf and is confirmed to be updated) renders the box unusable. I've seen many people say that this is all you need to do, but it is not. I can provide screenshots to verify that I have done this precisely and that there are no typos. Furthermore, I have done this immediately after the "apt-get install lxde" command, so there is no chance of anything interfering. This is a clean and completely standard installation on a standard Linux 32-bit VirtualBox.

(7) I have found some discussion that the password needs to be deleted with "passwd -d USERNAME" and files located in /etc/pam.d/ need to be edited. However I have not been able to figure out how these files would need to be altered. My attempts so far have failed. I've only been able to find lxdm-related documentation for PAM files for Archlinux and Red Hat.

Here are the current (unaltered by me) contents of /etc/pam.d/lxdm:[INDENT]%PAM-1.0[/INDENT]
[INDENT]auth    requisite       pam_nologin.so[/INDENT]
[INDENT]auth    required        pam_env.so readenv=1[/INDENT]
[INDENT]auth    required        pam_env.so readenv=1 envfile=/etc/default/locale[/INDENT]
[INDENT]auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin[/INDENT]
[INDENT]@include common-auth[/INDENT]
[INDENT]auth    optional        pam_gnome_keyring.so[/INDENT]
[INDENT]@include common-account[/INDENT]
[INDENT]session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinu$[/INDENT]
[INDENT]session required        pam_limits.so[/INDENT]
[INDENT]@include common-session-noninteractive[/INDENT]
[INDENT]session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinu$[/INDENT]
[INDENT]session optional        pam_gnome_keyring.so auto_start[/INDENT]
[INDENT]@include common-password[/INDENT]

Here are the current (unaltered be me) contents of /etc/pam.d/common-auth:[INDENT]# /etc/pam.d/common-auth - authentication settings common to all services[/INDENT]
[INDENT]#[/INDENT]
[INDENT]# This file is included from other service-specific PAM config files,[/INDENT]
[INDENT]# and should contain a list of the authentication modules that define[/INDENT]
[INDENT]# the central authentication scheme for use on the system[/INDENT]
[INDENT]# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the[/INDENT]
[INDENT]# traditional Unix authentication mechanisms.[/INDENT]
[INDENT]#[/INDENT]
[INDENT]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.[/INDENT]
[INDENT]# To take advantage of this, it is recommended that you configure any[/INDENT]
[INDENT]# local modules either before or after the default block, and use[/INDENT]
[INDENT]# pam-auth-update to manage selection of other modules.  See[/INDENT]
[INDENT]# pam-auth-update(8) for details.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]# here are the per-package modules (the "Primary" block)[/INDENT]
[INDENT]auth    [success=1 default=ignore]      pam_unix.so nullok_secure[/INDENT]
[INDENT]# here's the fallback if no module succeeds[/INDENT]
[INDENT]auth    requisite                       pam_deny.so[/INDENT]
[INDENT]# prime the stack with a positive return value if there isn't one already;[/INDENT]
[INDENT]# this avoids us returning an error just because nothing sets a success code[/INDENT]
[INDENT]# since the modules above will each just jump around[/INDENT]
[INDENT]auth    required                        pam_permit.so[/INDENT]
[INDENT]# and here are more per-package modules (the "Additional" block)[/INDENT]
[INDENT]auth    optional        pam_ecryptfs.so unwrap[/INDENT]
[INDENT]auth    optional                        pam_cap.so[/INDENT]
[INDENT]# end of pam-auth-update config[/INDENT]




If someone could help me figure this out, I would be very grateful. I have already spent the better part of a day pouring through forums (including this one) and reading documentation and running every search I can conceive of.

While I've learned quite a bit about the internal workings of Ubuntu and LXDE, and it's all been fascinating... I still can't manage to enable a basic feature which I know can be done because I've seen it done on my precise setup.

(In fact I've had this exact setup with autologin enabled running on my computer for a long time, except that it used Ubuntu Server 12.04.2 64-bit. However I need to be able to port this box to a computer that can only run a 32-bit box.)

Feel free to ask any questions that you may need to help me figure this out. I can provide screen caps and provide any necessary information.

Thank you very much!

Matt

tl;dr: This is NOT lubuntu or lightdm. I need a procedure that works for standard LXDE with lxdm as display manager. Just uncommenting the autologin line and putting my username in /etc/lxdm/lxdm.conf does not work or is insufficient. Overall setup is completely standard and clean up to this point.

---

### Post by exarchate on 2013-04-26
A little bit of additional information...

The username is ustinov. The machine name is Ustinov.

Here are the contents of /etc/lxdm/lxdm.conf (which match /etc/lxdm/default.conf) as altered by me:[INDENT][base][/INDENT]
[INDENT]## uncomment and set autologin username to enable autologin[/INDENT]
[INDENT]autologin=ustinov[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## uncomment and set timeout to enable timeout autologin,[/INDENT]
[INDENT]## the value should >=5[/INDENT]
[INDENT]# timeout=10[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## default session or desktop used when no systemwide config[/INDENT]
[INDENT]# session=/usr/bin/startlxde[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## uncomment and set to set numlock on your keyboard[/INDENT]
[INDENT]# numlock=0[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## set this if you don't want to put xauth file at ~/.Xauthority[/INDENT]
[INDENT]# xauth_path=/tmp[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## greeter used to welcome the user[/INDENT]
[INDENT]greeter=/usr/lib/lxdm/lxdm-greeter-gtk[/INDENT]
[INDENT]
[/INDENT]
[INDENT][server][/INDENT]
[INDENT]## arg used to start xserver, not fully function[/INDENT]
[INDENT]# arg=/usr/bin/X -background vt1[/INDENT]
[INDENT]
[/INDENT]
[INDENT][display][/INDENT]
[INDENT]## gtk theme used by greeter[/INDENT]
[INDENT]gtk_theme=Clearlooks[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## background of the greeter[/INDENT]
[INDENT]bg=/usr/share/backgrounds/default.png[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## if show bottom pane[/INDENT]
[INDENT]bottom_pane=1[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## if show language select control[/INDENT]
[INDENT]lang=1[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## if show keyboard layout select control[/INDENT]
[INDENT]keyboard=0[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## the theme of greeter[/INDENT]
[INDENT]theme=Industrial[/INDENT]
[INDENT]
[/INDENT]
[INDENT][input][/INDENT]
[INDENT]
[/INDENT]
[INDENT][userlist][/INDENT]
[INDENT]## if disable the user list control at greeter[/INDENT]
[INDENT]disable=0[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## whitelist user[/INDENT]
[INDENT]white=[/INDENT]
[INDENT]
[/INDENT]
[INDENT]## blacklist user[/INDENT]
[INDENT]black=[/INDENT]


Here is a screenshot of the box after it is rebooted with the above lxdm.conf (note that there is about a 30-second delay between completion of bootup dialog and the appearance of the bar at the bottom of the screen):

[IMG]http://i.imgur.com/slS8iBS.png[/IMG]

From here I can get into the file manager, however it only shows two files: "Access-Your-Private-Data.desktop" and "README.txt". There are no accessible applications to view the contents of these files. The "Run" menu option above does nothing.

N.B. To copy+paste contents of config and PAM files into these posts, I created a separate version of the box with the clean OS and LXDE installed as above, and then added the VBox Guest Additions along with the necessary libraries to support the Guest Additions. However, there are no differences between the config files and PAM files in the box with the Guest Additions and the box without the Guest Additions. I can provide screen shots of the box without Guest Additions if anything needs to be verified. Also, my attempts to get autologin are being done in the box without Guest Additions always starting from the post-"apt-get install lxde" snapshot. I created the box with Guest Additions solely to be able to copy+paste out the contents of the config and PAM files.

---

### Post by exarchate on 2013-04-26
UPDATE: I might have figured out the problem. I'm reinstalling the OS from scratch to test my theory.

I figured out how to auto-login to the command line. When I did that I was able to see the error message. When the OS immediately loaded up LXDE I never saw that message.

And it may be the key to everything.

---

### Post by exarchate on 2013-04-26
Problem solved. I'll write up a bit more about it later. But I just wanted to let the forum know that I've figured out the issue and no one has to spin their wheels on it anymore. Thank you!

---

