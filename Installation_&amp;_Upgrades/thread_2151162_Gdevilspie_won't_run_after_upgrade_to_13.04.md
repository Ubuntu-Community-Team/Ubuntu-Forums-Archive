---
title: "Gdevilspie won't run after upgrade to 13.04"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by Lateralus138 on 2013-06-03
Hello, I recently upgraded to 13.04 and there was a few small problems which I fixed from past experience, but I can't seem to get Gdevilspie to run. I tried uninstalling and reinstalling and didn't work. I know devilspie still works because all the things it controls still work. I tried running it from terminal and I get this:

```

ian@Hell:~$ gdevilspie 
Traceback (most recent call last):
  File "/usr/bin/gdevilspie", line 893, in <module>
    MainWindow = RulesListWindow()
  File "/usr/bin/gdevilspie", line 374, in __init__
    self.UpdateAutostartStatus()
  File "/usr/bin/gdevilspie", line 545, in UpdateAutostartStatus
    if (os.path.exists(xdg.DesktopEntry.xdg_config_home + "/autostart/devilspie.desktop")):
AttributeError: 'module' object has no attribute 'xdg_config_home'



```

with gksudo:
```

(gksudo:28749): Gtk-WARNING **: Theme directory 22x22/action of theme glass has no size field


(gksudo:28749): Gtk-WARNING **: Theme directory 22x22/status of theme glass has no size field

    MainWindow = RulesListWindow()
  File "/usr/bin/gdevilspie", line 374, in __init__
    self.UpdateAutostartStatus()
  File "/usr/bin/gdevilspie", line 545, in UpdateAutostartStatus
    if (os.path.exists(xdg.DesktopEntry.xdg_config_home + "/autostart/devilspie.desktop")):
AttributeError: 'module' object has no attribute 'xdg_config_home'

```


Ok I am so sorry for wasting forum space I figured it out... It is a known bug and when I first searched I didn't find anything, but if you comment out line 374 in the program it works!

---

### Post by ClientAlive on 2014-02-10
> **Lateralus138 said:**
> Hello, I recently upgraded to 13.04 and there was a few small problems which I fixed from past experience, but I can't seem to get Gdevilspie to run. I tried uninstalling and reinstalling and didn't work. I know devilspie still works because all the things it controls still work. I tried running it from terminal and I get this:

```

ian@Hell:~$ gdevilspie 
Traceback (most recent call last):
  File "/usr/bin/gdevilspie", line 893, in <module>
    MainWindow = RulesListWindow()
  File "/usr/bin/gdevilspie", line 374, in __init__
    self.UpdateAutostartStatus()
  File "/usr/bin/gdevilspie", line 545, in UpdateAutostartStatus
    if (os.path.exists(xdg.DesktopEntry.xdg_config_home + "/autostart/devilspie.desktop")):
AttributeError: 'module' object has no attribute 'xdg_config_home'



```

with gksudo:
```

(gksudo:28749): Gtk-WARNING **: Theme directory 22x22/action of theme glass has no size field


(gksudo:28749): Gtk-WARNING **: Theme directory 22x22/status of theme glass has no size field

    MainWindow = RulesListWindow()
  File "/usr/bin/gdevilspie", line 374, in __init__
    self.UpdateAutostartStatus()
  File "/usr/bin/gdevilspie", line 545, in UpdateAutostartStatus
    if (os.path.exists(xdg.DesktopEntry.xdg_config_home + "/autostart/devilspie.desktop")):
AttributeError: 'module' object has no attribute 'xdg_config_home'

```


Ok I am so sorry for wasting forum space I figured it out... It is a known bug and when I first searched I didn't find anything, but _**if you comment out line 374 in the program it works**_!

Thank you so very, very much for telling what the soln is. As of today's date, I commented out line 374 as you say and gdevilspie lanuches and appears to work just fine. My terminal output before commenting that line out was identical to what you show though.

Peace
Jake

PS : For anyone new to ubuntu or the command line, a good way to accomplish commenting the line out is...

