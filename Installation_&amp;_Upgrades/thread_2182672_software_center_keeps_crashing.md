---
title: "software center keeps crashing"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2013-10-22
This is getting a bit annoying...

Complete fresh install of Ubuntu Gnome 13.10.

When launched, the software center starts to launch, then crashes.

I get this when launched in terminal..
```
baldrick@baldrick:~$ software-center
2013-10-22 18:29:08,093 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-10-22 18:29:08,319 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.GLib.UnmappedError.GeoclueErrorQuark.Code1: Geoclue master client has no usable Address providers'
2013-10-22 18:29:08,563 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-10-22 18:29:08,564 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-10-22 18:29:08,568 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-10-22 18:29:08,568 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-10-22 18:29:08,636 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-10-22 18:29:10,521 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/utils.py', 271, 'get_title_from_html')'
2013-10-22 18:29:10,521 - root - WARNING - failed to parse: '<div style="background-color: #161513; width:1680px; height:200px;">
*<div style="background: url('/site_media/exhibits/2013/09/AAMFP_Leaderboard_700x200_1.jpg') top left no-repeat; width:700px; height:200px;"></div>
</div>' ('ascii' codec can't encode character u'\xa0' in position 70: ordinal not in range(128))

(software-center:3955): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 1670 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

```

Looks like something to do with X?

EDIT: Tried re-installing it with no luck. Gnome Tweak Tool seems to have the same problem, just crashes once you make another associated window active. 
Any help would be greatly appreciated!

---

### Post by ibjsb4 on 2013-10-22
For what its worth, I some hits here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Gdk-ERROR+**%3A+The+program+%27software-center%27+received+an+X+Window+System+error&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Gdk-ERROR+**%3A+The+program+%27software-center%27+received+an+X+Window+System+error&sa=Search&cof=FORID:9)

Good luck

---

### Post by Cosmik Debris on 2013-10-22
It happened to me as well with software-center.
This is an install that was upgraded from 13.04 yesterday (not sure if that is causing the problem)

However, I then started software-center as root using sudo, and the crash didn't reoccur.
The crash does not re-occur anymore, even if I start software-center as non-root user.

Hope it helps

---

### Post by Baldrick_NZ on 2013-10-23
> **Cosmik Debris said:**
> 
However, I then started software-center as root using sudo, and the crash didn't reoccur.
The crash does not re-occur anymore, even if I start software-center as non-root user.

Hope it helps

Hmmm, tried that but still a no-go. Seems to work ok sometimes though when you double-click on a deb file downloaded from the internet. But not when you either click the icon or ```
sudo software-center
```
Any further help would be very much appreciated!

---

### Post by varunendra on 2013-10-23
Any specific reason to stick with SC? It's mostly a matter of preferences, and I like using Synaptic over SC, mainly for its speed, and partly for its extra options.

If you wish to try that -
```
sudo apt-get install synaptic
```

---

### Post by Baldrick_NZ on 2013-10-23
> **varunendra said:**
> Any specific reason to stick with SC? It's mostly a matter of preferences, and I like using Synaptic over SC, mainly for its speed, and partly for its extra options.

If you wish to try that -
```
sudo apt-get install synaptic
```

I've already got synaptic installed, and it works fine as does terminal. I guess It's just good to know that if I ever do need it, it's there ready to go.

I also install for new users, and while both synaptic and terminal are awesome to the regular user, SC would better suit these users better.

Googling around, it does seem this issue is fairly widespread in 13.10. Might just be a case of waiting for an update...

Cheers.

---

### Post by varunendra on 2013-10-23
> **Baldrick_NZ said:**
> Googling around, it does seem this issue is fairly widespread in 13.10. **Might just be a case of waiting for an update**...

Indeed. And I believe that is the case with all new releases, with exception of maybe a few LTS ones - a huge wave of bugs and broken systems as it comes out, then everything gradually settling down with subsequent updates..

I've made it a habit to wait at least a month or two before upgrading my 'working' system to the newer (or newest release).

---

