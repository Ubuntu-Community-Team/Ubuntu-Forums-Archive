---
title: "Games Micro-Stuttering"
date: 2018-10-15
forum: MINT
---

### Post by steocullen91 on 2018-10-15
Hi all. I have only used Linux a little bit here and there, but I'm trying to get used to it and thinking of using it as my main OS. Basically I'm trying to run WIndows games and I have this problem where every game seems to micro-stutter for me. I have an i7-7700k, 16GB 3000MHz DDR4 and a VEGA 64 GPU. 

I was messing around with Mint a while back with a HD6950 and managed to get it all working the way I wanted to, including somehow fixing the stutter. It was even lag free with the VEGA 64 when I got it, but then I had some small problems and reinstalled. Now the stuttering issue has returned. I even installed Ubuntu instead just to see if there was any difference but now it's still the same.

I'm using the Mesa 18.3.0 driver and it happens with all games I've tried where they seem to stutter or judder etc. Even a simple to run game like Rayman Origins keeps stuttering even though it's 2D. It requires gallium nine or else some sprites will be missing, but even without it the stuttering issue is present.

I'm using Lutris and Wine D3D9 Staging to run Rayman and I've tried GTA V with proton on Steam while still having the issue present. I also have a 144Hz 1080p monitor though I've disabled freesync and even tried using the TV while the issue would still persist. The reason I'm trying Rayman is because firstly I'm a huge fan of the series and also because if it can't run a 2D game stutter free, then it won't run a 3D one properly either. My idea was to try figure it out on that first.

Does anyone have any ideas what could cause this to be happening? I'm sorry if I left out any needed info.

---

### Post by Holger_Gehrke on 2018-10-15
Try a few (graphical) Linux games from the repositories. If those don't show the stuttering, then the problem is with Wine. If they do, the problem could be the graphics driver. There is a proprietary driver for newer AMD GPUs (named appropriately enough AMDGPU) which might help.

Holger

---

### Post by steocullen91 on 2018-10-15
Thanks for the reply. I've went ahead and reinstalled Mint again to have a fresh install then installed Portal and I was getting about 290fps while it ran nicely. I've updated all of the drivers and used Mesa 18.3.0-devel along with updating the kernel using ukuu. After doing so, I tested Portal again and it still runs fine. I then tried Tomb Raider which seems to be supported on Linux also and it also seemed to run fairly well. It had a little hitch here and there but overall it was running at a nice framerate too. 

I tried GTA V and that is still the same where it just plays badly with huge freezes and stutters. I know that's not optimised for Linux at all and uses Proton so it's a separate issue, I just seen others report that they have it running pretty well.  Overall though, games like Portal seem to run nicely and I guess it's all up to me setting up Proton properly to try optimise GTA V myself.

As for Rayman Origins on Lutris though, I literally have no idea what I did last time to make it work, but it was using Wine staging with gallium nine definitely when I had it working properly on the HD 6950. I'm using the GoG version also since I don't own it on steam but I guess I'll just play around a little more and see if I can figure out the issue. I just literally have no idea what I done to fix it last time.

---

### Post by wildmanne39 on 2018-10-15
*Thread moved to **MINT for a more appropriate fit**.*

---

