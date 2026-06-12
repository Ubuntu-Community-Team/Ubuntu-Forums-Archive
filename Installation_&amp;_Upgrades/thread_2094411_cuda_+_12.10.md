---
title: "cuda + 12.10?"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by DuckZoro on 2012-12-13
Hi, I've spent most of today unsuccessfully attempting to install the proprietary driver for my shiny Geforce GT 640 M gpu, so I can get to play around with this new-fangled cuda-business. 
 (I should mention I'm using ubuntu 12.10 64-bit).

Does anyone know if it is supposed to work? I simply downloaded the self-installing package from nvidia, went ctrl+alt+f1, stopped lightdm, ran the installer (it gave an error-message about distribution install script failing, but otherwise made no problems), and watched my computer partly melt.... (oh yeah, and I did tell it to blacklist nouveau, as the internet prescribes)
 Or, more precisely, I was suddenly unable to get any other resolution than something like 600x400, and unity and compiz were gone. I ended up using the "--uninstall" option for the installer, and reinstalling all compiz packages I could find in synaptic (and all unity-related as well, though that didn't seem to have any effect). So now I'm back at square one.

I'd be willing to venture out there again, seeing as I actually did manage to make my way back (wooh!), but I thought I should ask whether anyone has actually had any luck doing this? simply googling cuda + ubuntu 12.10 it seems that there's some problem that means people are sticking to 12.04?

EDIT:
Going here: [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)
it seems that, for the moment, CUDA is still only supposed to work on 11.10. So, I guess it might be a good idea to wait a while...

---

