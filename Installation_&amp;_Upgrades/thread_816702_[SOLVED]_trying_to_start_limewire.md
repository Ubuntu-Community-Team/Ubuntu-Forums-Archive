---
title: "[SOLVED] trying to start limewire"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2008-06-02
I just downlaoded and unzipped Limewire from sourceforge. 

The read me text mentions this 

[I][COLOR=Blue]You must place Sun's JRE in the path prior to launching LimeWire.

[/COLOR][/I][COLOR=Blue][COLOR=Black]I[/COLOR][/COLOR][COLOR=Blue][COLOR=Black] am running sun java V6 so that's fine, but what does the above instruction actually mean, what path and how do I do it (whatever 'it' is) :confused:

I tried running the comand as given ```
douglas@desktop:~$ sh ./runLime.sh
sh: Can't open ./runLime.sh
douglas@desktop:~$ 

``` but it won't run. 

hmmmm :([/COLOR][/COLOR][I][COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR][/I]

---

### Post by iaculallad on 2008-06-02
Try placing sudo:

```
sudo sh ./runLime.sh
```

---

### Post by tropdoug on 2008-06-02
Should have mentioned that, tried it. I also tried changing to the limewire directory first, no dice. So I think it must have something to do with the java path thing. 

I also opened a jar file using sun java 6 which came up with a host of errors. I might re do that and post the result, maybe there is something in there that will help. 

Thanks for the suggestion though

---

### Post by tropdoug on 2008-06-02
I reckon the blue highlighted one is the issue. don't know what it means though:guitar:

```
LimeWire version 4.8.1
Java version 1.6.0_03 from Sun Microsystems Inc.
Linux v. 2.6.22-14-generic on i386
Free/total memory: 3730584/5177344

[COLOR=Blue] com.limegroup.gnutella.gui.GUILoader$StartupFailedException: invalid logicrypto.jar[/COLOR]
    at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:271)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:43)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Main.java:31)

STARTUP ERROR!




FILES IN CURRENT DIRECTORY:
/home/douglas/.java
LAST MODIFIED: 1212399321000
SIZE: 4096

/home/douglas/.qt
LAST MODIFIED: 1211433879000
SIZE: 4096

/home/douglas/.aspell.en.prepl
LAST MODIFIED: 1211785653000
SIZE: 24

/home/douglas/.gtk-bookmarks
LAST MODIFIED: 1212450903000
SIZE: 116

/home/douglas/Business folders
LAST MODIFIED: 1212398938000
SIZE: 4096

/home/douglas/.kde
LAST MODIFIED: 1211433878000
SIZE: 4096

/home/douglas/.cups
LAST MODIFIED: 1212382136000
SIZE: 4096

/home/douglas/.DCOPserver_desktop_:0
LAST MODIFIED: 1212455943000
SIZE: 54

/home/douglas/.mozilla
LAST MODIFIED: 1211417598000
SIZE: 4096

/home/douglas/.Xauthority
LAST MODIFIED: 1212450896000
SIZE: 118

/home/douglas/.hplip
LAST MODIFIED: 1211424886000
SIZE: 4096

/home/douglas/.dbus-keyrings
LAST MODIFIED: 1212362121000
SIZE: 4096

/home/douglas/.bash_history
LAST MODIFIED: 1212464628000
SIZE: 20659

/home/douglas/.mcop
LAST MODIFIED: 1211433977000
SIZE: 4096

/home/douglas/.audacity-data
LAST MODIFIED: 1212376265000
SIZE: 4096

/home/douglas/.gnome
LAST MODIFIED: 1211416972000
SIZE: 4096

/home/douglas/.nvidia-settings-rc
LAST MODIFIED: 1212024727000
SIZE: 1034

/home/douglas/Videos
LAST MODIFIED: 1211416964000
SIZE: 4096

/home/douglas/.recently-used
LAST MODIFIED: 1212398706000
SIZE: 1835

/home/douglas/.Trash
LAST MODIFIED: 1212461138000
SIZE: 20480

/home/douglas/.update-notifier
LAST MODIFIED: 1211416968000
SIZE: 4096

/home/douglas/.aspell.en.pws
LAST MODIFIED: 1211785653000
SIZE: 44

/home/douglas/.gstreamer-0.10
LAST MODIFIED: 1212036407000
SIZE: 4096

/home/douglas/.mcoprc
LAST MODIFIED: 1211433977000
SIZE: 31

/home/douglas/.bashrc
LAST MODIFIED: 1211451273000
SIZE: 2298

/home/douglas/Music
LAST MODIFIED: 1212392004000
SIZE: 4096

/home/douglas/.wapi
LAST MODIFIED: 1212450905000
SIZE: 4096

/home/douglas/.gconf
LAST MODIFIED: 1212450900000
SIZE: 4096

/home/douglas/.bash_logout
LAST MODIFIED: 1211451273000
SIZE: 220

/home/douglas/.scribus
LAST MODIFIED: 1212119102000
SIZE: 4096

/home/douglas/.gtkrc-1.2-gnome2
LAST MODIFIED: 1211416966000
SIZE: 89

/home/douglas/Icons
LAST MODIFIED: 1212370302000
SIZE: 4096

/home/douglas/symphonic_settings.xml
LAST MODIFIED: 1212451471000
SIZE: 794

/home/douglas/.cache
LAST MODIFIED: 1211416968000
SIZE: 4096

/home/douglas/azureus
LAST MODIFIED: 1197012305000
SIZE: 4096

/home/douglas/.sudo_as_admin_successful
LAST MODIFIED: 1211417185000
SIZE: 0

/home/douglas/.esd_auth
LAST MODIFIED: 1211416977000
SIZE: 16

/home/douglas/.nautilus
LAST MODIFIED: 1212417576000
SIZE: 4096

/home/douglas/Pictures
LAST MODIFIED: 1212370223000
SIZE: 4096

/home/douglas/.xine
LAST MODIFIED: 1211433965000
SIZE: 4096

/home/douglas/Documents
LAST MODIFIED: 1212398933000
SIZE: 4096

/home/douglas/My Music
LAST MODIFIED: 1212457736000
SIZE: 4096

/home/douglas/.recently-used.xbel
LAST MODIFIED: 1212465332000
SIZE: 265642

/home/douglas/.themes
LAST MODIFIED: 1211509752000
SIZE: 4096

/home/douglas/.dmrc
LAST MODIFIED: 1212450896000
SIZE: 28

/home/douglas/.icons
LAST MODIFIED: 1211509753000
SIZE: 4096

/home/douglas/.gnome2
LAST MODIFIED: 1212465043000
SIZE: 4096

/home/douglas/.update-manager-core
LAST MODIFIED: 1211928867000
SIZE: 4096

/home/douglas/.gdesklets
LAST MODIFIED: 1211702681000
SIZE: 4096

/home/douglas/Desktop
LAST MODIFIED: 1212451176000
SIZE: 4096

/home/douglas/.local
LAST MODIFIED: 1211416968000
SIZE: 4096

/home/douglas/.gnome2_private
LAST MODIFIED: 1211502329000
SIZE: 4096

/home/douglas/.macromedia
LAST MODIFIED: 1211433837000
SIZE: 4096

/home/douglas/.gksu.lock
LAST MODIFIED: 1212461217000
SIZE: 0

/home/douglas/.xsession-errors
LAST MODIFIED: 1212465333000
SIZE: 185298

/home/douglas/.thumbnails
LAST MODIFIED: 1211451076000
SIZE: 4096

/home/douglas/.metacity
LAST MODIFIED: 1211416971000
SIZE: 4096

/home/douglas/.evolution
LAST MODIFIED: 1212417576000
SIZE: 4096

/home/douglas/.profile
LAST MODIFIED: 1211451273000
SIZE: 566

/home/douglas/.audacity1.3-douglas
LAST MODIFIED: 1212376265000
SIZE: 4096

/home/douglas/Public
LAST MODIFIED: 1211416964000
SIZE: 4096

/home/douglas/.fontconfig
LAST MODIFIED: 1211593354000
SIZE: 4096

/home/douglas/cep
LAST MODIFIED: 1212459580000
SIZE: 4096

/home/douglas/.hwdb
LAST MODIFIED: 1212387144000
SIZE: 32

/home/douglas/.config
LAST MODIFIED: 1211700855000
SIZE: 4096

/home/douglas/.gimp-2.4
LAST MODIFIED: 1212385861000
SIZE: 4096

/home/douglas/.DCOPserver_desktop__0
LAST MODIFIED: 1212455943000
SIZE: 54

/home/douglas/Templates
LAST MODIFIED: 1212113974000
SIZE: 4096

/home/douglas/.gconfd
LAST MODIFIED: 1212465329000
SIZE: 4096

/home/douglas/.openoffice.org2
LAST MODIFIED: 1212398706000
SIZE: 4096

/home/douglas/.mplayer
LAST MODIFIED: 1211780568000
SIZE: 4096

/home/douglas/Downloaded-Programs
LAST MODIFIED: 1212461129000
SIZE: 4096

/home/douglas/.w3m
LAST MODIFIED: 1211500229000
SIZE: 4096

/home/douglas/.adobe
LAST MODIFIED: 1211433837000
SIZE: 4096

/home/douglas/.ICEauthority
LAST MODIFIED: 1212455943000
SIZE: 2011


```

---

### Post by iaculallad on 2008-06-03
Had you tried looking at this [page]("https://help.ubuntu.com/community/LimeWire")?

---

### Post by tropdoug on 2008-06-03
> **iaculallad said:**
> Had you tried looking at this [page]("https://help.ubuntu.com/community/LimeWire")?

Nope, but now I have! thanks, I sometimes forget about the wiki's brilliant stuff. Whats more I really want to support Open source so I have decided not to use Limewire but to use Frostwire instead. 

Sop that's two pluses.

---

