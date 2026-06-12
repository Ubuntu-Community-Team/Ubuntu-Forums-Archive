---
title: "Mousepad won't work ubuntu 10.10"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by startaglia on 2011-03-15
Ok so after downgrading from 11.04 alpha 3 to 10.10, my laptop's built-in mousepad won't work neither my network connection. They both worked great on natty and maverick before I upgrade to natty (so we have 10.10 works 11.04 alpha 3 works 10.10 doesn't work anymore). I tried with my brother's USB mouse and it did work after rebooting, but the mousepad doesn't. For the network, I tried rfkill list in the terminal but it doesn't show me anything. HELPPPPPPPP I'm stuck with faildows now I want winux back!

P.s: both features worked great on the 10.10 live cd

---

### Post by mörgæs on 2011-03-15
Have you applied all updates using a wired internet connection?

---

### Post by startaglia on 2011-03-15
I will try it thanks

---

### Post by startaglia on 2011-03-15
Didn't work :(

---

### Post by mörgæs on 2011-03-16
I think we need a little more explanation in order to help you.

How many updates did you install (approx.) after installing 10.10? Did you reboot afterwards? Do you have any trace of what you did differently in the first install - changing boot options, for example? BIOS settings? Does it still run well using the 10.10 live CD? Have you installed 10.04.2? And so on, and so on.

---

### Post by startaglia on 2011-03-16
Ok so 
1. I don't know how many, but it downloaded 300 megabytes
2. Yes I rebooted afterwards
3. What do you mean by changing boot options? Anyways I have noticed the boot screen isn't quite the same in 11.04 alpha 3 and 10.10. (in 11.04, you have a "previous versions" option)
4. BIOS...what? Downgrading changes the BIOS?
5. It still runs well using the 10.10 live CD, but not really for the 11.04 one, which has always been crashing anyways.
6. I first installed 10.04 then upgraded to 10.10 then 11.04 and back to 10.10, so I didn't try 10.04 to get my problem fixed. I will try it.

---

### Post by startaglia on 2011-03-16
Oh I also tried to install kubuntu 10.10 hoping it would work and I could install gnome afterwards, but I have the same problem with the mousepad, but I don't know for the internet since it won't let me log in because it uninstalled gnome and my previous session was a gnome one xD

---

### Post by mörgæs on 2011-03-17
1) Sounds like the updating went well.
3) Adding boot options might help, see below.
4) The installation does not change BIOS, but I wanted to know whether you had tried something there.


I don't have a clear answer, but this might help you:
[http://ubuntuforums.org/showthread.php?t=1477803](http://ubuntuforums.org/showthread.php?t=1477803) 
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by startaglia on 2011-03-19
I think I'll be trying to install 10.04 lts from live cd and then install 10.10 from update manager. I already tried to install 11.04 with a live cd but it didn't work, and I upgraded from 10.10 to 11.04 using update manager and it worked

---

### Post by 1dbzfanjake on 2011-04-17
Hey I guess you solved your problem, but for anyone else looking, if you enter the code: 
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

into the terminal, it will enable your touch pad if your computer recognizes it. I just installed 10.10 and my mousepad didn't work. I looked on the forums and on this thread, but didn't find any help. I found the solution here: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Thank you Ubuntu support team :)
-Jake

---

