---
title: "problems with gutsy upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by centro99 on 2007-10-19
Hi,

I tried to upgrade a stable feisty to gutsy. I used the common way to upgrade, the update-manager. After downloading all new packages it began to install, but suddenly stopped with the message that I should shut down other package management related programs... no other program was running except of update-manager.

After a reboot, I tried to boot the new kernel, but failed with the message of a kernel panic/mount error. I restarted with the old kernel, but the login-manager did not appear (colored background could be seen, but nothing more..). The last possible thing to do was to start with the old kernel, in recovery mode. I checked package dependencies - there were lots of unmet dependencies...

Commands like "apt-get -f install" "apt-get dist-upgrade" did not help. So I started to manually solve the package dependencies, but now I stuck with the following problem: At certain points in my work the following error occurs:

```
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing compiz-gtk (--remove):
 subprocess pre-removal script returned error exit status 127
```

Could please someone help me? :confused:

bye

---

### Post by inhabit on 2007-10-19
I have a somewhat similar problem, well at least considering that "undefined symbol" error. I upgrade from feisty with the command-line tool, do-release-upgrade. It gave an error while updating database entries for torrentflux [I think it was that], but all in all the upgrade seemed to go well. But now my gnome-panel won't start. It gives the following error[s]:

```
(gnome-panel:12853): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x6c6b60

(gnome-panel:12853): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x6c6b60
gnome-panel: symbol lookup error: /usr/lib/gnome-panel/libwnck-applet.so: undefined symbol: gtk_widget_set_tooltip_text
```


Any ideas?

---

### Post by rookie_paul on 2007-10-20
Hello folks! I had the same problem upgrading from Xubuntu Feisty to Gutsy. I managed to fix it after I read the solution given by PerJensen here: [https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045]("https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045") (permalink: [https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045/comments/4]("https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045/comments/4")).
Also in my case, removing /usr/local/lib/libz.so.1.2.3 fixed the problem.

---

### Post by alexrudd on 2007-10-22
I had a similar problem, which completely screwed up my upgrade (different undefined symbol).

For me, removing a manually-compiled version of glib from /usr/local/lib did the trick.

---

### Post by jhillyerd on 2007-10-22
> **alexrudd said:**
> I had a similar problem, which completely screwed up my upgrade (different undefined symbol).

For me, removing a manually-compiled version of glib from /usr/local/lib did the trick.

Thanks, that helped me!  I didn't even remember I had another glib install.  I renamed /usr/local/lib and that seems to have unstuck things.

-james

---

### Post by dwinc on 2007-11-06
I too had aproblem after doing the upgrade to GG; when I tried to run R, which was installed previously and worked fine, I got the message about gzopen64 being an unrecognised symbol. I looked for files called libz.so* and found in my /usr/lib one called libz.so.1.2.3.3 along with symbolic links to it called libz.so and libz.so.1. I tried renaming each of these three, without helping the R problem, and with the result that OpenOffice would no longer load.So i gave them back their original names, and hey presto, now both R and OO work!
I don't understand why this fixed the problem but doing something similar might help someonoe to fix their own woes - or maybe suggest an explanation !

---

### Post by dwinc on 2007-11-07
further to my last post:
today i discover that i was wrong - trying to launch R still produces the same error if I try to launch it from my usual wd, but it works if launched from /usr/lib, where the three libz files are. anybody any ideas?

---

