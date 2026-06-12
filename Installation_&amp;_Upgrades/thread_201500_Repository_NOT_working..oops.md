---
title: "Repository NOT working..oops"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-21
Hi,
I am trying to run Repository through System->Administration->Software Properties. But it seems I am not able to run the program at all Software properties and also the same with Add/Remove program.
What would be the problem? Any help?
thanks

---

### Post by aysiu on 2006-06-21
What's the terminal output of these commands? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
cat /etc/apt/sources.list
gksudo gnome-app-install
```

---

### Post by vasimakhtar on 2006-06-21
Thanks. Here is the report.

root@vasimakhtar:~# sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Fetched 2B in 5s (0B/s)
Reading package lists... Done


root@vasimakhtar:~# sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


root@vasimakhtar:~# cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory

root@vasimakhtar:~# cat /etc/apt/sources/list
cat: /etc/apt/sources/list: No such file or directory

root@vasimakhtar:~# gksudo gnome-app-install

(gksudo:12941): Gtk-WARNING **: cannot open display:


root@vasimakhtar:~#

---

### Post by vasimakhtar on 2006-06-21
Hi. I am sorry. I again run all the commands. Output is as under:

vasimakhtar@vasimakhtar:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Fetched 2B in 1s (2B/s)
Reading package lists... Done
vasimakhtar@vasimakhtar:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
vasimakhtar@vasimakhtar:~$ cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory
vasimakhtar@vasimakhtar:~$ gksudo gnome-app-install
warning: could not initiate dbus

** (gnome-app-install:13480): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:13480): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:13480): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:13480): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'
vasimakhtar@vasimakhtar:~$

---

### Post by aysiu on 2006-06-22
That's some weird output.

The first two commands--updating and making sure *ubuntu-desktop* is installed--seem to be working fine. 

Not having an /etc/apt/sources.list seems to run contrary to the update output, which seems to have drawn from several sources at ubuntu.com.

And a Google search on your python errors turns up nothing.

Can you try this? ```
cd /etc/apt
ls
``` I just want to see if there actually is a sources.list file...

---

### Post by vasimakhtar on 2006-06-22
Thanks. Here is the ls report:

root@vasimakhtar://etc/apt# ls
apt.conf                            sources.list-eu-2006-6-10-19-58-50
apt.conf.d                          sources.list-eu-2006-6-10-20-10-8
secring.gpg                         sources.list.save
sources.list~                       trustdb.gpg
sources.list_backup_200606122210    trusted.gpg
sources.list.d                      trusted.gpg~
sources.list-eu-2006-6-10-19-42-12

---

### Post by rcarring on 2006-06-22
I think you posted this in another thread. There I suggested your sources.list is missing, you need to create one.

---

### Post by vasimakhtar on 2006-06-22
Thanks. Can you please guide me how I can create source.list?
many thanks

---

### Post by aysiu on 2006-06-22
```
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo chown root:root sources.list
sudo mv sources.list /etc/apt/sources.list
sudo aptitude update
```

---

### Post by vasimakhtar on 2006-06-22
Thanks. I did the same and it works perfect. Once again thanks for your guidance.

---

