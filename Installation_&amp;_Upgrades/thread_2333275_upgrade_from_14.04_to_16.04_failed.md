---
title: "upgrade from 14.04 to 16.04 failed"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2016-08-08
the upgrade failed and resulted in a black screen, no way to wake it up. had to reboot by holding the power for 10secs.
now when it tries to load it says kernel panic and gets to a black screen with error messages. tried to login to earlier versions of ubuntu, but nothing works.
upgrade was proposed to me by the system.
how can I preserve my old filesystem? I suppose I need to install 16.04 from a usb now. 

thanks everyone.

---

### Post by marcos-sub on 2016-08-08
Hi

I have a similar issue. The upgrade to 16.04 failed and now when try to start the laptop it loads a Guest session. Grub works ok I tried recovery mode, repair broken packages and all sorts but nothing. I have also tried boot-repair
[RIGHT][COLOR=#000000]**Distro **[/COLOR][COLOR=#000000]Ubuntu 14.04 Trusty Tahr[/COLOR][/RIGHT] 

Thanks

---

### Post by katcw on 2016-08-09
I have the same problem. I made it worse by using an old Ubuntu Live disk, and that didn't give me access to any of my files but somehow dropped me into Ubuntu 3.03!

---

### Post by raman03 on 2016-08-09
Hi,
I have started the upgrade to 16.04 and now it boots and take me to login prompt and not booting in GUI.  I tried to use Grub screen but it keeps taking me to command line asking for login.  I tried my login and password but it is not accepting it.  I am sure I made my id as administrator when I installed Ubuntu 3 years back on this machine.  It has been working for 3 years and I updated so many times.  But this time it is giving this problem.  One another thing when I boot it shows an error but that screen passes so fast, how do I stop that so I can see what is that "Failed" error"?
Or any other suggestions.

Thanks,

---

### Post by zurga on 2016-08-09
Similarly, my software updater offered me the option to upgrade, which I accepted. After the downloads, the installation took a long time with a lot of errors reported. It eventually terminated, without the ability to shut down or reboot. The pc is now completely broken. If I try to turn it on, it comes up with a glass screen that offers a number of options. I can select 'ubuntu' and press 'c', which gives me a bash like command line in <grub> which I have no idea what to do with.
Is there anyway I can retrieve my files before I install Ubuntu from scratch?

---

### Post by Richard_York on 2016-08-10
Fairly similar here: I accepted the offered 14.04 to 16.04 upgrade on my laptop, left it with all packages apparently downloaded and installing, & went to bed as it was so slow. I took the option to remove obsolete packages.
This morning on restarting, it gets as far as the purple screen, asks for password, then on entry, just switches into sleep mode or something like it. Holding power button restores a fuzzy version of screen, but again entering password results in it dying again.  
No idea where to go from here, but not inclined to upgrade the working 14.04 laptop I'm using to write this. Do I just have to create a usb and start all over again - and as Stephenbbb fears having to reinstall filesystem and everything else?
Thanks for any answers!

---

### Post by stephenbbb on 2016-08-10
Folks, I think we should forget about 16.04 until Canonical issues a good sub-version. I will try to re-install 14.04 and report here.

---

### Post by mörgæs on 2016-08-10
Upgrading is always dangerous and I don't recommend it. The errors reported here are not necessarily due to bugs in 16.04.1 but could be a problem with upgrading in general. See more in the link in my signature.

I recommend trying 16.04.1 (not 16.04.0) in a live boot and a clean install if it behaves well.

---

### Post by katcw on 2016-08-10
my computer now tries to boot into version 3.03 (see earlier note). I've read one cannot upgrade from a really version to a newer one. So what do I do now? Unfortunately I did not not backup my files recently.   Yikes!!

---

### Post by mörgæs on 2016-08-11
There is no such thing as Ubuntu 3.03. 
Please tell in details how you did the live boot.

---

### Post by QIII on 2016-08-11
Folks, this thread now has no fewer than 5 hijackers.  Please do not hijack threads.

Since this has already caused one person who would like to provide support to start trying to understand an issue presented by a hijacker, this Gordian Knot is closed.

To the OP:  my apologies.  Feel free to start a new thread and refer back to this one.

To all others who piled on:  please start your own individual threads and do not hijack each other.  "I'm having the same issue..." posts are hijacks that are not helpful and cause confusion.

Thank you.

Closed.

---

