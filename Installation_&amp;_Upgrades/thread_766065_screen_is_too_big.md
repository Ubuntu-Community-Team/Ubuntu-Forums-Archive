---
title: "screen is too big"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by HunkieChan on 2008-04-25
i just updated my beta hardy to final release..and then installed the restricted drivers..after i installed nvidia.. my screen resolution is 800x600 now.. how can i change it ? also, when i started my computer.. a black screen came up for password but then it suddenly disappeared and the normal login screen showed up.. i think its due to nvidia driver.. so how can i change the resolution ? thank you

---

### Post by HunkieChan on 2008-04-25
anyone please ?

---

### Post by SunnyRabbiera on 2008-04-25
did you try screens and resolutions?
its hidden now (for some oddball reason)

---

### Post by HunkieChan on 2008-04-25
i tried it from preference ..there is only option and its 800x600

---

### Post by bbmak on 2008-04-25
I got the opposite problem after installed 8.04
My screen is too small.
Only 800x600 or smaller

---

### Post by howlingmadhowie on 2008-04-25
this seams to be a real problem atm. i think it's because xorg 7.3 doesn't recognise enough monitors correctly. on my new notebook it worked a charm allowing me to set dual-display correctly and so on. my 20" desktop monitor from 1999 does not get recognised, however, and i only get the option of 800x600

---

### Post by HunkieChan on 2008-04-25
is there a solution then ?

---

### Post by iaculallad on 2008-04-25
You could try this one:

Issue the command sudo gedit /etc/X11/xorg.conf

and locate the Screen section and insert the codes without the asterisk below the Device

Section "Screen"
*Identifier	"Default Screen"
*Monitor		"Configured Monitor"
*Device		"Configured Video Device"
	
          DefaultDepth 24
          SubSection "Display"
          Depth 24
          Modes "1280x1024"
          EndSubSection

EndSection

---

### Post by HunkieChan on 2008-04-25
ok,i created some new problem..i just logged on hardy heron and the screen resolution changed itself somehow but it wasnt good enought.. cause it was 1600x(something).. i need 1200x800 .. so i tried to change and now my screen is static-y.. i cant say anything.. ugh.. how do i fix this now ?

---

### Post by iaculallad on 2008-04-25
Go to System->Preferences->Screen Resolution. check if you could adjust your existing resolution.

---

### Post by HunkieChan on 2008-04-25
i cant, its to static-y.. i cant see anyything.

---

### Post by iaculallad on 2008-04-25
What video adapter are you using?

---

### Post by rupierto on 2008-04-25
Don't know if this can resolve:

[http://ubuntuforums.org/showpost.php?p=4789536&postcount=110](http://ubuntuforums.org/showpost.php?p=4789536&postcount=110)

---

### Post by HunkieChan on 2008-04-25
> **iaculallad said:**
> What video adapter are you using?

umm, dont really know

guys, i cant even see screen anymore.. so anything i do.. i have to do from alt+ctrl+f1.. can anyone please help ?

---

### Post by HunkieChan on 2008-04-26
nevermind guys, somehow my screen was fixed . so i downloeaded envy and installed nvidia using that. thanks guys

---

