---
title: "ndiswrapper module"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by nkingcade on 2008-10-18
I have run the command:

sudo find /lib/modules/$(uname -r) -name "*ndiswrapper*"

What this returns is:

/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

my question is:

What is this indicating? That the kernel module is available? I have a wusb54g linksys card I am trying to use on this machine. It only has windows drivers. What would be my next step if the kernel module is available? thanks.

---

### Post by cariboo on 2008-10-18
It would seem that the modules are ready for insertion. You need to have your windows drivers handy. If you have your Livecd close at hand, install ndisgtk. It is in /pool/main/n. this will make it a lot easier  to install the drivers.

Other wise in a terminal type:

```
sudo ndiswrapper -i /path/to/windows/inf file
```

Then to make sure that you installed the correct windows driver, in the same terminal:

```
sudo ndiswrapper -l
```

this command should echo back that the device is present and what driver it is using. If it was successful, next insert the module, in the same terminal type:

```
sudo modprobe ndiswrapper
```

if nothing echoed back the you succeeded in installing the module. Now just restart networking and things should work. To restart networking in the terminal type:

```
sudo /etc/init.d/networking restart
```

If you don't get any errors you should be ready to go.

Jim

---

### Post by Ayuthia on 2008-10-18
> **nkingcade said:**
> I have run the command:

sudo find /lib/modules/$(uname -r) -name "*ndiswrapper*"

What this returns is:

/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

my question is:

What is this indicating? That the kernel module is available? I have a wusb54g linksys card I am trying to use on this machine. It only has windows drivers. What would be my next step if the kernel module is available? thanks.

It does mean that the module is available.  Ubuntu packages the kernel module for ndiswrapper, but you will still need to install the ndiswrapper application (ndiswrapper-utils-1.9 from the Ubuntu repositories or the live CD) to get it to work.

---

### Post by nkingcade on 2008-10-19
I have found the ndisgtk on the disk. However, it is a .deb file. How do I install the file? Thanks again.

---

### Post by Partyboi2 on 2008-10-19
> **nkingcade said:**
> I have found the ndisgtk on the disk. However, it is a .deb file. How do I install the file? Thanks again.
You can double click on it to install, or from a terminal change directory to where the deb is and install it using
```
sudo dpkg -i package
``` Change package to actual package name. You probably will also need to install ndiswrapper-common ndiswrapper-utils-1.9

---

### Post by amup on 2008-10-19
> install ndisgtk. It is in /pool/main/n.

Hello, I too am trying to install ndiswrapper.  I am in /pool/main/n and can not find ndisgtk.  Can it be somewhere else and how do I find it?

I have tried (from /media/cdrom0):

find -name ndisgtk
find -name "*ndisgtk*"

And nothing.

---

### Post by Bucky Ball on 2008-10-19
What wireless cards are you both using? You can find this by pasting:

**lspci**

in a terminal. Just curious as to whether you need ndiswrapper in the first place.

---

### Post by amup on 2008-10-19
Mine is a Belkin Wireless Pre-N Notebook Network Card Part# F5D8010 Version 1000

Btw, when I do "lspci" it says the Ethernet controller is Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 01)

---

### Post by nkingcade on 2008-10-19
I have installed ndwrapper. Still no joy with the wusb54g card. ndiswrapper -l gives me

rt2500usb : driver installed

               device (13B1:000D) present (alternate driver: rt2500usb)

Anyone give me any pointers on this problem? thanks

---

### Post by Bucky Ball on 2008-10-19
nkingcade:

[http://blog.eksfiles.net/2008/07/06/sucess-with-hardy-heron-and-linksys-wusb54g-wireless-adapter/](http://blog.eksfiles.net/2008/07/06/sucess-with-hardy-heron-and-linksys-wusb54g-wireless-adapter/)

[http://www.ubuntugeek.com/howto-setup-linksys-wusb54g-v4-wireless-in-ubuntu-gusty.html](http://www.ubuntugeek.com/howto-setup-linksys-wusb54g-v4-wireless-in-ubuntu-gusty.html)

[http://www.fam.tuwien.ac.at/~schamane/_/blog:080512_wusb54g_wpa_on_ubuntu_8.04](http://www.fam.tuwien.ac.at/~schamane/_/blog:080512_wusb54g_wpa_on_ubuntu_8.04)

You might want to dig in here also:

[http://au.altavista.com/web/results?itag=ody&q=wusb54g+ubuntu+hardy+&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=wusb54g+ubuntu+hardy+&kgs=0&kls=0)

From what I can see, ndiswrapper is not mentioned for you USB device in the three links I have posted. :)

---

### Post by nkingcade on 2008-10-19
Thanks to all who helped in this problem. I think I have it working now. Signal strength is low. However, the driver is loaded and it appears I'm usiing the proper version of rt2500usb. thanks again to all.

---

