---
title: "Changing boot splash screen back to Ubuntu"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by fushorts on 2006-12-22
i have had ubuntu 6.10 on my pc for a while now and i love it.  runs nice, no real problems (at least no problems that were hard to fix).  however i decided to give kde a try on it so i apt-get install the kde files.

no problem there 

however,  i would really really really like to know how to get my boot screen to say ubuntu again instead of using the kubuntu boot screen.

the loading screen looks nice and i guess it is not a huge problem but it is something that bugs me.

if there is a way to uninstall kde easily as i put in on there that would be great but i do not want to mess up the system seeing how i am what most would consider a linux newb.

to install all i did was "apt-get install kubuntu-desktop"

if there is any way to undo this please let me know

---

### Post by bulldog on 2006-12-22
Try ```
sudo aptitude remove kubuntu-desktop
```

Can't promise if the splash screen will be removed.
You can take a look at this link to restore gnome.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by aysiu on 2006-12-22
To change the splash screen, follow these directions:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by ovidescu on 2007-01-09
> **aysiu said:**
> To change the splash screen, follow these directions:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

Link is dead :confused: 
and I do have the same problem

---

### Post by ovidescu on 2007-01-13
> **fushorts said:**
> however,  i would really really really like to know how to get my boot screen to say ubuntu again instead of using the kubuntu boot screen.


This worked for me:
```

sudo aptitude install usplash-theme-ubuntu
```
and then
```
sudo dpkg-reconfigure usplash
```

Hope it helps.

---

### Post by MrJackdaw on 2007-01-14
Thanks! This worked for me...

I swear to god - I could type "How to fry sausages with Ubuntu" and *somebody* would be able to solve it!

Brilliant, you're all hero's! :KS

---

### Post by floke on 2007-01-14
sudo apt-get install sausages | grep fry

---

### Post by Janusz11 on 2007-01-17
Can I also change the usplash of Ubuntu 6.10 back to the one of Ubuntu 6.06? 

The artwork of the new usplash of Edgy looks great. But I don't like it being so "quiet". The little box in Dapper Drake's usplash showing what's going on is really great- and I'd like to add that in Edgy Eft. 

Is this possible? 

Thanks in advance.

---

### Post by lotacus on 2007-01-17
I'm always a sucker for boot screens. Doesn't seem to be something that Linux peeps care too much about. heh. What I would like howver, is the boot screen to display more colors at a higher  refresh rate. I know this can be done some how, becuase this is done when first instaling Ubuntu. Would like to know more about these boot screens so I can make a better animation other than the default scrolling bar.

---

### Post by Ingo88 on 2007-01-24
> **ovidescu said:**
> ```
sudo dpkg-reconfigure usplash
```

Thanks. This solved my problem. I installed kubuntu-desktop today but didn't like the blue kubuntu bootsplash :P

> **Janusz11 said:**
> Can I also change the usplash of Ubuntu 6.10 back to the one of Ubuntu 6.06? 

The artwork of the new usplash of Edgy looks great. But I don't like it being so "quiet". The little box in Dapper Drake's usplash showing what's going on is really great- and I'd like to add that in Edgy Eft. 

Is this possible? 

Thanks in advance.

If the quietness is the problem then take a look at this part of your /boot/grub/menu.lst

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=8a82d66c-73fc-426f-9b86-8828287b9180 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot
```

Just remove the word "quiet" and enjoy your speaking bootsplash :)

---

### Post by mblackwell8 on 2007-11-02
the two steps above didn't work for me alone (although i'm a bit of a newb so i tend to follow command line sequences pretty blindly).

i also needed to follow some of the instructions here:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

specifically:
sudo update-alternatives --config usplash-artwork.so

... then select the ubuntu logo from the list

then:
sudo dpkg-reconfigure linux-image-$(uname -r)

which regenerates the initramfs... whatever they are...

still having a great time with this wonderful (altho sometimes frustrating) OS. amazing what has been created here :)

---

