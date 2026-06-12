---
title: "Update/Upgrade my 8.04.2"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by hooligandisco on 2010-08-10
I have what was used to be called a dell notebook remix of linux ubuntu 8.04 (currently 8.04.2) running on my 12 inch netbook. It has served me well for nearly two years but apparently it hasn't updated in 112 days and refuses to do so?

I would like to run Lucid Lynx 10.04 on my system because CLEARLY, i am not up to date. when i click the update manager *check* button it acts like it's instaling 97 packages then pops up an error message (image link included).

Can somebody please help me? I would really like to have a newer version of linux ubuntu on my computer!

Image link: [http://i37.tinypic.com/o88dvd.png](http://i37.tinypic.com/o88dvd.png)

---

### Post by lechien73 on 2010-08-10
It looks like it's only the Google repository that's causing you problems.

Try unchecking the Google repository on the "Third Party Software" tab of the System > Administration > Software Sources applet.

---

### Post by hooligandisco on 2010-08-11
Thanks, i did what you suggested and it fixed the error message.. the *check* button just scans 91 updates and then says it's up to date. When i click to see more details, i noticed that many of them are failing. Clearly, my system is **not** up to date because i wouldn't be **still** running 8.04.2

Any more suggestions, help? I want me some LUCID LYNX

---

### Post by dcollier on 2010-08-11
sudo apt-get dist-upgrade, this should upgrade your distro to the latest.  Also check your disk space.

---

### Post by hooligandisco on 2010-08-11
disk space is not the problem, i got that covered..

when i tried the distribution upgrade, i didn't seem to get a nibble.. that didn't work, i am still running 8.04.2

image link: [http://i35.tinypic.com/21bu41.png](http://i35.tinypic.com/21bu41.png)

any more suggestions?

---

### Post by lechien73 on 2010-08-11
Could you post screenshots of your Software Sources tabs, please? Then we can check your repository settings.

---

### Post by kerry_s on 2010-08-11
just do a clean install. run it live first & make sure everything works.

if you update & it don't work, there's no going back your just screwed.

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

---

### Post by hooligandisco on 2010-08-11
> **kerry_s said:**
> just do a clean install. run it live first & make sure everything works.

if you update & it don't work, there's no going back your just screwed.

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

i'm not so sure how i feel about the whole usb thing... i mean it *seems* to be quite an easy alternative, it's just that i would like to see if i could do it all with my own settings and updates first. 

wait, can i do it with a micro sd chip instead? or will it only work with a usb stick

---

### Post by hooligandisco on 2010-08-11
> **lechien73 said:**
> Could you post screenshots of your Software Sources tabs, please? Then we can check your repository settings.

sure, please disclose images with great care....I'm new to this and for all i know i could be giving out crucial information regarding my machine. haha

image link: [http://i37.tinypic.com/14e2o74.png](http://i37.tinypic.com/14e2o74.png)
image link: [http://i38.tinypic.com/333ia9u.png](http://i38.tinypic.com/333ia9u.png)
image link: [http://i37.tinypic.com/35b60p4.png](http://i37.tinypic.com/35b60p4.png)

thanks for the help guys, i really appreciate it

---

### Post by kerry_s on 2010-08-11
> wait, can i do it with a micro sd chip instead? or will it only work with a usb stick


yes, you can use a sd if it's big enough & you can boot from it.

you need to have some kind of install ready, just in case what you have installed becomes unusable.

back up your data off the pc.

---

### Post by hooligandisco on 2010-08-11
> **kerry_s said:**
> yes, you can use a sd if it's big enough & you can boot from it.

you need to have some kind of install ready, just in case what you have installed becomes unusable.

back up your data off the pc.

what do you mean "some kind of install ready" ? what will become unusable and why? i have all my documents and files backed up so that's not a problem...

---

### Post by kerry_s on 2010-08-11
> **hooligandisco said:**
> what do you mean "some kind of install ready" ? what will become unusable and why? i have all my documents and files backed up so that's not a problem...

for example: you try to update, you reboot & just get a blinking cursor, it doesn't do nothing else.

do you have a live installer you can use to rescue it?
if that fails, are you ready to install a new system?

your install is old, your 4 releases behind the current, there have been many, many changes since then. 10.04 is nothing like 8.04, there in no way compatible, the boot loader is different, the splash is different, 8.04 used the old init system, newer releases use upstart, etc...

straight up, you have a 50/50 chance it may or may not work.

a clean install you have better odds of a working system.

---

### Post by hooligandisco on 2010-08-11
> **kerry_s said:**
> for example: you try to update, you reboot & just get a blinking cursor, it doesn't do nothing else.

do you have a live installer you can use to rescue it?
if that fails, are you ready to install a new system?

your install is old, your 4 releases behind the current, there have been many, many changes since then. 10.04 is nothing like 8.04, there in no way compatible, the boot loader is different, the splash is different, 8.04 used the old init system, newer releases use upstart, etc...

straight up, you have a 50/50 chance it may or may not work.

a clean install you have better odds of a working system.

What are the negative possibilities to this way of updating? Currently, this system is the only one I have to work with and it is imperative that I don't lose it too.

---

### Post by kerry_s on 2010-08-12
> **hooligandisco said:**
> What are the negative possibilities to this way of updating? Currently, this system is the only one I have to work with and it is imperative that I don't lose it too.

like i said you might not make it.
you see you can't just update 8.04->10.04
you have to 8.04-> 8.10-> 9.04-> 9.10-> 10.04

also your running a custom install of ubuntu that dell made, i don't even know if it's still ubuntu compatible. if you add the ubuntu repos to update to the next release, who knows what could happen.

your best bet is just a clean install of 10.04, you'll need to pick a version. from your screenshots it looks like your running a normal gnome desktop, the current netbook version uses a desktop launcher & the stock panel is locked.


i use netbook 10.04 & replaced the panel with tint2, i've also done some tweaks to the launcher.

---

### Post by hooligandisco on 2010-08-12
> **kerry_s said:**
> like i said you might not make it.
you see you can't just update 8.04->10.04
you have to 8.04-> 8.10-> 9.04-> 9.10-> 10.04

also your running a custom install of ubuntu that dell made, i don't even know if it's still ubuntu compatible. if you add the ubuntu repos to update to the next release, who knows what could happen.

your best bet is just a clean install of 10.04, you'll need to pick a version. from your screenshots it looks like your running a normal gnome desktop, the current netbook version uses a desktop launcher & the stock panel is locked.


i use netbook 10.04 & replaced the panel with tint2, i've also done some tweaks to the launcher.

Funny that you mention that! I was wondering if the new netbook version allows you to "switch desktop modes" (my 8.04.2 lets me do so) because as much as I appreciate the way that dell netbook desktop mode looks, i'd prefer the classic.

P.S. what's the stock panel? Once again, I am helpless when it comes to all this jazz, thanks

---

### Post by lechien73 on 2010-08-12
From looking at your repositories and reading this post: [http://uri.tl/11](http://uri.tl/11) I definitely think you'd be better off with a fresh install.

Backup your /home folder, so that your settings and documents aren't lost during the new installation.

---

### Post by kerry_s on 2010-08-12
> **hooligandisco said:**
> Funny that you mention that! I was wondering if the new netbook version allows you to "switch desktop modes" (my 8.04.2 lets me do so) because as much as I appreciate the way that dell netbook desktop mode looks, i'd prefer the classic.

P.S. what's the stock panel? Once again, I am helpless when it comes to all this jazz, thanks

well you can log out & select the normal desktop, but if your not going to use the netbook stuff you might as well go for the standard ubuntu.

here's pics of the normal purple netbook, of the default install.
[http://www.google.com/images?hl=en&source=imghp&biw=1024&bih=604&q=10.04+netbook+remix&gbv=2&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/images?hl=en&source=imghp&biw=1024&bih=604&q=10.04+netbook+remix&gbv=2&aq=f&aqi=&aql=&oq=&gs_rfai=)

the purple background is the first thing i get rid of. ;)

---

### Post by hooligandisco on 2010-08-12
> **kerry_s said:**
> well you can log out & select the normal desktop, but if your not going to use the netbook stuff you might as well go for the standard ubuntu.

here's pics of the normal purple netbook, of the default install.
[http://www.google.com/images?hl=en&source=imghp&biw=1024&bih=604&q=10.04+netbook+remix&gbv=2&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/images?hl=en&source=imghp&biw=1024&bih=604&q=10.04+netbook+remix&gbv=2&aq=f&aqi=&aql=&oq=&gs_rfai=)

the purple background is the first thing i get rid of. ;)

Yeah, i hear yeah.. I was under the impression that since my dell was made for the linux netbook remix, that it wouldn't do too well with the *normal* 10.04, do you think that because I have a netbook that i should install the netbook edition?

---

### Post by kerry_s on 2010-08-12
> **hooligandisco said:**
> Yeah, i hear yeah.. I was under the impression that since my dell was made for the linux netbook remix, that it wouldn't do too well with the *normal* 10.04, do you think that because I have a netbook that i should install the netbook edition?

nope, you can run what ever you want. some feel the desktop version is faster, some use xubuntu, some use lubuntu, some go fully custom.

we got a saying around here "use what you like". ;)

---

### Post by hooligandisco on 2010-08-14
Would you guys be so kind as to continue helping me in my other thread? thanks

[http://ubuntuforums.org/showthread.php?p=9718598]("http://ubuntuforums.org/showthread.php?p=9718598")

---

