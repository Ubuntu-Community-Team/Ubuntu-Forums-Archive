---
title: "Lucid xserver update breaks &quot;glxgears&quot;, etc."
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by azc on 2011-10-18
After applying the following updates on my laptop, "glxgears", etc. crashes.  I suspect the xserver-* updates are to blame, but that's guess a guess.

```

$ cat /var/log/dpkg.log|grep -i "status installed"
(...)
2011-10-18 13:56:17 status installed desktop-file-utils 0.16-0ubuntu2
2011-10-18 13:56:18 status installed python-gmenu 2.30.0-0ubuntu4
2011-10-18 13:56:19 status installed man-db 2.5.7-2ubuntu1
2011-10-18 13:56:20 status installed python-support 1.0.4ubuntu1
2011-10-18 13:56:22 status installed byobu 2.68-0ubuntu1.2
2011-10-18 13:56:22 status installed libdevkit-power-gobject1 1:0.9.1-1ubuntu1
2011-10-18 13:56:22 status installed libupower-glib1 0.9.1-1ubuntu1
2011-10-18 13:56:23 status installed upower 0.9.1-1ubuntu1
2011-10-18 13:56:23 status installed **xserver-common 2:1.7.6-2ubuntu7.8**
2011-10-18 13:56:23 status installed **xserver-xorg-core 2:1.7.6-2ubuntu7.8**
2011-10-18 13:56:23 status installed libc-bin 2.11.1-0ubuntu7.8
$

```

Output of "glxgears":

```

$ glxgears
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  17
  Current serial number in output stream:  17
$ 

```

Laptop graphics info:

```

$ lspci|grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
$ 

```

Can someone please tell me how to fix this, or point me in that direction?

Thanks!

---

### Post by DeGrijze on 2011-10-18
To fix this problem 4 now i just downgraded back 2 version be4 the downloaded and installed updates.

```
sudo aptitude install xserver-common=2:1.7.6-2ubuntu7
```

and

```
sudo aptitude install xserver-xorg-core=2:1.7.6-2ubuntu7
```

And after reboot all works again.

Gerard

---

### Post by redoscar3 on 2011-10-18
Gerard,

Many thanks for the tip on downgrading the two most recent xserver package updates.  Seems that when I applied those updates this evening, it killed my desktop effects.  Hopefully the package maintainers can resolve this issue.  Your tip has been a lifesaver.

Red

---

### Post by nmyrick on 2011-10-19
Thank You!  This worked for me! I first noticed the issue when Awn was no longer working properly.  

It would really be great if Ubuntu had an option in update manager to un-install recent updates.  As much as I love Ubuntu, this is something windows has that I have always missed in Ubuntu in the event that something like this happens.

---

### Post by Captain_Rage on 2011-10-19
Thank you! I was experiencing the same issues after some update in Ubuntu 10.04.
My machine is a Eee PC 901 with an integrated Intel graphics card.

---

### Post by panixo on 2011-10-19
Hi,
Silly question but I'm a pretty new linux user.
I got linked here from this thread:
[http://ubuntuforums.org/showthread.php?t=1864548](http://ubuntuforums.org/showthread.php?t=1864548)
Having the same problem as the poster, that since updating my netbook remix loads the home screen but with no icons except the time / internet / battery life in the top corner.  I was linked here with this as instructions how to fix the problem, but -- I don't know how to get into terminal to do this fix without having access to the icons?  Help?

---

### Post by sersang on 2011-10-19
@DeGrijze: Thanks a lot; this worked for me. I had the same problem and solved :)

---

### Post by sybille on 2011-10-19
Hi,

Could everyone who reported the problem in this thread go to the following Launchpad bug and click at the top of the page to confirm that the bug is affecting you?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)

Thanks!

Also, for people who are working around the problem by downgrading the problematic packages - xserver-common and xserver-xorg-core - please realize that the updated packages were for a security update. So it is important for you to follow the issue closely and to make sure to upgrade as soon as there are new, fixed packages if you must continue to use the old, insecure versions.

---

### Post by th_01 on 2011-10-19
This fix worked on my netbook Toshiba N205

To log into terminal mode from screen

Use hot key combo

ctrl - alt - t

or 

from login/password screen  at the bottom select x-term in drop down

T

---

### Post by nmyrick on 2011-10-19
To Panixo,

Right click on the panel next to where your current icons are.  Select "add to panel", then select Gnome Menu.  Once you have added the Gnome menu, go to "accessories > terminal" to open the terminal.

---

### Post by nmyrick on 2011-10-19
Where do I click in the bug report to show that it affects me?  I don't see anything at the top of the page to select.

---

### Post by panixo on 2011-10-19
Got it, thanks.
Accessed terminal but this solution didn't work for me - restart but it's the same as before.

---

### Post by sybille on 2011-10-19
It looks like new, fixed packages are on the way:
[https://bugs.launchpad.net/ubuntu/+s...05/comments/20]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905/comments/20")

So hopefully things will sort themselves out soon.

---

### Post by ChannelZ28 on 2011-10-19
thanks for that info, it worked for me!

---

### Post by sersang on 2011-10-19
Problem solved :)
[http://www.ubuntu.com/usn/usn-1232-2/](http://www.ubuntu.com/usn/usn-1232-2/)

---

### Post by gudrade on 2011-10-19
> **DeGrijze said:**
> To fix this problem 4 now i just downgraded back 2 version be4 the downloaded and installed updates.

```
sudo aptitude install xserver-common=2:1.7.6-2ubuntu7
```and

```
sudo aptitude install xserver-xorg-core=2:1.7.6-2ubuntu7
```And after reboot all works again.

Gerard


Thanks very much!

---

### Post by DeGrijze on 2011-10-19
> **sersang said:**
> Problem solved :)
[http://www.ubuntu.com/usn/usn-1232-2/](http://www.ubuntu.com/usn/usn-1232-2/)
Not 4 me and my HP netbook 

Gerard

---

### Post by lovayda on 2011-10-20
De la ptm. Thanks a lot!!!

---

### Post by azc on 2011-10-20
Thanks everyone for your input and participation, particularly DeGrijze and sybille.

I've just upgraded to "xserver-common 2:1.7.6-2ubuntu7.9" and "xserver-xorg-core 2:1.7.6-2ubuntu7.9", and GLX seems to be working properly on my laptop with Intel graphics.

FWIW, I did not earlier downgrade "xserver-*" due to security concerns, and just waited for the fixed packages.

As a sidebar, the latest "xserver-*" upgrades did not cause any problems on my desktop with Nvidia graphics.

I was going to mark this thread as "resolved", however I see that DeGrijze is still having problems, so I'll monitor this thread for a couple of days for his/her resolution.

Thanks again!

---

### Post by DeGrijze on 2011-10-20
@ azc, the updates of 2 day fixt the problem 4 my HP netboook, so you can mark this topic to resolved.

Gerard

p,s please keep up the good work

---

### Post by azc on 2011-10-20
Thanks for the report, Gerard. :D

Marking thread [SOLVED].

---

### Post by nmyrick on 2011-11-12
To all who posted here, x-server has been fixed.  The version that is now in your update manager is good.

I just tried it yesterday, and it works fine.

---

