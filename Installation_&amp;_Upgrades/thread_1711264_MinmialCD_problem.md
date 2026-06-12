---
title: "MinmialCD problem"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by ddavidd on 2011-03-21
Intel desktop board D845 GEBV2/D845 PESV, presumably Intel on-board graphics, Celeron 2 GHz, upgraded to 1 GB RAM

Computer ran a long time without problems under W2k, I would like to install Ubuntu.
The computer is absoutely determined not to install ubuntu, I have now tried everything I know for two days

I have already posted under this thread, although unfortunately noone had any suggestions:
[http://ubuntuforums.org/showthread.php?p=10580052](http://ubuntuforums.org/showthread.php?p=10580052)

I kept on trying everything and got this error:
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

There is a very good post here (post 176 !):
[http://ubuntuforums.org/showthread.php?t=1443231&page=18](http://ubuntuforums.org/showthread.php?t=1443231&page=18)

which gives a solution for this error by installing the MinimalCD

I downloaded the Minimal CD and tried to install it, but it stopped with this error:
undefined video mode number 314

Inspired by this blog:
[http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html](http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html)

I copied the MinimalCD onto the disc, opened all the .cfg files and wherever I found vga=788, changed it to vga=normal and then burnt the same altered files onto a new CD

but now the MinimalCD does not boot, just brings the dreaded flashing dash at top left.

HELP Anyone got any suggestions, please?

---

### Post by Rasa1111 on 2011-03-21
Which version of Ubuntu are you trying to install?
10.04?
10.10?

if it was 10.04, it wouldnt surprise me..
but 10.10, i think it would.  lol

I dont have much to offer at the moment, so i apologize.
hopefully my post will bump you back to the top for someone smarter to see. lol

good luck ddavidd.

---

### Post by ddavidd on 2011-03-21
Thanks for the reply!

I am trying to install ubuntu 10.10. 

The second link I pasted says:

If you encounter the problem while installing 10.10, the method mentioned here is the way to go

have I perhaps made some simple mistake so the CD won't boot?

---

### Post by Dutch70 on 2011-03-21
I don't know much about the minimal cd install, but have you tried installing Xubuntu 10.10? 
[[COLOR="Blue"]http://www.xubuntu.org/[/COLOR]]("http://www.xubuntu.org/")


Also, if you have & can boot to a usb, it's much easier & faster.

Edit: 
 You can also install the Ubuntu desktop from synaptic in Xubuntu. You would then be able to choose to log-in to Ubuntu or Xubuntu at the log-in screen, or just remove the Xubuntu desktop. It looks like your pc is just having trouble with the Ubuntu installer. 
There is a good chance you'll find that Xubuntu works better on your machine anyway.

---

### Post by cbowman57 on 2011-03-21
This is a non-fatal warning that is pretty common, never prevented any of my systems from running.  Reading further down the link you provided (#176) it looks like the problem was the result of a bad CD-DVD drive.  I wouldn't recommend the minimal install method to anyone other than very experienced linux users.

Does the CD boot to a desktop but the installation fails?

> **ddavidd said:**
> 

I kept on trying everything and got this error:
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)



Never mind, I read your earlier post.  It sounds like a bad disk or drive.

---

### Post by ddavidd on 2011-03-21
Thanks for the suggestions!

The GLib error was while trying to install the 10.10 CD

The attempt to install from the MinimalCD stopped with the video mode error and wouldn't click away. 
Anyone got any suggestions how to make it continue?

I have already tried changing the CD drive, the disc always worked with the previous installation. Everything is found all right in the BIOS set-up (the only unusual thing is that I have to set to boot from CD again after switching off. What might that indicate?)

---

### Post by Rasa1111 on 2011-03-21
> **Dutch70 said:**
> I don't know much about the minimal cd install, but have you tried installing Xubuntu 10.10? 
[[COLOR="Blue"]http://www.xubuntu.org/[/COLOR]]("http://www.xubuntu.org/")


Also, if you have & can boot to a usb, it's much easier & faster.

Edit: 
 You can also install the Ubuntu desktop from synaptic in Xubuntu. You would then be able to choose to log-in to Ubuntu or Xubuntu at the log-in screen, or just remove the Xubuntu desktop. It looks like your pc is just having trouble with the Ubuntu installer. 
There is a good chance you'll find that Xubuntu works better on your machine anyway.

good advice i think.

If you can boot from USB, and have one handy..
make a startup disk on that, and try it..

trying Xubuntu is also a good idea.
you may find that start right up for you.

then if it does, and you rather have ubuntu desktop, you can install it. 

 I have a lubuntu disc, xubuntu disc, ubuntu discs, kubuntu discs..
but the only one that would open and install on my 13 year old thinkpad was Xubuntu. (10.04)

 Sorry i cant help more,
im not well versed with these issues,
specially not minimal installs! 

good luck mate

---

### Post by ddavidd on 2011-03-21
Thanks for the sugestions, I will try Xubuntu.

Genmerally, I have got to like Ubuntu and now have all the family running it, but if Xubuntu works in this case, fine.

---

### Post by Dutch70 on 2011-03-21
> **ddavidd said:**
> Thanks for the sugestions, I will try Xubuntu.

Genmerally, I have got to like Ubuntu and now have all the family running it, but if Xubuntu works in this case, fine.

Really doesn't matter, if Xubuntu installs for you. You're about 3 clicks from having Xubuntu & Ubuntu. Not a lesser version, it's the real deal. 

If Ubuntu works well on your hardware, and you want to remove Xubuntu, that's quite simple to do also.

---

### Post by Hakunka-Matata on 2011-03-21
@[ddavidd]("http://ubuntuforums.org/member.php?u=482316")

Have you tried the 'nomodeset' option yet, flashing cursor upper left hand corner,

I searched this thread and found no instance of "nomodeset"

---

### Post by ddavidd on 2011-03-21
thenks, I have tried all the switches.
One of my other computers only installed with noapic

Currently downloading Xubuntu, takes about 3 hours with our weak DSL

---

### Post by Hakunka-Matata on 2011-03-21
so what video hardware does that machine have?  
Are you saying you're thinking Ubuntu won't run on the machine?

---

### Post by ddavidd on 2011-03-21
I presume it has Intel on-board graphics.

On the Intel web site, it has drivers for Linux, but it also says that installation should normally be no problem, and the drivers seem to be for Red Hat and Suse, and look awfully complicated to install

---

### Post by Hakunka-Matata on 2011-03-21
Please post output of:

```
lspci
```

---

### Post by ddavidd on 2011-03-21
sorry, I can't post the output of commands because I have been trying for two days to install it and it won't install the live CD either!

Am currently buring Xubuntu to try that

---

### Post by ddavidd on 2011-03-21
Further attempts:

Downloaded and burnt Xubuntu 10.10 CD, 

1. install, initian impression good, lots of CD noises
error "failed due to unknown user id,- continued!
error "try clesning the CD dirve", continued!
notice "Ubuntu is running with reduced graphic settings"
"have to restart graphics", black screen with init messages, hang

Installed new DVD burner
Xubuntu "try out"
freeze (no disc or CD lights, right-hand two lights on kexboard flashing

Xubuzntu "install" with option "noframeset"
stopped, lasz message   ? syscall-call+0x7/0xb

Xubuntu install, no options
back to the dreaded gfalshing dash at top left

It is really starting to look like a graphic driver problem.
There is another installation option F4 use driver update CD,which sounds promising
Does anyone have a link to a Howto for this with Intel D845 graphics?

---

### Post by ddavidd on 2011-03-21
I tried it with a Ubuntu 7.10 CD, which offers a safe graphics mode.

Doesn't help, it also freezes when I try to install, try out and in safe graphics mode. 

If only I could get to an operating system, I could work on the drivers, but it always hangs somewhere.

Next try: Ubuntu Alternate CD, which offers more options.

---

