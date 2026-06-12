---
title: "Normal Upgrade - Certain System Modules now Won't Work"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by myke on 2007-04-01
Hi. .... It seems lately that every other normal update I do cause something to malfunction.   I'm using edgy with KDE my main desktop.   I have both 'kcontrol center' and the newer 'system settings' installed and have for some time though I mainly rely on 'system settings' as my main avenue for tweaking control panel type modules.

Well ... everything was fine until two days ago when I followed the normal updates from Adept Updater.  It updated about 25 packages and everything for the most part is running smoothly.  However, there are now 4 modules within the system settings / kcontrol center that no longer work.

They are:  

user management
monitor & display
disk & file systems
system services

If I use kcontrol center to open any of these, it simply goes back to the main kcontrol center screen.  When I use System Settings, I get the exact same error when trying to open any of the 4 modules above:

[I]The module User Management could not be loaded

The diagnostics is:

Possible reasons:

 * An error occurred during the last KDE upgrade leaving an orphaned control module.
 * You have old third party module lying around.

Check these points carefully and try to remove the module mentioned in the error message.  If this fails, try  contacting your distributor or packager.[/I]

The error messages above are the same except for the module name of whichever of the one I am trying to load is in the first line.   I used User Management as an example.

Notice that no diagnostics are actually listed.

I do not want to attempt removing any of those modules as I think it might royally f'up something worse.   Each of the 4 that do not work are vital in my opinion so I do not know what to do.   

As I am still quite the novice when it comes to any sort of poking around and changing core settings, please give any advice as to what might be causing this.

---

### Post by myke on 2007-04-01
Someone over at the kde-forum.org put me in the right direction in getting this problem fixed.  Apparently it didn't have anything to do with the normal adept upgrades but a laptop power manager i had replaced.   I'll quote the solution below in case this might help anyone out.  BTW -- imho, the "power manager" applet for laptops really sucks compared to "kpowersave" applet.   

User jucato suggested the following:

*Try reinstalling the kde-guidance package. Those 4 modules are from that package. *

I did and had responded in kind:

[I]Thanks a lot, jucato. I used Synaptic (I use it interchangeably with Adept -- no preference -- like them both) to reinstall the kde-guidance package and those modules work perfectly now. I think now that it actually had nothing to do with the recent updates thru ubuntu. Around the same time this all happened, I had just removed the "power manager" in favor of installing "kpowersave" as the power manager applet kept trying to shut my laptop down as it kept thinking the lid was closed when it wasn't. So I went to kpowersave, which, in my opinion, is slicker and better anyway. But power manager was tied into the kde-guidance package I discovered when looking to uninstall it as it is named "kde-guidance-powermanager". I still don't know why they are interconnected as they are dependent on one another but when i did the uninstall to the kde-guidance-powermanager package, something must have went awry with the settings of modules within the kde-guidance package. Reinstalling that package as you suggested got everything working perfectly again. And I can keep using kpowersave as my laptop's power manager of choice.

Thanks again. I doubt the solution would have ever dawned on me. It's nice that folks like you around the forums can recognize such things. I wouldn't have known at all that those four packages happen to all be installed together under kde-guidance.[/I]

---

### Post by Al_maverick on 2007-04-20
I have the very same problem, but if I try to uninstall kde-guidance or kde-guidance-powermanager, it also tries to uninstall kubuntu-desktop.

At that point I decided not to proceed. :D

Do you think that a dpkg-reconfigure of kde-guidance would be enough?

---

### Post by myke on 2007-04-20
> **Al_maverick said:**
> I have the very same problem, but if I try to uninstall kde-guidance or kde-guidance-powermanager, it also tries to uninstall kubuntu-desktop.

At that point I decided not to proceed. :D

Do you think that a dpkg-reconfigure of kde-guidance would be enough?


I uninstalled kde-guidance-powermanager but you really need to keep kde-guidance as it has some system / control panel type modules included.  Unistalling kde-guidance-powermanager should do the trick just to get rid of that one applet/package.   It did the trick for me & I'm using kpowersave alone just fine now.

One thing of note, though, I actually did recently do an uninstall of kubuntu-desktop as it actually isn't fully tied to kde itself and won't actually (or shouldn't) mess up being able to use kde as your default desktop.  It's only tied to a few packages.  I removed it after removing kontact and kmail which were auto installed (for some reason I don't know) when I upgraded to Feisty from Edgy.   Those were the only packages that actually depended on kubuntu-desktop on my system.  If it says to uninstall that, it should also say you'll have to uninstall other packages if they are dependent upon it to be installed and work. 

but I'm no expert ... just been my experience ...

---

### Post by CyberAngel on 2007-08-05
Hello, 

I am using feisty and I have the same problem only on the "module User Management".

I did a reinstall of kde-guidance, kde-systemsettings and kcontrol but the problem still exists!

From the information (apt-cache show) of kde-guidance I read this:

```
Description: collection of KDE system administration tools for GNU/Linux
 Guidance currently consists of four programs designed to help you
 look after your system:
  o  userconfig - User and Group administration
  o  serviceconfig - Service/daemon administration
  o  mountconfig - Disk and filesystem administration
  o  displayconfig - Screen and display configuration
 .
 These tools are available in KDE Control Center, System Settings
 or can be run as standalone applications.

```

If I run these Applications manually they all start OK except the userconfig that I get the following errors on the console:

```
cyber@aurora:~$ userconfig
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/bin/userconfig", line 1713, in <module>
    userconfigapp = UserConfigApp()
  File "/usr/bin/userconfig", line 267, in __init__
    self.admincontext = unixauthdb.getContext(isroot)
  File "/usr/share/python-support/kde-guidance/unixauthdb.py", line 74, in getContext
    return PwdContext(editmode)
  File "/usr/share/python-support/kde-guidance/unixauthdb.py", line 744, in __init__
    newgroupobj._initString(line)
  File "/usr/share/python-support/kde-guidance/unixauthdb.py", line 1079, in _initString
    (self._groupname,self._encpass,self._gid,self._memberids) = tuple(line.strip().split(":"))
ValueError: need more than 3 values to unpack
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/userconfig", line 1713, in <module>
    userconfigapp = UserConfigApp()
  File "/usr/bin/userconfig", line 267, in __init__
    self.admincontext = unixauthdb.getContext(isroot)
  File "/usr/share/python-support/kde-guidance/unixauthdb.py", line 74, in getContext
    return PwdContext(editmode)
  File "/usr/share/python-support/kde-guidance/unixauthdb.py", line 744, in __init__
    newgroupobj._initString(line)
  File "/usr/share/python-support/kde-guidance/unixauthdb.py", line 1079, in _initString
    (self._groupname,self._encpass,self._gid,self._memberids) = tuple(line.strip().split(":"))
ValueError: need more than 3 values to unpack

```

Anyone that has been in front of this problem and solved it? :roll:

---

