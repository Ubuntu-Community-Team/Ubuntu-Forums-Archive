---
title: "Hardy Beta Fine, Now Blank Screen (with working pointer) after Login"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by williwaw on 2008-05-13
I installed Hardy Heron Beta via the DVD drive and it worked fine. As soon as the official release came out, I burned a DVD. Installation was fine, removed the system, and restarted. It booted fine, and loaded the splash screen page. Logged in and am confronted with a blank beige screen and circular mouse cursor.

With Hardy Heron Beta, this would happend for about 3 seconds and then the complete desktop would load, but here it's persistent. Left my system on for hours and it was still a blank beige screen and mouse cursor. 

Tried logging in via different sessions but always same result. Tried terminal and it does load a terminal but it's in the corner of the screen and rather unusable. Tried with other monitors as well. 

Hardware is an eBox-4300 (installed onto CF card that connects via IDE interface). 

Looked on forums but haven't found solution. 

Thanks in advance,

Thomas

---

### Post by veda_sticks on 2008-05-13
I have the same problem, i upgraded from ubuntu 7.04 to 8.04.

Everything went fine no errors until restarted. Login screen came up as usuall, log in and im presented with the gnome background and mouse pointer. desktop doesnt load.


I've only had this problem once before and that was with compiz and xfce4 after enabling compisite.

---

### Post by Herman on 2008-05-13
:)
If your Hardy Heron install boots to a tan screen with a mouse pointer in it and nothing else, that's because there is a bug in Hardy Heron that seems to affect Gnome especially in USB or SCSI devices. 
Refer to these two links, [https://bugs.launchpad.net/ubuntu/+s...dm/+bug/221850]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850") and [https://bugs.launchpad.net/ubuntu/+s...ng/+bug/218434]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434")

 To summarize, you can use the 'ctrl'+'alt'+'del' keyboard combination and log into a virtual terminal.
Log in with your usernam and password.
Type 'sudo rm /tmp/X0-lock'.
Then type 'startx'.
You should then have your Gnome Desktop.

Then open 'System'-->'Administration'-->'login window', open the security tab, and enable automatic login for the administrative user (yourself).
NOTE: It takes ages for the login window to open, like about five or six minutes and it looks like nothing is happening. Just be patient.

 The first time you try to shut down you'll be back to the tan screen again, (for the last time). 
Press'ctrl'+'alt'+'del' keyboard combination and log into a virtual terminal and type 'sudo shutdown -h -t 0 now', to shut the computer down.

From then on you shouldn't have any more problems, Hardy Heron will start up and shut down as normal. The only problem is it will be a single user system, if you add another user to share your computer you'll be back to the same problem, but maybe the developers will come up with an update that solves this problem if they haven't already done so. Likely they are working on it.

Regards, Herman :)

---

### Post by williwaw on 2008-05-15
That worked great - thanks so much!

---

### Post by ErmyDermy on 2008-05-18
I had the same problem and this fixed it, Thanks =]

---

