---
title: "nvidia control panel error"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cjnkns on 2009-10-06
Does anyone else have an issue when trying to save changes from the nvidia control panel?

When I open the panel from the terminal - sudo nvidia-settings

Then change the resolution I get an error stating that it is unable to parse the config file or something. 

I'd like to change my resolution is there a way around this?

---

### Post by cjnkns on 2009-10-09
Nobody has a problem setting their screen resolution?
I am the ONLY one?

---

### Post by sdowney717 on 2009-10-09
YES!
you have to do it differently.
from terminal run 
1. sudo nvidia-config
2. gksudo nvidia-settings

if you still have troubles
then you might have to look at the preview
option that shows up when you try to save the changes.
dont select merge with existing xorg.conf
select all the code text
open gksudo gedit
navigate to /etc/X11
open xorg.conf
paste over the text with the new code from nvidia-settings
save it and log out and login.

---

### Post by ToxinPowe on 2009-10-09
I think that you must create /etc/X11/xorg.conf first. Karmic don't use xorg.conf by default.

---

### Post by cjnkns on 2009-10-09
When I try sudo nvidia-config i get command not found.
When I try option 2 I get the nvidia dialog, but when I click 'Save to X Configuration File' I get an error message saying "Failed to prase config ..."

Thanks for your help but I am not sure what else to do here...

---

### Post by cjnkns on 2009-10-09
> I think that you must create /etc/X11/xorg.conf first. Karmic don't use xorg.conf by default.

I checked the directory and I have an xorg.conf file already.


> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


---

### Post by huwshimi on 2009-10-10
> **cjnkns said:**
> When I try sudo nvidia-config i get command not found.
I think it might actually be nvidia-xconfig. Try that instead.

---

### Post by sdowney717 on 2009-10-10
sorry, yes it is sudo nvidia-xconfig.

something about nvidia-settings requires that xorg.conf exist and that something about device is listed or it bombs. 
also unless run as root, it cant write in xorg.conf?

i got to the place that i just hit save configuaration then hit preview and copied and pasted the contents. Also i dont understand the merge with existing xorg.conf, Checking that option always gave me grief.

---

### Post by nilarimogard on 2009-10-10
It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/286424](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/286424)

To be able to save the changes, open nvidia-settings, delete xorg.conf, then click "Save changes" in nvidia-settings and enter the path to where xorg.conf was supposed to be and it will automatically create it (/etc/X11/xorg.conf)

---

### Post by cjnkns on 2009-10-10
> It's a known bug: [https://bugs.launchpad.net/ubuntu/+s...gs/+bug/286424](https://bugs.launchpad.net/ubuntu/+s...gs/+bug/286424)

Finally, fixed it - thanks for all your help!

---

