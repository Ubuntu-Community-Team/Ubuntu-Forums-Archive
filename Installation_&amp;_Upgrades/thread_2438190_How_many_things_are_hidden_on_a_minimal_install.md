---
title: "How many things are hidden on a minimal install?"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by soufianta on 2020-03-07
Hello,

I'm trying to figure out how many tools,scripts,services are installed & hidden with a minimal ubuntu install (netinstall). I wanted to keep my install simple,stupid !! I do not want to have some bloat, spyware, unwanted crap or I should just install another non-bloated distro :-).

Thanks.

---

### Post by speartip on 2020-03-07
That depends on exactly what You're installing through the minimal install. Are you installing a Desktop Environment or not? If so which one? If you choose a standard DE you will have more or less the same number of packages as a standard install. Some DEs offer a Minimal version, which will give you enough to get going, then you install whatever you want on top. (Budgie & Xfce come to mind) I find generally Ubuntu Distros don't come with much bloat compared to some distros. Tell us exactly what you want.

---

### Post by TheFu on 2020-03-07
> **soufianta said:**
> Hello,

I'm trying to figure out how many tools,scripts,services are installed & hidden with a minimal ubuntu install (netinstall). I wanted to keep my install simple,stupid !! I do not want to have some bloat, spyware, unwanted crap or I should just install another non-bloated distro :-).

Thanks.

All the popular distros are bloated.  Any Linux over about 20MB is bloated.  Used to be any distro over 5MB was bloated.
Do you use DNS?  Is that considered "spyware" in your world?  
Do you use Chrome as a browser?  That is most definitely spyware.  Chromium probably is as well, since about 20 necessary network needs phone home to google's infrastructure.  Same for firefox.  They have anti-malware capabilities ... which has every page you visit sent to their servers to look up that page in a DB.  Is that spyware or just smart safe browsing?

Are things "hidden" because you aren't aware of them, but everyone else knows?  It is very hard to keep up with network services used by every program.  The easy answer is to block all inbound and outbound network requests, then manually specify which are allowed.  That "easy answer" isn't nearly as easy as it sounds to actually implement.

Check out TinyCore for less bloated distros.  They have a 16MB version with X/Windows.  What more could you want?
[http://tinycorelinux.net/](http://tinycorelinux.net/)

---

### Post by soufianta on 2020-03-07
First, we have to agree on the signification of «*bloat”. For me, bloat means something I’m not aware of it (hidden), something too big that can be much more smaller/minimalist and something unnecessary ! A minimal install is for me only the base system (no DE etc.) ! So, is there some hidden bloat on a minimal Ubuntu install? Ps: @TheFu: You’re right but that kind of spyware (google chrome, dns, etc.) should be spied too but I’m already aware of that :-). I’m asking this question because I wanted to have an install similar to an Arch Linux one = KISS and only things I’ve personally chosen :-). Is that possible in 2020???

---

### Post by him610 on 2020-03-07
Sounds like you should consider the ubuntu mini.iso 
You can read about it here, [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by soufianta on 2020-03-08
@him610: I was obviously already talking about the mini iso (minimal install) and not about the full iso choosing "minimal installation" that installs everything then uninstall the bloat (what's IMO another ridiculous thing). So if I install only the base system via de mino iso, should there be only the base system like for every distro (without bloat)? And if I upgrade my system, did I upgrade only my installed base system or should there be other crap installed ? I hope you're now understanding what I meaned :-)

---

### Post by speartip on 2020-03-09
If you install from the Mini ISO & skip the 2nd part of the installation, you will only have the base system with no GUI. You will then need to run & install everything you want from a shell.

---

