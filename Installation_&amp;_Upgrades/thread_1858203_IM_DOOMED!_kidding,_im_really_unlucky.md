---
title: "IM DOOMED! kidding, im really unlucky"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by Bluethief on 2011-10-11
EDIT: aditonal info, im trying to instal 10.04.something, and my main OS right now is vista
the USB thing: [http://img62.imageshack.us/img62/1003/dsc03691cv.jpg](http://img62.imageshack.us/img62/1003/dsc03691cv.jpg)
hey guys im *kinda* desperated...
i tryed, with the help of a total ubuntu fan, to install it
methods tryed :
CD
WUBI
virtual disk(?)
result:
CD: nothing...and out of CDs
wubi: messed up graphics or 'cant find (ubuntu iso file name).iso'
virtualdisk ^^^same result

i bought a usb stick for that, thinking it would work
i followed exactly the tutorial on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
and used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
so i booted on the USB, tryed 'try' and 'install' both gives the SAME result
(purple loading screen)
(a bit later...)
cant (something) on adress 11....
(1 year later)
cant 9something) on adress 12....
(1 year later)
something something wrong IRQ??? ....
(1 year later)
(weird text)
120 seconds later 'something took more than 120seconds'
then every 120 seconds i get the weird bunch of text(and numbers)
after 4 time of waiting 120 seconds 
my screen stop and all i can do is reboot the PC
(by the way during all this my keyboard and mouse are disabled)
but now im really tired of this and i plan on making it work
thanks for any help i really want it to work its absolutely not normal that it refuse to work no matter how i try
(i know i want ubuntu that much since i managed to try it on virtualPC)
PLEASE PLEASE PLEASE THANKS THANKS THANKS
i alway wanted Ubuntu!
and if Ubuntu refuses to work that way, so will BackTrack, no?
without ubuntu(crappy vista)= :( 
with ubuntu(vista go to hell)= :D

---

### Post by Dangertux on 2011-10-11
Ok first things first. While I encourage the use of Linux and Open Source Software, and use Back Track myself on a regular basis for work and amusement. I honestly have to say that with the nature of your post I would absolutely not recommend installing it at this juncture. If you want to play with it in a virtual machine once you get Ubuntu working that's fine, but as it stands right now you need to understand that Back Track is a very specialized distribution. There is no hand holding and it expects you to know what you're doing, in addition to giving you access to very powerful tools it gives you all the permissions necessary to fully leverage them. It also expects you know the risks of running around with those types of permissions. I would highly recommend sticking to a user friendly desktop distro, such as Ubuntu at this time, at least until you know what those "thingies" and "text and numbers" mean, once you're more familiar with that then by all means go and learn.

Now on to your installation problem. From the information that you provided it would seem that you may have some compatibility issues with some of your hardware.  My suggestion would be when you boot (either USB or CD) and you see this screen

[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png?cache=[/IMG]

Hit any key to enter the advanced menu, then follow this guide

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

For editing your boot options, I would at very least insure you add VGA=791 and pci=noacpi. This may or may not fix your issues. However, it's probably a good start. 

If you could perhaps post more detailed information about what the 'text and numbers' are saying we could help you more. 

Also not to be rude, but if you could be more organized with further postings it would probably be easier for people to support you. This is a multi-national forum and english is not everyone's first language, heavy sarcasm and poorly organized posts make it harder for those without a strong grasp of english to support you, even though they may have had similar problems and experiences.

Thanks and good luck :-)

---

### Post by Bluethief on 2011-10-12
PS* yesterday i were frustrated, tired, anoyed, everything you can think of, lol.i use some of backtrack tools on vista and im working on passing from 'skid-medium' to 'good hacker' (have to learn C++ fully)
hey thanks for the answer
actualy when boot from the USB (i press f12 then chose my USB, L:)
i see a menu, if i chose  to try from the USB,
some loading stuff goes on, then it stick to Busybox
it starts telling me things i can hardly understand followed by numbers
ex: [5461.445616]unlink after PCI? controler is surely using wrong PCI
ex:found new high speed USB device
cannot connect on adress 11 ERROR-110
found new high speed USB device
cannot connect on adress 12 ERROR-110
unable to enumerate USB device on port 6 
found new full speed USB device

but then it gets really not understandable and start shooting me bunch of sentences (454.544564:USB_(SOMETHING)_URB 0XW8)
every 120seconds( because i think its trying to do something but keep timeingout every 120 seconds)
after 4 times it timeout, my screen go black, and all i can do is reboot
i tryed installation directly, (not try), same result
im not THAT much of a noob lol but when you get into other OS, BIOS, or programation, im still working to reach  that knowledge level
*and incompatibilities, i dont understand incompatibilities yet*
Thank you!
*another note, once i clicked something on the purple( lol ubuntu color ) menu my keyboard and mouse stop, i mean i cant use them, they receive no power
i made a video of it but ran out of battery and when i looked at my bit of video the quality was so bad i couldnt read
i can make a new one when its done charging, if you want
if you need more informations on my hardware tell me
sometimes i can sound VERY noob and sometime i can sound way better than i really am LOL but anywaY...

---

