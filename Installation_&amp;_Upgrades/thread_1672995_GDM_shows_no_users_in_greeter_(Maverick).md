---
title: "GDM shows no users in greeter (Maverick)"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by klotz on 2011-01-21
After today's update in Maverick, GDM showed no users in the greeter and so it was impossible to input any login info through the GUI, though Alt-F1 console worked.  I re-installed GDM and a variety of other packages to no avail.

I found this same problem in an old OpenSUSE message:
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/447375-weird-problem-console-kit-daemon-networkmanger.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/447375-weird-problem-console-kit-daemon-networkmanger.html)

Indeed, console-kit-daemon isn't running, and if I start it by hand and restart gdm, all is fine.

I also see the error message 
  Error org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1/dbus-daemon-launch-helper: Success#012

in the logs.  I also get a similar popup after logging in.  It says "You might not be able to connect to the Bluetooth network via this machine."

Any ideas why console-kit-daemon would fail to start?

---

### Post by klotz on 2011-01-21
This problem shows up in archlinux:

[https://bbs.archlinux.org/viewtopic.php?pid=723809](https://bbs.archlinux.org/viewtopic.php?pid=723809)

The workaround there worked for me, but it looks unsafe and seems to be covering a permission problem:

chmod o+x /usr/lib/dbus-1.0/dbus-daemon-launch-helper

Since dbus-daemon-launch-helper is suid to root, that seems like an unnecessary risk.

---

### Post by SleepWalkerX on 2011-01-21
I'm having the same issue.  Running console-kit-daemon and restarting gdm seems to temporarily fix my problem.  Although I don't have that same file you do (dbus-daemon-launch-helper).  Hmm

---

### Post by VincentLaw on 2011-01-30
Maybe coz dbus-daemon-launch-helper is in /lib/dbus-1.0 under Ubuntu ...

Doing this:
```
 chmod o+x /lib/dbus-1.0/dbus-daemon-launch-helper
```Did the trick for me

---

### Post by paulbaker85 on 2011-03-29
I just had this issue for the second time.
Last occurrence was several months ago. Then again last night.

Both occasions were after accepting package updates when prompted.

The fix for me both times has been [FONT="Courier New"]chmod o+x /lib/dbus-1.0/dbus-daemon-launch-helper[/FONT]

So... is it something fundamentally broken on my PC, so it recurs after a package update? I don't think so as I have done a fresh install from DVD since the first occurrence.

To check, I re-installed the dbus package and the perms are broken again...

```
# BEFORE
# ls -l /lib/dbus-1.0/dbus-daemon-launch-helper
-rwsr-xr-x 1 root messagebus 47520 2011-03-04 17:36 /lib/dbus-1.0/dbus-daemon-launch-helper

# apt-get install --reinstall dbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/219kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 228229 files and directories currently installed.)
.
snip
.
# AFTER
# ls -l /lib/dbus-1.0/dbus-daemon-launch-helper
-rwsr-xr-- 1 root messagebus 47520 2011-03-04 17:36 /lib/dbus-1.0/dbus-daemon-launch-helper
```

So the question is: is dbus package broken, or should I be able to run without setting execute for world? If the latter, what's the "proper" fix?
Is it something to do with the gdm user?
Mine is:```
# id -a gdm
uid=113(gdm) gid=120(gdm) groups=120(gdm)
```


Many thanks

---

### Post by paulbaker85 on 2011-03-29
I think I found my own answer...

Somehow my messagebus account had the wrong gid - not messagebus.
The package installed the file with correct group perms = messagebus.
But obviously my messagabus account couldn't execute it.

I corrected the group, reinstalled the package (so no world execute) and all is well now.

So... I can only think that I copied over some error in the passwd file from my old to my new system install.

Hope this helps someone else.

---

