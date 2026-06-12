---
title: "frequent file system errors/checking"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by biosol on 2012-01-21
Since re installing Ubuntu 11.10 64 on my Sony Laptop, more frequently I'm getting filesystem errors.  I've pushed F to fix them several times, but they keep coming back.  Because I don't know if the system will boot without finding errors, it's rendering the system almost useable.

A couple days ago, it ran for hours and hours fixing the errors and I had to reboot it several times to continue the process.  Then booted fine for a couple days, and now back to finding errors again.

I've found if I push I for ignore it will boot up.  I've had to load up 10.4.3 LTS on an old P4 system as a work around.

This is on a dual boot system, Win7 and Ubuntu.  The drive is 500GB, 100GB for Ubuntu, the rest for Win7.

Is there a way I can check the filesystem and fix the errors permanently?  What commands would do the trick and would it be best to run them from a Live CD?

Any help greatly appreciated.  Like the system, just need to get reliability back.

---

### Post by dino99 on 2012-01-21
depends on which errors, you dont give them :(

sudo dpkg-reconfigure -phigh -a
( can take a while, let it end itself)

sudo shutdown -R now
( force fsck on next boot)

---

### Post by biosol on 2012-01-21
Most of the time it just says (during the boot up) checking for errors and then found errors F to fix, I to ignore or S to skip something like that and then when I push F to fix is says something /tmp now ready continue to wait,  I just let it go because the disk activity light is on, so I know it's working a way.

Recently sometimes I've gotten a UUID with a long string after disk not found or something.

---

### Post by dino99 on 2012-01-21
glance at your logs to let you know exactly whats is going on (blah-blah goes nowhere)

~/.xsession-errors
/var/log/

---

### Post by biosol on 2012-01-21
Ok, will do.  Not a pro here.  Can you help a little more with the commands?

less or cat  ~/.xsession-errors  ?

less or cat /var/logs/?

Thanks

---

### Post by biosol on 2012-01-21
This is from the ~/.xsession-errors.  Can't locate the /var/logs/

I've also run this command.   sudo dpkg-reconfigure -phigh -a

```
cat ~/.xsession-errors
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/robert/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-WArOxj
SSH_AUTH_SOCK=/tmp/keyring-WArOxj/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-WArOxj
SSH_AUTH_SOCK=/tmp/keyring-WArOxj/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-WArOxj
SSH_AUTH_SOCK=/tmp/keyring-WArOxj/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-WArOxj
SSH_AUTH_SOCK=/tmp/keyring-WArOxj/ssh
GPG_AGENT_INFO=/tmp/keyring-WArOxj/gpg:0:1

(gnome-settings-daemon:2084): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/robert/.compiz/session to /home/robert/.compiz-1/session
[LOG]: Copied file /home/robert/.compiz/session/1033177066c4c4161d132716303687883500000019070038 to /home/robert/.compiz-1/session/1033177066c4c4161d132716303687883500000019070038
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
gnome-session[2020]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "dropbox" (No such file or directory)
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
** (gnome-fallback-mount-helper:2129): DEBUG: Starting automounting manager
(bluetooth-applet:2124): Bluetooth-DEBUG: adding killswitch idx 1 state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: adding killswitch idx 2 state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:2124): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
** (gnome-fallback-mount-helper:2129): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2
** (gnome-fallback-mount-helper:2129): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:2129): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:2129): DEBUG: Screensaver GetActive() returned 0
** (gnome-fallback-mount-helper:2129): DEBUG: ConsoleKit session is active 1
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing animation options...done
** Message: applet now removed from the notification area
Initializing resize options...done
Initializing place options...done
Initializing gnomecompat options...done
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
Initializing nautilus-gdu extension
Initializing nautilus-ideviceinfo extension
Initializing unitymtgrabhandles options...done
** (nautilus:2131): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing move options...done
** (nm-applet:2130): DEBUG: old state indicates that this was not a disconnect 0
Initializing workarounds options...done
Initializing snap options...done
Initializing grid options...done
Initializing mousepoll options...done
Initializing wall options...done
** Message: using fallback from indicator to GtkStatusIcon
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
I/O warning : failed to load external entity "/home/robert/.compiz/session/104881231e85fdb5ad132716928848875700000020200038"
Initializing session options...done
Initializing fade options...done
Initializing ezoom options...done
Initializing scale options...done
WARN  2012-01-21 10:08:11 glib.glib-gobject <unknown>:0 invalid (NULL) pointer instance

Screen geometry changed:
   0x0x1600x900

unity-panel-service: no process found
Initializing unityshell options...done
Starting unity-window-decorator
DEBUG 2012-01-21 10:08:12 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1600 h=900
** Message: moving back from GtkStatusIcon to indicator
Setting Update "main_menu_key"
Setting Update "run_key"
** (process:2249): DEBUG: Telepathy Indicator started

** (process:2270): WARNING **: recent-manager-provider.vala:125: Desktop file for soffice was not found
** (nautilus:2131): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-01-21 10:09:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-01-21 10:09:13 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-01-21 10:09:13 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
sh: dropbox: not found
** (process:2270): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

```

---

### Post by biosol on 2012-01-21
After running the above command, rebooted the laptop and it found errors again, now says,

Errors were found while checking the disk drive for /.

Fix, Ignore, Skip, Manual     Select F for fix,  then /tmp is not ready yet or not present.  The drive is now working away.

Any more direction as to what to do next appreciated.  (Would rather not try re installing, but may end up doing that).

Thanks

---

### Post by dino99 on 2012-01-21
As per the log above:
- you have tweaked the system ( no more a genuine one)
- dropbox might conflict with compiz/unity
- maybe some bluetooth issues too

So do some cleanings via synaptic:

sudo apt-get install synaptic (if not done yet)
sudo synaptic

- search & purge ALL the packages related to: dropbox, ubuntu-desktop, compiz, unity
- update the archives
- then reinstall: compiz, unity-2d & 3d, ubuntu-desktop

close synaptic then reboot

note: if some non genuine package(s)/archive(s) have been activated, then deactivate them first before doing the above tweaks.

---

### Post by biosol on 2012-01-21
Yes, I did install the cpu freq app from a different repo, and also installed Gnome.  Have also see those bluetooth messages on shutdown I believe.

This line makes me nervous.  Don't have any experience on synaptic.  Not sure how to tell what's a non genuine package/archive or how to activate/deactivate them.

Pretty much know how I want the system set up now, so am thinking about just reinstalling, updating and adding the few things I really used.  Nvidia driver, indicator-cpufreq, google chrome 64 bit beta, and standard programs like virtualbox, filezilla, etc.

I did try out putting the Gnome environment back on, maybe that started messing things up.

You think there's actual physical damage on the disk or it's just corruption that would be cleared out by a reinstall?

---

### Post by biosol on 2012-01-21
Humm/interesting.  Used Gparted to delete the swap and linux partition and tried re installing.  The installer has crashed 2 times in a row...

Guess I'll try to do a Windows system restore.  Maybe the disk is dying??

Anyone know how to get the Windows to redo the boot loader for Win only?

---

### Post by Old_Grey_Wolf on 2012-01-21
> **biosol said:**
> 
You think there's actual physical damage on the disk or it's just corruption that would be cleared out by a reinstall?

If you use gparted to reformat the disk it will flag bad sectors and not use them. Then you can do a fresh install. If the disk is going bad then the problem may reoccur.

---

### Post by biosol on 2012-01-21
Ok, am trying that now.  Created a linux swap and ext4 partitions with Gparted.  Downloaded and burned a new copy of 11.10 64.  Will try it out.

Marking sectors as bad and not using them, I was hoping/thinking that's what was happening when it "fixed" the errors.  I guess not.

---

### Post by Old_Grey_Wolf on 2012-01-21
> **biosol said:**
> 
Anyone know how to get the Windows to redo the boot loader for Win only?

To restore the Windows 7 boot loader, boot with your Windows 7 recovery disc, assuming you have made one. Then get to the command prompt, I can't remember without trying how to do so. Then, type in the following commands one at a time:

```
bootrec /fixmbr

bootrec /fixboot
```

Then reboot.

---

### Post by Old_Grey_Wolf on 2012-01-21
biosol,

You are changing the direction you are using to solve your problem faster than I can keep up with you. I will go to sleep and check in the morning to see if you solved the problem or if there is something I can suggest to help you.

---

### Post by biosol on 2012-01-21
Thanks Old Gray Wolf, the information for both directions is helpful.  Sorry for the inconsistency.  I am now deciding what OS is really best for the system and not my hobby'ing.

I'll let you know which way it goes.  Much thanks!

---

### Post by Old_Grey_Wolf on 2012-01-21
OK,

Gute Nacht.

However; though I can't be certain without physical access to the computer, I think your disk may be failing.

---

### Post by biosol on 2012-01-21
Old Gray Wolf, thank you very much for the help.  I decided to just convert the laptop back to a dedicated Win7 system.  The Windows commands you provided did the trick and I used Windows to extend the partition space.

I am still using an Ubuntu 10.4.3 LTS desktop at work.  I much prefer the Ubuntu fonts over the Windows fonts and hope I can get a current hardware based system to use Ubuntu on in the near future.

My laptop is a 1st Gen Core i7 so I really wanted to see/use Ubuntu to experience it.  It was a good 8 months, but the files system issues are starting to affect my work and taking time away from my book writing on the weekend :p


Best regards-

---

