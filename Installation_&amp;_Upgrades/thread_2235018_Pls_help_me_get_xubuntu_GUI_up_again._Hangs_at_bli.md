---
title: "Pls help me get xubuntu GUI up again. Hangs at blinking underscore. (see screenshots)"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by gnormal on 2014-07-18
- after upgrade 12.04 to 14.04 things seemed a bit unstable.  i read around and was (am) convinced i should stick with 14.04 but change to xubuntu on this ol` weezer box.
- I followed [these directions.]("https://sites.google.com/site/easylinuxtipsproject/alternative")
- I had it working.
- the final step on that page sent me to a list of nice mods.  the first mod was to update xubuntu.  i did.  **i ALSO SIMULTANEOUSLY updated to the nvidia driver in the system preferences instead of the generic.  so, i waited for both processes to finish downloading and installing.  afterward, there were TWO dialog boxes (as expected) prompting me to restart.**  so i restarted and since then, can not make it to the desktop. :((  [SIZE=1](i now know i should not have done that.)[/SIZE]
- heres what happens, in order: 
- [1 "this session is gonna be low-res mode. fix it yourself."]("http://i.imgur.com/NuBaI8C.jpg") 
- [2 "im going in- low res is fine.  just going to select nvidia myself in prefs."]("http://i.imgur.com/nXbwzxO.jpg")
- [3 "ok here goes the temporary low res session... hold on..."]("http://i.imgur.com/jLdBtII.jpg") 
- [4 -fail- cursor just blinks and wont go any farther.]("http://i.imgur.com/uEwG3Qn.jpg") 

- i already tried apt-get install --reinstall xubuntu-desktop, grub failsafe video, reinstalled other stuff.  over the course of the last 4 hrs.... i feel like im close...
- im hoping that jockey-text command could help to stick the generic neuveau driver back in for now, but that cammand is not found, and apt-get install jockey-text didnt work.  thats about the level i am with ubuntu.  im comfortable in linux but not with hardware drivers or any particular flavors.

my fix has to be via command line.  i can still get to command line with ctrl-alt-f1 when its displaying one of the 3 dialog boxes above.  
"[FONT=courier new]lspci | grep VGA[/FONT]" reports that i have a G84GL Quadro FX 1700.

any ideas?  i dont mind reinstalling anything short of the whole os.  i dont want to do a clean install back to 12.04 because the whole system is just fine, sitting there, if only it could display.


thanks

---

### Post by dannyboy79 on 2014-07-18
when you're logged into the tty1 session, can you pastebin your /var/log/Xorg.0.log so we can see what the X server is logging? you should be able to use the following command
```
pastebinit /var/log/Xorg.0.log
```
if it says that pastebinit isn't installed, then simply install it with the following
```
sudo apt-get install pastebinit
```

---

### Post by gnormal on 2014-07-19
this is prior to screenshot 2 above:  [http://paste.ubuntu.com/7817971/](http://paste.ubuntu.com/7817971/)
this is prior to screenshot 3 above:  [http://paste.ubuntu.com/7817992/](http://paste.ubuntu.com/7817992/)
this is prior to screenshot 4 (freeze) above:  [http://paste.ubuntu.com/7817995/](http://paste.ubuntu.com/7817995/)
After i hit ok on screenshot 3 i can no longer ctrl-alt-f1 (tried to jab it really quick a couple times but couldnt catch command line before hanging).

---

### Post by dannyboy79 on 2014-07-19
if i were you i would try to completely remove all traces of the nvidia driver and just try to get the default nouveau driver working

---

### Post by gnormal on 2014-07-19
good plan!  can you tell me how to get rid of all traces?

isn`t it already loaded?


[   771.458] (==) Matched nvidia as autoconfigured driver 0
[   771.458] (==) Matched nouveau as autoconfigured driver 1
[   771.458] (==) Matched modesetting as autoconfigured driver 2
[   771.458] (==) Matched fbdev as autoconfigured driver 3
[   771.458] (==) Matched vesa as autoconfigured driver 4
[   771.458] (==) Assigned the driver to the xf86ConfigLayout
[   771.458] (II) LoadModule: "nvidia"
[   771.459] (WW) Warning, couldn't open module nvidia
[   771.459] (II) UnloadModule: "nvidia"
[   771.459] (II) Unloading nvidia
[   771.459] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   771.459] (II) LoadModule: "nouveau"
[   771.459] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   771.472] (II) Module nouveau: vendor="X.Org Foundation"
[   771.472]  compiled for 1.15.0, module version = 1.0.10
[   771.472]  Module class: X.Org Video Driver
[   771.472]  ABI class: X.Org Video Driver, version 15.0

---

### Post by gnormal on 2014-07-21
i reinstalled.  even that had trouble. no keyboard or mouse response.  i had to install side by side.
thanks though.

---

