---
title: "Gnome starting multiple"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2009-09-21
I have posted on this problem before, but so far there has been no resolution. If I turn off 'show desktop' in gconf-editor > apps > nautilus > preferences, I get an apparently infinite number of "starting file manager" icons in the bottom panel. If I don't turn off 'show desktop', I get a desktop that shows everything in ~. 
Is this a known problem, or a configuration problem in my system?  Any help would be appreciated, as gnome isn't really useable this way.  Thanks.

---

### Post by mc4man on 2009-09-21
maybe double check in gconf (same place) and see if 'desktop_is_home_directory' is enabled

---

### Post by doctordruidphd on 2009-09-21
> maybe double check in gconf (same place) and see if 'desktop_is_home_directory' is enabled 
OK, there is a problem here. Whether I check the "desktop_is_home_directory" box or not, ~ is displayed. There is nothing in the ~/Desktop directory (no normal or hidden files), so when the box is unchecked, there should be nothing.

---

### Post by mc4man on 2009-09-22
> OK, there is a problem here.

That would certainly seem to a problem.

So the appearance is that your desktop is now your home and your home is just another directory..?

Personally not having a clue how to fix, I think I'd first confirm where ~ really is
Try doing something that would indicate, like a mv or cp command of something to ~ and see where it goes.
Or even for instance a   apt-get source gedit, the gedit source will be dl'ed and unpacked in your  ~ dir. by default

If Stuff goes to desktop well I did't know, if it goes to your ~ then I still don't know but maybe mv everything that belongs there from desktop...?

---

### Post by Sophont on 2009-09-22
> **mc4man said:**
> 
Personally not having a clue how to fix, I think I'd first confirm where ~ really is
Try doing something that would indicate, like a mv or cp command of something to ~ and see where it goes.
Or even for instance a   apt-get source gedit, the gedit source will be dl'ed and unpacked in your  ~ dir. by default

1. Open terminal
2. cd ~
3. pwd

The second step should be redundant.

---

### Post by doctordruidphd on 2009-09-22
Hello, and thanks for the replies.
The home directory is where it should be. 
pwd shows my home directory, and ~ references it correctly. The problem is, I think,  somewhere in nautilus, because if I do a 'pkill nautilus', the icons on the desktop go away, and then come right back. I checked the %gconf.xml in .gconf>apps>nautilus>preferences:
```
<?xml version="1.0"?>
<gconf>
        <entry name="exit_with_last_window" mtime="1253581628" type="bool" value="true"/>
        <entry name="media_automount_open" mtime="1253581237" type="bool" value="false"/>
        <entry name="media_automount" mtime="1253581360" type="bool" value="false"/>
        <entry name="click_policy" mtime="1253581171" type="string">
                <stringvalue>single</stringvalue>
        </entry>
        <entry name="desktop_is_home_dir" mtime="1253582962" type="bool" value="false"/>
        <entry name="media_autorun_never" mtime="1253581278" type="bool" value="true"/>
        <entry name="show_advanced_permissions" mtime="1252515387" type="bool" value="true"/>
        <entry name="always_use_browser" mtime="1253581210" type="bool" value="true"/>
        <entry name="always_use_location_entry" mtime="1253581675" type="bool" value="true"/>
        <entry name="show_desktop" mtime="1253582933" type="bool" value="true"/>
        <entry name="navigation_window_saved_maximized" mtime="1253583380" type="bool" value="false"/>
        <entry name="navigation_window_saved_geometry" mtime="1245977925" type="string">
                <stringvalue>800x550+377+205</stringvalue>
        </entry>
</gconf>

```

Notice that "desktop_is_home_dir" is set to false. Either nautilus is ignoring that (why?) or there is some other config file overriding it, not sure where. Or nautilus is broken; I tried 'sudo dpkg-reconfigure nautilus' and also apt-get reinstall, neither fixed it.
Thanks to all for ideas and help. This did work at one time, and later broke.

---

