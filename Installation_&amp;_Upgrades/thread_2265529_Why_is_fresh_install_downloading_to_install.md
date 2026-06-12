---
title: "Why is fresh install downloading to install?"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by Higgins909 on 2015-02-16
I had to download the 1GBish iso only to find out that its hogging my bandwidth... I thought it would be kinda quick, but since it wants to use bandwidth over usb stick... its slow...

Why is it using my bandwidth over my usb?!?!?
14.04.1 64bit... and now the screen just went black... cant get it to do anything...

Idk what version of ubuntu server I had b4, but it was maybe 12ish... only reason I'm upgrading is because of new mobo cpu, and bigger/faster hdd, gigabit...

---

### Post by kerry_s on 2015-02-16
there have been updates since the iso was created, so i'm guessing it's updating to the latest packages.

---

### Post by Higgins909 on 2015-02-16
This is driving me crazy!!! idk why the iso was half a gig* ... my usb thumb drive pretty much does nothing!
I'm on my damn 3rd try, this time with the 14.10 64 server...
I got some sort of dmi pool hang.... each time takes about a hour!!!
I can't find much info about it, but its some sort of mirror thing....


Just to be clear, I have not successfully booted into ubuntu server, yet.
... Got Verifying DMI Pool Data ........... hang again...
all I changed out was 1 hdd (thats all that is currently plugged in, play to manually set others up)
cpu, ram, mobo, video card.


I tried reseting my bios once, I got it to says success, but it still hung, tried to take out mobo battery for a bit, didn't fix either...


I thought I was going to have a faster server up in a hour.... guess not. giving up for the night...


Edit:
I wanted to get a better look at the options for booting from usb, because I was using server install or something like that, there where some other options that I wanted to explore.
I booted the usb, this time the boot menu was different, then it boots into ubuntu....
I'm guessing the boot got installed onto the damn usb drive, instead of the hdd that I auto partitioned....
its that, or it didn't use the hdd at all.
I took power from the hdd, then it wouldnt do anything other then the normal booting beep, pluged it back it, that same :/
why did it possibly install grub onto the usb??? that pretty much = another hour long installation/download...




I finally got it working... have only the installing to disk in, thumb drive, when I got to the formatting part, I unplugged to usb drive, and then reloaded the formatting screen by hitting back or something, and just continued like so... lots of hassle.

---

