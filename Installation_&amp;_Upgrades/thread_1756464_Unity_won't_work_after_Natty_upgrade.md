---
title: "Unity won't work after Natty upgrade"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by 6432crab on 2011-05-12
hello, i've just upgraded my Ubuntu version a week ago and got a problem that the Unity UI won't running after upgrade. My laptop is Dell Inspiron 14R which is i think is more than capable for running Unity 3D. 

when i rebooted after upgrade there was just a blank wallpaper screen, without Unity interface at all.
what should I do? 

THANK YOU SO MUCH

---

### Post by ivanovnegro on 2011-05-12
Maybe you are using a proprietary graphics card and could try to add additional drivers, or to go into Ubuntu Classic mode from the log on manager or to try Unity 2D from the repositories that does not require 3D acceleration.

---

### Post by 6432crab on 2011-05-12
how do i do that thing?

---

### Post by ivanovnegro on 2011-05-12
Ah, you cannot boot at all into a desktop?

---

### Post by 6432crab on 2011-05-13
i can boot into the classic desktop session normally. But when  i got to the unity desktop session, there was no unity UI at all. Just a blank wallpaper and the cursor

---

### Post by Hedgehog1 on 2011-05-13
Since you can see the wallpaper, I think your video driver is OK.

Please boot into Unity (such as it is), then -

Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...

***The Hedge***

:KS

---

### Post by ivanovnegro on 2011-05-13
If you want to look anyway for additional drivers go to System-> Additional drivers.
I hope Unity will work for you, if not and you are interested in Unity 2D, go to the Software Center and search for Unity 2D and install it, log out and log in with the Unity 2D session.
But first try what Hedgehog proposed to see if you can get to the normal Unity UI.

---

### Post by vitamincgo on 2011-06-29
It's a quick fix for everyone with an Nvidia card that wont work or boot.

First Log in usinging (Ubuntu Classic : No effects)
then goto Additional Drivers and tell it to use the Nvidia 173 drivers, the recommended ones are some how janking the Unity desktop up. It should still tell you that it's active but not in use. that's a bug that needs to be fixed, but for now you can just Alt + F2, type "unity" then hit enter and it should run. 

My bottom bar was still active after Unity started, I just rightclicked removed it.

[IMG]http://i4.photobucket.com/albums/y146/gothraverguy/Screenshot.png[/IMG]

Anyone got a better way to Unity to start each time after these drivers are installed let us know. :)

---

