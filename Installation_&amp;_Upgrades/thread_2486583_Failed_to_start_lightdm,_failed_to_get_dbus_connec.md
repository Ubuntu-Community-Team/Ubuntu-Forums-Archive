---
title: "Failed to start lightdm, failed to get dbus connection, running in Docker container"
date: 2023-05-04
forum: Installation &amp; Upgrades
---

### Post by AllGamer on 2023-05-04
Long story short, I need a Ubuntu Desktop to inside a Docker container.

Ubuntu installed fine, however when I try to start lightdm it throws this error, any help would be appreciated, Thanks.


root@ubuntu:/# service lightdm start                                                                                                                                    
 * Starting X display manager lightdm                                                                                                                                   
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log                                                                                                                 
[+0.02s] DEBUG: Starting Light Display Manager 1.30.0, UID=0 PID=26                                                                                                     
[+0.02s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d                                                                                       
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf                                                                      
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf                                                                 
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf                                                                    
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf                                                                      
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf                                                                             
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf                                                                      
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf                                                                    
[+0.02s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d                                                                                 
[+0.02s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d                                                                                         
[+0.02s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf                                                                                                    
[+0.02s] DEBUG: Registered seat module local                                                                                                                            
[+0.02s] DEBUG: Registered seat module xremote                                                                                                                          
[+0.02s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager                                                                                                         
[+0.02s] DEBUG: _g_io_module_get_default: Found default implementation local (GLocalVfs) for ?gio-vfs?                                                                  
[+0.02s] WARNING: Failed to get system bus: Could not connect: No such file or directory                                                                                
[+0.02s] DEBUG: Adding default seat                                                                                                                                     
[+0.03s] DEBUG: Seat seat0: Loading properties from config section Seat:*                                                                                               
[+0.03s] DEBUG: Seat seat0: Starting                                                                                                                                    
[+0.03s] DEBUG: Seat seat0: Creating greeter session                                                                                                                    
[+0.03s] DEBUG: Seat seat0: Creating display server of type x                                                                                                           
[+0.03s] DEBUG: Using VT 7                                                                                                                                              
[+0.03s] DEBUG: Seat seat0: Starting local X display on VT 7                                                                                                            
[+0.03s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log                                                                                                          
[+0.03s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0                                                                                       
[+0.11s] DEBUG: XServer 0: Launching X Server                                                                                                                           
[+0.11s] DEBUG: Launching process 30: /bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch                                          
[+0.11s] DEBUG: XServer 0: Waiting for ready signal from X server :0                                                                                                    
Failed to get D-Bus connection                                                                                                                                          [ OK ] 

root@ubuntu:/#

---

### Post by Bashing-om on 2023-05-04
AllGamer; Hello ---

As it is (U)buntu that you have installed - it is GDM (Gnome Display Manager) that is the DE; not lightdm/

Try as:
```

sudo systemctl start gdm3.service

```

Best I can say at this time as we do not know what provisions are in place to start the GUI.

[INDENT]there is a process, however
[/INDENT]

---

### Post by MAFoElffen on 2023-05-05
Backup please. 

What release version of what flavor Ubuntu are you working with? Why do I ask? Because the commands you used "were" for Ubuntu, but outdated... As in, that's what they were for Ubuntu 14.04, when Ubuntu used LightDM, way back when.

That was before it changed to GDM, and before systemd.

It would be nice to hear what you are working with so we can get you going with the correct commands.

Next... If anyone notices the prompt:
```

**[COLOR=#ff0000]root[/COLOR]**@ubuntu:/# service lightdm start 

```
With Ubuntu- The [COLOR=#ff0000]root[/COLOR] user cannot start an X Session. Only user's can. It can be done, but not without hacking it to even to be able to, and not recommended.

---

