---
title: "Nvidia GeForce 8800GT Linux 64Bit"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by cocoalder on 2008-10-25
Hey guys ,

I've a problem if i open the terminal and enter
cd /home/user/Dekstop
sudo sh NVIDIA-Linux-x86_64-177.80-pkg2.run

I get 2 error messages :

[ [IMG]http://s7b.directupload.net/images/081025/temp/n9q3dlv2.png[/IMG]](http://s7b.directupload.net/file/d/1593/n9q3dlv2_png.htm)


and



[ [IMG]http://s6b.directupload.net/images/081025/temp/tebl88s6.png[/IMG]](http://s6b.directupload.net/file/d/1593/tebl88s6_png.htm)


I need help because i need the graphical driver

---

### Post by bulldog on 2008-10-25
You can use EnvyNG or take a look here,
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by cocoalder on 2008-10-25
Now i did it manualy ( [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) )
Everything worked and than i started gnome again ( sudo /etc/init.d/gdm start ) After this i got error that it will use low resolution . I tried to restart my computer again and i got the same error again . I press ok and login to my Desktop . Now my Resolution is 800x600 and Cunter Strike Source doenst start . Bevore i installed the Driver it started but it lagged to much . I really dont know what to do , because i try to install the Driver the whole day and it wont work =/ . 
Pls Help me , i really dont know what to do and i wont to install Windows again ! 


Best Regards ,

cocoalder

---

### Post by bulldog on 2008-10-25
I think the fault is in your xorg.conf.
But to go there you must know what you're doing.
I suggest using envyNG,it's safe and it will write the changes to your xorg.conf.
Do a search in your synaptic it should be there.
Let envy un-install the nvidia driver you installed,and choose to install the nvidia driver again.
This is the most painless way I can think of.
Try it and you'll see what I mean.

You can download and install envyNG from this link,if you can't find it in synaptic,
```
http://linux.softpedia.com/get/System/Software-Distribution/EnvyNG-36961.shtml
```

---

### Post by cocoalder on 2008-10-26
I tried it with envyNG and it still dont work ! Ist there someone who had the same probleme or someone who has a 8800GT and it works on linux .
Because i realllllly wont to install windows again -.-

---

### Post by AllenGG on 2008-10-26
RE: ENVY,  you may have better luck if you re-install ENVY by switching to "root" at boot-up.  First, install Envy from Synaptic, if you haven't already.
After re-boot  'esc' to  root, then after you have entered your password, type in "Envy -t"
then, un-install the NVidia driver, then install the 'current' NVidia driver, then re-boot, normally, again.

---

### Post by kspncr on 2008-10-26
I have the same video card as you on my desktop, but I didn't have to install any drivers (or do anything for that matter). It worked OOB.

EDIT: It worked OOB on Hardy, Intrepid (beta), and Debian Etch. All 64-bit. Haven't tried it on anything else.

---

