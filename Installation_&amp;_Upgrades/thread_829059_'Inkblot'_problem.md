---
title: "'Inkblot' problem"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Over the hill on 2008-06-14
Hello,

I have Ubuntu 8.04 and an Epson Stylus Photo 790 printer. I recently installed 'Inkblot'

When I start the programme an icon appears in the top toolbar with a cross over it. If I right click on the icon I get a small menu inviting me to rescan for printer devices. When I click on this I get the following error message, 'Error No supported printers found, please check your printer and cables and scan for printers again.' I have checked that my printer is on the list of printers  supported by Inkblot. The only thing that I can think of is that I am not using proprietary ink cartridges, even though they are chipped and they did show the ink levels when I used Windows with these same type of cartridges.

Any help would be appreciated

---

### Post by Bruce R on 2008-06-26
Sorry,  but I don't have an answer,  merely to say that my Stylus Photo R220 fails to respond in exactly the same way with 'pukka' cartridges installed,  meaning that I have to re-boot into Windows to find out why Ubuntu 8.04 printing has stopped,  which is a bit of a pain !
So,  it must be an Inkblot 'bug' or hopefully,  just a lacking library-type 'package'.  If I find or am pointed to the latter, I will post again !

Edit PS. Synaptic Addition of 'qink' and use of 'sudo qink' command prouces a display of just four of the six cartridges in my printer,  so see if that helps.
Meanwhile,  I have raised Ubuntu Bug Report #243410 in Launchpad.

---

### Post by wbutchart on 2008-07-10
Im having the same problem with my epson printer...

---

### Post by killerisation on 2008-08-05
Me 2.

---

### Post by coderand on 2008-09-21
I'm using an **HPdeskjet940c** (which is a supported printer with **libinklevel**) and am unable to get **Inkblot** to recognize it. I tried installing **qink** and tried **sudo qink** but it too did not recognize my printer.

I did notice that the **Hardy** repository does not have the current version of **libinklevel**.

Does anyone have anymore ideas or information that could help us? :confused:

---

### Post by coderand on 2008-09-21
So I'm understanding that this problem is an issue with **Inkblot** not having permissions to access the printer? I checked and there is no **lp** group in my **Hardy** installation. I do have an **lpadmin** group which my current user is a part of. Shouldn't that be allowing **Inkblot** access to my printer? :confused:

---

### Post by leech on 2008-09-25
I've been trying to get inkblot to work for several releases.  Seems that you can go into gconf-editor and tell it to look for USB devices.  The problem is that the device names have all been obfuscated.  

I have an HP PSC 1315 and it says it's supported, and I can even go into the hp-toolbox (which is butt ugly on my Gnome desktop) and check the ink levels, but inkblot simply doesn't see the printer.  I also installed 'ink' and it uses the same libs as inkblot (libinklevel4 on Intrepid Ibex) but when I type ink -p usb it says it cannot access /dev/usb/lp0 or /dev/usblp0.

Upon further investigation, looks like there wasn't a /dev/usb/lp0.  I looked at dmesg and found 

```
usblp0: removed
```

So I had to sudo rmmod usblp (because it was still loaded by usbcore) and then sudo modprobe usblp again and...

```
[11408.756909] usbcore: deregistering interface driver usblp
[11412.512385] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
[11412.512722] usbcore: registered new interface driver usblp
```

Now the device is there.  But I still don't have access to it with ink -p usb....  so I looked in /etc/group and there IS a lp group, so I added my user in manually, so I'm about to log out and back in.  Will report after I've done that to see if I can access it.

Leech

---

### Post by leech on 2008-09-25
We're golden!  That worked, now Inkblot works, and apparently I need more ink soon.  16% Color and 13% Black.

So as a quick overview;

Check first to see if you have /dev/usb/lp0 (older versions of Ubuntu would have /dev/usblp0, just use 'ls /dev/usb`TAB``TAB` for those that don't know about the wonderful auto-complete that Bash / Dash has.)

If you don't have a /dev/usb/lp0 or /dev/usblp0 then you need to 
```
sudo rmmod usblp
sudo modprobe usblp
``` 
Then using your favorite text editor (I use nano, but you can use gedit, kedit, etc.)

```
sudo editor /etc/group
```
Do a search or page down for 'lp'  My lp line looked like
```
lp:x:7:
```
Add your user name to it.  For example;
```
lp:x:7:leech
```
Log out, then back in and you should be good to go.  Inkblot should now work as it should.  Idealistically, this should be fixed in Hal.  usblp0 should be in the lpadmin group, unless there is a specific reason it isn't, not sure.  I just thought it'd be easier this way.

Not sure if this will survive a reboot.  I don't even know why it was removed for me in the first place.  It shouldn't have been.

Leech

---

### Post by cariboo on 2008-09-25
Have a look at this bug for a work around:

[https://bugs.launchpad.net/ubuntu/+source/inkblot/+bug/243410](https://bugs.launchpad.net/ubuntu/+source/inkblot/+bug/243410)

Jim

---

### Post by coderand on 2008-11-03
Leech's instructions from above worked. Thank you Leech!

I made the changes using the current release Ubuntu 8.10 Intrepid Ibex and Inkblot was then able to recognize my HP Printer and report the correct ink levels. Even on restart the changes held.

Don't forget to check here [http://libinklevel.sourceforge.net/#supported]("http://libinklevel.sourceforge.net/#supported") to see if your printer is even supported through Inkblot.

I don't see an option to choose this, but I would say this thread is now solved. Thanks for everyone's help!

---

### Post by antony_css on 2009-07-27
> **leech said:**
> 
Then using your favorite text editor (I use nano, but you can use gedit, kedit, etc.)

```
sudo editor /etc/group
```
Do a search or page down for 'lp'  My lp line looked like
```
lp:x:7:
```
Add your user name to it.  For example;
```
lp:x:7:leech
```
Log out, then back in and you should be good to go.

Do you mean this?
```
sudo adduser *[username]* lp
```

---

