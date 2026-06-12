---
title: "intrepid ibex/firefox/cpu usage"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by em3ry on 2008-11-30
after upgrading to 8.10 intrepid ibex firefox is consuming way more cpu cycles than before. even when its just sitting there.  any idea why or what I can do about it?


if I decide that I should go back to 8.06 is there any way to un-upgrade or would I  just have to reinstall from cd?

---

### Post by scottmac112 on 2008-11-30
You'll have to reinstall from the disc. And are you sure it's Firefox and not Compiz or some other crap like that?

---

### Post by em3ry on 2008-11-30
it is firefox but its only when I have live365.com (internet radio) playing.  it uses flash.  I never figured out how to get it to use rhythmbox.  it didnt use so much cpu power under 8.06.  

system monitor just says that firefox uses 20% cpu and pulseaudio about 5%.  not very helpful.

---

### Post by em3ry on 2008-11-30
I'm installing streamtuner right this second. if it works well enough then it may all be moot.

---

### Post by em3ry on 2008-11-30
> **em3ry said:**
> I'm installing streamtuner right this second. if it works well enough then it may all be moot.

I'm not getting anywhere with this. I found this though:
[http://swiss.ubuntuforums.org/showthread.php?t=981207](http://swiss.ubuntuforums.org/showthread.php?t=981207)

---

### Post by em3ry on 2008-11-30
the article says:
Perform a search on an artist and select a stream. You will get a "play.pls" file. Save this file and rename with a meaningful radio name.
For example quartet_radio.pls
Open with xmms and enjoy.

I installed xmms2 through synaptic but when I right click on the file and go to 'open with' there is no option for xmms or xmms2.  then I went to 'use custom command' (at the bottom) and entered 'xmms2' and that didnt do anything then I tried 'xmms" and it said that it couldnt locate such a program.  

darn. this looks like just what I need but as usual I just cant get it to work and have no idea why.

am I supposed to follow the name of the program with some kind of...what do they call it...a variable thing.  like this: 
%C

---

### Post by em3ry on 2008-11-30
I'm going to try installing medibuntu and see if that makes any difference. 

 if I can stay awake that long.


edit: dont know if it matters but here is more of what the article says:
Perform a search on an artist and select a stream. You will get a "play.pls" file. Save this file and rename with a meaningful radio name.
For example quartet_radio.pls
Open with xmms and enjoy. Install w32codecs (if legal in your area) to decode the mp3pro streams.

The stream is kind of ugly:

Code:

[playlist]
NumberOfEntries=1
File1=http://www.live365.com/play/312423?auth=d2e64adc243071ac76a6d8d103a6afb3-1226634525-quartet4ever&tag=live365&token=0a7a717a7cdfd5ca61340c6f9f8119b5-4819130080400000&sid=**.**.250.25-1226512941889198&lid=803-usa&from=pls

Hope this reduces the agony units for playing internet radio on older machines.

---

