---
title: "Gutsy upgrad w/ intel graphics - shows only an empty screen"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by pyramoose on 2007-10-21
I upgraded from feisty to gutsy yesterday using the update manager.  Things seemed to go fine except when I rebooted after the install, the boot procedure seemed to go okay and then when I should get a login screen I get a blank screen (but with a colored background) and the busy cursor flickering.  The mouse is responsive and can be moved around the screen.  I am using a dell 700m with intel 855 graphics.  In feisty I had it set up with the 855resolution hack and the i810 graphics driver.  I also had compiz-fusion running on feisty.  

As is suggested in a post back a few, I have tried changing the driver from i810 to intel, but this made no difference.  I also tried the vesa driver.  I have also disabled the 855resolution hack, run dpkg-reconfigure xserver-xorg and changed my gdm config file to use the default login.  The last changed the background screen to the default color, but still no login prompt.  Sometimes I can use cntl-alt-f2 to get a prompt (I'm not clear on why sometimes this works and sometimes not, but it seems to have something to do with which driver I have set and the vga line in my grub menu).  I just about run out of ideas, so any help would be great.

---

### Post by pyramoose on 2007-10-22
I'm now convinced I was on the wrong track.  After playing with the graphics settings for a day and failing to find consistent errors in the log files, I now think this might be a pam problem.  In auth.log I get pam_nologin(gdm:auth): cannot determine username.  This is repeated hundreds of times.  Looking at the date, these errors stated after I upgraded.  I made nologin optional in /etc/pam.d/gdm and then I get gkr-pam: couldn't get the user name: Conversation error

In feisty I already had libpam-keyring installed in feisty and had made the autologin changes posted here: [http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

If I remember correctly, during the upgrade I accepted new conf files for pam in place of my old ones.

Anyone have ideas how to fix this?  I will keep playing with it.

---

### Post by eric.guerin on 2007-10-22
Same problem with a dell latitude D420, still looking for an issue

---

### Post by web_knows on 2007-10-26
Maybe not exactly same thread, but I'm facing the following issue:

- upgraded from 7.04 to 7.10

- everything boots up correctly and I also get the GDM logon screen

- selected the user I wanted to log in and then, entered the password

- the GDM screen fades away and I get stuck with the mouse, the logon sound and the background only (X server continued to work, but the Gnome session doesn't come up)

- went to the logs and get this:

[INDENT][FONT="Courier New"][SIZE="1"]Oct 26 08:49:28 poseidon gdm[22948]: pam_nologin(gdm:auth): cannot determine username
Oct 26 08:49:36 poseidon gdm[22948]: pam_unix(gdm:session): session opened for user rivanor by (uid=0)
Oct 26 08:49:36 poseidon gdm[22948]: gkr-pam: unlocked 'login' keyring
Oct 26 08:51:08 poseidon gdm[22948]: pam_unix(gdm:session): session closed for user rivanor[/SIZE][/FONT][/INDENT]

My card is this one:

[INDENT][FONT="Courier New"][SIZE="1"]01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266][/SIZE][/FONT][/INDENT]

Also didn't find anything on the Release Notes for 7.10.

---

### Post by pyramoose on 2007-10-26
Well I gave up, made a new partition out of my empty space, installed gutsy in the new partition and mounted my old partition as my home directory and then rearranged my old files to get my old settings back.  I had to reinstall several programs but it ended up only taking a few hours, which was faster than trying to fix the uograde problem.  Gutsy works fine with the fresh install, so it was an upgrade issue.

---

