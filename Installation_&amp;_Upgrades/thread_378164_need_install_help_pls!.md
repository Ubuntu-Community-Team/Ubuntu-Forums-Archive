---
title: "need install help pls!"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by compostbrain on 2007-03-06
I am trying to install 6.06 on an ibm netvista pentium4 and get the error "buffer I/O error on device hdc, logical block 0".  This error repeats over and over with numbers 0 through 7 at the end.  this is after booting and getting the splash screen.  Thx for any help--

---

### Post by Kateikyoushi on 2007-03-07
Found someone in similar situation on launchpad. [LINK]("https://answers.launchpad.net/ubuntu/+ticket/3451")

So try what they recommend.

> 1. Press F6 when the liveCD boot menu comes up to alter the boot options.
2. Add the following at the end (before the '--'):
pci=noacpi ide=nodma ide=reverse
3. Boot

---

### Post by compostbrain on 2007-03-07
awesome, it worked but now it says there is an error with the x11 so i only have a command line.  Any advice on how to fix this??

---

### Post by Kateikyoushi on 2007-03-07
What is your video card ?

---

### Post by compostbrain on 2007-03-07
not sure about that.  It is whatever came with the computer.  how would I determine this?

---

### Post by Kateikyoushi on 2007-03-07
This should let us know. Copy to the terminal and post the output.
```
lspci | grep VGA
```

---

### Post by compostbrain on 2007-03-07
intel corp 82845G/gl[Brookdale Gl/GE chipset Integrated Graphics Device.  Thank you for all your help

---

### Post by Kateikyoushi on 2007-03-07
That should work out of the box, could you type in the error message ?

---

### Post by compostbrain on 2007-03-07
it is very similar to this:
This error occurs:
"Failed to start the x server. It is likely it isn't configured correctly. Would you like to view the x server output to diagnose the problem?"
Yes
..."Module loader present"...
(==) Log file: "/var/log/xorg.o.log"...
(==) Using config file:"/etc/X11/Xorg.config"
I press Esc and it says:
"Would you like to view the detailed x server output as well?" Yes.
It is the same exactly.
I press Esc
It then says
"The x server is now disabled.Restart GDM when it is configured correctly"

---

### Post by Kateikyoushi on 2007-03-07
Could try to reconfigure x and set it to use the right driver which could make the live cd work, but I think it would be easier to ue the alternate cd to install it on your PC.

---

### Post by compostbrain on 2007-03-25
What do you mean "alternate cd" ? I am using an iso that I downloaded and burned on my mac.

---

