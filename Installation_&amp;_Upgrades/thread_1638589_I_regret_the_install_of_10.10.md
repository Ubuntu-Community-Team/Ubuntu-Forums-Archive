---
title: "I regret the install of 10.10"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Fresh_NL on 2010-12-05
I was running 10.04 on my Asus EEE PC.
Today I upgraded from 10.04 to 10.10, but with lots of regrets.
The complete desktop changed. I don't even know how to access the system settings anymore.
I just wanted to start up the Twonky Media server from my personal folder again, which resides in my personal user folder, but I cannot find the folder at all!
Shame on the Ubuntu team to throw around the user experience so much. The Ubuntu Linux distribution has gone back to a nerdy level, I hoped it had recovered from that.
Make-the-user-feel-at-home! Is that so difficult?

Where is my Favorite group, where is my System group, where is my personal Home user folder?
I'm sure I can find them on my own, but it's a shame that my user experience has been taken into a rolercoaster.
Why make it so difficult on the user Ubuntu, why?!

---

### Post by uRock on 2010-12-05
Hello and Welcome to the forums.

Are you using the UNE or Ubuntu Desktop version?

Have you looked in the places menu? The folders should not have moved or changed in any way.

Can you open a terminal and enter **ls -al** and post the output here?

---

### Post by Fresh_NL on 2010-12-05
The terminal won't even start. I can see it in the left tray, because it used to be in my favorites, but clicking it doesn't seem to start it up.
I'm really disappointed about this upgrade. Why did I do it? All seems to be gone.

Thank you for your help though. The only application I want to start up now is the Twonky Media server. If you could help me to access my user folder again from this 10.10 version I'd be happy.

I'm really sad...

---

### Post by uRock on 2010-12-05
1. Are you using Ubuntu Desktop or the Netbook version, as the GUI's are very different with the integration of Unity.

2. When you installed Ubuntu, did you use the standard partitioning scheme or did you create a separate / and /home partition? This information will come in handy whould you decide to reinstall 10.04.

---

### Post by Fresh_NL on 2010-12-05
> **uRock said:**
> Hello and Welcome to the forums.

Are you using the UNE or Ubuntu Desktop version?

Have you looked in the places menu? The folders should not have moved or changed in any way.

Can you open a terminal and enter **ls -al** and post the output here?

Okay, I finally got the terminal started.
Here's what it says with 'ls -al':

