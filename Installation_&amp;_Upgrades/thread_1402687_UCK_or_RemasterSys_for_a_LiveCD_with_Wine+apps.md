---
title: "UCK or RemasterSys for a LiveCD with Wine+apps?"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by qyot27 on 2010-02-09
I'm trying to get a remastered disc of 9.10 together so I can quickly log on to the LiveCD session and go to work on the more powerful comp I have access to (but unfortunately cannot do an install on - for the tasks I'm needing to do, VirtualBox isn't an option either).

So I went with UCK to facilitate the remastering process, and everything went well, the ISO came out fine with all its updates intact, excess languages trimmed out, and Wine enabled (I did test under VirtualBox just to make sure), but I couldn't seem to be able to install any programs under Wine during the customization process so that they'd be on the disc as well.  It kept complaining that my main Ubuntu .wine directory couldn't be found on the LiveCD (no duh, obviously).

So my question is, is there any way for UCK to allow me to install programs into the Wine setup I created on the disc?  Is there a system-wide folder I could use to substitute for it, if I can't actually make that happen (the app I actually need to use doesn't require installation, just unpacking, but I need the /home/user/.wine system structure in place so that I can put it in Wine's $PATH).  Yeah, I could be happy with the fact I do have a working Wine installation on the LiveCD, but I don't want to have to bother with carting the program(s) I need around with me on a flash drive every time I need to go into this live session.

In looking around, though, it seems that RemasterSys can take the existing install on my main setup and turn it into a LiveCD - I assume this would keep my .wine folder and Wine's $PATH intact on the CD so I wouldn't have to worry about it?

---

