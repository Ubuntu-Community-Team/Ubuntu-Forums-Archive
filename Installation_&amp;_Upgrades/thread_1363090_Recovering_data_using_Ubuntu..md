---
title: "Recovering data using Ubuntu."
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Apthartos on 2009-12-24
I'm attempting to recover some data off my old hard drive using Ubuntu, but I am running into a bit of a problem. I am using a LiveCD to do this, and it is booting up to the main screen (where it gives options to install ubuntu, test memory, etc.) I want to use Ubuntu without installing it, but when I try to do so, nothing happens. When I remove the internal hard drive, ubuntu starts up just fine. However, I can't get information from this drive if it is not in the computer, and putting it back in after Ubuntu loads doesn't read, and doing so while it loads freezes up the computer until I take it back out.
 I have an external hard drive to work with here. does anyone have an idea on why Ubuntu won't load up with my internal hard drive in the computer, and if so what I could do?

---

### Post by Herman on 2009-12-24
I'm only making a wild guess, but it might have something to do with the way you have your IDE cables plugged in and what jumper settings you're using.

If you have IDE hard drive cables and they're the master-slave variety, make sure you have the jumpers on your hard drive(s) and CD drive set accordingly.
Only one hard drive on each IDE cable can be set as master and the other should be set as slave. That includes the CD drive(s) too.
You can tell if your IDE cable is the master/slave type of IDE cable if it has a black plug for the motherboard and two other black plugs, one for each hard disk drive or one for a hard disk and one for a CD drive.

If you have the newer 'cable select' IDE cables, it's best to set the jumpers on the drives in 'cable select' position. I have seen a lot of computers with 'cable select cables and jumpers set as master and slave and they still work okay, but I always set mine to suit the type of cables I'm using. No need for belts and suspenders.
You can identify a 'cable select' type of IDE cable by the different colored plugs they have. The blue plug is for the motherboard socket, the grey plug is for the slave drive, and the black plug goes to the master drive. 
I have heard of people plugging them in wrongly because of limits in the distance the cables need to reach. In that case consider using the master/slave type of cable instead, consider relocating your drives to suit the cables you have, or maybe go shopping and look for a different cable-select cable that suits your computer case and drive arrangement better.

I hope that helps you, it's only a stab in the dark. I hope you can recover all of your data easily.
Regards, Herman :)

---

### Post by Apthartos on 2009-12-24
Well that makes sense, except for the fact that this is a laptop that I am working on, so the hard drive only goes in one way. I should probably also mention that I believe that the hard drive stopped working because It was dropped about a month ago.

---

### Post by chewearn on 2009-12-24
Well, a probable bad news is that the hard drive is already damaged after being dropped.

However, if you could find an IDE-to-USB dongle/enclosure, you could boot up your laptop without the drive.  Then once the LiveCD is up and running, you could plug the USB in and see if the drive is detected and mounted.

Else, check the syslog for any error message.

---

### Post by Herman on 2009-12-24
Have you tried holding your ear close to the drive to listen to it spinning up, or attempting to spin? Most hard drives make quite a loud whirring noise, so you should be able to easily hear it spinning up.
A doctor's stethoscope would be a useful tool if you can get one. Otherwise, an old mechanic's trick is to use a pencil or a pen or similar shaped solid object for transmitting the vibrations. Hold a pencil between the ear and a device you want to listen to. (You should never put anything in your ear though, of course, just close to the entrance of your ear). 
If it's making a clicking or ticking noise, or if it's making no noise at all, your hard drive is probably too badly damaged for recovering the data yourself. In that case if it's important, you could send it to a lab where they might have the right equipment. Probably it would be worth enquiring the manufacturer of your hard drive to find out if they offer that kind of service.

 It would be easier to use a desktop type of computer for this kind of work if you can. There's also the possibility that some other part of the laptop might have been damaged when it was dropped, and the hard drive might not be the faulty part at all, so you should try in some other computer.

---

