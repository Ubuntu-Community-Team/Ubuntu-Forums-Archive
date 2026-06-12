---
title: "[SOLVED] Gutsy + Compiz Fusion + ATi1950 + 3D"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by garyj1972 on 2007-11-19
Hi there

I'm only 2 weeks into Linux so sorry if my questions seem daft. I have searched the forums to try to answer this problem, but haven't seen solutions specific to my needs.

I have Ubuntu working with Compiz Fusion and thinks it's great - I want to stick with this and not resort to running back to Microsoft.

Here's my problem:

I'm running Ubuntu 32-bit installation (Gutsy) with a dual core AMD CPU and an ATi x1950 graphics card. When I install Ubuntu it updates and makes an ATi restricted driver available.

I have had Compiz Fusion working perfectly with this Ubuntu provided restricted driver and also with drivers installed with the help of ENVY.

I have had 3D games such as Alien Arena, Nexuiz, etc working great with both of these driver options too but never with Compiz Fusion installed, only on clean installs.

As soon as I install Compiz Fusion the 3D games go wrong. By wrong I mean the texture maps go haywire and where there should be text there is junk.

I have tried installing Compiz Fusion first, the games first, the restricted driver, the ENVY driver in just about every order on fresh Gutsy installs. This has taken ages as you can imagine.

Does anyone have any idea of the cause of this and a possible solution?

I am typing this from the browser from the LiveCD so I haven't posted any files. If you need files, tell me which order you want me to install everything in and I'll do that and post the necessary files up. As a newbie please provide the exact text you need typing into the terminal to access these files.

Many thanks in advance

Gary

---

### Post by garyj1972 on 2007-11-19
I thought I'd advise anyone facing a similar problem what I did to resolve this. It's not a perfect solution but it does allow me to do what I want.

On a fresh Gutsy i386 install with "GARY" as Admin user defined during install
Installed all hardware (wifi) in my case
Installed all Ubuntu updates
Installed ENVY  and ran it to update ATI driver
Installed Compiz Fusion Settings Manager from this link >   
       [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
BUT DIDN'T ENABLE ANYTHING - JUST INSTALLED IT AT THIS STAGE

Now created a second Admin authorised user, for me called GAMER

Now in the original Admin account "GARY" for me I enabled the 3D cube, wobbly windows, etc... that I wanted.

These settings did not transfer to the "GAMER" account, so as long as I never enable Custom Effects on this account all my 3D games still run perfectly.

I appreciate this doesn't cure the proble but for me is a satisfactory work-around - hope it helps someone else. Gary

---

