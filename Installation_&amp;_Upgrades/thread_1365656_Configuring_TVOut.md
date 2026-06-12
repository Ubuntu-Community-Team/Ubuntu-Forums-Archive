---
title: "Configuring TVOut"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by ngtybear on 2009-12-27
I would be very thankful for some help. I have tried everything I can think of. Should ahve posted asking for help a week ago. 

Running Mythbuntu 9.10 on an AMD 64 fully patched. 

Video Card is PNY 7900 GS PCe with 256 MB. 

I upgraded the Nvidia driver to the latest (190.53). 

I am attempting to drive the video through the COMPONENT video out. Using the Nvidia Xserver app, it does not allow for any resolution over 1024x768, and the screen is entirely blue. 

When I edit the xorg.conf manually and force it to component and HD720p or HD1080i, they system locks completely and has to be reset.

Using the VGA output, everything looks and works great. Under XP, everything is working fine also. I can drive 1080i with no issue out of the COMPONENT video out. 

I have no idea what to try next. Please help if you do. I have searched for a week for a solution, and have found none. 

Thanks to those who reply.

---

### Post by papalaz on 2010-02-09
Do you mean "component" video out or "composite" video out? As far as I know xorg.conf only allows the options "SVIDEO" and "COMPOSITE". Here are the relevant sections from mine:

    Option         "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
    Option         "TVStandard" "PAL-I"

Of course, I could be wrong...

---

