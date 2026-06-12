---
title: "Another Installation Issue [Please Help]"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by drichicken on 2007-05-29
Hi

I have installed Ubuntu couple of times on my Computer. After the installation, my Ubuntu is always look like this..

[IMG]http://img514.imageshack.us/img514/2112/p5290481pr5.jpg[/IMG]

---

### Post by merlinus on 2007-05-29
Were you able to get the live cd up-and-running without this kind of screen?  If so, it probably is due to the wrong driver being loaded for your video card after installation, and/or the wrong screen resolution..

If you can boot from the live cd, look at etc/X11/xorg.conf on your hard drive and post the contents, as well as the make and model of your video card.

Then someone may be able to help.

-merlin

---

### Post by drichicken on 2007-05-29
ohh yes Thank you.. it makes sense now..

I will try to download other Ubuntu version and see if that works..

---

### Post by Wim Sturkenboom on 2007-05-29
> **drichicken said:**
> I will try to download other Ubuntu version and see if that works..And why would you do that?
Makes more sense to post make and model of videocard (as requested) and of monitor.

When you have that screen, does <ctrl><alt><Fx> (x=1..6) take you to a console? If so, there is a command that you can run to configure your video (something with dpkg configure ....); just search the forum.

---

### Post by drichicken on 2007-06-01
my video card model is leadtek 256mb 6800 GS

---

### Post by drichicken on 2007-06-12
what should I do after I have found out my video card?

Thanks

---

### Post by drichicken on 2007-06-13
i think i know the problem

When i bot from the cd, I have to choose "1024x768x32",if I boot from VGA, it will looks like that (the pic I show you above)

so, when it is installed,  it always boot to display it in VGA. is there anyway to make "1024x768x32" a default?

I dont know if that makes sense to u guys..

thanks a lot!

---

### Post by merlinus on 2007-06-13
Once installed, if it does not run in your desired resolution, there are a number of things you can do to make it so.

-merlin

---

### Post by drichicken on 2007-06-13
What should I do to make my Ubuntu run in desired resolution? can you provide me with a link?

thanks

---

### Post by merlinus on 2007-06-13
Have you installed ubuntu, or are you running it from the live cd?

If it is not installed, then nothing you do will make the changes stick.

After installation, here is a good guide:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)

-merlin

---

### Post by drichicken on 2007-06-17
I cant even enter ubuntu, knowing that the resolution is too high.

I am, downloading the file right now, Will try yo install it, hopefully it works :)

---

