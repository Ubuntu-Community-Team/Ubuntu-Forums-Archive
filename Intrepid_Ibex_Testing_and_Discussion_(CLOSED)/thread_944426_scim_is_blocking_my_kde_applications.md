---
title: "scim is blocking my kde applications"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hardhu on 2008-10-11
Hello everybody,
after latest upgrades I have some problems when I start a kde session (no problem so far in Gnome).

When I launch dolphin for example, it takes two minutes or more to show on the desktop; the same happens with konqueror, and it can't connect to any web page, while I have no problem when I launch Firefox.

Looking at active processes with ps ax, I have plenty of lines related to scim-panel gtk:

```
 6013 ?        S      0:00 kded4                                                                                                              
 6019 ?        S      0:00 kwrapper4 ksmserver                                                                                                
 6020 ?        Sl     0:00 ksmserver                                                                                                          
 6022 ?        Sl     1:22 kwin -session 10ca61676c000122372272700000067950000_1223728014_851765                                              
 6079 ?        Sl     0:12 /usr/bin/knotify4                                                                                                  
 6080 ?        Sl     0:01 /usr/bin/krunner                                                                                                   
 6087 ?        Ss     0:00 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay -d                                         
 6089 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6093 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6097 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6101 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6105 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6109 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6113 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6117 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6121 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6125 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6130 ?        Sl     0:14 /usr/bin/plasma                                                                                                    
 6131 ?        Sl     0:00 /usr/bin/nepomukserver                                                                                             
 6133 ?        S      0:00 /usr/bin/nepomukservicestub nepomukstorage                                                                         
 6135 ?        S      0:00 /usr/bin/nepomukservicestub nepomukontologyloader                                                                  
 6136 ?        S      0:00 /usr/bin/nepomukservicestub nepomukfilewatch                                                                       
 6144 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6148 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6152 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6156 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6160 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6164 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6168 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6172 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6176 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6180 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6186 ?        S      0:00 kdeinit4: kio_file [kd up                                                                                          
 6196 ?        S      0:00 /usr/bin/kaccess                                                                                                   
 6209 ?        S      0:00 kmix -session 10ca61676c000122372276200000067950030_1223728004_255747                                              
 6214 ?        Sl     0:02 konsole -session 10ca61676c000122372282400000067950059_1223728004_259163 -name Qt-subapplication                   
 6220 ?        S      0:00 python /usr/bin/printer-applet                                                                                     
 6222 ?        SNl    0:02 python /usr/bin/update-notifier-kde                                                                                
 6223 ?        S      0:00 /usr/bin/python /usr/bin/kblueplugd                                                                                
 6225 ?        S      0:00 /usr/bin/klipper                                                                                                   
 6233 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6242 ?        S      0:00 /usr/bin/knetworkmanager                                                                                           
 6246 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d                                               
 6248 ?        Ss     0:00 kdeinit Running...                                                                                                 
 6251 ?        S      0:00 dcopserver [kdeinit] --nosid --suicide                                                                             
 6254 ?        S      0:00 /usr/bin/python /usr/bin/guidance-power-manager                                                                    
 6256 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6257 ?        S      0:00 klauncher [kdeinit] --new-startup
 6262 ?        S      0:00 kded [kdeinit] --new-startup
 6269 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6271 pts/1    Ss     0:00 /bin/bash
 6336 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6338 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6342 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6344 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6346 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6348 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6358 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6361 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6363 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6365 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6367 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6369 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6373 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6375 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6379 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6382 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6384 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6387 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6389 ?        Ss     0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6611 ?        Ssl    0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d
 6616 ?        S      0:00 scim-bridge
 7422 ?        SN     0:00 scim-bridge
 7433 ?        S      0:02 /usr/bin/dolphin -icon system-file-manager -caption Dolphin /home/rick
 7436 ?        Sl     0:45 /usr/lib/firefox-3.0.3/firefox
 7440 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 7455 ?        S      0:28 konqueror https://bugs.launchpad.net/ubuntu/+source/scim-bridge/+filebug/nsIsqXvtVC6bxHYV5hHowzvPzCH?field.title=sc
 7687 ?        Sl     0:00 kdeinit4: kio_http [kd up
 7729 pts/1    R+     0:00 ps ax

```

I have also this errors reported on syslog:

```
Oct 11 14:41:06 eagle scim-bridge: Failed to open the panel socket
Oct 11 14:41:13 eagle last message repeated 54 times

```

If i kill scim-launcher and scim-panel-gtk, then my kde applications wake up. 
Is anyone who has both Gnome and Kde installed experiencing the same issues?

---

### Post by NeoFax on 2008-10-13
I have a problem with multiple scims opening up.  However, I do not have the problem of konqueror/dolphin having problems.  Every time I try to kill scim it just respawns itself.

---

### Post by davija on 2008-10-14
I have had similar issues.  It will actually make my computer completely unusable.  I can move the mouse around and click on things, but half of the time, it don't actually perform the requested action.  Keyboard is completely defunct.


I was able to fix this somewhat by putting a script in the auto start (.kde/Autostart) like this:
```
#!/bin/bash
killall -9 scim-bridge
killall -9 scim-launcher
killall -9 scim-panel-gtk
```

---

### Post by davija on 2008-10-14
I found a fix here...  Place the contents in the ~/.scim/global as mentioned and restart.

[click here for solution]("https://bugs.launchpad.net/ubuntu/+source/skim/+bug/109827")

---

