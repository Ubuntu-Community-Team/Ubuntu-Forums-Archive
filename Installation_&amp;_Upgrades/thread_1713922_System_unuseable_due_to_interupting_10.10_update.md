---
title: "System unuseable due to interupting 10.10 update"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by Madgemade on 2011-03-24
Hi 

I have a server that was running 10.04 and I decided to upgrade it to 10.10 as I had already done this successfully to a different server.The upgrade was about 3/4 way through when I can't exactly remember why but it had to shut down I think it may have got stuck on a simple package update anyhow when I next turn on the server the login screen if different with a purple background and a popup about a gnome power installation error comes up after I enter my user name and password the login box freezes up and a box comes up saying that a unknown process has stop working and gives me the options to 'lock screen', 'cancel' or 'log out anyway' if I press 'cancel' the box disappears and nothing happens if I press 'log out anyway' the login box the bottom bar and the pop-up disappear if I wait a little 'update manager' comes up saying I can partly update some packages after I enter my password to do this though it all closes and does not reappear all you can do is move the mouse!!!

Please hep me fix this as I use this server to host my website and I would hate to have to reinstall Ubuntu.

Thanks,

---

### Post by Hedgehog1 on 2011-03-24
We need to get a look at what shape your partitions are in.  Then we can see what can be saved.

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by prshah on 2011-03-25
> **Madgemade said:**
> The upgrade was about 3/4 way through when I can't exactly remember why but it had to shut down 

Hi, please see this thread [Hardy is wonderful]("http://ubuntuforums.org/showthread.php?t=780531") for advice on how to recover from an interrupted upgrade.

Please post back here if you have problems with this advice.

---

### Post by Madgemade on 2011-04-02
The advise from the hardy is wonderful page would be very helpful if I could implement it but I have no way of getting into recovery mode or using a console at all I can access no more than the broken login prompt.:(

---

### Post by prshah on 2011-04-02
> **Madgemade said:**
> but I have no way of getting into recovery mode or using a console at all

Do you have physical access to the server? Then you can access Recovery Mode from the GRUB menu. Failing that, when at the login screen, you can press Ctrl+Alt+F1..F5 to access a virtual terminal.

If you do not have physical access to the server (Eg, hosted server) then you can also do this over ssh. SSH should continue to work even if your update was interrupted.

---

### Post by Madgemade on 2011-04-03
Thanks for that I do have physical access i'm sitting next to it now but I already knew about Ctrl Alt F1 I have no idea why I haven't tried it I will do that now!

---

