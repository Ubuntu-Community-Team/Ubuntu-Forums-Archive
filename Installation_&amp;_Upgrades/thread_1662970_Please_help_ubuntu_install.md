---
title: "Please help ubuntu install"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by AaronsDarts on 2011-01-09
Hello this is really starting to make me mad, I have installed ubuntu on a cooke comps and have never had this type of problem. I am trying to install it on a sony vaio vgn-nw350f I really want to put uberstudent on it from uberstudent.org, but I keep getting the error "unknown keyword in configuration file". So I decided to try and install from an old ubuntu live cd version 8.04.1 this starts to boot then ask for language and finally asks me what I want to do either install or run from cd, either one i choose goes to a ubuntu loading screen like normal then I get a black screen with dotted lines going down from top to bottom, then goes to a really bad looking orange screen where I can kinda see a mouse but nothing else and it doesn't load.

I made sure that all my drives are up to date and still nothing I tried several times with no luck, I really can't stand windows any longer... I know that the ubuntu disc does work because my friend used it a couple of weeks ago. Plus I installed it to part of an external but for some rain when I go to boot off of it all I get is, the - blinking repeatedly...

Please help me I have looked at other forms with no luck.

---

### Post by slooksterpsv on 2011-01-09
I would highly recommend a newer version of Ubuntu, at least 10.04 (Long-Term Support version) because the kernel is newer and has enhancements for the type of computer you're using.

When trying to boot from Uberstudent, you should be able to hold down the shift key while booting to get into a menu where you can select how to boot into Uberstudent. If you can get there, press e to edit the current boot option, then at the end of the line that looks something like this:
```

linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b1b3afaf-07a9-4db1-90f6-6f65f3fb6860 ro   quiet splash

```

Type in (at the end): nomodeset
Then press I believe its CTRL+X, it says at the bottom, to boot press _____
If that fails try: acpi=no

If both of those fail, let us know. I'm not sure what version of Ubuntu its based off of.

---

### Post by AaronsDarts on 2011-01-09
Uberstudent uses ubuntu 10.10 I believe, its just modded more for students with study aids and stuff. But holding shift did not do anything butted like normal about to dl a newer version of ubuntu and try that.

---

### Post by AaronsDarts on 2011-01-09
Ok so this is what I have so far I downloaded 10.04 like you said and I have that up and running. 

Now that I have ubuntu on here will that get rid of the "unknown keyword in configuration file" when I try to install Uberstudent? Or is there a list of apps that any one knows of that will get me all of the apps uberstudent has?

---

### Post by AaronsDarts on 2011-01-09
Ok uberstudent didn't work still. I have ubuntu 10.04 going good, I even rewrote the disc on the lowest speed. I get like 7 lines straight when I try to boot it that all say 

"unknown keyword in configuration file"
"unknown keyword in configuration file"
"unknown keyword in configuration file"
"unknown keyword in configuration file"
"unknown keyword in configuration file"
"unknown keyword in configuration file"
"unknown keyword in configuration file"
"unknown keyword in configuration file"
boot:

and nothing I try will fix it above that it says the linux edition and all that but I can't remember it...

---

### Post by slooksterpsv on 2011-01-09
> **AaronsDarts said:**
> Ok so this is what I have so far I downloaded 10.04 like you said and I have that up and running. 

Now that I have ubuntu on here will that get rid of the "unknown keyword in configuration file" when I try to install Uberstudent? Or is there a list of apps that any one knows of that will get me all of the apps uberstudent has?

They list the applications in the slideshows, and that. I downloaded KeepNote, and I really like it. There's a lot of OpenSource software they list on there, just need to google it.

KeepNote, I got from: [http://keepnote.org](http://keepnote.org) | Here's a direct download to the program, just save and run: [http://keepnote.org/keepnote/download/keepnote_0.6.7-1_all.deb](http://keepnote.org/keepnote/download/keepnote_0.6.7-1_all.deb)

---

### Post by AaronsDarts on 2011-01-10
Thanks I think that is what I might have to do, apparently I read a couple of reviews and it turns out that the network is broken. that they can't get faster speeds...

---

