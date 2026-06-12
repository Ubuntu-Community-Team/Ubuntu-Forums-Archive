---
title: "[SOLVED] Problems with HAL synaptics script"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Valde_91 on 2008-10-31
Hi!

This morning I upgraded to Intrepid from Hardy on my HP Compaq nx7000. On hardy I used to have two finger scrolling and tapping with 2 or 3 fingers. With the upgrade I lost my configuration of the synaptics touchpad driver, because this configuration is now done with Hal and no more in xorg.conf.

So I googled a bit and finally write this script ```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
   <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
   <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
  </match>
 </device>
</deviceinfo>

``` 
and saved it in ```
/etc/hal/fdi/policy/ 
``` for two finger scrolling (horizontal and vertical) and tapping with 2 (right - click) and 3 (center button) fingers. 

I've log out and then re-logged in but my configuration still not working!

Can someone explain me why my script doesn't work? It's very strange that only tapping with 2 or 3 fingers is working, but not scrolling

thanks a lot 

Valde_91

---

### Post by Valde_91 on 2008-10-31
I restarted my computer and everythings works fine! Only Log off and Log in, as is specified at this page [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad), wasn't enough to apply the changes.

Bye Bye Valde_91

---

### Post by joel_gil on 2009-03-25
hello
i randombly ran into your post
i never had actually thought  of setting the maclike gestures on the tochpad

i do not have much experience with linux, could you tell me what is it exactly i need to do?

do i jsut add the script to preferences.fdi or create a new file? if i have to create a new file, what shall i call it?

thanks in advance

---

### Post by mikko.ohtamaa on 2009-10-10
> **joel_gil said:**
> 
i do not have much experience with linux, could you tell me what is it exactly i need to do?

[http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

---

