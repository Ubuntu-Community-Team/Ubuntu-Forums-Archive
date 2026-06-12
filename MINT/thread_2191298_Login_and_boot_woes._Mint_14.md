---
title: "Login and boot woes. Mint 14"
date: 2013-12-01
forum: MINT
---

### Post by newbeeman on 2013-12-01
I am trying to help a daughter on the other side of the country get into her machine. It's an HP pavilion.
Yesterday she had a broken file, which she fixed, today on start up her machine failed. A black screen with OS and machine details, then a log in request for information, filling that in leads to a cursor waiting for more input. 
I have no idea what information it's waiting for, please help.

---

### Post by QIII on 2013-12-01
Hello!

What OS and version?  Could you give us a little more information about the hardware specifications?

If you could, a bit more detail about the exact behavior would be very helpful.

---

### Post by Impavidus on 2013-12-02
It seems she gets to the console login screen. This may happen when for some reason the graphical interface fails to load.

There are several consoles (tty1...6) and you can switch between them using ctrl-alt-F1...6. Ctrl-alt-F7 usually gets you to the GUI. Login in the console is possible by typing your user name, hit enter, type password, hit enter. Whilst typing the password no feedback is given on screen.

---

### Post by newbeeman on 2013-12-02
> **Impavidus said:**
> There are several consoles (tty1...6) and you can switch between them using ctrl-alt-F1...6. Ctrl-alt-F7 usually gets you to the GUI. Login in the console is possible by typing your user name, hit enter, type password, hit enter. Whilst typing the password no feedback is given on screen.

Thank you for the speedy reply. We tried all suggestions, ended up with Ctrl-alt-F7. This came up with "Starting .....OK" which then hung.
Suggestions gratefully received.

---

### Post by TOMBSTONEV2 on 2013-12-02
So what os are you running on what pc?

---

### Post by newbeeman on 2013-12-02
> **TOMBSTONEV2 said:**
> So what os are you running on what pc?

I did mention in the original post.  HP Pavilion, unsure of the model number. Running Linux Mint 14. Don't believe that makes a difference in this case?

---

### Post by oldos2er on 2013-12-03
Moved to Other OS/Distro Support.

---

### Post by newbeeman on 2013-12-03
> **oldos2er said:**
> Moved to Other OS/Distro Support.

Gee Thanks. Whatever happened to the Open Source creed. (Helping others!)  
Great, now I cannot find the original post as you've hidden it.  Definitely back To Mint.

---

### Post by oldos2er on 2013-12-04
Nothing's been hidden that I'm aware of.

We're an Ubuntu support forum. The Other OS/Distro Support subforum is maintained as a courtesy to people who may have questions or comments about other OSes. As noted at the [top of the page]("http://ubuntuforums.org/forumdisplay.php?f=401") "Please be aware this is not the best place to receive tech support for  these OSs/Distros and users should look for official support channels  for those systems."

[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Good luck with Mint.

---

### Post by steeldriver on 2013-12-04
> **newbeeman said:**
> I did mention in the original post.  HP Pavilion, unsure of the model number. **Running Linux Mint 14. Don't believe that makes a difference in this case?**

> **newbeeman said:**
> Gee Thanks. **Whatever happened to the Open Source creed. (Helping others!)  **
Great, now I cannot find the original post as you've hidden it.  Definitely back To Mint.

Yes it does make a difference - Mint 14 runs a different desktop (either Maya or Cinnamon) and likely a different display manager (mdm instead of lightdm) than any version of Ubuntu. Since your daughter's issue seems to be a failure to start the display manager those are directly relevant, and any Ubuntu-specific advice you would have got (such as "try logging in at the command line prompt and starting lightdm manually" or "try reconfiguring lightdm") would probably have been unhelpful at best - and at worst left her system in an even more broken state.

---

### Post by philinux on 2013-12-04
Prefix and title amended.

---

