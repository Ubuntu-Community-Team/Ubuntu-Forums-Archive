---
title: "Displayconfig-gtk and Xorg ????"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by toontastic on 2007-10-19
Finally think I've managed to upgrade to 7.10. I managed to get a look round and it looked nice but it told me to restart. After restart I'm getting the error:

Cannot launch graphical configuration tool because displayconfig-gtk is not installed.

Sorry, without this tool installed you must manually configure Xorg.


Ehm how do I fix this problem ? :confused: :(

---

### Post by toontastic on 2007-10-19
Forgot to mention after a get the error I get access to terminal which lets me log in that way but still not GUI.

---

### Post by anubhavrocks on 2007-10-19
```
 sudo apt-get install displayconfig-gtk
```

---

### Post by toontastic on 2007-10-19
Thanks for that. I've given it a try but I'm still getting the same error.

---

### Post by anubhavrocks on 2007-10-19
can you provide the output of
```
ls -l /etc/X11/xorg.conf*
```

---

### Post by toontastic on 2007-10-19
> **anubhavrocks said:**
> can you provide the output of
```
ls -l /etc/X11/xorg.conf*
```

Will it be a long file just I'm not sure how I can copy it from there to here other than rewriting so this might take a while.

---

### Post by toontastic on 2007-10-19
> **toontastic said:**
> Will it be a long file just I'm not sure how I can copy it from there to here other than rewriting so this might take a while.

I had a look at it but couldn't work out a way to copy it to Windows where I'm typing this. It seemed to just be some of the files on my system in fact it seemed to be my music, but I couldn't see them all as they went off the page. Any ideas ?

---

### Post by okst666 on 2007-10-19
ls -l /etc/X11/xorg.conf* >myfiles.txt
gedit myfiles.txt

then you can easily copy and paste it here.

---

### Post by toontastic on 2007-10-20
> **okst666 said:**
> ls -l /etc/X11/xorg.conf* >myfiles.txt
gedit myfiles.txt

then you can easily copy and paste it here.

If I type all of that in I get an error saying the file does not exist. If I type in ls -l /etc/X11/xorg.conf* first then >myfiles.txt secondaly and finally gedit myfiles.txt I get the error Cannot open display.

If I ran the terminal through the live CD (version 7.04) would I be able to do the same thing ? I could probably take screen shots then as well or would that not work ? 




:( :confused:

---

### Post by toontastic on 2007-10-20
> **toontastic said:**
> If I type all of that in I get an error saying the file does not exist. If I type in ls -l /etc/X11/xorg.conf* first then >myfiles.txt secondaly and finally gedit myfiles.txt I get the error Cannot open display.

If I ran the terminal through the live CD (version 7.04) would I be able to do the same thing ? I could probably take screen shots then as well or would that not work ? 




:( :confused:

Right, I tried running terminal through the 7.04 live disk. I entered the code suggested and got this:

-rw-r--r-- 1 root root 3513 2007-10-20 13:16 /etc/X11/xorg.conf

Which I assume is the information from the live disk and not from my other Linux install. Is there a way round this ?

---

### Post by toontastic on 2007-10-20
Ok I believe this is the output from myfiles.txt done from the terminal window when I try to login to 7.10

-rw-r--r-- 1 root root 3591 2007-10-19 19:01 /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1491 2007-10-20 13:33 /etc/X11/xorg.conf.failsafe
-rw-r--r-- 1 root root 1491 2007-10-20 08:49 /etc/X11/xorg.conf.failsafe.bak

---

### Post by anubhavrocks on 2007-10-20
can you try this
```
sudo apt-get update && sudo apt-get install  ubuntu-desktop
```

---

### Post by toontastic on 2007-10-20
> **anubhavrocks said:**
> can you try this
```
sudo apt-get update && sudo apt-get install  ubuntu-desktop
```

I've tried that, still the same.

---

### Post by toontastic on 2007-10-20
> **toontastic said:**
> I've tried that, still the same.

Just noticed there is a small error which appears when I try to access 7.10 from grub it says:

kinit: trying to resume from /dev/disk/by_uuid/8fc5bba9-225a-476d-9b7d-889e0b8f5da3
kinit: No resume image doing normal boot...

I then get the displayconfig-gtk error.

---

### Post by toontastic on 2007-10-20
> **toontastic said:**
> I've tried that, still the same.

The message at the end may help it says:

ubuntu-desktop is already the newest version.

The following packagtes were automatically installed and are no longer required:
(long list of files)
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by toontastic on 2007-10-20
I've just thought, I allowed Ubuntu to use the restricted ATI driver and it was after that reboot that it all went horribly wrong :) I don't believe I had done another reboot after the upgrade though. Could that be causing this and how do i fix it, I miss linux I didn't realize how much I had got used to it instead of Windows.

---

### Post by anubhavrocks on 2007-10-20
That explains it :)

---

### Post by toontastic on 2007-10-21
> **anubhavrocks said:**
> That explains it :)

How do I go about fixing it ?

---

### Post by toontastic on 2007-10-21
thats if it is possible to fix :)

