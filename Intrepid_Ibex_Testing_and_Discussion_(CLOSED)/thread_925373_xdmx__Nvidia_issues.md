---
title: "xdmx / Nvidia issues"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AmitDeshwar on 2008-09-20
Hi

I'm running Intrepid Ibex alpha 6.  My regular X session works just fine with nvidia drivers.  
I'm trying to use xdmx to use my laptop as a second monitor.

Currently I'm trying to xdmx to work just on my computer.  I open a naked X session (:1) by running "X :1  &"
Then I launch xdmx and add that naked x session to it by running "xdmx :2 -display 127.0.0.1:1"
Xdmx then seg faults.  By looking at my xorg.1.log file I see the following errors at the very end of the file:

(EE) NVIDIA(0): EVO Push buffer channel allocation failed
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Failed to allocate EVO DMA push buffer
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(EE) NVIDIA(GPU-0): Failed to map CURSOR PIO for CRTC 0

Fatal server error:
AddScreen/ScreenInit failed for driver 0

I've tried googling but there's not much on that error and the xdmx documentation is fairly sketchy.  

Hardware: Asus P5Q Deluxe w/ EVGA 9800 GT.

Does any have any ideas on what the problem could be?

---

### Post by overdrank on 2008-09-20
Moved :)

---

### Post by sweetsinse on 2008-10-10
i too am trying to get Xdmx to work, although my attempts are a bit trickier...

i am trying to bypass all the problems with single xserver, multihead, compiz rendering.  i have a quad-core comp, with two nvidia quadro 570 cards, each with two DVIs; four DVI ports total.

i want to get the whole thing working with compiz.  I had it going in hardy by binding the screens on each gpu using nvidia's twinview.  then i used XGL server to provide the underlying xinerama binding and fuse it into a single contiguous desktop with full compiz WITHOUT disabling GLX support. sweeeeet.

however XGL has been removed from intrepid and probably rightfully so...  but xdmx i think can be made to do the same; i just need to figure a couple things out.  i have read the entire man pages at x.org.


1) i am running two xservers on a single box, each with their own xorg.conf that binds them to their respective screens and GPUs. that works fine

2) i have an (/etc/X0.hosts) and an (/etc/X1.hosts).  each contain localhost and 127.0.0.1, probably redundant, which automatically enables connectivity to the servers via loopback if it wasnt already enabled. this works -->

3) TCP connectivity is enabled on both -->

4) i can verify with (netstat --inet -lnp -t | grep X) that there are two xservers running (however one is of course on port 6001 vs. 6000)

5) i have tried enabling AllowNonLocalModInDev which i thought would allow outside hosts (Xdmx) to change the keyboard layout.

6) i set both real servers up with CoreKeyboard and CorePointer on VOID devices, and tried specifying the device (/dev/input/mice)


when i run Xdmx (no gdm running, only 2 barebone xservers), the screen flashes and changes to a new VT (i think?) with BOTH xservers SIDE-BY-SIDE!!  it seems like im very close.  however xdmx complains because it cannot acquire the local keyboard and mouse, as one of the other servers has consumed them.  xdmx segfaults with one of the servers controlling the mouse that should have been void...  and looking at the Xorg.0.log etc. files proves that the xserver is loading the devices and unwanted extentions/modules anyway...


1) I know Xdmx is a proxy xserver similar to XGL, but doesnt it just take over the running xscreens?  or does it need a screen of its own?  what config file does it use? the localmachine's xorg.conf?  could i bind it to the "dummy" display driver to make it not need anything?  any help appreciated
2) how can i force the xserver to not hot load the local mice/keyboard and force disable certain extentions?  that seems to be a big part of the issue too.
3) do i need to somehow specify that the second server is running on port 6001?
4) anyway i could do this with the unix domain sockets instead of the loopback interface?


any help is greatly appreciated.  xdmx looks really cool; has anyone had success setting it up completely on a local box like this?  if i get this working i can add screens like mad...  i work at a internet/technology company, among my team we have 19 available flat panels and about 3 big screen LCD tv's...  haha i really want to get this going!  if i get her up and running i plan on making a little howto.

Thanks!

---