( 1 ) Open a terminal with ctrl + alt + t
( 2 ) Type sudo gedit /usr/bin/gdevilspie and press enter
( 3 ) Enter your password and press enter
( 4 ) If you do not see line numbers, click the edit menu in gedit, then click preferences ( look for the check box "show line numbers" and check it
( 5 ) Scroll down to line 374 and put a # symbol to the far left of the line ( prefix the line with # )
( 6 ) Press ctrl + s to save the changes and then exit out of gedit ( maybe give it a few seconds to finish saving before exiting though )
( 7 ) You are done with the fix, you can now launch gdevilspie and it ( should ) work.

Note : As programs/applications do change over time, this fix may not work in the future and it may not work for other problems. If your terminal output matches what Lateralus138 shows ( like mine did ) it probably will work. Give it a shot, you can always reverse the change if it doesn't work.

-----------------------------------------------------------------------------------------------------------

Edit : I just discoverd that, while gdevilspie will launch after commenting out line 374, it will not autostart the daemon when you check the box for it in it's gui ( bottom of the window in gdevilspie ). I don't know whether that line being commented out is the cause of it or not; but having it's daemon autostart/work is something I have to have. If I find a soln I'll post it. In the mean time, is there someone here that knows how to fix this?

Thanks

---

### Post by kemal-karabeg on 2014-04-13
Well I have exactly the same problem.I am using Ubuntu 14.04 beta 2 gnome and trying to accomplish the same thing.But,uncommenting that 374 line is causing gdevilspie daemon to not autostart.Any solution to this??

---

### Post by kannehana on 2014-05-11
> **kemal-karabeg said:**
> Well I have exactly the same problem.I am using Ubuntu 14.04 beta 2 gnome and trying to accomplish the same thing.But,uncommenting that 374 line is causing gdevilspie daemon to not autostart.Any solution to this?? I upgraded from Ubuntu 12.04 LTS to 14.04 LTS and can confirm that the problem still persists. Sad, since devilspie is such a useful tool and gdevispie helps to use it !
[FONT=Courier New]apt-cache policy devilspie
**devilspie**:
  Installed: **0.23-2**
  Candidate: 0.23-2
apt-cache policy gdevilspie
**gdevilspie**:
  Installed: **1:0.5-3**
  Candidate: 1:0.5-3
apt-cache policy python-xdg
**python-xdg**:
  Installed: **0.25-4**
  Candidate: 0.25-4[/FONT]
From [http://pyxdg.readthedocs.org/en/latest/basedirectory.html]("http://pyxdg.readthedocs.org/en/latest/basedirectory.html") we learn that 
```
xdg.BaseDirectory.xdg_data_dirs
```
Editing the [FONT=Courier New]/usr/bin/gdevilspie[/FONT] script (make a copy first !):, after
```
import xdg.DesktopEntry
```add
```
import xdg.BaseDirectory
```and then, using the Replace function of your editor (ex. [FONT=Courier New]gedit[/FONT]), replace all occurrences of
```
xdg.DesktopEntry.xdg_config_home
```with 
```
xdg.BaseDirectory.xdg_config_home
```Or, if you prefer patching, [here's the 'diff -u' patch file]("https://dl.dropboxusercontent.com/u/62585371/linux/gdevilspie-0.5.-3_ubuntu14.04.patch") of my modifications which are doing the above.
Check that you have indeed **0.5-3** version of gdevilspie package (see above).
Move the above patch file into the [FONT=Courier New]/usr/bin[/FONT] directory ([FONT=Courier New]mv[/FONT] as root, or with [FONT=Courier New]sudo mv[/FONT], as you prefer) and then patch as in
[FONT=Courier New]root@clevo:/usr/bin#[/FONT]
with
```
patch -b -V t < gdevilspie-0.5.-3_ubuntu14.04.patch
```
You would have
[FONT=Courier New]-rwxr-xr-x 1 root root 38292 May 11 12:38 [COLOR="#00FF00"]gdevilspie[/COLOR]
-rwxr-xr-x 1 root root 38259 May 11 12:38 [COLOR="#00FF00"]gdevilspie.~1~[/COLOR][/FONT]
Give it a try (or wait until it gets fixed first in the repository and then in the distribution).

**BTW**, you can autostart devilspie yourself, if you have already working rules in [FONT=Courier New]~/.devilspie[/FONT] :
Either use [FONT=Courier New]cinnamon-session-properties[/FONT] (type *startup* in the Unity lense or start from command line), or simply add the following file, named [FONT=Courier New]devilspie.desktop[/FONT] in [FONT=Courier New]$HOME/.config/autostart[/FONT] directory:
```
[Desktop Entry]
Type=Application
Name=Devilspie
X-GNOME-Autostart-enabled=true
Exec=devilspie
```

**BTW(2) rant**: the new login method to this forum through the now going-away-anyway-UbuntuOne is ridiculously complicated and one needs to be really determined to contributre ! All good things are fading under the business logic.

---

### Post by debbie3 on 2015-02-18
[QUOTE]> **Lateralus138 said:**
> 
[CODE]
ian@Hell:~$ gdevilspie 
Traceback (most recent call last):
  File "/usr/bin/gdevilspie", line 893, in <module>
    MainWindow = RulesListWindow()
  File "/usr/bin/gdevilspie", line 374, in __init__
    self.UpdateAutostartStatus()
  File "/usr/bin/gdevilspie", line 545, in UpdateAutostartStatus
    if (os.path.exists(xdg.DesktopEntry.xdg_config_home + "/autostart/devilspie.desktop")):
AttributeError: 'module' object has no attribute 'xdg_config_home'

Ok I am so sorry for wasting forum space I figured it out... It is a known bug and when I first searched I didn't find anything, but if you comment out line 374 in the program it works!

Just installed linux mint 17.0. cinnamon 64 bit and I got the same problem. Gdevilspie would not open (got a spinning icon that then disappeared). Glad to say that commenting out line 374 in the program it worked. 
Many Thanks

---

### Post by oldos2er on 2015-02-18
Old thread closed.

---

