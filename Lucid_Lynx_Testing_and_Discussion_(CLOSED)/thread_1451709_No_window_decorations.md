---
title: "No window decorations"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rhill on 2010-04-10
Running Lucid Lynx 10.04, Kernel Linux 2.6.32-19-generic, GNOME 2.30.0, 64-bit version.
Intel integrated graphics H55.

I installed the latest updates a few minutes ago. I usually update every single day, but this one time I skipped one day. So after I updated, I was asked to restart the computer, and when I confirmed to do so, the computer shutdown, but the Ubuntu logo seen at shutdown stayed there for ages. I figured I needed to perform a manual reboot. After the computer restarted, and I logged in, all seem fine *except* for the fact that I have no window decorations whatever application launched: No title bar, no close button, no status bar, no scroll bars, etc.

I also noticed I am down to one single workspace whereas before it had always been two.

[Edit] Something else I notice, if I go in the "Appearance" applet, in the "Visual Effects" tab all options are disabled, even the "None" one.

[Edit] Also noticed that if I run Preference->Windows, I receive the message "Windows manager 'unknown' has not registered a configuration tool". So I gather there is no Window manager. I still don't know how to fix this though.

I have no idea how to proceed from here to fix this problem.

---

### Post by cariboo on 2010-04-10
Try pressing Alt-F2 and typing:

```
metacity --replace
```

To see if that solves the problem.

---

### Post by kalmos on 2010-04-10
I have exactly the same problems as described above, and I'm on a 64bit, too.

I also have an additional problem:
My keyboard doesn't work. This is strange, because here I am typing. Specifically, it does not work in any normal typing location right after I login, like the address bar for Google Chrome or in gedit. However, I noticed that I could type into a little search box while pidgin has focus. So I copied and pasted text from there in order to arrive at this forum. Ugh. Now, my keyboard seems to work normally again, in the address bar for Google Chrome and in gedit. I think it started working immediately after I clicked the reply button on this page, but it's hard to tell.

I would greatly appreciate some help to fix these issues.

**EDIT:** cariboo907 posted before I could finish typing. Thanks, that command puts all the window decorations back on my windows.My keyboard doesn't work...

---

### Post by rhill on 2010-04-10
> **cariboo907 said:**
> Try pressing Alt-F2 and typing:

```
metacity --replace
```To see if that solves the problem.

From another thread, I found out I needed to install compiz. All is back to normal. Wish I had it figured out before posting, sorry.

---

### Post by kalmos on 2010-04-10
I have to close pidgin so that my keyboard works in the other windows. This is frustrating.

This command puts decorations back on my windows, and the keyboard behaves normally again. However, the decorations go away as soon as I close my terminal, so I still have a problem.
```
metacity --replace
```

Also, I tried installing compiz as the op suggested, but it's already installed. I'm not sure what's wrong...

```
sudo apt-get install compiz
[sudo] password for kalmos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
The following packages were automatically installed and are no longer required:
  python-matplotlib kakasi-dic odbcinst1debian1 python-matplotlib-data kakasi
  odbcinst unixodbc python-tk python-tz python-sqlalchemy python-pysqlite2
  python-dateutil python-pyparsing
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by petronell on 2010-04-11
I have exactly the same issue on the Lucid beta following the updates this morning.

metacity --replace fixes this for as long as I have the terminal window minimised, as soon as I close the window goes back to the bug.

I also have compiz installed.

thanks,

dave

---

### Post by Elessar_81 on 2010-04-11
I had the same Problems.
Do you have the Package compiz-gnome installed? It wasn't in my case and i had no Window decoration. I installed it and everything is back to normal.

I hope i can help

---

### Post by eriro on 2010-04-11
Installing compiz-gnome solved it for me. Tanks a lot!

---

### Post by gbear14275 on 2010-04-11
Running into the same issue.  No window decorations and sometimes my keyboard is not responsive.

metacity --replace resolves the issue but only as long as the terminal is open.

Anyone aware of how to resolve this issue long term?  I can try installing compiz-gnome but would rather run without it.

Thanks
Garrett

Update: installing compiz-gnome alone did not resolve the issue.  Changing my appearance visual effects settings from none to normal did though.

---

### Post by Uncle Spellbinder on 2010-04-11
> **gbear14275 said:**
> ...Anyone aware of how to resolve this issue long term?  I can try installing compiz-gnome but would rather run without it.

The post above yours might be the answer. Not sure why you wouldn't want to run it though?...> **eriro said:**
> Installing compiz-gnome solved it for me. Tanks a lot!

---

### Post by flmommens on 2010-04-19
I had the same problem.
But I couldn't change the keyboard focus from firefox to other applications. So no way to execute 'metacity --replace'. And compiz and gnome-compiz were correctly already installed (I checked that through a text console with Ctrl-Alt-F1). I finally went to System -> Appearance Preferences -> Visual Effect and changed None to Normal which corrected the issue.

---

### Post by flmommens on 2010-04-19
> **gbear14275 said:**
> 
Update: installing compiz-gnome alone did not resolve the issue.  Changing my appearance visual effects settings from none to normal did though.

This solved the issue for me too but the setting is not saved and the problem reappear after rebooting.

---

### Post by BrokeMahPC on 2010-04-21
This also happened to me - no window decorations but the keyboard was not affected (it's usb?). I had simpleccsm installed so thought it might be a clash with that - uninstalled it and rebooted - no change.

I then found that setting visual effects to none brought the windows decs back.
I went to compiz config setting manager->preferences->reset to defaults and rebooted. This seemed to fix it - the window decs returned and I could enable extra visual effects.

When I logged in this morning everything relating to the desktop cube was unticked even though when I logged off last night it was all set up and working.
Under visual effects - none of the options were selected - selected extra and it stayed for a moment - then the selection returned to unselected.

Could be something to do with a graphics update - I have tried:
```
sudo aticonfig --initial -f
```to reconfig the ATI fglrx driver and it overwrites and backs up xorg - visual effects is now behaving normally - will post back if this solves it.

Edit - After the aticonfig above desktop effects is working normally. Compiz is un-ticking all the desktop cube options after a reboot. I have looked at the gconf-editor settings suggested above and below - all were as they should be.

Edit - Compiz now working after re-installing it and the CCSM and dependencies.

---

### Post by Stijndg on 2010-04-21
> **gbear14275 said:**
> Running into the same issue. No window decorations and sometimes my keyboard is not responsive.
 
metacity --replace resolves the issue but only as long as the terminal is open.
 
Anyone aware of how to resolve this issue long term? I can try installing compiz-gnome but would rather run without it.
 
Thanks
Garrett
 
Update: installing compiz-gnome alone did not resolve the issue. Changing my appearance visual effects settings from none to normal did though.
 
Hi,
 
*2 methods to do this:*
 
**#1**

Open up gconf-editor (alt-f2 and run the command gconf-editor) and then navigate to '/desktop/gnome/applications/window_manager' and change the value of "default" to "/usr/bin/compiz"

**#2**
 
Try to create a startup script.

Type in terminal sudo gedit /home/"your name"/.compiz-start.sh

Then paste these lines to file and save it:
 
#!/bin/bash
sleep 15 && compiz --replace -c emerald &
;

make script excutable
sudo chmod /home/"your name"/.compiz-start.sh
then add .compiz-start to startup programs
 
 
**Hope one of these works for you**

---

