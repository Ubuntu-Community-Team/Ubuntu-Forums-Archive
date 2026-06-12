---
title: "No Splash Screen on Encrypted Bootup"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2016-05-17
Hi:

I've installed encrypted Lubuntu 16.04 LTS on multiple Thinkpad X40 systems.

It works fine, with the usual minor bugs (disappearing cursor, etc) but the one striking thing is that blank boot screen--there's no text or box to enter the encryption code--just a very dark purple screen.  If one blindly enters the encryption code, it boots no problem.

Is this a bug or a feature?  (I could see how it might make the system more secure; if someone tries to boot it, they get what looks very much like a blank screen.)

Does anyone else have this issue/question?

Bill

---

### Post by sudodus on 2016-05-17
It is a known bug, [cryptsetup password prompt not shown](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1359689)

If you remove the boot option splash, you will se the prompt for the passphrase.

See this link: [Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

***Edit:*** Browse to

9. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

So edit **/etc/default/grub**

Remember to run

```
sudo update-grub
```

after you have edited and saved.

---

### Post by wjbmd48 on 2016-05-17
Thanks! You guys are great.

But no joy on this one. Here's how I edited the grub file:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""

I still get a blank splash screen, but now I see some text--too fast to read--right before the password box.

This isn't a big deal--the more I think about it, the more I like not having a thief/intruder not seeing a splash screen. More curious than anything else.

Again, thanks!

Bil

---

### Post by sudodus on 2016-05-17
Please try again and remove the word **splash**:

GRUB_CMDLINE_LINUX_DEFAULT=""

The word "quiet" can be there or not, it is not important in this case.

---

### Post by wjbmd48 on 2016-05-17
OK, got it. Not the pretty splash screen of 14.04 and previous, but a lot better than a blank screen.

Thanks so much! You guys are the best!

Bill

---

### Post by sudodus on 2016-05-17
When it works for you, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

[COLOR="#696969"]Otherwise, keep asking[/COLOR] ;-)

---

### Post by wjbmd48 on 2016-05-17
Duh, thanks for reminding me.


Bill

---

