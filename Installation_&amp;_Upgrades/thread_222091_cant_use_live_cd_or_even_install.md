---
title: "cant use live cd or even install"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by Seyeko on 2006-07-24
I finally got my Ubuntu discs in the mail the other day and I've been trying to set ubuntu up as a second OS. Dual booting with Windows xp. I created my second partition for Ubuntu and was trying to run it as a live cd first, but each time i stops and gives me this error:
> Failed to start the x server which is my Graphics interface or something.
So i went to the Ubuntu forums and someone said to type this command in:
> sudo dpkg-reconfigure xserver-xorg

so  i did and it gave me some options to select from and driver,
I use a Radeon PCI 9250 graphics card, but I couldn't find it on the list. IT did have the intel extreme graphics controller card that came built onto my mother board there, but I don't use that one.

So I haven't been able to install it or even get it to work via the live cd since it stops at this point.

does anyone here have any suggestions on how I could get this running?
Im brand new to linux and I really wanted to see what this was like.

thanks
-josh

edit:

someone said to do this:
> Well you'll need to install the ati linux drivers.
I assume your internet connection works.
enter this in the shell:
wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run)

now type:
chmod +x ati-driver-installer-8.26.18-x86.run

Then:
sudo sh ./ati-driver-installer-8.26.18-x86.run

Now it will ask for your account password!

Select Install and click next.
Installation Mode: Automatic

After that execute:
/usr/X11R6/bin/aticonfig --initial

Offcourse you'll need to accept the agreement etc during the setup.

After this reboot the system and xserver should start.

Incase it doesn't work you might need to try this drivers:
[http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)
_________________

but i am on dial up, netzero.
is there a way to do download it to my harddrive and load it from there some how?

---

### Post by kb3hkg on 2006-07-24
I would recommend you try using the onboard graphics for now until it is installed. It would be much easier that way.

---

### Post by Seyeko on 2006-07-24
wow support does suck.

---

