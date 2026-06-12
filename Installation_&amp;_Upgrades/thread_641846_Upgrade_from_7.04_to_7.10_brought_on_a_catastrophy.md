---
title: "Upgrade from 7.04 to 7.10 brought on a catastrophy of problems; please help"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by inzania on 2007-12-15
Hey all,

I'd really appreciate some help - my laptop is currently unusable, as I am far from a Linux guru, and upgrading to the latest version caused a whole slew of problems.  I used the standard update manager and let it run its updates... the first thing I noticed on re-boot was that things were running noticeably slower.

As soon as I was logged in, I received a "Failed to initialize HAL" message.  Then I noticed the network icon in the upper right corner, which insisted that it could not connect to the internet.  Interestingly, I brought up the manual configuration, and the wireless did indeed seem to find the network, but I had no luck getting the network manager to actually connect to anything.  I should also mention that the network manager was running VERY slow, and after a change I often had to wait a minute+ before the window was responsive again.  I then tried to start Firefox/Opera with no luck - they seem to just terminate before the window even opens.  I then noticed that I had exactly 0 bytes free on my home drive; I'm not sure if this was my fault or not, but I could have sworn I had a lot more space than that before the upgrade.  I cleaned out some files and rebooted a few times to no avail.

So I don't know what to make out of all this.  I really need to get my system working smoothly again, even if it means downgrading back to 7.04.  Unfortunately, everything I've found seems to indicate I need an active internet connection in order to downgrade.  In case it helps, I'm running a ThinkPad T60 with 2x1GB sticks of RAM and I replaced the CDROM drive in the optical bay with a 200GB HD.

Thanks in advance.

---

### Post by Recovering from MS. on 2007-12-17
I think you may have a similer problem as this post...

[http://ubuntuforums.org/showthread.php?t=642303](http://ubuntuforums.org/showthread.php?t=642303)

From what little Ive learned to day. you may have to reinstall to downgrade...
hope im atleast a little help... goodluck

---

### Post by Sef on 2007-12-17
> you may have to reinstall to downgrade...

That is correct.

> I received a "Failed to initialize HAL" message.

For this poster, it seems to be a [Dbus problem]("http://www.linuxforums.org/forum/ubuntu-help/61350-failed-initialize-hal.html").

> i had this error also.

the problem was that i deactivated dbus service from service-admin.
D-Bus is a message bus, used for sending messages between
applications.

it is used heavily by many Ubuntu config scripts.

by deactivating it , at the runtime /var/run/dbus was not created and from here the hal error appeared.

So be sure that dbus service runs at startup and if the error persists reinstall dbus package.

[LaunchPad Bug Report 137559]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/137559") has some solutions.   Maybe one will work for you.

---

