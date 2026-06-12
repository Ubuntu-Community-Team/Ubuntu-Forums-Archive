---
title: "Desk top issues"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clifdavis on 2010-04-24
First let me say I apologize for what ever bad terminology I may use. 

I have installed 10.04 in dual boot and am enjoying it tons. About the only time I use winders now is to run my sim racer. (rFactor) 

A couple of days ago, I did the update and there were about 240 of them and after the reboot and things came up normal, when I minimize things where they used to be at the bottom of the screen on the bar, now it is gone and if I minimize them they disappear. They don't go to another desk top or workspace, I didn't have that turned on. They are just gone. Also now on each side of the screen I have what looks like tiled black sections that don't appear to do anything. 

Again, I apologize if my terms are wrong.

Thanks,
Clif

---

### Post by howefield on 2010-04-24
> **clifdavis said:**
> when I minimize things where they used to be at the bottom of the screen on the bar, now it is gone and if I minimize them they disappear.

Try right clicking the panel and select Add to Panel, and add Window List.

> Also now on each side of the screen I have what looks like tiled black sections that don't appear to do anything.

Can you post a screenshot ?

---

### Post by BrokeMahPC on 2010-04-24
Hardware? - particularly, what is your graphics card model and chip number, did you enable any drivers in System-admin-Hardware drivers? Is it a laptop or desktop PC.
Please type these in a  terminal:
     ```
lspci | grep VGA 
``````
sudo lshw -C video 
```The 2nd command may sometimes also list the driver you are using under   - configuration.

If you just want to restore the default panels and put them back to how they  looked at install, use this, may work in your case:
     ```
gconftool-2 --recursive-unset /apps/panel 
```
     ```
killall gnome-panel
```

---

### Post by BrokeMahPC on 2010-04-24
RE the black panels at each side of the screen - what wallpaper are you using? 

If you use a wallpaper that does not match your screen resolution it may not be displayed with the correct style - right click on desktop->change desktop background->Backgrounds->Style:
In the style menu there are several options, tile, zoom, centre, stretch, span - click on each one in turn and see if the black panels disappear.
Hopefully it's this simple!

---

### Post by clifdavis on 2010-04-26
I apologize for taking so long to supply answers. Below are listed the retrieved data from the 2 suggested Terminal queries. 

This morning when I logged into it was as I have explained  and now when I logged in, it has a gray frame around the edges. I have not changed the appearance intentionally. I wouldn't know how to do this. HA.
Thanks.
Clif

01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2) *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable) memory:f8000000-f9ffffff ioport:c800(size=128) memory:fcee0000-fcefffff(prefetchable)

---

### Post by x-shaney-x on 2010-04-26
Sounds like your panels have gotten messed up.

The tiled sections at each side of the screen are almost certainly extra panels (the background image of the panel goes tiled when they are vertical).
And the vanishing windows will no doubt be down to the taskbar/window picker missing.

Following BrokeMahPC's advice a couple of posts up to reset the panels would probably be the best idea.

---

### Post by clifdavis on 2010-04-26
OK, thanks. I will give that a try... 
Clif

---

### Post by clifdavis on 2010-04-26
Wooo hooo, I now have not only the bottom bar with the minimized clickables but also the 4 extra desktops I wanted. super job, thanks.
Clif

---

### Post by paul.drover on 2010-04-26
You guys are fabulous!

I just lost all of my panels on my desktop. No Applications/Places/System, nothing! I was about to panic when I discovered that right-clicking on my desktop would let me create a launcher. So I found firefox and make a desktop launcher for it. Launched firefox and came straight to the forums, searched for "disappear panel", and found this thread. The panel reset commands worked fabulously! I've now got my panels back, all in the space of 20 minutes. I'm so relieved. Thanks guys.

Now, if only knew why they disappeared in the first place.

Paul.

---