---

### Post by anubhavrocks on 2007-10-21
try this 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.con.bak
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
sudo /etc/init.d gdm restart
```

---

### Post by toontastic on 2007-10-21
> **anubhavrocks said:**
> try this 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.con.bak
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
sudo /etc/init.d gdm restart
```

The first two lines seem to go through but when I type the last line I get the error:

sudo: /etc/init.d: command not found

---

### Post by toontastic on 2007-10-21
I've tried rebooting even though the last line of code gave me an error and I can finally get a GUI wahoo. Unfortunately however everything looks massive. I tried changing the screen res but I only seem to have the option of 800x600. Any ideas ?

---

### Post by anubhavrocks on 2007-10-21
I think you should select the right driver and things should work after that
```
displayconfig-gtk
```

---

### Post by toontastic on 2007-10-22
> **anubhavrocks said:**
> I think you should select the right driver and things should work after that
```
displayconfig-gtk
```

Thats for that I'll give it a go tonight.

---

### Post by toontastic on 2007-10-22
Ok I tried that and got this

```
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 11, in <module>
    app = DisplayConfig("/usr/share/displayconfig-gtk/displayconfig.glade")
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 116, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/usr/lib/python2.5/site-packages/displayconfig/displayconfigabstraction.py", line 72, in __init__
    self.xorg_config = xorgconfig.readConfig(xorg_config_filename)
  File "/usr/lib/python2.5/site-packages/displayconfig/xorgconfig.py", line 657, in readConfig
    raise ParseException,"Unknown line type '%s' on line %i" % (first,line)
displayconfig.xorgconfig.ParseException: Unknown line type 'disable' on line 13
phillip@ubuntu:~$ 

```

---

### Post by toontastic on 2007-10-23
I've just thought maybe that was the correct message to get I just had to type more after it ? Anyone care to shed any light ?

Thanks for all the help so far by the way.

---

### Post by anubhavrocks on 2007-10-23
Okay it seems something is wrong with displayconfig.
Now i dont have a solution to that,but a clever workaround would be,
Assuming things work okay with the Live CD,copy the xorg.conf in the live session and use that xorg.conf for the installed version.I guess that should do the trick.

---

### Post by toontastic on 2007-10-23
> **anubhavrocks said:**
> Okay it seems something is wrong with displayconfig.
Now i dont have a solution to that,but a clever workaround would be,
Assuming things work okay with the Live CD,copy the xorg.conf in the live session and use that xorg.conf for the installed version.I guess that should do the trick.

Would I have to download it from the version 7.10 CD as I'm assuming that file has been updated from 7.04 ? Looks like I'll have to spend today downloading :)

Thanks for that I'll give it a try and post back tonight.

---

### Post by toontastic on 2007-10-24
Just to let you know reverting back to the old file worked great and I'm finally up and running, just go to get my graphics card drivers working now. Thanks for all the help guess this one is solved now :)

---

### Post by toontastic on 2007-10-25
After much trying to get the graphics card working I had another go at the LiveCD and realised that all the graphicy things were working fine and that was without the restricted drivers working. So I made the decision to install the OS again and it worked perfectly, in fact a few things which were missing are now there as well so it's better than ever and faster. 

So if anyone is having any problems with the update I would reinstall. Just back up your home folder and you'll be fine took me about 30 mins max to do as I just formated the current linux partitions and installed it there.

Thanks again for all your help.

---

