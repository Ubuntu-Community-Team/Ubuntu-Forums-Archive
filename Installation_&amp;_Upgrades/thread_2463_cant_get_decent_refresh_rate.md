---
title: "cant get decent refresh rate"
date: 2004-10-28
forum: Installation &amp; Upgrades
---

### Post by realnoob on 2004-10-28
I have downloaded and installed ubuntu, but i dont think that the install has correctly configured my monitor as it only gives me a max refresh rate of 60hz which is unusable. It will not let me change it to anything else. Is there a way to change it or am i stuck with it at 60?

---

### Post by im_ka on 2004-10-28
you can run
```
sudo dpkg-reconfigure xserver-xfree86
```
to go through the whole configuration of the x server (x is the graphical server). this is handy if you have more things to set up (eg. your video card).

or edit XF86Config-4 manually by
```
sudo gedit /etc/X11/XF86Config-4
```

be careful with the refresh rates. if you set it too high (higher than your monitors capabilites), it might damages the screen.

hope this helps

---

### Post by HungSquirrel on 2004-10-28
If you have a Radeon video card, change the value of Driver in the Device section of /etc/X11/XF86Config-4 to "radeon".

---

### Post by dasfiend on 2004-10-28
before you edit the XF86Config-4, go to your manufacturer's website for your monitor and find the vertial and horizontal refresh rates your montor supports.  Then edit your /etc/X11/XF86Config-4 file as im_ka mentioned.  Look for the Section "Monitor"
tag and change the HorizSync and VertRefresh values to whatever your monitor supports. (30-85 and 50-160  respectively for my samsung 955DF for example)  Then you should by default have the highest refresh you can support at whatever res you chose during setup.

---

### Post by daniels on 2004-10-28
Even better, edit /etc/X11/XF86Config-4, go into the 'Monitor' section, and remove the HorizSync and VertRefresh lines altogether.

---

### Post by HungSquirrel on 2004-10-28
X can run without being told the refresh rates?  :o

---

### Post by realnoob on 2004-10-29
Thanks for the replies guys. I am a little bit apprehensive to start editing config files. Is it easy? Like my name says i am a real noob so anything that is gonna involve possibly messing up my system is causing me to have the willies. Is the file edited by hand or does it open in a text editor? thanks.

---

