---
title: "Deluge not uninstalling destroying my system"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by otek on 2007-09-19
Hi,

Deluge cant be uninstalled, which makes my software list broken, i cant install anything and i cant uninstall anything since it always crashes on that deluge is broken or something. I stopped using deluge since it out of nowhere couldnt read torrents or add new ones. Synaptic says this: E: deluge-torrent: subprocess post-removal script returned error exit status 139

I cant install the updates i get notifications about, i cant install anything and i cant install or uninstall deluge.

Thank you in advance.

---

### Post by Pumalite on 2007-09-19
Try this:

sudo dpkg --remove --force-remove-reinstreq deluge

---

### Post by otek on 2007-09-19
simon@simon-desktop:~$ sudo dpkg --remove --force-remove-reinstreq deluge
Password:
dpkg - warning: ignoring request to remove deluge which isn't installed.

But in synaptic it shows as marked for uninstallation but not uninstalled, and you cant install it because you need to uninstall it first, and then it says it isnt installed. I dont know who i should be mad at, but deluge was a buggy piece of ****.

---

### Post by Pumalite on 2007-09-19
Try:

sudo dpkg --configure -a

---

### Post by otek on 2007-09-19
simon@simon-desktop:~$ sudo dpkg --configure -a
Password:
Setting up fglrx-amdcccle (8.40.4-1) ...

(update-desktop-database:19919): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing fglrx-amdcccle (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 fglrx-amdcccle

Awesome, another problem.

Thank you for helping me out (no i'm not ironic).

I dont want to reinstall ubuntu for the fifth time in a row :(.

---

### Post by Pumalite on 2007-09-19
Run:
sudo killall deluge

---

### Post by otek on 2007-09-20
simon@simon-desktop:~$ sudo killall deluge
Password:
deluge: no process killed

---

### Post by otek on 2007-09-20
I've changed deluge status to installed ok in the dpkg status file. I can access synaptic and view the updates but i cant install anything and i cant uninstall anything. When i try the remove code i now get this, which isnt the worlds biggest surprise.

simon@simon-desktop:~$ sudo dpkg --remove --force-remove-reinstreq deluge
Password:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2834 package `deluge-torrent':
 Configured-Version for package with inappropriate Status

---

### Post by Pumalite on 2007-09-20
I think you have to change all the instances of deluge in 'status'.


This is similar to what you have done, but review it and see if you can get something out of it:

To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
__________________
Good luck.

---

### Post by otek on 2007-09-20
Well changing i to install ok didnt work, since nothing can be installed or uninstalled, it just quits without any error message. So ive removed the entry from the status file and after the 10th restart today im gonna see how it goes. Thank you very much for youre time.

---

### Post by otek on 2007-09-20
Well i get no complaints about deluge anymore since i removed it completely from the status file, but now i get this.

dpkg: error processing fglrx-amdcccle (--configure):
subprocess post-installation script returned error exit status 139

my card is working like it should, well kind of, ive always had a problem with video output but now output is set to x11 and everything works. It's the same error, what does it mean? I've installed the drivers through envy, but the restricted driver blabla says im using the proprietary ati drivers, doesnt the drivers you get from envy not show up there?

Edit: I can uninstall and install but i still get the error, im thinking that maybe this will fudge up all the installations i make.

---

### Post by Pumalite on 2007-09-20
They will not fudge them. You will just have to put up with a reminder of the error you committed in the past.

---

### Post by otek on 2007-09-20
Hehe, but what does the error about fgrlx mean?

---

### Post by Pumalite on 2007-09-20
I wouldn't worry about it, unless it gives you trouble.

---

