---
title: "Nautilus samba share browsing broken?"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by smbm on 2009-03-11
Is anyone else finding Nautilus samba share browsing broken?

Just wondering if it's something peculiar to my network. If not I'll file a bug.

I can still access the machines with smb://hostname but can't browse for them.

This thread seemed to touch on it:

[http://ubuntuforums.org/showthread.php?t=1053202](http://ubuntuforums.org/showthread.php?t=1053202)

Ultimately it's about something else though so I didn't want to take it off topic.

Cheers.

---

### Post by JohnJackson on 2009-03-11
It's samba testing day tomorrow, might be a good time to bring it up

---

### Post by smbm on 2009-03-11
There seems to be an existing bug about it:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/320547/](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/320547/)

Hopefully it will be fixed in the bug day :)

---

### Post by SketchyClown on 2009-03-11
Yes there is definitely something broken.

Normally I can connect to my USB drive that is connected to my router through Nautilus & the "Connect to Server" dialogue where I will enter the details and when it asks for a password I just leave it blank and select for it to always remember that there is no password. The share mounts on the desktop without fail in 8.10 Intrepid.

Now with Jaunty, it refuses to allow me to leave the password field blank. It demands a password. Needless to say, typing anything in there results in an error.

Hopefully this will be fixed in some upcoming updates.

---

### Post by syko21 on 2009-03-12
Make sure its not simply a configuration issue on your end, pop in a recent livecd and see if you can access the share from there.

---

### Post by SketchyClown on 2009-03-12
From: Setting Up Samba : Ubuntu Community

***[B]"Ubuntu Client***[/B]

 [I][B]Alternate : From the menu at the top select "Location" -> "Connect to a server". In the "Service type" pull down select "Windows share". Enter the server ip address in the "Server:" box and the share name in the "Share:" box. Click "Connect" and then "Connect" again on the second dialog box (no need for a password)."
[/B][/I]


This is how I usually connect to my share, except that now when I go to click "Connect" on the 2nd dialog box where there is usually ***"no need for a password"*** in 8.10 Intrepid, the "Connect" button is grayed out. The button becomes active if you type something in the password box, but it will not allow me to go forward without a password any longer.

Pressing on....

---

### Post by smbm on 2009-03-12
> **SketchyClown said:**
> From: Setting Up Samba : Ubuntu Community

***[B]"Ubuntu Client***[/B]

 [I][B]Alternate : From the menu at the top select "Location" -> "Connect to a server". In the "Service type" pull down select "Windows share". Enter the server ip address in the "Server:" box and the share name in the "Share:" box. Click "Connect" and then "Connect" again on the second dialog box (no need for a password)."
[/B][/I]


This is how I usually connect to my share, except that now when I go to click "Connect" on the 2nd dialog box where there is usually ***"no need for a password"*** in 8.10 Intrepid, the "Connect" button is grayed out. The button becomes active if you type something in the password box, but it will not allow me to go forward without a password any longer.

Pressing on....

Bizarre.

I normally browse for them through the Network option in the places menu.

It seems to have started working again here though. That is after changing no config files and applying no updates.

I'm not complaining though.

---

### Post by SketchyClown on 2009-03-12
> **smbm said:**
> Bizarre.

I normally browse for them through the Network option in the places menu.

It seems to have started working again here though. That is after changing no config files and applying no updates.

I'm not complaining though.

Glad to hear yours started working for you again.

Connecting this way for me is the easiest. It usually works flawlessly and of course it puts a bookmark for the share in my **Places** menu, so then I just click that to instantly mount the share on the desktop without having to even navigate the Network > etc > etc.....

Yes this is very bizarre indeed.

---

### Post by GARoss on 2009-03-15
Having the same issue with Ubuntu jaunty that I had with Kubuntu jaunty. Samba doesn't retain settings.

---

### Post by smbm on 2009-03-15
Which Samba settings are not being retained? Are they client or server settings or both?

---

### Post by SketchyClown on 2009-03-20
Many , many updates but this still seems to be broken. Still trying to connect with the ***Connect To Server*** dialog with no success. Still has the ***Connect ***button grayed out, so unabe to connect without a password.

And of course browsing the shares through the ***Network*** in Nautilus has not made any improvements since Intrepid.

Hoping for good things with the Beta.

---

### Post by scaine on 2009-03-31
I've been using autofs5 with my password-less samba shares since about Alpha 2 (maybe 3) and I've not experienced any issues connecting.

Have you tried autofs or autofs5?  I'm happy to run through how it works if so.

---

