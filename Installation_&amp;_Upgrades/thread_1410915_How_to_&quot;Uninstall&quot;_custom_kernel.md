---
title: "How to &quot;Uninstall&quot; custom kernel?"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by markus_orreilly on 2010-02-19
I was recently trying to get VMWare Server 1.0 working on Ubuntu 9.10 (kernel 2.6.31-19) by following the directions here: [http://www.howtoforge.com/how-to-ins...u-9.10-desktop](http://www.howtoforge.com/how-to-ins...u-9.10-desktop) The directions didn't work for me, and now I run into errors now and then when installing new packages. I'm trying to revert back to the original generic kernel, but with no luck. I'm decent with common functions in linux, but this is beyond my experience. Any tips?

---

### Post by darkod on 2010-02-19
I'm not sure about custom kernels but it should be the same as removing old generic kernels. Open Synaptic Package Manager and search for linux-image

It will give you all kernels that are there (I hope the custom ones have the same name structure).

Be careful NOT to delete all kernels. :) Or if the custom one is your only one, you can't remove it because there will be nothing to boot. In fact, you can but it's more complicated then.

Otherwise, from the Synaptic list of linux-image-xxxxx just mark the one you want to remove for complete removal, click on the green button and that's it.

You'll probably need to run
sudo update-grub

for grub2 after that so it creates updated grub boot menu.

---

