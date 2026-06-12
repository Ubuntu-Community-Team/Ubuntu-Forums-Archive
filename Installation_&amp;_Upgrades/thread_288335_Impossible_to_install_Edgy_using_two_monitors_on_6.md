---
title: "Impossible to install Edgy using two monitors on 6600gt?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Buffi on 2006-10-29
I used a two monitor-setup for dapper and it worked perfect.
The setup is two monitors, one connected with vga and one with dvi from a nvidia 6600gt.

Now I decided to do a fresh install with Edgy since I heard it had upgrade issues and ehm... This install had major. Everytime X would start, this would happend.
[[img]http://pici.se/thumbs/IqYa2c.jpg[/img]](http://pici.se/?6176)

One monitor wouldnt even get a signal and the other one was getting a bunch of weird lines. Ctrl+alt+f1 confirmed that linux was running but X was ******.
[[img]http://pici.se/thumbs/3AFEXP.jpg[/img]](http://pici.se/?6175)

Notice that both monitors has signals here... something is seriously ****** up with Edgys installer... oh well, I tried this three times and gave up. Plugged out my DVI-screen and there you have it. X started fine.
[[img]http://pici.se/thumbs/GuI4IM.jpg[/img]](http://pici.se/?6173)

Lets hope that I can configure my second screen for dual head by xinevision like in Dapper...
Seems like Edgy REALLY could use some more testing before going final...


Ok.. I got it installed using a single monitor, plugged in my second one and rebooted. Same screen. X wont work.

Im switching distribution tomorrow

---

### Post by iamdavid on 2006-11-02
anyone figure this out?

---

### Post by rsambuca on 2006-11-02
I did a fresh install of Edgy recently.  I have a 6600GT and have two monitors working fine with twinview.  I have never tried xinevision.

When I did the Edgy install, only one monitor worked until i did the quick twinview setup, and all has worked fine since.  As twinview is working well for me and suits my needs, I haven't bothered to try xinevision as the setup looked a little more involved.  With twinview, I just needed to add four lines to the xorg.conf file.

---

### Post by snailian on 2007-03-29
I had the same problem.  I have a 6800GT with two monitors.  When you have the install CD in, and it pops up with the install menu, you'll see at the bottom of the screen it reads "VGA". I think bound to F4. You'll want to change that to a resolution other than VGA. It should work like a charm after that!

EDIT: sorry for raising the dead, I just noticed when this was posted.

---

### Post by llavalle on 2007-03-29
Got that problem with a dual-monitor setup on my 7900GT.

I'll try the F4 option.

---

