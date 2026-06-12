---
title: "Ubuntu Minimalist Install"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by paxsonsa on 2012-08-22
Hey there guys! I hope you can help me out!

Been trying to install Ubuntu 12.04 on my 27in iMac for well over a week. Its be quite the ride. 

I tried a LiveCD install and every trick people had for prevent this 'Black/Blank Screen' which I assumed was the result of the Graphics Card or! The Fact that its trying to use the display port to display my screen. (Still dont know) 

So I opted for a better approach. Load a basic Command Line System and Build the DE from there after I install the proper drivers. 

Problems:
I think I am having driver malfuctions because when I text the DE by using startx the BG Image loads and the mouse is present however it hangs here forever and never changes. So I cancel startx. 
The log on the terminal says:

```
(WW) fglrx: No matching Device section for instance (BusID PCI:001:0:1) found
```

Which I have no clue it means. After Forum Diving for a bit I tried:

```
andrew@ubuntu:~$ LIBGL_DEBUG=verbose glxinfo
```
and I recieve
```
Error: unable to open display [CODE]

Then I ran

[CODE]sudo fglrxinfo
```
and the response is similar
[CODE] Error: unable to open display (null) [CODE]

What I need:
-For startx to load my DE
-To finish building my System
-For it to work with 3D Acceleration because I am a VFX Artist

System:
27" iMac (late 2009)
Intel i7 Core Processor
AMD ATI Mobility Radeon HD 4850 512 mb Graphics
4 GB RAM
1TB (50GB for Ubuntu)

I am not sure how to fix this. Any suggestion and help would be amazing!

---

