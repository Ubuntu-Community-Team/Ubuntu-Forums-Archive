---
title: "Install on Acer C300 tablet freezes"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by iubun22_yo on 2010-08-24
Hi,

I am new to linux & ubuntu, & have played around with a few installs & put it on a USB ok.

But when I'm installing 10.04 on the Acer I get stuck at the same place, either from a Live CD or to the hard drive or usb.

If left to boot from a LiveCD, it seems to freeze when the gui is about to load. I get the ubuntu boot logo, but as I think when it switches to the gui..it freezes.

So if I bring up the text menu & set vga=ask & use any vga mode it will proceed ok  until failing with the following messages.

===

init - ureadahead -  other main process ( 1048 ) terminated with status 4 .
ditto but with ( 1049 )

[76.661921] acer-wmi: No or unsupported WMI interface, unable to load
* Setting sensors limit    [OK]

====


Now I presume it's probably the Wacom Tablet device is failing, or something linked with. Although I am able to use another tablet PC with a Wacom, that runs ok out of the box.

I've tried the netbook install but still the same results.

I'm not sure what the WMI interface is (Wacom Media Interface???) 

Can any one point me in the right direction? Or any ideas? 

Is 10.10 likely to fix this?

Any info will be greatly appreciated.

Regards


PS. post9567832 in general help seems to expain the WMI.  Seems blacklisting is the way 2 go.


Except how do I do that on a live CD install???

=============================
Ok problem Solved 

By using boot option 

i915.modeset=1 


Thanks to this thread

[http://ubuntuforums.org/showthread.php?t=1558311](http://ubuntuforums.org/showthread.php?t=1558311)

and 

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

