---
title: "Black screen when I login in Ubuntu 13.10"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by leon.lain.delysid on 2013-12-30
Hi!

Summary: When I login to my user account, neither Unity nor Gnome load and I get a black screen.

When I got my laptop, I installed Ubuntu alongside Windows 7 (must've been 11.04 at the time). Unfortunately, Ubuntu was never able to tame my Nvidia graphics card. I think I remember I had to reset the driver settings but it completely broke everything, Windows included. Everytime I tried. I spent days reinstalling everything over and over again without success.
So, I stopped using Linux. I left it on my hard drive probably because I didn't want to install everything all over again.

One year ago, I decided to dig it out of the dirt, I upgraded to 13.04 and I was left with the lowest possible resolution on Earth. You can't see much of any window that way, including Grub configuration or anything...
So I completely stopped using Linux and buried my installation for good, praying for my Windows setup to be able to boot, because I have everything on there. I managed to get Ubuntu to leave Windows be while still being there like a radioactive cadaver that no one can remove.

And then nowadays I decided that my next computer would run Ubuntu as its main OS, because Windows is Windows and Ubuntu is so great. Something I have never done before. I'll still keep Windows for games and stuff that's Windows only.
But I couldn't wait and went to upgrade my existing Ubuntu installation. I won't be able to make this one my main OS, it will have to wait for a new computer. But if I could at least use it as much as I can, the wait for the new computer would've been ok.

So I upgraded to 13.10 a few hours ago. But to everyone's astonishment, I seem to have the same problem everyone seems to have on the Internet but has no solution whatsoever. When I login, I get a black screen with my cursor in front. I tried many solutions I found here and there. It doesn't seem to be caused by Nvidia drivers, but the last things I saw before giving up were errors preventing startx from finishing. Something like "warning : one_level is 1 levels but RALT has 2 symbols, but no worries because it won't stop X from running...". I have no idea what on Earth that could ever mean and at 2 a.m., I just can't take it anymore.
When I removed xorg.conf, I had managed to get the right resolution again, but the black screen remained standstill remains to this moment.

I really wish this won't happen when I switch because that would mean not switching. And I really want to dump Faildows once and for all, and I believe Linux should be a choice, not a non working alternative to forget about.
I decided to stick to LTS releases as they are supposed to be more stable, hopefully preventing a user to have to give up Ubuntu completely...

Now I'm really tired, and have to wake up for work in less than 4 hours... So I'll come back tomorrow and we'll try to make my Ubuntu installation work.
My goal here is first to have my current installation working so I can maybe half switch for now. And in a few months to have 14.04 as my main OS, but that'll be work for later.
Obviously, if I might have and zombie for a system everytime I change the background, I can't risk it. I backup my data but I don't have days at a time to reinstall my systems.

Thanks for reading, I hope I didn't bore anyone. I thought I'd share my experience so you'd be able to help me, and I thought this information was important. (Bear in mind that I'm exhausted, so I did what I could. XD Enough mumbling, let's sleep...)

My graphics card is an Nvidia GeForce GT 540M as it might interest some of you.
Also, I want to get an ATI card next, so is that a good choice concerning the drivers on Debian?

---

### Post by leon.lain.delysid on 2014-01-01
Hello,
I solved my problem. Half solved, really.
I reinstalled Ubuntu 13.10 from the LiveCD. So I didn't really fix it like other people would want. But now I have information that might interest some people having the same problem I had.
The  problem was the Optimus technology Nvidia mobile cards have. **If you  have an Nvidia card with Optimus, do not by any means install nvidia-current (the proprietary drivers from Nvidia in the Third Party proprietary section of Software Updates).** Doing this is known to at best not give access to the card more efficiently or at worst break your system like it did with me.
It is a known bug with these drivers, and Nvidia decided a few years ago when the problem arose that they wouldn't fix it. It would seem you're only a Linux user after all... It's been a few years that the technology exists and is put in place in every new mobile card. So beware.
Fortunately, society stepped in. The community has developed its own home-made solution. The project is called Bumblebee. I installed it and it everything worked fine afterwards (just a few bugs here and there).
[http://bumblebee-project.org/](http://bumblebee-project.org/) [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

It could be something else that fixed it for me. I had installed Gnome 3 and Gnome 2 as alternate Desktops and now they're gone obviously. I read among all my research that gnome packages might break Unity. I removed all gnome packages but it made no difference. That's when I reinstalled my system.
Bear in mind though that my display was very small and stretched and buggy (I had no mouse too at first) until I installed Bumblebee packages. And it remains true and known that Optimus coupled with nvidia-current can break your system.

For people that might get stuck:
If the display doesn't work, you can switch to a terminal with Ctrl+Alt+F1 to F6 (and switch back to graphical display with Ctrl+Alt+F7). Your username is without capital letters or special characters. To install packages, do "sudo apt-get install" space the name of your package. You can remove packages with "sudo apt-get purge" space packagename. You can reinstall packages with "sudo apt-get install --reinstall" space packagename. To reboot, type "sudo reboot". This information comes in handy if you want to implement my solution.

Hope this helps somebody one day...
Until then, see ya!
(I will receive notifications of any replies, so ask me anything if you like. ;) )

PS: And now I don't want too boot Windows anymore. ^^''' Seems like I just might migrate (or half-migrate) sooner than expected after all...

---

