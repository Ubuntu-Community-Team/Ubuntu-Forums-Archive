---
title: "Gets stuck at the loading screen"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by 42f87d89 on 2011-11-17
Hi there, my computer is an acer aspire 7738 by the way.
Recently I have had some problems with my ubuntu, it gets stuck at the 5 dots screen.

I suspect either of these:
    When I first installed ubuntu 11.10 I had the same problem, but then I installed some drivers through the recovery mode and it fixed it.

or

    Right before I had this problem I just had finished some installations and I restarted my computer but the battery ran out.

Please halp me and thank you fo your time.

---

### Post by 2F4U on 2011-11-17
Can you get to a console with Ctrl-Alt-F1? If yes, check the log files to get some info on whats going on.

---

### Post by 42f87d89 on 2011-11-19
> **2F4U said:**
> Can you get to a console with Ctrl-Alt-F1? If yes, check the log files to get some info on whats going on.
Where are they located?

---

### Post by MAFoElffen on 2011-11-19
> **42f87d89 said:**
> Where are they located?
So... You were a little vague in your first post, so lets clear some of the haze.

You have an Acer Aspire 7738, which has a either ATI or NVidia graphics in it.
- You said you installed drivers, so what drivers for what card did you install?

You said this happened after "some installations"... What did you install?

What keys?  He asked for a 3-key combination, hold down the control key and the alt key, then press the F2 key = <cntrl><alt><F2>. It might not, depending how far it got in the X-Session.

So, if not, follow these directions:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR][/B]

Then do this
```

lspci -vnn | grep VGA

```
and post the results here.  We need the results to branch to one of 2 fixes... which depends on what type of video you have.

---

### Post by 42f87d89 on 2011-11-21
> **MAFoElffen said:**
> So... You were a little vague in your first post, so lets clear some of the haze.

You have an Acer Aspire 7738, which has a either ATI or NVidia graphics in it.
- You said you installed drivers, so what drivers for what card did you install?

You said this happened after "some installations"... What did you install?

What keys?  He asked for a 3-key combination, hold down the control key and the alt key, then press the F2 key = <cntrl><alt><F2>. It might not, depending how far it got in the X-Session.

So, if not, follow these directions:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR][/B]

Then do this
```

lspci -vnn | grep VGA

```and post the results here.  We need the results to branch to one of 2 fixes... which depends on what type of video you have.
I have a nvidia gt240m, I followed a tutorial to install a windows driver(I believe)
after 11.10 gave me some problems, the problem was very common.
I can get into the terminal through recovery mode I just want to know where is the log he reffered to located.

---

### Post by MAFoElffen on 2011-11-24
> **42f87d89 said:**
> I have a nvidia gt240m, I followed a tutorial to install a windows driver(I believe)
after 11.10 gave me some problems, the problem was very common.
I can get into the terminal through recovery mode I just want to know where is the log he reffered to located.
I'm not sure which tutorial, from who, or what log you are referring to.  I have several out there.  The logs I look at for NVidia graphics issues are:
```

/var/log/Xorg.0.log          # <-- Please post this for me
/var/nvidia-installer.log    # <-- This one is only there after installing a nvidia binary driver.
/var/syslog.log               # <-- I only have users post this when warranted.

```
The configuration file I look at is:
```

/etc/X11/xorg.conf    # <-- Please post this

```
 - What version of Ubuntu? What driver did you install?
 - I asked you to post the results of a command that specifically returns more info that just the card type and model.  Could you please post those results?

---

