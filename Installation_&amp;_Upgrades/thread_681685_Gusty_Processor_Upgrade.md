---
title: "Gusty Processor Upgrade"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by budlatte on 2008-01-29
I currently have an AMD athlon 64 3500+ processor on an asus a8v deluxe mobo.with 1 gb ram and am running 32-bit Gusty on an IDE HD, with a SATA HD as a storage. Since the upgrade from edgy, and the install of the storage drive  the CPU load as been near 100% even for things like scrolling in firefox, and if i have any windows open, compiz-fusion is very slow, especially the window effects and things like that (they are always lagging).  I want to upgrade to a dual-core processor, and found the X2 3600 for a good price that will work for my mobo. (socket 939).  I would like to get the 3800 or even the 4000, but i cant find them for sale for the socket 939, despite the fact that AMD supposedly makes them.

I am wondering if Gusty will have any problems working when upgraded from a single core to a dual core.  I have heard processor swaps are usually trivial, but have found nothing which deals with upgrades to multi-core processors.  I have built several computers in the past but all were "from scratch" so i never had to worry about losing Hard Drive info.  Will the X2 3600+ dual-core replace the 3500+ single-core without any fuss beyond a BIOS upgrade?  I would really like to avoid having to get a new mobo and ram as it is obviously more expensive.

---

### Post by tisse on 2008-01-29
I recently did an upgrade from AMD 64 3000+ to an Intel Dual Core E2160 without any problem at all. I only changed all the components (motherboard, cpu, and graphics-card) and restarted the computer. Gutsy worked as a charm and in the performance monitor I saw two processors. So it should be any problem for you.


But I don't think your computer is too slow though, it should handle Gutsy without any problem at all. Have you tried to find if there is any special process that causes your 100% CPU? For instance using the command 'top'.

---

### Post by budlatte on 2008-01-29
The system monitor shows some processes but most are named either gnome or compiz-fusion.  I am not at that computer right now, but will check 'top ' out as soon as i get back.

---

### Post by tisse on 2008-01-29
You probably have some problem with compiz-fusion as I see it. I don't think upgrading your computer will help... I used to run a AMD 64 3000+ with compiz-fusion and it rarely used any CPU at all. The only reason I upgraded my computer is that I wanted to play some new games.

So I suggest that you try to find the cause why compiz-fusion doesn't work instead of spending your money on a new CPU. What I would do is to backup all important data then reinstall gutsy.

---

### Post by budlatte on 2008-01-29
sorry for the split reply, however, i don't think that other processes are to blame, because if i have no windows open and just an empty desktop, the CPU usage goes down to around 3% or less, even with pidgin and skype running in the background.  If i rotate the comp-fusion cube it works great with no lagging at all (unless i keep rotating it for extended periods of time) but as soon as i open a window say firefox with their default start-page, and i rotate the cube it lags severely on the pane with that window.  I will still try top when i get back.  
thanks for the tip

---

### Post by budlatte on 2008-01-29
the thing is i am running basic functions with compiz-fusion, i have 6 panes, reflection, and caps are the most cpu intensive things in have running, all panes have the same wallpaper.  compiz-fusion runs fine until a window is open on any one pane.

This is my top readout when opening a window
5603 abe       15   0  245m  95m  17m S 44.9  9.4 347:43.13 Xgl                
18268 abe       15   0  126m  36m  19m S  3.0  3.7   0:02.01 firefox-bin        
 5293 root      15   0 39892  12m 7580 S  0.7  1.2   0:28.18 Xorg               
 5625 abe       15   0 93132  22m  15m S  0.7  2.2   0:16.19 gnome-panel        
 5626 abe       15   0  111m  17m  13m S  0.7  1.7   0:02.25 nautilus           
 5643 abe       15   0 66028  11m 7616 S  0.7  1.1   0:08.28 gtk-window-deco    
 4944 root      18   0  2728  980  796 S  0.3  0.1   0:23.94 hald-addon-usb-    
18250 abe       15   0  2364 1156  876 R  0.3  0.1   0:00.07 top                
    1 root      15   0  2948 1852  532 S  0.0  0.2   0:01.01 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:15.49 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid      

and this is just static (with obviously lower cpu usage)

5603 abe       15   0  254m 104m  17m S  1.7 10.4 348:29.65 Xgl                
18298 abe       15   0  135m  45m  19m S  0.7  4.5   0:07.66 firefox-bin        
 5644 abe       15   0 22656  16m 7000 S  0.3  1.6   2:18.84 compiz.real        
    1 root      15   0  2948 1852  532 S  0.0  0.2   0:01.01 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:15.51 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  132 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  155 root      15   0     0    0    0 S  0.0  0.0   0:00.22 pdflush            
  156 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush            
  157 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 kswapd0 

if compiz fusion is the problem how should i configure it?  but wouldn't a faster processer run everything faster, even if compiz fusion is giving the current cpu trouble because of incorrect configuration?

Also,  i wouldn't be opposed to overclocking the 3500+ considering it is getting old anyway, but i dont know anything about overclocking, thats why i went with the amd instead of intel in the first place.  but if someone knows how to correctly overclock my setup i would consider it, if compiz fusion is not the problem

---

### Post by budlatte on 2008-01-29
also as a side note, i just set the visual effects to normal, and speed hasn't improved

---

### Post by tisse on 2008-01-30
I would say that you have problems with xgl (desktop-effekts). I had similar problems in Feisty and would recommend that you search the desktop-effekts forum for help. I think buying a newer CPU would be a waste of money in your case...

---

### Post by budlatte on 2008-01-30
I will do that, thanks a lot for you help.

---

