---
title: "No default route"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by _tom_ on 2009-02-05
Hi,

every time I get connected with my wireless router via networkmanger I have to add a default route (route add default gw 10.0.0.138) otherwise I can't use the internet. I use a wpa encrypted network, connecting either by nm-applet or the plasma-network-applet. 
Problem exists only in jaunty not in intrepid.

Any idea?

---

### Post by olskar on 2009-02-05
> **_tom_ said:**
> Hi,

every time I get connected with my wireless router via networkmanger I have to add a default route (route add default gw 10.0.0.138) otherwise I can't use the internet. I use a wpa encrypted network, connecting either by nm-applet or the plasma-network-applet. 
Problem exists only in jaunty not in intrepid.

Any idea?

I have the same problem on all my three computers, has this showstopperbug been reported?

---

### Post by marmuta on 2009-02-06
Maybe this is [#307204]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204") again.
Any chance you are using speedTouch routers?

---

### Post by olskar on 2009-02-06
> **marmuta said:**
> Maybe this is [#307204]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204") again.
Any chance you are using speedTouch routers?

Indeed I am

---

### Post by marmuta on 2009-02-06
A speedtouch router was mentiond in the bug report, that's why I was asking. There could be something about how they implement static routes with dhcp option 121 aka rfc3442. Nothing wrong with that, maybe they are the only routers doing it right or supporting that feature at all. At least my pitiful router doesn't know anything about option 121.

There is a [workaround]("http://ubuntuforums.org/showpost.php?p=6595573&postcount=25") ripped from the bug report which basically turns Ubuntus rfc3442 support off, but of course it would be better to get the underlying bug resolved. It could be interesting to see the dhcp packets that your speedtouch is returning. This would allow to setup a custom dhcp server with that response for testing. 

So, if you have a couple of minutes to spare, maybe you would like to post a [package dump]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204/comments/6")? Best at [#307204]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204")on launchpad. If that is not an option just post it here. You can open the dump in wireshark afterwards if you want to check what's inside.

---

### Post by olskar on 2009-02-06
> **marmuta said:**
> A speedtouch router was mentiond in the bug report, that's why I was asking. There could be something about how they implement static routes with dhcp option 121 aka rfc3442. Nothing wrong with that, maybe they are the only routers doing it right or supporting that feature at all. At least my pitiful router doesn't know anything about option 121.

There is a [workaround]("http://ubuntuforums.org/showpost.php?p=6595573&postcount=25") ripped from the bug report which basically turns Ubuntus rfc3442 support off, but of course it would be better to get the underlying bug resolved. It could be interesting to see the dhcp packets that your speedtouch is returning. This would allow to setup a custom dhcp server with that response for testing. 

So, if you have a couple of minutes to spare, maybe you would like to post a [package dump]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204/comments/6")? Best at [#307204]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204")on launchpad. If that is not an option just post it here. You can open the dump in wireshark afterwards if you want to check what's inside.

If I do:  sudo dhclient eth0 -r; sudo dhclient eth

the problem disappears and I get connected.. :confused:


Anyway, upping dump to launchpad

---

### Post by marmuta on 2009-02-07
Thank you both for the tcpdumps!
> **olskar said:**
> If I do:  sudo dhclient eth0 -r; sudo dhclient eth

the problem disappears and I get connected.. :confused:


Yep, the routes are fine the first time after a release. The breakage should happen when you run sudo dhclient eth0 a second time.
 
There may even be a fix now. It worked for me, but could use some more testing. So, if you would like to try it run
```
gksu gedit /etc/dhcp3/dhclient-exit-hooks.d/rfc3442-classless-routes
```
and replace line 8
```
                if [ x"$reason" == x"BOUND" ]; then

```with
```
                if [ x"$reason" == x"BOUND" -o x"$reason" == x"REBOOT" ]; then

```
Then restart networking with sudo /etc/init.d/networking restart or just reboot.

---

### Post by olskar on 2009-02-11
> **marmuta said:**
> Thank you both for the tcpdumps!


Yep, the routes are fine the first time after a release. The breakage should happen when you run sudo dhclient eth0 a second time.
 
There may even be a fix now. It worked for me, but could use some more testing. So, if you would like to try it run
```
gksu gedit /etc/dhcp3/dhclient-exit-hooks.d/rfc3442-classless-routes
```
and replace line 8
```
                if [ x"$reason" == x"BOUND" ]; then

```with
```
                if [ x"$reason" == x"BOUND" -o x"$reason" == x"REBOOT" ]; then

```
Then restart networking with sudo /etc/init.d/networking restart or just reboot.

That did not help me sadly, no default route, however running sudo dhclient does :)

---

### Post by marmuta on 2009-02-11
Things turned out to be a bit more complicated with networkmanager. The above change fixes only the command line side. For some reason nm ignores all dhclient hook scripts ([#293139]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/293139")) and never even calls rfc3442-classless-routes. If you would like to try again, please save the little script below as '/etc/NetworkManager/dispatcher.d/10rfc3442-classless-routes'. 
```
#!/bin/bash -e
# Script to dispatch NetworkManager events
#
# Runs dhclient hook script to add rfc3442 classless static routes.

if [ x"$2" = x"up" ]; then
        reason="BOUND"
        interface="$1"
        new_rfc3442_classless_static_routes="$DHCP4_RFC3442_CLASSLESS_STATIC_ROUTES"
        . /etc/dhcp3/dhclient-exit-hooks.d/rfc3442-classless-routes
fi
```

and make it executable with
```
sudo chmod 755 /etc/NetworkManager/dispatcher.d/10rfc3442-classless-routes
```
This should make sure that it does get called.

---