marco@EEEPC:~$ ls -al
totaal 6272
drwxr-xr-x 53 marco marco    4096 2010-12-06 02:38 .
drwxr-xr-x  4 root  root     4096 2010-04-10 19:07 ..
drwx------  3 marco marco    4096 2010-04-11 00:08 .adobe
drwxr-xr-x  3 marco marco    4096 2010-04-12 23:36 Afbeeldingen
drwx------  9 marco marco    4096 2010-04-15 12:46 .amsn
drwx------  2 marco marco    4096 2010-04-15 12:45 amsn_received
-rw-------  1 marco marco    1441 2010-12-05 15:25 .bash_history
-rw-r--r--  1 marco marco     220 2010-04-05 17:52 .bash_logout
-rw-r--r--  1 marco marco    3180 2010-04-05 17:52 .bashrc
drwx------  2 marco marco    4096 2010-04-10 17:48 .bogofilter
drwxr-xr-x  2 marco marco    4096 2010-04-05 18:00 Bureaublad
drwx------ 19 marco marco    4096 2010-12-06 01:46 .cache
drwxr-xr-x 20 marco marco    4096 2010-12-06 01:46 .config
drwx------  3 marco marco    4096 2010-04-05 18:00 .dbus
-rw-r--r--  1 marco marco      46 2010-12-06 02:28 .dmrc
drwxr-xr-x  2 marco marco    4096 2010-04-21 14:52 Documenten
drwxr-xr-x  2 marco marco    4096 2010-11-04 21:42 Downloads
-rw-------  1 marco marco      16 2010-04-05 18:00 .esd_auth
drwxr-xr-x  8 marco marco    4096 2010-06-29 11:46 .evolution
-rw-r--r--  1 marco marco     167 2010-04-05 17:52 examples.desktop
drwxr-xr-x  2 marco marco    4096 2010-12-05 22:21 .fontconfig
drwx------  5 marco marco    4096 2010-12-06 02:28 .gconf
drwx------  2 marco marco    4096 2010-12-06 02:53 .gconfd
-rw-r-----  1 marco marco       0 2010-12-05 15:46 .gksu.lock
drwx------ 10 marco marco    4096 2010-12-06 01:42 .gnome2
drwx------  2 marco marco    4096 2010-04-05 18:00 .gnome2_private
drwx------  2 marco marco    4096 2010-05-05 19:53 .gnupg
drwxr-xr-x  2 marco marco    4096 2010-04-10 16:52 .gpilotd
-rw-r--r--  1 marco marco       4 2010-04-10 16:52 .gpilotd.pid
drwxr-xr-x  2 marco marco    4096 2010-10-06 20:08 .gstreamer-0.10
-rw-r--r--  1 marco marco     187 2010-12-06 02:28 .gtk-bookmarks
dr-x------  2 marco marco       0 2010-12-06 02:28 .gvfs
drwxr--r--  2 marco marco    4096 2010-04-19 00:59 .hardinfo
-rw-------  1 marco marco   32652 2010-12-06 02:28 .ICEauthority
drwxr-xr-x  2 marco marco    4096 2010-05-05 23:37 .icons
drwx------  3 marco marco    4096 2010-04-05 21:02 .kde
drwxr-xr-x  2 marco marco    4096 2010-06-09 12:52 Library
drwx------  3 marco marco    4096 2010-04-05 18:00 .local
drwx------  3 marco marco    4096 2010-04-11 00:08 .macromedia
drwx------  3 marco marco    4096 2010-04-10 19:33 .mission-control
drwx------  4 marco marco    4096 2010-04-15 17:05 .mozilla
drwx------  3 marco marco    4096 2010-04-15 17:05 .mozilla-thunderbird
drwxr-xr-x  2 marco marco    4096 2010-05-10 12:15 Muziek
-rw-------  1 root  root       14 2010-12-03 14:28 .nano_history
drwxr-xr-x  2 marco marco    4096 2010-04-05 18:00 .nautilus
drwxr-xr-x  2 marco marco    4096 2010-04-05 18:00 Openbaar
drwxr-xr-x  3 marco marco    4096 2010-04-05 18:57 .openoffice.org
drwx------  3 marco marco    4096 2010-04-18 00:21 .pki
-rw-r--r--  1 marco marco      37 2010-12-03 13:25 .printer-groups.xml
-rw-r--r--  1 marco marco     675 2010-04-05 17:52 .profile
drwx------  2 marco marco    4096 2010-12-06 02:28 .pulse
-rw-------  1 marco marco     256 2010-04-05 18:00 .pulse-cookie
drwxr-xr-x  3 marco marco    4096 2010-04-23 22:56 .rapache
-rw-------  1 marco marco    2493 2010-12-06 02:38 .recently-used.xbel
drwxr-xr-x  2 marco marco    4096 2010-04-05 18:00 Sjablonen
drwx------  3 marco marco    4096 2010-04-17 11:23 .Skype
drwx------  2 marco marco    4096 2010-04-05 18:00 .ssh
-rw-r--r--  1 marco marco       0 2010-04-05 18:04 .sudo_as_admin_successful
drwxr-xr-x  2 marco marco    4096 2010-05-05 23:37 .themes
drwx------  4 marco marco    4096 2010-04-05 21:55 .thumbnails
drwx------  2 marco marco    4096 2010-05-24 12:12 .tsclient
drwxr-xr-x  5 marco marco    4096 2010-06-20 00:32 twonkymedia
drwxr-xr-x  3 marco marco    4096 2010-06-20 00:14 .twonkymedia
drwxr-xr-x  5 marco marco   12288 2010-12-06 00:18 TwonkyMedia
-rwxr-xr-x  1 marco marco 2866767 2010-04-05 19:06 twonkymedia-i386-glibc-2.2.5-5.1.3.sh
-rwxr-xr-x  1 marco marco 2881722 2010-05-07 21:17 twonkymedia-i386-glibc-2.2.5-5.1.4.sh
drwxr-xr-x  8 marco marco    4096 2010-06-20 00:13 .TwonkyMediaServer
drwxrwxr-x  2 marco marco    4096 2010-04-05 20:01 Ubuntu One
drwxr-xr-x  2 marco marco    4096 2010-04-05 18:12 .update-manager-core
drwx------  2 marco marco    4096 2010-12-06 01:46 .update-notifier
-rw-r--r--  1 marco marco    5978 2010-04-19 00:54 .usbcreator.log
drwxr-xr-x  3 marco marco    4096 2010-04-12 23:36 Video's
-rw-------  1 marco marco    8443 2010-12-03 14:13 .viminfo
-rw-------  1 marco marco  117607 2010-12-06 02:54 .xsession-errors
-rw-------  1 marco marco  211311 2010-12-06 02:07 .xsession-errors.old
marco@EEEPC:~$

