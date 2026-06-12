---
title: "installation problem"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Caesum on 2008-03-05
Hi,

I've just put together a new system with a Q6600 and GT8800 graphics card. I've downloaded the 64-bit ISO and tried to install it - the initial screen comes up with options and I've tried changing the graphics mode quite a few times. When it starts installing the screen goes blank and there is some cd activity for a short period followed by minutes of nothing....... Sometimes I get four lines of text ending in [ok], the last one of which is something about Running local boot strips (/etc/rc.local/) but that's all I can get. Should I try the 32-bit version? As there is currently no OS on the machine I can't check anything out or change booting from the CD,

Thanks

---

### Post by nutz on 2008-03-05
> **Caesum said:**
> Hi,

I've just put together a new system with a Q6600 and GT8800 graphics card. I've downloaded the 64-bit ISO and tried to install it - the initial screen comes up with options and I've tried changing the graphics mode quite a few times. When it starts installing the screen goes blank and there is some cd activity for a short period followed by minutes of nothing....... Sometimes I get four lines of text ending in [ok], the last one of which is something about Running local boot strips (/etc/rc.local/) but that's all I can get. Should I try the 32-bit version? As there is currently no OS on the machine I can't check anything out or change booting from the CD,

Thanks

Check the CD to make sure it burned correctly first. I have had this same issue on some Core 2 Duo machines. I don't think Intel uses the same 64 bit implementation that AMD does. If the CD is found to be free of defects then give the 32 bit version a try. I don't know why but the 64 bit capable Intel processors don't seem to like running in 64 bit mode as well as the AMD processors do. That is the case in my experience anyway.

---

### Post by Caesum on 2008-03-05
Finally managed to get ubuntu installed using the alternate iso. Now when it starts up I get a blank screen and nothing happens, and my monitor appears to be on standby. I booted up in recovery mode and that seems to get me in fine but now I'm stuck at the prompt and wondering what to do next. I tried "startx" and get a load of messages followed by 'fatal server error: no screens found'. What should I be doing ?

---

### Post by fafadex on 2008-03-05
i also have a problem installing ubuntu... i downloaded the 64bit and also got a chance to copy a 32bit version... i tried them both but it didnt workd... i always get the garbled screen... btw im trying to install it to my laptop with pentium dual core processor... 1GB ram... 80GB hdd... 
the first one was the 64bit, it didnt work, it says about the incompatibility so i tried the 32bit... then i got the garbled screen... so i tried them to my desktop pc... with amd 64bit processor... 2gb ram... but the result are the same... :( what should i do? please help me... i am really new to ubuntu...

---

### Post by bullgr on 2008-03-05
> **fafadex said:**
> i also have a problem installing ubuntu... i downloaded the 64bit and also got a chance to copy a 32bit version... i tried them both but it didnt workd... i always get the garbled screen... btw im trying to install it to my laptop with pentium dual core processor... 1GB ram... 80GB hdd... 
the first one was the 64bit, it didnt work, it says about the incompatibility so i tried the 32bit... then i got the garbled screen... so i tried them to my desktop pc... with amd 64bit processor... 2gb ram... but the result are the same... :( what should i do? please help me... i am really new to ubuntu...

I don't thing its the incompatibility of 64bit.
The garbled screen makes me suspicious for the graphic card.
What graphic card do yoy have?

---

### Post by fafadex on 2008-03-26
> **bullgr said:**
> I don't thing its the incompatibility of 64bit.
The garbled screen makes me suspicious for the graphic card.
What graphic card do yoy have?

its just a buil-in video from my laptop
im not sure what it is...

---

