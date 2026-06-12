---
title: "Laptop not supporting Ubuntu Anymore?"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by solwatts on 2012-04-29
Hello,  I've been a short time Ubuntu-user, and I've really enjoyed using the OS.  I've installed it, uninstalled, and re-installed it multiple times through different mediums, but it looks like my computer doesn't want to handle it anymore.

I'd like to start using Ubuntu 12.04, but it doesn't seem like my computer wants to boot into it.  I've installed it onto a separate partition via WUBI, and when I boot into it, I see the Ubuntu loading screen, followed by blackness.  I tried booting from one of my 11.10 CDs, with the same result.

Is there any way to fix this problem? I'd really like to get back to using it!

---

### Post by oldfred on 2012-04-30
I do not know wubi, but it sounds like the same type of  video issue many others are having. What video do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by solwatts on 2012-05-01
> **oldfred said:**
> I do not know wubi, but it sounds like the same type of  video issue many others are having. What video do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Video? Are you talking about my Video/Graphics card, or something else?

---

### Post by solwatts on 2012-05-16
> **oldfred said:**
> I do not know wubi, but it sounds like the same type of  video issue many others are having. What video do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I apologize for my obvious ignorance about the topic, as I haven't paid much attention to the technical specs in my computer due to the fact that the majority of the computer is integrated by Intel in one way or another.

The detailed technical specifications file about my computer is found below:

---

### Post by goldblattster on 2012-05-16
> **oldfred said:**
> I do not know wubi, but it sounds like the same type of  video issue many others are having. What video do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I think Wubi uses the Windows Bootloader.

---

### Post by jadtech on 2012-05-16
wubi just uses window mostly to install on C drive  it uses dos grub to boot ..

though they are not trying to necessarily install wubi they also tried full install I would think nomodeset would  help..

following the links already posted should be a good start if they do install wubi they can use  nomodeset on boot up if they get a black screen

---

### Post by mastablasta on 2012-05-17
but intel GPu shouldn't neede nomodeset.
 
but you can try it and see what happens.

---

