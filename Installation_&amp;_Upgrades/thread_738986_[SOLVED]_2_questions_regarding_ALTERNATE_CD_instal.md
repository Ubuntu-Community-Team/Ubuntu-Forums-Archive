---
title: "[SOLVED] 2 questions regarding ALTERNATE CD installation"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-03-29
This morning I took the add-on video card out of my computer and hooked my monitor to the built-in/motherboard video instead.  I made the proper changes in BIOS for this change.

Now I notice 2 things.

1) When I boot to the Ubuntu ALTERNATE installation CD, I get a different Ubuntu installation menu screen than that which I formerly got.  In all my time of using Ubuntu, I had never seen this version of the boot menu before.  

This new menu screen is more of a text based menu with written scripts and a prompt line which will start the installation if you hit the enter key & F1 key which takes you to various other F key functions.  Before I changed video cards sources, the menu was a menu listing with 7 line items on the menu and then a listing of F key functions across the bottom, i.e. more of a graphics type listing.

Is the menu screen that is displayed dependent upon the type of video card that is being used ?  Apparently it is.

2) Also, since I changed to the built-in/motherboard video, now I am NOT getting the Ubuntu logo or loading progress scroll bar during the boot process.  I just get a blank screen and then go directly to the user name and password logon prompts.  After those I get to the desktop just fine.

How do I get the Ubuntu logo and loading progress scroll bar to display during boot when I am using the built-in motherboard graphics ?

Thanks.

---

### Post by banewman on 2008-03-29
The problem with the lack of a progress bar might be due to the video card driver you're using - did you install the one for your onboard card or are you using the vesa driver ?
You might get some joy from changing the resolution in the file /etc/usplash.conf to something less.
:)

---

### Post by wpshooter on 2008-03-29
> **banewman said:**
> The problem with the lack of a progress bar might be due to the video card driver you're using - did you install the one for your onboard card or are you using the vesa driver ?
You might get some joy from changing the resolution in the file /etc/usplash.conf to something less.
:)

I have edited it all the way down to 800 x 600 and still not seeing any change.

Is there something else I need to be doing ?

Thanks.

---

### Post by confused57 on 2008-03-29
> **wpshooter said:**
> I have edited it all the way down to 800 x 600 and still not seeing any change.

Is there something else I need to be doing ?

Thanks.
After you edit usplash.conf, you may need to:
```
sudo update-initramfs -u -k `uname -r`
```

---

### Post by wpshooter on 2008-03-29
> **confused57 said:**
> After you edit usplash.conf, you may need to:
```
sudo update-initramfs -u -k `uname -r`
```

Are you sure that the syntax of this command is correct ?

I get an error regarding uname.

Is uname abbreviation for** user name** ?  Or is that a constant ?

I am having to type this command since I am going from one machine to another.

Thanks.

---

### Post by confused57 on 2008-03-29
> **wpshooter said:**
> Are you sure that the syntax of this command is correct ?

I get an error regarding uname.

Is uname abbreviation for** user name** ?  Or is that a constant ?

I am having to type this command since I am going from one machine to another.

Thanks.
I had problems with Gutsy usplash out of range when I went from a 19" CRT to a 19" LCD...found the solution in this launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/154781](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/154781)
I basically just copied & pasted the command from the instructions in the bug report...I assume uname refers to the latest kernel being used?

---

### Post by wpshooter on 2008-03-29
> **confused57 said:**
> I had problems with Gutsy usplash out of range when I went from a 19" CRT to a 19" LCD...found the solution in this launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/154781](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/154781)
I basically just copied & pasted the command from the instructions in the bug report...I assume uname refers to the latest kernel being used?

Well, I got forum setup on this computer, so now that I can use copy and paste.  Thank the lord for copy and paste.  However, I know I typed that command exactly as given. 

However, even though I got the command to run, NO dice.  Still no logo or progress bar during boot !!!  What to do.  I am getting tired of fooling with this.  I have some gun magazines that I need to finish cleaning up.  I think I am going to go work on them until someone can come up with a solution to this.

Thanks.

---

### Post by confused57 on 2008-03-29
> **wpshooter said:**
> Well, I got forum setup on this computer, so now that I can use copy and paste.  Thank the lord for copy and paste.  However, I know I typed that command exactly as given. 

However, even though I got the command to run, NO dice.  Still no logo or progress bar during boot !!!  What to do.  I am getting tired of fooling with this.  I have some gun magazines that I need to finish cleaning up.  I think I am going to go work on them until someone can come up with a solution to this.

Thanks.
Initially, I just removed quiet & splash from the kernel options, at least I was able to see the boot process in text mode, until I found the fix, which thankfully worked for my system.

Added:  I don't know if it may be a framebuffer issue, maybe you could add a boot option vga=?:
[http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html#ss5.3](http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html#ss5.3)

---

### Post by wpshooter on 2008-03-30
O.K., I finally came up with the solution to this problem.

So for anyone in the future that might be trying to use & configure an IBM Netvista Model 8303-52U desktop computer, then here is what my problem was.  I discovered this quite by accident.

If you are using the on-motherboard/integraged-video on this IBM system, then in order to get the Ubuntu slash screen to display properly at bootup and shutdown, then you must set the **SHARED VIDEO MEMORY** parameter in the BIOS to 8192K and NOT 512K.  Apparently setting it at 512K does not give enough video memory for the requirements of displaying the graphics in the Ubuntu logo, etc.

Thanks.

---

