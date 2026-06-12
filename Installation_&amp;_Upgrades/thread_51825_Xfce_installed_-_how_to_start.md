---
title: "Xfce installed - how to start?"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-25
Hi experts :)

I have just installed xfce with this command :
# apt-get install xfce4

After fetching and installing everything, I was back in my console. I got no errors, so I kind a thougt that I could just do 'startxfce4' - but no. I get this error :

/usr/bin/startxfce4: Starting X server
/usr/bin/startxfce4: line 45: xinit: not found

Could someone please help me solve my problem? Thanks :)

---

### Post by Ramon on 2005-07-25
I think you have to reboot??

---

### Post by jemt on 2005-07-25
Already tried that - didn't help at all

---

### Post by jemt on 2005-07-25
Any suggestions ?

---

### Post by majikstreet on 2005-07-25
hmmmm........... maybe x didn't get installed right?

---

### Post by jemt on 2005-07-25
Not sure. How do I check that ?

---

### Post by majikstreet on 2005-07-25
Not sure either. 

Maybe you can do this: apt-get install --reinstall xorg

Hope that will work :P

---

### Post by rmjokers on 2005-07-25
Have you tried starting xfce from the graphical login?  After you install it, it is added as an option for GDM.  I dont know how to start it from the command line.  You man need to do something with:

/etc/xdg/xfce4/xinitrc

(either run it or put it in your home directory as .xinitrc), but I have not tested this.

good luck

---

### Post by jemt on 2005-07-25
No X - did a server installation :)

---

### Post by majikstreet on 2005-07-25
[QUOTE=jemt]No X - did a server installation :)[/QUOTE]
 you need X for xfce to run.

---

### Post by craigevil on 2005-07-25
On the login screen look under Sessions. Click XFCE. Then login as usual.

You might want to use Synaptic and install the other pckages that go with XFCE.

---

### Post by mctavish on 2005-07-25
I also did a server install then installed xfce4, and had the same problem. Installing xfce4 doesn't drag in xorg dependencies, so you need to make sure you get the right x packages.

From memory I think there were a couple of key metapackages... perhaps xserver-common and xserver-xorg??

---

### Post by jemt on 2005-07-25
Well, yes ofcause.
But I'd bet xfce depends on X - so it should have been installed with xfce.

---

### Post by jemt on 2005-07-25
mctavish > Oh, overlooked your post. Thanks - i'll try that :)

---

