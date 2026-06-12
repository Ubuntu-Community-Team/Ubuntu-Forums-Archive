---
title: "Noob Question on 9.10 --&gt; 10.04 Upgrade"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by flcltd on 2010-05-16
Hi All,

A quick potted history of me. 20 years in Windows IT, 4 years on my beloved Mac (but GUI only). I have now taken over a customer with Ubuntu 8.10. It was headless but I added Gnome etc as I just feel more comfortable with it, sorry to all you purists.

Today I moved them to 9.04 (successful), then up to 9.10 (again successful) then ...to 10.04 (not successful).

This is all done via SSH and x11vnc but I have easy access to the box tomorrow (2 miles from home - no biggie).

Right - my problem...

It's all working - I know this because Webmin is happy. How ever x11vnc not working because its not auto logging in. X11 forwarding allows me access to Gnome Control Centre but when I look at the login applet I can't unlock it. Error at load as follows: -

** (gdmsetup:1880): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:1880): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:1880): WARNING **: Error calling GetValue('daemon/TimedLogin'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:1880): DEBUG: init user='(null)' auto=False

Click Unlock gives: -

** (gdmsetup:1880): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files

I have tried "playing" with the old gdm.conf-custom and the new custom.conf etc but no joy. I have also seen no seat ID but I have lost track at what point I saw this.

Restart GDM give: -

restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.31" (uid=1001 pid=1894 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

As I say I can still do "stuff" via command line and Webmin but I would like to get the VNC to the real X11 session working. I hven't been on site yet so I am not sure whether there is a login screen on the monitor (which isn't currently attached) but can check tomorrow.

Thanks for your patience with a real noob and any help you can offer,

Chris

---

