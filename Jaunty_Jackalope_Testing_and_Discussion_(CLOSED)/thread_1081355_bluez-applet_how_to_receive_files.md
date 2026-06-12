---
title: "bluez-applet: how to receive files"
date: 2009-02-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-02-26
Hello, I want to receive files using bluetooth.
There is a gconf key in /apps/bluetooth-manager I enabled it, but it does not work!
Have you got any solution? thanks

---

### Post by scaine on 2009-02-26
I think you need the obex stuff to do this.  I use Blueman myself, so I'm not sure which one you need.  "obex-data-server", maybe?  Possilby "gnome-vfs-obexftp".

I think once you've installed them, there's an etc file you can edit which tells the server where to place files when they're received.  It's been a while though - sorry I can't be more specific.

---

### Post by smbm on 2009-02-26
I installed blueman, it seems to work a lot better.

[https://launchpad.net/blueman](https://launchpad.net/blueman)

---

### Post by yelo3 on 2009-02-26
It must work also with bluez-gnome and without root access!

---

### Post by smbm on 2009-02-26
I tried to get it to work for a whole evening and failed.

Good luck though.

If you do manage to make it work let me know how you did it.

---

### Post by scaine on 2009-02-26
Well, Blueman replaces bluez-gnome, but doesn't need root access for sure.  If you want to set this up with bluez-gnome, then follow my original sketchy instructions to install the obex support, then you should be good to go (well, after you've paired your device of course...)

EDIT : @smbm, this is really simple with Blueman.  Perhaps you can elaborate what type of phone/device you're sending files from and how you tried it?  In Blueman, you just enabled the "Transfer" service, chose a folder from the drop-down, tick the boxes for permissions and you're off.

[ATTACH]104736[/ATTACH]

---

### Post by smbm on 2009-02-26
> **scaine said:**
> Well, Blueman replaces bluez-gnome, but doesn't need root access for sure.  If you want to set this up with bluez-gnome, then follow my original sketchy instructions to install the obex support, then you should be good to go (well, after you've paired your device of course...)

EDIT : @smbm, this is really simple with Blueman.  Perhaps you can elaborate what type of phone/device you're sending files from and how you tried it?  In Blueman, you just enabled the "Transfer" service, chose a folder from the drop-down, tick the boxes for permissions and you're off.

[ATTACH]104736[/ATTACH]

Sorry, I meant I tried to get bluez working for a whole evening. Blueman worked straight away. IMHO it should replace bluez.

---

### Post by ViRMiN on 2009-02-26
Nice tool, thanks for the info! ;)

---

### Post by yelo3 on 2009-02-26
bluez-gnome always worked... it must be a bug for sure.
I don't like blueman, it's way too complicated, I prefer silmpler apps

---

### Post by scaine on 2009-02-26
You posted this thread, Yelo3, cos you couldn't get it working (at all) and now two people have described how stupidly easy it is to get working with Blueman, but you claim that Blueman is too complicated?

Sorry, I just can't help you.  Maybe someone willing to hack the Bluez stuff can't post here to help out.  Bluez is *too* oversimplified IMO, and this is proof.

The way that Blueman also ties into the Gnome environment is really slick too, seamlessly hooking into Network Manager - it's a joy to use.

Good luck with Bluez though.

---

### Post by yelo3 on 2009-02-26
I'm sorry if we have different opinions

---

### Post by scaine on 2009-02-26
Hey, not at all.  I *do* love the Blueman project though, so sorry too if I came over a bit strong.  I'm not a big fan of the way that sometimes gnome dumbs things down, although I do appreciate that it strongly follows the one-tool-for-one-job principle.

Anyway, did you try the Obex support I mentioned above?  I have a PC upstairs and a spare bluetooth dongle, so I might be able to give it a go over the weekend if you're still struggling.  What's your timescale for a fix?

---

### Post by smbm on 2009-02-26
> **scaine said:**
> You posted this thread, Yelo3, cos you couldn't get it working (at all) and now two people have described how stupidly easy it is to get working with Blueman, but you claim that Blueman is too complicated?

Sorry, I just can't help you.  Maybe someone willing to hack the Bluez stuff can't post here to help out.  Bluez is *too* oversimplified IMO, and this is proof.

The way that Blueman also ties into the Gnome environment is really slick too, seamlessly hooking into Network Manager - it's a joy to use.

Good luck with Bluez though.

I agree about the network manager functionality, I didn't even know my phone would operate as a modem as it's not documented that it would anywhere. Blueman found that it could instantly which has saved me considerable outlay on a 3g dongle.

---

### Post by yelo3 on 2009-02-26
I have obex-data-server installed, so it should just work, as it used to do in the past. I filed a bug report, I'm not in a hurry at all!

I tested blueman, it works, but I prefer to not install new apps since I don't need bluetooth dial up.

---

### Post by scaine on 2009-02-26
Fair enough.  On the one hand, I support your decision to stay with the default apps and make them better by publishing bug reports.

On the other hand, I've found bluez-gnome to be so utterly featureless that I quite simply cannot support its existence when far, far better alternatives exist.

Let me ask an honest question.  If Blueman were the default in Ubuntu, would you go out of your way to un-install it, then install bluez-gnome instead?  And if so, can I ask why?

BTW, this thread makes me look like a complete Blueman fanatic and I'm fully aware that I've advocated its use in other threads too!  I have nothing to do with the project, but really, really appreciate good software!

---

