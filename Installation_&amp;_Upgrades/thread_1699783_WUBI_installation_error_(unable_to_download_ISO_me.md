---
title: "WUBI installation error (unable to download ISO meta data)"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by sffvba[e0rt on 2011-03-04
Hi,

We had an "Installfest" on Wednesday here in the UAE (the first thing like this in the country ever if I am not mistaken) and just about everyone requested us to install via WUBI which we did very successfully via CD and DVD however we where unable to get even one system successfully installed via USB... we kept getting an error right at the end of the process in Windows stating "unable to download ISO meta data..." or something to that extent (I feel stupid for not at least writing it down now :/)...

What where we doing wrong?  This happened using 4 different USB thumb drives, using the "Super OS image of Ubuntu 10.10 and also the standard Ubuntu 10.10 on several different machines running various versions of Windows (even tried safe mode just to see)...



Cheers and thanks
404

---

### Post by bcbc on 2011-03-04
The problem is this:
Wubi can only install from the desktop ISO. So it uses a very simplistic check to make sure of this... the size must be < 900MB (probably 892MB since it's actually 900000bytes).
This excludes the possibility of installing from the DVD image (not a DVD since you can still burn a CD image to a DVD and the size does not change).
But if you create a USB then - depending on the size of the USB - it can easily exceed 900MB.
You can get around this - I believe - by partitioning the USB so that it is < 900000 bytes - and then wubi should succeed (never tried this myself). Or there used to be a --force option.

Anyway - that's probably the main problem.

Once Wubi decides that the install medium check has failed, it then goes to the Net to download the image from there. But I think it's already set an error code - so the next step (downloading the metalink) always fails. And that's the message you see.

That's what I know, mixed with my assumptions. I haven't tried testing it all. I usually just suggest placing the .iso and wubi.exe in the same folder and running wubi from there. This seems to work the best.

---

### Post by bcbc on 2011-03-04
I had a look in the source code and it appears the option is "--skipsizecheck"

So you could create a shortcut to wubi.exe on the USB, and then modify it changing the Target line to read: "wubi.exe --skipsizecheck"

Maybe that will fix it.

---

### Post by sffvba[e0rt on 2011-03-04
> **bcbc said:**
> I had a look in the source code and it appears the option is "--skipsizecheck"

So you could create a shortcut to wubi.exe on the USB, and then modify it changing the Target line to read: "wubi.exe --skipsizecheck"

Maybe that will fix it.

bcbc - Thanks a lot!  The searches online I have tried had been in vain... cheers for the info (I will actually try this out when I have time just to confirm it works too...)


404

---

### Post by bcbc on 2011-03-05
OK... I had a closer look. Not sure about this. 

The --skipsizecheck seems to be skip the disk size checks (whether there is enough space to install - not the size of the install medium).

Apparently you have to supply the --force-wubi when running from a USB to even show the "install inside windows" option. And then it still doesn't bypass the iso size check.

I'm not very familiar with the python code, and the comments are sparse (non-existent).

Actually I think I might have a USB somewhere - maybe I should test this :)

---

### Post by bcbc on 2011-03-05
OK... so this is not a good idea. What I did is try install from a 4GB USB stick. It won't allow you to start the install unless you use the --force-wubi option. 

But then it copies the "ISO" from the USB to the hard drive in preparation for the install. So it basically copies the 4GB usb partition as the ISO. (Good thing I didn't try this with my 16GB stick).

Then as predicted, it still checks the size of the ISO and fails it.

So, this would probably only work if you created an 800MB partition on the USB.

---

### Post by sffvba[e0rt on 2011-03-05
> **bcbc said:**
> OK... so this is not a good idea. What I did is try install from a 4GB USB stick. It won't allow you to start the install unless you use the --force-wubi option. 

But then it copies the "ISO" from the USB to the hard drive in preparation for the install. So it basically copies the 4GB usb partition as the ISO. (Good thing I didn't try this with my 16GB stick).

Then as predicted, it still checks the size of the ISO and fails it.

So, this would probably only work if you created an 800MB partition on the USB.

Sounds to me like installing with WUBI from USB is not a good idea (or very very difficult, which defeats the purpose of WUBI a little :p)... 

Thanks for all the effort... I think I will just ensure I have an external DVD available next time :)


404

---