---

### Post by uRock on 2010-12-05
That is the contents of your /home folder. We just have to get the GUI changes figured out so that you can get things working right again.

---

### Post by Fresh_NL on 2010-12-05
> **uRock said:**
> That is the contents of your /home folder. We just have to get the GUI changes figured out so that you can get things working right again.

Yeah, I thought so. I knew all is still there, but Ubuntu 10.10 is obviously leaving me in the cold...
I'm switching back to 'nerd level' now and I will find out..
I'm only sorry for Ubuntu for it had to come to this point.

Still, 'why'?...

Thanks for your help!

---

### Post by uRock on 2010-12-05
> **Fresh_NL said:**
> Yeah, I thought so. I knew all is still there, but Ubuntu 10.10 is obviously leaving me in the cold...
I'm switching back to 'nerd level' now and I will find out..
I'm only sorry for Ubuntu for it had to come to this point.

Still, 'why'?...

Thanks for your help!
If you are using the Netbook version aka UNE, then yeah, there were a lot of changes. I personally haven't taken UNE for a spin yet. If you log out, will it allow you to select Gnome on the bottom panel where it says, Sessions? If yes, then give it a try and see how it looks.

---

### Post by Fresh_NL on 2010-12-06
> **uRock said:**
> If you are using the Netbook version aka UNE, then yeah, there were a lot of changes. I personally haven't taken UNE for a spin yet. If you log out, will it allow you to select Gnome on the bottom panel where it says, Sessions? If yes, then give it a try and see how it looks.

Thank you, you saved my day.
I followed your suggestion and changed the session from UNE to Desktop, that did the trick.
Many thanks!

---

### Post by uRock on 2010-12-06
> **Fresh_NL said:**
> Thank you, you saved my day.
I followed your suggestion and changed the session from UNE to Desktop, that did the trick.
Many thanks!
You are most welcome. I have a EeeeeeeeeeeeeeeePC as well, but I only use the desktop version on it.

---

### Post by Fresh_NL on 2010-12-06
> **uRock said:**
> You are most welcome. I have a EeeeeeeeeeeeeeeePC as well, but I only use the desktop version on it.

Yeah, the Ubuntu desktop version runs nicely on the 900. Ubuntu just seems to fit this little machine.
Ubuntu gave me so much combined with the 900. Twonky runs like a charm and I even managed to configure Ubuntu to allow printing from my iPhone with AirPrint.

The 900 runs night and day as a media server. The reason I still installed a GUI edition of Ubuntu is that I sometimes take the 900 with me to perform your everyday online stuff like e-mail and surfing.

My 'emotional' first post only shows how much I learned to rely on Ubuntu; can't do without it anymore.
Sometimes one just needs a little help from the community...

Please add a [SOLVED] to the title of this thread.
I guess I will keep on following these Ubuntu forums actively from now on.

---

