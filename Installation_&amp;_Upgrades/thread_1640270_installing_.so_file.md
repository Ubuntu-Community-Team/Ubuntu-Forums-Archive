---
title: "installing .so file"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by aznjoka on 2010-12-07
I'm wanting to install an .so file but I have no idea how.

Would appreciate the help.

---

### Post by wojox on 2010-12-07
Is it a driver? What's it called?

---

### Post by coffeecat on 2010-12-07
A library file? Normally you install them through the package manager. What are you trying to install?

---

### Post by Carharttjimmy on 2010-12-07
This might help: [http://www.fileinfo.com/extension/so](http://www.fileinfo.com/extension/so)

---

### Post by aznjoka on 2010-12-07
I am trying to install the flash player 10.2b beta, i heard about the hardware acceleration and really need it at the moment, I had extracted it, but have no idea what to do next??

---

### Post by Carharttjimmy on 2010-12-07
Interesting, I heard that also. But, does it come in .so file?

Because that sounds like an executable. What did almighty google say?

---

### Post by aznjoka on 2010-12-07
The almighty google made it pretty complex for me to understand, not that it's a problem. But heading to Ubuntu Forum hoping to have it in laymen terms.

---

### Post by wojox on 2010-12-07
Open a terminal and cd to the directory it's in and run

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

Close firefox and reopen.

---

### Post by coffeecat on 2010-12-07
If that's a libflashplayer.so file, the easiest way is to create a 'plugins' folder in the hidden .mozilla folder in your home folder. Then simply copy/move the libflashplayer.so file into ~/.mozilla/plugins/.

If you've installed any other version of flash you need to uninstall that first.

This way only works for your account. It is possible to install it somewhere in /usr for all accounts, but I've forgotten the path. If you need it someone else might be able to help.

**Edit:** wojox already has.

---

### Post by aznjoka on 2010-12-07
Thanks! it worked ! thank you all, flash 10.2b working great hardware acceleration is amazing! thanks!

---

