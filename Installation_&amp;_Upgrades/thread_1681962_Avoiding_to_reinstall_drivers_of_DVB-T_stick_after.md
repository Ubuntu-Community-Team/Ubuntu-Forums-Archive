---
title: "Avoiding to reinstall drivers of DVB-T stick after kernel minor update"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by stefboombastic on 2011-02-05
Hi all!
 I've got a Terrestrial DVB-T receiver USB stick (Terratec Cinergy TStick RC) and ubuntu( I have 10.10, but also the previous versions behaved the same) does not install it automatically.
For installing it I have to patch v4l-dvb manually following this: [http://ohioloco.ubuntuforums.org/showthread.php?t=1444535&page=2]("http://ohioloco.ubuntuforums.org/showthread.php?t=1444535&page=2")
Not a big problem, it just takes long!
What really drives me mad is that everytime Ubuntu updates itself, advancing the kernel of a minor release (i.e. 2.6.35.24.28 ->
2.6.35.25.32), my card stop working, and I have to do that procedure again!!
 Is there a way for avoiding that? Other programs/drivers do not behave like that! 
Even in Windows I've never had to reinstall drivers after installing any update!
 Thank You in advance!
Stefano B.

---

### Post by jjrp78 on 2011-02-06
no way around..if you update the kernel you need to compile the drivers again. I heard ubuntu 11.04 will support some cards nativelly..so cross your fingers

In the meanwhile you can avoid updating your kernel by:

   1. Open the synaptic package manager
   2. Search for &#8216;linux-image-generic&#8217;
   3. Select the package starting with &#8216;linux-image-generic&#8217;
   4. Click &#8216;Package > Lock Version&#8217;
   5. Search for &#8216;linux-headers-generic&#8217;
   6. Select the package starting with &#8216;linux-headers-generic&#8217;
   7. Click &#8216;Package > Lock Version

---

### Post by stefboombastic on 2011-02-12
Thank you very much!
It really sounds awful .. such minor releases are pretty frequent!! 
I think they are necessary updates.. I am worried about preventing them :(
And I can't understand why Linux didn't find a solution.. I never had such problems with windows..
Best regards,
Stefano

---

### Post by Zennon on 2011-04-15
It is my understanding that the DVB modules have to be re-compiled and re-installed after every kernel upgrade. I do this for my system by running:

```

stop mythtv-backend; modprobe --remove dvb_usb_af9015 dvb_core dvb_usb
cd v4l-dvb; make rminstall  

``````
apt-get dist-upgrade
``````
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make -j3 --silent
make install
```However, after upgrading from 2.6.35-28-generic #49 to 2.6.35-28-generic #50 today, the required DVB modules for my TV card were just there - and just worked:

/lib/modules/2.6.35-28-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-af9005-remote.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-af9005.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-af9015.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/media/dvb/frontends/af9013.ko

I'm puzzled.. can somebody educate me a bit here? Perhaps a re-compile is needed only when upgrading from e.g. 2.6.35.27 to 2.6.35.28? Either way, it would be nice if kernel upgrades would automatically install the required DVB modules. :)

EDIT: I've worked out that the 'make rminstall' command may have failed to remove the modules this time around - that explains why the DVB modules were still there (and loaded) after the kernel upgrade. My last question still stands, though: when is a re-compile/re-install of the DVB modules required?

---

