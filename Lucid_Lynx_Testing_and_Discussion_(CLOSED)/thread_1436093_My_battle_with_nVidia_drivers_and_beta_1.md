---
title: "My battle with nVidia drivers and beta 1"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by taylorkh on 2010-03-22
I have run the alphas a little as virtual machines in VMWare and on an old Pentium 4 machine.  So now that beta 1 is out I decided to try it on my main desktop.  I have been struggling with 9.10 64 bit, nVidia and Flash (and a host of other annoying issues in 9.10).  After 3 abortive attempts to automagically install and configure the nVidia drivers I decided to do it manually as had been recommended is a couple of posts.  Here is my story:

Hardware:
Dell Studio XPS 8000
Intel i7-860 Quad Core Processor
8 GB RAM
nVidia GeForce GT220 1 GB Video Card (Dell OEM)
Samsung SyncMaster 932B on HDMI (monitor 0)
Acer X223W on DVI (monitor 1)

Installed Lucid Beta 1 64 bit on 320 GB drive as follows
/dev/sda1 20 GB /
/dev/sda2 10 GB swap (real big as I plan to test suspend to disk)
/dev/sda3 the rest /data (used for backups etc.)
Installed all updates through 3/21/10
The machine runs OK except
- the fan on the GPU runs at about 37,000 RPM
- I have only one monitor active
created snapshot of /dev/sda1 with g4l

manually installed nVida driver sudo apt-get install nvidia-current
ran sudo nvidia-xconfig
saved a copy of xorg.conf as xorg.conf.step1
Restarted

When the system came back...
- the GPU fan slowed to a reasonable, quiet speed
- I was able to login and find one monitor 0 displaying my desktop as expected

I then ran sudo nvidia-settings
- shows the  OS as Linux-x86_64
- NVIDIA Driver version 195.36.15

I went to the X Server Display Configuration panel
- the second monitor is shown as Disabled

I Configured it to Twinview and saved the X config file.  I also made a copy to xorg.conf.step2.  I then Restarted.

When the machine came back up 
- the system barked about needing to fsck something but it didn't do it (I see this occasionally)
- the fan speed is OK
- monitor 1 is lighted and the login panel is displayed on monitor 1
- after login I have my normal desktop on monitor 0 and a blank area on monitor 1
- I can move items between the monitors (I guess this is what Twinview is supposed to do - it is not what I wish to use)

I again run sudo nvidia-settings.
- change Display Device to Separate X screen
- set the second X Screen Position to Right of (screen 0)
- save config and make copy as xorg.conf.step3
- Restart

And here we go - login dialog is on screen 0 so I login
Monitor 0 
- There are TWO show desktop icons
- TWO desktop switchers
- TWO trash cans
- TWO of everything in the notification area except for a Crash Report Detected icon and the Wired Network icon and the Me icon (with the Busy, Available etc.)
Monitor 1
- looks OK except that there are 4 desktops shown in the switcher

So I Restart again

I get a message re. Previous attempts to boot this machine failed... - can't catch the rest (I get this on occasion also even though it has never failed to boot).
Login dialog on screen 0 so I login
Except for the 4 desktops shown in the selector on screen 1 all looks well.  The dupes are gone.

I Restart again and login again.  All looks OK.

Now I do a Shutdown/switch off. When it comes back up and I login.

- Screen 0 ERROR - The panel encountered a problem while loading OAFIID:GNOME_Notification_Area_Applet Do you want to delete the applet from your configuration [Don't Delete] [Delete]
- Screen 1 ERROR - Notification Area has quit unexpectedly. If you relaod a panel object, it will automatically be added back to the panel. [Don't Reload] [Reload]
 
All items appear to be present on both screens.  All notification items are present.

I choose [Don't Delete] - clears error dialog and [Reload].  Reload simply brings back the same error so I [Don't Reload].  All looks OK.

So I restart and login.  All looks OK.

I Shut Down and switch off. I then power back on and login.  This time there are no errors. I try several other restarts and shut downs - cannot reproduce the issues with the Notification Area Applet.

What I conclude from the above experience is:

- Somehow the Notification Panel Applet somehow got configured to load twice on screen 0.
- It did in fact load things twice - the configuration error was cleared temporarily after the Restart
- After the first Shut Down the configuration error came back - this time the system processed it differently - thus the Error messages
- After clearing the Error messages the configuration problem was permanently(?) fixed

I will do some comparison of the xorg.conf file I backed up along the way and post anything interesting which I find.

Now I guess I need to load Flash and see what breaks.

Ken

---

