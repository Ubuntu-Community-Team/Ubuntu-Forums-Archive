---
title: "Enlighten Me: Error installing Xubuntu hard LOCKUP on cpu"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by philomathus206 on 2016-11-10
I have a Samsung N150 Plus with an empty HDD. I've already created a live USB containing Xubuntu, but when I run the installation or "try Xubuntu before installing", it shows this:
[COLOR=#009900]
[/COLOR]```

[COLOR=#009900]
[[/COLOR]    [COLOR=#cc66cc]12.920017[/COLOR][COLOR=#009900]][/COLOR] NMI watchdog [COLOR=#339933]:[/COLOR] Watchdog detected hard LOCKUP on cpu 0
[COLOR=#009900][[/COLOR]    [COLOR=#cc66cc]12.916171[/COLOR][COLOR=#009900]][/COLOR] NMI watchdog [COLOR=#339933]:[/COLOR] Watchdog detected hard LOCKUP on cpu [COLOR=#cc66cc]1[/COLOR]
``` 

:confused:

I really need your help guys, I need it for my studies. 
BTW, I'm absolutely new to Ubuntu and its flavors.

---

### Post by Bucky Ball on 2016-11-10
Welcome. More info please. Are you dual-booting with Windows? Xubuntu 16.04? Whatever you can think of that might be relevant. Looked for [that error online]("https://duckduckgo.com/?q=Watchdog+detected+hard+LOCKUP+on+cpu+0+ubuntu&t=hu&ia=web")? Tried any fixes?

* Just having a sniff about and may be a reasonably obscure bug, among other things. Do you have an ethernet cable plugged in when this happens? Unplug everything from the computer except the Ubuntu install media you are booting from. Are you using USB3 socket with USB2 dongle?

Could you please post the output that comes before the error rather than just the error it's throwing please?

---

### Post by philomathus206 on 2016-11-10
The HDD is completely empty (no OS installed), in fact I've installed Xubuntu 16.04 on it just now, by putting the HDD on a different laptop (I didn't receive an error). Absolutely nothing is plugged in after this.

Mounting the HDD on my MSI U135
[IMG]https://lh3.googleusercontent.com/-cWqyRs6x6ZA/WCSMBuD7n0I/AAAAAAAAABs/nJ6-96G-Xywk1tupKFos-8GcUMnE8lLZwCJoC/w424-h318-n-rw/20161110_223306.jpg[/IMG]

After booting the live USB and installing on my MSI
[IMG]https://lh3.googleusercontent.com/-9hvW0U2rpac/WCSMBgQW2_I/AAAAAAAAABs/jH0-LjSMs9Epj50BQGJN9bNwjn4NX_7CwCJoC/w424-h318-n-rw/20161110_221324.jpg[/IMG]

Works without hiccups 
[IMG]https://lh3.googleusercontent.com/-WNNLs8F4GQk/WCSMBmtf7PI/AAAAAAAAABs/Jtx5lXwKqrUJxP5OMERxLjiCg-l1EX7_ACJoC/w424-h318-n-rw/20161110_221359.jpg[/IMG]

***Then, I remounted the HDD back on my Samsung NP-N150 Plus

Selecting Ubuntu
[IMG]https://lh3.googleusercontent.com/-bJ8kxWfjX6s/WCSMBklzbCI/AAAAAAAAABs/NEucVjwbLrgt01VVUbspuqv_5ImrKaxfQCJoC/w424-h318-n-rw/20161110_215749.jpg[/IMG]

After Selecting--the same error popped back
[IMG]https://lh3.googleusercontent.com/-CFRP88DiFRQ/WCSMBjWh5II/AAAAAAAAABs/2TrFE1iPxSUDOajsDLL2AntMYqB0uaB7gCJoC/w424-h318-n-rw/20161110_220139.jpg[/IMG]

