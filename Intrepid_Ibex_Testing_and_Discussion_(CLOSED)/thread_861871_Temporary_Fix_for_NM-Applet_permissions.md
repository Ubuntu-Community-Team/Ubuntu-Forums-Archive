---
title: "Temporary Fix for NM-Applet permissions"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mewithafez on 2008-07-17
This should work if you have NetworkManager but no applet is coming up.

If you have an Intel 3945, this applies best. If not it is still worth a shot if the "permissions" error comes up when you run "nm-applet" in terminal.

1. For Intel 3945, install linux-restricted-modules-common from Synaptic and reboot.

2. Check that NetworkManager and NM-applet are in system-preferences-sessions.

3. Run nm-applet in terminal and you should get an error about not having permissions for org.freesomething.networksomethingelse

4. SO, make a launcher with the command sudo nm-applet because that will override the permissions thing. This has been reported as a bug I believe but until it is fixed this'll help the wireless blues.

Peace all!

update: scroll down for the better fix.

double update!: fixed with latest update. this thread can be deleted, thanks for the help.

---

### Post by thonuz on 2008-07-17
Thanks,
Just what I needed.

 Also Ethernet (Marvell something or other unknown in Hardy) now works in Ibex due to the newer kernel I imagine. This affects many Toshiba Satellite models and is difficult to fix for most people.

So Ibex works better than Hardy already, but I got both installed in case I need to get work done.

---

### Post by ccw on 2008-07-17
I filed  bug 24904

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404)

I filed it against nm-applet, but I don't think its the issue. There was a new consolekit package last night. Could that be the problem? I'm not quite clear on what it does yet.

---

### Post by pferraro on 2008-07-17
You can also downgrade consolekit and libck-connector0 to the last working version: 0.2.10-0ubuntu2.

---

### Post by stari4ek on 2008-07-17
I had this kind of problem before, when I've started x-server from terminal through startx instead of gdm (/etc/init.d/gdm start)
It looks like if x-server started without gdm, user doesn't have some rights. And as result some soft can't work. For me it was:
1. nm-applet, as mention in topic. with the same errors
2. governor apple (it couldn't change current governor)

Do you login from gdm-greeter or from terminal?

---

### Post by ccw on 2008-07-17
> **stari4ek said:**
> 
Do You Login From Gdm-greeter Or From Terminal?

Gdm

---

### Post by jfernyhough on 2008-07-17
I found a better fix on [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager]("https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager") .

However, I copied the user="root" section and added in my own username, I thought that might be a bit more secure.

> Change the default policy context in both /etc/dbus-1/system.d/NetworkManager.conf and /etc/dbus-1/system.d/nm-applet.conf so it says 'allow' instead of 'deny'.

<policy context="default">
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>

Then restart dbus

sudo /etc/init.d/dbus restart

and launch the applet

nm-applet

I should probably add that adding my user to the "netdev" group, as per another suggestion on that page, didn't fix anything.

---

### Post by BwackNinja on 2008-07-17
fixed with an update

---

