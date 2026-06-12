---
title: "Graphics card upgrade; driver install issues."
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by wmdvanzyl on 2012-06-08
I feel like the name of this thread echoes around the support forums very often. I have tried using Google, but i have reached a point of desperation. I urgently need this system back up, since there is outstanding work for a client that needs to be done! 

A little background:

My HD4870 started artifacting so it was replaced by a HD6870 - nice. :guitar: But the unexpected hardware upgrade left my Ubuntu Oneric system without any display - i just got a purple haze at the login screen. So i whipped out my Ubuntu livecd (which is still Meerkat), but i it got me back in. So here's what i've done:

[LIST]
[*]Ubuntu Meerkat livecd
[*]chrooted into the system with internet access using script given [here ]("http://ubuntuforums.org/showthread.php?t=1699633")
[*]Manually downloaded ATI drivers off of web
[*]Installed execstack using commands given [here]("http://www.breaknenter.org/2012/04/how-to-install-execstack-on-ubuntu-hardy/")
[*]Tried running the following command as found on [this]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") page
sudo sh ./amd-driver-installer-[12-4]("http://wiki.cchtml.com/index.php/12-4")-x86.x86_64.run --buildpkg Ubuntu/oneiric
[/LIST]

Now i am getting this error:

At the start of the installation , but i don't know if it is really an issue.

> (synaptic:8710): Gtk-WARNING **: cannot open display: :0.0
Unable to resolve  dh-modaliases.  Please manually install and try again.


And then at the end i get this: 
> # Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx > \
        debian/fglrx.modaliases
dh_modaliases
make: dh_modaliases: Command not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.ViMeWW
root@ubuntu:/home/willie/Downloads# 


As she said in 5th element... "Please, help."

---

### Post by dino99 on 2012-06-08
maybe you can purge: fglrx, jockey
then rename xorg.conf to *.old or else
and check that dkms and the kernel headers are installed
finally reinstall fglrx & jockey

then reboot

but with new graphic hardware its a good idea to install one of the latest stable kernel, so why not Precise, which has a 5 years support.

---

### Post by QIII on 2012-06-08
The route of installing from the ATI website is unnecessarily painful and the "Additional Drivers" method does not work for some users.

ATI and Canonical are in bed together.  Phoronix complains about it all the time.  There is no reason to do this from the ATI site.

Please see the link in my signature.

---

### Post by wmdvanzyl on 2012-06-10
Thanks for the responses. In the thread you created one has to reboot several times. How does this translate when using a livecd and chrooted environment? Do i ahve to reboot every time, because that would be time consuming and in some ways counter-productive.

---

### Post by wmdvanzyl on 2012-06-12
> **QIII said:**
> The route of installing from the ATI website is unnecessarily painful and the "Additional Drivers" method does not work for some users.

ATI and Canonical are in bed together.  Phoronix complains about it all the time.  There is no reason to do this from the ATI site.

Please see the link in my signature.

Your link was the perfect solution - thank you! With the exception of the restarts, as i was using chroot. GEtting internet access in chroot was also critical. Thanks!

---

