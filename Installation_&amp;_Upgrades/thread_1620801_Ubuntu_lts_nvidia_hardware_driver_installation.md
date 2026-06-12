---
title: "Ubuntu lts nvidia hardware driver installation"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by rambo15 on 2010-11-13
Good Afternoon:

I installed UBUNTU LTS 10.4 on my Dell 8100. I am trying to activate the NVIDIA accelerated graphics drivers version 96. Using the mouse I select > System > Admin > Hardware Drivers.

The GUI pops up and says I need to activate these drivers. Using the mouse I select the Activate button. I then get a pop window which states:

"You are not authorized to perform this action"

I have executed the update manager and my system is updated.

Does anyone know how to fix this problem?

Regards - Mark K.

---

### Post by Frogs Hair on 2010-11-13
Are you using a user account ?  Does the account have user privileges that allow you to preform that task ? You can check that from Users and Groups.

---

### Post by rambo15 on 2010-11-13
Hi:
    I check what groups I am in and they are as follows:

root
adm
admin

The syslog file shows the following error being record when I execute the activate button:
ov 13 15:34:24 rambo-dell kernel: [17797.829132] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Nov 13 15:36:09 rambo-dell hp[2807]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov 13 15:36:09 rambo-dell python: io/hpmud/pp.c 627: unable to read device-id ret=-1

Thanks for your help

---

