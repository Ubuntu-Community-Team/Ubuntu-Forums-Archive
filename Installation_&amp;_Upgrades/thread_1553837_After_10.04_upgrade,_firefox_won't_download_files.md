---
title: "After 10.04 upgrade, firefox won't download files"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2010-08-15
Hi--

Yesterday I upgraded from Ubunutu 8.04lts to 10.04 lts.

Now I cannot get Firefox to save downloads.

I get to the download page (for example, the OOo site), click on save the download, and the screen just disappears and nothing is downloaded.

Any ideas?

Thanks!

---

### Post by lovinglinux on 2010-08-15
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Report back with the results.

---

### Post by dgermann on 2010-08-15
lovinglinux--

Thanks for helping me!

Step 1--reinstalled ff and xul-runner, still have the problem.

Step 2--safemode: did not download, but got this error message:
```
[NoScript] style is null while processing JS redirects
*** exception in validateLeafName: [Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFile.create]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: file:///usr/lib/firefox-3.6.8/components/nsHelperAppDlg.js :: anonymous :: line 328"  data: no]

```

Will try the other two things--and disable NoScript--and report back soon. Probably not tonight.

Thanks for your help!

---

### Post by dgermann on 2010-08-15
OK, did step 3 and disabled NoScript. No joy.

Will do step 4 tomorrow.

Thanks!

---

### Post by dgermann on 2010-08-16
Hi--

OK, the new profile was able to do the download. So now I am going into the process of fixing the old profile, because I have so many bookmarks, I don't want to lose them, nor the various addons I have....

I will report back.

Thanks for this troubleshooting link!

---

### Post by lovinglinux on 2010-08-16
> **dgermann said:**
> Hi--

OK, the new profile was able to do the download. So now I am going into the process of fixing the old profile, because I have so many bookmarks, I don't want to lose them, nor the various addons I have....

I will report back.

Thanks for this troubleshooting link!

You are welcome. See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

---

### Post by dgermann on 2010-08-16
lovinglinux--

Your program FEBE is wonderful. Thank you for it. Also your tutorial.

Not sure where the problem was exactly, but after I restored the preferences the downloading was a no go.

So I created another new profile, looked and the preferences and found they were not so far off from what I wanted. So I tweaked those, added my extensions using FEBE, and the downloading worked!

So I am now using profile # 3 and it seems to be working. Did save # 1 just in case. So now to clean out all those files FEBE created that I no longer need.

Thanks again!

(By the way, tried to post earlier in the day but this site seemed to be down--whenever I logged in it just took me to another login screen. Tried some other sites and no problems there. Did anybody else notice that?)

---

### Post by lovinglinux on 2010-08-17
> **dgermann said:**
> lovinglinux--

Your program FEBE is wonderful. Thank you for it. Also your tutorial.

Not sure where the problem was exactly, but after I restored the preferences the downloading was a no go.

So I created another new profile, looked and the preferences and found they were not so far off from what I wanted. So I tweaked those, added my extensions using FEBE, and the downloading worked!

So I am now using profile # 3 and it seems to be working. Did save # 1 just in case. So now to clean out all those files FEBE created that I no longer need.

Thanks again!

(By the way, tried to post earlier in the day but this site seemed to be down--whenever I logged in it just took me to another login screen. Tried some other sites and no problems there. Did anybody else notice that?)

You are welcome. FEBE is not mine btw.

The forums were down yesterday.

---

### Post by dgermann on 2010-09-02
Hi--

Well I thought this problem was solved. Firefox and crew had other ideas! <grin>

I find that ff will not download files to a network directory and in fact to some other directories on my local drive. It will download them to Desktop, and then I can mv them to the correct directory.

I wanted to upgrade my router firmware. I asked it (Netgear WNR854T) to check for upgrades and it repeatedly reports a failure--check internet connection.

These problems also repeat in Epiphany Browser and in a fresh profile under ff.

When I run from firefox -P, and try to do a download, I get this error message:
```
*** exception in validateLeafName: [Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFile.create]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: file:///usr/lib/firefox-3.6.8/components/nsHelperAppDlg.js :: anonymous :: line 328"  data: no]
```

There are lots of references, some back to 2005, with this same error message in ff, and reports that it has been fixed. But nothing that seems to resolve this issue for me.

I did not have this issue before upgrading to Ubuntu 10.04.

The files download OK if I use IE from an XP computer on this same Samba network.

I checked out the file mentioned in the error message. Line 328 reads:
        ```
aLocalFile.create(Components.interfaces.nsIFile.NORMAL_FILE_TYPE, 0600);

```

I searched in that file for "data:no" and "anonymous" and "328" and found none of these phrases or words.

Any clues?

Thanks!

---

### Post by lovinglinux on 2010-09-02
> **dgermann said:**
> Any clues?

Thanks!

Nope.

---

### Post by dgermann on 2010-09-02
How bout with that clue I added from line 328?

Thanks!

---

### Post by ericlb on 2010-09-03
> **dgermann said:**
> Hi--

Yesterday I upgraded from Ubunutu 8.04lts to 10.04 lts.

Now I cannot get Firefox to save downloads.

I get to the download page (for example, the OOo site), click on save the download, and the screen just disappears and nothing is downloaded.

Any ideas?

Thanks!  Hi,  I also did an upgrade from 8.04 to 10.04 and have the same problem.  I tried all the solutions suggested but still no go.  In Firefox, files that I want to download I first have to save to desktop and then move to the desired directory.   In thunderbird I also can no longer open attachments. I have to save them to hard drive and then go to that file and open it.  Both are a pain.  Any suggestions about where to look to solve this problem?   Eric

---

### Post by lovinglinux on 2010-09-03
> **dgermann said:**
> How bout with that clue I added from line 328?

Thanks!

Perhaps Apparmor is messing with your Firefox permissions. Unfortunately, I have no experience with Apparmor.

---

### Post by dgermann on 2010-09-04
I wonder.

