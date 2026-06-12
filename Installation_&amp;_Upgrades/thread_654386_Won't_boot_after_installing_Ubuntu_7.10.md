---
title: "Won't boot after installing Ubuntu 7.10"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by burnttoast11 on 2007-12-31
I am trying to install Ubuntu on my brothers ThinkPad T30 but I am having some problems.  I can load the Live CD and install Ubuntu without any problems, but I can't boot into Ubuntu after the installation I can get to GRUB but if I boot normally it just goes blank and nothing happens.  If I select boot into recovery mode it lets me, but I don't know what the problem is so I don't know what to change.  Does anyone have any suggestions?
Thanks

---

### Post by Herman on 2007-12-31
When you say you "can get to GRUB but if I boot normally it just goes blank and nothing happens", do you mean your monitor goes completely blank and there's no text on it at all?
Or is there some text on there like "GRUB>_'" or anything at all?

---

### Post by Herman on 2007-12-31
I'm just guessing here, but...

It's strange that you wouldn't see anything at all because there are two chances you'll see something. 
When your computer is first booting, you'd be running in 'VGA' mode, which is a simple video mode from the BIOS.  Here is a link to an excellent howto which explains all we need to know about the vga= option, **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), by **[Indras]("http://www.ubuntuforums.org/member.php?u=126305")
Then when Ubuntu boots it loads the operating system's video drivers and you get a much nicer display.

Normally, even if you had a blank screen during boot-up, there would be no harm in that. You just wouldn't see anything for a while and then when it gets to the part where the vidoe driver kicks in and Ubuntu comes up, you'd get your display back.
Have you tried simply waiting a while in case it's just doing a file system check?

The main concern is, it could be stopping at some error and you can't read the error message because you have no display at that stage.
Maybe try pressing 'Enter', followed by 'Ctrl'+ 'D', in case it's hanging at the file system check. That would get you over that.
You'd still need to wait a minute for it to finish booting.

It could be something different from that, I'm only guessing at this stage, we might need to do some experiments and tests to try to work out what's wrong for sure.

---

### Post by Herman on 2007-12-31
Well you can do thjs, [Temporarily Edit the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu") if that's what your problem is. 
I'm still not even sure if I'm guessing right, probabably there's two problems and when you can see your display then you'll see an error message where it's stopping somewhere and then we'll be able to take it from there and get the real problem fixed. 
While I was waiting I made that article for you on the GRUB Page anyhow. It'll help some-one, sooner or later.
Bye for now, I'll check back here later on sometime.
Regards, Herman :)

---

### Post by burnttoast11 on 2007-12-31
Thanks for the help!
So I was able to boot into Ubuntu now.  I'm not sure what the problem is yet but if a push Ctrl-Alt-F1 after the screen goes blank I will get to the login screen.  I guess I will mess around and check out the logs and see what is wrong.

---

### Post by Herman on 2007-12-31
Oh, okay, good! :)
What does Ctrl-Alt-F1 do? 
That's a new one to me, is that from your ThinkPad T30 manual? I'm just curious in case it might help someone else someday, that's all. 
Anyhow, I'm very glad to read you got it booting! :)

Regards, Herman :)

---

### Post by burnttoast11 on 2007-12-31
I saw that Ctrl-Alt-F1 tip in one of the links you posted.  I will have to do some research to see what it does, but I am very happy it works!
Thanks again.

---

