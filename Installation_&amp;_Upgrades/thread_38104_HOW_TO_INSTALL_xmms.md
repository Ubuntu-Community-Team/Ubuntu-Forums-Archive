---
title: "HOW TO INSTALL: xmms"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by juzdandyjane on 2005-05-30
I have instructions but i can't make it work. I have never used Linux before. If you know how to install xmms on version 5.04 please explain in very simple terms as if you are speaking to a 5 year old.   ](*,)

---

### Post by tread on 2005-05-30
[http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)
Edited to add: its a really nice guide, I'd suggest reading to check if instructions for installing any particular package are given there.

---

### Post by juzdandyjane on 2005-05-30
I already tried there. Still don't understand.  :???: 

I need something A lot easier.

---

### Post by Seti on 2005-05-30
Open a terminal (console) and enter ```
sudo apt-get install xmms
``` 
it will prompt you for your user passwd and you should be good to go.

---

### Post by SAPnet on 2005-05-30
[QUOTE=Seti]Open a terminal (console) and enter ```
sudo apt-get install xmms
``` 
it will prompt you for your user passwd and you should be good to go.[/QUOTE]
 When I open XMMS and try to play an MP3, it seems to crash XMMS, i can't do anything on it except move it about the screen... any ideas?

Is there a way of making totem play MP3s?

Thanks,
Brad.

---

### Post by tread on 2005-05-30
Check what the output plugin for xmms is .. if it is esd, and esd isn't running that would be a problem. Guess you can just experiment ... try different output plugins till one works (not the diskwriter plugin :))

---

### Post by Fab on 2005-05-30
[QUOTE=SAPnet]When I open XMMS and try to play an MP3, it seems to crash XMMS, i can't do anything on it except move it about the screen... any ideas?

Is there a way of making totem play MP3s?

Thanks,
Brad.[/QUOTE]
 please, go to ubuntuguide.org and look at "enable extra repos" "multimedia codecs" and "alsa"

---

### Post by SAPnet on 2005-05-30
ok, cheers every1.

I'll give it a go!

Brad.

---

### Post by juzdandyjane on 2005-05-30
I tried what you suggested (sudo apt-get install xmms), and I get this:

"Package xmms is not available, but is refered to by another package. This may mean that the package is missing, has been absoleted, or is only available from another source
E: package xmms has no installation candidate"

please help!

Thanks..

---

### Post by asianette on 2008-07-01
> **juzdandyjane said:**
> I tried what you suggested (sudo apt-get install xmms), and I get this:

"Package xmms is not available, but is refered to by another package. This may mean that the package is missing, has been absoleted, or is only available from another source
E: package xmms has no installation candidate"


I get the same error. However, when I run the synaptic GUI, I can only install the packages for XMMS2. Is this just a more recent version? Do I need XMMS or will XMMS2 suffice?

I'm on Debian 4.0 Lenny Kernel 2.6.25

---

### Post by niyonk on 2008-07-01
> **asianette said:**
> I get the same error. However, when I run the synaptic GUI, I can only install the packages for XMMS2. Is this just a more recent version? Do I need XMMS or will XMMS2 suffice?

I'm on Debian 4.0 Lenny Kernel 2.6.25

Hi, first of all you do realise this is a 3 year old thread :lolflag:
Second of all, i am not sure about you. Since you are using Debian and i am using Ubuntu.

Thirdly, according to this _[link]("http://wiki.xmms2.xmms.se/wiki/Main_Page")_  yes, it is the latest version. :)
You do not need the first one in order to get the second version.

Cheers :biggrin:

---

