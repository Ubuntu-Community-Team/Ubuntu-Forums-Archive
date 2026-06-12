---
title: "Installing ubuntu on the most broken laptop ever"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Ilovemahcup on 2010-07-18
Hello,

I have a Fujitsu Siemens 1667g laptop on witch I want to install ubuntu, with the following problems:

a) screen is broken, so now I run windows on a screen connected to the DVI output on the laptop. Normally I would press FN-F4 to switch between screens, but that does not work in ubuntu

b) CD-rom is broken, so no cd-rom install for me

c) computer does not support USB-booting

d) only have access to wireless network

So, how could I install ubuntu on this one? Most obvious answer would be wubi, but how do I switch the view on the external monitor by default?

---

### Post by Asymptotic on 2010-07-18
Does the boot sequence (splash page etc) show on your DVI monitor? If so could you change the BIOS settings to say which monitor is the default one?...

Maybe I'm clutching at straws I dunno.

Feel free to ignore my suggestion.

I'll go back in to my hole.

---

### Post by Asymptotic on 2010-07-18
Hold on a sec, couldn't you change which monitor is your primary one in the windows display settings? then you shouldn't need to press Fn F4 any more, even for windows? The setting should persist right?? Then when you use Wubi (which im guessing is a virtual machine running Ubuntu under windows) it should stay on your primary monitor, i.e the DVI one.

---

### Post by Zimmer on 2010-07-18
I think you need to have a read around here
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

and see which combination might suit your purpose...

..as for the monitor, you might get lucky and X will detect it as the only one working :) if not..  FN F4 works for me when switching screens.... particularly when using projectors..

---

### Post by Rhubarb on 2010-07-18
I don't have much experience with wubi, but I've got loads of experience with installing ubuntu on laptops that have:
[LIST]
[*]broken screen
[*]no cdrom drive
[*]unable to boot from usb
[/LIST]
And I have managed to setup a server via wireless as well - without any LAN connection with no desktop.

Wubi might be good, I really don't know.

My method is somewhat complicated, and not for the feint of hart.
But basically:

Remove the laptop hard drive, put it into another laptop / hard drive adapter onto a regular PC.
Install ubuntu onto the hard drive.
Make sure to install ssh onto it as well.

At this point you may need to change some configuration files around (such as networking stuff - to make wifi connect automatically - which isn't too easy in this case).

Put the hard drive back into your laptop, cross your fingers.
If it goes onto the network, then you have ssh access, from there you can configure up other stuff if need be (if you can't see your external monitor).

To broaden your options, I'd make an image copy of your laptop hard disk first - so you can always revert back to windows should things not work too well.

Sorry I can't be of too much help, it's something that presents quite a challenge. It's certainly possible to do, it's just not at all easy. (Unless of course wubi works easily for you).

I'm driveling on a bit now :P  - but you get the idea.
PM me if you need more help.

---

### Post by Ilovemahcup on 2010-07-18
> Does the boot sequence (splash page etc) show on your DVI monitor? If so could you change the BIOS settings to say which monitor is the default one?...

I can use Fn-F4 to see the boot sequence up until the log-in screen. The login screen appears on the default screen, and I cannot use Fn-F4 to switch screens.

The BIOS has no such settings.

I guess I kinda missed the proper question in my first post. I can install it just fine with WUBI, the question is "How do I reconfigure the xorg to use my second monitor by default?". Recovery mode also starts by default on my main screen, so that's a dead end.

---

