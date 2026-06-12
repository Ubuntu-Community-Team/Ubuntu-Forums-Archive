---
title: "problems installing from cd"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by lcurros on 2006-07-28
When i reboot computer and starts cd (shipped) i choose first option (START OR INSTALL UBUNTU) and all aparently works and finishes correctly, but always with a blank screen.
Live system is mounted and if i change to a text console (CTL+ALT+F1) i can work normally, but not in graphic mode. Apparently problems with ATI graphics of my notebook.

What do i have to do to start installation (not live) of system?
Is there any way to start installation directly from cd without mounting live system?

thanks in advance and sorry my english

---

### Post by lcurros on 2006-07-28
is there any way to do installation in text mode?

please help!!

---

### Post by confused57 on 2006-07-28
I wouldn't try to install until you work out your graphics problem.
When you get a console by pressing Ctrl+Alt+F1, you could

```
sudo dpkg-reconfigure xserver-xorg
```

You can probably select default for most questions, but you could try different video drivers, starting with "vesa", "ati", "radeon"

See this guide:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by lcurros on 2006-07-28
I have to install ati drivers (i did the same with 5.10), but process needs to [COLOR="Red"]restart[/COLOR]. 
Here is the problem if i restart without install there is no system!!

---

### Post by confused57 on 2006-07-28
After reconfiguring the xserver, you would need to get back to a console & enter:

startx

or

sudo /etc/init.d/gdm start

If you're getting to a console, the LiveCD must be loaded, except the GUI display isn't configured...what kind of ati video card do you have?  Do you have an internet connection at the console?

Edit: Glad you were able to get it working on your own...I suppose the x.org entry is laptop specific?

---

### Post by lcurros on 2006-07-28
I have an ati mobility radeon x700
Console works fine with internet connection.

But the solution must be easy, only with a text mode installation program. Is there ?

---

### Post by lcurros on 2006-07-28
Reading forums i found that adding next line to device section (in xorg.conf)
[INDENT][COLOR="Orange"]Option "MonitorLayout" "LVDS,Auto"[/COLOR][/INDENT]

After i restart X and now works :p

---

### Post by john_m on 2006-07-28
> **lcurros said:**
> I have an ati mobility radeon x700
Console works fine with internet connection.

But the solution must be easy, only with a text mode installation program. Is there ?

I had to use the Ubuntu alternate ISO image -- that uses a text installer and everything worked fine.

---

### Post by lcurros on 2006-07-30
> **lcurros said:**
> Reading forums i found that adding next line to device section (in xorg.conf)
[INDENT][COLOR="Orange"]Option "MonitorLayout" "LVDS,Auto"[/COLOR][/INDENT]

After i restart X and now works :p

With this i could install ubuntu without problems :p . Maybe rendering of ati is disable (i didn´t check it) and i have to install propietary driver. 

Great!!
Thanks to all

---

### Post by az on 2006-07-30
> **lcurros said:**
> 
What do i have to do to start installation (not live) of system?
Is there any way to start installation directly from cd without mounting live system?

thanks in advance and sorry my english
Have you tried hitting F4 before you start the boot process (at the prompt) and select the VGA monitor mode?

---

