---
title: "(SOLVED) Mouse not working during installation"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by gordan-vrbanec-vepar on 2013-11-14
Hello!

I have an older computer that i want to put lubuntu on. I read somewhere that it's the best distro for older computers.
I don't know the exact specs, all i know is that it has 256 RAM, so the processor can't be all that powerful.
And, i can't get BIOS to show, and spamming DELETE key does nothing, so i can't get into BIOS.

BIOS aside (for now, it's a separate issue but i need the bios to show at some point if i want to change anything there), after that, lubuntu CD boots up normally.
I select "nomodeset" because it freezes otherwise, and it loads good, except, when i get to the actual installation part, the mouse doesn't work.
The pointer is there, but moving the mouse does nothing. It even "shuts dows" for a lack of a better explanation. The red light stops working. Unplugging the mouse and plugging it in again lights it up again, but it still doesn't work.
This is a new USB mouse. I tried plugging it in the PS/2 port with an adapter, but it still doesn't work, except the light doesn't shut down.

I tried using the keyboard, but nothing is happening no matter what i press. I don't know if that's how it should be, but regardless of that, i don't know how to install linux without a mouse, so the keyboard wouldn't do me much good anyway.
Maybe there's some option in BIOS that i should change for the mouse to work but i can't get into bios...

I tried selecting "Try ubuntu without installing", also with "nomodeset", but it doesn't boot up, probably because the computer doesn't have enough memory to do that

Please help, i don't know what to do.

---

### Post by ibjsb4 on 2013-11-14
Without knowing your computer specifications, this is a shot in the dark.  

You can try installing with the alt-install CD.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

However I think your going to see a performance hit with just 256M of ram.

You may have to go with another lighter distro.

You need to figure out what cpu you have and what kind of video support you need.

---

### Post by gordan-vrbanec-vepar on 2013-11-14
Hmm... That's gonna be a bit hard to do when i can't get into bios, but i'll think of something.
The video part works good with nomodeset. Everything shows up, no graphic glitches or anything, it's just that the mouse shuts down. Maybe the keyboard too, i don't know.

Thank you for the link to the alternate ISO, i'll try that.
If i can't get this to work, what distro would you recommend i try?
Which one is simmilar to ubuntu?

---

### Post by ibjsb4 on 2013-11-14
> If i can't get this to work, what distro would you recommend i try?
Which one is simmilar to ubuntu?

Its been years since I ran another distro, so not a good person to ask.  Puppy Linux looks to be a still good choice.

[http://distrowatch.com/?newsid=07977](http://distrowatch.com/?newsid=07977)

---

### Post by gordan-vrbanec-vepar on 2013-11-14
Ok, thank you, i'll check it out.
I'm downloading the alternate install now, so i'll try that first and see how it goes, and if the mouse works after and if lubuntu boots up in the end.
If not, i'll try some other distro.

---

### Post by gordan-vrbanec-vepar on 2013-11-14
Ok, the installer worked great, i managed to install it and everything was great during the installation.

But, when i try to boot it up, after the splash screen with the dots, the monitor goes to sleep and nothing happens after that. I can't do anything.
I managed to find some more memory lying around in some other dissasembled computer that i found, same one, installed it and it now has 512 MB RAM...
Didn't seem to help though. Still blank screen and monitor goes to sleep.

I searched for a fix, and it says to press shift until GRUB shows up, then "e" to edit options for boot.
I did that and i'm supposed to add nomodeset there, but it doesn't say where on some sites, and on others it says, but i don't have that written there...
Also, at the end of the text there is something like

"re nomodeset quiet splash" written, so i assumed nomodeset is allready written there and that it should work. 

It doesn't... 

What should i do?

---

### Post by ibjsb4 on 2013-11-14
512M of ram should do just fine.

Nomodeset!  Yes a very good idea.  See if this helps you:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Your Google Fu is very good :)  back at you with my Googlubuntu Fu :D

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nomodeset&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nomodeset&sa=Search&cof=FORID:9)

---

### Post by gordan-vrbanec-vepar on 2013-11-14
Thank you! I'll check that out and try it.
I hope i can work something out. :)

EDIT: I marked this thread as solved, because the new issue doesn't have anything to do with the mouse not working. Mouse was not working so i couldn't install, i did an alt install instead and it's done. :) I'll open a new thread for lubuntu not booting.
Thank you!

---

### Post by mörgæs on 2013-11-15
Thanks for an attempt at marking it solved, but the best way is using 'thread tools'.

---

