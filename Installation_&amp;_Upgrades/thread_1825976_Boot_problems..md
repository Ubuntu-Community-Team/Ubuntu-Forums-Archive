---
title: "Boot problems."
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by chromefourfour on 2011-08-16
So I installed wubi and it did not show up in my boot manager when i restarted, so i went into My Computer, Properties, Advanced and manually changed the default os to ubuntu. Now I have no idea how to change it back into windows, and i would very much like to. I am using windows xp professional by the way. thanks in advance!

---

### Post by kranezor on 2011-08-16
Hi! 
just boot up from installation cd of xp
and select repair menu
:o

---

### Post by chromefourfour on 2011-08-16
Oh yeah, I forgot to mention I don't have a back up cd, and I didn't make one prior to wubi because i thought i could easily remove it, as it stated.:confused:

---

### Post by bcbc on 2011-08-16
You can edit the boot.ini but be very careful when doing it - because if you make a mistake you could stop Ubuntu booting as well.

If you installed Wubi on C:, these are the instructions

```
# backup first
cp /host/boot.ini /host/boot.ini.bu
# edit the file
nano /host/boot.ini
```

e.g. mine looks like this:

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

```

Once you're done editing, hit Ctrl+O and Enter to write the changes, and Ctrl+X to exit.

I'd stick to adding or modifying the **timeout=xx**. Try not to hit enter as the linux line endings aren't the same as windows line endings and that could be enough to stop Windows booting. 

You can also use "gedit /host/boot.ini" if you don't like *nano*

Hope that helps.
PS you might want to create an ubuntu cd you can boot from in case something goes wrong ;)

---

### Post by chromefourfour on 2011-08-16
I can't find the boot.ini, that's the reason i had to do it from My Computer in the first place, so i'm not quite sure what to do right now. Thanks for your reply

---

### Post by bcbc on 2011-08-16
Did you install Wubi on windows C: drive? If not, e.g. you did it on D:, then you need to click the home icon (top left of unity bar) and then look for the C: drive in the left side and mount it. Then you can identify the mountpoint (either the label or uuid) and change the instructions I gave above:
i.e.

gedit /media/LABEL/boot.ini
or
gedit /media/xxxx-xxxx-xxxx-xxxx/boot.ini (xxx=uuid)

---

### Post by chromefourfour on 2011-08-17
Hm. After I rebooted, there's a boot.ini file in my host folder now, it has the exact same look as yours but windows does not show up still. In my startupmanager, it does not even show a windows. And yaaa I installed wubi in the C: Drive

---

### Post by bcbc on 2011-08-17
Can you post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") please?

---

