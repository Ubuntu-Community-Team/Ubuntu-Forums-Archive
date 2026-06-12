---
title: "ASPEED Graphics Card under Ubuntu Karmic"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by k3Rn on 2010-03-23
Hello!

I am running a SUNFIRE 2200 server with an ASPEED Graphics Card.

Up to now I was using Ubuntu Jaunty. In Jaunty as in Karmic I have
problems with the login-manager GDM. On bootup i get the error: "Ubuntu
is running in low-graphics mode". Under Jaunty i could work around it
using XDM as login-manager.

Now I upgraded my system to Karmic. For some reason XDM doesn't work
anymore - I get a shell on bootup. When I use "dpkg-reconfigure gdm" to
change the login-manager to GDM, i get the same old low-graphics error.
I tryed alot meanwhile, i reinstalled XDM aswell as GDM, tryed it again
to get XDM to work, but no.

So my question, can you perhaps help me to get Ubuntu Karmic working on
my system? I read about the possible VBIOS update - do I have to do
that? Do i need to install a driver, or edit configs? I'd be glad if I
could solve that issue as easy, as just using XDM again, don't know.
I also tryed to edit GdmXserverTimeout in gdm.conf, but with no success.
By the way, in the "low-graphics error dialog" it also says: "Failed to
load module "ast" (module does not exist)".

Config:
-------

  Sun SunFire X2200

  Ubuntu Karmic

  lspci | grep VGA:
  01:05.0 VGA compatible controller: ASPEED Technology, Inc.
          ASPEED Graphics Family


Any help appreciated!

---

### Post by k3Rn on 2010-03-24
I now got it working.

I replaced the ast driver, deleted the xorg.conf and did a 'dpkg-reconfigure xserver-xorg'.
Then i could boot into GDM withour errors!

---

### Post by laymer on 2010-06-03
hi k3Rn,
 
pleeeease give more detail on how you fixed this issue? where did you get the driver?
 
i have the same issue

---

### Post by k3Rn on 2010-06-03
> I replaced the ast driver, deleted the xorg.conf and did a 'dpkg-reconfigure xserver-xorg'.
Then i could boot into GDM withour errors!     I got the driver from the ASPEED support. I attached the driver file. Add the attached file(ast.ids) to /usr/share/xserver-xorg/pci .

Hope this helps... Greets

---