I've done research about it, but I can't find or transpose the solutions to this context--that's why I came here for help. 
Here are the specs of my samsung: [http://tech.firstpost.com/product/netbooks/np-n150-jp0gin-specification-183822.html](http://tech.firstpost.com/product/netbooks/np-n150-jp0gin-specification-183822.html)

---

### Post by Bucky Ball on 2016-11-10
Confused. You now have Ubuntu installed on the hard drive, the hard drive in the computer, when you boot, what do you get? You are obviously not getting this:

> ... "try Xubuntu before installing"

... as you shouldn't be getting 'Try Ubuntu' options from an install. 

So, you select Ubuntu at boot and after selecting ... what? As I say, if the problem is now anything other than this:

```
[    12.920017] NMI watchdog : Watchdog detected hard LOCKUP on cpu 0
[    12.916171] NMI watchdog : Watchdog detected hard LOCKUP on cpu 1
```

... then you're better off starting another thread or changing the title of this one as that is what your thread title's about and any new problem is off-topic and your chances of support will be reduced. ;)

---

### Post by philomathus206 on 2016-11-10
Okay, here's what I did step-by-step:

1. I created a live USB containing Xubuntu.
2. I booted it on my Samsung NP-N150 Plus.
3. When I select "try Xubuntu before installing" or "install", I get this message: 

[    12.920017] NMI watchdog : Watchdog detected hard LOCKUP on cpu 0
[    12.916171] NMI watchdog : Watchdog detected hard LOCKUP on cpu 1

4. So, I mounted the HDD on a different laptop, an MSI U135. 
5. I booted the live USB once more and selected "try Xubuntu before installing", and afterwards, selected "install".
6. It worked, I did not get the error.
7. Installation is done.
8. It works on my MSI.
9. I remounted the HDD back on my Samsung NP-N150 Plus.
10. I selected "Ubuntu".
11. And the same error popped back:

[    12.920017] NMI watchdog : Watchdog detected hard LOCKUP on cpu 0
[    12.916171] NMI watchdog : Watchdog detected hard LOCKUP on cpu 1

12. It does not work on my Samsung.

Conclusion: Installing or running Xubuntu on my Samsung NP-N150 Plus, gives this error:

[    12.920017] NMI watchdog : Watchdog detected hard LOCKUP on cpu 0
[    12.916171] NMI watchdog : Watchdog detected hard LOCKUP on cpu 1

The problem is INSTALLING Xubuntu on my Samsung, and actually running it.

Now, how do I fix the error?

---

### Post by Bucky Ball on 2016-11-10
> **philomathus206 said:**
> Now, how do I fix the error?

Wouldn't have the faintest idea, but at least that's clear. You have Ubuntu installed on the hard drive in the Samsung and get exactly the same error message as you do when you try and launch anything from the install media (USB or CD/DVD) so I don't imagine this has got anything to do specifically with installing it. There's something about Xubuntu that your machine is not liking, period, as it is exactly the same error installing or installed already on the hard drive.

To experiment, try spinning a Ubuntu ISO and see if you get *exactly* the same error when you boot from that. Do you know what graphics card that machine is using?

As I say, I had a sniff around for that error earlier and found little.

---

### Post by philomathus206 on 2016-11-10
> [COLOR=#000000]To experiment, try spinning a Ubuntu ISO and see if you get [/COLOR]*exactly the same error*

Okay, I'll download it right now and I'll try it tomorrow.

My Samsung uses an Intel(R) Graphics Media Accelerator 3150.

BTW, I found this: [https://github.com/TobleMiner/wintron7.0/issues/2](https://github.com/TobleMiner/wintron7.0/issues/2) - something about clocksource settings, I don't know how to do that in this context. But, I can follow instructions pretty well. ;-)

---

### Post by philomathus206 on 2016-11-10
I found the solution by exploring the BIOS, I changed DOS mode to "other". I can't believe I missed that! I'm using it right now. :cool:

---

### Post by Bucky Ball on 2016-11-10
Fantastic news and well sniffed out. :)

Please mark the thread as solved using Thread Tools at top of page or check link in my signature at bottom of my post for how. (Doesn't close thread but does help others.)

Enjoy. :)

---

