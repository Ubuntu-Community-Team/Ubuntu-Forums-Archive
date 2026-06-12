---
title: "Failed to load session &quot;Ubuntu&quot;"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by khanley52 on 2011-10-15
Hi, after upgrading my Ubuntu Studio 11.04 to 11.10, it won't let me log in.  When I get to the login screen, when I type in my password, it just says "Failed to load session "Ubuntu".  I can switch the drop down menu to "Gnome Classic" and log in just fine, but "Ubuntu" won't allow me to get in.

I've looked at other similar problems, but other people are saying it's not liking their password or whatever, and the solution was to delete .Xauthority.  I tried that and it didn't change anything.

Does anyone else have any suggestions?

---

### Post by armanja on 2011-10-16
I've just have the same problem too but it solved. I've manage to check my driver and found that my 3d acceleration driver were not installed.

Do your pc have graphic card installed?  If so the problem might be because or unsupported driver. try to login using other 'session' and try to check/update graphic driver especially 3d accelaration/renderer.

---

### Post by khanley52 on 2011-10-16
That fixed things.  Thank you. :)

---

### Post by wvxvw on 2012-03-11
Hello. I'm having the same problem, however it got more complicated.

- I can't download anything from internet and my CD is broken... I can't boot from USB disk either for reasons I can't explain - It'll just stop during the initial device mount phase and hang there...

- I can't download anything from internet because when updating, the update (which didn't went smoothly, and required a bunch of restarts) screwed the network-manager, so whenever I try to:

```
# nmcli con up id <valid id>
```It would tell me that the device is not managed. I've tried to change the `managed' setting in the NetworkManager.conf file to true (it's listed under [ifupdown]) to no effect.

Subsequently, I can't run apt-get to load new stuff - so my only option is to remove what I have, or try to fix things by hand.

Interestingly, the rescue mode won't manage to shut down Gnome (or, at least, that's the last message it gives before either rebooting or hanging). But I can get to the login screen in the normal mode. As this thread's title suggests: this is the message I'm getting: `Failed to load session "Ubuntu"'. Beside this session, there is only one other option, which is an anemic console window, however, it gives me command line access so, I hoped to use it somehow to edit session(s?) to let me log in and try to reconfigure network interfaces and network manager. Possibly remove Gnome/Unity?

So, please, is there any conscious description of how to create a "session" so to make this new display manager happy? Actually, if this is such a complication - I would be happy to avoid it altogether, if it is possible (I'd rather go back to Gnome - I've no interest in sessions - there's no practical use for me in this feature...)

To make the matter worse, I have Nvidia graphic card. It used to work fine with Nvidia drivers, but never worked good with Nueuvo drivers. However, older oss versions would work in a low resolution mode. I looked into kernel logs and debug logs to find out that nueuvo writes error messages telling about unsupported chipset. However, the result is dramatically different - once such error occurs, the computer will shutdown immediately.
I've tried about 10 different driver versions from Nvidia - the old ones won't compile on Ubutnu 10.04+, the very new one tells something about not being able to compile a file required for gcc check. One, the second recent would compile the kernel, but would not install because once it tries to update xorg configuration files it fails and computer shuts down.
To make it clear, even though I have access to the driver installers, I can't use them, because, if I try to terminate X-server, the console window will also die. In a funny way, my keyboard will also became half-functional, not being able to send aphanumeric keys, only the control keys... (I can Ctrl+Alt+Del, but I can't type anything).

This is not a hardware problem. This computer is a dual boot, and I'm writing from it right now, logged into Windows :(

Sorry, for the long rant, I've just tried to be explicit...

---