I see this, too from here [https://help.ubuntu.com/community/AppArmor]("https://help.ubuntu.com/community/AppArmor"):
> How can I enable AppArmor for Firefox?

Since Ubuntu 9.10 (Karmic), AppArmor ships with a profile for Firefox which is disabled by default. 

It still seems to me something is messing with permissions somewhere, and it might be this. Anybody have any idea how to trouble shoot this?

Thanks!

---

### Post by lovinglinux on 2010-09-04
> **dgermann said:**
> I wonder.

I see this, too from here [https://help.ubuntu.com/community/AppArmor]("https://help.ubuntu.com/community/AppArmor"):


It still seems to me something is messing with permissions somewhere, and it might be this. Anybody have any idea how to trouble shoot this?

Thanks!

bodhi.zazen is the Apparmor guru here.

---

### Post by dgermann on 2010-09-04
lovinglinux--

Thanks, I have sent him or her a pm inviting a look-see here.

---

### Post by bodhi.zazen on 2010-09-05
To test if the problem is with apparmor, put the firefox profile into complain.

```
sudo aa-complain firefox
```

ff should then run.

Follow your logs for error messages

```
tail -F /var/log/messages
```

---

### Post by dgermann on 2010-09-07
bodhi.zazen--

Thanks! Sorry you had to wait for a response.

I ran the commands. The first time, ff was running and when I ran your first command, nothing happened--ff did not start as I expected. Then I closed ff and ran the command again. Again, nothing happened. So I started ff. Up came a screen about fireuploader, which is not normal. Here are the logs:

```
doug@doug2:~$ man aa-complain
doug@doug2:~$ sudo aa-complain firefox
[sudo] password for doug: 
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.
doug@doug2:~$ sudo aa-complain firefox
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.
doug@doug2:~$ tail -F /var/log/messages
Sep  7 20:21:26 localhost kernel: [426789.434920] type=1502 audit(1283905286.390:691):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.434936] type=1502 audit(1283905286.390:692):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.434948] type=1502 audit(1283905286.390:693):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435014] type=1502 audit(1283905286.390:694):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435062] type=1502 audit(1283905286.390:695):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435074] type=1502 audit(1283905286.390:696):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435086] type=1502 audit(1283905286.390:697):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435108] type=1502 audit(1283905286.390:698):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435267] type=1502 audit(1283905286.390:699):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"
Sep  7 20:21:26 localhost kernel: [426789.435280] type=1502 audit(1283905286.390:700):  operation="file_lock" pid=29768 parent=29764 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"

```

time passes....

OK, I tried to do a download from a site where the downloads had previously failed. This time it succeeded, so perhaps the logs will tell us nothing useful. But here they are:
```

doug@doug2:~$ tail -F /var/log/messages
Sep  7 20:37:07 localhost kernel: [427730.324326] type=1502 audit(1283906227.282:1619):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.351671] type=1502 audit(1283906227.306:1620):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.380179] type=1502 audit(1283906227.338:1621):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.407305] type=1502 audit(1283906227.362:1622):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.434829] type=1502 audit(1283906227.390:1623):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.463077] type=1502 audit(1283906227.418:1624):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.489317] type=1502 audit(1283906227.446:1625):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.518161] type=1502 audit(1283906227.474:1626):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.544998] type=1502 audit(1283906227.502:1627):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
Sep  7 20:37:07 localhost kernel: [427730.573226] type=1502 audit(1283906227.530:1628):  operation="file_perm" pid=30057 parent=30053 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz.part"
```






Not sure if I did it right. If I did, what do these messages tell us?

Thanks!

---

### Post by bodhi.zazen on 2010-09-07
What firefox profile are you using ?

Post your ff profile and we can add to it.

The first error message, you need to allow "k" to 
[FONT=monospace]
~/[/FONT].mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db

```
owner @{HOME}/.mozilla/firefox/*/fireuploader/*.db rwk,
```For the second, you need to dl to Downloads or Desktop, or allow rw to 
[FONT=monospace]
[/FONT]/sam/doug2/dl-2010

I would dl to Downloads and move the file later, up to you.

---

### Post by dgermann on 2010-09-07
bodhi.zazen--

Thank you for helping me.

Which ff profile? The one called "doug." Maybe I don't know where to look, but this is what I see:
```
doug@doug2:~/.mozilla/firefox$ ls -alh
total 36K
drwxr-xr-x  5 doug doug 4.0K 2010-09-02 19:54 .
drwx------  5 doug doug 4.0K 2008-08-02 16:47 ..
drwx------ 12 doug doug 4.0K 2010-09-03 16:55 2fgopryj.default
drwx------  6 doug doug 4.0K 2010-09-03 16:53 kjkm482g.test20100902
-rw-------  1 doug doug 6.5K 2008-08-01 12:14 pluginreg.dat
-rw-------  1 doug doug 3.2K 2006-10-13 18:48 pluginreg.dat~
-rw-r--r--  1 doug doug  234 2010-09-07 22:44 profiles.ini
drwx------  9 doug doug 4.0K 2010-09-07 22:44 w3n7jo03.doug-test2

```

So there is no profile called "doug." But I have had this downloading problem with the profile called "test20100902" as well--this is one I used firefox -P to create, so it has only the bare bones.

I am lost by the rest of your post. I see that you seem to be giving me code to add the "k" to a file, but where? In /etc/fstab?

What does "k" do? Don't think I've ever seen it before.

And if I have to add this code to every extension I have, why haven't the developers made that part of the installation process?

As to adding write access to dl-2010, here are its permissions:

```
doug@doug2:~$ ls -alh /sam/doug2
total 23M
drwxr-xr-x  3 doug doug    0 2010-09-07 21:55 dl-2010

```

Since I am performing this operation as the user doug, then it appears to me the permissions already include write access. Or am I missing something?

Thanks!

---

### Post by bodhi.zazen on 2010-09-07
The apparmor profile for firefox is in 

/etc/apparmor.d/

If you post the profile it is easier to debug. If this is the default profile, you should file a bug report on launchpad.

For an intro to apparmor see :

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

---

### Post by dgermann on 2010-09-08
bodhi.zazen--

OK, there are two files named usr.bin.firefox: one in the apparmor.d directory, and one in its subdirectory cache. The latter is a binary file, the previously named one I could not upload. The response I got here was "Upload Errors usr.bin.firefox: Invalid File" So here is the file:

```
doug@doug2:/etc/apparmor.d$ cat usr.bin.firefox
# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

/usr/lib/firefox-3.6.8/firefox-*bin flags=(complain) {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/X>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/timezone r,
  /etc/wildmidi/wildmidi.cfg r,
  /etc/xdg/xubuntu/applications/defaults.list r,
  /usr/bin/dbus-launch ixr,
  /usr/bin/scim Ux,
  /usr/bin/scim-bridge Ux,
  /usr/bin/apport-bug Ux,
  /usr/local/lib{,32,64}/*.so* mr,
  /usr/lib/gstreamer0.10/gstreamer-0.10/gst-plugin-scanner ix,
  /usr/bin/apturl Uxr,

  # firefox specific
  /etc/firefox*/ r,
  /etc/firefox*/** r,
  /etc/xul-ext/** r,
  /etc/xulrunner-1.9*/ r,
  /etc/xulrunner-1.9*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-3.6.8/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-3.6.8/** ixr,
  /usr/bin/basename ixr,
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  /usr/bin/tr ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,

  /etc/mtab r,
  /etc/fstab r,

  # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # allow read and write to all user's files, except explicitly denied ones
  @{HOME}/ r,
  @{HOME}/** r,
  owner @{HOME}/** w,
  owner @{HOME}/Desktop/** r,

  # removable media and filesystems
  /media/** r,
  /mnt/** r,
  /srv/** r,
  owner /media/** w,
  owner /mnt/** w,
  owner /srv/** w,

  #include <abstractions/private-files>
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,

  # comment this out if using gpg plugin/addons
  audit deny @{HOME}/.gnupg/** mrwkl,

  # per-user firefox configuration
  owner @{HOME}/.mozilla/ rw,
  owner @{HOME}/.mozilla/** rw,
  owner @{HOME}/.mozilla/**/*.sqlite* k,
  owner @{HOME}/.mozilla/**/.parentlock k,
  owner @{HOME}/.mozilla/plugins/** rm,
  owner @{HOME}/.mozilla/**/plugins/** rm,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny /usr/lib/firefox-3.6.8/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  #
  # Plugins/helpers
  #
  @{PROC}/[0-9]*/fd/ r,
  /usr/lib/** rm,
  /bin/bash ixr,
  /bin/dash ixr,
  /bin/grep ixr,
  /bin/sed ixr,
  /bin/ps Uxr,
  /bin/uname Uxr,
  /usr/bin/gnome-codec-install Uxr,
  /usr/bin/m4 ixr,
  /usr/bin/mkfifo Uxr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer Uxr,
  /usr/bin/pulseaudio ixr,
  /var/lib/ r,
  /var/lib/** mr,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # for maximum plugin/helper compatibility
  #/usr/bin/* Uxr,
  #/usr/lib/*/** ixr,

  #
  # For stricter access, comment out the 'maximum plugin/helper compatibility'
  # lines above and uncomment these
  #

  # for PDFs
  owner @{HOME}/.adobe/** rw,
  /opt/Adobe/Reader9/bin/acroread Uxr,
  /opt/Adobe/Reader9/** r,
  /usr/bin/evince PUxr,
  /usr/bin/okular Uxr,

  # Image viewers
  /usr/bin/eog Uxr,
  /usr/bin/gimp* Uxr,

  # Openoffice.org
  /usr/bin/ooffice Uxr,
  /usr/bin/oocalc Uxr,
  /usr/bin/oodraw Uxr,
  /usr/bin/ooimpress Uxr,
  /usr/bin/oowriter Uxr,
  /usr/lib/openoffice/program/soffice Uxr,

  # Multimedia
  #include <abstractions/ubuntu-media-players>
  owner @{HOME}/.macromedia/** rw,
  /opt/real/RealPlayer/mozilla/nphelix.so rm,

  # Bittorrent clients
  #include <abstractions/ubuntu-bittorrent-clients>

  # Archivers
  /usr/bin/ark Uxr,
  /usr/bin/file-roller Uxr,
  /usr/bin/xarchiver Uxr,

  # Text editors (It's All Text [https://addons.mozilla.org/en-US/firefox/addon/4125])
  /usr/bin/emacsclient.emacs-snapshot Uxr,
  /usr/bin/emacsclient.emacs22 Uxr,
  /usr/bin/gedit Uxr,
  /usr/bin/vim.gnome Uxr,
  /usr/bin/leafpad Uxr,
  /usr/bin/mousepad Uxr,

  # Mozplugger
  /etc/mozpluggerrc r,
  /usr/bin/mozplugger-helper Uxr,

  # Java
  @{HOME}/.java/deployment/deployment.properties k,
  /etc/java-*/ r,
  /etc/java-*/** r,
  /usr/lib/jvm/java-6-openjdk/jre/bin/java cx -> firefox_openjdk,
  /usr/lib/jvm/java-*-sun-1.*/jre/bin/java{,_vm} cx -> firefox_java,
  /usr/lib/jvm/java-*-sun-1.*/jre/lib/*/libnp*.so cx -> firefox_java,
  /usr/lib/j2*-ibm/jre/bin/java cx -> firefox_java,

  # for mailto:
  #include <abstractions/ubuntu-email>
  #include <abstractions/ubuntu-console-email>

  # Terminals for using console applications. These abstractions should ideally
  # have 'ix' to restrct access to what only firefox is allowed to do
  #include <abstractions/ubuntu-gnome-terminal>

  # By default, we won't support launching a terminal program in Xterm or
  # KDE's konsole. It opens up too many unnecessary files for most users.
  # People who need this functionality can uncomment the following:
  ##include <abstractions/ubuntu-xterm>
  ##include <abstractions/ubuntu-konsole>

  # Miscellaneous (to be abstracted)
  /usr/bin/nautilus Uxr,
  /usr/bin/thunar Uxr,
  /usr/bin/liferea-add-feed Uxr,


  #
  # Child profiles
  #

  # Profile for the supported OpenJDK in Ubuntu. This doesn't require the
  # unfortunate workarounds of the proprietary Javas, so have a separate
  # profile.
profile firefox_openjdk flags=(complain) {
    #include <abstractions/base>
    #include <abstractions/fonts>
    #include <abstractions/gnome>
    #include <abstractions/kde>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/user-tmp>
    #include <abstractions/private-files-strict>

    network inet stream,
    network inet6 stream,
    @{PROC}/[0-9]*/net/if_inet6 r,
    @{PROC}/[0-9]*/net/ipv6_route r,

    /etc/java-*/ r,
    /etc/java-*/** r,
    /etc/lsb-release r,
    /etc/ssl/certs/java/* r,
    /etc/timezone r,

    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/filesystems r,
    /sys/devices/system/cpu/ r,
    /sys/devices/system/cpu/** r,
    /usr/share/** r,
    /var/lib/dbus/machine-id r,

    /usr/bin/env ix,
    /usr/lib/jvm/java-6-openjdk/jre/bin/java ix,
    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa m,

    # Why would java need this?
    deny /usr/bin/gconftool-2 x,

    owner @{HOME}/ r,
    owner @{HOME}/** rwk,
  }

  # Profile for commercial Javas. These need workarounds to work right (eg
  # Sun's forcing of an executable stack (LP: #535247)).
profile firefox_java flags=(complain) {
    #include <abstractions/base>
    #include <abstractions/fonts>
    #include <abstractions/gnome>
    #include <abstractions/kde>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/user-tmp>
    #include <abstractions/private-files-strict>

    network inet stream,
    network inet6 stream,
    @{PROC}/[0-9]*/net/if_inet6 r,
    @{PROC}/[0-9]*/net/ipv6_route r,

    /etc/java-*/ r,
    /etc/java-*/** r,
    /etc/lsb-release r,
    /etc/ssl/certs/java/* r,
    /etc/timezone r,

    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/filesystems r,
    /sys/devices/system/cpu/ r,
    /sys/devices/system/cpu/** r,
    /usr/share/** r,
    /var/lib/dbus/machine-id r,

    /usr/bin/env ix,
    /usr/lib/jvm/java-*-sun-1.*/jre/bin/java{,_vm} ix,
    /usr/lib/jvm/java-*-sun-1.*/jre/lib/i386/client/classes.jsa m,
    /usr/lib/j2*-ibm/jre/bin/java ix,

    # noisy, can't write here anyway
    deny /etc/.java/ w,
    deny /etc/.java/** w,

    deny /usr/bin/gconftool-2 x,

    owner @{HOME}/ r,
    owner @{HOME}/** rwk,

    # These are seriously unfortunate, but required due to LP: #535247
    /etc/passwd m,
    owner @{HOME}/.java/**/cache/** m,
    owner /tmp/** m,
    /usr/lib{,32,64}/jvm/**/*.jar mr,
    /usr/share/fonts/** m,
  }
}
doug@doug2:/etc/apparmor.d$ 

```


It is the only such file that says firefox, so does that mean it is the default and needs to be reported to launchpad? Launchpad where? Seems to me there are many projects there, right?

There is also a file under abstractions/user-download which reads (this also would not upload here): 

```
doug@doug2:/etc/apparmor.d$ cat abstractions/user-download 
# $Id$
# ------------------------------------------------------------------
#
#    Copyright (C) 2002-2006 Novell/SUSE
#
#    This program is free software; you can redistribute it and/or
#    modify it under the terms of version 2 of the GNU General Public
#    License published by the Free Software Foundation.
#
# ------------------------------------------------------------------

# Description: Where common programs should allow users to download
# files

  @{HOME}/tmp/**       		rwl,
  @{HOME}/download/**  		rwl,
  @{HOME}/downloads/** 		rwl,
  @{HOME}/[a-zA-Z0-9]* 		rwl,
  @{HOME}/Desktop      		r,
  @{HOME}/Desktop/*    		rwl,
  "@{HOME}/My Downloads/" 	r,
  "@{HOME}/My Downloads/**" 	rwl,
doug@doug2:/etc/apparmor.d$ 

```

Hopefully this will tell you something. I'm not sure what I'm looking at.

OK, I am off to look at those introductions.

Thanks!

---

### Post by dgermann on 2010-09-08
OK, after reading those and thinking about what is going on, it seems to me that turning on complain mode opened up the gates so I could do the downloads. It therefore was probably in enforce mode before.

So just now I did a download and got these messages:
```
Sep  8 20:59:32 localhost kernel: [515475.846859] type=1502 audit(1283993972.802:3240):  operation="mknod" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033
Sep  8 20:59:32 localhost kernel: [515475.853615] type=1502 audit(1283993972.810:3241):  operation="open" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033
Sep  8 20:59:32 localhost kernel: [515475.855493] type=1502 audit(1283993972.810:3242):  operation="mknod" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.871171] type=1502 audit(1283993972.826:3243):  operation="open" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.872362] type=1502 audit(1283993972.830:3244):  operation="open" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="a::" denied_mask="a::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.889581] type=1502 audit(1283993972.846:3245):  operation="file_perm" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.889835] type=1502 audit(1283993972.846:3246):  operation="file_perm" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.932342] type=1502 audit(1283993972.890:3247):  operation="file_perm" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.932606] type=1502 audit(1283993972.890:3248):  operation="file_perm" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274
Sep  8 20:59:32 localhost kernel: [515475.932835] type=1502 audit(1283993972.890:3249):  operation="file_perm" pid=30227 parent=30223 profile="/usr/lib/firefox-3.6.8/firefox-*bin" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D70332E70617274

```

So if I had it in enforce mode, the downloads would not have happened. Correct?

So Apparmor is where my issue is, then?

So what is the fix? I know you said to make some entry, but where?

Thanks!

---

### Post by bodhi.zazen on 2010-09-08
First, you are using the default firefox apparmor profile, so I advise you file a bug report on Launchpad.

Second, the latest round of messages is I believe because you are using an encrypted home directory. They can be ignored.

Abstractions are pieces of code that can be used in more then one profile. So you can use that set of restrictions for firefox, thunderbird, chromium, whatever simply by calling it with the line
[FONT=monospace]
[/FONT]#include <abstractions/user-download>

rather then writing those restrictions over and over in each profile.

To solve your problem, I think adding the line 

> owner @{HOME}/.mozilla/firefox/*/fireuploader/*.db rwk,

at the bottom of the "# per-user firefox configuration" section will help.

In terms of downloads, I do not see the source of the error at first glance.

You could try changing the line

> owner @{HOME}/** w,

to

```
owner @{HOME}/** rw,
```

But that is a bit messy.

It may be better to download files to your desktop, and then, after the download is complete, copy or move the files to their final location.

Part of the point of apparmor, IMO, is to restrict access to files in your home directory. There is no need for firefox to read any files in ~/.ssh or ~/.gpg for example.

You certainly could loosen those restrictions (with the line I gave you), it should work.

Put aa bace into enforce mode and watch the logs. Post any error messages 

```
sudo aa-enforce firefox
```

---

### Post by dgermann on 2010-09-10
bodhi.zazen--

Is this the correct place to report this bug? [https://bugs.launchpad.net/apparmor/+filebug]("https://bugs.launchpad.net/apparmor/+filebug")

I'm not using an encrypted home directory as far as I know. How would I test to make sure?

I want to download to the directory where I have been downloading for several years. Downloading and copying is an extra step and an extra chance to make a mistake. So I think allowing downloads there makes sense for me.

I am unclear why those messages are there about fire-uploader since I was doing no uploading at the time. Is that perhaps part of the bug report I need to make?

I will try playing with the code you gave me.

By the way, there was a firefox update last night and it wrote over the apparmor file. Here is the changed file:

```
doug@doug2:~$ cat /etc/apparmor.d/usr.bin.firefox
# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

/usr/lib/firefox-3.6.9/firefox-*bin {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/X>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/timezone r,
  /etc/wildmidi/wildmidi.cfg r,
  /etc/xdg/xubuntu/applications/defaults.list r,
  /usr/bin/dbus-launch ixr,
  /usr/bin/scim Ux,
  /usr/bin/scim-bridge Ux,
  /usr/bin/apport-bug Ux,
  /usr/local/lib{,32,64}/*.so* mr,
  /usr/lib/gstreamer0.10/gstreamer-0.10/gst-plugin-scanner ix,
  /usr/bin/apturl Uxr,

  # firefox specific
  /etc/firefox*/ r,
  /etc/firefox*/** r,
  /etc/xul-ext/** r,
  /etc/xulrunner-1.9*/ r,
  /etc/xulrunner-1.9*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-3.6.9/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-3.6.9/** ixr,
  /usr/bin/basename ixr,
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  /usr/bin/tr ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,

  /etc/mtab r,
  /etc/fstab r,

  # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # allow read and write to all user's files, except explicitly denied ones
  @{HOME}/ r,
  @{HOME}/** r,
  owner @{HOME}/** w,
  owner @{HOME}/Desktop/** r,

  # removable media and filesystems
  /media/** r,
  /mnt/** r,
  /srv/** r,
  owner /media/** w,
  owner /mnt/** w,
  owner /srv/** w,

  #include <abstractions/private-files>
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,

  # comment this out if using gpg plugin/addons
  audit deny @{HOME}/.gnupg/** mrwkl,

  # per-user firefox configuration
  owner @{HOME}/.mozilla/ rw,
  owner @{HOME}/.mozilla/** rw,
  owner @{HOME}/.mozilla/**/*.sqlite* k,
  owner @{HOME}/.mozilla/**/.parentlock k,
  owner @{HOME}/.mozilla/plugins/** rm,
  owner @{HOME}/.mozilla/**/plugins/** rm,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny /usr/lib/firefox-3.6.9/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  #
  # Plugins/helpers
  #
  @{PROC}/[0-9]*/fd/ r,
  /usr/lib/** rm,
  /bin/bash ixr,
  /bin/dash ixr,
  /bin/grep ixr,
  /bin/sed ixr,
  /bin/ps Uxr,
  /bin/uname Uxr,
  /usr/bin/gnome-codec-install Uxr,
  /usr/bin/m4 ixr,
  /usr/bin/mkfifo Uxr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer Uxr,
  /usr/bin/pulseaudio ixr,
  /var/lib/ r,
  /var/lib/** mr,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # for maximum plugin/helper compatibility
  #/usr/bin/* Uxr,
  #/usr/lib/*/** ixr,

  #
  # For stricter access, comment out the 'maximum plugin/helper compatibility'
  # lines above and uncomment these
  #

  # for PDFs
  owner @{HOME}/.adobe/** rw,
  /opt/Adobe/Reader9/bin/acroread Uxr,
  /opt/Adobe/Reader9/** r,
  /usr/bin/evince PUxr,
  /usr/bin/okular Uxr,

  # Image viewers
  /usr/bin/eog Uxr,
  /usr/bin/gimp* Uxr,

  # Openoffice.org
  /usr/bin/ooffice Uxr,
  /usr/bin/oocalc Uxr,
  /usr/bin/oodraw Uxr,
  /usr/bin/ooimpress Uxr,
  /usr/bin/oowriter Uxr,
  /usr/lib/openoffice/program/soffice Uxr,

  # Multimedia
  #include <abstractions/ubuntu-media-players>
  owner @{HOME}/.macromedia/** rw,
  /opt/real/RealPlayer/mozilla/nphelix.so rm,

  # Bittorrent clients
  #include <abstractions/ubuntu-bittorrent-clients>

  # Archivers
  /usr/bin/ark Uxr,
  /usr/bin/file-roller Uxr,
  /usr/bin/xarchiver Uxr,

  # Text editors (It's All Text [https://addons.mozilla.org/en-US/firefox/addon/4125])
  /usr/bin/emacsclient.emacs-snapshot Uxr,
  /usr/bin/emacsclient.emacs22 Uxr,
  /usr/bin/gedit Uxr,
  /usr/bin/vim.gnome Uxr,
  /usr/bin/leafpad Uxr,
  /usr/bin/mousepad Uxr,

  # Mozplugger
  /etc/mozpluggerrc r,
  /usr/bin/mozplugger-helper Uxr,

  # Java
  @{HOME}/.java/deployment/deployment.properties k,
  /etc/java-*/ r,
  /etc/java-*/** r,
  /usr/lib/jvm/java-6-openjdk/jre/bin/java cx -> firefox_openjdk,
  /usr/lib/jvm/java-*-sun-1.*/jre/bin/java{,_vm} cx -> firefox_java,
  /usr/lib/jvm/java-*-sun-1.*/jre/lib/*/libnp*.so cx -> firefox_java,
  /usr/lib/j2*-ibm/jre/bin/java cx -> firefox_java,

  # for mailto:
  #include <abstractions/ubuntu-email>
  #include <abstractions/ubuntu-console-email>

  # Terminals for using console applications. These abstractions should ideally
  # have 'ix' to restrct access to what only firefox is allowed to do
  #include <abstractions/ubuntu-gnome-terminal>

  # By default, we won't support launching a terminal program in Xterm or
  # KDE's konsole. It opens up too many unnecessary files for most users.
  # People who need this functionality can uncomment the following:
  ##include <abstractions/ubuntu-xterm>
  ##include <abstractions/ubuntu-konsole>

  # Miscellaneous (to be abstracted)
  /usr/bin/nautilus Uxr,
  /usr/bin/thunar Uxr,
  /usr/bin/liferea-add-feed Uxr,


  #
  # Child profiles
  #

  # Profile for the supported OpenJDK in Ubuntu. This doesn't require the
  # unfortunate workarounds of the proprietary Javas, so have a separate
  # profile.
  profile firefox_openjdk {
    #include <abstractions/base>
    #include <abstractions/fonts>
    #include <abstractions/gnome>
    #include <abstractions/kde>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/user-tmp>
    #include <abstractions/private-files-strict>

    network inet stream,
    network inet6 stream,
    @{PROC}/[0-9]*/net/if_inet6 r,
    @{PROC}/[0-9]*/net/ipv6_route r,

    /etc/java-*/ r,
    /etc/java-*/** r,
    /etc/lsb-release r,
    /etc/ssl/certs/java/* r,
    /etc/timezone r,

    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/filesystems r,
    /sys/devices/system/cpu/ r,
    /sys/devices/system/cpu/** r,
    /usr/share/** r,
    /var/lib/dbus/machine-id r,

    /usr/bin/env ix,
    /usr/lib/jvm/java-6-openjdk/jre/bin/java ix,
    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa m,

    # Why would java need this?
    deny /usr/bin/gconftool-2 x,

    owner @{HOME}/ r,
    owner @{HOME}/** rwk,
  }

  # Profile for commercial Javas. These need workarounds to work right (eg
  # Sun's forcing of an executable stack (LP: #535247)).
  profile firefox_java {
    #include <abstractions/base>
    #include <abstractions/fonts>
    #include <abstractions/gnome>
    #include <abstractions/kde>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/user-tmp>
    #include <abstractions/private-files-strict>

    network inet stream,
    network inet6 stream,
    @{PROC}/[0-9]*/net/if_inet6 r,
    @{PROC}/[0-9]*/net/ipv6_route r,

    /etc/java-*/ r,
    /etc/java-*/** r,
    /etc/lsb-release r,
    /etc/ssl/certs/java/* r,
    /etc/timezone r,

    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/filesystems r,
    /sys/devices/system/cpu/ r,
    /sys/devices/system/cpu/** r,
    /usr/share/** r,
    /var/lib/dbus/machine-id r,

    /usr/bin/env ix,
    /usr/lib/jvm/java-*-sun-1.*/jre/bin/java{,_vm} ix,
    /usr/lib/jvm/java-*-sun-1.*/jre/lib/i386/client/classes.jsa m,
    /usr/lib/j2*-ibm/jre/bin/java ix,

    # noisy, can't write here anyway
    deny /etc/.java/ w,
    deny /etc/.java/** w,

    deny /usr/bin/gconftool-2 x,

    owner @{HOME}/ r,
    owner @{HOME}/** rwk,

    # These are seriously unfortunate, but required due to LP: #535247
    /etc/passwd m,
    owner @{HOME}/.java/**/cache/** m,
    owner /tmp/** m,
    /usr/lib{,32,64}/jvm/**/*.jar mr,
    /usr/share/fonts/** m,
  }
}
doug@doug2:~$ 

```

Anything there catch your eye?

Thanks for helping me, bodhi.zazen!

---

### Post by dgermann on 2010-09-10
Hi--

OK, I just tried to do a download after the new profile was installed, and it would not allow me to do so. I have not changed it to enforce mode. Here are the error messages:

```
Sep 10 00:10:58 localhost kernel: [613361.401058] __ratelimit: 12 callbacks suppressed
Sep 10 00:10:58 localhost kernel: [613361.401063] type=1503 audit(1284091858.358:3412):  operation="mknod" pid=30457 parent=30453 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033

```

Even after I run
```
doug@doug2:~$ sudo aa-complain firefox
[sudo] password for doug: 
doug@doug2:~$ 

```

I get:

```
Sep 10 00:14:27 localhost sudo: pam_sm_authenticate: Called
Sep 10 00:14:27 localhost sudo: pam_sm_authenticate: username = [doug]
Sep 10 00:14:53 localhost kernel: [613596.900307] type=1503 audit(1284092093.854:3413):  operation="mknod" pid=30457 parent=30453 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033

```

So what was working is no longer working, after this upgrade.

A couple of other things that might be helpful:

```
doug@doug2:~$ sudo apparmor --status
[sudo] password for doug: 
sudo: apparmor: command not found
doug@doug2:~$ sudo /etc/init.d/apparmor status
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
/usr/lib/firefox-3.6.8/firefox-*bin (complain)
/usr/lib/firefox-3.6.8/firefox-*bin//firefox_openjdk (complain)
/usr/lib/firefox-3.6.8/firefox-*bin//firefox_java (complain)
/usr/sbin/tcpdump (enforce)
/usr/sbin/ntpd (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/clamd (enforce)
/usr/bin/freshclam (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
doug@doug2:~$ ls /etc/apparmor.d
abstractions    gdm-guest-session  usr.bin.evince            usr.sbin.clamd
cache           local              usr.bin.firefox           usr.sbin.cupsd
disable         sbin.dhclient3     usr.bin.firefox.dpkg-old  usr.sbin.ntpd
force-complain  tunables           usr.bin.freshclam         usr.sbin.tcpdump
doug@doug2:~$ 

```

Any clues here?

---

### Post by bodhi.zazen on 2010-09-10
Your apparmor profile does not appear to be in complain mode. I would re-start apparmor and re-check that.

I would file a bug report as if you do not have an encrytped $HOME then I do not know what the "name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033" refers to.

I see no other problems with what you posted.

---

### Post by dgermann on 2010-09-11
bodhi.zazen--

Well, this is getting strange.

As you suggested, I tried to restart apparmor and got a fail message. So I started it and reloaded it, and then issued the command to put firefox into complain mode. Still I have it in enforce mode. I tried different permutations and tried to follow the messages I was getting, but it is not working--it is still in enforce mode. Here is what I did and the results, in case it gives any useful clues:

```
doug@doug2:~$ sudo /etc/init.d/apparmor stop
[sudo] password for doug: 
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
doug@doug2:~$ sudo /etc/init.d/apparmor stop
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
doug@doug2:~$ sudo /etc/init.d/apparmor start
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:~$ sudo /etc/init.d/apparmor reload
 * Reloading AppArmor profiles                                                  Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:~$ sudo /etc/init.d/apparmor status
/usr/sbin/tcpdump (enforce)
/usr/sbin/ntpd (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/clamd (enforce)
/usr/bin/freshclam (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
doug@doug2:~$ sudo aa-complain firefox
doug@doug2:~$ sudo /etc/init.d/apparmor status
/usr/sbin/tcpdump (enforce)
/usr/sbin/ntpd (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/clamd (enforce)
/usr/bin/freshclam (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
doug@doug2:~$ sudo aa-complain firefox-3.6.9
Can't find firefox-3.6.9 in the system path list.  If the name of the application is correct, please run 'which firefox-3.6.9' as a user with the correct PATH environment set up in order to find the fully-qualified path.
doug@doug2:~$ sudo aa-complain firefox-*bin
Can't find firefox-*bin in the system path list.  If the name of the application is correct, please run 'which firefox-*bin' as a user with the correct PATH environment set up in order to find the fully-qualified path.
doug@doug2:~$ which firefox-3.6.9
doug@doug2:~$ which firefox-*bin
doug@doug2:~$ which firefox-
doug@doug2:~$ sudo aa-complain firefox_openjdk
Can't find firefox_openjdk in the system path list.  If the name of the application is correct, please run 'which firefox_openjdk' as a user with the correct PATH environment set up in order to find the fully-qualified path.
doug@doug2:~$ sudo aa-complain firefox_java
Can't find firefox_java in the system path list.  If the name of the application is correct, please run 'which firefox_java' as a user with the correct PATH environment set up in order to find the fully-qualified path.
doug@doug2:~$ which firefox_openjdk
doug@doug2:~$ which firefox_java
doug@doug2:~$ 

```

Now I just re-ran the stop command twice, getting the fail message as before on the first time, but not on the second. Here is what the logs show:

```
Sep 11 16:48:34 localhost kernel: [759617.767430] type=1505 audit(1284238114.723:3467):  operation="profile_remove" pid=30765 name="/sbin/dhclient3" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.767489] type=1505 audit(1284238114.723:3468):  operation="profile_remove" pid=30765 name="/usr/bin/evince" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.767646] type=1505 audit(1284238114.723:3469):  operation="profile_remove" pid=30765 name="/usr/bin/evince-previewer" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.767759] type=1505 audit(1284238114.723:3470):  operation="profile_remove" pid=30765 name="/usr/bin/evince-thumbnailer" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.767862] type=1505 audit(1284238114.723:3471):  operation="profile_remove" pid=30765 name="/usr/bin/freshclam" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.767931] type=1505 audit(1284238114.723:3472):  operation="profile_remove" pid=30765 name="/usr/lib/connman/scripts/dhclient-script" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.767990] type=1505 audit(1284238114.723:3473):  operation="profile_remove" pid=30765 name="/usr/lib/cups/backend/cups-pdf" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.768333] type=1505 audit(1284238114.723:3474):  operation="profile_remove" pid=30765 name="/usr/lib/firefox-3.6.9/firefox-*bin" namespace="root"
Sep 11 16:48:34 localhost kernel: [759617.768456] type=1505 audit(1284238114.723:3475):  operation="profile_remove" info="profile does not exist" error=-2 pid=30765 name="/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java" namespace="root"
Sep 11 16:48:56 localhost kernel: [759639.297104] type=1505 audit(1284238136.254:3476):  operation="profile_remove" pid=30790 name="/usr/lib/NetworkManager/nm-dhcp-client.action" namespace="root"
Sep 11 16:48:56 localhost kernel: [759639.297190] type=1505 audit(1284238136.254:3477):  operation="profile_remove" pid=30790 name="/usr/sbin/clamd" namespace="root"
Sep 11 16:48:56 localhost kernel: [759639.297255] type=1505 audit(1284238136.254:3478):  operation="profile_remove" pid=30790 name="/usr/sbin/cupsd" namespace="root"
Sep 11 16:48:56 localhost kernel: [759639.297316] type=1505 audit(1284238136.254:3479):  operation="profile_remove" pid=30790 name="/usr/sbin/ntpd" namespace="root"
Sep 11 16:48:56 localhost kernel: [759639.297382] type=1505 audit(1284238136.254:3480):  operation="profile_remove" pid=30790 name="/usr/sbin/tcpdump" namespace="root"
Sep 11 16:48:56 localhost kernel: [759639.297491] type=1505 audit(1284238136.254:3481):  operation="profile_remove" pid=30790 name="/usr/share/gdm/guest-session/Xsession" namespace="root"

```

Thinking the reload took this time because of only one fail message, I did this:

```
doug@doug2:~$ sudo /etc/init.d/apparmor stop
 * Unloading AppArmor profiles                                        [fail] 
                                                                      [ OK ]
doug@doug2:~$ sudo /etc/init.d/apparmor stop
 * Unloading AppArmor profiles                                        [ OK ] 
doug@doug2:~$ sudo /etc/init.d/apparmor start
 * Starting AppArmor profiles                                                Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                      [ OK ]
doug@doug2:~$ sudo /etc/init.d/apparmor status
/usr/sbin/tcpdump (enforce)
/usr/sbin/ntpd (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/clamd (enforce)
/usr/bin/freshclam (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
doug@doug2:~$ sudo aa-complain firefox
doug@doug2:~$ sudo aa-complain firefox*
Can't find firefox* in the system path list.  If the name of the application is correct, please run 'which firefox*' as a user with the correct PATH environment set up in order to find the fully-qualified path.
doug@doug2:~$ sudo /etc/init.d/apparmor status
/usr/sbin/tcpdump (enforce)
/usr/sbin/ntpd (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/clamd (enforce)
/usr/bin/freshclam (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
doug@doug2:~$ 

```

So it is still showing firefox in enforce mode. What am I doing wrong? What do I need to do differently?

I will try to post this as a bug now.

Oh, I have no idea what that long string of numbers is either. I looked in fstab and find nothing with that string in it. The HDDs are referred to in that file by UUID, but nothing like that string.

Thanks for helping me, bodhi.zazen!

---

### Post by dgermann on 2010-09-11
OK, it has been filed as a bug, here: [https://bugs.launchpad.net/apparmor/+bug/636023]("https://bugs.launchpad.net/apparmor/+bug/636023")

Please add anything else you think is helpful to the developers. Thanks!

---

### Post by bodhi.zazen on 2010-09-11
I did not see anythign wrong with what you posted.

To put firefox into complain:

```
sudo aa-complain firefox
``` should work.

---

### Post by dgermann on 2010-09-11
Nope: 

```
doug@doug2:~$ sudo aa-complain firefox
[sudo] password for doug: 
doug@doug2:~$ sudo /etc/init.d/apparmor status
/usr/sbin/tcpdump (enforce)
/usr/sbin/ntpd (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/clamd (enforce)
/usr/bin/freshclam (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
```

What do you suggest, O guru? <wink>

---

### Post by bodhi.zazen on 2010-09-11
Well, it seems your apparmor is not acting as mine is =(

> bodhi@lucid:~$ firefox -v
Mozilla Firefox 3.6.9, Copyright (c) 1998 - 2010 mozilla.org

[COLOR=darkred]bodhi@lucid:~$ sudo service apparmor status | grep firefox
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)[/COLOR]

bodhi@lucid:~$ sudo aa-complain firefox
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.

[COLOR=darkgreen]bodhi@lucid:~$ sudo service apparmor status | grep firefox
/usr/lib/firefox-3.6.9/firefox-*bin (complain)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (complain)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (complain)[/COLOR]

bodhi@lucid:~$ 

---

### Post by dgermann on 2010-09-12
bodhi.zazen--

Well I tried the exact same commands:
```
doug@doug2:~$ sudo service apparmor status | grep firefox
[sudo] password for doug: 
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ sudo aa-complain firefox
doug@doug2:~$ sudo service apparmor status | grep firefox
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ 

```

I see that yours responds to sudo aa-complain firefox; mine does not. Is that some setting in apparmor?

Also, last night (after I posted the bug report) I was able to download a file to a network directory, even though it says it is in enforce mode. That seems strange to me--to you too?

Any suggestions?

I will try rebooting and see if that makes any difference....


...Time passes....

Nope, same exact results after rebooting. Not sure what to do next? Reinstall apparmor? Reinstall ff?

Oh, and the log continues to complain about fireuploader:

```
Sep 12 20:53:49 localhost kernel: [  206.085561] type=1503 audit(1284339229.032:22):  operation="file_lock" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"

```

OK, I disabled fireuploader, restarted ff, and got this log entry:


```
Sep 12 21:00:10 localhost kernel: [  587.180108] type=1503 audit(1284339610.260:23):  operation="file_lock" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"

```

Then I tried to download, and got this log entry:

```
Sep 12 21:05:24 localhost kernel: [  901.710444] type=1503 audit(1284339924.792:24):  operation="mknod" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033
```

Downloading the same file to Desktop works, and there is no log entry generated. Tried a different file from a different website and got this error:
```
Sep 12 21:09:42 localhost kernel: [ 1159.416430] type=1503 audit(1284340182.496:25):  operation="mknod" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-11-2010-2.tar.gz"

```

(Maybe that long string is the file name on the one site?)

So we still have something strange going on. Thoughts as to what to do?

---

### Post by bodhi.zazen on 2010-09-12
> **dgermann said:**
> bodhi.zazen--

Well I tried the exact same commands:
```
doug@doug2:~$ sudo service apparmor status | grep firefox
[sudo] password for doug: 
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ sudo aa-complain firefox
doug@doug2:~$ sudo service apparmor status | grep firefox
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ 

```I see that yours responds to sudo aa-complain firefox; mine does not. Is that some setting in apparmor?

Also, last night (after I posted the bug report) I was able to download a file to a network directory, even though it says it is in enforce mode. That seems strange to me--to you too?

Any suggestions?

I will try rebooting and see if that makes any difference....


...Time passes....

Nope, same exact results after rebooting. Not sure what to do next? Reinstall apparmor? Reinstall ff?

Oh, and the log continues to complain about fireuploader:

```
Sep 12 20:53:49 localhost kernel: [  206.085561] type=1503 audit(1284339229.032:22):  operation="file_lock" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"

```OK, I disabled fireuploader, restarted ff, and got this log entry:


```
Sep 12 21:00:10 localhost kernel: [  587.180108] type=1503 audit(1284339610.260:23):  operation="file_lock" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/doug/.mozilla/firefox/w3n7jo03.doug-test2/fireuploader/dbFireUploader.db"

```Then I tried to download, and got this log entry:

```
Sep 12 21:05:24 localhost kernel: [  901.710444] type=1503 audit(1284339924.792:24):  operation="mknod" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031302F312D3133204265696E672050726573656E74202620496E76697369626C652E6D7033
```Downloading the same file to Desktop works, and there is no log entry generated. Tried a different file from a different website and got this error:
```
Sep 12 21:09:42 localhost kernel: [ 1159.416430] type=1503 audit(1284340182.496:25):  operation="mknod" pid=3119 parent=3115 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-11-2010-2.tar.gz"

```(Maybe that long string is the file name on the one site?)

So we still have something strange going on. Thoughts as to what to do?

Well, you have two issues. First apparmor is not working normally after an upgrade. You may want to perform a fresh install.

You could try purging and re-installing apparmor. You will probably need to purge and re-install apparmor-profiles as well and possibly firefox. may or may not be easier then a fresh install.

In terms of your audit messages, you have to decide if you wish to allow them or not, and if so, modify your apparmor profile.

For fireupload, I think I already gave you the information
[FONT=monospace]
```
[/FONT]owner @{HOME}/[FONT=monospace][/FONT].mozilla/firefox/w3n7jo03.doug-test2/fireuploader/*.db rwk,
```

And on for all your denials.

After modifying a profile you would normally reload it

```
sudo apparmor_parser -r firefox
```

---

### Post by dgermann on 2010-09-13
bodhi.zazen--

Thanks for sticking with me!

OK, I did these things in this order:

installed apparmor-profiles, previously uninstalled
ran the three commands you gave--no different results

completely uninstalled apparmor, apparmor-profiles, and apparmor-utils (nothing else is shown in synaptic with an apparmor name as installed)
reinstalled all three
ran the three commands you gave--still got no different results

reinstalled via synaptic firefox, firefox-3.0, firefox-3.0-gnome-support, firefox-branding, and firefox-gnome-support
completely uninstalled apparmor, apparmor-profiles, and apparmor-utils 
reinstalled all three
ran the three commands you gave--still no different results

By fresh install do you mean to wipe my hdd clean and install Ubuntu 10.04 fresh?

Yes, you had given me some code to put into an apparmor profile. I did not do it, because I thought I was supposed to try some of these other steps first. Sorry. I will look up what and where and work on it.

Thanks, bodhi.zazen!

time passes....

OK, I made the two changes you suggested above in post # 24, and then did this and got this error message:

```
doug@doug2:/etc/apparmor.d$ sudo apparmor_parser -r firefox
Error: Could not read profile firefox: No such file or directory.
doug@doug2:/etc/apparmor.d$ 

```

So it appears it does not see its own files!

What if I were to delete these files from apparmor.d? usr.bin.firefox & usr.bin.firefox.dpkg-old

---

### Post by dgermann on 2010-09-13
OK, here are the next things I did, thinking I would remove the profiles I saw in /etc/apparmor.d/:
```

doug@doug2:/etc/apparmor.d$ sudo mv usr.bin.firefox usr.bin.firefox20100913
doug@doug2:/etc/apparmor.d$ sudo mv usr.bin.firefox.dpkg-old usr.bin.firefox.dpkg-old20100913
doug@doug2:/etc/apparmor.d$ sudo apparmor_parser -r firefoxError: Could not read profile firefox: No such file or directory.
doug@doug2:/etc/apparmor.d$ sudo service apparmor --help
Usage: service < option > | --status-all | [ service_name [ command | --full-restart ] ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor --full-restart
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor --full-restart
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor --full-restart
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [ OK ] 
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [ OK ] 
doug@doug2:/etc/apparmor.d$ sudo service apparmor start
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo apparmor_parser -r firefoxError: Could not read profile firefox: No such file or directory.
doug@doug2:/etc/apparmor.d$ sudo service apparmor status | grep firefox/usr/lib/firefox-3.6.8/firefox-*bin (complain)
/usr/lib/firefox-3.6.8/firefox-*bin//firefox_openjdk (complain)
/usr/lib/firefox-3.6.8/firefox-*bin//firefox_java (complain)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
```

Notice that to get it to stop took 3 tries, but it seemed to go. Then after reloading, it found more profiles, some in complain and some in enforce mode.

When I go to the /etc/apparmor.d directory, none of these shows up, ust the two renamed files. Shouldn't they show up there? Is it storing the profiles someplace else?

Thanks!

---

### Post by bodhi.zazen on 2010-09-13
Well, you can not just rename the profiles in /etc/apparmor.d like that.

Any file in /etc/apparmor.d must be the name of the binary you want to confine.

And it is not a great idea to delete or rename them like that, you may "break" apt or some of the apparmor packages.I would advise you :

1. rename the files to restore the origional names.

2. Make the changes I suggested to the firefox apparmor profile.

The reboot and see if it is working.

---

### Post by dgermann on 2010-09-14
bodhi.zazen--

Previously had made the changes in the files as you requested. See posts 35 & 24 above.

Renamed them: 
```
doug@doug2:/etc/apparmor.d$ sudo mv usr.bin.firefox20100913 usr.bin.firefox
[sudo] password for doug: 
doug@doug2:/etc/apparmor.d$ sudo mv usr.bin.firefox.dpkg-old20100913 usr.bin.firefox.dpkg-old
doug@doug2:/etc/apparmor.d$ ls -alh |grep firefox
-rw-r--r--   1 root root 8.7K 2010-09-13 22:54 usr.bin.firefox
-rw-r--r--   1 root root 8.6K 2010-09-07 20:29 usr.bin.firefox.dpkg-old
doug@doug2:/etc/apparmor.d$ 

```

Going down for reboot now....

Returning....

And we are back to this:

```
doug@doug2:~$ sudo service apparmor status | grep firefox
[sudo] password for doug: 
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ 

```

---

### Post by bodhi.zazen on 2010-09-14
OK, is firefox working the way you want ? Can you download and use your extensions ?

If that is not the case, post any apparmor denial (in /var/log/messages).

If so, I do not know how to fix the apparmor problem you have with placing firefox into complain, ie I do not know why 

```
sudo aa-complain firefox
``` is not working.

---

### Post by dgermann on 2010-09-14
bodhi.zazen--

Just tried to do a download, and it failed. Log entry was:

```
Sep 14 22:28:49 localhost kernel: [ 1937.659732] type=1503 audit(1284517729.662:43):  operation="mknod" pid=3038 parent=3034 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz"
```

It will however download to Desktop. So no, it is not working the way I expect or want.

And yes, the changes you suggested I put in the profile are still in there.

Is there another apparmor profile someplace else? If not, why does it think there are these?

```
doug@doug2:/etc/apparmor.d$ sudo service apparmor status | grep firefox
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)

```

---

### Post by bodhi.zazen on 2010-09-15
> **dgermann said:**
> bodhi.zazen--

Just tried to do a download, and it failed. Log entry was:

```
Sep 14 22:28:49 localhost kernel: [ 1937.659732] type=1503 audit(1284517729.662:43):  operation="mknod" pid=3038 parent=3034 profile="/usr/lib/firefox-3.6.9/firefox-*bin" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2010/backup-Sep-1-2010-2.tar.gz"
```It will however download to Desktop. So no, it is not working the way I expect or want.

For that one, add this line in your profile :

```
owner @{HOME}/dl* rw,
```

> And yes, the changes you suggested I put in the profile are still in there.

Is there another apparmor profile someplace else? If not, why does it think there are these?

```
doug@doug2:/etc/apparmor.d$ sudo service apparmor status | grep firefox
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)

```

No, all the profiles are in the same location, /etc/apparmor.d

They are called "/usr/lib/firefox-3.6.9/" as that is where the firefox binary is , /bin/firefox is a symbolic link. 

This is "normal" , but your apparmor is not acting normally.

---

### Post by dgermann on 2010-09-15
bodhi.zazen--

OK, now* it seems to allow me to download to my dl directory. Thanks!

Any idea why it sees two versions of Firefox installed, and one as complain and one as enforce? Does this suggest that a fix might involve the FF installation in some way?

* For the record, here is what I did:

```
doug@doug2:/etc/apparmor.d$ sudo gedit usr.bin.firefox
[sudo] password for doug: 
doug@doug2:/etc/apparmor.d$ sudo apparmor_parser -r firefox
Error: Could not read profile firefox: No such file or directory.
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [ OK ] 
doug@doug2:/etc/apparmor.d$ sudo service apparmor start
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ 

```

---

### Post by bodhi.zazen on 2010-09-15
> **dgermann said:**
> bodhi.zazen--

OK, now* it seems to allow me to download to my dl directory. Thanks!

Any idea why it sees two versions of Firefox installed, and one as complain and one as enforce? Does this suggest that a fix might involve the FF installation in some way?

* For the record, here is what I did:

```
doug@doug2:/etc/apparmor.d$ sudo gedit usr.bin.firefox
[sudo] password for doug: 
doug@doug2:/etc/apparmor.d$ sudo apparmor_parser -r firefox
Error: Could not read profile firefox: No such file or directory.
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [fail] 
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Unloading AppArmor profiles                                           [ OK ] 
doug@doug2:/etc/apparmor.d$ sudo service apparmor start
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]
doug@doug2:/etc/apparmor.d$ 

```

You should have only one profile for firefox, if you have more then one, move the old profile elsewhere.

with that error message , apparmor_parse, use the full path to the profile

```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
```

or what have you.

---

### Post by dgermann on 2010-09-15
bodhi.zazen--

OK, that command worked to the extent it did not complain.

Thank you for all your help, bodhi.zazen!

Do you feel we are as far as we can go, at least until we hear on the bug report? Should I withdraw the bug report?

---

### Post by dgermann on 2010-09-15
bodhi.zazen--

You gave me what I think is THE clue. I just did this:
```
doug@doug2:~$ sudo aa-complain firefox
doug@doug2:~$ sudo service apparmor status |grep fire
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ sudo aa-complain /etc/apparmor.d/usr.bin.firefox
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.
doug@doug2:~$ sudo service apparmor status |grep fire
/usr/lib/firefox-3.6.9/firefox-*bin (complain)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (complain)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (complain)
doug@doug2:~$ 

```
Now that we have gotten here, is there anything I need to be doing?

---

### Post by bodhi.zazen on 2010-09-16
> **dgermann said:**
> bodhi.zazen--

You gave me what I think is THE clue. I just did this:
```
doug@doug2:~$ sudo aa-complain firefox
doug@doug2:~$ sudo service apparmor status |grep fire
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (enforce)
doug@doug2:~$ sudo aa-complain /etc/apparmor.d/usr.bin.firefox
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.
doug@doug2:~$ sudo service apparmor status |grep fire
/usr/lib/firefox-3.6.9/firefox-*bin (complain)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_openjdk (complain)
/usr/lib/firefox-3.6.9/firefox-*bin//firefox_java (complain)
doug@doug2:~$ 

```Now that we have gotten here, is there anything I need to be doing?

That looks fantastic =)

Hope you learned a bit along the way, sounds as if it is "working".

I still do not understand why "sudo aa-complain firefox" does not work, but that is minor. When in doubt, use the full path, "sudo aa-complain /etc/apparmor.d/profile_name"

---

### Post by lovinglinux on 2010-09-16
I have been following the discussion silently. I'm glad you fixed. 

bodhi.zazen rocks :D

---

### Post by dgermann on 2012-02-04
Hi--

Well, it happened again!

Today, Firefox upgraded to a new version (10), and installed a new apparmor profile.

What I want to do: download to a network directory.
What I can do: download to my home directory.

Here is what I tried: 

1. sudo gedit /etc/apparmor.d/usr.bin.firefox
adding to section “# allow read and write to all user's files, except explicitly denied ones”
  owner @{HOME}/** rw,
  owner @{HOME}/Desktop/** rw,
  owner @{HOME}/dl* rw,
  owner /sam/** rw,
[Note: network is mounted at /sam, and I download to /sam/../dl-2012; see post #41 above for the line "owner @{HOME}/dl* rw,"]

adding to section “# per-user firefox configuration:”
owner @{HOME}/.mozilla/firefox/*/fireuploader/*.db rwk,

2. Then:
```
doug@doug2:/etc/apparmor.d$ sudo apparmor_parser -r ./usr.bin.firefox
doug@doug2:/etc/apparmor.d$ sudo service apparmor stop
 * Clearing AppArmor profiles cache                                      [ OK ] 
All profile caches have been cleared, but no profiles have been unloaded.
Unloading profiles will leave already running processes permanently
unconfined, which can lead to unexpected situations.

To set a process to complain mode, use the command line tool
'aa-complain'. To really tear down all profiles, run the init script
with the 'teardown' option."
doug@doug2:/etc/apparmor.d$ sudo service apparmor start
 * Starting AppArmor profiles                                                   Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                         [ OK ]

```

3. Then I stopped and restarted firefox and attempted my download to the network. No joy. Downloaded to home directory as workaround.

What do I need to do? (I do not understand Apparmor, and am merely following the steps above in this thread the best I can.)

Thanks!

---

### Post by bodhi.zazen on 2012-02-05
Are you the owner of the /sam directory ?

Are there any denials in the logs ?

---

### Post by dgermann on 2012-02-05
bodhi.zazen--

root is the owner of /sam and all / level directories, so no I am not the owner of this directory.

The logs show this when I try to do a download now:
```
Feb  5 19:33:07 localhost kernel: [1031416.059988] type=1503 audit(1328488387.803:288):  operation="open" pid=9764 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2012/ImportExportTools-2.6.4.xpi"
Feb  5 19:33:35 localhost kernel: [1031443.629024] type=1503 audit(1328488415.375:289):  operation="mknod" pid=8656 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2012/backup-Feb-4-2012-2.tar.gz"
```

Thanks, bodhi.zazen!

---

### Post by dgermann on 2012-02-09
Hi--

Testing some things here to see if I can find some clues.

1. First I set to complain and asked for a status:
```
doug@doug2:/etc/apparmor.d$ sudo aa-complain /etc/apparmor.d/usr.bin.firefox
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.
doug@doug2:/etc/apparmor.d$ sudo service apparmor status | grep firefox
   /usr/lib/firefox-9.0.1/firefox-*bin
   /usr/lib/firefox-9.0.1/firefox-*bin//firefox_java
   /usr/lib/firefox-9.0.1/firefox-*bin//firefox_openjdk
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_java
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_openjdk
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]} (25177) 
doug@doug2:/etc/apparmor.d$ 
```

The status responses are not comprehensible to me. Are they telling me anything useful?

Before I did this, I could not do a download to a network directory as I wished. After this, I could download to the network folder where I want it. I was running
```
tail -F /var/log/messages
```
while I did this test, and got absolutely no log messages during this download after I set it to complain.

Before I set it to complain, I did get several complaints, some as I started specifying the download on the website, but before I actually hit the download button there:```


Feb  9 20:34:11 localhost kernel: [1380679.327154] type=1503 audit(1328837651.071:785):  operation="open" pid=26284 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031312F3230313130373032206C69666520726576696577206D616E75616C2E646F63
Feb  9 20:34:18 localhost kernel: [1380686.316686] type=1503 audit(1328837658.063:786):  operation="open" pid=26292 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2012/ImportExportTools-2.6.4.xpi"
Feb  9 20:34:42 localhost kernel: [1380710.568448] type=1503 audit(1328837682.315:787):  operation="mknod" pid=25177 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2012/backup-Feb-8-2012-1.tar.gz.test"
Feb  9 20:35:23 localhost kernel: [1380751.874843] type=1503 audit(1328837723.619:788):  operation="open" pid=26319 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2012/ImportExportTools-2.6.4.xpi"
Feb  9 20:35:23 localhost kernel: [1380751.881754] type=1503 audit(1328837723.627:789):  operation="open" pid=26317 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/sam/doug2/dl-2012/ImportExportTools-2.6.4.xpi"
Feb  9 20:35:33 localhost kernel: [1380761.980555] type=1503 audit(1328837733.727:790):  operation="open" pid=26317 parent=1 profile="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F73616D2F646F7567322F646C2D323031312F3230313130373032206C69666520726576696577206D616E75616C2E646F63
Feb  9 20:37:24 localhost sudo: pam_sm_authenticate: Called
Feb  9 20:37:24 localhost sudo: pam_sm_authenticate: username = [doug]
Feb  9 20:41:09 localhost kernel: [1381097.953132] type=1505 audit(1328838069.699:791):  operation="profile_replace" pid=26474 name="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}"
Feb  9 20:41:09 localhost kernel: [1381097.953363] type=1505 audit(1328838069.699:792):  operation="profile_replace" pid=26474 name="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_java"
Feb  9 20:41:09 localhost kernel: [1381097.953594] type=1505 audit(1328838069.699:793):  operation="profile_replace" pid=26474 name="/usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_openjdk"
```

So that is one set of clues, although I do not know what it means.

2. The second is that since this upgrade, I cannot do *uploads* either. I have tried uploads to both Facebook and Dropbox.com and neither will go. The uploads are from a network directory.

Aha! Having this set in complain mode allows me to do some uploading on Facebook. I uploaded 2 or so photos, and then Facebook started complaining about needing the latest Flash Player (which I have), and pushed me into their "Basic uploader" Then it would not publish the pictures, but did allow them to be uploaded. In any case, I don't think I got anything in the log during the first two regular uploads, but these on the basic uploads:

```
Feb  9 21:03:38 localhost kernel: [1382447.226468] Inbound IN=eth0 OUT= MAC[blanked] SRC=184.85.82.110 DST=192.168.0.5 LEN=77 TOS=0x00 PREC=0x20 TTL=58 ID=48916 DF PROTO=TCP SPT=443 DPT=57301 WINDOW=17119 RES=0x00 ACK PSH URGP=0 
Feb  9 21:03:39 localhost kernel: [1382447.739642] Inbound IN=eth0 OUT= MAC=[blanked] SRC=184.85.82.110 DST=192.168.0.5 LEN=77 TOS=0x00 PREC=0x20 TTL=58 ID=22840 DF PROTO=TCP SPT=443 DPT=57299 WINDOW=17119 RES=0x00 ACK PSH URGP=0 
Feb  9 21:03:39 localhost kernel: [1382447.866736] Inbound IN=eth0 OUT= MAC=[blanked] SRC=184.85.82.110 DST=192.168.0.5 LEN=77 TOS=0x00 PREC=0x20 TTL=58 ID=64543 DF PROTO=TCP SPT=443 DPT=57300 WINDOW=17119 RES=0x00 ACK PSH URGP=0 
Feb  9 21:04:06 localhost kernel: [1382475.067031] Inbound IN=eth0 OUT= MAC=[blanked] SRC=184.85.82.110 DST=192.168.0.5 LEN=77 TOS=0x00 PREC=0x20 TTL=58 ID=48917 DF PROTO=TCP SPT=443 DPT=57301 WINDOW=17119 RES=0x00 ACK PSH URGP=0 
Feb  9 21:04:07 localhost kernel: [1382476.090707] Inbound IN=eth0 OUT= MAC=[blanked] SRC=184.85.82.110 DST=192.168.0.5 LEN=77 TOS=0x00 PREC=0x20 TTL=58 ID=22841 DF PROTO=TCP SPT=443 DPT=57299 WINDOW=17119 RES=0x00 ACK PSH URGP=0 
Feb  9 21:04:08 localhost kernel: [1382476.347576] Inbound IN=eth0 OUT= MAC=[blanked] SRC=184.85.82.110 DST=192.168.0.5 LEN=77 TOS=0x00 PREC=0x20 TTL=58 ID=64544 DF PROTO=TCP SPT=443 DPT=57300 WINDOW=17119 RES=0x00 ACK PSH URGP=0 
```

Seems clear to me that Apparmor is the culprit here. (FWIW, I am able to do uploads via the Epiphany browser.)

So is there some solution to all this?

Is Apparmor more trouble than it's worth?

---

### Post by bodhi.zazen on 2012-02-10
Try removing the "owner" in "owner /sam/** rw,"

```
/sam rw,
/sam/** rw,
```

---

### Post by dgermann on 2012-02-11
bodhi.zazen--

Thank you very much, bodhi.zazen!

Was not entirely sure of the two lines in your example, so I chose to do only the second one. Here's what I did:
```
doug@doug2:~$ sudo gedit /etc/apparmor.d/usr.bin.firefox
[sudo] password for doug: 
doug@doug2:~$ sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.
doug@doug2:~$ 
```

Then, without restarting Firefox I tried the download to the network drive (from the site where I noticed the problem), and tried uploads from the network drive to Facebook and Dropbox, and all went flawlessly.

Thank you!

Did I need to run the parser again too?

What exactly did this change accomplish? Where might I learn a little more about apparmor syntax?

Thanks!

---

### Post by bodhi.zazen on 2012-02-11
You should be good to go. "owner" means you are granting privileges to the owner of the file / directory and as this is a shared directory it was causing problems.

---

### Post by dgermann on 2012-02-12
bodhi.zazen--

Thank you very much!

---

### Post by bodhi.zazen on 2012-02-13
> **dgermann said:**
> bodhi.zazen--

Thank you very much!

You are most welcome.

---

